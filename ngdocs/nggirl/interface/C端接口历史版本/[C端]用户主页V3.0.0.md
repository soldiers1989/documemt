<h1>用户主页V3.0.0</h1>

目录

* [1.获取用户主页基本信息V3.0.0](#1)
* [2.获取用户主页帖子列表V3.0.0](#2)


<h2 id="1">1.获取用户主页基本信息V3.0.0</h2>

>入参无变化,添加出参fansNum、followedNum

请求方法：nggirl/app/cli/user/getUserInfo/3.0.0

请求URL：接口地址/nggirl/app/cli/user/getUserInfo/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|[可选]用户授权令牌，如果该用户已登录，则必填
|userId	|[必填]用户id

请求示例：

> http://localhost/nggirl/app/cli/user/getUserInfo/3.0.0

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
      "isMyHome":0,
      "userLevel":1,
      "fansNum":100,
      "followedNum":200
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
|Data - userLevel|用户等级:0LV0,1LV1,2LV2...|
|Data - fansNum|该用户粉丝量|
|Data - followedNum|该用户关注了多少人|


<h2 id="2">2.获取用户主页帖子列表V3.0.0</h2>

>入参添加accessToken

请求方法：nggirl/app/cli/user/getUserPosts/3.0.0

请求URL：接口地址/nggirl/app/cli/user/getUserPosts/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|[可选]用户授权令牌，如果该用户已登录，则必填
|page	|[可选]页数,非必需参数，默认第一页
|num	|[可选]每页信息数目,非必须参数，默认20
|userId	|[必填]用户id


请求示例：

> http://localhost/nggirl/app/cli/user/getUserPosts/3.0.0?page=0&num=10&userId=1

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
      "status":2,
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
      "status":1,
      "isEssential":1
    }
  ]
}
```

返回字段说明：

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
|Data - status|帖子状态,1审核中，2已上线|
|Data - isEssential|是否加精帖，1是，0否
