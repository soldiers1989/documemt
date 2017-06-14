# 帖子列表以及详情V2.5.0

目录
---

* [1.首页专栏帖子列表V2.0.0](#1)
* [2.某一专栏对应帖子列表V2.0.0](#2)
* [3.视频帖子详情V2.4.2](#3)
* [4.文章帖子详情V2.4.2](#4)
* [5.获取标签对应的帖子列表V2.2.0](#5)
* [6.商品详情V2.5.0](#6)




<h2 id="1">1.首页帖子列表V2.0.0</h2>

请求方法：nggirl/app/cli/column/getPostList/2.0.0

请求url：接口地址/nggirl/app/cli/column/getPostList/2.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|pageNum|第几页，默认从0开始（非必填）|
|pageSize|每页条数，默认为5（非必填）|

请求示例：
> http://localhost/nggirl/app/cli/column/getPostList/V2.0.0

返回结果示例：
```json
{
    "code":0,
    "data":[
        {   
            "id":1,
            "name":"种草间",
            "bgimg":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
            "hasMore":1,
            "posts":[
                {
                    "postId":10,
                    "title":"教你如何3分钟搞定范冰冰的大波浪",
                    "postType":1,
                    "picture":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
                    "viewNum":1234,
                    "commentNum":200
                },
                {
                    "postId":11,
                    "title":"教你如何3分钟搞定范冰冰的大波浪",
                    "postType":1,
                    "picture":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
                    "viewNum":1234,
                    "commentNum":200
                }
            ]
        },
        {
            "id":2,
            "name":"美妆教程",
            "bgimg":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
            "hasMore":0,
            "posts":[
                {
                    "postId":10,
                    "title":"教你如何3分钟搞定范冰冰的大波浪",
                    "postType":1,
                    "picture":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
                    "viewNum":1234,
                    "commentNum":200
                },
                {
                    "postId":12,
                    "title":"教你如何3分钟搞定范冰冰的大波浪",
                    "postType":1,
                    "picture":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
                    "viewNum":1234,
                    "commentNum":200
                }
            ]
        }

    ]
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code|错误码,0表示正确|
|Data - id|专栏编号|
|Data - name|专栏名字|
|Data - bgimg|专栏背景图片|
|Data - hasMore|是否有更多 0否，1是|
|Data - posts|帖子列表|
|Data - posts - postId|帖子编号|
|Data - posts - title|帖子标题|
|Data - posts - postType|帖子类型 1为文章，2为视频|
|Data - posts - picture|帖子配图|
|Data - posts - viewNum|浏览数量|
|Data - posts - commentNum|评论数量|


<h2 id="2">2.某一专栏对应帖子列表V2.0.0</h2>

请求方法：nggirl/app/cli/column/getPostListByColumn/2.0.0

请求url：接口地址/nggirl/app/cli/column/getPostListByColumn/2.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|columnId|专栏编号|
|pageNum|第几页，默认从0开始（非必填）|
|pageSize|每页条数，默认为10（非必填）|

请求示例：
> http://localhost/app/cli/column/getPostListByColumn/2.0.0?columnId=1

返回结果示例：
```json
{
    "code":0,
    "data":[
        {   
            "postId":1,
            "postType":1,
            "title":"教你如何3分钟搞定范冰冰的大波浪",
            "picture":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
            "viewNum":123,
            "commentNum":2000
        },
        {   
            "postId":2,
            "postType":2,
            "title":"教你如何3分钟搞定范冰冰的大波浪",
            "picture":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
            "viewNum":123,
            "commentNum":2000
        },
        {   
            "postId":3,
            "postType":2,
            "title":"教你如何3分钟搞定范冰冰的大波浪",
            "picture":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
            "viewNum":123,
            "commentNum":2000
        }
    ]
}
```
返回字段说明：

|字段名称|字段含义|
|---|---|
|Code |错误码，0表示正确|
|Data - postId|帖子编号|
|Data - postType|帖子类型 1为文章，2为视频|
|Data - title|帖子标题|
|Data - picture|配图|
|Data - viewNum|浏览数量|
|Data - commentNum|评论数量|

<h2 id="3">3.视频帖子详情V2.4.2</h2>

> 去掉brief，添加字段商品推荐度recommendation,字段productDetails -> videoDetail


请求方法：nggirl/app/cli/post/getVideoPostDetail/2.4.2

请求url：接口地址/nggirl/app/cli/post/getVideoPostDetail/2.4.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|用户授权令牌（非必填,登录时必填）|
|postId|帖子编号（必填）|
|postType|帖子类型（必填）|

请求示例：
> http://localhost/nggirl/app/cli/post/getVideoPostDetail/2.4.2?postId=10&postType=2

返回结果示例：
```json
{
    "code":0,
    "data":{
        "postId":10,
        "postType":1,
        "columnName":"种草间",
        "title":"教你如何3分钟搞定范冰冰大波浪",
        "picture":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
        "videoUrl":"http://testphotosd.nggirl.com.cn/work/66d7b2a54e994abebe3f0fde075d977c.jpg",
        "videoId":"dsfdsfjkljlsa",
        "viewNum":1234,
        "commentNum":200,
        "createTime":1320718222932,
        "createUserId":10,
        "userProfile":"http://wx.qlogo.cn/mmopen/H9XkvMl38uDrDibLNp5Tqr5ckUVonlTKISh2LGjU6jcldPnssiatSjtR7PSOVGdAtyKAUicqXvEwLiaFCtGfmxUqocGhKeEYEicPj/0",
        "userName":"小可爱",
        "userRole":"南瓜小编",
        "isPraised":0,
        "isCollected":1,
        "labels":[
          "美白",
          "欧美系口红",
          "种草"
        ],
        "loverCount":2,
        "lovers":[
          {
            "loverUserId":269,
            "loverProfile":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
          },
          {
            "loverUserId":269,
            "loverProfile":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
          }
        ],
        "isNoTalk":0,
        "noTalkTime":"2016年07月10日 00:00:00",
        "videoDetail":[
            {
              "type":5,
              "content":"1",
              "seedProductId":1,
              "name":"精美春装",
              "picture":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
              "price":20,
              "seedNum":90,
              "isSeed":0,
              "recommendation":5,
              "descrip":"",
              "extend":""
            },
            {
              "type":5,
              "content":"1",
              "seedProductId":1,
              "name":"精美春装",
              "picture":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
              "price":20,
              "seedNum":90,
              "isSeed":0,
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
|Code |错误码，0表示正确|
|Data - postId|帖子编号|
|Data - postType|帖子类型 1为文章，2为视频|
|Data - columnName|专栏名称|
|Data - title|帖子标题|
|Data - picture|配图|
|Data - videoUrl|视频地址|
|Data - videoId|视频编号（用于视频播放，由乐视后台生成）|
|Data - viewNum|浏览数量|
|Data - commentNum|评论数量|
|Data - createTime|创建时间|
|Data - createUserId|创建用户编号|
|Data - userProfile|用户头像|
|Data - userName|用户昵称|
|Data - userRole|用户角色|
|Data - isPraised|是否已点赞 0未点赞，1已点赞|
|Data - isCollected|是否已收藏 0未收藏，1已收藏|
|Data - labels|帖子标签
|Data - loverCount|喜欢的人数|
|Data - lovers - loverUserId|用户编号|
|Data - lovers - loverProfile|用户头像|
|Data - isNoTalk|是否禁言 0未禁言，1已禁言|
|Data - noTalkTime|禁言截止时间 格式："yyyy年MM月dd日 HH:mm:ss"|
|Data - videoDetail|帖子详情|
|Data - videoDetail - type|元件类型，5商品|
|Data - videoDetail - content|5商品编号-商品编号|
|Data - videoDetail - descrip|描述-空|
|Data - videoDetail - extend|扩展字段-空|
|Data - videoDetail - seedProductId|商品编号|
|Data - videoDetail - name|商品名称|
|Data - videoDetail - picture|商品图|
|Data - videoDetail - price|价格|
|Data - videoDetail - seedNum|种草人数|
|Data - videoDetail - isSeed|是否已种草，0未种草，1已种草|
|Data - videoDetail - recommendation|推荐度，0-10|



<h2 id="4">4.文章帖子详情V2.4.2</h2>

> 去掉brief 添加字段商品推荐度recommendation，增加type=6的时，增加字段workId，workPhoto，workName，workCost，workPrice，workIsCollected，collectNum。articleType -> type

请求方法：nggirl/app/cli/post/getArticlePostDetail/2.4.2

请求url：接口地址/nggirl/app/cli/post/getArticlePostDetail/2.4.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|用户授权令牌（非必填，登录时必填）|
|postId|帖子编号（必填）|
|postType|帖子类型（必填）|

请求示例：
> http://localhost/nggirl/app/cli/post/getArticlePostDetail/2.4.2?postId=10&postType=1

返回结果示例：
```json
{
    "code":0,
    "data":{
        "postId":100,
        "postType":1,
        "columnName":"种草间",
        "title":"教你如何三分钟搞定范冰冰",
        "picture":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
        "viewNum":1234,
        "commentNum":200,
        "createTime":1320718222932,
        "createUserId":156,
        "userProfile":"http://wx.qlogo.cn/mmopen/H9XkvMl38uDrDibLNp5Tqr5ckUVonlTKISh2LGjU6jcldPnssiatSjtR7PSOVGdAtyKAUicqXvEwLiaFCtGfmxUqocGhKeEYEicPj/0",
        "userName":"小可爱",
        "userRole":"南瓜小编",
        "isPraised":1,
        "isCollected":0,
        "article":[
            {
                "type":1,
                "content":"副标题",
                "seedProductId":-1,
                "name":"",
                "picture":"",
                "price":-1,
                "seedNum":-1,
                "isSeed":-1,
                "recommendation":5,
                "descrip":"",
                "extend":"",
                "workId":2,
                "workPhoto":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
                "workName":"少女情怀",
                "workCost":20,
                "workPrice":10,
                "workIsCollected":1,
                "collectNum":55
            },
            {
                "type":2,
                "content":"段落详情段落详情段落详情",
                "seedProductId":-1,
                "name":"",
                "picture":"",
                "price":-1,
                "seedNum":-1,
                "isSeed":-1,
                "recommendation":5,
                "descrip":"",
                "extend":"",
                "workId":2,
                "workPhoto":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
                "workName":"少女情怀",
                "workCost":20,
                "workPrice":10,
                "workIsCollected":1,
                "collectNum":55
            },
            {
                "type":3,
                "content":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
                "seedProductId":-1,
                "name":"",
                "picture":"",
                "price":-1,
                "seedNum":-1,
                "isSeed":-1,
                "recommendation":5,
                "descrip":"",
                "extend":"640_320",
                "workId":2,
                "workPhoto":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
                "workName":"少女情怀",
                "workCost":20,
                "workPrice":10,
                "workIsCollected":1,
                "collectNum":55
            },
            {
                "type":4,
                "content":"图片注释图片注释图片注释",
                "seedProductId":-1,
                "name":"",
                "picture":"",
                "price":-1,
                "seedNum":-1,
                "isSeed":-1,
                "recommendation":5,
                "descrip":"",
                "extend":"",
                "workId":2,
                "workPhoto":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
                "workName":"少女情怀",
                "workCost":20,
                "workPrice":10,
                "workIsCollected":1,
                "collectNum":55
            },
            {
                "type":5,
                "content":"1",
                "seedProductId":1,
                "name":"精美春装",
                "picture":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
                "price":20,
                "seedNum":90,
                "isSeed":0,
                "recommendation":5,
                "descrip":"",
                "extend":"",
                "workId":2,
                "workPhoto":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
                "workName":"少女情怀",
                "workCost":20,
                "workPrice":10,
                "workIsCollected":1,
                "collectNum":55
            },
            {
                "type":6,
                "content":"1",
                "seedProductId":1,
                "name":"精美春装",
                "picture":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
                "price":20,
                "seedNum":90,
                "isSeed":0,
                "recommendation":5,
                "descrip":"",
                "extend":"",
                "workId":2,
                "workPhoto":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
                "workName":"少女情怀",
                "workCost":20,
                "workPrice":10,
                "workIsCollected":1,
                "collectNum":55
            }
        ],
        "labels":[
          "美白",
          "欧美系口红",
          "种草"
        ],
        "loverCount":2,
        "lovers":[
          {
            "loverUserId":269,
            "loverProfile":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
          },
          {
            "loverUserId":269,
            "loverProfile":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
          }
        ],
        "isNoTalk":0,
        "noTalkTime":"2016年07月10日 00:00:00"
    }
}
```


返回字段说明：

|字段名称|字段含义|
|---|---|
|Data - postId|帖子编号|
|Data - postType|帖子类型 1为文章，2为视频|
|Data - columnName|专栏名称|
|Data - title|帖子标题|
|Data - picture|配图|
|Data - viewNum|浏览数量|
|Data - commentNum|评论数量|
|Data - createUserId|创建用户编号|
|Data - userProfile|用户头像|
|Data - userName|用户昵称|
|Data - userRole|用户角色|
|Data - isPraised|是否已点赞 0未点赞，1已点赞|
|Data - isCollected|是否已收藏 0未收藏，1已收藏|
|Data - article|文章|
|Data - article - type|元件类型。 1标题，2段落，3图片，4.图片注释，5商品详情，6妆品|
|Data - article - content|相关类型内容。1标题--标题文字，2段落--段落文字，3图片-图片url，4图片注释--注释文字，5商品编号-商品编号，6妆品编号-妆品编号|
|Data - article - descrip|相关类型的描述。1标题--空，2段落--空，3图片-空，4图片注释--空，5商品详情-空，6妆品详情-空|
|Data - article - extend|扩展字段。1标题--空，2段落--空，3图片-宽\_高（640_320），4图片注释--空，5商品详情-空，，6妆品详情-空|
|Data - article - seedProductId|商品编号|
|Data - article - name|商品名称|
|Data - article - picture|商品图|
|Data - article - price|价格|
|Data - article - seedNum|种草人数|
|Data - article - isSeed|是否已种草，0未种草，1已种草|
|Data - article - recommendation|推荐度，0-10|
|Data - article - workId|妆品编号|
|Data - article - workPhoto|妆品小图|
|Data - article - workName|妆品名称|
|Data - article - workCost|妆品原价|
|Data - article - workPrice|妆品折扣价|
|Data - article - workIsCollected|是否收藏，0未收藏，1已收藏|
|Data - article - collectNum|收藏人数|
|Data - labels|帖子标签
|Data - loverCount|喜欢的人数|
|Data - lovers - loverUserId|用户编号|
|Data - lovers - loverProfile|用户头像|
|Data - isNoTalk|是否禁言 0未禁言，1已禁言|
|Data - noTalkTime|禁言截止时间 格式："yyyy年MM月dd日 HH:mm:ss"|


<h2 id="5">5.获取标签对应的帖子列表V2.2.0</h2>

请求方法：nggirl/app/cli/post/getPostListByLabel/2.2.0

请求url：接口地址/nggirl/app/cli/post/getPostListByLabel/2.2.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|labelName|[必填]标签名称|
|page|第几页，默认从0开始|
|num|每页多少条，默认10|


请求示例：
> http://localhost/nggirl/app/cli/post/getPostListByLabel/V2.2.0?labelName=美白

返回结果示例：

```json
{
    "code":0,
    "data":[
        {
            "postId":1,
            "postType":1,
            "title":"拯救手残党，手把手教你画最in一字眉",
            "picture":"http://photosd.nggirl.com.cn/work/c9138c508f5d49f0afddf324c9097f3a.png"
        },
        {
            "postId":2,
            "postType":1,
            "title":"拯救手残党，手把手教你画最in一字眉",
            "picture":"http://photosd.nggirl.com.cn/work/c9138c508f5d49f0afddf324c9097f3a.png"
        },
        {
            "postId":3,
            "postType":1,
            "title":"拯救手残党，手把手教你画最in一字眉",
            "picture":"http://photosd.nggirl.com.cn/work/c9138c508f5d49f0afddf324c9097f3a.png"
        }
    ]
}
```

返回结果说明：

|字段名称|字段含义|
|---|---|
|Code|错误标识码，0表示正确|
|Data - postId|帖子编号|
|Data - postType|帖子类型 1文章，2视频|
|Data - title|帖子标题|
|Data - picture|帖子封面|


<h2 id="6">6.商品详情V2.5.0</h2>

>入参增加targetType，targetId 返回字段增加tb_item_id,tb_detail_url,isAllowBuy,targetType,targetId

请求方法：nggirl/app/cli/post/getSeedProductDetail/2.5.0

请求url：接口地址/nggirl/app/cli/post/getSeedProductDetail/2.5.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[可选]用户授权令牌（非必填，登录时必填）|
|seedProductId|[必填]商品编号|
|targetType |[必填]采集类型，1文章帖子，2视频帖子，3日签，0其他,4商品活动专题，5首页商品搜索，6首页推荐|
|targetId |[必填]采集点id，文章帖子id，视频帖子id，日签id，0其他，4商品活动专题id|

请求示例：
> http://localhost/nggirl/app/cli/post/getSeedProductDetail/2.5.0

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
      "isSeed":1,
      "recommendation":9,
      "productDesc":"敷一次一天都水嫩嫩。。。。",
      "detailImg":"http://photosd.nggirl.com.cn/work/c9138c508f5d49f0afddf324c9097f3a.png",
      "country":"法国",
      "brand":"锐澳",
      "brandImg":"http://photosd.nggirl.com.cn/work/c9138c508f5d49f0afddf324c9097f3a.png",
      "brandDesc":"暂无",
      "tb_item_id":"535029781633",
      "tb_detail_url":"http://s.click.taobao.com/t?e=m%3D2%26s%3D4a3DHoNzn44cQipKwQzePOeEDrYVVa64LKpWJ%2Bin0XLjf2vlNIV67lCxQo0EqW9tDOz%2BQ0Bmwbyg0d5GbxjoQ90pa4g5f6CeU7KR72F4cOggipziTxXbBP1cOjs7CjLzqGWIcIvrPh6go8yw%2BartgYJdLWm%2BQ5dOxgxdTc00KD8%3D&pvid=10_123.124.20.10_7833_1472701924154",
      "isAllowBuy":1,
      "targetType":1,
      "targetId":200
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
|Data - isSeed|是否已采集，0未采集，1已采集|
|Data - recommendation|推荐度，0-10|
|Data - productDesc |商品介绍|
|Data - detailImg|商品详情头图|
|Data - country|商品所属国家|
|Data - brand|商品品牌|
|Data - brandImg|品牌图片|
|Data - brandDesc|品牌描述|
|Data - tb_item_id|该商品在淘宝系统中的编号|
|Data - tb_detail_url|跳转的淘宝链接|
|Data - isAllowBuy|是否可以购买，1可购买，0不可购买|
|Data - targetType |从哪个页面点进来的 1文章帖子，2视频帖子，3日签，0其他|
|Data - targetId| 对应targetType，文章id，视频id，日签id，其他|
