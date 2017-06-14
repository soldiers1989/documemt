#spring+redis做数据对象缓存

##1.添加maven依赖
```java
		<dependency>
			<groupId>org.springframework.data</groupId>
			<artifactId>spring-data-redis</artifactId>
			<version>1.6.4.RELEASE</version>
		</dependency>
		<dependency>
			<groupId>redis.clients</groupId>
			<artifactId>jedis</artifactId>
			<version>2.8.0</version>
		</dependency>
		<!-- 注意这里-->
		<dependency>
			<groupId>com.fasterxml.jackson.core</groupId>
			<artifactId>jackson-databind</artifactId>
			<version>2.6.6</version>
		</dependency>
```

对于jackson-databind的引用不是必须的。但是，如果你使用的是默认的jdk序列化器，那么要求你的缓存类必须实现Serializable接口。如果不想影响你的model的，又想使用json序列化器的话，那么这个依赖就需要加了。

##2.添加spring配置文件
可以以spring-redis.xml命名
```java
<?xml version="1.0" encoding="UTF-8"?>
<beans
    xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:context="http://www.springframework.org/schema/context"
    xmlns:c="http://www.springframework.org/schema/c"
    xmlns:p="http://www.springframework.org/schema/p"
    xmlns:cache="http://www.springframework.org/schema/cache"
    xsi:schemaLocation="
        http://www.springframework.org/schema/beans
		http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context
		http://www.springframework.org/schema/context/spring-context.xsd
        http://www.springframework.org/schema/cache
		http://www.springframework.org/schema/cache/spring-cache.xsd">
 
    <context:component-scan base-package="com.pumpkin.carriage.service" />
    <context:property-placeholder location="classpath:redis.properties"/>
 
    <!-- turn on declarative caching -->
    <cache:annotation-driven cache-manager="cacheManager"/>
 
    <!-- Jedis ConnectionFactory -->
   <!--  <bean
        id="jedisConnectionFactory"
        class="org.springframework.data.redis.connection.jedis.JedisConnectionFactory"
        p:host-name="${redis.hostname}"
        p:port="${redis.port}"
        p:password="${redis.password}"
        p:use-pool="true"/> -->
        
    <bean
        id="jedisConnectionFactory"
        class="org.springframework.data.redis.connection.jedis.JedisConnectionFactory">
        <property name="hostName" value="${redis.hostname}"></property>
        <property name="port" value="${redis.port}"></property>
        <property name="password" value="${redis.password}"></property>
    </bean>
 
    <!-- redis template definition -->
    <bean
        id="redisTemplate"
        class="org.springframework.data.redis.core.RedisTemplate"
        p:connection-factory-ref="jedisConnectionFactory" >
        <property name="valueSerializer">
        	<bean class="org.springframework.data.redis.serializer.GenericJackson2JsonRedisSerializer" />
        </property>
        <!-- 1.注意这里 -->
        <property name="keySerializer">  
	        <bean class="org.springframework.data.redis.serializer.StringRedisSerializer" />  
	    </property> 
        </bean>
 
    <!-- declare Redis Cache Manager -->
    <bean
        id="cacheManager"
        class="org.springframework.data.redis.cache.RedisCacheManager">
        <constructor-arg name="redisOperations" ref="redisTemplate" /> 
   </bean>
 
</beans>

```

以下是redis.properties文件的内容：
```java
redis.hostname=121.42.201.230
redis.port=7001
#2.注意这里
redis.password=3456789
```

以上，第1个注意点，缓存对象key值的序列化形式的，如果这里不添加keySerializer，而是使用默认的话那么，在redis后台看到的key会是：“\xac\xed\x00\x05t\x00\tb”这样包含一个转码的前缀，是不是很不爽，是不是查看的时候会很不方便，所以这里必须要设置key的序列化器。
第2个注意点，是redis链接配置的，如果你的redis没有设置密码，那么这个地方可以不写，不过redis还是应该设置密码的吧，不然大门四开....

##3.添加Cacheable注解
cacheable能够实现自动缓存接口的返回结果，所以我们可以把注解直接加到我们需要缓存结果的接口上。

放的位置可以试service也可以是dao，以下是放到service和dao层的示例：

放到service层上：
```java
@Cacheable(value="workDetailV150",key="'workDetailV150'.concat(#param.workId.toString()).concat(#param.userId.toString())")
	public CliDresserWorkDetailV150 getWorkDetail(CliGetWorkDetailParam param) throws Exception {
		return doGetWorkDetail(param);
	}
```

放到dao层上：
```java
	@Cacheable(value="getWorkDetailPhotos",key="'getWorkDetailPhotos'.concat(#root.args[0])")
	List<String> getWorkDetailPhotos(Integer workId);
```

有没有看到，两者的不同，在dao层上，因为用了mybatis的缘故，这里只有接口，那么用workId放到key里面是存不到redis的，因为spring cache拿到的是null。所以这里必须用#root.args[x]的方式设置。

问题来了，那个这里有一个value还有一个key，他们分别代表了什么呢？
![](http://img.blog.csdn.net/20150924194924945)
上边这张图很好的说明了他们的作用，每一个key对应到一个缓存的对象实体，那么value呢？可以看做是一个分作，你缓存的所有key都可以在这里找到。图中的“zset”就是value对应的项，每一个省都是一个key对应的项。为什么要弄一个zset在这里多余？后边的弹出一章你就明白了。


这里有一个细节，如果我的service接口返回了很多内容，不想全部缓存，怎么办？这里不能直接定义内部方法，添加cacheable然后在一个service接口方法里调用。因为，不管你用的是private还是public在这里都不会缓存的，必须是直接被controller调用的接口，或者直接调用的另外一个注入的service的接口。这里我和海威有一些争议：我的想法是，既然都是get方法，那么直接在controller里面组装业务逻辑比较合适，他觉得在service里面调用其他service也无妨。

##4.强制清除缓存
如果我们缓存的实体更新了，怎么办？不能够get的还是就的东西。这时候就需要强制清除相关联的缓存了。方法就是提供一个空的接口方法，在该方法上添加@CacheEvict的注解，如下：

```java
@CacheEvict(value = "workDetailV150", allEntries=true)
	public void evictWorkDetailCache(){
	}
```

再到controller层的时候，该怎么做呢？这个你应该能够想到的...

##5.cacheable注解中key表达式的说明
这个地方主要简单说明一下3个要素：1.字符串、2.接口参数、3.环境参数，以及一个函数
字符串很好说了用单引号括起来就可以了。
接口参数直接用#加参数名，如果是参数内的属性那么继续用.串联接好了。
环境参数：

|属性名称|描述|示例
---|---|---
methodName|当前方法名|#root.methodName
method|当前方法|#root.method.name
target|当前被调用的对象|#root.target
targetClass|当前被调用的对象的class|#root.targetClass
args|当前方法参数组成的数组|#root.args[0]
caches|当前被调用的方法使用的Cache|#root.caches[0].name

最后是关键函数concat，意思很明白了，就是连接字符串用的。

##6.重要连接
这是海威找到的一个特别好的贴子，将的很细致：http://haohaoxuexi.iteye.com/blog/2123030
这是spring-data-redis的官方文档：http://docs.spring.io/spring-data/data-redis/docs/current/reference/html/#redis:support:cache-abstraction
这时spring cache的一个英文教程：http://www.baeldung.com/spring-cache-tutorial
这是序列化器的一个贴子：http://www.360doc.com/content/15/0513/21/1073512_470277654.shtml
这是cacheable注解key表达式的一个stackoverflow上的贴子：http://stackoverflow.com/questions/11889428/spring-cacheable-with-complex-keys-still-executed
这是一个redis的命令集合，分类的特别好：http://doc.redisfans.com/

