<h1>用户地址V2.5.0</h1>
目录

* [1.获取用户地址列表V2.5.0](#1)
* [2.新增用户地址V2.5.0](#2)
* [3.编辑用户地址V2.5.0](#3)
* [4.删除用户地址V1.5.0](#4)

<h2 id="1">1.获取用户地址列表V2.5.0</h2>

> 出参：添加省编号和省名称

请求方法：nggirl/app/cli/address/getAddressList/2.5.0

请求URL：接口地址/nggirl/app/cli/address/getAddressList/2.5.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌（必填）

请求示例：

> http://localhost/nggirl/app/cli/address/getAddressList/2.5.0?accessToken=

返回结果示例：

```json
{
    "code": 0,
    "data": [
        {
            "address": "乐乎城市青年社区",
            "id": 448,
            "provinceId": 1,
            "cityId": 1,
            "areaId": 7,
            "cityName": "北京市",
            "areaName": "昌平区",
            "bizName": "通州北苑",
            "detail": "乐乎",
            "provinceName": "北京",
            "cityCode":"100"
        },
        {
            "address": "乐乎城市青年社区",
            "id": 446,
            "provinceId": 1,
            "cityId": 1,
            "areaId": 7,
            "cityName": "北京市",
            "areaName": "昌平区",
            "bizName": "通州北苑",
            "detail": "乐乎",
            "provinceName": "北京",
            "cityCode":"100"
        },
        {
            "address": "乐乎城市",
            "id": 437,
            "provinceId": 1,
            "cityId": 1,
            "areaId": 7,
            "cityName": "北京市",
            "areaName": "昌平区",
            "bizName": "通州北苑",
            "detail": "乐乎",
            "provinceName": "北京",
            "cityCode":"100"
        },
        {
            "address": "北京市朝阳区团结湖(地铁站)",
            "id": 114,
            "provinceId": 1,
            "cityId": 1,
            "areaId": 3,
            "cityName": "北京市",
            "areaName": "朝阳区",
            "bizName": "团结湖",
            "detail": "5号楼",
            "provinceName": "北京",
            "cityCode":"100"
        },
        {
            "address": "金隅嘉华大厦",
            "id": 220,
            "provinceId": 1,
            "cityId": 1,
            "areaId": 4,
            "cityName": "北京市",
            "areaName": "海淀区",
            "bizName": "上地",
            "detail": "adfa",
            "provinceName": "北京",
            "cityCode":"100"
        },
        {
            "address": "北京市运通123路",
            "id": 142,
            "provinceId": 1,
            "cityId": 1,
            "areaId": -1,
            "cityName": "北京市",
            "areaName": "",
            "bizName": "",
            "detail": "理你",
            "provinceName": "北京",
            "cityCode":"100"
        },
        {
            "address": "SOHO嘉盛中心",
            "id": 119,
            "provinceId": 1,
            "cityId": 1,
            "areaId": 3,
            "cityName": "北京市",
            "areaName": "朝阳区",
            "bizName": "三里屯",
            "detail": "通知我",
            "provinceName": "北京",
            "cityCode":"100"
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
|Data - provinceId|省编号|
|Data - provinceName|省名称|
|Data - cityCode|市编号，用于高德地图详细地址查询


<h2 id="2">2.新增用户地址V2.5.0</h2>
>入参：增加省编号

请求方法：nggirl/app/cli/address/addAddress/2.5.0

请求URL：接口地址/nggirl/app/cli/address/addAddress/2.5.0

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
|provinceId|省编号（必填）|
请求示例：

> http://localhost/nggirl/app/cli/address/addAddress/2.5.0


返回结果示例：

```json
{
  "code":0,
  "data":null
  
}
```

<h2 id="3">3.编辑用户地址V2.5.0</h2>
>入参：增加省编号

请求方法：nggirl/app/cli/address/updateAddress/2.5.0

请求URL：接口地址/nggirl/app/cli/address/updateAddress/2.5.0

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
|provinceId|省编号（必填）|

请求示例：

> http://localhost/nggirl/app/cli/address/updateAddress/2.5.0

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

