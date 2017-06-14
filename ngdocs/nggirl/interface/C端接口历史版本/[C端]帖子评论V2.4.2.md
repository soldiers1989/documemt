<h1>帖子评论V2.4.2</h1>

目录

* [1.获取帖子(文章或者视频)的评论列表V2.4.2](#1)
* [2.评论帖子V2.0.0](#2)
* [3.回复评论V2.0.0](#3)
* [4.删除评论V2.0.0](#4)
* [5.删除回复V2.0.0](#5)
* [6.举报评论V2.0.0](#6)
* [7.对评论点赞和取消点赞V2.4.2](#7)


<h2 id="1">1.获取帖子(文章或者视频)的评论列表V2.4.2</h2>

>入参无变化，出参添加praiseCount和isPraised字段

请求方法：nggirl/app/cli/post/getComments/2.4.2

请求URL：接口地址/nggirl/app/cli/post/getComments/2.4.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|[可选]用户授权令牌，若用户已登录，则必填
|postType|[必填]贴子类型，1为文章，2为视频
|postId|[必填]贴子id(文章id或者视频id)
|page	|[可选]页数,非必需参数，默认第一页
|num	|[可选]每页信息数目,非必须参数，默认20
|queryTime|[可选]查询时间，查询第一页时，不需要传入该参数；查询第二页及其他页时，则传入该参数，必填

请求示例：
> http://localhost/nggirl/app/cli/post/getComments/2.4.2?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：

```json
{
    "code": 0,
    "data":{
      "queryTime":1466497616723,
      "comments":[
        {
          "floorNum":1,
          "commentId":111,
          "userId":1,
          "nickName":"小清新",
          "profile":"http://testphotosd.nggirl.com.cn/work/68856d91c7674daca32e59c79bdd8a6c.png",
          "commentTime":1323450912123,
          "comment":"简直太棒了，很有收获！",
          "systemTime":1323450912123,
          "isMyComment":1,
          "isIllegal":0,
          "praiseCount":100,
          "isPraised":1,
          "replies":[
            {
              "replyId":123,
              "replyUserId":2,
              "replyUserNickName":"小萝莉",
              "reply":"层主美美美！！",
              "isMyReply":0,
              "replyType":1,
              "replyToUserId":0,
              "replyToUserNickName":"",
              "replyTime":1323450912123,
              "systemTime":1323450912123,
              "isIllegal":0
            },{
              "replyId":456,
              "replyUserId":1,
              "replyUserNickName":"小清新",
              "reply":"你更美美美！！",
              "isMyReply":1,
              "replyType":2,
              "replyToUserId":2,
              "replyToUserNickName":"小萝莉",
              "replyTime":1323450912123,
              "systemTime":1323450912123,
              "isIllegal":1
            }
          ]
        }
      ]
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - queryTime	|查询的开始时间（第一次查询后，后台返回该时间，以后加载下一页时，需要将该时间回传给后台）
|Data - floorNum |楼层号
|Data - commentId	|评论id
|Data - userId	|用户id
|Data - nickName	|用户昵称
|Data - profile	|用户头像
|Data - commentTime	|用户评论时间
|Data - comment	|评论内容
|Data - systemTime	|系统当前时间
|Data - isMyComment	|该评论是否是当前用户发表的评论，1是，0否
|Data - isIllegal	|该评论是否合法,0合法,1不合法
|Data - praiseCount |该评论获得点赞的数量
|Data - isPraised	|是否已对该评论点赞，1已点赞，0未点赞
|Data - replies	| 该评论的所有回复
|Data - replies	- replyId| 回复id
|Data - replies	- replyUserId| 回复者id
|Data - replies	- replyUserNickName| 回复者昵称
|Data - replies	- reply| 回复内容
|Data - replies	- isMyReply| 该回复是否是当前用户的回复，1是，0否
|Data - replies	- replyType| 回复类型，1针对当前评论的回复，2针对指定回复的回复
|Data - replies	- replyToUserId| 如果replayType=2，被回复者id
|Data - replies	- replyToUserNickName| 如果replayType=2，被回复者昵称
|Data - replies	- replyTime| 回复时间
|Data - replies	- systemTime| 当前系统时间
|Data - replies	- isIllegal| 该回复是否合法,0合法,1不合法

<h2 id="2">2.评论帖子V2.0.0</h2>

>评论字数需要10个字以上，否则弹出toast提示：亲亲要写10个汉字以上哟~

请求方法：nggirl/app/cli/post/comment/2.0.0

请求URL：接口地址/nggirl/app/cli/post/comment/2.0.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|[必填]用户授权令牌
|postType|[必填]贴子类型，1为文章，2为视频
|postId|[必填]贴子id(文章id或者视频id)
|content|[必填]评论内容

请求示例：
> http://localhost/nggirl/app/cli/post/comment/2.0.0

返回结果示例：

```json
{
    "code": 0,
    "data": {
      "commentId":111,
      "userId":1,
      "nickName":"小清新",
      "profile":"http://testphotosd.nggirl.com.cn/work/68856d91c7674daca32e59c79bdd8a6c.png",
      "commentTime":1323450912123,
      "systemTime":1323450912123,
      "isIllegal":0,
      "comment":"这是一条评论。。。",
      "floorNum":2,
      "isMyComment":1
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - commentId	|评论id
|Data - userId	|用户id
|Data - nickName	|用户昵称
|Data - profile	|用户头像
|Data - commentTime	|用户评论时间
|Data - systemTime	|系统当前时间
|Data - isIllegal	|该评论是否合法,0合法,1不合法
|Data - comment	|评论内容
|Data - floorNum	|楼层号
|Data - isMyComment	|该评论是否是当前用户发表的评论，1是，0否


<h2 id="3">3.回复评论V2.0.0</h2>

请求方法：nggirl/app/cli/post/reply/2.0.0

请求URL：接口地址/nggirl/app/cli/post/reply/2.0.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|[必填]用户授权令牌
|replyType|[必填]回复类型，1针对评论的回复，2针对回复的回复
|commentId|[必填]评论id
|replyId|[可选]指定回复id，若replyType=2，则必填
|content|[必填]回复内容

请求示例：
> http://localhost/nggirl/app/cli/article/reply/2.0.0

返回结果示例：

```json
{
    "code": 0,
    "data": {
      "replyId":456,
      "replyUserId":1,
      "replyUserNickName":"小清新",
      "replyType":2,
      "replyToUserId":2,
      "replyToUserNickName":"小萝莉",
      "replyTime":1323450912123,
      "systemTime":1323450912123,
      "isMyReply":1,
      "isIllegal":0,
      "reply":"哈哈哈哈"
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data	- replyId| 回复id
|Data	- replyUserId| 回复者id
|Data	- replyUserNickName| 回复者昵称
|Data	- replyType| 回复类型，1针对当前评论的回复，2针对指定回复的回复
|Data	- replyToUserId| 如果replyType=2，被回复者id
|Data	- replyToUserNickName| 如果replyType=2，被回复者昵称
|Data - replyTime| 回复时间
|Data - systemTime| 当前系统时间
|Data - isIllegal	|该回复是否合法,0合法,1不合法
|Data - isMyReply|该回复是否是当前用户的回复，1是，0否
|Data	- reply| 回复内容

<h2 id="4">4.删除评论V2.0.0</h2>

请求方法：nggirl/app/cli/post/deleteComment/2.0.0

请求URL：接口地址/nggirl/app/cli/post/deleteComment/2.0.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|[必填]用户授权令牌
|commentId|[必填]评论id

请求示例：
> http://localhost/nggirl/app/cli/post/deleteComment/2.0.0

返回结果示例：

```json
{
    "code": 0,
    "data": null
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确

<h2 id="5">5.删除回复V2.0.0</h2>

请求方法：nggirl/app/cli/post/deleteReply/2.0.0

请求URL：接口地址/nggirl/app/cli/post/deleteReply/2.0.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|[必填]用户授权令牌
|replyId|[必填]回复id

请求示例：
> http://localhost/nggirl/app/cli/post/deleteReply/2.0.0

返回结果示例：

```json
{
    "code": 0,
    "data": null
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确

<h2 id="6">6.举报评论V2.0.0</h2>

请求方法：nggirl/app/cli/post/report/2.0.0

请求URL：接口地址/nggirl/app/cli/post/report/2.0.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|[必填]用户授权令牌
|targetType|[必填]目标类型，1针对评论的举报，2针对回复的举报
|targetId|[必填]目标id，若targetType=1，则为评论id；若targetType=2，则为回复id

请求示例：
> http://localhost/nggirl/app/cli/post/report/2.0.0

返回结果示例：

```json
{
    "code": 0,
    "data": null
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确

<h2 id="7">7.对评论点赞和取消点赞V2.4.2</h2>

请求方法：nggirl/app/cli/post/praiseComment/2.4.2

请求URL：接口地址/nggirl/app/cli/post/praiseComment/2.4.2

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|[必填]用户授权令牌
|commentId|[必填]评论id
|status|[必填]点赞状态，1点赞，0取消点赞

请求示例：
> http://localhost/nggirl/app/cli/post/praiseComment/2.4.2

返回结果示例：

```json
{
    "code": 0,
    "data":null
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
