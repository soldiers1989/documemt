<h1>系统消息</h1>
目录

* [1.根据环信账户信息,批量获取用户信息](#1)
* [2.获取未读系统消息条数](#2)
* [3.获取系统消息](#3)
* [4.标记消息为已读状态](#4)


<h2 id="1">1.根据环信账户信息,批量获取用户信息</h2>

请求方法：nggirl/app/cli/user/getUserProfile

请求URL：接口地址/ nggirl/app/cli/user/getUserProfile

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|idString	|用户环信账户字符串,多个账户间用英文","号分隔

请求示例：

> http://localhost/nggirl/app/bus/user/getUserProfile?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&idString=dresser_551ac26fd180a,client_552642a7de202

返回结果示例：

```json
{
    "code": 0,
    "data": [
        {
            "id": "dresser_551ac26fd180a",
            "nickname": "羿乐",
            "photo": "http://www.baidu.com/1.jpg"
        }
{
            "id": " client_552642a7de202",
            "nickname": "完颜",
            "photo": "http://www.baidu.com/5.jpg"
        }
    ]
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data – id	|账号id
|Data – nickname	|昵称
|Data – photo	|头像


<h2 id="2">2.获取未读系统消息条数</h2>

请求方法：nggirl/app/cli/user/getSystemMsgCount

请求URL：接口地址/nggirl/app/cli/user/getSystemMsgCount

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌

请求示例：

> http://localhost/nggirl/app/cli/user/getSystemMsgCount?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0

返回结果示例：

```json
{
    "code": 0,
    "data":  {
            "count": 5
        }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data – count	|未读系统消息条数

<h2 id="3">3.获取系统消息</h2>

请求方法：nggirl/app/cli/user/listSystemMessage

请求URL：接口地址/nggirl/app/cli/user/listSystemMessage

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|page	|页数。非必需参数，默认第一页
|num	|每页信息数目。非必须参数，默认20

请求示例：

> http://localhost/nggirl/app/cli/user/listSystemMessage?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&page=0&num=20

返回结果示例：

```json
{
    "code": 0,
    "data":  [{
            "messageType": 1,
            "messageContent": "相约七夕，来一场任性的折扣，敬请期待",
            "forwardKey": "",
            "profile": "",
            "orderStatus":1,
            "isVDresser": 0,
            "sendTime": 1435196075742

        },{
            "messageType": 2,
            "messageContent": "你预约的2015年08月18日14:00-16:00的Party妆化妆师已接单",
            "forwardKey": "123456",
            "profile": " http://www.baidu.com/1.jpg",
            "orderStatus":4,
            "isVDresser": 0,
            "sendTime": 1435196075742
        }]
}
```


返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data – messageType	|消息类型（消息类型，1系统消息，2作品消息，3预约/订单消息）--C端没有作品消息
|Data - messageContent	|消息内容
|Data - forwardKey	|跳转关键字（预约编号、作品编号、或者是跳转链接）(当messageType=1时为空)
|Data - profile	|来源用户头像(当messageType=1时为空)
|Data - orderStatus	|预约单/订单状态（当messageType=3时有效）
|Data - isVDresser	|是否为加V化妆师，0为否，1为是（当messageType=2/3时有效）
|Data - sendTime	|发出时间

<h2 id="4">4.标记消息为已读状态</h2>

请求方法：nggirl/app/cli/user/markReaded

请求URL：接口地址/nggirl/app/cli/user/markReaded

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌

请求示例：

> http://localhost/nggirl/app/cli/user/markReaded?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0

返回结果示例：

```json
{
    "code": 0,
    "data":  null
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
