# 帖子列表以及详情V3.0.0

目录

---

* [1.首页专栏帖子列表V2.0.0](#1)
* [2.某一专栏对应帖子列表V3.0.0--弃用](#2)
* [3.视频帖子详情V3.0.0](#3)
* [4.文章帖子详情V3.0.0](#4)
* [5.获取标签对应的帖子列表V3.0.0](#5)
* [6.商品详情V2.5.0](#6)
* [7.帖子的相关商品列表V2.5.3](#7)
* [8.喜欢的人列表V2.5.4](#8)




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


<h2 id="2">2.某一专栏对应帖子列表V3.0.0--弃用</h2>

>使用[\[C端\]首页分类按钮和推荐帖子与商品V3.0.0.md](\[C端\]首页分类按钮和推荐帖子与商品V3.0.0.md#3)接口替换该接口

请求方法：nggirl/app/cli/column/getPostListByColumn/3.0.0

请求url：接口地址/nggirl/app/cli/column/getPostListByColumn/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|columnId|[必填]专栏编号|
|pageNum|[可选]第几页，默认从0开始|
|pageSize|[可选]每页条数，默认为20|

请求示例：

> http://localhost/app/cli/column/getPostListByColumn/3.0.0?columnId=1

返回结果示例：

```json
{
  "code": 0,
  "data": [
    {
      "postId": 1,
      "postType": 1,
      "picture": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
      "userId": 269,
      "nickName": "尼克",
      "profile": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
      "userRole": "官方",
      "title": "兰蔻 玫瑰菁纯柔润唇膏口红唇彩",
      "descrip": "这款精华我用了30ML的一瓶。用后角质层修复效果极佳，脸部特别软。兑在乳液、精华、面膜、粉底都可以。完全百搭百搭百搭！重点是完全不油腻！抗过敏效",
      "commentNum": 100,
      "likeNum": 200,
      "viewNum": 1000
    },
    {
      "postId": 2,
      "postType": 1,
      "picture": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
      "userId": 269,
      "nickName": "小清新",
      "profile": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
      "userRole": "官方",
      "title": "兰蔻 玫瑰菁纯柔润唇膏口红唇彩",
      "descrip": "这款精华我用了30ML的一瓶。用后角质层修复效果极佳，脸部特别软。兑在乳液、精华、面膜、粉底都可以。完全百搭百搭百搭！重点是完全不油腻！抗过敏效",
      "commentNum": 100,
      "likeNum": 200,
      "viewNum": 1000
    }
  ]
}
```
返回字段说明：

|字段名称|字段含义|
|---|---|
|Code |错误码，0表示正确|
|Data - postId|帖子编号|
|Data - postType|帖子类型：1文章帖子，2视频帖子|
|Data - picture|帖子列表配图|
|Data - userId|用户编号|
|Data - nickName|用户昵称|
|Data - profile|用户头像|
|Data - userRole|用户角色|
|Data - title|标题|
|Data - descrip|描述|
|Data - commentNum|评论数|
|Data - likeNum|喜欢的人数|
|Data - viewNum|浏览数|

<h2 id="3">3.视频帖子详情V3.0.0</h2>

>picture重命名为detailImg

>入参添加isCountViewNum字段

>出参添加status、isMyPost

请求方法：nggirl/app/cli/post/getVideoPostDetail/3.0.0

请求url：接口地址/nggirl/app/cli/post/getVideoPostDetail/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|用户授权令牌（非必填,登录时必填）|
|postId|[必填]帖子编号|
|postType|[必填]帖子类型|
|isCountViewNum|[可选]是否统计本次浏览数据，1统计，0不统计，默认为1|

请求示例：
> http://localhost/nggirl/app/cli/post/getVideoPostDetail/3.0.0?postId=10&postType=2

返回结果示例：
```json
{
    "code":0,
    "data":{
        "postId":10,
        "postType":1,
        "columnName":"种草间",
        "title":"教你如何3分钟搞定范冰冰大波浪",
        "shareContent":"变美的路有那么多，南瓜姑娘的帖子是一条捷径~",
        "detailImg":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
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
        "status":2,
        "isMyPost":1,
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
                "tb_item_id":"532908619147",
                "tb_detail_url":"http://s.click.taobao.com/t?e=m%3D2%26s%3D%2Fn40tp%2BOf1gcQipKwQzePOeEDrYVVa64LKpWJ%2Bin0XLjf2vlNIV67kc1djqQgzT%2BQev46Oo1utSg0d5GbxjoQ90pa4g5f6CeU7KR72F4cOggipziTxXbBP1cOjs7CjLzqGWIcIvrPh5kkW9DBiyiMZKuiAxTyMspxgxdTc00KD8%3D&pvid=10_49.4.155.146_71449_1473072470177",
                "isAllowBuy":1,
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
              "type":1,
                "content":"副标题",
                "seedProductId":-1,
                "name":"",
                "picture":"",
                "price":-1,
                "seedNum":-1,
                "isSeed":-1,
                "recommendation":5,
                "tb_item_id":"532908619147",
                "tb_detail_url":"http://s.click.taobao.com/t?e=m%3D2%26s%3D%2Fn40tp%2BOf1gcQipKwQzePOeEDrYVVa64LKpWJ%2Bin0XLjf2vlNIV67kc1djqQgzT%2BQev46Oo1utSg0d5GbxjoQ90pa4g5f6CeU7KR72F4cOggipziTxXbBP1cOjs7CjLzqGWIcIvrPh5kkW9DBiyiMZKuiAxTyMspxgxdTc00KD8%3D&pvid=10_49.4.155.146_71449_1473072470177",
                "isAllowBuy":1,
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
|Data - shareContent|分享内容|
|Data - detailImg|配图|
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
|Data - status|帖子状态，1审核中，2已上线|
|Data - labels|帖子标签
|Data - loverCount|喜欢的人数|
|Data - lovers - loverUserId|用户编号|
|Data - lovers - loverProfile|用户头像|
|Data - isNoTalk|是否禁言 0未禁言，1已禁言|
|Data - isMyPost|是否是否是我的帖子，1是我的帖子，0不是我的帖子|
|Data - noTalkTime|禁言截止时间 格式："yyyy年MM月dd日 HH:mm:ss"|
|Data - article|帖子详情|
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
|Data - article - tb_item_id|淘宝商品id|
|Data - article - tb_detail_url|商品链接|
|Data - article - isAllowBuy|0不可购买，1可购买|
|Data - article - workId|妆品编号|
|Data - article - workPhoto|妆品小图|
|Data - article - workName|妆品名称|
|Data - article - workCost|妆品原价|
|Data - article - workPrice|妆品折扣价|
|Data - article - workIsCollected|是否收藏，0未收藏，1已收藏|
|Data - article - collectNum|收藏人数|



<h2 id="4">4.文章帖子详情V3.0.0</h2>

>picture重命名为detailImg

>入参添加isCountViewNum字段

>出参添加status字段、isMyPost

请求方法：nggirl/app/cli/post/getArticlePostDetail/3.0.0

请求url：接口地址/nggirl/app/cli/post/getArticlePostDetail/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|用户授权令牌（非必填，登录时必填）|
|postId|[必填]帖子编号|
|postType|[必填]帖子类型|
|isCountViewNum|[可选]是否统计本次浏览数据，1统计，0不统计，默认为1|

请求示例：
> http://localhost/nggirl/app/cli/post/getArticlePostDetail/3.0.0?postId=10&postType=1

返回结果示例：
```json
{
    "code":0,
    "data":{
        "postId":100,
        "postType":1,
        "columnName":"种草间",
        "title":"教你如何三分钟搞定范冰冰",
        "shareContent":"变美的路有那么多，南瓜姑娘的帖子是一条捷径~",
        "detailImg":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
        "viewNum":1234,
        "commentNum":200,
        "createTime":1320718222932,
        "createUserId":156,
        "userProfile":"http://wx.qlogo.cn/mmopen/H9XkvMl38uDrDibLNp5Tqr5ckUVonlTKISh2LGjU6jcldPnssiatSjtR7PSOVGdAtyKAUicqXvEwLiaFCtGfmxUqocGhKeEYEicPj/0",
        "userName":"小可爱",
        "userRole":"南瓜小编",
        "isPraised":1,
        "isCollected":0,
        "status":2,
        "isMyPost":1,
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
                "tb_item_id":"532908619147",
                "tb_detail_url":"http://s.click.taobao.com/t?e=m%3D2%26s%3D%2Fn40tp%2BOf1gcQipKwQzePOeEDrYVVa64LKpWJ%2Bin0XLjf2vlNIV67kc1djqQgzT%2BQev46Oo1utSg0d5GbxjoQ90pa4g5f6CeU7KR72F4cOggipziTxXbBP1cOjs7CjLzqGWIcIvrPh5kkW9DBiyiMZKuiAxTyMspxgxdTc00KD8%3D&pvid=10_49.4.155.146_71449_1473072470177",
                "isAllowBuy":1,
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
                "tb_item_id":"532908619147",
                "tb_detail_url":"http://s.click.taobao.com/t?e=m%3D2%26s%3D%2Fn40tp%2BOf1gcQipKwQzePOeEDrYVVa64LKpWJ%2Bin0XLjf2vlNIV67kc1djqQgzT%2BQev46Oo1utSg0d5GbxjoQ90pa4g5f6CeU7KR72F4cOggipziTxXbBP1cOjs7CjLzqGWIcIvrPh5kkW9DBiyiMZKuiAxTyMspxgxdTc00KD8%3D&pvid=10_49.4.155.146_71449_1473072470177",
                "isAllowBuy":1,
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
                "tb_item_id":"532908619147",
                "tb_detail_url":"http://s.click.taobao.com/t?e=m%3D2%26s%3D%2Fn40tp%2BOf1gcQipKwQzePOeEDrYVVa64LKpWJ%2Bin0XLjf2vlNIV67kc1djqQgzT%2BQev46Oo1utSg0d5GbxjoQ90pa4g5f6CeU7KR72F4cOggipziTxXbBP1cOjs7CjLzqGWIcIvrPh5kkW9DBiyiMZKuiAxTyMspxgxdTc00KD8%3D&pvid=10_49.4.155.146_71449_1473072470177",
                "isAllowBuy":1,
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
                "tb_item_id":"532908619147",
                "tb_detail_url":"http://s.click.taobao.com/t?e=m%3D2%26s%3D%2Fn40tp%2BOf1gcQipKwQzePOeEDrYVVa64LKpWJ%2Bin0XLjf2vlNIV67kc1djqQgzT%2BQev46Oo1utSg0d5GbxjoQ90pa4g5f6CeU7KR72F4cOggipziTxXbBP1cOjs7CjLzqGWIcIvrPh5kkW9DBiyiMZKuiAxTyMspxgxdTc00KD8%3D&pvid=10_49.4.155.146_71449_1473072470177",
                "isAllowBuy":1,
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
                "tb_item_id":"532908619147",
                "tb_detail_url":"http://s.click.taobao.com/t?e=m%3D2%26s%3D%2Fn40tp%2BOf1gcQipKwQzePOeEDrYVVa64LKpWJ%2Bin0XLjf2vlNIV67kc1djqQgzT%2BQev46Oo1utSg0d5GbxjoQ90pa4g5f6CeU7KR72F4cOggipziTxXbBP1cOjs7CjLzqGWIcIvrPh5kkW9DBiyiMZKuiAxTyMspxgxdTc00KD8%3D&pvid=10_49.4.155.146_71449_1473072470177",
                "isAllowBuy":1,
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
                "tb_item_id":"532908619147",
                "tb_detail_url":"http://s.click.taobao.com/t?e=m%3D2%26s%3D%2Fn40tp%2BOf1gcQipKwQzePOeEDrYVVa64LKpWJ%2Bin0XLjf2vlNIV67kc1djqQgzT%2BQev46Oo1utSg0d5GbxjoQ90pa4g5f6CeU7KR72F4cOggipziTxXbBP1cOjs7CjLzqGWIcIvrPh5kkW9DBiyiMZKuiAxTyMspxgxdTc00KD8%3D&pvid=10_49.4.155.146_71449_1473072470177",
                "isAllowBuy":1,
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
|Data - shareContent|分享内容|
|Data - detailImg|配图|
|Data - viewNum|浏览数量|
|Data - commentNum|评论数量|
|Data - createUserId|创建用户编号|
|Data - userProfile|用户头像|
|Data - userName|用户昵称|
|Data - userRole|用户角色|
|Data - isPraised|是否已点赞 0未点赞，1已点赞|
|Data - isCollected|是否已收藏 0未收藏，1已收藏|
|Data - status|帖子状态，1审核中，2已上线|
|Data - isMyPost|是否是否是我的帖子，1是我的帖子，0不是我的帖子|
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
|Data - article - tb_item_id|淘宝商品id|
|Data - article - tb_detail_url|商品链接|
|Data - article - isAllowBuy|0不可购买，1可购买|
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


<h2 id="5">5.获取标签对应的帖子列表V3.0.0</h2>

请求方法：nggirl/app/cli/post/getPostListByLabel/3.0.0

请求url：接口地址/nggirl/app/cli/post/getPostListByLabel/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|labelName|[必填]标签名称|
|page|第几页，默认从0开始|
|num|每页多少条，默认10|

请求示例：

> http://localhost/nggirl/app/cli/post/getPostListByLabel/3.0.0?labelName=美白

返回结果示例：

```json
{
  "code": 0,
  "data": [
    {
      "postId": 1,
      "postType": 1,
      "detailImg": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
      "userId": 269,
      "nickName": "尼克",
      "profile": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
      "userRole": "官方",
      "userLevel":1,
      "title": "兰蔻 玫瑰菁纯柔润唇膏口红唇彩",
      "descrip": "这款精华我用了30ML的一瓶。用后角质层修复效果极佳，脸部特别软。兑在乳液、精华、面膜、粉底都可以。完全百搭百搭百搭！重点是完全不油腻！抗过敏效",
      "columnId":1,
      "columnName":"美妆课堂",
      "commentNum": 100,
      "likeNum": 200,
      "viewNum": 1000,
      "isEssential":1
    },
    {
      "postId": 2,
      "postType": 1,
      "detailImg": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
      "userId": 269,
      "nickName": "小清新",
      "profile": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
      "userRole": "官方",
      "userLevel":1,
      "title": "兰蔻 玫瑰菁纯柔润唇膏口红唇彩",
      "descrip": "这款精华我用了30ML的一瓶。用后角质层修复效果极佳，脸部特别软。兑在乳液、精华、面膜、粉底都可以。完全百搭百搭百搭！重点是完全不油腻！抗过敏效",
      "columnId":1,
      "columnName":"美妆课堂",
      "commentNum": 100,
      "likeNum": 200,
      "viewNum": 1000,
      "isEssential":1
    }
  ]
}
```

返回结果说明：

|字段名称|字段含义|
|---|---|
|Code|错误标识码，0表示正确|
|Data - postId|帖子编号|
|Data - postType|帖子类型：1文章帖子，2视频帖子|
|Data - detailImg|帖子列表配图|
|Data - userId|用户编号|
|Data - nickName|用户昵称|
|Data - profile|用户头像|
|Data - userRole|用户角色|
|Data - userLevel|用户等级|
|Data - title|标题|
|Data - descrip|描述|
|Data - columnId|专栏id|
|Data - columnName|专栏名称|
|Data - commentNum|评论数|
|Data - likeNum|喜欢的人数|
|Data - viewNum|浏览数|
|Data - isEssential|是否加精贴：0否，1是|


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
|targetType |[必填]采集类型，1文章帖子，2视频帖子，3日签，4商品活动专题，推送，banner|
|targetId |[必填]采集点id，文章帖子id，视频帖子id，日签id，商品活动专题id|

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
|Data - targetType |从哪个页面点进来的 1文章帖子，2视频帖子，3日签，0其他，4商品活动专题|
|Data - targetId| 对应targetType，文章id，视频id，日签id，其他，商品活动专题id|




<h2 id="7">7.帖子的相关商品列表V2.5.3</h2>

请求方法：nggirl/app/cli/post/getSeedProductList/2.5.3

请求url：接口地址/nggirl/app/cli/post/getSeedProductList/2.5.3

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[可选]用户授权令牌（非必填，登录时必填）|
|postType|帖子类型：1文章帖子，2视频帖子|
|postId|帖子编号|
|pageNum|第几页，默认从0开始（非必填）|
|pageSize|每页条数，默认为10（非必填）|


请求示例：
> http://localhost/nggirl/app/cli/post/getSeedProductList/2.5.3

返回结果示例：

```json
{
    "code":0,
    "data":[
        {
            "seedProductId":1,
            "name":"商品名称",
            "picture":"http://photosd.nggirl.com.cn/work/c9138c508f5d49f0afddf324c9097f3a.png",
            "price":1209,
            "seedNum":32,
            "isSeed":1,
            "tb_item_id":"532908619147",
            "tb_detail_url":"",
            "isAllowBuy":1,
        },
        {
            "seedProductId":1,
            "name":"商品名称",
            "picture":"http://photosd.nggirl.com.cn/work/c9138c508f5d49f0afddf324c9097f3a.png",
            "price":1209,
            "seedNum":32,
            "isSeed":1,
            "tb_item_id":"532908619147",
            "tb_detail_url":"",
            "isAllowBuy":1,
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
|Data - isSeed|是否已种草：0未种草，1已种草|
|Data - tb_item_id|商品淘宝编号|
|Data - tb_detail_url|商品购买链接|
|Data - isAllowBuy|0不可购买，1可购买|


<h2 id="8">8.喜欢的人列表V2.5.4</h2>

请求方法：nggirl/app/cli/column/getPostLoverList/2.5.4

请求url：接口地址/nggirl/app/cli/column/getPostLoverList/2.5.4

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|pageNum|第几页，默认从0开始（非必填）|
|pageSize|每页条数，默认为5（非必填）|
|postId|贴子编号（必填）|
|postType|贴子类型（必填）|

请求示例：
> http://localhost/nggirl/app/cli/column/getPostLoverList/2.5.4

返回结果示例：
```json
{
    "code":0,
    "data":{   
            "total":10,
            "users":[
                {
                    "loverUserId":10,
                    "loverName":"王小仙",
                    "loverProfile":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg"                
                },
                {
                    "loverUserId":10,
                    "loverName":"张小贱",
                    "loverProfile":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg"
                }
            ]
        }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code|错误码,0表示正确|
|Data - total|喜欢的人总数|
|Data - users|用户列表|
|Data - users - loverUserId|用户编号|
|Data - users - loverName|用户 昵称|
|Data - users - loverProfile|用户头像|
