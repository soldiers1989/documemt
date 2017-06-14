<h1>化妆师</h1>
目录

* [1.全部化妆师](#1)
* [2.化妆师模糊查询](#2)
* [3.获取化妆师个人信息](#3)
* [4.获取化妆师作品列表](#4)
* [5.对化妆师的评价](#5)
* [6.取消关注化妆师](#6)
* [7.关注化妆师](#7)
* [8.评论作品](#8)
* [9.作品分享成功](#9)


<h2 id="1">1.全部化妆师</h2>

请求方法：nggirl/app/cli/dresser/listDresser

请求URL：接口地址/nggirl/app/cli/dresser/listDresser

支持格式：JSON

HTTP请求方式：POST（考虑到中文可能乱码）

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|用户授权令牌
|dresserCity	|化妆师所在城市[可选]
|workTypes	|妆束类型[可选][可能是多个]
|page	|页数。非必需参数，默认第一页
|num	|每页信息数目。非必须参数，默认20

请求示例：

> http://localhost/ nggirl/app/cli/dresser/listDresser?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0& dresserCity =北京&workTypes=职业装&page=1&num=20

返回结果示例：

```json
{
	"code": 0,
    "data": [{
		"dresserId": 10000,
		"dresserName":"张晓梅",
		"profile":" http://www.baidu.com/1.jpg",
		"workTypes":["职业妆","约会妆","大片写真"],   
 		"authentication":1,
		"starLevel": 4,
		"orderNum": 63,
		"isVDresser":0
	},
	{
		"dresserId": 10000,
		"dresserName":"于子涵",
		"profile":" http://www.baidu.com/1.jpg",
		"workTypes":["职业妆","约会妆","大片写真"],   
 		"authentication": 1,
		"starLevel": 4,
		"orderNum": 63,
		"isVDresser":1
       }]
}
```

返回字段说明：

|字段名称|字段含义
|---|---
|Code	|错误码，0表示正确
|Data - dresserId	|化妆师编号
|Data - dresserName	|化妆师姓名
|Data - profile	|化妆师头像文件路径
|Data - workType	|妆束类型
|Data - authentication	|是否已经认证，0未认证，1已认证
|Data - starLevel	|星级
|Data - orderNum	|成功订单数量
|Data - isVDresser	|是否为加V化妆师，0为否，1为是

<h2 id="2">2.化妆师模糊查询</h2>

请求方法：nggirl/app/cli/dresser/listDresserBlur

请求URL：接口地址/ nggirl/app/cli/dresser/ listDresserBlur

支持格式：JSON

HTTP请求方式：POST(考虑到可能有中文会乱码的问题)

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|dresserCity	|化妆师所在城市
|key	|查询关键字[可选]
|page	|页数。非必需参数，默认第一页
|num	|每页信息数目。非必须参数，默认20

请求示例：

> http://localhost/ nggirl/app/cli/dresser/listDresserBlur?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&key=于&page=1&num=20

返回结果示例：

```json
{
	"code": 0,
    "data": [{
		"dresserId": 10000,
		"dresserName":"张晓梅",
		"profile":" http://www.baidu.com/1.jpg",
		"workType":["职业妆","约会妆","大片写真"],   
 		"authentication":1,
		"starLevel": 4,
		"orderNum": 63,
		"isVDresser":1
	},
	{
		"dresserId": 10000,
		"dresserName":"于子涵",
		"profile":" http://www.baidu.com/1.jpg",
		"workType":["职业妆","约会妆","大片写真"],   
 		"authentication": 1,
		"starLevel": 4,
		"orderNum": 63,
		"isVDresser":0
       }]
}
```

返回字段说明：

|字段名称|字段含义
|---|---
|Code	|错误码，0表示正确
|Data - dresserId	|化妆师编号
|Data - dresserName	|化妆师姓名
|Data - profile	|化妆师头像文件路径
|Data - workType	|妆束类型
|Data - authentication	|是否已经认证，0未认证，1已认证
|Data - starLevel	|星级
|Data - orderNum	|成功订单数量
|Data - isVDresser	|是否为加V化妆师，0为否，1为是

<h2 id="3">3.获取化妆师个人信息</h2>

请求方法：nggirl/app/cli/ dresser/getDresserInfo

请求URL：接口地址/ nggirl/app/cli/ dresser/getDresserInfo

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|dresserId	|化妆师id

请求示例：

> http://localhost/ nggirl/app/cli/dresser/getDresserInfo?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&dresserId=10000

返回结果示例：

```json
{
	"code": 0,
	"data":{
		"dresserId":10000,
		"dresserName":"于子涵",
		"district":"北京 朝阳区",
		"profile":" http://www.baidu.com/1.jpg",
		"orderNum":23,
		"authentication":1,
		"cover":" http://www.baidu.com/1.jpg",
		"starLevel":4,
   	"followed":1,
		"isVDresser":1
	}
}
```

返回字段说明：

|字段名称|字段含义
|---|---
|Code	|错误码，0表示正确
|Data – dresserId	|化妆师编号
|Data – dresserName	|化妆师姓名
|Data – district	|所在区域
|Data – profile	|头像
|Data – orderNum	|已完成订单量
|Data – authentication	|是否已经授权，0未授权，1已授权
|Data – cover	|背景图片路径
|Data – starLevel	|评价星级
|Data – followed	|该用户是否已经关注过该化妆师，0未关注，1已关注
|Data - isVDresser	|是否为加V化妆师，0为否，1为是

<h2 id="4">4.获取化妆师作品列表</h2>

请求方法：nggirl/app/cli/ dresser /listWorksByDresserId

请求URL：接口地址/ nggirl/app/cli/ dresser /listWorksByDresserId

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|用户授权令牌
|dresserId	|化妆师id
|page	|页数。非必需参数，默认第一页
|num	|每页信息数目。非必须参数，默认20

请求示例：

> http://localhost/ nggirl/app/cli/dresser/listWorksByDresserId?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&page=0&num=20&dresserId=10000

返回结果示例：

```json
{
	"code": 0,
	"data":[{
		"workId": 1234567,
		"cover":" http://www.baidu.com/1.jpg",
		"workType":"约会妆",   
		"cost":100,
		"praiseNum":12,
		"praised":0,
		"isVDresser":1
	},
	{
		"workId": 1234567,
		"cover":" http://www.baidu.com/1.jpg",
		"workType":"职业妆",   
		"cost":100,
		"praiseNum":12,
		"praised":1,
		"isVDresser":0
       }]
}
```

返回字段说明：

|字段名称|字段含义
|---|---
|Code	|错误码，0表示正确
|Data - workId	|作品编号
|Data - cover	|封面图片路径
|Data - workType	|作品类型
|Data - cost	|费用
|Data - praiseNum	|点赞人数
|Data - praised	|该用户是否已经对该作品点过赞[0未点赞，1已点赞]
|Data - isVDresser	|是否为加V化妆师，0为否，1为是

<h2 id="5">5.对化妆师的评价</h2>

请求方法：nggirl/app/cli/dresser/getEvaluateList

请求URL：接口地址/nggirl/app/cli/dresser/getEvaluateList

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|dresserId	|化妆师编号
|page	|页数。非必需参数，默认第一页
|num	|每页信息数目。非必须参数，默认20

请求示例：

> http://localhost/nggirl/app/cli/dresser/getEvaluateList?app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=0c0cf4990aa72f3a75b961c21bab61d51f682f68&dresserId=1234&page=1&num=3

返回结果示例：

```json
{
    "code": 0,
    "data": [
        {
            "evaluationId": 343,
            "userName": "美丽",
            "profile": "http://photosd.nggirl.com.cn/work/f40b2e3d9b3c4bbb8641e0d46732450f.png",
            "workType": "约会妆",
            "evaluation": "今生难见",
            "startLevel": 5,
            "datetime": 1446172535000,
            "photos": [
                "http://testphotosd.nggirl.com.cn/work/677666e6aa7146fc94fac17e8db22e85.jpg",
                "http://testphotosd.nggirl.com.cn/work/3ecdfaec37d14d1e9b8ba9bf7f15ca71.jpg",
                "http://testphotosd.nggirl.com.cn/work/2b40f14c08c04e81a7f3ea8921d96b73.jpg"
            ]
        },
        {
            "evaluationId": 342,
            "userName": "美丽",
            "profile": "http://photosd.nggirl.com.cn/work/f40b2e3d9b3c4bbb8641e0d46732450f.png",
            "workType": "特殊造型",
            "evaluation": "11111",
            "startLevel": 5,
            "datetime": 1446172469000,
            "photos": [
                "http://testphotosd.nggirl.com.cn/work/2ddf3e707a6c41f5af651739c743296b.jpg"
            ]
        }
    ]
}
```

返回字段说明：

|字段名称|字段含义
|---|---
|Code	|错误码，0表示正确
|Data - userName	|用户名
|Data - profile	|用户头像路径
|Data- reservationType	|预约类型名称
|Data - evaluation	|评价内容
|Data - startLevel	|星级
|Data - datetime	|时间。13位数字，代表自January 1, 1970 00:00:00 GMT开始到现在经历的毫秒数
|Datat - photos	|照片列表

<h2 id="6">6.取消关注化妆师</h2>

请求方法：nggirl/app/cli/dresser/cancelFollowDresser

请求URL：接口地址/ nggirl/app/cli/dresser/ cancelFollowDresser

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|dresserId	|化妆师编号

请求示例：

> http://localhost/ nggirl/app/cli/dresser/cancelFollowDresser?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0& dresserId=1234567

返回结果示例：

```json
{
	"code": 0,
	"data":null
}
```

返回字段说明：

|字段名称|字段含义
|---|---
|Code	|错误码，0表示正确


<h2 id="7">7.关注化妆师</h2>

请求方法：nggirl/app/cli/dresser/followDresser

请求URL：接口地址/ nggirl/app/cli/dresser/ followDresser

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|dresserId	|化妆师编号

请求示例：

> http://localhost/ nggirl/app/cli/dresser/followDresser?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0& dresserId=1234567

返回结果示例：

```json
{
	"code": 0,
	"data":null
}
```

返回字段说明：

|字段名称|字段含义
|---|---
|Code	|错误码，0表示正确

<h2 id="8">8.评论作品</h2>

请求方法：nggirl/app/cli/dresser/evaluateWork

请求URL：接口地址/ nggirl/app/cli/dresser/ evaluateWork

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|workId	|作品编号
|evaluateContent|评价内容

请求示例：

> http://localhost/ nggirl/app/cli/dresser/evaluateWork?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&workId=1234567& evaluateContent=赞一个

返回结果示例：

```json
{
	"code": 0,
	"data": {
		"evaluateUserId":1,
		"evaluateName": "王明",
		"evaluateProfile":" http://www.baidu.com/1.jpg",
		"evaluation":"非常喜欢，想来一个",
		"evaluateTime": 1435196075742,
	}
}
```

返回字段说明：

|字段名称|字段含义
|---|---
|Code	|错误码，0表示正确

<h2 id="9">9.作品分享成功</h2>

请求方法：nggirl/app/cli/dresser/shareSuccess

请求URL：接口地址/ nggirl/app/cli/dresser/shareSuccess

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌

请求示例：

> http://localhost/ nggirl/app/cli/dresser/shareSuccess?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0

返回结果示例：

```json
{
"code": 0,
"data":null
}
```

返回字段说明：

|字段名称|字段含义
|---|---
|Code	|错误码，0表示正确
|Data - evaluateUserId	|用户编号
|Data - evaluateName	|用户名
|Data - evaluateProfile	|头像路径
|Data - evaluation	|评价内容
|Data - evaluateTime	|评价时间
