
# 日程V1.1.1(B端)

> 跟随C端V1.4.2

* [1. 获取某个月可预约时间段V1.1.1](#1)
* [2. 设置一系列时间段预约状态V1.1.1](#2)
* [3. 设置一系列日期全天预约状态V1.1.1](#3)


<h2 id="1" >1.获取某个月可预约时间段V1.1.1</h2>

> 预约时间由可预约1个月改为6个月，此接口返回传入年月所有可预约时间段，若为当月，返回当月余下所有可预约时间段。

请求方法：nggirl/app/bus/schedule/listResTimeByMonth/1.1.1

请求URL：接口地址/nggirl/app/bus/schedule/listResTimeByMonth/1.1.1

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|month|年月,数字（1-6），1表示本月，2表示下个月，6表示第6个月

请求示例：

> http://localhost/nggirl/app/bus/schedule/listResTimeByMonth/1.1.1?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&month=2

返回结果示例：

```json
{
   "code": 0,
   "data": {
    "monthStatus": -1,
    "reservationDates": [
            {
                "realDate": "20160401",
                "reservationDate": "03.28 周一",
                "reservationTimes": [
                    {
                        "name": "17:00 - 17:20",
                        "status": 1
                    },
                    {
                        "name": "17:20 - 17:40",
                        "status": 1
                    },
                    {
                        "name": "20:40 - 21:00",
                        "status": 1
                    },
                    {
                        "name": "21:00 - 21:20",
                        "status": 1
                    },
                    {
                        "name": "21:20 - 21:40",
                        "status": 1
                    },
                    {
                        "name": "21:40 - 22:00",
                        "status": 1
                    },
                ]
            },
            {
                "realDate": "20160402",
                "reservationDate": "03.29 周二",
                "reservationTimes": [
                    {
                        "name": "06:00 - 06:20",
                        "status": 1
                    },
                    {
                        "name": "06:20 - 06:40",
                        "status": 1
                    },
                    {
                        "name": "14:40 - 15:00",
                        "status": 1
                    },
                    {
                        "name": "15:00 - 15:20",
                        "status": 1
                    },
                    {
                        "name": "16:40 - 17:00",
                        "status": 1
                    },
                    {
                        "name": "17:00 - 17:20",
                        "status": 1
                    }
                ]
            }
         ]
       }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - monthStatus|请求月份状态，-1表示当月，0表示中间月，1表示最后一月
|Data -reservationDates- reservationDate	|预约日期 （用于显示在移动端的）
|Data -reservationDates- reservationTimes	|时段
|Data -reservationDates- realDate | 所代表的真实日期 “20160121” 标准八位字符串（用于传给后台的，方便处理）
|Data -reservationDates- reservationTimes-name|时段名
|Data -reservationDates- reservationTimes-status|时段状态，0不可预约，1可预约，2有订单


<h2 id="2" >2.设置一系列时间段预约状态V1.1.1</h2>

>设置某天某些时间段预约状态

请求方法：nggirl/app/bus/schedule/setStatusByTimes/1.1.1

请求URL：接口地址/nggirl/app/bus/schedule/setStatusByTimes/1.1.1

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|resDateTimes|预约日期时间段，json数组格式，为包含预约日期及状态组成的集合

>resDateTimes格式示例：
```json
     [
            {
                "realDate": "20160401",
                "reservationTimes": [
                    {
                        "name": "17:00 - 17:20",
                        "status": 1
                    },
                    {
                        "name": "17:20 - 17:40",
                        "status": 1
                    },
                    {
                        "name": "20:40 - 21:00",
                        "status": 1
                    },
                    {
                        "name": "21:00 - 21:20",
                        "status": 1
                    },
                    {
                        "name": "21:20 - 21:40",
                        "status": 1
                    },
                    {
                        "name": "21:40 - 22:00",
                        "status": 1
                    },
                ]
            },
            {
                "realDate": "20160402",
                "reservationTimes": [
                    {
                        "name": "06:00 - 06:20",
                        "status": 1
                    },
                    {
                        "name": "06:20 - 06:40",
                        "status": 1
                    },
                    {
                        "name": "14:40 - 15:00",
                        "status": 1
                    },
                    {
                        "name": "15:00 - 15:20",
                        "status": 1
                    },
                    {
                        "name": "16:40 - 17:00",
                        "status": 1
                    },
                    {
                        "name": "17:00 - 17:20",
                        "status": 1
                    }
                ]
            }
   ]
 ```

请求示例：

> http://localhost/nggirl/app/bus/schedule/setStatusByTimes/1.1.1?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&resDateTimes=[ {"realDate": "20160328","reservationTimes": ["name": "17:00 - 17:20","status": 1},{"name": "17:20 - 17:40", "status": 1 } ]},{"realDate": "20160329","reservationTimes": [{"name": "06:00 - 06:20","status": 1 }  ] }]

返回结果示例：
```json
{
  "code":0,
  "data":"null"
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确


<h2 id="3" >3.设置一系列日期全天预约状态V1.1.1</h2>

>将某些天设为全天可约或不可约

请求方法：nggirl/app/bus/schedule/setStatusByDates/1.1.1

请求URL：接口地址/nggirl/app/bus/schedule/setStatusByDates/1.1.1

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|resDates|一系列预约日期，格式为yyyyMMdd,每个用","（逗号）分隔
|status|预约状态，0为不可预约，1为可预约

>resDates 示例：20160312,20160313,20160317

请求示例：

> http://localhost/nggirl/app/bus/schedule/setStatusByTimes/1.1.1?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&resDates=20160312,20160313,20160317&status=1

返回结果示例：
```json
{
  "code":0,
  "data":"null"
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
