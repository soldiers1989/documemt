# 为O2O上门服务添加支持的城市

* [1.数据表](#1)
* [2.添加步骤](#2)
  * [2.1.检查和修改电商相关城市、城区信息](#2.1)
  * [2.2.向O2O城市城区表中添加数据](#2.2)
* [3.更新单实例缓存](#3)
  * [3.1.更新O2O服务支持的城市城区](#3.1)
  * [3.2.更新电商支持的省市区](#3.2)


<h2 id="1">1.数据表</h2>

O2O上门服务支持的城市、城区，与电商支持的省市区不相同。

|表名|表备注|支持O2O服务|支持电商服务|
|:---|:---|:---:|:---:|
|sys_supported_city|O2O服务支持的城市|√||
|sys_supported_area|O2O服务支持的城区|√||
|sys_province|全国对应的省份||√|
|sys_city|全国对应的城市（省份下属地级市）||√|
|sys_district|全国对应的区县（地级市下属区、县）||√|

1，sys_supported_city表中有CITYCODE字段，以及sys_city表的citycode字段都是`对应高德地图中的城市编码`

sys_city表中的编码较为完整，在插入sys_supported_city表内容时，应该参考sys_city表中的数据

2，sys_supported_area表中的数据，并不一定是全部的城区信息，因为O2O服务一般只支持市辖区，在添加数据时需要注意。

<h2 id="2">2.添加步骤</h2>

<h3 id="2.1">2.1.检查和修改电商相关城市、城区信息</h3>

>以你要添加的城市为`成都`为例

1，检查城市名称和城区名称

可以到[百度百科](http://baike.baidu.com/)中查询，看看这些城市名称和城区名称是否修改了，是否遗漏了，是否删除了。

根据检查结果，修改sys_city、sys_district表（修改、添加、删除操作）。

例如：郫县2016年12月撤县设区并更名为郫都区，但是sys_district表中依然记录的是郫县，所以就需要更改`郫县`为`郫都区`。


2，删除城市、城区

对于城市城区的删除，要非常谨慎。需要查看用户是否有使用过这两个地址才能删除！！!

可以通过item_order_address、user_common_address、score_shop_user_address这三张表中是否使用了对应的城市、城区，再决定是否删除、如何删除、如何迁移数据。


<h3 id="2.2">2.2.向O2O城市城区表中添加数据</h3>

先想城市表sys_supported_city中添加数据，然后向城区表sys_supported_area中添加数据。

O2O服务一般只支持市辖区，在添加数据时需要注意，询问提出该需求的人，应该添加哪些城区。

<h2 id="3">3.更新单实例缓存</h2>

系统支持的O2O城市、城区，以及电商支持的省市区信息是缓存在每一个服务器内存中的，所以在数据库中添加和修改城市、城区信息之后，需要通知对应的服务器更新缓存。

[更新单实例缓存](./缓存-单实例内存预存储功能项.md)


<h3 id="3.1">3.1.更新O2O服务支持的城市城区</h3>

更新O2O服务支持的城市城区expireKey为`O2OCityArea`，调用地址：

https://cli.nggirl.com.cn/nggirl-web/web/admin/common/memdata/reload?expireKey=O2OCityArea

>由于访问的是管理后台的接口，所以需要先登录

<h3 id="3.2">3.2.更新电商支持的省市区</h3>

如果更新了电商省市区相关表的信息，也需要更新电商缓存的省市区

电商支持的省市区expireKey为`ItemProvinceCityArea`，调用地址：

https://cli.nggirl.com.cn/nggirl-web/web/admin/common/memdata/reload?expireKey=ItemProvinceCityArea

>由于访问的是管理后台的接口，所以需要先登录
