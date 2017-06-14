# 首页V4.0.0相关接口
  
## 目录
------

* [1.推荐V4.0.0](#1)
* [3.美物V4.0.0](#3)
* [4.标签对应帖子列表V4.0.0](#4)
* [5.获取控制标签V4.0.0](#5)
* [关注用户下的帖子](https://github.com/nggirl/ngdocs/blob/master/nggirl/interface/%5BC端%5D社区-南瓜社团和关注V4.0.0.md#8)
* [所有推荐关注用户](https://github.com/nggirl/ngdocs/blob/master/nggirl/interface/%5BC端%5D社区-南瓜社团和关注V4.0.0.md#6)



<h2 id="1">1.推荐V4.0.0</h2>

请求方法：nggirl/app/cli/homePage/recommendPost/4.0.0

请求url：接口地址/nggirl/app/cli/homePage/recommendPost/4.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|pageNum|[可选]第几页，默认从0开始|
|pageSize|[可选]每页条数，默认为20|

请求示例：

> http://localhost/nggirl/app/cli/homePage/recommendPost/4.0.0

返回结果示例：
```json
{
  "code":0,
  "data":[
    {
      "postId":1,
      "postType":1,
      "title":"",
      "detailImg":"",
      "userId":123,
      "nickName":"",
      "profile":"",
      "descrip":"",
      "commentNum":100,
      "viewNum":10000,
      "likeNum":200
    },
    {
      "postId":1,
      "postType":1,
      "title":"",
      "detailImg":"",
      "userId":123,
      "nickName":"",
      "profile":"",
      "descrip":"",
      "commentNum":100,
      "viewNum":10000,
      "likeNum":200
    }
  ]
}
```
返回结果说明：

|字段名称|字段含义|
|----|----|
|Code|错误标识码，0表示正确|
|Data - postId|帖子id|
|Data - postType|帖子类型：1文章，2视频|
|Data - title|帖子标题|
|Data - detailImg|封面图|
|Data - userId|用户id|
|Data - nickName|昵称|
|Data - profile|头像|
|Data - descrip|简介|
|Data - commentNum|评论数|
|Data - viewNum|浏览数|
|Data - likeNum|喜欢的人数|

<h2 id="2">2.推荐关注用户V4.0.0</h2>

请求方法：nggirl/app/cli/homePage/recommendUser/4.0.0

请求url：接口地址/nggirl/app/cli/homePage/recommendUser/4.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|pageNum|[可选]第几页，默认从0开始|
|pageSize|[可选]每页条数，默认为20|

请求示例：

> localhost/nggirl/app/cli/homePage/recommendUser/4.0.0

返回结果示例：
```json
{
  "code":0,
  "data":[
    {
      "userId":1,
      "profile":"",
      "nickName":""
    },
    {
      "userId":1,
      "profile":"",
      "nickName":""
    }
  ]
}
```
返回结果说明：

|字段名称|字段含义|
|----|----|
|Code|错误标识码，0表示正确|
|Data - userId|用户id|
|Data - profile|头像|
|Data - nickName|昵称|

<h2 id="3">3.美物V4.0.0</h2>

请求方法：nggirl/app/cli/homePage/itemList/4.0.0

请求url：接口地址/nggirl/app/cli/homePage/itemList/4.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|pageNum|[可选]第几页，默认从0开始|
|pageSize|[可选]每页条数，默认为20|

请求示例：

> http://localhost/nggirl/app/cli/homePage/itemList/4.0.0

返回结果示例：

```json
{
  "code":0,
  "data":{
    "newItems":[
      {
        "itemId":1,
        "imgUrl":"",
        "reamTitle":"",
        "salePrice":99
      },
      {
        "itemId":1,
        "imgUrl":"",
        "reamTitle":"",
        "salePrice":99
      }
    ],
    "recommendItems":[
      {
        "itemId":1,
        "imgUrl":"",
        "reamTitle":"",
        "salePrice":99
      },
      {
        "itemId":1,
        "imgUrl":"",
        "reamTitle":"",
        "salePrice":99
      }
    ]
  }
}
```

返回结果说明:

|字段名称|字段含义|
|----|----|
|Code|错误标识码，0表示正确|
|Data - newItems - itemId|新品推荐 - 商品id|
|Data - newItems - imgUrl|新品推荐 - 商品图片|
|Data - newItems - reamTitle|新品推荐 - 商品名称|
|Data - newItems - salePrice|新品推荐 - 售价|
|Data - recommendItems - itemId|为您推荐 - 商品id|
|Data - recommendItems - imgUrl|为您推荐 - 商品图片|
|Data - recommendItems - reamTitle|为您推荐 - 商品名称|
|Data - recommendItems - salePrice|为您推荐 - 售价|

<h2 id="4">4.标签对应帖子列表V4.0.0</h2>

请求方法：nggirl/app/cli/homePage/getLabelPostList/4.0.0

请求url：接口地址/nggirl/app/cli/homePage/getLabelPostList/4.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|label|【必填】标签名称|
|pageNum|[可选]第几页，默认从0开始|
|pageSize|[可选]每页条数，默认为20|

请求示例：

> http://localhost/nggirl/app/cli/homePage/getLabelPostList/4.0.0

返回结果示例：
```json
{
  "code":0,
  "data":[
    {
      "postId":1,
      "postType":1,
      "title":"",
      "detailImg":"",
      "userId":123,
      "nickName":"",
      "profile":"",
      "descrip":"",
      "commentNum":100,
      "viewNum":10000,
      "likeNum":200
    },
    {
      "postId":1,
      "postType":1,
      "title":"",
      "detailImg":"",
      "userId":123,
      "nickName":"",
      "profile":"",
      "descrip":"",
      "commentNum":100,
      "viewNum":10000,
      "likeNum":200
    }
  ]
}
```
返回结果说明：

|字段名称|字段含义|
|----|----|
|Code|错误标识码，0表示正确|
|Data - postId|帖子id|
|Data - postType|帖子类型：1文章，2视频|
|Data - title|帖子标题|
|Data - detailImg|封面图|
|Data - userId|用户id|
|Data - nickName|昵称|
|Data - profile|头像|
|Data - descrip|简介|
|Data - commentNum|评论数|
|Data - viewNum|浏览数|
|Data - likeNum|喜欢的人数|

<h2 id="5">5.获取控制标签V4.0.0</h2>

请求方法：nggirl/app/cli/homePage/getHomeLabelList/4.0.0

请求url：接口地址/nggirl/app/cli/homePage/getHomeLabelList/4.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：无


请求示例：

> http://localhost/nggirl/app/cli/homePage/getHomeLabelList/4.0.0

返回结果示例：
```json
{
  "code":0,
  "data":["种草","美妆","发型","瘦身"]
}
```

返回结果说明：

|字段名称|字段含义|
|----|----|
|Code|错误标识码，0表示正确|
|Data|标签列表|






