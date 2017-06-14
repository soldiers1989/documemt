# 注册V2.3.0
目录

* [1.用户登录](#1)
* [2.创建账户V2.1.0](#2)
* [3.第三方账号登录（微信）](#3)
* [4.第三方账号登录（微博）](#4)
* [5.获取注册验证码](#5)
* [6.获取注册验证码(忘记密码)](#6)
* [7.验证注册验证码](#7)
* [8.更新授权令牌](#8)
* [9.修改密码（忘记密码时）](#9)
* [10.上传用户信息V2.1.0](#10)
* [11.更新账户推送信息V2.0.0](#11)
* [12.获取短信验证码V2.3.0](#12)
* [13.验证短信验证码V2.3.0](#13)


<h2 id="1">1.用户登录</h2>

请求方法：nggirl/app/cli/phoneUser/logon

请求URL：接口地址/nggirl/app/cli/phoneUser/logon

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|phoneNum	|手机号
|password	|密码md5
|accessToken	|本地保存的授权令牌，如果本地没有保存此值（首次登陆时）此值置空

请求示例：

> http://localhost/nggirl/app/cli/phoneUser/create?phoneNum=13581878073&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&password=123456&accessToken=e69165ff30434105af03f593a26fceb0

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "userId": 1,
        "accessToken": "9c4c96c3def866c866d44575392d6dd0c9511973",
        "refreshToken": "da7d0666a7706d64c4bf7283e71a1f8289bd8aa1",
        "expireTime": 1434038634,
        "imAccount": "coach_551ac20eb4ce2",
        "imPassword": "MTIzNDU2"
    }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - userId	|用户id
|Data - accessToken	|用户授权令牌
|Data - refreshToken	|刷新授权令牌
|Data - expireTime	|用户授权过期时间
|Data - imAccount	|IM账户登陆用户名
|Data - imPassword	|IM账户登陆密码



<h2 id="2">2.创建账户V2.1.0</h2>

> 入参添加profile,nickName；出参添加nickName，profile，score

请求方法：nggirl/app/cli/phoneUser/create/2.1.0

请求URL：接口地址/nggirl/app/cli/phoneUser/create/2.1.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|phoneNum	|手机号
|password	|密码md5
|code	|注册验证码
|profile|用户头像
|nickName|用户昵称

请求示例：

> http://localhost/nggirl/app/cli/phoneUser/create?phoneNum=13581878073&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&password=123456&code=423396&profile=image.baidu.com/a.jpg&nickName=ixaomi

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "userId": 1,
        "accessToken": "9c4c96c3def866c866d44575392d6dd0c9511973",
        "refreshToken": "da7d0666a7706d64c4bf7283e71a1f8289bd8aa1",
        "expireTime": 1434038634,
        "imAccount": "coach_551ac20eb4ce2",
        "imPassword": "MTIzNDU2",
        "nickName" :"hahah",
        "profile": "http://testphotosd.nggirl.com.cn/work/98b09cbc00804529a408c3e5fd061fd7.jpg",
        "score": 100
    }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - userId	|用户id
|Data - accessToken	|用户授权令牌
|Data - refreshToken	|刷新授权令牌
|Data - expireTime	|用户授权过期时间
|Data - imAccount	|IM账户登陆用户名
|Data - imPassword	|IM账户登陆密码
|Data - profile| 头像
|Data - nickName|昵称
|Data - score|积分


<h2 id="3">3.第三方账号登录（微信）</h2>

请求方法：nggirl/app/cli/phoneUser/logonThirdWeixin

请求URL：接口地址/nggirl/app/cli/phoneUser/logonThirdWeixin

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌（微信登陆成功后返回的token）
|openid	|普通用户的标识，对当前开发者帐号唯一
|unionid|普通用户的统一标识，对公众号，开发者账号一致
|sysAccessToken	|本系统的授权令牌

请求示例：

> http://localhost/nggirl/app/cli/phoneUser/logonThirdWeibo?accessToken=9432a83e6e6748339b3738b65525be5a&openid=123456&unionid=12345678&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&sysAccessToken=

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "userId": 1,
        "accessToken": "9c4c96c3def866c866d44575392d6dd0c9511973",
        "refreshToken": "da7d0666a7706d64c4bf7283e71a1f8289bd8aa1",
        "expireTime": 1434038634,
        "imAccount": "coach_551ac20eb4ce2",
        "imPassword": "MTIzNDU2"
    }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - userId	|用户id
|Data - accessToken	|用户授权令牌
|Data - refreshToken	|刷新授权令牌
|Data - expireTime	|用户授权过期时间
|Data - imAccount	|IM账户登陆用户名
|Data - imPassword	|IM账户登陆密码


<h2 id="4">4.第三方账号登录（微博）</h2>

请求方法：nggirl/app/cli/phoneUser/logonThirdWeibo

请求URL：接口地址/nggirl/app/cli/phoneUser/logonThirdWeibo

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|用户授权令牌（微博登陆成功后返回的token）
|uid	|用户ID
|sysAccessToken	|本系统的授权令牌

请求示例：

> http://localhost/nggirl/app/cli/phoneUser/logonThirdWeibo?accessToken=9432a83e6e6748339b3738b65525be5a&uid=123456&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&sysAccessToken=

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "userId": 1,
        "accessToken": "9c4c96c3def866c866d44575392d6dd0c9511973",
        "refreshToken": "da7d0666a7706d64c4bf7283e71a1f8289bd8aa1",
        "expireTime": 1434038634,
        "imAccount": "coach_551ac20eb4ce2",
        "imPassword": "MTIzNDU2"
    }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - userId	|用户id
|Data - accessToken	|用户授权令牌
|Data - refreshToken	|刷新授权令牌
|Data - expireTime	|用户授权过期时间
|Data - imAccount	|IM账户登陆用户名
|Data - imPassword	|IM账户登陆密码


<h2 id="5">5.获取注册验证码</h2>

请求方法：nggirl/app/cli/phoneUser/getCode

请求URL：接口地址/nggirl/app/cli/phoneUser/getCode

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|phoneNum	|手机号

请求示例：

> http://localhost/nggirl/app/cli/phoneUser/getCode?phoneNum=18801168634&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：

```json
{
	"code": 0,
    "data": {
        "code": "123456",
	}
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - code	|验证码

<h2 id="6">6.获取注册验证码(忘记密码)</h2>

请求方法：nggirl/app/cli/phoneUser/getCodeForgot

请求URL：接口地址/nggirl/app/cli/phoneUser/getCodeForgot

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|phoneNum	|手机号

请求示例：

> http://localhost/nggirl/app/cli/phoneUser/getCodeForgot?phoneNum=18801168634&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：

```json
{
  "code": 0,
  "data": {
        "code": "123456",
	}
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确,1表示用户未注册
|Data - code	|验证码

<h2 id="7">7.验证注册验证码</h2>

请求方法：nggirl/app/cli/phoneUser/checkRegisterCode

请求URL：接口地址/nggirl/app/cli/phoneUser/checkRegisterCode

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|phoneNum	|手机号
|code	|注册验证码

请求示例：

> http://localhost/nggirl/app/cli/phoneUser/checkRegisterCode?phoneNum=18801168634&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&code=423396

返回结果示例：

```json
{
    "code": 0
}
```

返回字段说明：
|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确

<h2 id="8">8.更新授权令牌</h2>

请求方法：nggirl/app/cli/phoneUser/

请求URL：接口地址/nggirl/app/cli/phoneUser/authorization

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|refreshToken	|刷新授权令牌

请求示例：

> http://localhost/nggirl/app/cli/phoneUser/authorization?app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=45f64d975bd367acadd2fc2fbf15143598930b06&refreshToken=b736e1025f99960440b0b89b0225554e05860ef3

返回结果示例：

见创建账户

<h2 id="9">9.修改密码（忘记密码时）</h2>

请求方法：nggirl/app/cli/phoneUser/updatePasswordForgot

请求URL：接口地址/nggirl/app/cli/phoneUser/updatePasswordForgot

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|phoneNum	|手机号
|code	|注册验证码
|newPassword	|新密码md5

请求示例：

> http://localhost/nggirl/app/cli/phoneUser/updatePasswordForgot?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&phoneNum=13581878073&code=123456&newPassword=654321

返回结果示例：见创建账户


<h2 id="10">10.上传用户信息V2.1.0</h2>

> 入参去除城区district

请求方法：nggirl/app/cli/phoneUser/uploadUserInfo/2.1.0

请求URL：接口地址/nggirl/app/cli/phoneUser/uploadUserInfo/2.1.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|nickName	|昵称
|sex	|性别(0-男；1-女)
|birthday	|生日(yyyy-MM-dd)
|profile	|头像文件，为上传图片后返回的路径。
|phoneNum	|用户电话号码

请求示例：

> http://localhost/nggirl/app/cli/phoneUser/uploadUserInfo/1.5.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=0c0cf4990aa72f3a75b961c21bab61d51f682f68&nickName=bluesky&sex=0&birthday=1989-04-03profile=&phoneNum=

返回结果示例：

```json
{
    "code": 0,
    "data":null
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确


<h2 id="11">11.更新账户推送信息V2.0.0</h2>

> 出参无变化，入参添加了pushType

请求方法：nggirl/app/cli/phoneUser/updatePushInfo/2.0.0

请求URL：接口地址/nggirl/app/cli/phoneUser/updatePushInfo/2.0.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|[可选]用户授权令牌，但是若用户已登录，则必填
|deviceType	|[必填]设备类型0为android，1为ios
|pushType|[必填]推送类型，0百度推送，1个推推送
|pushUserId	|[可选]推送用户id，因为个推没有这个字段，所以不是必填项
|pushChannelId	|[必填]推送管道id，对应个推的clientId
|deviceId	|[必填]设备编号，ios使用idfa，安卓使用imei，用以跟踪渠道用户的注册和下单转化率

请求示例：

> http://localhost/nggirl/app/cli/phoneUser/updatePushInfo/2.0.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=0c0cf4990aa72f3a75b961c21bab61d51f682f68&deviceType=ios&pushUserId=xxxxxxx&pushChannelId=8977625224424242424&deviceId=adcdesgcdeldjllj

返回结果示例：

```json
{
    "code": 0,
    "data":null
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确


<h2 id="12">12.获取短信验证码V2.3.0</h2>

请求方法：nggirl/app/cli/phoneUser/getPhoneCode/2.3.0

请求URL：接口地址/nggirl/app/cli/phoneUser/getPhoneCode/2.3.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|phoneNum	|[必填]手机号

请求示例：

> http://localhost/nggirl/app/cli/phoneUser/getPhoneCode/2.3.0?phoneNum=18801168634&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：

```json
{
    "code": 0,
    "data": {
      "code": "123456"
    }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - code	|验证码


<h2 id="13">13.验证短信验证码V2.3.0</h2>

请求方法：nggirl/app/cli/phoneUser/checkPhoneCode/2.3.0

请求URL：接口地址/nggirl/app/cli/phoneUser/checkPhoneCode/2.3.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|phoneNum	|[必填]手机号
|code	|[必填]注册验证码

请求示例：

> http://localhost/nggirl/app/cli/phoneUser/checkPhoneCode/2.3.0?phoneNum=18801168634&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&code=423396

返回结果示例：

```json
{
    "code": 0,
    "data":null
}
```

返回字段说明：
|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
