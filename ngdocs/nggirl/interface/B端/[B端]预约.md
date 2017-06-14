# <h1>预约</h1>
目录

* [1.获取预约列表](#1)
* [2.预约详情](#2)
* [3.预约数量](#3)
* [4.拒绝](#4)
* [5.接单](#5)
* [6.订单列表](#6)
* [7.订单详情](#7)
* [8.过往列表](#8)
* [9.过往详情](#9)
* [10.获取评价](#10)



<h2 id="1">1.获取预约列表</h2>

请求方法：nggirl/app/bus/reservation/listReservation

请求URL：接口地址/nggirl/app/bus/reservation/listReservation

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|page	|页数,非必需参数，默认第一页
|num	|每页信息数目，非必须参数，默认20

请求示例：

> http://localhost/nggirl/app/bus/reservation/listReservation?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP& accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&page=0&num=20

返回结果示例：

```json
{
    "code": 0,
    "data": [{
		"reservationId": 1234567,
		"userName":"晓丽",
		"profile":" http://www.baidu.com/1.jpg",
		"reservationType":"预约职业装",
		"cost":100,
		"reservationTime": "2015年5月20日 8:00-12:00",
		"reservationAddress":"北京市朝阳区立汤路龙德紫金",
	},
	{
		"reservationId": 1234567,
		"userName":"王明",
		"profile":" http://www.baidu.com/1.jpg",
		"reservationType":"预约职业装",
		"cost":100,
		"reservationTime": "2015年5月20日 8:00-12:00",
		"reservationAddress":"北京市朝阳区立汤路龙德紫金",
       }]
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - orderId	|订单号
|Data - userName	|订单用户名
|Data - profile	|订单用户头像地址
|Data - orderType	|订单装束类型
|Data - cost	|费用
|Data - orderTime	|订单约定时间段
|Data - reservationAddress|预约地点
|Data - orderAddress|订单地点
|Data - status|订单状态，0预约初始状态,1已取消，2已结算，3已接收，4已拒绝，5已完成
|Date - lastUpdateTime|最后修改时间，如果status为已接收时，此值为接单时间；如果status为已支付时，此值为支付时间。
|Data - systemTime|系统当前时间
|Data - payType|1微信支付，2支付宝支付



<h2 id="2">2.订单详情</h2>

请求方法：nggirl/app/bus/reservation/getReservationDetail

请求URL：接口地址/nggirl/app/bus/reservation/getReservationDetail

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|reservationId	|预约单号


请求示例：

> http://localhost/nggirl/app/bus/reservation/getReservationDetail?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&reservationId=1234567

返回结果示例：

```json
{
    "code": 0,
    "data": {
		"reservationId": 1234567,
		"userName":"晓丽",
		"profile":" http://www.baidu.com/1.jpg",
		"reservationType":"预约职业装",
		"cost":100,
		"reservationTime": "2015年5月20日 8:00-12:00",
		"reservationAddress":"北京市朝阳区立汤路龙德紫金",
	}
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - reservationId	|预约单号
|Data - userName	|预约用户名
|Data - profile	|预约用户头像地址
|Data - reservationType	|预约装束类型
|Data - cost	|费用
|Data - reservationTime	|预约时间段
|Data - reservationAddress	|预约地点


<h2 id="3">3. 预约数量</h2>

请求方法：nggirl/app/bus/reservation/getReservationCount

请求URL：接口地址/nggirl/app/bus/reservation/getReservationCount

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|dresserId	|化妆师编号

请求示例：

> http://localhost/nggirl/app/bus/reservation/getReservationCount?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&dresserId=1234567

返回结果示例：

```json
{
	"code": 0,
    "data": {
        "count":5
	}
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - count	|未被处理的预约数量

<h2 id="4">4.拒绝</h2>

请求方法：nggirl/app/bus/reservation/rejectReservation

请求URL：接口地址/nggirl/app/bus/ reservation/ rejectReservation

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|[必填]用户授权令牌
|reservationId|[必填]预约单号
|reason	|[选填]取消原因

>reason拒单原因字段，是在1.4.1版本新添加的，在当前版本中可以为空

请求示例：

> http://localhost/nggirl/app/bus/reservation/getDetail?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&reservationId=1234567

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


<h2 id="5">5. 接单</h2>

请求方法：nggirl/app/bus/reservation/acceptReservation

请求URL：接口地址 /nggirl/app/bus/reservation/acceptReservation

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|reservationId	|预约单号

请求示例：

> http://localhost/nggirl/app/bus/reservation/acceptReservation?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&reservationId=1234567

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

<h2 id="6">6.订单列表</h2>

请求方法：nggirl/app/bus/reservation/listOrder

请求URL：接口地址/nggirl/app/bus/reservation/ listOrder

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|page	|页数,非必需参数，默认第一页
|num|每页信息数目,非必须参数，默认20

请求示例：

> http://localhost/nggirl/app/bus/reservation/listOrder?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&page=0&num=20

返回结果示例：

```json
{
"code": 0,
    "data":[{
		"orderId": 1234567,
		"userName":"李斯",
		"profile":" http://www.baidu.com/1.jpg",
		"orderType":"预约职业装",
		"cost":100,
		"orderTime": "2015年5月20日 8:00-12:00",
		"orderAddress":"北京市朝阳区立汤路龙德紫金",
		"status":1,
"lastUpdateTime":1435196075742,
"systemTime":1435196075742,
"payType":1
	},
	{
		"orderId": 1234567,
		"userName":"晓丽",
		"profile":" http://www.baidu.com/1.jpg",
		"orderType":"预约职业装",
		"cost":100,
		"orderTime": "2015年5月20日 8:00-12:00",
		"orderAddress":"北京市朝阳区立汤路龙德紫金",
		"status":2,
"lastUpdateTime":1435196075742,
"systemTime":1435196075742,
"payType":2
       }]
}
```
返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - orderId|定单号
|Data - userName|订单用户名
|Data - profile|订单用户头像地址
|Data - orderType|订单装束类型
|Data - cost|费用
|Data - orderTime|订单约定时间段
|Data - orderAddress|订单地点
|Data - status|	订单状态，0预约初始状态,1已取消，2已结算，3已接收，4已拒绝，5已完成
|Date - lastUpdateTime|最后修改时间，如果status为已接收时，此值为接单时间；如果status为已支付时，此值为支付时间。
|Data - systemTime|系统当前时间
|Data - payType|1微信支付，2支付宝支付

<h2 id="7">7.订单详情</h2>

请求方法：nggirl/app/bus/reservation/getOrderDetail

请求URL：接口地址 /nggirl/app/bus/reservation/getOrderDetail

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|orderId	|定单号


请求示例：

> http://localhost/nggirl/app/bus/reservation/getOrderDetail?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&orderId= 1234567

返回结果示例：

```json
{
    "code": 0,
    "data": {
		"orderId": 1234567,
		"userName":"李斯",
		"profile":" http://www.baidu.com/1.jpg",
		"orderType":"预约职业装",
		"cost":100,
		"orderTime": "2015年5月20日 8:00-12:00",
		"orderAddress":"北京市朝阳区立汤路龙德紫金",
		"status":1,
        "lastUpdateTime":1435196075742,
        "systemTime":1435196075742,
        "imAccount":"client_552642a7de202",
        "phoneNum":"13426129466",
        "payType":1
	}
}
```

返回字段说明：
|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - reservationId|预约单号
|Data - userName|预约用户名
|Data - profile|预约用户头像地址
|Data - orderType|预约装束类型
|Data - cost|费用
|Data - reservationTime|预约时间段
|Data - reservationAddress|预约地点
|Data - status|	订单状态，0预约初始状态,1已取消，2已结算，3已接收，4已拒绝，5已完成
|Date - lastUpdateTime|最后修改时间，如果status为已接收时，此值为接单时间；如果status为已支付时，此值为支付时间。
|Data - systemTime|系统当前时间
|Data - imAccount|环信账号
|Data - phoneNum|用户电话
|Data - payType|1微信支付，2支付宝支付


<h2 id="8">8.过往列表</h2>

请求方法：nggirl/app/bus/reservation/listHistory

请求URL：接口地址/nggirl/app/bus/ reservation/ listHistory

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|page	|页数,非必需参数，默认第一页
|num	|每页信息数目,非必须参数，默认20


请求示例：

> http://localhost/nggirl/app/bus/reservation/listHistory?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP& accessToken =5db6ad15a16d3424845adb1ab8172e42066120f0&page=0&num=20

返回结果示例：

```json
{
    "code": 0,
    "data": [{
		"reservationId": 1234567,
		"userName":"晓丽",
		"profile":" http://www.baidu.com/1.jpg",
		"reservationType":"预约职业装",
		"cost":100,
		"reservationTime": "2015年5月20日 8:00-12:00",
		"reservationAddress":"北京市朝阳区立汤路龙德紫金",
        "status":1,
        "lastUpdateTime":1435196075742,
        "systemTime":1435196075742,
        "payType":1
	},
	{
		"reservationId": 1234567,
		"userName":"张三",
		"profile":" http://www.baidu.com/1.jpg",
		"reservationType":"预约职业装",
		"cost":100,
		"reservationTime": "2015年5月20日 8:00-12:00",
		"reservationAddress":"北京市朝阳区立汤路龙德紫金",
        "status":2,
        "lastUpdateTime":1435196075742,
        "systemTime":1435196075742,
        "payType":2
       }]
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - reservationId	|预约单号
|Data - userName	|预约用户名
|Data - profile	|预约用户头像地址
|Data - reservationType	|预约装束类型
|Data - cost	|费用
|Data - reservationTime	|预约时间段
|Data - reservationAddress|预约地点
|Data - status|预约单状态，0预约初始状态,1已取消，2已结算，3已接收，4已拒绝，5已完成
|Date - lastUpdateTime|最后修改时间，如果status为已接收时，此值为接单时间；如果status为已支付时，此值为支付时间。
|Data - systemTime|系统当前时间
|Data - payType|1微信支付，2支付宝支付


<h2 id="9">9.过往详情</h2>

请求方法：nggirl/app/bus/reservation/getHistoryDetail

请求URL：接口地址/nggirl/app/bus/reservation/getHistoryDetail

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|reservationId|定单号


请求示例：

> http://localhost/nggirl/app/bus/reservation/getHistoryDetail?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&reservationId=1234567

返回结果示例：

```json
{
    "code": 0,
    "data": {
		"reservationId": 1234567,
		"userName":"晓丽",
		"profile":" http://www.baidu.com/1.jpg",
		"reservationType":"预约职业装",
		"cost":100,
		"reservationTime": "2015年5月20日 8:00-12:00",
		"reservationAddress":"北京市朝阳区立汤路龙德紫金",
		"status":1,
        "lastUpdateTime":1435196075742,
        "systemTime":1435196075742,
        "imAccount":"client_552642a7de202",
        "phoneNum":"13426129466",
        "payType":1
	}
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - reservationId	|预约单号
|Data - userName	|预约用户名
|Data - profile	|预约用户头像地址
|Data - reservationType	|预约装束类型
|Data - cost	|费用
|Data - reservationTime	|预约时间段
|Data - reservationAddress|预约地点
|Data - status|预约单状态，0预约初始状态,1已取消，2已结算，3已接收，4已拒绝，5已完成
|Date - lastUpdateTime|最后修改时间，如果status为已接收时，此值为接单时间；如果status为已支付时，此值为支付时间。
|Data - systemTime|系统当前时间
|Data - imAccount|环信账号
|Data - phoneNum|用户电话
|Data - payType|1微信支付，2支付宝支付

<h2 id="10">10. 获取评价</h2>

请求方法：nggirl/app/bus/reservation/getReservationEvaluate

请求URL：接口地址/nggirl/app/bus/reservation/getReservationEvaluate

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|reservationId|预约的单号


请求示例：

> http://localhost/nggirl/app/bus/reservation/getReservationEvaluate?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&reservationId=10000

返回结果示例：

```json
{
    "code": 0,
    "date":{
    "onTimeEvaluation":4,
    "descriptionEvaluation":5,
    "tecniqueEvaluation":5,
    "serviceEvaluation":3,
    "sumEvaluation":4,
    "evaluation":"特别细心，特别用心，见过最好的妆师",
    "evaluationTime":1438247918000,
    "photos":[
    "http://www.nggirl.com.cn",
    "http://www.nggirl.com.cn"
    ]
    }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|onTimeEvaluation |准时情况评价（1-5）
|descriptionEvaluation|描述一致情况评价（1-5）
|tecniqueEvaluation|技法娴熟情况评价（1-5）
|serviceEvaluation|服务态度情况评价（1-5）
|evaluation|评价的内容
|evaluationTime|评价时间
|photos|图片的集合，为图片上传后返回的路径组成的json数组。示例：[“url”,”url”,”url”]
