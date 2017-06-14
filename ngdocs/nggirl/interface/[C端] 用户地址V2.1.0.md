<h1>用户地址V2.1.0</h1>
目录

* [1.获取用户地址列表V2.1.0](#1)
* [2.新增用户地址V1.5.0](#2)
* [3.编辑用户地址V1.5.0](#3)
* [4.删除用户地址V1.5.0](#4)

<h2 id="1">1.获取用户地址列表</h2>

> 出参：添加地址总数addressNum

请求方法：nggirl/app/cli/address/getAddressList/2.1.0

请求URL：接口地址/nggirl/app/cli/address/getAddressList/2.1.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌（必填）

请求示例：

> http://localhost/nggirl/app/cli/address/getAddressList/1.5.0?accessToken=

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "addressList": [
            {
                "address": "huahua100鲜花店(龙湖时代天街店)",
                "id": 30,
                "areaId": 9,
                "areaName": "渝中区",
                "cityName": "重庆",
                "detail": "gs",
                "bizName": "大坪",
                "cityId": 2
            },
            {
                "address": "FLIGHT(新燕莎金街购物广场)",
                "id": 16,
                "areaId": 1,
                "areaName": "东城区",
                "cityName": "北京",
                "detail": "j修改",
                "bizName": "王府井",
                "cityId": 1
            },
            {
                "address": "DDING STUDIO OF CHINA",
                "id": 17,
                "areaId": 40,
                "areaName": "越秀区",
                "cityName": "广州",
                "detail": "DDING STUDIO OF CHINA",
                "bizName": "建设",
                "cityId": 5
            },
            {
                "address": "中国人民解放军总医院",
                "id": 21,
                "areaId": 4,
                "areaName": "海淀区",
                "cityName": "北京",
                "detail": "中国人民解放军总医院",
                "bizName": "五棵松",
                "cityId": 1
            },
           
           
        ],
        "addressNum": 4
    }
}
```

返回字段说明：

|参数名称|参数含义|
|---|---|
|Code|错误标识码，0表示正确|
|Data -addressList- id|地址编号|
|Data -addressList- cityId|城市编号|
|Data -addressList- cityName|城市名称|
|Data -addressList- areaId|城区编号|
|Data -addressList- areaName|城区名称|
|Data -addressList- address|地址（地图api选的）|
|Data -addressList- detail|详细地址，楼号门牌号等|
|Data -addressList- bizName|商圈名称|
|Data - addressNum|地址数

<h2 id="2">2.新增用户地址</h2>

请求方法：nggirl/app/cli/address/addAddress/1.5.0

请求URL：接口地址/nggirl/app/cli/address/addAddress/1.5.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌（必填）|
|cityId|城市编号（必填）|
|areaName|城区名称（非必填）|
|address|地址（地图api选的）（必填）|
|detail|详细地址，楼号门牌号等（必填）|
|bizName|商圈名称（非必填）|
请求示例：

> http://localhost/nggirl/app/cli/address/addAddress/1.5.0

返回结果示例：

```json
{
  "code":0,
  "data":null
  
}
```

<h2 id="3">3.编辑用户地址</h2>

请求方法：nggirl/app/cli/address/updateAddress/1.5.0

请求URL：接口地址/nggirl/app/cli/address/updateAddress/1.5.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌（必填）|
|id|地址编号（必填）|
|cityId|城市编号（必填）|
|areaName|城区名称（非必填）|
|address|地址（地图api选的）（必填）|
|detail|详细地址，楼号门牌号等（必填）|
|bizName|商圈名称（非必填）|

请求示例：

> http://localhost/nggirl/app/cli/address/updateAddress/1.5.0

返回结果示例：

```json
{
  "code":0,
  "data":null
  
}
```

<h2 id="4">4.删除用户地址</h2>

请求方法：nggirl/app/cli/address/deleteAddress/1.5.0

请求URL：接口地址/nggirl/app/cli/address/deleteAddress/1.5.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌（必填）|
|id|地址编号（必填）|


请求示例：

> http://localhost/nggirl/app/cli/address/deleteAddress/1.5.0

返回结果示例：

```json
{
  "code":0,
  "data":null
  
}
```

