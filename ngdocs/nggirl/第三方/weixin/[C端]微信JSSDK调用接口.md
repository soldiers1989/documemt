# 微信JSSDK调用接口

> [微信JSSDK配置文档](http://mp.weixin.qq.com/wiki/7/aaa137b55fb2e0456bf8dd9148dd613f.html)

* [1.获取微信JSSDK权限验证配置](#1)
* [2.微信支付请求](#2)

<h2 id="1">1.获取微信JSSDK权限验证配置</h2>


请求方法：nggirl/app/cli/weixinjs/config

请求URL：接口地址/nggirl/app/cli/weixinjs/config

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

参数名称 | 参数含义
------------ | -------------
accessToken | [可选]授权令牌
url | [必填]调用JS接口页面的完整URL

请求示例：

`http://localhost/nggirl/app/cli/weixinjs/config`

返回结果示例：
```json
{
  "code":0,
  "data":{
    "appId":"wx0987mdungh1",
    "timestamp":1414587457,
    "nonceStr":"Wm3WZYTPz0wzccnW",
    "signature":"0f9de62fce790f9a083d5c99e95740ceb90c27ed"
  }
}
```
返回字段说明：

字段 | 说明
:------|:-------
code	|错误码，0表示正确
Data - appId | 公众号的唯一标识
Data – noncestr | 生成签名的随机串,签名用的noncestr和timestamp必须与wx.config中的nonceStr和timestamp相同
Data – timestamp | 生成签名的时间戳,签名用的noncestr和timestamp必须与wx.config中的nonceStr和timestamp相同
Data - signature | 必填，签名，见[微信JSSDK,附录1-JS-SDK使用权限签名算法](http://mp.weixin.qq.com/wiki/7/aaa137b55fb2e0456bf8dd9148dd613f.html#JSSDK.E4.BD.BF.E7.94.A8.E6.AD.A5.E9.AA.A4)


<h2 id="2">2.微信支付获取订单信息</h2>

> [网页端调起支付API，详细文档说明](https://pay.weixin.qq.com/wiki/doc/api/jsapi.php?chapter=7_7&index=6)

请求方法：nggirl/app/cli/weixinjs/getOrder

请求URL：接口地址/nggirl/app/cli/weixinjs/getOrder

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

参数名称 | 参数含义
------------ | -------------
accessToken | [必填]授权令牌
reservationId | [必填]预约编号

请求示例：

`http://localhost/nggirl/app/cli/weixinjs/getOrder`

返回结果示例：
```JSON
{
  "data": {
        "order_status": 1,
        "weixin_prepay_id": "123456789",
        "weixin_appid": "wxfe8754d4e19d9c85",
        "weixin_package": "prepay_id=123456789",
        "weixin_noncestr": "636138788e564044b7c2b63b1cec0aea",
        "weixin_timestamp": "1438931958",
        "weixin_sign": "D9F92DC0B05AA670A71B6E15F2FEBD54",
        "weixin_signtype":"MD5"
    },
    "code": 0
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - order_status|本订单的支付状态，1未支付，2已支付
|Data - weixin_prepay_id|微信的预支付id
|Data - weixin_appid|微信分配的公众账号ID
|Data - weixin_package|统一下单接口返回的prepay_id参数值，提交格式如：prepay_id=***
|Data - weixin_noncestr|随机字符串，不长于32位
|Data - weixin_timestamp|时间戳
|Data - weixin_sign|签名
|Data - weixin_signtype | 固定值MD5
