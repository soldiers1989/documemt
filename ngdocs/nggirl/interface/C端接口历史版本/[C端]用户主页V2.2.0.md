<h1>用户主页V2.2.0</h1>
目录

* [1.获取用户主页基本信息V2.2.0](#1)
* [2.获取用户主页帖子列表V2.2.0](#2)


<h2 id="1">1.获取用户主页基本信息V2.2.0</h2>

请求方法：nggirl/app/cli/user/getUserInfo/2.2.0

请求URL：接口地址/nggirl/app/cli/user/getUserInfo/2.2.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|[可选]用户授权令牌，如果该用户已登录，则必填
|userId	|[必填]用户id

请求示例：

> http://localhost/nggirl/app/cli/user/getUserInfo/2.2.0

返回结果示例：

```json
{
    "code": 0,
    "data": {
      "userId":1,
      "profile":"http://testphotosd.nggirl.com.cn/work/135dd0dd6fc9436f8834a73ae31e8e2b.jpg",
      "nickName":"南瓜哥哥",
      "userRole":"客座小编",
      "sex":0,
      "cover":"http://testphotosd.nggirl.com.cn/work/135dd0dd6fc9436f8834a73ae31e8e2b.jpg",
      "isFollowed":1,
      "isMyHome":0
    }
}
```

返回字段说明：

|参数名称|参数含义|
|---|---|
|Code|错误标识码，0表示正确|
|Data - userId|用户id|
|Data - profile|用户头像|
|Data - nickName|用户昵称|
|Data - userRole|用户身份|
|Data - sex|用户性别，1女，0男|
|Data - cover|背景图|
|Data - isFollowed|是否关注了此用户，1已关注，0未关注|
|Data - isMyHome|是否是我的主页，1是我的主页，0不是我的主页|

<h2 id="2">2.获取用户主页帖子列表V2.2.0</h2>

请求方法：nggirl/app/cli/user/getUserPosts/2.2.0

请求URL：接口地址/nggirl/app/cli/user/getUserPosts/2.2.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|page	|[可选]页数,非必需参数，默认第一页
|num	|[可选]每页信息数目,非必须参数，默认20
|userId	|[必填]用户id


请求示例：

> http://localhost/nggirl/app/cli/user/getUserPosts/2.2.0?page=0&num=10&userId=1

返回结果示例：

```json
{
    "code": 0,
    "data": [
      {
          "postId":10,
          "postType":1,
          "picture":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
          "title":""
      },
      {
          "postId":11,
          "postType":1,
          "picture":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
          "title":""
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
|Data - title|帖子标题|
