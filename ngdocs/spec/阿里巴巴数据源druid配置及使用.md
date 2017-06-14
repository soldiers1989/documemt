# 阿里巴巴数据源druid配置及使用

<h2 id="1">1.配置druid</h2>

相关链接：

1.[常见问题](https://github.com/alibaba/druid/wiki/%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98)

2.[DruidDataSource配置属性列表](https://github.com/alibaba/druid/wiki/DruidDataSource%E9%85%8D%E7%BD%AE%E5%B1%9E%E6%80%A7%E5%88%97%E8%A1%A8)

3.[打开Druid的监控统计功能](https://github.com/alibaba/druid/wiki/%E9%85%8D%E7%BD%AE_StatFilter)

4.[使用Druid的内置监控页面](https://github.com/alibaba/druid/wiki/%E9%85%8D%E7%BD%AE_StatViewServlet%E9%85%8D%E7%BD%AE)

5.内置监控中的Web和Spring关联监控怎么配置？

[Web关联监控配置](https://github.com/alibaba/druid/wiki/%E9%85%8D%E7%BD%AE_%E9%85%8D%E7%BD%AEWebStatFilter)

[Spring关联监控配置](https://github.com/alibaba/druid/wiki/%E9%85%8D%E7%BD%AE_Druid%E5%92%8CSpring%E5%85%B3%E8%81%94%E7%9B%91%E6%8E%A7%E9%85%8D%E7%BD%AE)

6.[防御SQL注入攻击配置](https://github.com/alibaba/druid/wiki/%E9%85%8D%E7%BD%AE-wallfilter)

<h2 id="2">2.登陆druid默认统计页面</h2>

1，页面路径

druid的登陆页面路径：http://<服务器域名或IP>:<端口号>/<项目名>/druid/index.html

例如测试服务器testcli1上的路径为：http://testcli1.nggirl.com.cn:8080/nggirl-web/druid/index.html

2，登陆账户

登陆账户配置在对应项目的web.xml文件中，例如nggirl-web项目：

![nggirl-web项目web.xml文件中的账户](https://photosd.nggirl.com.cn/work/0394aa4b8c2e4bd1949241aac6ae15af.png@1000w_1000h_80Q)


<h2 id="3">3.使用druid注意点</h2>

<h3 id="3.1">3.1.Session监控中的Principal配置</h3>

![Session监控结果页面](https://photosd.nggirl.com.cn/work/5cc7538399b84df484c59fefb0f7d687.png@1000w_1000h_80Q)

1，向Session中写入信息

![向Session中写入信息](https://photosd.nggirl.com.cn/work/2dff86a3927a42be891a1c965948cc6f.png@1000w_1000h_80Q)

2，web.xml配置

![web.xml配置](https://photosd.nggirl.com.cn/work/ccd4c01b74d6488588173e5e9d74e504.png@1000w_1000h_80Q)
