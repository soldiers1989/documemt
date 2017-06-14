# 商品活动专题V3.1.0


* [1.商品活动基本信息V2.5.4](#1)
* [2.商品列表V3.1.0](#2)


<h2 id="1">1.商品活动基本信息V2.5.4</h2>

请求方法：nggirl/app/cli/seedProductColumn/getColumnInfo/2.5.4

请求URL：接口地址/nggirl/app/cli/seedProductColumn/getColumnInfo/2.5.4

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|columnId|[必填]商品活动专题编号


请求示例：

> http://localhost/nggirl/app/cli/seedProductColumn/getColumnInfo/2.5.4

返回结果示例：
```json
{
  "code":0,
  "data":{
    "columnId":1,
    "name":"",
    "headImg":"",
    "content":""
  }
}
```

返回结果说明：

|字段名称|字段含义|
|----|----|
|columnId|商品活动专题编号|
|name|专题名称|
|headImg|头图|
|content|内容|


<h2 id="2">2.商品列表V3.1.0</h2>

>出参删除tb_item_id、tb_detail_url，添加productDetailType

请求方法：nggirl/app/cli/seedProductColumn/getProductList/3.1.0

请求URL：接口地址/nggirl/app/cli/seedProductColumn/getProductList/3.1.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken|[非必填，登陆时必填]用户授权令牌|
|columnId|[必填]商品活动专题编号
|pageNum|页数 从0开始|
|pageSize|每页多少条，默认10|


请求示例：

> http://localhost/nggirl/app/cli/seedProductColumn/getProductList/3.1.0

返回结果示例：
```json
{
  "code":0,
  "data":[
    {
      "seedProductId":1,
      "name":"",
      "picture":"",
      "price":,
      "isSeed":1,
      "seedNum":88,
      "productDetailType":1
    },
    {
      "seedProductId":1,
      "name":"",
      "picture":"",
      "price":,
      "isSeed":1,
      "seedNum":88,
      "productDetailType":1
    }
  ]
}
```

返回结果说明：

|字段名称|字段含义|
|----|----|
|code|错误标识码，0表示正确|
|data - seedProductId|商品编号|
|data - name|商品名称|
|data - picture|商品配图|
|data - price|参考价|
|data - isSeed|是否种草：0未种草，1已种草|
|data - seedNum|种草人数|
|data - productDetailType|跳转商品详情类型，1老版本商品种草页面，2新版本商品详情页面|
