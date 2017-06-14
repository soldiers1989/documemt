# 南瓜社团V4.0.0

目录

---

* [1.获取免费试用、推荐帖子及热门话题V3.0.0](#1)
* [2.获取全部热门话题V3.0.0](#2)
* [3.获取话题详情V3.0.0](#3)
* [4.获取话题下帖子列表V3.0.0](#4)
* [5.获取热门帖子及推荐用户列表V3.0.0](#5)
* [6.获取推荐用户列表V3.0.0](#6)
* [7.获取新鲜帖子列表V3.0.0](#7)
* [8.获取关注用户的帖子列表V3.0.0](#8)
* [9.发现-福利-获取免费试用、推荐帖子V4.0.0](#9)
* [10.发现-话题-获取热门话题及其下的三篇热门帖子V4.0.0](#10)

---


<h2 id="1">1.获取免费试用、推荐帖子及热门话题V3.0.0</h2>

请求方法：nggirl/app/cli/community/getPageTopInfo/3.0.0

请求URL：接口地址/nggirl/app/cli/community/getPageTopInfo/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义|
|---|---|
|hotTopicNum	|[可选]热门话题数量，默认6|

请求示例：

> http://localhost/nggirl/app/cli/community/getPageTopInfo/3.0.0

返回结果示例：

```json
{
  "code": 0,
  "data": {
    "cosmeticTrials": [
      {
        "cosmeticId": 1,
        "title": "mac口红",
        "headImg": "http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
        "limits": 5,
        "applyNum": 56,
        "leftTime": "1天14小时"
      },{
        "cosmeticId": 2,
        "title": "mac口红",
        "headImg": "http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
        "limits": 5,
        "applyNum": 56,
        "leftTime": "已结束"
      }
    ],
    "recommendPosts": [
      {
        "postType": 1,
        "postId": 11,
        "title": "教你如何3分钟搞定范冰冰的大波浪",
        "recommendImg": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
        "viewNum": 1234,
        "likeNum": 100,
        "commentNum": 200,
        "label": "有奖互动"
      },
      {
        "postType": 1,
        "postId": 12,
        "title": "教你如何3分钟搞定范冰冰的大波浪",
        "recommendImg": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
        "viewNum": 3943,
        "likeNum": 3292,
        "commentNum": 95,
        "label": "年终大促"
      }
    ],
    "hotTopics": [
      {
        "topicId": 1,
        "topicName": "冬季护肤大法",
        "picture": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg"
      },
      {
        "topicId": 2,
        "topicName": "冬季护肤大法",
        "picture": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg"
      }
    ]
  }
}
```

返回结果说明:

|字段名称|字段含义|
|---|---|
|Code|错误码，0表示正确|
|Data - cosmeticTrials |试用妆品信息|
|Data - cosmeticTrials - cosmeticId|试用妆品id|
|Data - cosmeticTrials - title|标题|
|Data - cosmeticTrials - headImg|头图|
|Data - cosmeticTrials - limits|申请限量多少份|
|Data - cosmeticTrials - applyNum|申请人数|
|Data - cosmeticTrials - leftTime|剩余时间,如果返回空字符串"",表示申请时间已经结束|
|Data - recommendPosts |推荐帖子列表|
|Data - recommendPosts - postType|帖子类型 1为文章，2为视频|
|Data - recommendPosts - postId|帖子编号|
|Data - recommendPosts - title|帖子标题|
|Data - recommendPosts - recommendImg|推荐帖子配图，图片比例1:1|
|Data - recommendPosts - viewNum|浏览数量|
|Data - recommendPosts - likeNum|喜欢帖子的人的数量|
|Data - recommendPosts - commentNum|评论数量|
|Data - recommendPosts - label|帖子标签(帖子的第一个标签)|
|Data - hotTopics |热门话题列表|
|Data - hotTopics - topicId|话题id|
|Data - hotTopics - topicName|话题名称|
|Data - hotTopics - picture|话题配图，图片比例1:1|


<h2 id="2">2.获取全部热门话题V3.0.0</h2>

请求方法：nggirl/app/cli/community/getAllHotTopics/3.0.0

请求URL：接口地址/nggirl/app/cli/community/getAllHotTopics/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|pageNum|[可选]第几页，默认从0开始|
|pageSize|[可选]每页条数，默认为20|


请求示例：

> http://localhost/nggirl/app/cli/community/getAllHotTopics/3.0.0

返回结果示例：

```json
{
  "code": 0,
  "data": [
    {
      "topicId": 1,
      "topicName": "冬季护肤大法",
      "picture": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg"
    },
    {
      "topicId": 2,
      "topicName": "冬季护肤大法",
      "picture": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg"
    }
  ]
}
```

返回结果说明:

|字段名称|字段含义|
|---|---|
|Data - topicId|话题id|
|Data - topicName|话题名称|
|Data - picture|话题配图，图片比例1:1|


<h2 id="3">3.获取话题详情V3.0.0</h2>

请求方法：nggirl/app/cli/community/getHotTopicDetail/3.0.0

请求URL：接口地址/nggirl/app/cli/community/getHotTopicDetail/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|[非必填，已登录时必填]用户授权令牌
|topicId	|[必填]话题id

请求示例：

> http://localhost/nggirl/app/cli/community/getHotTopicDetail/3.0.0

返回结果示例：

```json
{
  "code": 0,
  "data": {
    "topicId": 2,
    "topicName": "冬季护肤大法",
    "headImg": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
    "shareImg": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
    "descrip": "话题描述话题描述话题描述话题描述话题描述话题描述话题描述",
    "isFollowed": 1,
    "fansNum": 983,
    "postNum": 97
  }
}
```

返回结果说明:

|字段名称|字段含义|
|---|---|
|Data - topicId|话题id|
|Data - topicName|话题名称|
|Data - headImg|话题背景头图|
|Data - shareImg|话题分享配图，图片比例1:1|
|Data - descrip|话题描述|
|Data - isFollowed|用户是否关注了此话题|
|Data - fansNum|粉丝数量|
|Data - postNum|话题下帖子数量|


<h2 id="4">4.获取话题下帖子列表V3.0.0</h2>

请求方法：nggirl/app/cli/community/getHotTopicPostList/3.0.0

请求URL：接口地址/nggirl/app/cli/community/getHotTopicPostList/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义|
|---|---|
|topicId	|[必填]话题id|
|pageNum|[可选]第几页，默认从0开始|
|pageSize|[可选]每页条数，默认为20|

请求示例：

> http://localhost/nggirl/app/cli/community/getHotTopicPostList/3.0.0

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
      "isEssential":0
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
      "isEssential":0
    }
  ]
}
```

返回结果说明:

|字段名称|字段含义|
|---|---|
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
|Data - isEssential|加精标志，1已加精，0未加精|



<h2 id="5">5.获取热门帖子及推荐用户列表V3.0.0</h2>

请求方法：nggirl/app/cli/community/getHotPostsAndRecommendUsers/3.0.0

请求URL：接口地址/nggirl/app/cli/community/getHotPostsAndRecommendUsers/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken	|[非必填，已登录时必填]用户授权令牌|
|pageNum|[可选]第几页，默认从0开始|
|pageSize|[可选]每页条数，默认为20|

请求示例：

> http://localhost/nggirl/app/cli/community/getHotPostsAndRecommendUsers/3.0.0

返回结果示例：

```json
{
  "code": 0,
  "data": [
    {
      "postId": 0,
      "postType": 0,
      "detailImg": "",
      "userId": 0,
      "nickName": "",
      "profile": "",
      "userRole": "",
      "userLevel":0,
      "title": "",
      "descrip": "",
      "columnId":0,
      "columnName":"",
      "commentNum": 0,
      "likeNum": 0,
      "viewNum": 0,
      "isEssential":0,
      "type": 2,
      "recommendUsers": [
        {
          "userId": 1,
          "nickName": "尼克",
          "profile": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
          "userLevel":1,
          "userRole":"南瓜小编",
          "isFollowed":1,
          "fansNum": 200,
          "postNum": 13
        },
        {
          "userId": 1,
          "nickName": "小清新",
          "profile": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
          "userLevel":0,
          "userRole":"",
          "isFollowed":0,
          "fansNum": 200,
          "postNum": 13
        }
      ]
    },
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
      "isEssential":0,
      "type": 1,
      "recommendUsers": []
    }
  ]
}
```

返回结果说明:

|字段名称|字段含义|
|---|---|
|Data - type|元素类型，1帖子（文章或者视频），2推荐用户列表|
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
|Data - isEssential|加精标志，1已加精，0未加精|
|Data - recommendUsers|推荐用户列表|
|Data - recommendUsers - userId|用户id|
|Data - recommendUsers - nickName|用户昵称|
|Data - recommendUsers - profile|用户头像|
|Data - recommendUsers - userLevel|用户等级|
|Data - recommendUsers - userRole|用户角色，南瓜小编、南瓜CEO、客座小编等，如果是普通用户则返回空字符串|
|Data - recommendUsers - isFollowed|是否已关注该用户，1已关注，0未关注|
|Data - recommendUsers - fansNum|用户粉丝数量|
|Data - recommendUsers - postNum|用户发帖数量|


<h2 id="6">6.获取推荐用户列表V3.0.0</h2>

请求方法：nggirl/app/cli/community/getRecommendUserList/3.0.0

请求URL：接口地址/nggirl/app/cli/community/getRecommendUserList/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken	|[非必填，已登录时必填]用户授权令牌|
|pageNum|[可选]第几页，默认从0开始|
|pageSize|[可选]每页条数，默认为20|

请求示例：

> http://localhost/nggirl/app/cli/community/getRecommendUserList/3.0.0

返回结果示例：

```json
{
  "code": 0,
  "data": [
    {
      "userId": 1,
      "nickName": "尼克",
      "profile": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
      "userRole":"南瓜小编",
      "userLevel":0,
      "isFollowed":0,
      "fansNum": 200,
      "postNum": 13
    },
    {
      "userId": 1,
      "nickName": "小清新",
      "profile": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
      "userRole":"",
      "userLevel":0,
      "isFollowed":0,
      "fansNum": 200,
      "postNum": 13
    }
  ]
}
```

返回结果说明:

|字段名称|字段含义|
|---|---|
|Data - userId|用户id|
|Data - nickName|用户昵称|
|Data - profile|用户头像|
|Data - userRole|用户角色|
|Data - userLevel|用户等级|
|Data - isFollowed|是否已关注该用户，1已关注，0未关注|
|Data - fansNum|用户粉丝数量|
|Data - postNum|用户发帖数量|




<h2 id="7">7.获取新鲜帖子列表V3.0.0</h2>

请求方法：nggirl/app/cli/community/getFreshPostList/3.0.0

请求URL：接口地址/nggirl/app/cli/community/getFreshPostList/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|pageNum|[可选]第几页，默认从0开始|
|pageSize|[可选]每页条数，默认为20|

请求示例：

> http://localhost/nggirl/app/cli/community/getFreshPostList/3.0.0

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
      "isEssential":0,
      "type":1
    },
    {
      "postId": 1,
      "postType": 1,
      "detailImg": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
      "userId": 269,
      "nickName": "尼克",
      "userLevel":1,
      "profile": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
      "userRole": "官方",
      "title": "兰蔻 玫瑰菁纯柔润唇膏口红唇彩",
      "descrip": "这款精华我用了30ML的一瓶。用后角质层修复效果极佳，脸部特别软。兑在乳液、精华、面膜、粉底都可以。完全百搭百搭百搭！重点是完全不油腻！抗过敏效",
      "columnId":1,
      "columnName":"美妆课堂",
      "commentNum": 100,
      "likeNum": 200,
      "viewNum": 1000,
      "isEssential":1,
      "type":1
    }
  ]
}
```

返回结果说明:

|字段名称|字段含义|
|---|---|
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
|Data - isEssential|加精标志，1已加精，0未加精|
|Data - type|为让安卓各个接口一致而添加的字段，固定为1|

<h2 id="8">8.获取关注用户的帖子列表V3.0.0</h2>

请求方法：nggirl/app/cli/community/getFollowedUserPostList/3.0.0

请求URL：接口地址/nggirl/app/cli/community/getFollowedUserPostList/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken	|[必填]用户授权令牌|
|pageNum|[可选]第几页，默认从0开始|
|pageSize|[可选]每页条数，默认为20|

请求示例：

> http://localhost/nggirl/app/cli/community/getFollowedUserPostList/3.0.0

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
      "isEssential":0,
      "status":2,
      "type":1
    },
    {
      "postId": 1,
      "postType": 1,
      "detailImg": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
      "userId": 269,
      "nickName": "尼克",
      "userLevel":1,
      "profile": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
      "userRole": "官方",
      "title": "兰蔻 玫瑰菁纯柔润唇膏口红唇彩",
      "descrip": "这款精华我用了30ML的一瓶。用后角质层修复效果极佳，脸部特别软。兑在乳液、精华、面膜、粉底都可以。完全百搭百搭百搭！重点是完全不油腻！抗过敏效",
      "columnId":1,
      "columnName":"美妆课堂",
      "commentNum": 100,
      "likeNum": 200,
      "viewNum": 1000,
      "isEssential":0,
      "status":1,
      "type":1
    }
  ]
}
```

返回结果说明:

|字段名称|字段含义|
|---|---|
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
|Data - isEssential|加精标志，1已加精，0未加精|
|Data - type|为让安卓各个接口一致而添加的字段，固定为1|
|Data - status|帖子状态,1审核中，2已上线|

<h2 id="9">9.发现-福利-获取免费试用、推荐帖子V4.0.0</h2>

> 与第一个接口相比,入参变成没有,出参去除话题hotTopics相关的参数  

请求方法：nggirl/app/cli/community/getPageTopInfo/4.0.0

请求URL：接口地址/nggirl/app/cli/community/getPageTopInfo/4.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数： 无


请求示例：

> http://localhost/nggirl/app/cli/community/getPageTopInfo/4.0.0

返回结果示例：

```json
{
  "code": 0,
  "data": {
    "cosmeticTrials": [
      {
        "cosmeticId": 1,
        "title": "mac口红",
        "headImg": "http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
        "limits": 5,
        "applyNum": 56,
        "leftTime": "1天14小时"
      },{
        "cosmeticId": 2,
        "title": "mac口红",
        "headImg": "http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
        "limits": 5,
        "applyNum": 56,
        "leftTime": "已结束"
      }
    ],
    "recommendPosts": [
      {
        "postType": 1,
        "postId": 11,
        "title": "教你如何3分钟搞定范冰冰的大波浪",
        "recommendImg": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
        "viewNum": 1234,
        "likeNum": 100,
        "commentNum": 200,
        "label": "有奖互动"
      },
      {
        "postType": 1,
        "postId": 12,
        "title": "教你如何3分钟搞定范冰冰的大波浪",
        "recommendImg": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
        "viewNum": 3943,
        "likeNum": 3292,
        "commentNum": 95,
        "label": "年终大促"
      }
    ]

  }
}
```

返回结果说明:

|字段名称|字段含义|
|---|---|
|Code|错误码，0表示正确|
|Data - cosmeticTrials |试用妆品信息|
|Data - cosmeticTrials - cosmeticId|试用妆品id|
|Data - cosmeticTrials - title|标题|
|Data - cosmeticTrials - headImg|头图|
|Data - cosmeticTrials - limits|申请限量多少份|
|Data - cosmeticTrials - applyNum|申请人数|
|Data - cosmeticTrials - leftTime|剩余时间,如果返回空字符串"",表示申请时间已经结束|
|Data - recommendPosts |推荐帖子列表|
|Data - recommendPosts - postType|帖子类型 1为文章，2为视频|
|Data - recommendPosts - postId|帖子编号|
|Data - recommendPosts - title|帖子标题|
|Data - recommendPosts - recommendImg|推荐帖子配图，图片比例1:1|
|Data - recommendPosts - viewNum|浏览数量|
|Data - recommendPosts - likeNum|喜欢帖子的人的数量|
|Data - recommendPosts - commentNum|评论数量|
|Data - recommendPosts - label|帖子标签(帖子的第一个标签)|


<h2 id="10">10.发现-话题-获取热门话题及其下的三篇热门帖子V4.0.0</h2>

请求方法：nggirl/app/cli/community/getAllHotTopics/4.0.0

请求URL：接口地址/nggirl/app/cli/community/getAllHotTopics/4.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|pageNum|[可选]第几页，默认从0开始|
|pageSize|[可选]每页条数，默认为20|


请求示例：

> http://localhost/nggirl/app/cli/community/getAllHotTopics/4.0.0

返回结果示例：

```json
{
  "code": 0,
  "data": [
    {
      "topicId": 1,
      "topicName": "冬季护肤大法",
	  "discussNum": 1236,
      "picture": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
      "cover": "",
	  "posts": [
	      {
	        "postType": 1,
	        "postId": 11,
	        "title": "教你如何3分钟搞定范冰冰的大波浪"
	      },
	      {
	        "postType": 1,
	        "postId": 12,
	        "title": "教你如何3分钟搞定范冰冰的大波浪"
	      },
		  {
	        "postType": 1,
	        "postId": 12,
	        "title": "教你如何3分钟搞定范冰冰的大波浪"
	      }
    ]
    },
    {
      "topicId": 2,
      "topicName": "冬季护肤大法",
	  "discussNum": 1266,
      "picture": "http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
	  "cover": "",
	  "posts": [
	      {
	        "postType": 1,
	        "postId": 11,
	        "title": "教你如何3分钟搞定范冰冰的大波浪"
	      },
	      {
	        "postType": 1,
	        "postId": 12,
	        "title": "教你如何3分钟搞定范冰冰的大波浪"
	      },
		  {
	        "postType": 1,
	        "postId": 12,
	        "title": "教你如何3分钟搞定范冰冰的大波浪"
	      }
    ]
    }
  ]
}
```

返回结果说明:

|字段名称|字段含义|
|---|---|
|Data - topicId|话题id|
|Data - topicName|话题名称|
|Data - discussNum|在线讨论人数|
|Data - picture|话题配图，图片比例1:1|
|Data - cover|话题封面图，图片比例3:2|
|Data - posts|该话题下的三篇热门帖子|
|Data - posts - postType|帖子类型 1 文章 2 视频|
|Data - posts - postId|帖子id|
|Data - posts - title|帖子标题|


