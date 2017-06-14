<h1>用户地址V1.5.0</h1>
目录

* [1.获取用户地址列表](#1)
* [2.新增用户地址](#2)
* [3.编辑用户地址](#3)
* [4.删除用户地址](#4)


<h2 id="1">1.获取用户地址列表</h2>

请求方法：nggirl/app/cli/address/getAddressList/1.5.0

请求URL：接口地址/nggirl/app/cli/address/getAddressList/1.5.0

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
    "code":0,
    "data":[
          {
          "id":1,
          "cityId":1,
          "cityName":"北京市",
          "areaId":3,
          "areaName":"朝阳区",
          "address":"北京市朝阳区soho嘉盛中西",
          "detail":"2006",
          "bizName":"三里屯"
          },
          {
          "id":2,
          "cityId":1,
          "cityName":"北京市",
          "areaId":3,
          "areaName":"朝阳区",
          "address":"北京市朝阳区soho嘉盛中西",
          "detail":"2006",
          "bizName":"三里屯"
          },
          {
          "id":3,
          "cityId":1,
          "cityName":"北京市",
          "areaId":3,
          "areaName":"朝阳区",
          "address":"北京市朝阳区soho嘉盛中西",
          "detail":"2006",
          "bizName":"三里屯"
          }
    ]
}
```

返回字段说明：

|参数名称|参数含义|
|---|---|
|Code|错误标识码，0表示正确|
|Data - id|地址编号|
|Data - cityId|城市编号|
|Data - cityName|城市名称|
|Data - areaId|城区编号|
|Data - areaName|城区名称|
|Data - address|地址（地图api选的）|
|Data - detail|详细地址，楼号门牌号等|
|Data - bizName|商圈名称|

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

