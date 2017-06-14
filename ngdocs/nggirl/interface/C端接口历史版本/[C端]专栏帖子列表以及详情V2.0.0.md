# 南瓜姑娘后台接口-帖子列表以及详情V2.0.0

目录
---

* [1.首页专栏帖子列表V2.0.0](#1)
* [2.某一专栏对应帖子列表V2.0.0](#2)
* [3.视频帖子详情V2.0.0](#3)
* [4.文章帖子详情V2.0.0](#4)




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

<h2 id="3">3.视频帖子详情V2.0.0</h2>

请求方法：nggirl/app/cli/post/getVideoPostDetail/2.0.0

请求url：接口地址/nggirl/app/cli/post/getVideoPostDetail/2.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|用户授权令牌（非必填,登录时必填）|
|postId|帖子编号（必填）|
|postType|帖子类型（必填）|

请求示例：
> http://localhost/nggirl/app/cli/post/getVideoPostDetail/V2.0.0?postId=10&postType=2

返回结果示例：
```json
{
    "code":0,
    "data":{
        "postId":10,
        "postType":1,
        "columnName":"种草间",
        "title":"教你如何3分钟搞定范冰冰大波浪",
        "brief":"描述描述描述描述描述",
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
        "isCollected":1
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
|Data - brief|帖子描述|
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

<h2 id="4">4.文章帖子详情V2.0.0</h2>

请求方法：nggirl/app/cli/post/getArticlePostDetail/2.0.0

请求url：接口地址/nggirl/app/cli/post/getArticlePostDetail/2.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|用户授权令牌（非必填，登录时必填）|
|postId|帖子编号（必填）|
|postType|帖子类型（必填）|

请求示例：
> http://localhost/nggirl/app/cli/post/getArticlePostDetail/V2.0.0?postId=10&postType=1

返回结果示例：
```json
{
    "code":0,
    "data":{
        "postId":100,
        "postType":1,
        "columnName":"种草间",
        "title":"教你如何三分钟搞定范冰冰",
        "brief":"描述描述描述描述描述",
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
                "articleType":1,
                "content":"副标题",
                "descrip":"",
                "extend":""
            },
            {
                "articleType":2,
                "content":"段落详情段落详情段落详情",
                "descrip":"",
                "extend":""
            },
            {
                "articleType":3,
                "content":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
                "descrip":"",
                "extend":"640_320"
            },
            {
                "articleType":4,
                "content":"图片注释图片注释图片注释",
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
|Data - columnName|专栏名称|
|Data - title|帖子标题|
|Data - brief|帖子描述|
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
|Data - article - articleType|元件类型。 1标题，2段落，3图片，4.图片注释|
|Data - article - content|相关类型内容。1标题--标题文字，2段落--段落文字，3图片-图片url，4图片注释--注释文字|
|Data - article - descrip|相关类型的描述。1标题--空，2段落--空，3图片-空，4图片注释--空|
|Data - article - extend|扩展字段。1标题--空，2段落--空，3图片-宽\_高（640_320），4图片注释--空|

