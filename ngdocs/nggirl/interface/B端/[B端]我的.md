<h1>我的</h1>
目录

* [1.获取用户信息（化妆师）](#1)
* [2.背景封面修改](#2)
* [3.修改用户信息](#3)
* [4.注销](#4)
* [5.收支](#5)
  * [5.1. 收支情况](#5.1)
  * [5.2. 提现](#5.2)
* [6.获取评价总数](#6)
* [7.评价](#7)
* [8.使用化妆品](#8)
* [9.修改密码](#9)
* [10.服务条款](#10)
* [11.反馈建议](#11)



<h2 id="1">1.获取用户信息（化妆师）</h2>

请求方法：nggirl/app/bus/personalInfo/getUserInfo

请求URL：接口地址/nggirl/app/bus/personalInfo/getUserInfo

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|用户授权令牌

请求示例：

>http://localhost/nggirl/app/bus/personalInfo/getUserInfo?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "nickName": "bluesky",
        "sex": 0,
        "district": "北京 朝阳",
    	"identificationVerified":1,
         "starLevel ": 4 ,
        "profile": "http://www.baidu.com/1.jpg",
        "cover": "http://www.baidu.com/1.jpg",
        "phoneNum": "13426129466",
        "identificationCard": "131025198604125123",
        "identificationUpside":         "http://www.baidu.com/2.jpg",
        "identificationDownside": "http://www.baidu.com/3.jpg",
            "isVDresser":1
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|nickName	|昵称
|sex	|性别(0-男；1-女)
|district	|所在城区
|identificationVerified	|身份核实状态0未核实1已核实
|starLevel	|星级0-5的整数
|profile	|头像文件地址
|cover	|空间背景图片
|phoneNum	|用户手机号
|identificationCard	|身份证编号
|identificationUpside	|身份证照片（正面）文件地址
|identificationDownside	|身份证照片（反面）文件地址
|isVDresser|是否为加V化妆师，0为否，1为是

<h2 id="2">2.背景封面图修改</h2>

请求方法：nggirl/app/bus/personalInfo/updateBackgroud

请求URL：接口地址/nggirl/app/bus/personalInfo/updateBackgroud

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|background	|用户封面图片文件，为图片上传后返回的路径。

请求示例：

>http://localhost/nggirl/app/bus/personalInfo/updateBackgroud?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&background=

返回结果示例：
```json
{
    "code": 0,
    "data": {
        "url": "http://www.baidu.com/1.jpg",
        "md5": "pg12MQ68QFmdiqkPDE5Z8NKjUSksKg"
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - url	|上传文件网络地址
|Data - md5	|上传文件md5

<h2 id="3">3. 修改用户信息</h2>

请求方法：nggirl/app/bus/personalInfo/updateUserInfo

请求URL：接口地址/nggirl/app/bus/personalInfo/ updateUserInfo

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|用户授权令牌
|name|真实姓名[可选]
|sex|性别(0-男；1-女) [可选]
|district|所在城区[可选]
|phoneNum|手机号[可选]
|identificationCard|身份证号[可选]
|identificationUpside	|身份证照片（正面），为上传图片后返回的地址。[可选]
|identificationDownside	|身份证照片（反面），为上传图片后返回的地址。[可选]

请求示例：

>http://localhost/nggirl/app/bus/personalInfo/updateUserInfo?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&nickName=bluesky&sex=0&birthday=1989-04-03&district=北京朝阳&address=立汤路龙德2栋301&profile=&identificationUpside=&identificationDownside=

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


<h2 id="4">4.注销</h2>

请求方法：nggirl/app/bus/personalInfo/logout

请求URL：接口地址/ nggirl/app/bus/personalInfo/logout

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	用户授权令牌


请求示例：

>http://localhost/nggirl/app/bus/personalInfo/logout?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0

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

<h2 id="5">5. 收支</h2>
<h2 id="5.1">5.1 收支情况</h2>

请求方法：nggirl/app/bus/personalInfo/getBalanceInfo

请求URL：接口地址/nggirl/app/bus/personalInfo/getBalanceInfo

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|用户授权令牌
|page   |页数,非必需参数，默认第一页
|num|每页信息数目,非必须参数，默认20

请求示例：

>http://localhost/nggirl/app/bus/personalInfo/getBalanceInfo?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&page=0&num=20

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "balance": 1210,
        "inAndOut":[{
		"datetime": 1435196075742,
		"title":"工行尾号5858提现590元",
		"amount":-590
	},
	{
		"datetime": 1435196075742,
		"title":"来自晓丽的职业装化妆费结算",
		"amount":590
       }]
}
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - balance	|账户余额
|Data – inAndOut|账号收支信息数组，按时间倒序排列
|Data – inAndOut - datetime|信息时间,13位数字，代表自January 1, 1970 00:00:00 GMT开始到现在经历的毫秒数
|Data – inAndOut - title|收支信息标题
|Data – inAndOut - amount|收支数值

<h2 id="5.2">5.2 提现</h2>

请求方法：nggirl/app/bus/personalInfo/withdrawCash

请求URL：接口地址/nggirl/app/bus/personalInfo/ withdrawCash

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|用户授权令牌
|amount   |提现金额
|name|提现人
|bankName|银行名称
|accountNum|银行账号


请求示例：
> http://localhost/nggirl/app/bus/personalInfo/withdrawCash?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&amount=500&name=于子涵& bankName=工商银行&accountNum=1234567789

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


<h2 id="6">6.获取评价总数</h2>

请求方法：nggirl/app/bus/personalInfo/getEvaluateCount

请求URL：接口地址/nggirl/app/bus/personalInfo/getEvaluateCount

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌


请求示例：
> http://localhost/nggirl/app/bus/personalInfo/getEvaluateCount?app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=0c0cf4990aa72f3a75b961c21bab61d51f682f68

返回结果示例：
```json
{
    "code": 0,
    "data": {
        "total": 45
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - count	|评价总条数

<h2 id="7">7.评价</h2>

请求方法：nggirl/app/bus/personalInfo /getEvaluateList

请求URL：接口地址/ nggirl/app/bus/personalInfo /getEvaluateList

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|page|页数，非必需参数，默认第一页
|num|每页信息数目,非必须参数，默认20


请求示例：
> http://localhost/nggirl/app/bus/personalInfo/getEvaluateList?app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=0c0cf4990aa72f3a75b961c21bab61d51f682f68

返回结果示例：
```json
{
    "code": 0,
    "data": [{
		"userId":123456,
		"userName": "小美",
		"profile": "http://www.baidu.com/1.jpg",
		"reservationType":"预约职业装",
		"evaluation":"非常赞的化妆老师，很棒",
		"startLevel":3,
		"datetime": 1435196075742,
		"photos":[
				"http://www.baidu.com/1.jpg",
				"http://www.baidu.com/1.jpg",
				"http://www.baidu.com/1.jpg"
		]
},
	{
"userId":123456,
		"userName": "张杰",
		"profile": "http://www.baidu.com/1.jpg",
		"reservationType":"预约大片写真",
		"evaluation":"非常赞的化妆老师，很棒",
		"startLevel":3,
		"datetime": 1435196075742,
		"photos":[
				"http://www.baidu.com/1.jpg",
				"http://www.baidu.com/1.jpg"
		]
       }]
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - userId	|用户编号
|Data - userName	|用户名
|Data - profile	|用户头像路径
|Data - reservationType	|预约类型名称
|Data - evaluation	|评价内容
|Data - startLevel	|星级
|Data - datetime	|时间，13位数字，代表自January 1, 1970 00:00:00 GMT开始到现在经历的毫秒数
|Data – photos|照片列表

<h2 id="8">8.使用化妆品</h2>

请求方法：nggirl/app/bus/personalInfo /getCosmeticsInfo

请求URL：接口地址 nggirl/app/bus/personalInfo/ getCosmeticsInfo

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|用户授权令牌

请求示例：
> http://localhost/nggirl/app/bus/user/getCosmeticsInfo?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=0c0cf4990aa72f3a75b961c21bab61d51f682f68

返回结果示例：

```json
{
   "code":0,
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

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data – cosmeticsClass	|品类名称
|Data – cosmeticsBrand	|品牌列表




<h2 id="9">9.修改密码</h2>

请求方法：nggirl/app/bus/personalInfo/updatePassword

请求URL：接口地址/nggirl/app/bus/personalInfo/updatePassword

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|用户授权令牌
|oldPassword|旧密码MD5
|newPassword|新密码MD5

请求示例：
> http://localhost/nggirl/app/bus/personalInfo/updatePassword?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&phoneNum=13581878073&oldPassword=123456&newPassword=654321

>`返回结果示例：见创建账户`

<h2 id="10">10.服务条款</h2>

请求方法：app/bus/personalInfo/serviceInfo

请求URL：接口地址 app/bus/personalInfo/serviceInfo

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|用户授权令牌


请求示例：
http://localhost/nggirl/app/bus/personalInfo/serviceInfo?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：
```json
{
   "code": 0,
   "data": {
     "url": "http://www.baidu.com"
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data – url	|服务条款url

<h2 id="11">11.反馈建议</h2>

请求方法：nggirl/app/bus/personalInfo/submitFeedback

请求URL：接口地址/nggirl/app/bus/personalInfo/submitFeedback

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	| 用户授权令牌
|opinionType|反馈意见类型
|feedbackContent|反馈内容


请求示例：
>http://localhost/nggirl/app/bus/personalInfo/submitFeedback?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&opinionType=0&feedbackContent=这个版本很好用

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
