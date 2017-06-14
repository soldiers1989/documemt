#弹性搜索（elasticsearch）最新入门攻略#

##elassticsearch#
###能做什么#
elasticsearch是一个专用的站内全文搜索引擎，基于开源的lucene实现，本身也是开源的产品，允许进行修改和再发布。

elasticsearch采用lucene作为它的索引和检索核心，并且，提供了restful api进行服务管理和数据检索，部署和使用都十分便捷。

更好的是，elasticsearch原生的支持集群化和分布式，能够很好的适应当前DT的潮流，做到高可用和易扩展。

###什么时候用#

数据库能够很好的支持索引和搜索，一般来说，如果公司刚刚起步，那么没有必要上来就弄一个es做搜索服务。

如果，产品的基础服务已经搭建好了，需要向更好的用户体验方面发展那么这时候可以使用es这类的全文搜索引擎了。

es不支持数据库连表查询功能，所以，es应该是搜索的的辅助，原始数据应该仍然是存储在数据库里面的。同步，要么相关接口更新es索引，要么采用阿里canal这样的数据库binlog同步工具。

es的搜索方式是和baidu、360、神马这些搜索引擎的搜索方式一样的，搜索的过程中首先会对搜索词条进行分词，每一个分词都会被作为匹配条件，最终所有分词的匹配度加和给出所有命中项的匹配度分值，也就是相关度。

es返回的结果按照的就是相关度由大到小的顺序。

好了，接下来我们看一下入门es的完整步骤，如果想了解更多关于es的高级功能，请参见最后推荐阅读一章，尤其是其中的《elasticsearch权威指南》。
##安装部署##
es有三种安装方式：1.使用官方版本安装，这种方式安装需要自己安装相关插件；2.使用rtf版本安装，这种方式已经添加了必要的中文分词和索引插件；3.使用docker镜像安装，这种方式直接安装的是包含了es的虚拟机。

###使用rtf版本安装#
在github上下载rtf版本的es，下载地址：https://github.com/medcl/elasticsearch-rtf

我使用的是2.2.0版本的rtf，下载后把压缩包放到/usr/local中，执行以下命令解压：

> unzip elasticsearch-rtf-2.2.0.zip

cd到conf目录，修改如下两项：
> cluster.name: 你的工程名
> network.host: 局域网网卡地址

修改第一项，是因为es是采用广播的方式寻找局域网内的其他es，如果集群名相同则自动加入到集群中。如果不修改，集群名默认是elasticsearch，很容易被其他人部署的es，或者自己测试的es干扰，造成不可预测的问题。

修改第二项，是因为，es默认绑定的ip是127.0.0.1，不修改的话其他机器无法访问这个es节点。

修改后，执行以下命令启动es：

> ./elasticsearch -d

-d命令是指定es作为后台程序执行，如果不加-d，当你远程ssh连接服务器，启动es之后，一旦关闭了本季的命令行窗口，es也将自动关闭。

好了，启动好只好，我们来和es打个招呼。es提供了restful的接口，所以这里我们用curl请求，查看一下es是否安装成功。在命令行输入命令：

> curl -XGET http://ip:9200/

安装正确，应该可以得到如下形式的反馈：

```json
{
  "name" : "Margali Szardos",
  "cluster_name" : "nggirl-es",
  "version" : {
    "number" : "2.2.0",
    "build_hash" : "8ff36d139e16f8720f2947ef62c8167a888992fe",
    "build_timestamp" : "2016-01-27T13:32:39Z",
    "build_snapshot" : false,
    "lucene_version" : "5.4.1"
  },
  "tagline" : "You Know, for Search"
}
```

###录入索引数据#
可以使用如下命令创建一个索引
> curl -XPUT http://ip:9200/myIndex -d '{"settings" :{"number_of_shards" :3,"number_of_replicas" : 1}}'

该索引的名称是myIndex，共有3个分片，每隔分片有一个副本。

执行如下命令，在上述索引中插入数据

> curl -XPUT http://ip:9200/myIndex/employee/1 -d '{"first_name" : "John","last_name" :  "Smith","age" :        25,"about" :      "I love to go rock climbing", "interests":[ "sports", "music" ]}'

上述命令在myIndex索引中的employee类型，插入了一个_id为1的员工数据。

也可以在没有创建索引的情况下，直接执行插入数据的操作，那么索引的设置会采用默认设置，即5个分片，每个分片1个副本。

要获取上述数据可以执行如下命令

> curl -XGET http://ip:9200/myIndex/employee/1

或者用更复杂的查询，具体可参见推荐阅读。

##spring+elasticsearch集成#
###添加配置文件#
这里不默认大家已经知道如何创建spring-mvc 的web工程。 以下的内容，均在spring-mvc工程中添加。这里使用的spring版本是4.2.6、pring-data-elasticsearch 2.0.0.RELEASE、elasticsearch 2.2.0、所以elasticsearch-rtf必须使用2.2.0，否则连接失败。

添加一个spring-elasticsearch.xml文件，内容如下

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:elasticsearch="http://www.springframework.org/schema/data/elasticsearch"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
http://www.springframework.org/schema/beans/spring-beans-3.1.xsd
http://www.springframework.org/schema/data/elasticsearch
http://www.springframework.org/schema/data/elasticsearch/spring-elasticsearch-1.0.xsd">

    <elasticsearch:repositories base-package="com.pumpkin.carriage.repository.elasticsearch" />

	<!-- 本地文件存储，无需部署elasticsearch -->
    <!-- <elasticsearch:node-client id="client" local="true" /> -->
    <!-- 远程elasticsearch服务 -->
    <elasticsearch:transport-client id="client" cluster-nodes="${application.parameter.elasticsearch.cluster.nodes}"  cluster-name="nggirl-es"/>

    <bean name="elasticsearchTemplate"
          class="org.springframework.data.elasticsearch.core.ElasticsearchTemplate">
        <constructor-arg name="client" ref="client" />
    </bean>
</beans>
```

elasticsearch:repositories是repository接口文件的包目录，用于自动扫描实例化repository接口。

client是集群bean对象，cluster-nodes是集群中的节点ip列表，端口号用9300。因为client是作为一个集群节点链接的，不是采用的restful接口。

elasticsearchTemplate是es的模板bean，会被自动注入到实例化的repository中。

说下node-client和transport-client。node-client是会存储数据的节点，但是不参与数据获取；transport-client是不存储数据的节点，仅用来支持增删改查。

当node-client的local设置为true时，会在tomcat相同的jvm中创建本地的es服务，随tomcat一同启动。

###添加域模型#
定义自己的业务模型，这里以常见的用户为例：

```java
package com.pumpkin.carriage.model.elasticsearch;

import org.springframework.data.annotation.Id;
import org.springframework.data.elasticsearch.annotations.Document;
import org.springframework.data.elasticsearch.annotations.Field;
import org.springframework.data.elasticsearch.annotations.FieldType;

@Document(indexName= "myIndex", type= "user", shards = 1, replicas = 0, refreshInterval = "-1")
public class ESUser {
	@Id
	private String userId;
	@Field(type = FieldType.String)
	private String profile;
	@Field(type = FieldType.String)
	private String nickName;
	@Field(type = FieldType.String)
	private String userRole;
	public String getUserId() {
		return userId;
	}
	public void setUserId(String userId) {
		this.userId = userId;
	}
	public String getProfile() {
		return profile;
	}
	public void setProfile(String profile) {
		this.profile = profile;
	}
	public String getNickName() {
		return nickName;
	}
	public void setNickName(String nickName) {
		this.nickName = nickName;
	}
	public String getUserRole() {
		return userRole;
	}
	public void setUserRole(String userRole) {
		this.userRole = userRole;
	}
}

```

其中的@Id字段必须要有，该字段会自动被设置成es中该对象的_id，也就是可以通过GET命令的id获取方式获得，也就是可以用：

> curl -XGET http://ip:9200/myIndex/user/_id

方式获得数据对象。

###添加访问接口（repository）#

```java
package com.pumpkin.carriage.repository.elasticsearch;

import java.util.List;

import org.springframework.data.domain.Pageable;
import org.springframework.data.elasticsearch.repository.ElasticsearchCrudRepository;

import com.pumpkin.carriage.model.elasticsearch.ESUser;

public interface UserRepositry   extends ElasticsearchCrudRepository<ESUser, String>{
	List<ESUser> findByNickName(String nickName,Pageable pageable);
	
	List<ESUser> findByNickNameLike(String nickName,Pageable pageable);
}

```

findByNickName方法的作用是，获取用户名为nickName的用户列表，Pageabel可以传入一个PageRequest对象，包含页数和每页的大小。

findByNickNameLike方法的作用是，获取用户名模糊等于nickName的用户列表。

要理解这里，需要看推荐阅读中的spring-data-jpa相关文档。

好了，这样就可以把你的repository注册给任何service了，配置和使用方式和mybatis如出一辙，十分相像。

##使用web管理插件#
要查看es集群的状态可以使用命令查看
> curl -XGET http://ip:9200/_cluster/health

会返回如下形式的结果：

```json
{
"cluster_name":"nggirl-es",
"status":"green",
"timed_out":false,
"number_of_nodes":1,
"number_of_data_nodes":1,
"active_primary_shards":2,
"active_shards":2,
"relocating_shards":0,
"initializing_shards":0,
"unassigned_shards":0,
"delayed_unassigned_shards":0,
"number_of_pending_tasks":0,
"number_of_in_flight_fetch":0,
"task_max_waiting_in_queue_millis":0,
"active_shards_percent_as_number":100.0
}
```

这样不是很方便，也不是很全面，es有两个插件可以做到集群信息查看和集群管理，一个是官方的marvel，这个是收费的，一个是head，这个是免费的。接下来说一下head的安装。

首先cd到elasticsearch/bin目录，执行如下命令：

> ./plugin -install mobz/elasticsearch-head


完成之后，重新启动es，然后在浏览器访问，http://ip:9200/_plugin/head/即可。

这里还缺少一些关于es安全防护和后期维护的问题，后续有机会再增加。

##推荐阅读#
1. 《elasticsearch权威指南》在线翻译版本：http://es.xiaoleilu.com/index.html
2. elasticsearch官方下载地址：https://www.elastic.co/downloads/elasticsearch
3. rtf版下载地址：https://github.com/medcl/elasticsearch-rtf
4. spring-data-elasticsearch帮助文档：https://es.yemengying.com/
5. spring-data-jpa的使用文档：http://www.ibm.com/developerworks/cn/opensource/os-cn-spring-jpa/
6. 博客专栏：http://blog.csdn.net/laoyang360/article/details/52244917#t28



