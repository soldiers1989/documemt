# 我的关注V3.0.0

目录

---

* [1.添加关注用户V2.2.0](#1)
* [2.获取我关注的用户列表V3.0.0](#2)
* [3.取消关注用户V2.2.0](#3)
* [4.获取关注的话题列表V3.0.0](#4)
* [5.我的粉丝列表V3.0.0](#5)
* [6.添加关注话题V3.0.0](#6)
* [7.取消关注话题V3.0.0](#7)

<h2 id="1">1.添加关注用户V2.2.0</h2>

请求方法：nggirl/app/cli/personal/addFollowUser/2.2.0

请求URL：接口地址/app/cli/personal/addFollowUser/2.2.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]用户授权令牌|
|followedUserId|[必填]被关注的用户编号|

请求示例：localhost/nggirl/app/cli/personal/addFollowUser/2.2.0

返回结果示例：

```json
{
  "code":0,
  "data":null
}
```


<h2 id="2">2.获取我关注的用户列表V3.0.0</h2>

>入参去除page、num，添加pageNum、pageSize，出参添加userLevel、isFollowed、followerNum、postNum

请求方法：nggirl/app/cli/personal/getFollowedUserList/3.0.0

请求URL：接口地址/nggirl/app/cli/personal/getFollowedUserList/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]用户授权令牌|
|pageNum|[可选]页数,非必需参数，默认第一页|
|pageSize|[可选]每页信息数目,非必须参数，默认20|

请求示例：localhost/nggirl/app/cli/personal/getFollowedUserList/3.0.0

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

返回字段说明：

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

<h2 id="3">3.取消关注用户V2.2.0</h2>

请求方法：nggirl/app/cli/personal/cancelFollowUser/2.2.0

请求URL：接口地址/nggirl/app/cli/personal/cancelFollowUser/2.2.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]用户授权令牌|
|followedUserId|[必填]被关注的用户编号|

请求示例：localhost/nggirl/app/cli/personal/cancelFollowUser/2.2.0

返回结果示例：

```json
{
  "code":0,
  "data":null
}
```


<h2 id="4">4.获取关注的话题列表V3.0.0</h2>

请求方法：nggirl/app/cli/personal/getFollowedHotTopicList/3.0.0

请求URL：接口地址/nggirl/app/cli/personal/getFollowedHotTopicList/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]用户授权令牌|
|pageNum|[可选]页数,非必需参数，默认第一页|
|pageSize|[可选]每页信息数目,非必须参数，默认20|

请求示例：

> http://localhost/nggirl/app/cli/personal/getFollowedHotTopicList/3.0.0

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


<h2 id="5">5.我的粉丝列表V3.0.0</h2>

请求方法：nggirl/app/cli/personal/getMyFansList/3.0.0

请求URL：接口地址/nggirl/app/cli/personal/getMyFansList/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]用户授权令牌|
|pageNum|[可选]页数,非必需参数，默认第一页|
|pageSize|[可选]每页信息数目,非必须参数，默认20|

请求示例：localhost/nggirl/app/cli/personal/getMyFansList/3.0.0

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

返回字段说明：

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



<h2 id="6">6.添加关注话题V3.0.0</h2>

请求方法：nggirl/app/cli/personal/addFollowTopic/3.0.0

请求URL：接口地址/app/cli/personal/addFollowTopic/3.0.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]用户授权令牌|
|topicId|[必填]被关注的话题编号|

请求示例：localhost/nggirl/app/cli/personal/addFollowTopic/3.0.0

返回结果示例：

```json
{
  "code":0,
  "data":null
}
```



<h2 id="7">7.取消关注话题V3.0.0</h2>

请求方法：nggirl/app/cli/personal/cancelFollowTopic/3.0.0

请求URL：接口地址/nggirl/app/cli/personal/cancelFollowTopic/3.0.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]用户授权令牌|
|topicId|[必填]被关注的用户编号|

请求示例：localhost/nggirl/app/cli/personal/cancelFollowTopic/3.0.0

返回结果示例：

```json
{
  "code":0,
  "data":null
}
```
