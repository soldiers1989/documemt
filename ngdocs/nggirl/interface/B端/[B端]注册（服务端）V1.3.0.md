<h1>注册（服务端）</h1>
目录

* [1.用户登录](#1)
* [2.创建账户](#2)
* [3.获取注册验证码](#3)
* [4.获取注册验证码（忘记密码）](#4)
* [5.验证注册验证码](#5)
* [6.更新授权令牌](#6)
* [7.修改密码（忘记密码时）](#7)
* [8.上传用户信息V1.3.0](#8)
* [9.获取化妆品品类列表](#9)
* [10.获取化妆品品牌列表](#10)
* [11.设置化妆品信息](#11)
* [12.更新账号推送信息](#12)


<h2 id="1">1.用户登录</h2>

请求方法：nggirl/app/bus/phoneUser/logon

请求URL：接口地址/nggirl/app/bus/phoneUser/ logon

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|phoneNum	|手机号
|password	|密码md5
|accessToken	|本地保存的授权令牌，如果本地没有保存此值（首次登陆时）此值置空

请求示例：

> http://localhost/nggirl/app/bus/phoneUser/create?phoneNum=13581878073&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&password=123456&accessToken=e69165ff30434105af03f593a26fceb0

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
|Data - imPassword	|IM账户登陆密码，已使用base64处理



<h2 id="2">2.创建账户</h2>

请求方法：nggirl/app/bus/phoneUser/create

请求URL：接口地址/nggirl/app/bus/phoneUser/create

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|phoneNum	|手机号
|password	|密码md5
|code	|注册验证码

请求示例：

> http://localhost/nggirl/app/bus/phoneUser/create?phoneNum=13581878073&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&password=123456&code=423396

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
|Data - imPassword	|IM账户登陆密码,已使用base64处理


<h2 id="3">3. 获取注册验证码</h2>

请求方法：nggirl/app/bus/phoneUser/getCode

请求URL：接口地址/nggirl/app/bus/phoneUser/getCode

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|phoneNum	|手机号

请求示例：

> http://localhost/nggirl/app/bus/phoneUser/getCode?phoneNum=18801168634&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

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

<h2 id="4">4.获取注册验证码(忘记密码)</h2>

请求方法：nggirl/app/bus/phoneUser/getCodeForgot

请求URL：接口地址/nggirl/app/bus/phoneUser/getCodeForgot

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|phoneNum	|手机号

请求示例：

> http://localhost/nggirl/app/bus/phoneUser/getCodeForgot?phoneNum=18801168634&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

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

<h2 id="5">5. 验证注册验证码</h2>

请求方法：nggirl/app/bus/phoneUser/checkRegisterCode

请求URL：接口地址/nggirl/app/bus/phoneUser/checkRegisterCode

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|phoneNum	|手机号
|code	|注册验证码

请求示例：

> http://localhost/nggirl/app/bus/phoneUser/checkRegisterCode?phoneNum=18801168634&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&code=423396

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

<h2 id="6">6.更新授权令牌</h2>

请求方法：nggirl/app/bus/phoneUser/

请求URL：接口地址/nggirl/app/bus/phoneUser/authorization

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|refreshToken	|刷新授权令牌

请求示例：

> http://localhost/nggirl/app/bus/phoneUser/authorization?app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=45f64d975bd367acadd2fc2fbf15143598930b06&refreshToken=b736e1025f99960440b0b89b0225554e05860ef3

返回结果示例：`见创建账户`


<h2 id="7">7.修改密码（忘记密码时）</h2>

请求方法：nggirl/app/bus/phoneUser/updatePasswordForgot

请求URL：接口地址/nggirl/app/bus/phoneUser/updatePasswordForgot

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|phoneNum	|手机号
|code	|注册验证码
|newPassword	|新密码md5

请求示例：

> http://localhost/nggirl/app/bus/phoneUser/updatePasswordForgot?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&phoneNum=13581878073&code=123456&newPassword=654321

返回结果示例：`见创建账户`


<h2 id="8">8.上传用户信息V1.3.0</h2>

>1.3.0是B端版本号

>接口入参删除name、district，添加nickName、realName、cityId、areaId

请求方法：nggirl/app/bus/phoneUser/uploadUserInfo/1.3.0

请求URL：接口地址/nggirl/app/bus/phoneUser/uploadUserInfo/1.3.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken|[必填]化妆师授权令牌
|nickName|[必填]化妆师昵称（对应数据表中的REALNAME字段）
|realName|[必填]化妆师真实姓名（对应数据表中的NAME字段）
|sex|[必填]性别(0-男；1-女)
|cityId|[必填]城市id
|areaId|[必填]区县id
|phoneNum|[必填]手机号
|profile|[可选]头像文件路径
|identificationCard	|[可选]身份证号
|identificationUpside	|[可选]身份证照片（正面），为上传图片后返回的路径
|identificationDownside	|[可选]身份证照片（反面），为上传图片后返回的路径

请求示例：

> http://localhost/nggirl/app/bus/phoneUser/uploadUserInfo/1.3.0

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


<h2 id="9">9.获取化妆品品类列表</h2>

请求方法：nggirl/app/bus/phoneUser/listCosmeticsClass

请求URL：接口地址/nggirl/app/bus/phoneUser/listCosmeticsClass

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌


请求示例：

> http://localhost/nggirl/app/bus/phoneUser/updatePushInfo?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=0c0cf4990aa72f3a75b961c21bab61d51f682f68

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "cosmeticsClass": ["粉底液","粉饼","散粉","眼影","眼线笔","眼线膏"]
    }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - cosmeticsClass |化妆品品类数组

<h2 id="10">10. 获取化妆品品牌列表</h2>

请求方法：nggirl/app/bus/phoneUser/listCosmeticsBrand

请求URL：接口地址/nggirl/app/bus/phoneUser/listCosmeticsBrand

支持格式：JSON

HTTP请求方式：POST(考虑到中文)

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|cosmeticsClass|化妆品品类名


请求示例：

> http://localhost/nggirl/app/bus/phoneUser/updatePushInfo?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=0c0cf4990aa72f3a75b961c21bab61d51f682f68&cosmeticsClass=粉底液

返回结果示例：

```json
{
    "code": 0,
    "data": [{
		"country":"法国",
		"brand": ["Dior迪奥","香奈儿chanel","Givenchy纪梵希","娇兰Guerlain"]
        },
        {
		"country":"英国",
		"brand": ["glo&ray","巴宝莉Burberry","博姿Boots","凯特 莫斯Kate Moss"]
        }]
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - country |化妆品品类数组
|Data - brand |国家分类下的品牌列表

<h2 id="11">11. 设置化妆品信息</h2>

请求方法：nggirl/app/bus/phoneUser/setCosmeticsInfo

请求URL：接口地址/nggirl/app/bus/phoneUser/setCosmeticsInfo

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|cosmeticsInfo|JSON格式的对象。包含化妆品品类和对应品类下的品牌

请求示例：

> http://localhost/nggirl/app/bus/phoneUser/setCosmeticsInfo?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=0c0cf4990aa72f3a75b961c21bab61d51f682f68&cosmeticsInfo=参见cosmeticsInfo格式
参见cosmeticsInfo格式:

返回结果示例：

```json
{
        "data":[{
		"cosmeticsClass":"粉底液",
		"cosmeticsBrand": ["Dior迪奥","香奈儿chanel"]
       },
       {
		"cosmeticsClass":"粉饼",
		"cosmeticsBrand": ["glo&ray","巴宝莉Burberry"]
        }]
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确


<h2 id="12">12.更新账户推送信息</h2>

请求方法：nggirl/app/bus/phoneUser/updatePushInfo

请求URL：接口地址/nggirl/app/bus/phoneUser/updatePushInfo

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|deviceType|设备类型0为android，1为ios
|pushUserId|推送用户id
|pushChannelId|推送管道id


请求示例：

> http://localhost/nggirl/app/bus/phoneUser/updatePushInfo?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=0c0cf4990aa72f3a75b961c21bab61d51f682f68&deviceType=ios&pushUserId=xxxxxxx&pushChannelId=8977625224424242424

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
|Code	|错误码，0表示正确,1表示用户未注册
