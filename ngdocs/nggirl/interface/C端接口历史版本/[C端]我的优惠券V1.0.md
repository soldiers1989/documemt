<h1>我的优惠券V1.0</h1>

目录

* [1.我的优惠券](#1)
* [2.适用当前作品预约的优惠券](#2)

<h2 id="1">1.我的优惠券</h2>

请求方法：nggirl/app/cli/personalInfo/listCoupon/1.0

请求URL：接口地址/nggirl/app/cli/personalInfo/listCoupon/1.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken|	用户授权令牌
|page|	页数，非必需参数，默认第一页，页码从0开始
|num|	每页信息数目，非必须参数，默认20

请求示例：
>
http://localhost/nggirl/app/cli/personalInfo/listCoupon/1.0?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&page=0&num=20

返回结果示例：
```json
{
    "code": 0,
    "data": [
        {
            "couponId": 151,
            "title": "领取 规划局 的邀请码获得",
            "couponNum": null,
            "deadLine": "永久有效",
            "fromUserName": "杨凯",
            "status": 1,
            "money": 30,
            "userId": 115,
            "fromUserId": 117,
            "balance": 0,
            "getTime": "2015-09-28 17:07:40",
            "code": "00030839",
            "startTime": null,
            "deadlineTime": null,
            "isForever": 1,
            "usedTime": "2015-09-28 17:51:36",
            "used": 1,
            "couponCode": "SP3QFNFLYP",
            "fitProduct": null,
            "lowPrice": null,
            "isDiscount": 0,
            "discount": null,
            "deadlineStatus": 0
        },
        {
            "couponId": 149,
            "title": "领取 张海威 的邀请码获得",
            "couponNum": null,
            "deadLine": "永久有效",
            "fromUserName": "杨凯",
            "status": 0,
            "money": 30,
            "userId": 115,
            "fromUserId": 113,
            "balance": 30,
            "getTime": "2015-09-28 17:05:10",
            "code": "00000135",
            "startTime": null,
            "deadlineTime": null,
            "isForever": 1,
            "usedTime": null,
            "used": 0,
            "couponCode": "SP36FVC4AD",
            "fitProduct": null,
            "lowPrice": null,
            "isDiscount": 0,
            "discount": null,
            "deadlineStatus": 0
        }
    ]
}
```

返回字段说明：

|字段名|字段含义
|---|---
|Code|	错误码，0表示正确
|Data - couponId|优惠券id
|Data - title	|优惠券标题
|Data - deadline|	有效期
|Data - couponNum	|优惠券编号
|Data - fromUserName	|来自哪个用户（用户名）
|Data - status	|是否使用了 （0未使用1使用）
|Data - money	|优惠金额
|Data - userId	|用户id
|Data - fromUserId	|来自哪个用户（用户id）
|Data - balance	|余额
|Data - getTime	|获取时间
|Data - code	|邀请码的值
|Data - startTime	|优惠券可用的起始时间
|Data - deadlineTime	|优惠券截止时间
|Data - isForever	|是否是永久有效，1永久有效，0非永久有效
|Data - usedTime	|优惠券被使用时间
|Data - used	|优惠券是否已经使用,0未使用,1已使用.
|Data - couponCode	|南瓜券的编号,用于显示在移动端的页面上
|Data - fitProduct	|适用的产品类型
|Data - lowPrice	|最低多少元起可用
|Data - isDiscount	|是否是折扣券
|Data - discount	|折扣,如7.5折，则值为7.5
|Data - deadlineStatus	|0永久有效,1未开始,2有效期内,3已过期


<h2 id="2">2.适用当前作品预约的优惠券</h2>

请求方法：nggirl/app/cli/personalInfo/listCouponUse/1.0

请求URL：接口地址/nggirl/app/cli/personalInfo/listCouponUse/1.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken|	用户授权令牌
|page|	页数，非必需参数，默认第一页，页码从0开始
|num|	每页信息数目，非必须参数，默认20
|workId|作品id

请求示例：
>
http://localhost/nggirl/app/cli/personalInfo/listCouponUse/1.0?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&page=0&num=20

返回结果示例：
```json
{
    "code": 0,
    "data": [
        {
            "couponId": 151,
            "title": "领取 规划局 的邀请码获得",
            "couponNum": null,
            "deadLine": "永久有效",
            "fromUserName": "杨凯",
            "status": 1,
            "money": 30,
            "userId": 115,
            "fromUserId": 117,
            "balance": 0,
            "getTime": "2015-09-28 17:07:40",
            "code": "00030839",
            "startTime": null,
            "deadlineTime": null,
            "isForever": 1,
            "usedTime": "2015-09-28 17:51:36",
            "used": 1,
            "couponCode": "SP3QFNFLYP",
            "fitProduct": null,
            "lowPrice": null,
            "isDiscount": 0,
            "discount": null,
            "deadlineStatus": 0
        },
        {
            "couponId": 149,
            "title": "领取 张海威 的邀请码获得",
            "couponNum": null,
            "deadLine": "永久有效",
            "fromUserName": "杨凯",
            "status": 0,
            "money": 30,
            "userId": 115,
            "fromUserId": 113,
            "balance": 30,
            "getTime": "2015-09-28 17:05:10",
            "code": "00000135",
            "startTime": null,
            "deadlineTime": null,
            "isForever": 1,
            "usedTime": null,
            "used": 0,
            "couponCode": "SP36FVC4AD",
            "fitProduct": null,
            "lowPrice": null,
            "isDiscount": 0,
            "discount": null,
            "deadlineStatus": 0
        }
    ]
}
```
返回字段说明：

|字段名|字段含义
|---|---
|Code|	错误码，0表示正确
|Data - couponId|优惠券id
|Data - title	|优惠券标题
|Data - deadline|	有效期
|Data - couponNum	|优惠券编号
|Data - fromUserName	|来自哪个用户（用户名）
|Data - status	|是否使用了 （0未使用1使用）
|Data - money	|优惠金额
|Data - userId	|用户id
|Data - fromUserId	|来自哪个用户（用户id）
|Data - balance	|余额
|Data - getTime	|获取时间
|Data - code	|邀请码的值
|Data - startTime	|优惠券可用的起始时间
|Data - deadlineTime	|优惠券截止时间
|Data - isForever	|是否是永久有效，1永久有效，0非永久有效
|Data - usedTime	|优惠券被使用时间
|Data - used	|优惠券是否已经使用,0未使用,1已使用.
|Data - couponCode	|南瓜券的编号,用于显示在移动端的页面上
|Data - fitProduct	|适用的产品类型
|Data - lowPrice	|最低多少元起可用
|Data - isDiscount	|是否是折扣券
|Data - discount	|折扣,如7.5折，则值为7.5
|Data - deadlineStatus	|0永久有效,1未开始,2有效期内,3已过期
