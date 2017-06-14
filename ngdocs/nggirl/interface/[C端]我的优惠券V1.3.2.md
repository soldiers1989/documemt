<h1>我的优惠券V1.3.2</h1>

目录

* [1.我的优惠券(更新优惠券信息)](#1)
* [2.适用当前作品预约的优惠券(更新优惠券信息)](#2)

<h2 id="1">1.我的优惠券(更新优惠券信息)</h2>

请求方法：nggirl/app/cli/personalInfo/listCoupon/1.3.2

请求URL：接口地址/nggirl/app/cli/personalInfo/listCoupon/1.3.2

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
http://localhost/nggirl/app/cli/personalInfo/listCoupon/1.3.2?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&page=0&num=20

返回结果示例：
```json
{
    "code": 0,
    "data": [
        {
            "couponId": 151,
            "saleInfo": "88元",
            "lowPrice": 50,
            "deadLine": "永久有效",
            "fromChannel":"新用户注册得券",
            "fitProductName":"全品类",
            "useStatus": 1,
            "cutCost":0
        },
        {
             "couponId": 56,
            "saleInfo": "88元",
            "lowPrice": 50,
            "deadLine": "有效期：2016.01.15-2016.01.31",
            "fromChannel":"新用户注册得券",
            "fitProductName":"仅限上门美妆",
            "useStatus": 2,
            "cutCost":0
        }
    ]
}
```

返回字段说明：

|字段名|字段含义
|---|---
|Code|	错误码，0表示正确
|Data - couponId|优惠券id
|Data - saleInfo|优惠金额或打几折
|Data - lowPrice|最低多少元起可以使用
|Data - deadLine	|有效期 "永久有效" 或者 "有效期：2015.10.21-2015.10.29"
|Data - fromChannel	|来自哪个渠道
|Data - fitProductName	|适用产品类型 "全品类","仅限上门美妆","仅限美妆沙龙"
|Data - useStatus	|使用状态 0未使用,1已使用,2已过期
|Data - cutCost	|需要减去的金额，方便移动端计算（当是打折时，四舍五入取整）个人中心默认取零

<h2 id="2">2.适用当前作品预约的优惠券(更新优惠券信息)</h2>

请求方法：nggirl/app/cli/personalInfo/listCouponUse/1.3.2

请求URL：接口地址/nggirl/app/cli/personalInfo/listCouponUse/1.3.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken|	用户授权令牌
|page|	页数，非必需参数，默认第一页，页码从0开始
|num|	每页信息数目，非必须参数，默认20
|reservationId|预约编号

请求示例：
>
http://localhost/nggirl/app/cli/personalInfo/listCouponUse/1.3.2?accessToken=ACCESS_TOKEN&reservationId=2015082300391299&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&page=0&num=20

返回结果示例：
```json
{
    "code": 0,
    "data": [
        {
             "couponId": 151,
            "saleInfo": "80元",
            "lowPrice": 50,
            "deadLine": "有效期：2016.01.15-2016.01.31",
            "fromChannel":"新用户注册得券",
            "fitProductName":"仅限上门美妆",
            "useStatus": 0,
            "cutCost":80
        },
        {
             "couponId": 151,
            "saleInfo": "7.5折",
            "lowPrice": 50,
            "deadLine": "永久有效",
            "fromChannel":"领取 月辉 的邀请码获得",
            "fitProductName":"仅限上门美妆",
            "useStatus": 0,
            "cutCost":50
        }
    ]
}
```
返回字段说明：

|字段名|字段含义
|---|---
|Code|	错误码，0表示正确
|Data - couponId|优惠券id
|Data - saleInfo|优惠金额或打几折
|Data - lowPrice|最低多少元起可以使用
|Data - deadLine	|有效期 "永久有效" 或者 "有效期：2015.10.21-2015.10.29"
|Data - fromChannel	|来自哪个渠道
|Data - fitProductName	|适用产品类型 "全品类","仅限上门美妆","仅限美妆沙龙"
|Data - useStatus	|使用状态 0未使用,1已使用,2已过期
|Data - cutCost	|需要减去的金额，方便移动端计算（当是打折时，四舍五入取整）
