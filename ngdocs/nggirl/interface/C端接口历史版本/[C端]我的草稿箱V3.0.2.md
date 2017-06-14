# 我的草稿箱V3.0.2

目录

---

* [1.获取草稿箱中帖子列表V3.0.0](#1)
* [2.批量删除草稿V2.5.4](#2)
* [3.获取文章帖子草稿V3.0.0](#3)
* [4.新增或编辑文章帖子草稿V3.0.2](#4)
* [5.发布帖子V3.0.2](#5)
* [6.获取商品详情V2.5.4](#6)
* [7.查询可选商品列表V2.5.4](#7)
* [8.获取可选的专栏列表V3.0.0](#8)
* [9.获取可选的帖子标签V3.0.0](#9)
* [10.删除草稿箱中的帖子V3.0.0](#10)
* [11.我的发帖（我的日志）V3.0.0](#11)


<h2 id="1">1.获取草稿箱中帖子列表V3.0.0</h2>

请求方法：nggirl/app/cli/draft/getPostList/3.0.0

请求url：接口地址/nggirl/app/cli/draft/getPostList/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]用户授权令牌|
|pageNum|[可选]第几页，默认从0开始|
|pageSize|[可选]每页条数，默认为20|

请求示例：

> http://localhost/nggirl/app/cli/draft/getPostList/3.0.0

返回结果示例：

```json
{
    "code":0,
    "data":[
      {
          "postId":10,
          "postType":1,
          "title":"教你如何3分钟搞定范冰冰的大波浪",
          "detailImg":"",
          "descrip":"",
          "status":1,
          "userId":1,
          "nickName":"ghhahha",
          "profile":"",
          "userLevel":1
      },
      {
          "postId":11,
          "postType":1,
          "title":"教你如何3分钟搞定范冰冰的大波浪",
          "detailImg":"",
          "descrip":"",
          "status":1,
          "userId":1,
          "nickName":"",
          "profile":"",
          "userLevel":1
      }
    ]
}
```

返回字段说明：

|字段名|字段含义|
|---|---|
|Code|错误码,0表示正确|
|Data - postId|帖子编号|
|Data - postType|帖子类型 1为文章，2为视频|
|Data - title|帖子标题|
|Data - detailImg|头图|
|Data - descrip|描述|
|Data - status|帖子状态，0草稿，1审核中，2审核通过、已上线|
|Data - userId|用户编号|
|Data - nickName|用户昵称|
|Data - profile|用户头像|
|Data - userLevel|用户等级 0-Lv0，1-Lv1,2-Lv2...


<h2 id="2">2.批量删除草稿V2.5.4</h2>

请求方法：nggirl/app/cli/draft/deleteDraftPosts/2.5.4

请求url：接口地址/nggirl/app/cli/draft/deleteDraftPosts/2.5.4

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]用户授权令牌|
|postIds|[必填]帖子id，Json数组形式|

>postIds字段示例

```json
[1,2,3,4,5]
```


请求示例：

> http://localhost/app/cli/draft/deleteDraftPosts/2.5.4

返回结果示例：

```json
{
  "code":0,
  "data":null
}
```

返回字段说明：

|字段名称|字段含义|
|---|---|
|Code |错误码，0表示正确|


<h2 id="3">3.获取文章帖子草稿V3.0.0</h2>

请求方法：nggirl/app/cli/draft/getArticlePostDetail/3.0.0

请求url：接口地址/nggirl/app/cli/draft/getArticlePostDetail/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]用户授权令牌|
|postId|[必填]帖子编号|

请求示例：

> http://localhost/nggirl/app/cli/draft/getArticlePostDetail/3.0.0?postId=10&postType=1

返回结果示例：

```json
{
    "code":0,
    "data":{
        "postId":100,
        "postType":1,
        "columnId":1,
        "columnName":"护肤心机",
        "title":"教你如何三分钟搞定范冰冰",
        "detailImg":"",
        "labels":["试用报告","瘦身","粉底"],
        "status":0,
        "article":[
            {
                "type":2,
                "content":"段落详情段落详情段落详情",
                "seedProductId":-1,
                "name":"",
                "picture":"",
                "price":0,
                "seedNum":0,
                "recommendation":5,
                "descrip":"",
                "extend":""
            },
            {
                "type":3,
                "content":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
                "seedProductId":-1,
                "name":"",
                "picture":"",
                "price":0,
                "seedNum":0,
                "recommendation":5,
                "descrip":"根据设计需求，这里存放图片注释",
                "extend":"640_320"
            },
            {
                "type":5,
                "content":"1",
                "seedProductId":1,
                "name":"精美春装",
                "picture":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
                "price":20,
                "seedNum":90,
                "recommendation":5,
                "descrip":"",
                "extend":""
            }
        ]
    }
}
```


返回字段说明：

|字段名称|字段含义|
|---|---|
|Data - postId|帖子编号|
|Data - postType|帖子类型 1为文章，2为视频|
|Data - columnId|专栏编号|
|Data - columnName|专栏名称|
|Data - title|帖子标题|
|Data - detailImg|头图|
|Data - labels|标签，JSON数组|
|Data - status|帖子状态，0草稿，1审核中，2审核通过、已上线|
|Data - article|文章|
|Data - article - type|元件类型。 1标题，2段落，3图片，4.图片注释，5商品详情，6妆品，暂时只有|
|Data - article - content|相关类型内容。1标题--标题文字，2段落--段落文字，3图片-图片url，4图片注释--注释文字，5商品编号-商品编号，6妆品编号-妆品编号|
|Data - article - descrip|相关类型的描述。1标题--空，2段落--空，3图片-图片注释，4图片注释--空，5商品详情-空，6妆品详情-空|
|Data - article - extend|扩展字段。1标题--空，2段落--空，3图片-宽\_高（640_320），4图片注释--空，5商品详情-空，，6妆品详情-空|
|Data - article - seedProductId|商品编号|
|Data - article - name|商品名称|
|Data - article - picture|商品图|
|Data - article - price|价格|
|Data - article - seedNum|种草人数|
|Data - article - recommendation|推荐度，0-10|

>注type=3时是图片，正常时descrip字段是没有值的

>但是根据最新的设计需求，需要将type=4的图片注释与type=3的图片整合到一块

>所以在此，会将type=4的图片注释内容直接放入图片的descrip字段


<h2 id="4">4.新增或编辑文章帖子草稿V3.0.2</h2>

>出参增加addScore字段

请求方法：nggirl/app/cli/draft/saveArticlePost/3.0.2

请求url：接口地址/nggirl/app/cli/draft/saveArticlePost/3.0.2

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]用户授权令牌|
|postId|[可选]帖子id，如果是编辑已有的帖子，则必填|
|columnId|[可选]专栏编号|
|title|[可选]标题|
|detailImg|[可选]头图，如果用户没有上传该图片，我们在后台会默认保存一张设计给的一张默认图片|
|labels|[可选]帖子标签，JSON数组，至少一个标签，最多五个标签|
|article|[可选]文章详情，包裹副标题，段落，图片，图片注释（JSON格式的字符串），商品|
|topicId|[可选]话题编号，如果是在话题下发帖，则传入，否则不传|

article字段示例

```json
[
  {
    "type":2,
    "content":"段落详情段落详情",
    "descrip":"",
    "extend":""
  },{
    "type":3,
    "content":"http://photosd.nggirl.com.cn/work/5873566f4257414c9cec9b4ff0b27635.png",
    "descrip":"根据设计需求，这里存放图片注释",
    "extend":"640_320"
  },{
  "type":5,
  "content":"1",
  "descrip":"",
  "extend":""
  }
]
```

>type=5时，content是商品id

>type=3时是图片，正常时descrip字段是没有值的

>但是根据最新的设计需求，需要将type=4的图片注释与type=3的图片整合到一块

>所以在此，会将type=4的图片注释内容直接放入图片的descrip字段

请求示例：

> http://localhost/nggirl/app/cli/draft/saveArticlePost/3.0.2

返回结果示例：

```json
{
    "code":0,
    "data":{
      "postId":1,
      "addScore":0
    }
}
```

返回结果说明：

|字段名称|字段含义|
|---|---|
|Code|错误标识码，0表示正确|
|Data - postId|帖子id|
|Data - addScore|用户本次操作增加的积分数|

<h2 id="5">5.发布帖子V3.0.2</h2>

>出参增加addScore字段

请求方法：nggirl/app/cli/draft/publishArticlePost/3.0.2

请求url：接口地址/nggirl/app/cli/draft/publishArticlePost/3.0.2

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]用户授权令牌|
|postId|[可选]帖子id，如果是编辑已有的帖子，则必填|
|columnId|[必填]专栏编号|
|title|[必填]标题|
|detailImg|[必填]头图|
|labels|[必填]帖子标签，JSON数组，至少一个标签，最多五个标签|
|article|[可选]文章详情，包裹副标题，段落，图片，图片注释（JSON格式的字符串），商品|
|topicId|话题编号，如果是在话题下发帖，则传入，否则不传|

article字段示例

```json
[
  {
    "type":2,
    "content":"段落详情段落详情",
    "descrip":"",
    "extend":""
  },{
    "type":3,
    "content":"http://photosd.nggirl.com.cn/work/5873566f4257414c9cec9b4ff0b27635.png",
    "descrip":"根据设计需求，这里存放图片注释",
    "extend":"640_320"
  },{
  "type":5,
  "content":"1",
  "descrip":"",
  "extend":""
  }
]
```

>type=5时，content是商品id

>type=3时是图片，正常时descrip字段是没有值的

>但是根据最新的设计需求，需要将type=4的图片注释与type=3的图片整合到一块

>所以在此，会将type=4的图片注释内容直接放入图片的descrip字段

请求示例：

> http://localhost/nggirl/app/cli/draft/publishArticlePost/3.0.2

返回结果示例：

```json
{
    "code":0,
    "data":{
      "postId":1,
      "addScore":0
    }
}
```

返回结果说明：

|字段名称|字段含义|
|---|---|
|Code|错误标识码，0表示正确|
|Data - postId|帖子id|
|Data - addScore|用户本次操作增加的积分数|

<h2 id="6">6.获取商品详情V2.5.4</h2>

请求方法：nggirl/app/cli/draft/getSeedProductDetail/2.5.4

请求url：接口地址/nggirl/app/cli/draft/getSeedProductDetail/2.5.4

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]用户授权令牌|
|seedProductId|[必填]商品id|


请求示例：

> http://localhost/nggirl/app/cli/draft/getSeedProductDetail/2.5.4

返回结果示例：

```json
{
    "code":0,
    "data":{
      "seedProductId":1,
      "name":"锐澳BB霜",
      "picture":"http://photosd.nggirl.com.cn/work/c9138c508f5d49f0afddf324c9097f3a.png",
      "price":100,
      "seedNum":50,
      "recommendation":9,
      "productDesc":"敷一次一天都水嫩嫩。。。。",
      "detailImg":"http://photosd.nggirl.com.cn/work/c9138c508f5d49f0afddf324c9097f3a.png",
      "country":"法国",
      "brand":"锐澳",
      "brandImg":"http://photosd.nggirl.com.cn/work/c9138c508f5d49f0afddf324c9097f3a.png",
      "brandDesc":"暂无"
    }
}
```

返回结果说明：

|字段名称|字段含义|
|---|---|
|Code|错误标识码，0表示正确|
|Data - seedProductId|商品编号|
|Data - name|商品名称|
|Data - picture|商品小图|
|Data - price|价格|
|Data - seedNum|采集人数|
|Data - recommendation|推荐度，0-10|
|Data - productDesc |商品介绍|
|Data - detailImg|商品详情头图|
|Data - country|商品所属国家|
|Data - brand|商品品牌|
|Data - brandImg|品牌图片|
|Data - brandDesc|品牌描述|


<h2 id="7">7.查询可选商品列表V2.5.4</h2>

请求方法：nggirl/app/cli/draft/getSeedProductList/2.5.4

请求url：接口地址/nggirl/app/cli/draft/getSeedProductList/2.5.4

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]用户授权令牌|
|keyWords|[必填]搜索关键字|
|pageNum|[可选]第几页，默认从0开始|
|pageSize|[可选]每页条数，默认为10|


请求示例：

> http://localhost/nggirl/app/cli/draft/getSeedProductList/2.5.4

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
            "recommendation":5
        },
        {
            "seedProductId":2,
            "name":"商品名称2",
            "picture":"http://photosd.nggirl.com.cn/work/c9138c508f5d49f0afddf324c9097f3a.png",
            "price":1209,
            "seedNum":32,
            "recommendation":5
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
|Data - recommendation|推荐度，0-10|



<h2 id="8">8.获取可选的专栏列表V3.0.0</h2>

请求方法：nggirl/app/cli/draft/getOptionalColumn/3.0.0

请求url：接口地址/nggirl/app/cli/draft/getOptionalColumn/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：无


请求示例：

> http://localhost/nggirl/app/cli/draft/getOptionalColumn/3.0.0

返回结果示例：
```json
{
  "code":0,
  "data":[
    {
      "columnId":1,
      "columnName":"护肤心机"
    },
    {
      "columnId":2,
      "columnName":"种草间"
    },
    {
      "columnId":3,
      "columnName":"发型空间"
    }
  ]
}
```

返回字段说明：

|字段名称|字段含义|
|---|----|
|Code|错误标识码，0表示正确|
|Data - columnId|专栏编号|
|Data - columnName|专栏名称|



<h2 id="9">9.获取可选的帖子标签V3.0.0</h2>

请求方法：nggirl/app/cli/draft/getOptionalLabels/3.0.0

请求url：接口地址/nggirl/app/cli/draft/getOptionalLabels/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：无


请求示例：

> http://localhost/nggirl/app/cli/draft/getOptionalLabels/3.0.0

返回结果示例：
```json
{
  "code":0,
  "data":[
    {
      "className":"美妆标签",
      "labels":[
        {
            "marked":0,
            "name":"护肤"
        },
        {
            "marked":0,
            "name":"美白"
        },
        {
            "marked":0,
            "name":"缺水"
        }
      ]
    },
    {
      "className":"热门标签",
      "labels":[
        {
            "marked":0,
            "name":"护肤"
        },
        {
            "marked":0,
            "name":"美白"
        },
        {
            "marked":0,
            "name":"缺水"
        }
      ]
    },
    {
      "className":"明星标签",
      "labels":[
        {
            "marked":0,
            "name":"护肤"
        },
        {
            "marked":0,
            "name":"美白"
        },
        {
            "marked":0,
            "name":"缺水"
        }
       ]
    }
  ]
}
```
返回结果说明：

|字段名称|字段含义|
|----|----|
|Code|错误标识码，0标识正确|
|Data - className|标签类别|
|Data - labels - marked|是否被标记：0未被标记，1被标记，用户前端标记试用|
|Data - labels - name|标签名字|


<h2 id="10">10.删除草稿箱中的帖子V3.0.0</h2>

请求方法：nggirl/app/cli/draft/deletePost/3.0.0

请求url：接口地址/nggirl/app/cli/draft/deletePost/3.0.0

支持格式：JSON

HTTP请求方式：PSOT

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]授权令牌|
|postType|[必填]帖子类型：1文章2视频|
|postId|[必填]帖子编号|


请求示例：

> http://localhost/nggirl/app/cli/draft/deletePost/3.0.0

返回结果说明：

|字段名称|字段含义|
|---|---|
|Code|错误标识码，0标识正确|
|Data|null|



<h2 id="11">11.我的发帖（我的日志）V3.0.0</h2>

请求方法：nggirl/app/cli/draft/myPublishPost/3.0.0

请求url：接口地址/nggirl/app/cli/draft/myPublishPost/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]用户授权令牌|
|pageNum|[可选]第几页，默认从0开始|
|pageSize|[可选]每页条数，默认为20|

请求示例：

> http://localhost/nggirl/app/cli/draft/myPublishPost/3.0.0

返回结果示例：
```json
{
  "code": 0,
  "data": {
    "postNum": 10,
    "postList": [
      {
        "postId": 1,
        "postType": 1,
        "detailImg": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
        "userId": 269,
        "nickName": "尼克",
        "profile": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
        "userRole": "官方",
        "userLevel": 1,
        "title": "兰蔻 玫瑰菁纯柔润唇膏口红唇彩",
        "descrip": "这款精华我用了30ML的一瓶。用后角质层修复效果极佳，脸部特别软。兑在乳液、精华、面膜、粉底都可以。完全百搭百搭百搭！重点是完全不油腻！抗过敏效",
        "columnId": 1,
        "columnName": "美妆课堂",
        "commentNum": 100,
        "likeNum": 200,
        "viewNum": 1000,
        "status": 2,
        "isEssential": 1
      },
      {
        "postId": 2,
        "postType": 1,
        "detailImg": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
        "userId": 269,
        "nickName": "小清新",
        "profile": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
        "userRole": "官方",
        "userLevel": 1,
        "title": "兰蔻 玫瑰菁纯柔润唇膏口红唇彩",
        "descrip": "这款精华我用了30ML的一瓶。用后角质层修复效果极佳，脸部特别软。兑在乳液、精华、面膜、粉底都可以。完全百搭百搭百搭！重点是完全不油腻！抗过敏效",
        "columnId": 1,
        "columnName": "美妆课堂",
        "commentNum": 100,
        "likeNum": 200,
        "viewNum": 1000,
        "status": 1,
        "isEssential": 1
      }
    ]
  }
}
```
返回字段说明：

|字段名称|字段含义|
|----|----|
|Code|错误标识码，0表示正确|
|Data - postNum|帖子数量|
|Data - postList - postId|帖子编号|
|Data - postList - postType|帖子类型：1文章2视频|
|Data - postList - columnId|专栏编号|
|Data - postList - columnName|专栏名称|
|Data - postList - title|标题|
|Data - postList - detailImg|头图|
|Data - postList - descrip|描述|
|Data - postList - status|状态：0草稿，1已发布待审核，2审核通过|
|Data - postList - userId|用户编号|
|Data - postList - profile|用户头像|
|Data - postList - nickName|用户昵称|
|Data - postList - userLevel|用户等级：0Lv0,1Lv1,2Lv2...|
|Data - postList - commentNum|评论数|
|Data - postList - viewNum|浏览数|
|Data - postList - likeNum|喜欢的人数|
|Data - postList - userRole|用户角色|
|Data - postList - isEssential|是否加精帖，1是，0否|
