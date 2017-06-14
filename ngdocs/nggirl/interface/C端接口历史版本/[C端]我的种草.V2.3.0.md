# 我的种草V2.3.0

* [1.种草（收藏商品）V2.3.0](#1)
* [2.获取种草列表V2.3.0](#2)
* [3.删除种草V2.3.0](#3)


<h2 id="1">1.种草（收藏商品）V2.3.0</h2>

请求方法：nggirl/app/cli/seedproduct/collectProduct/2.3.0

请求URL：接口地址/nggirl/app/cli/seedproduct/collectProduct/2.3.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken|授权令牌（必填）
|seedProductId|商品编号（必填）


请求示例：

> http://localhost/nggirl/app/cli/seedproduct/collectProduct/2.3.0

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


<h2 id="2">2.获取种草列表V2.3.0</h2>

请求方法：nggirl/app/cli/seedproduct/ListCollectProduct/2.3.0

请求URL：接口地址/nggirl/app/cli/seedproduct/ListCollectProduct/2.3.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken|授权令牌（必填）
|pageNum|页数，默认为0（选填）
|pageSize|每页大小，默认20（选填）

请求示例：

> http://localhost/nggirl/app/cli/seedproduct/ListCollectProduct/2.3.0

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
      "seedNum":100
    },
    {
      "seedProductId":12,
      "name":"Mac唇膏",
      "picture":"http://testphotosd.nggirl.com.cn/sysres/dressTypeImage/makeup-list-2.png",
      "price":99,
      "seedNum":100
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
