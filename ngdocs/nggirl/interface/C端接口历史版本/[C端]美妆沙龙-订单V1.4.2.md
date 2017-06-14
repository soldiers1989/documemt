#  美妆沙龙-订单V1.4.2
* [1. 我的订单V1.3.2](#1)
* [2. 订单详情（含订单流程）V1.4.2](#2)
* [3. 订单详情V1.4.2](#3)
* [4. 获取订单流程V1.4.2](#4)
* [5. 标识沙龙活动已完成](#5)
* [6. 获取作品进行中及待评价的数目](#6)
* [7. 获取上门化妆和美妆教学订单数](#7)
* [8. 对活动进行评价](#8)
* [9. 获取评价详情](#9)
* [10. 对活动投诉](#10)
* [11. 获取成团状态V1.3.2](#11)

<h2 id="1">1.我的订单V1.3.2：</h2>

请求方法：nggirl/app/cli/salon/reservation/list/1.3.2

请求URL：接口地址/nggirl/app/cli/salon/reservation/list/1.3.2

支持格式：JSON

HTTP请求方式：GET


应用请求参数：

|参数名称	|参数含义|
|---|---|
|accessToken|授权令牌|
|reservationStatus	|订单类型（1进行中，2待评价，3已完成）|
|page|页码，从0开始|
|num|页面大小，数据条数，默认为20|

请求示例：
> http://nggirl/app/cli/salon/reservation/list/1.3.2?accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&reservationStatus=1&page=0&num=20

返回结果示例：

```json
{
    "code": 0,
    "data":
            [
               {
                "unionResId": 2015103002708452,
                "unionProductId":111,
                "resType":1,
                "productCover":"http://photosd.nggirl.com.cn/work/fc3ba1e13b2140249802abbc044102d2.jpg",
                "price": 100,
                "peopleNum":3,
                "cost":300,
                "resStatus": 2,
                "resTime": "2015年10月30日 21:00 - 21:20",
                "createTime":"2015-10-11 16:00:00",
                "productTitle":"美妆下午茶——小白专场",
                "statusDesc":"本订单正在进行中",
                "dresserCover":"http://photosd.nggirl.com.cn/work/fc3ba1e13b2140249802abbc044102d2.jpg"
               },
         {
                "unionResId": 2015103002708452,
                "unionProductId":111,
                "resType":1,
                "productCover":"http://photosd.nggirl.com.cn/work/fc3ba1e13b2140249802abbc044102d2.jpg",
                "price": 100,
                "peopleNum":3,
                "cost":300,
                "resStatus": 2,
                "resTime": "2015年10月30日 21:00 - 21:20",
                "createTime":"2015-10-11 16:00:00",
                "productTitle":"美妆下午茶——小白专场",
                "statusDesc":"本订单正在进行中",
                "dresserCover":"http://photosd.nggirl.com.cn/work/fc3ba1e13b2140249802abbc044102d2.jpg"
               },
              {
                "unionResId": 2015103002708452,
                "unionProductId":111,
                "resType":1,
                "productCover":"http://photosd.nggirl.com.cn/work/fc3ba1e13b2140249802abbc044102d2.jpg",
                "price": 100,
                "peopleNum":1,
                "cost":100,
                "resStatus": 2,
                "resTime": "2015年10月30日 21:00 - 21:20",
                "createTime":"2015-10-11 16:00:00",
                "productTitle":"美妆下午茶——小白专场",
                "statusDesc":"本订单正在进行中",
                "dresserCover":"http://photosd.nggirl.com.cn/work/fc3ba1e13b2140249802abbc044102d2.jpg"
               }
    ]
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|Data - unionResId	|订单编号|
|Data - unionProductId|作品id|
|Data - resType|预约类型，1下午茶，2上门教学，3企业教学,4年会妆|
|Data - productCover	| 活动封面图片路径 |
|Data - price	| 费用 |
|Data - peopleNum |预约人数|
|Data - cost|总费用|
|Data - resStatus	| 见[美妆沙龙预约状态码](https://github.com/nggirl/ngdocs/blob/master/nggirl/interface/%E9%A2%84%E7%BA%A6%E7%8A%B6%E6%80%81%E7%A0%81.md#2美妆沙龙) |
|Data - resTime	| 预约日期 |
|Data - createTime|订单创建时间|
|Data - productTitle|产品标题|
|Data - statusDesc|状态描述|
|Data - dresserCover|化妆师头像|


<h2 id="2">2.订单详情(含订单流程)V1.4.2</h2>

>返回值：
>    添加：resFlowsByDate、couponMoney、deleted

请求方法：nggirl/app/cli/salon/reservation/orderFlowDetails/1.4.2

请求URL：接口地址/nggirl/app/cli/salon/reservation/orderFlowDetails/1.4.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义|
|---|---|
|accessToken|用户授权令牌|
|unionResId	|订单编号|
|resType|订单类型|


请求示例：
> http://nggirl/app/cli/salon/reservation/orderFlowDetails/1.4.2?accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&unionResId=2015082309836626

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "name": "薛云梦（海威）",
        "productTitle": "短信测试-zmy(10-20)",
        "praiseStar": null,
        "productCover": "http://photosd.nggirl.com.cn/work/e3124ffd0ae849fea8147b838a9d10f4.jpg",
        "couponMoney": 0,
        "unionResId": 2016012676380329,
        "dresserId": 58,
        "cost": 0,
        "deleted":0,
        "starLevel": 4,
        "praised": 0,
        "profile": "http://nggirl-product-res.oss-cn-beijing.aliyuncs.com/work/97161288e0b342848210acd806721896.jpg",
        "sex": 0,
        "resPlace": "点睡",
        "resStatus": 6,
        "statusDesc": "订单完成",
        "resType": 1,
        "resTime": "2016年01月26日 11:00-11:10",
        "price": 0,
        "peopleNum": 1,
        "unionProductId": 53,
        "resFlowsByDate":[
         	 {
                "recordDate": "2016.03.15",
                "reservationFlows": [
                    {
                        "majorDesc": "退款申请成功，正在退款中",
                        "minorDesc": "钱款将在1-3个工作日内退回至原账户，请注意查收",
                        "recordTime": 1458029454000
                    },
                    {
                        "majorDesc": "化妆师已接单，请尽快完成支付",
                        "minorDesc": "请在15分钟内完成支付",
                        "recordTime": 1458029235000
                    },
                    {
                        "majorDesc": "订单提交成功，请等待化妆师接单",
                        "minorDesc": "化妆师将在15分钟内确认您的订单",
                        "recordTime": 1458029215000
                    }
                ]
            },
            {
                "recordDate": "2016.03.16",
                "reservationFlows": [
                    {
                        "majorDesc": "退款申请成功，正在退款中",
                        "minorDesc": "钱款将在1-3个工作日内退回至原账户，请注意查收",
                        "recordTime": 1458029454000
                    },
                    {
                        "majorDesc": "化妆师已接单，请尽快完成支付",
                        "minorDesc": "请在15分钟内完成支付",
                        "recordTime": 1458029235000
                    },
                    {
                        "majorDesc": "订单提交成功，请等待化妆师接单",
                        "minorDesc": "化妆师将在15分钟内确认您的订单",
                        "recordTime": 1458029215000
                    }
                ]
            }
         ],
       }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|Data - dresserId	| 化妆师id |
|Data - unionProductId|产品id|
|Data - profile	| 化妆师头像图片 |
|Data - name	| 化妆师名称 |
|Data - sex	| 化妆师性别，0为男，1为女 |
|Data - starLevel	| 化妆师星级 |
|Data - price	| 活动费用 |
|Data - peopleNum	|预约人数  |
|Data - cost	|总计金额  |
|Data - deleted|上线状态，1为下线，0为在线|
|Data - resTime	| 预约日期 |
|Data - resPlace	|预约地址  |
|Data - praised	| 用户是否已经评价，0为未评价，1为已评价 |
|Data - resStatus	| 见[美妆沙龙预约状态码](https://github.com/nggirl/ngdocs/blob/master/nggirl/interface/%E9%A2%84%E7%BA%A6%E7%8A%B6%E6%80%81%E7%A0%81.md#2美妆沙龙)|
|Data - unionResId	| 预约编号 |
|Data - productCover|活动封面|
|Data - resType|预约类型|
|Data - productTitle	|作品标题  |
|Data - statusDesc|状态描述|
|data - couponMoney|南瓜券优惠价，为0表示没有用优惠券|
|data-resFlowsByDate-recordDate|预约流程-预约日期|
|data-resFlowsByDate-reservationFlows-majorDesc|预约流程-主描述|
|data-resFlowsByDate-reservationFlows-minorDesc |预约流程-次描述|
|data-resFlowsByDate-reservationFlows-recordTime|预约流程-流程时间|

<h2 id="3">3.订单详情V1.4.2</h2>

>返回值：
>    添加：couponMoney、deleted

请求方法：nggirl/app/cli/salon/reservation/orderDetails/1.4.2

请求URL：接口地址/nggirl/app/cli/salon/reservation/orderDetails/1.4.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义|
|---|---|
|accessToken|用户授权令牌|
|unionResId	|订单编号|
|resType|订单类型|


请求示例：
> http://nggirl/app/cli/salon/reservation/orderDetails/1.4.2?accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&unionResId=2015082309836626

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "name": "薛云梦（海威）",
        "productTitle": "短信测试-zmy(10-20)",
        "praiseStar": null,
        "productCover": "http://photosd.nggirl.com.cn/work/e3124ffd0ae849fea8147b838a9d10f4.jpg",
        "couponMoney": 0,
        "unionResId": 2016012676380329,
        "dresserId": 58,
        "cost": 0,
        "deleted":0,
        "starLevel": 4,
        "praised": 0,
        "profile": "http://nggirl-product-res.oss-cn-beijing.aliyuncs.com/work/97161288e0b342848210acd806721896.jpg",
        "sex": 0,
        "resPlace": "点睡",
        "resStatus": 6,
        "statusDesc": "订单完成",
        "resType": 1,
        "resTime": "2016年01月26日 11:00-11:10",
        "price": 0,
        "peopleNum": 1,
        "unionProductId": 53,
      }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|Data - dresserId	| 化妆师id |
|Data - unionProductId|产品id|
|Data - profile	| 化妆师头像图片 |
|Data - name	| 化妆师名称 |
|Data - sex	| 化妆师性别，0为男，1为女 |
|Data - starLevel	| 化妆师星级 |
|Data - price	| 活动费用 |
|Data - peopleNum	|预约人数  |
|Data - cost	|总计金额  |
|Data - deleted|上线状态，0为在线，1为下线|
|Data - resTime	| 预约日期 |
|Data - resPlace	|预约地址  |
|Data - praised	| 用户是否已经评价，0为未评价，1为已评价 |
|Data - resStatus	| 见[美妆沙龙预约状态码](https://github.com/nggirl/ngdocs/blob/master/nggirl/interface/%E9%A2%84%E7%BA%A6%E7%8A%B6%E6%80%81%E7%A0%81.md#2美妆沙龙)|
|Data - unionResId	| 预约编号 |
|Data - productCover|活动封面|
|Data - resType|预约类型|
|Data - productTitle	|作品标题  |
|Data - statusDesc|状态描述|
|data - couponMoney|南瓜券优惠价，为0表示没有用优惠券|

<h2 id="4">4.订单流程V1.4.2</h2>

请求方法：nggirl/app/cli/salon/reservation/orderFlow/1.4.2

请求URL：接口地址/nggirl/app/cli/salon/reservation/orderFlow/1.4.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义|
|---|---|
|accessToken|用户授权令牌|
|unionResId	|订单编号|
|resType|订单类型|


请求示例：
> http://nggirl/app/cli/salon/reservation/orderFlow/1.4.2?accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&unionResId=2015082309836626

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "resStatus":2,
        "resFlowsByDate":[
         	 {
                "recordDate": "2016.03.15",
                "reservationFlows": [
                    {
                        "majorDesc": "退款申请成功，正在退款中",
                        "minorDesc": "钱款将在1-3个工作日内退回至原账户，请注意查收",
                        "recordTime": 1458029454000
                    },
                    {
                        "majorDesc": "化妆师已接单，请尽快完成支付",
                        "minorDesc": "请在15分钟内完成支付",
                        "recordTime": 1458029235000
                    },
                    {
                        "majorDesc": "订单提交成功，请等待化妆师接单",
                        "minorDesc": "化妆师将在15分钟内确认您的订单",
                        "recordTime": 1458029215000
                    }
                ]
            },
            {
                "recordDate": "2016.03.16",
                "reservationFlows": [
                    {
                        "majorDesc": "退款申请成功，正在退款中",
                        "minorDesc": "钱款将在1-3个工作日内退回至原账户，请注意查收",
                        "recordTime": 1458029454000
                    },
                    {
                        "majorDesc": "化妆师已接单，请尽快完成支付",
                        "minorDesc": "请在15分钟内完成支付",
                        "recordTime": 1458029235000
                    },
                    {
                        "majorDesc": "订单提交成功，请等待化妆师接单",
                        "minorDesc": "化妆师将在15分钟内确认您的订单",
                        "recordTime": 1458029215000
                    }
                ]
            }
         ],
       }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|data -resStatus|订单当前状态|
|data-resFlowsByDate-recordDate|预约流程-预约日期|
|data-resFlowsByDate-reservationFlows-majorDesc|预约流程-主描述|
|data-resFlowsByDate-reservationFlows-minorDesc |预约流程-次描述|
|data-resFlowsByDate-reservationFlows-recordTime|预约流程-流程时间|

<h2 id="5">5. 标识沙龙活动已完成：</h2>
请求方法：nggirl/app/cli/salon/reservation/setCompleted/1.3

请求URL：接口地址/nggirl/app/cli/salon/reservation/setCompleted/1.3

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义|
|---|---|
|accessToken|用户授权令牌|
|unionResId	|订单编号|

请求示例：
> http://localhost/nggirl/app/cli/salon/reservation/setCompleted/1.3?accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&unionResId=2015082309836626

返回结果示例：

```json
{
    "data": "null",
    "code": 0
}
```

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|

<h2 id="6">6. 获取美妆沙龙中进行中和待评价数目：</h2>
请求方法：nggirl/app/cli/salon/reservation/getReservationNum/1.3

请求URL：接口地址/nggirl/app/cli/salon/reservation/getReservationNum/1.3

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义|
|---|---|
|accessToken	|用户授权令牌|



请求示例：
> http://localhost/nggirl/app/cli/salon/reservation/getReservationNum/1.3?accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0

返回结果示例：

```json
{
    "data": {
            "running":13,
            "notEvaluated" : 12
          },
    "code": 0
}
```

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|Data - -running	|进行中|
|Data - -notEvaluated	| 待评价|


<h2 id="7">7. 获取上门美妆和美妆沙龙订单数：</h2>
请求方法：nggirl/app/cli/salon/reservation/getSumResNum/1.3

请求URL：接口地址/nggirl/app/cli/salon/reservation/getSumResNum/1.3

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义|
|---|---|
|accessToken	|用户授权令牌|



请求示例：
> http://localhost/nggirl/app/cli/salon/reservation/getSumResNum/1.3?accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0

返回结果示例：

```json
{
    "data":{
            "teachNum":13,
            "salonNum":12
          },
    "code": 0
}
```

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|Data - -teachNum	| 上门美妆进行中和待评价总数|
|Data - -salonNum	| 美妆沙龙进行中和待评价总数|


<h2 id="8">8. 对活动进行评价：</h2>
请求方法：nggirl/app/cli/salon/reservation/evaluation/1.3

请求URL：接口地址/nggirl/app/cli/salon/reservation/evaluation/1.3

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义|
|---|---|
|accessToken	|用户授权令牌|
|unionResId	|订单编号|
|resType|预约类型|
|onTimeEvaluation|准时到达（1-5）|
|descriptionEvaluation|内容实用（1-5）|
|serviceEvaluation|服务周到（1-5）|
|tecniqueEvaluation|技法娴熟（1-5）|
|content|评价内容|
|photos|图片url(json格式字符串)|



请求示例：
> http://localhost/nggirl/app/cli/salon/reservation/evaluation/1.3?accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&unionResId=2015082309836626&content=挺好&resType=1&onTimeEvaluation=4&descriptionEvaluation=5&serviceEvaluation=3&tecniqueEvaluation=5&photos="["http://www.nggirl.com.cn","http://www.nggirl.com.cn"]"

返回结果示例：

```json
{
    "data":{
        "sumEvaluation":4
    },
    "code": 0
}
```

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|data - sumEvaluation	|汇总得分值|

<h2 id="9">9.获取评价详情：</h2>
请求方法：nggirl/app/cli/salon/reservation/praiseDetails/1.3

请求URL：接口地址/nggirl/app/cli/salon/reservation/praiseDetails/1.3

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义|
|---|---|
|accessToken|用户授权令牌|
|unionResId	|订单编号|
|resType	|预约类型|

请求示例：
> http://nggirl/app/cli/salon/reservation/praiseDetails/1.3?accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&unionResId=2015082309836626&resType=1

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
        "content":"特别细心，特别用心，见过最好的妆师",
        "evaluationTime":1438247918000,
        "photos":[
            "http://www.nggirl.com.cn",
            "http://www.nggirl.com.cn"
                ]
        }
}
```
返回字段说明：

|参数名称|参数含义
|---|---
|Code|错误码，0表示正确
|data - onTimeEvaluation|准时情况评价（1-5）
|data - descriptionEvaluation|描述一致情况评价（1-5）
|data - tecniqueEvaluation|技法娴熟情况评价（1-5）
|data - serviceEvaluation|服务态度情况评价（1-5）
|data - sumEvaluation|总分
|data - content|评价的内容
|data - evaluationTime|评价时间
|data - photos|图片的集合，为图片上传后返回的路径组成的json数组。示例：[“url”,”url”,”url”]

<h2 id="10">10. 对活动投诉：</h2>
请求方法：nggirl/app/cli/salon/reservation/complaints/1.3

请求URL：接口地址/nggirl/app/cli/salon/reservation/complaints/1.3

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义|
|---|---|
|accessToken	|用户授权令牌|
|unionResId	|订单编号|
|content|投诉内容|

请求示例：
> http://localhost/nggirl/app/cli/salon/reservation/complaints/1.3?accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&unionResId=2015082309836626&content=不好

返回结果示例：

```json
{
    "data": "null",
    "code": 0
}
```

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|


<h2 id="11">11. 获取成团状态V1.3.2 ：</h2>
请求方法：nggirl/app/cli/salon/reservation/groupStatus/1.3.2

请求URL：接口地址/nggirl/app/cli/salon/reservation/groupStatus/1.3.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义|
|---|---|
|accessToken	|用户授权令牌|
|unionResId	|订单编号|


请求示例：
> http://localhost/nggirl/app/cli/salon/reservation/groupStatus/1.3.2?accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&unionResId=2015082309836626

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "groupStatus": 0
    }
}
```

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|data -groupStatus |成团状态，0未成团，1成团|
