# 我的草稿箱V4.0.0

目录

---

* [1.获取草稿箱中帖子列表V4.0.0](#1)
* [2.批量删除草稿V2.5.4](#2)
* [3.获取文章帖子草稿详情V4.0.0](#3)
* [4.新增或编辑文章帖子草稿V4.0.0](#4)
* [5.发布帖子V4.0.0](#5)
* [6.获取商品详情V3.1.0](#6)
* [7.搜索可选商品列表V4.0.0](#7)
* [8.获取可选的专栏列表V3.0.0](#8)
* [9.获取可选的帖子标签V3.0.0](#9)
* [10.删除草稿箱中的帖子V3.0.0](#10)
* [11.我的发帖（我的日志）V3.0.0](#11)
* [12.获取可选的官方标签和热门话题标签V4.0.0](#12)


<h2 id="1">1.获取草稿箱中帖子列表V4.0.0</h2>

请求方法：nggirl/app/cli/draft/getPostList/4.0.0

请求url：接口地址/nggirl/app/cli/draft/getPostList/4.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]用户授权令牌|
|pageNum|[可选]第几页，默认从0开始|
|pageSize|[可选]每页条数，默认为20|

请求示例：

> http://localhost/nggirl/app/cli/draft/getPostList/4.0.0

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
          "updateTime":"2017-04-29"
      },
      {
          "postId":11,
          "postType":1,
          "title":"教你如何3分钟搞定范冰冰的大波浪",
          "detailImg":"",
          "descrip":"",
          "status":1,
          "updateTime":"2017-04-29"
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
|Data - updateTime|修改时间|



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


<h2 id="3">3.获取文章帖子草稿V4.0.0</h2>

请求方法：nggirl/app/cli/draft/getArticlePostDetail/4.0.0

请求url：接口地址/nggirl/app/cli/draft/getArticlePostDetail/4.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]用户授权令牌|
|postId|[必填]帖子编号|

请求示例：

> http://localhost/nggirl/app/cli/draft/getArticlePostDetail/4.0.0?postId=10&postType=1

返回结果示例：

```json
{
    "code":0,
    "data":{
        "postId":100,
        "postType":1,
        "title":"教你如何三分钟搞定范冰冰",
        "detailImg":"",
        "customLabels":["试用报告","瘦身","粉底"],
        "officialLabels":["保湿","瘦身","美白"],
        "topics":[
            {
                "topicId":1,
                "title":"",
                "talkNum":200
            },
            {
                "topicId":1,
                "title":"",
                "talkNum":200
            }
        ]
        "status":0,
        "article":[
            {
                "type":2,
                "content":"段落详情段落详情段落详情",
                "itemId":-1,
                "reamTitle":"",
                "imgUrl":"",
                "brandName":"",
                "country":"中国",
                "descrip":"",
                "extend":"",
                "isCover":0
            },
            {
                "type":3,
                "content":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
                "itemId":-1,
                "reamTitle":"",
                "imgUrl":"",
                "brandName":"",
                "country":"中国",
                "descrip":"根据设计需求，这里存放图片注释",
                "extend":"640_320",
                "isCover":0
            },
            {
                "type":5,
                "content":"1",
                "itemId":1,
                "reamTitle":"精美春装",
                "imgUrl":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
                "brandName":"倩碧",
                "country":"中国",
                "descrip":"",
                "extend":"",
                "isCover":0
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
|Data - title|帖子标题|
|Data - detailImg|头图|
|Data - customLabels|自定义标签|
|Data - officialLabels|官方标签|
|Data - topics|热门话题标签|
|Data - topics - topicId|热门话题id|
|Data - topics - title|标题|
|Data - topics - talkNum|参与讨论人数|
|Data - status|帖子状态，0草稿，1审核中，2审核通过、已上线|
|Data - article|文章|
|Data - article - type|元件类型。 1标题，2段落，3图片，4.图片注释，5商品详情，6妆品，暂时只有|
|Data - article - content|相关类型内容。1标题--标题文字，2段落--段落文字，3图片-图片url，4图片注释--注释文字，5商品编号-商品编号，6妆品编号-妆品编号|
|Data - article - descrip|相关类型的描述。1标题--空，2段落--空，3图片-图片注释，4图片注释--空，5商品详情-空，6妆品详情-空|
|Data - article - extend|扩展字段。1标题--空，2段落--空，3图片-宽\_高（640_320），4图片注释--空，5商品详情-空，，6妆品详情-空|
|Data - article - isCover|是否是封面图：0否，1是|
|Data - article - itemId|商品编号|
|Data - article - reamTitle|商品名称|
|Data - article - imgUrl|商品图|
|Data - article - brandName|品牌名称|
|Data - article - country|产地国家|


>注type=3时是图片，正常时descrip字段是没有值的

>但是根据最新的设计需求，需要将type=4的图片注释与type=3的图片整合到一块

>所以在此，会将type=4的图片注释内容直接放入图片的descrip字段


<h2 id="4">4.新增或编辑文章帖子草稿V4.0.0</h2>


请求方法：nggirl/app/cli/draft/saveArticlePost/4.0.0

请求url：接口地址/nggirl/app/cli/draft/saveArticlePost/4.0.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]用户授权令牌|
|postId|[可选]帖子id，如果是编辑已有的帖子，则必填|
|title|[可选]标题|
|detailImg|[可选]头图|
|customLabels|[可选]自定义帖子标签，JSON数组:["","",""]|
|officialLabels|[可选]官方帖子标签，JSON数组:["","",""]|
|article|[可选]文章详情，包裹副标题，段落，图片，图片注释（JSON格式的字符串），商品|
|topics|[可选]热门话题,JSON数组|

topics示例：
```json
[
    {
        "topicId":1,
        "title":"",
        "talkNum":100
    },
    {
        "topicId":1,
        "title":"",
        "talkNum":100
    },
    {
        "topicId":1,
        "title":"",
        "talkNum":100
    }   
]
```



article字段示例

```json
[
  {
    "type":2,
    "content":"段落详情段落详情",
    "descrip":"",
    "extend":"",
    "isCover":0
    },{
    "type":3,
    "content":"http://photosd.nggirl.com.cn/work/5873566f4257414c9cec9b4ff0b27635.png",
    "descrip":"根据设计需求，这里存放图片注释",
    "extend":"640_320",
    "isCover":0
  },{
  "type":5,
  "content":"1",
  "descrip":"",
  "extend":"",
  "isCover":0
  }
]
```

>type=5时，content是商品id

>type=3时是图片，正常时descrip字段是没有值的

>但是根据最新的设计需求，需要将type=4的图片注释与type=3的图片整合到一块

>所以在此，会将type=4的图片注释内容直接放入图片的descrip字段

> isCover是否是封面图：0否，1是

请求示例：

> http://localhost/nggirl/app/cli/draft/saveArticlePost/4.0.0

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



<h2 id="5">5.发布帖子V4.0.0</h2>


请求方法：nggirl/app/cli/draft/publishArticlePost/4.0.0

请求url：接口地址/nggirl/app/cli/draft/publishArticlePost/4.0.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]用户授权令牌|
|postId|[可选]帖子id，如果是编辑已有的帖子，则必填|
|title|[必填]标题|
|detailImg|[必填]头图|
|customLabels|[可选]自定义帖子标签，JSON数组:["","",""]|
|officialLabels|[必填]官方帖子标签，JSON数组:["","",""]|
|article|[可选]文章详情，包裹副标题，段落，图片，图片注释（JSON格式的字符串），商品|
|topics|[可选]热门话题,JSON数组|

topics示例：
```json
[
    {
        "topicId":1,
        "title":"",
        "talkNum":100
    },
    {
        "topicId":1,
        "title":"",
        "talkNum":100
    },
    {
        "topicId":1,
        "title":"",
        "talkNum":100
    }   
]
```
article字段示例

```json
[
  {
    "type":2,
    "content":"段落详情段落详情",
    "descrip":"",
    "extend":"",
    "isCover":0
  },{
    "type":3,
    "content":"http://photosd.nggirl.com.cn/work/5873566f4257414c9cec9b4ff0b27635.png",
    "descrip":"根据设计需求，这里存放图片注释",
    "extend":"640_320",
    "isCover":0
  },{
  "type":5,
  "content":"1",
  "descrip":"",
  "extend":"",
  "isCover"
  }
]
```

>type=5时，content是商品id

>type=3时是图片，正常时descrip字段是没有值的

>但是根据最新的设计需求，需要将type=4的图片注释与type=3的图片整合到一块

>所以在此，会将type=4的图片注释内容直接放入图片的descrip字段

> isCover是否是封面图：0否，1是

请求示例：

> http://localhost/nggirl/app/cli/draft/publishArticlePost/4.0.0

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

<h2 id="6">6.获取商品详情V3.1.0</h2>

>出参添加productDetailType

请求方法：nggirl/app/cli/draft/getSeedProductDetail/3.1.0

请求url：接口地址/nggirl/app/cli/draft/getSeedProductDetail/3.1.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]用户授权令牌|
|seedProductId|[必填]商品id|
|pageNum|第几页，|
|pageSize||

请求示例：

> http://localhost/nggirl/app/cli/draft/getSeedProductDetail/3.1.0

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
      "brandDesc":"暂无",
      "productDetailType":1
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
|Data - productDetailType|跳转商品详情类型，1老版本商品种草页面，2新版本商品详情页面|


<h2 id="7">7.搜索可选商品列表V4.0.0</h2>

请求方法：nggirl/app/cli/draft/getSeedProductList/4.0.0

请求url：接口地址/nggirl/app/cli/draft/getSeedProductList/4.0.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]用户授权令牌|
|keyWords|[必填]搜索关键字|
|pageNum|第几页，默认从0开始|
|pageSize|每页多少条，默认20|



请求示例：

> http://localhost/nggirl/app/cli/draft/getSeedProductList/4.0.0

返回结果示例：

```json
{
    "code":0,
    "data":[
        {
            "itemId":1,
            "reamTitle":"商品名称1",
            "imgUrl":"http://photosd.nggirl.com.cn/work/c9138c508f5d49f0afddf324c9097f3a.png",
            "brandName":"碧欧泉",
            "country":"法国"
        },
        {
            "itemId":2,
            "reamTitle":"商品名称2",
            "imgUrl":"http://photosd.nggirl.com.cn/work/c9138c508f5d49f0afddf324c9097f3a.png",
            "brandName":"碧欧泉",
            "country":"法国"
        }
    ]
}
```

返回结果说明：

|字段名称|字段含义|
|----|----|
|Code|错误标识码，0标识正确|
|Data - itemId|商品编号|
|Data - reamTitle|商品名称|
|Data - imgUrl|商品图|
|Data - brandName|品牌名称|
|Data - country|所属国家|


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


<h2 id="12">12.获取可选的官方标签和热门话题标签V4.0.0</h2>


请求方法：nggirl/app/cli/draft/getOfficialAndHotTopicLabels/4.0.0

请求url：接口地址/nggirl/app/cli/draft/getOfficialAndHotTopicLabels/4.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|----|----|
|accessToken|[必填]用户授权令牌|
|topicId|【选填】热门话题id|
|title|【选填】热门话题标题|

请求示例：

> http://localhost/nggirl/app/cli/draft/getOfficialAndHotTopicLabels/4.0.0

返回结果示例：
```json
{
  "code":0,
  "data":{
    "officialLabels":["美妆","种草","护肤","发型","瘦身"],
    "topicLabels":[
      {
        "topicId":1,
        "title":"秒变大眼妆",
        "talkNum":"99"
      },
      {
        "topicId":2,
        "title":"我的空瓶记",
        "talkNum":"99"
      },
      {
        "topicId":3,
        "title":"最美不过口红控",
        "talkNum":"99"
      }
    ]
  }
}
```
返回结果说明：

|字段名称|字段含义|
|---|---|
|Code|错误标识码，0表示正确|
|Data - officialLabels|官方标签|
|Data - topicLabels - topicId|话题id|
|Data - topicLabels - title|话题标题|
|Data - topicLabels - talkNum|参与次数|


