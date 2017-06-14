<h1>首页搜索V2.5.4</h1>

> 合并贴子和标签搜索。三个搜索均添加高亮标记。

目录

* [1.获取热门搜索词](#1)
* [2.搜索帖子V2.5.6](#2)
* [3.搜索用户V2.5.6](#3)
* [4.搜索商品V2.5.6](#4)


<h2 id="1">1.获取热门搜索词</h2>

请求方法：nggirl/app/cli/search/getPopularSearchWords/2.2.0

请求URL：接口地址/nggirl/app/cli/search/getPopularSearchWords/2.2.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：无

请求示例：

> http://localhost/nggirl/app/cli/search/getPopularSearchWords/2.2.0?phoneNum=13581878073&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&password=123456&accessToken=e69165ff30434105af03f593a26fceb0

返回结果示例：

```json
{
  "code": 0,
  "data": [
    [
      "美白",
      "护肤"
    ],
    [
      "隔离霜",
      "papi酱"
    ],
    [
      "pikaqiu酱"
    ]
  ]
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data 	|热门搜索词列表

<h2 id="2">2.搜索帖子V2.5.6</h2>

> 输入和输出参数不变，输出结果的tags中需要高亮的文字用“<em></em>”包裹

请求方法：nggirl/app/cli/search/postSearch/2.5.6

请求URL：接口地址/nggirl/app/cli/search/postSearch/2.5.6

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---
|page	|[可选]页数,非必需参数，默认第一页
|num	|[可选]每页信息数目,非必须参数，默认20
|searchWord |[必填]搜索词


请求示例：

> http://localhost/nggirl/app/cli/search/postSearch/2.5.6

返回结果示例：

```json
{
    "code": 0,
    "data": [
      {
          "postId":10,
          "postType":1,
          "picture":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg"
      },
      {
          "postId":11,
          "postType":1,
          "picture":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg"
      }
    ]
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - postId|帖子编号|
|Data - postType|帖子类型 1为文章，2为视频|
|Data - picture|帖子配图|


<h2 id="3">3.搜索用户V2.5.6</h2>

> 输入和输出参数不变，输出结果的nickName中需要高亮的文字用“<em></em>”包裹

请求方法：nggirl/app/cli/search/userSearch/2.5.6

请求URL：接口地址/nggirl/app/cli/search/userSearch/2.5.6

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|[可选]用户授权令牌，若用户已登录，则必填。
|page	|[可选]页数,非必需参数，默认第一页
|num	|[可选]每页信息数目,非必须参数，默认20
|searchWord |[必填]搜索词


请求示例：

> http://localhost/nggirl/app/cli/search/userSearch/2.5.6

返回结果示例：

```json
{
    "code": 0,
    "data": [
      {
          "userId": 1,
          "profile": "http://testphotosd.nggirl.com.cn/work/135dd0dd6fc9436f8834a73ae31e8e2b.jpg",
          "nickName": "南瓜哥哥",
          "userRole": "南瓜小编",
          "isFollowed":0,
      },{
          "userId": 2,
          "profile": "http://testphotosd.nggirl.com.cn/work/135dd0dd6fc9436f8834a73ae31e8e2b.jpg",
          "nickName": "南瓜小小",
          "userRole": "客座小编",
          "isFollowed":1,
      }
    ]
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - userId|用户id|
|Data - profile|用户头像|
|Data - nickName|用户昵称|
|Data - userRole|用户角色|
|Data - isFollowed|是否已关注该用户，1已关注，0未关注|

<h2 id="4">4.搜索商品V2.5.6</h2>

> 输入和输出参数不变，输出结果的name中需要高亮的文字用“<em></em>”包裹

请求方法：nggirl/app/cli/search/seedProductSearch/2.5.6

请求url：接口地址/nggirl/app/cli/search/seedProductSearch/2.5.6

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken	|[可选]用户授权令牌，若用户已登录，则必填。|
|searchWord |[必填]搜索词|
|pageNum	|[可选]页数,非必需参数，默认第一页|
|pageSize	|[可选]每页信息数目,非必须参数，默认20|


请求示例：

> http://localhost/nggirl/app/cli/search/seedProductSearch/2.5.6

返回结果示例：

```json
{
    "code":0,
    "data":[
        {
            "seedProductId":1,
            "name":"商品名称1",
            "picture":"http://photosd.nggirl.com.cn/work/c9138c508f5d49f0afddf324c9097f3a.png",
            "price":1209,
            "seedNum":32,
            "isSeed":0
        },
        {
            "seedProductId":2,
            "name":"商品名称2",
            "picture":"http://photosd.nggirl.com.cn/work/c9138c508f5d49f0afddf324c9097f3a.png",
            "price":1209,
            "seedNum":32,
            "isSeed":1
        }
    ]
}
```

返回结果说明：

|字段名称|字段含义|
|----|----|
|Code|错误标识码，0标识正确|
|Data - seedProductId|商品编号|
|Data - name|商品名称|
|Data - picture|商品图|
|Data - price|商品价格|
|Data - seedNum|种草人数|
|Data - isSeed|是否已种草，0未种草，1已种草|
