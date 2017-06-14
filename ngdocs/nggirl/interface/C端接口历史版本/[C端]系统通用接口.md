<h1>系统通用接口</h1>
目录

* [1.图片上传](#1)
* [2.支持的城市](#2)
* [3.城区列表](#3)
* [4.验证客户端授权令牌是否有效](#4)
* [5.获取安卓B端最新版信息](#5)
* [6.获取系统支持的妆束类型列表](#6)


<h2 id="1">1.图片上传：</h2>

请求方法：uploadserver/app/image/uploads

请求URL：接口地址/uploadserver/app/image/uploads

支持格式：JSON

HTTP请求方式：POST


应用请求参数：

|参数名称	|参数含义|
|---|---|
|file	|上传的文件。为上传文件表单name固定为file。|

请求示例：
> http://localhost/uploadserver/app/image/uploads

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "md5":"F1D42BCFAB94A7EB4C59327011C9E5F4",
	    "url":"http://nggirl-userres.oss-cn-beijing.aliyuncs.com/work/25affbc087ac471d98598d406591cbb8.png"
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|Data - md5	|上传文件的md5码|
|Data - url	|上传后文件路径|

<h2 id="2">2.支持的城市：</h2>

请求方法：nggirl/app/supportedCity

请求URL：接口地址/nggirl/app/supportedCity

支持格式：JSON

HTTP请求方式：GET

应用请求参数：
|参数名称	|参数含义|
|---|---|
|accessToken	|用户授权令牌|

请求示例：

> http://localhost/nggirl/app/supportedCity?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0

返回结果示例：

```json
{
    "code": 0,
	"data": [{
		"id":1,
        "key":"B",
	    "city":"北京"
	},{
		"id":2,
        "key":"C",
	    "city":"成都"
	},{
		"id":3,
        "key":"C",
	    "city":"重庆"
	},{
		"id":4,
        "key":"S",
	    "city":"上海"
	},{
		"id":5,
        "key":"T",
	    "city":"天津"
    }]
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - key	|城市的拼音首字母
|Data - city	|城市名称

<h2 id="3">3.城区列表：</h2>

请求方法：nggirl/app/cityArea

请求URL：接口地址/nggirl/app/cityArea

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|cityId	|城市编号

请求示例：

> http://localhost/nggirl/app/cityArea?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&cityId=1

返回结果示例：

```json
{
    "code": 0,
	"data": [{
		"id":1,
	    "name":"东城区"
	},{
		"id":2,
	    "name":"西城区"
	},{
		"id":3,
	    "name":"朝阳区"
	},{
		"id":4,
	    "name":"海淀区"
	},{
		"id":5,
	    "name":"丰台区"
    }]
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - id	|城区编号
|Data - name	|城区名称

<h2 id="4">4.验证客户端授权令牌是否有效：</h2>

请求方法：nggirl/app/cli/checkAccessToken

请求URL：接口地址/nggirl/app/cli/checkAccessToken

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌

请求示例：

> http://localhost/nggirl/app/cli/checkAccessToken?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0

返回结果示例：
```json
{
    "code": 0,
	"data": null
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示有效，1表示无效

<h2 id="5">5.获取安卓B端最新版信息：</h2>

请求方法：nggirl/app/version/lastestInfo

请求URL：接口地址/nggirl/app/version/lastestInfo

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌

请求示例：

> http://localhost/nggirl/app/cityArea?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0

返回结果示例：
```json
{
    "code": 0,
	"data": {
		"appType":"android-b",
		"updateTime":"2015年04月12日",
		"versionCode": "1.0.2",
		"versionName": "1.0.2",
		"downloadUrl": " http://nggirl-product-res.oss-cn-beijing.aliyuncs.com/ngdresser-v1.0.2.apk",
		"updateLog": "1.更改欢迎页图片（应用宝首发闪屏）2. 更换启动icon图标 3. 解决修改`个人资料`时昵称为空仍可以保存的错误 4. 优化作品详情页面作品图的显示效果（显示原图）"
	}
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - appType	|App类型
|Data - updateTime	|更新时间
|Data - versionCode	|版本代码
|Data - versionName	|版本名称
|Data - downloadUrl	|下载地址

<h2 id="6">6.获取系统支持的妆束类型列表：</h2>

请求方法：nggirl/app/sys/listWorkTypes

请求URL：接口地址/nggirl/app/sys/listWorkTypes

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|

请求示例：

> http://localhost/nggirl/app/sys/listWorkTypes?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：
```json
{
    "code": 0,
	"data": [{
		"typeName":"职业妆",
		"pictureSelected":"http://nggirl-product-res.oss-cn-beijing.aliyuncs.com/sysres/dressTypeImage/makeup-list-1-hl",
		"pictureUnselected": "http://nggirl-product-res.oss-cn-beijing.aliyuncs.com/sysres/dressTypeImage/makeup-list-1"
	},
	{
	    "typeName":"Party妆",
		"pictureSelected":"http://nggirl-product-res.oss-cn-beijing.aliyuncs.com/sysres/dressTypeImage/makeup-list-1-hl",
		"pictureUnselected": "http://nggirl-product-res.oss-cn-beijing.aliyuncs.com/sysres/dressTypeImage/makeup-list-1"
	}]
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - typeName	|妆束类型
|Data - pictureSelected	|选中的高亮图片
|Data - pictureUnselected	|没有选中的灰度图片

> 备注：要获取2x图片使用pictureSelected+@180w_180h.png，要获取3x图片使用pictureSelected+@340w_340h.png，要获取安卓的图使用pictureSelected+@340w_340h.png
