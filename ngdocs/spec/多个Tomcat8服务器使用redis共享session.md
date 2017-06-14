# 多个Tomcat8服务器使用redis共享session

前提条件：

Tomcat为8.x

JDK为1.8或以上

<h2 id="1">1.打包Redis Session Manager</h2>


```
git clone git@github.com:chexagon/redis-session-manager.git
cd redis-session-manager
git checkout redis-session-manager-2.1.0
mvn clean
mvn package
```

1，克隆开源项目：https://github.com/chexagon/redis-session-manager

2，切换到一个最近release版

3，使用maven打包

打包之后生成文件：`redis-session-manager-2.1.0.jar`

<h2 id="2">2.导出所有的依赖包</h2>

根据项目中个包依赖，找到全部的jar包

![各个jar引用结构](http://photosd.nggirl.com.cn/work/f91f6e140b8c49ca8f58ca42b19bc974.png)

![导出结果](http://photosd.nggirl.com.cn/work/452ac8d4ebfa4087ad2b82bd3e501233.png)

<h2 id="3">3.配置Tomcat8</h2>

1，将打包结果和依赖包放到tomcat8的`conf/lib/`目录下

2，配置Tomcat8的`conf/context.xml`文件

![配置context.xml文件](http://photosd.nggirl.com.cn/work/44051085594d4e058654eedd524eb12b.png)

在`conf/context.xml`文件中添加`Manager`节点

其中：

endpoint是`<redis主机名>:<端口号>`格式
