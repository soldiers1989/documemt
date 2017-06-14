# 我的种草V2.5.3

* [1.种草（收藏商品）V2.5.3](#1)
* [2.获取种草列表V2.5.0](#2)
* [3.删除种草V2.3.0](#3)


<h2 id="1">1.种草（收藏商品）V2.5.3</h2>

>出参增加addScore字段

请求方法：nggirl/app/cli/seedproduct/collectProduct/2.5.3

请求URL：接口地址/nggirl/app/cli/seedproduct/collectProduct/2.5.3

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken|[必填]授权令牌
|seedProductId|[必填]商品编号
|targetType|[必填]采集类型，1文章帖子，2视频帖子，3日签,0其他,4商品活动专题，5首页商品搜索，6首页推荐,7电商-商品详情
|targetId|[必填]采集点id，1文章帖子id，2视频帖子id，3日签id，0其他，4商品活动专题id

请求示例：

> http://localhost/nggirl/app/cli/seedproduct/collectProduct/2.5.3

返回结果示例：
```json
{
  "code":0,
  "data":{
    "addScore":1
  }
}
```

返回字段说明：


|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|Data - addScore|用户本次操作增加的积分数|


<h2 id="2">2.获取种草列表V2.5.0</h2>

> 入参增加isStartSell，出参增加targetType，targetId

请求方法：nggirl/app/cli/seedproduct/ListCollectProduct/2.5.0

请求URL：接口地址/nggirl/app/cli/seedproduct/ListCollectProduct/2.5.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken|授权令牌（必填）
|pageNum|页数，默认为0（选填）
|pageSize|每页大小，默认20（选填）
|isStartSell|是否已开售，1已开售，0未开售|

请求示例：

> http://localhost/nggirl/app/cli/seedproduct/ListCollectProduct/2.5.0

返回结果示例：
```json
{
  "code":0,
  "data":[
    {
      "seedProductId":1,
      "name":"Mac唇膏",
      "picture":"http://testphotosd.nggirl.com.cn/sysres/dressTypeImage/makeup-list-2.png",
      "price":99,
      "seedNum":100,
      "recommendation":10,
      "targetType":1,
      "targetId":100
    },
    {
      "seedProductId":12,
      "name":"Mac唇膏",
      "picture":"http://testphotosd.nggirl.com.cn/sysres/dressTypeImage/makeup-list-2.png",
      "price":99,
      "seedNum":100,
      "recommendation":10,
      "targetType":1,
      "targetId":100
    }
  ]
}
```

返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|Data - seedProductId|商品编号|
|Data - name|商品名称|
|Data - picture|商品图|
|Data - price|价格|
|Data - seedNum|种草人数|
|Data - recommendation|推荐度，0-10|
|Data - targetType|1文章帖子，2视频帖子，3日签，0其他|
|Data - targetId| 对应targetType，文章id，视频id，日签id，0其他|


<h2 id="3">3.删除种草V2.3.0</h2>


请求方法：nggirl/app/cli/seedproduct/deleteCollectProduct/2.3.0

请求URL：接口地址/nggirl/app/cli/seedproduct/deleteCollectProduct/2.3.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken|授权令牌（必填）|
|seedProductIds|商品编号,英文逗号“,”分隔（必填）|


请求示例：

> http://localhost/nggirl/app/cli/seedproduct/deleteCollectProduct/2.3.0

返回结果示例：
```json
{
  "code":0,
  "data":null
}
```

返回字段说明：


|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
