<h1>作品</h1>
目录

* [1.获取作品列表V1.5.0](#1)
* [2.获取作品详情V1.5.0](#2)
* [3.获取评价总数](#3)
* [4.获取作品评论](#4)
* [5.获取喜欢的人总数](#5)
* [6.获取喜欢的人](#6)
* [7.删除作品](#7)
* [8.发布作品V1.1.0](#8)
* [9.获取装束类型列表](#9)
* [10.获取装束标签列表](#10)
* [11.获取化妆品品类列表](#11)
* [12.获取化妆品品牌列表](#12)
* [13.修改作品信息V1.1.0](#13)


<h2 id="1">1.获取作品列表V1.5.0</h2>

>1.5.0添加是否是预置作品的返回值isFixed

请求方法：nggirl/app/bus/works/listWorks/1.5.0

请求URL：接口地址/nggirl/app/bus/works/listWorks/1.5.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|page	|页数  非必需参数，默认第一页
|num	|每页信息数目 非必需参数，默认20

请求示例：

> http://localhost/nggirl/app/bus/works/listWorks/1.1.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&page=0&num=20

返回结果示例：

```json
{
   "code": 0,
   "data": [{
		"workId": 1234567,
		"cover":" http://www.baidu.com/1.jpg",
		"workType":"职业装",
		"cost":100,
		"praiseNum":12,
		"auditStatus":0,
		"isFixed":0
	},
	{
		"workId": 1234567,
		"cover":" http://www.baidu.com/1.jpg",
		"workType":"职业装",
		"cost":100,
		"praiseNum":12,
		"auditStatus":1,
		"isFixed":1
       }]
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - workId	|作品编号
|Data - cover	|封面图片路径
|Data - workType|作品类型
|Data - workName	|妆束名称
|Data - cost	|费用
|Data - praiseNum|点赞人数
|Data - auditStatus|作品审核状态，0审核中，1审核通过。
|Data - isFixed|标记作品是否为预置作品，0非预置，1预置。预置作品不允许编辑



<h2 id="2">2.获取作品详情V1.5.0</h2>
>1.5.0添加是否是预置作品的返回值isFixed

请求方法：nggirl/app/bus/works/getWorksDetail/1.5.0

请求URL：接口地址/nggirl/app/bus/works/getWorksDetail/1.5.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|workId	|作品编号

请求示例：

> http://localhost/nggirl/app/bus/works/getWorksDetail/1.5.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP& accessToken =5db6ad15a16d3424845adb1ab8172e42066120f0&workId=123456

返回结果示例：

```json
{
   "code": 0,
    "data": {
		"workId": 1234567,
		"cover":" http://www.baidu.com/1.jpg",
		"workType":"职业装",
		"cost":100,
		"reservationNum":3,
		"timeUsed":60,
		"contentPhoto":[
				"http://www.baidu.com/1.jpg"，
				"http://www.baidu.com/1.jpg"
],
"descriptions":"肤质较佳的女生。强调重点：强调眼唇重点。以润色隔离霜作为底妆，然后以睫毛膏…….",
		"cosmetics": [{
				"cosmeticsClass":"粉底液",
				"cosmeticsBrand": ["Dior迪奥","香奈儿chanel"]
},
{
				"cosmeticsClass":"粉饼",
				"cosmeticsBrand": ["glo&ray","巴宝莉Burberry"]
}],
		"tags":["小清新","森女","欧美风","英伦"],
		"auditStatus":1,
		"workName":"青春昂扬的魅力",
		"isFixed":1
	}
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - workId	|作品编号
|Data - cover	|封面图片路径
|Data - workType	|作品类型
|Data - workName	|妆束名称
|Data - cost	|费用
|Data - reservationNum	|预约人数
|Data - timeUsed	|作品耗时，以分钟为单位
|Data - contentPhoto|其他图片的路径列表
|Data -  descriptions|作品描述
|Data - cosmetics|使用的化妆品信息
|Data –cosmetics - cosmeticsClass	|化妆品品类
|Data –cosmetics - cosmeticsBrand|化妆品品牌列表
|Data -  tags|作品标签列表
|Data - auditStatus|作品审核状态，0审核中，1审核通过。
|Data - isFixed|标记作品是否为预置作品，0非预置，1预置。预置作品不允许编辑



<h2 id="3">3.获取评论总数</h2>

请求方法：nggirl/app/bus/works/getEvaluationCount

请求URL：接口地址/nggirl/app/bus/works/getEvaluationCount

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义
|---|---
|accessToken|用户授权令牌
|workId|作品编号

请求示例：

> http://localhost/nggirl/app/bus/works/getEvaluationCount?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP& accessToken =5db6ad15a16d3424845adb1ab8172e42066120f0&workId=1234567

返回结果示例：

```json
{
"code": 0,
"data": {
	"count":10
	}
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - code	|评价总数

<h2 id="4">4.获取作品评价</h2>

请求方法：nggirl/app/bus/works/listWorkEvaluation

请求URL：接口地址/nggirl/app/bus/works/listWorkEvaluation

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|workId|作品编号
|page|页数 非必须参数，默认第一页
|num|每页信息数目，非必须参数，默认20

请求示例：

> http://localhost/nggirl/app/bus/works/listWorkEvaluation?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP& accessToken =5db6ad15a16d3424845adb1ab8172e42066120f0&workId=1234567&page=0&num=20

返回结果示例：

```json
{
"code": 0,
"data": [{
		"evaluateUserId":1,
		"evaluateName": "王明",
		"evaluateProfile":" http://www.baidu.com/1.jpg",
		"evaluateContent":"非常喜欢，想来一个",
		"evaluateTime": 1435196075742,
	},
	{
		"evaluateUserId":1,
		"evaluateName": "王明",
		"evaluateProfile":" http://www.baidu.com/1.jpg",
		"evaluateContent":"非常喜欢，想来一个",
		"evaluateTime": 1435196075742,
       }]
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确,1表示用户未注册
|Data - evaluateUserId	|用户编号
|Data - evaluateName|用户名
|Data - evaluateProfile|头像路径
|Data - evaluation|评价内容
|Data - evaluateTime|评论时间

<h2 id="5">5.获取喜欢的人总数</h2>

请求方法：nggirl/app/bus/works/getLoverCount

请求URL：接口地址/nggirl/app/bus/works/getLoverCount

支持格式：JSON

HTTP请求方式：POST
应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|workId	|作品编号

请求示例：

> http://localhost/nggirl/app/bus/works/getLoverCount?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&workId=1234567

返回结果示例：

```json
{
   "code": 0,
   "data": {
	"count":2
	},
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - count|喜欢的人总数

<h2 id="6">6.获取喜欢的人</h2>

请求方法：nggirl/app/bus/works/listWorkLover

请求URL：接口地址/nggirl/app/bus/works/listWorkLover

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|workId|作品编号
|page|页数 非必须参数，默认第一页
|num|每页信息数目，非必须参数，默认20

请求示例：

> http://localhost/nggirl/app/bus/works/listWorkLover?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP& accessToken =5db6ad15a16d3424845adb1ab8172e42066120f0&workId=1234567&page=0&num=20

返回结果示例：

```json
{
 "code":0,
 "data": [{
		"loverUserId":1,
		"loverName": "王明",
		"loverProfile":" http://www.baidu.com/1.jpg"
	},
	{
		"loverUserId":1,
		"loverName": "丽丽",
		"loverProfile":" http://www.baidu.com/1.jpg"
       }]
}
```
返回字段说明

|参数名称|参数含义
|---|---
|Code|错误码，0表示正确
|Data - loverUserId|用户编号
|Data - loverName|用户名
|Data - loverProfile|头像路径

<h2 id="7">7.删除作品</h2>

请求方法：nggirl/app/bus/works/deleteWork

请求URL：接口地址/nggirl/app/bus/works/deleteWork

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|workId	|作品编号


请求示例：

> http://localhost/ nggirl/app/bus/works/deleteWork?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP& accessToken =5db6ad15a16d3424845adb1ab8172e42066120f0&workId=1234567

返回结果示例：

```json
{
    "code": 0,
    "data":null
}

```
返回字段说明

|参数名称|参数含义
|---|---
|Code|错误码，0表示正确


<h2 id="8">8.发布作品V1.1.0</h2>

请求方法：nggirl/app/bus/works/publishWork/1.1.0

请求URL：接口地址/nggirl/app/bus/works/publishWork/1.1.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|workType	|妆束类型
|workName	|妆束名称
|timeUsed|化妆用时
|cost|费用
|tags|作品标签（多个标签用空格分隔的一个字符串）
|descriptions|化妆说明
|cosmetics|使用的化妆品（json格式的数组字符串）
|cover|作品封面图片，为上传图片后返回的路径。
|contentPhoto|作品内容图片，为上传文件后返回路径组成的json数组。示例：["url","url","url"]
cosmetics示例（说明参见获取作品详情）：
```json
[{
				"cosmeticsClass":"粉底液",
				"cosmeticsBrand": ["Dior迪奥","香奈儿chanel"]
},
{
				"cosmeticsClass":"粉饼",
				"cosmeticsBrand": ["glo&ray","巴宝莉Burberry"]
}]
```


请求示例：

> http://localhost/nggirl/app/bus/works/publishWork/1.1.0

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


<h2 id="9">9.获取装束类型列表</h2>

请求方法：nggirl/app/bus/works/listDressTypes

请求URL：接口地址/nggirl/app/bus/works/listDressTypes

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌


请求示例：

> http://localhost/nggirl/app/bus/works/listDressTypes?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0

返回结果示例：

```json
{
   "code": 0,
    "data": ["职业妆","约会妆","年会妆","Party妆     ","特殊造型妆","VIP定制"]
}
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data|妆束类型列表

<h2 id="10">10.获取装束标签列表</h2>

请求方法：nggirl/app/bus/works/ listDressTags

请求URL：接口地址/nggirl/app/bus/works/listDressTags

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|page	|页数 ,非必需参数，默认第一页
|num| 每页信息数目 ,非必须参数，默认20


请求示例：

> http://localhost/nggirl/app/bus/works/listDressTags?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&page=0&num=20

返回结果示例：

```json
{
   "code": 0,
    "data": ["赫本","韩式公主","小清新","欧美风","英伦"]
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data|标签列表

<h2 id="11">11.获取化妆品品类列表</h2>
参见注册（服务端）接口

<h2 id="12" >12. 获取化妆品品牌列表</h2>
参见注册（服务端）接口

<h2 id="13">13. 修改作品信息V1.1.0</h2>

请求方法：nggirl/app/bus/works/updateWork/1.1.0

请求URL：接口地址/nggirl/app/bus/works/updateWork/1.1.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|workId|作品编号
|workType|妆束类型
|workName|妆束名称
|timeUsed|化妆用时
|cost|费用
|tags|作品标签（多个标签用空格分隔的一个字符串）
|descriptions|化妆说明
|cosmetics|使用的化妆品（json格式的数组字符串
||作品封面图片，为上传文件表单name固定为cover。
||作品内容图片，为上传文件表单name固定为contentPhoto?,问号是一个整数值，多个作品内容图片不同名

cosmetics示例（说明参见获取作品详情）：
```json
[{
				"cosmeticsClass":"粉底液",
				"cosmeticsBrand": ["Dior迪奥","香奈儿chanel"]
},
{
				"cosmeticsClass":"粉饼",
				"cosmeticsBrand": ["glo&ray","巴宝莉Burberry"]
}]
```



请求示例：
> http://localhost/ nggirl/app/bus/works/updateWork/1.1.0

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
