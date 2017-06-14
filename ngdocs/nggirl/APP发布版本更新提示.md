# 发布版本更新提示

* [1.数据表](#1)
* [2.发布步骤](#2)
  * [2.1.上传安卓APK到阿里云并记录各个渠道包下载地址](#2.1)
  * [2.2.填充appversion](#2.2)
  * [2.3.填充appversion_log](#2.3)
  * [2.4.填充appversion_market](#2.4)
* [3.发布结果示例](#3)
  * [3.1.appversion](#3.1)
  * [3.2.appversion_log](#3.2)
  * [3.3.appversion_market](#3.3)
* [4.更新单实例缓存](#4)


<h2 id="1">1.数据表</h2>

版本发布时需要向三个

|表名|表备注|
|:---|:---|
|appversion|APP版本汇总信息|
|appversion_log|APP版本日志表|
|appversion_market|APK下载路径表|


<h2 id="2">2.发布步骤</h2>

<h3 id="2.1">2.1.上传安卓APK到阿里云并记录各个渠道包下载地址</h3>

1，上传APK，请参照相关文档：[上传安卓APK到阿里云](APP安卓APK上传到阿里云.md)

2，各个渠道包的下载路径：`http://photosd.nggirl.com.cn/apks/<版本号>/<APK文件名>`

<h3 id="2.2">2.2.填充appversion</h3>

>该表中填充的是本次发布的汇总信息

>每个版本发布都有两条信息，一条IOS信息，一条安卓信息


1，VERSIONNAME字段的值

版本名称，即本次发布的版本号，例如，3.1.2

2，VERSIONCODE字段的值

VERSIONCODE字段的值是一个正整数

（1）IOS计算方法：将版本号分隔，每一位乘以100，加上下一位，再乘以100，以此类推。

例如，版本号3.1.2，计算：`((3*100+1)*100)+2 = 30102`

（2）安卓计算方法：直接将IOS计算结果乘以10

例如，版本3.1.2，计算：`(((3*100+1)*100)+2)*10 = 301020`

3，APPTYPE字段的值

IOS端的值为`ios-c`，安卓端的值为`android-c`

<h3 id="2.3">2.3.填充appversion_log</h3>

>该表中的内容是app发布日志，appversion表与该表是一对多的关系。

>每一条日志都是一行数据。

<h3 id="2.4">2.4.填充appversion_market</h3>

>该表中的内容是APP在各个渠道的下载地址，appversion表与该表是一对多的关系。

>每一条下载地址都是一行数据

market字段是渠道号

IOS只有一个渠道：`appstroe`

<h2 id="3">3.发布结果示例</h2>

假设最近发布的版本是：3.1.2

发布日志为：

>1.解决手机版本兼容问题；

>2.解决线上一丢丢的小bug！

<h3 id="3.1">3.1.appversion</h3>

![插入版本信息](https://photosd.nggirl.com.cn/work/20b52ae082884e00b9f573d6453d0861.png@500w_100h_70Q)

<h3 id="3.2">3.2.appversion_log</h3>

![插入日志](https://photosd.nggirl.com.cn/work/59c764964d984925a3b562d3879a4fe2.png@500w_200h_70Q)

<h3 id="3.3">3.3.appversion_market</h3>

![插入渠道信息i](https://photosd.nggirl.com.cn/work/6ae5309042ed4a47860fb957880013f7.png@500w_500h_70Q)


<h2 id="4">4.更新单实例缓存</h2>

APP版本信息是存放在每一台服务器的内存中的，所以，如果数据库中更新了版本信息，需要通知服务器进行更新。

[更新单实例缓存](./缓存-单实例内存预存储功能项.md)

更新APP版本信息expireKey为`AppVersion`，调用地址：

https://cli.nggirl.com.cn/nggirl-web/web/admin/common/memdata/reload?expireKey=AppVersion

>由于访问的是管理后台的接口，所以需要先登录
