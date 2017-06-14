<h1>系统通用接口</h1>
目录

* [1.图片上传](#1)
* [2.多图片上传](#2)
* [3.字符串形式文件上传](#3)
* [4.支持的城市V2.0.0](#4)
* [5.城区列表](#5)
* [6.验证客户端授权令牌是否有效](#6)
* [7.获取安卓B端最新版信息](#7)
* [8.获取系统支持的妆束类型列表](#8)
* [9.获取最新版本信息 V1.3](#9)
* [10.图片压缩上传V1.3.2](#10)
* [11.文件上传](#11)
* [12.日签生成接口](#12)
* [13.获取全国城市列表V2.4.2](#13)
* [14.获取最新版本信息和软硬更新 V4.0.0](#14)


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
	"url":"http://nggirl-userres.oss-cn-beijing.aliyuncs.com/work/25affbc087ac471d98598d406591cbb8.png",
	"width":640,
	"height":640
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|Data - md5	|上传文件的md5码|
|Data - url	|上传后文件路径|
|Data - width	|图片宽度|
|Data - height	|图片高度|

<h2 id="2">2.多图片上传：</h2>

请求方法：uploadserver/app/image/uploads/multi

请求URL：接口地址/uploadserver/app/image/uploads/multi

支持格式：JSON

HTTP请求方式：POST


应用请求参数：

|参数名称	|参数含义|
|---|---|
|fileX	|上传的文件。多个文件的上传文件名不能同名！！|

请求示例：
> http://localhost/uploadserver/app/image/uploads/multi

返回结果示例：

```json
{
    "code": 0,
    "data": [{
        "md5":"F1D42BCFAB94A7EB4C59327011C9E5F4",
	"url":"http://nggirl-userres.oss-cn-beijing.aliyuncs.com/work/25affbc087ac471d98598d406591cbb8.png",
	"width":640,
	"height":640
    },{
        "md5":"F1D42BCFAB94A7EB4C59327011C9E5F4",
	"url":"http://nggirl-userres.oss-cn-beijing.aliyuncs.com/work/25affbc087ac471d98598d406591cbb8.png",
	"width":640,
	"height":640
    }]
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|Data - md5	|上传文件的md5码|
|Data - url	|上传后文件路径|
|Data - width	|图片宽度|
|Data - height	|图片高度|

<h2 id="3">3.字符串形式文件上传：</h2>

请求方法：uploadserver/app/image/uploads/paramtype

请求URL：接口地址/uploadserver/app/image/uploads/paramtype

支持格式：JSON

HTTP请求方式：POST


应用请求参数：

|参数名称	|参数含义|
|---|---|
|file	|上传图片文件的dataUrl字符串|

请求示例：
> http://localhost/uploadserver/app/image/uploads/paramtype

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "md5":"F1D42BCFAB94A7EB4C59327011C9E5F4",
	"url":"http://nggirl-userres.oss-cn-beijing.aliyuncs.com/work/25affbc087ac471d98598d406591cbb8.png",
	"width":640,
	"height":640
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|Data - md5	|上传文件的md5码|
|Data - url	|上传后文件路径|
|Data - width	|图片宽度|
|Data - height	|图片高度|

<h2 id="4">4.支持的城市V2.0.0：</h2>
> 返回值添加了一个citycode城市编码

请求方法：nggirl/app/supportedCity/2.0.0

请求URL：接口地址/nggirl/app/supportedCity/2.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：
|参数名称	|参数含义|
|---|---|
|accessToken	|用户授权令牌|

请求示例：

> http://localhost/nggirl/app/supportedCity/2.0.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0

返回结果示例：

```json
{
    "code": 0,
	"data": [{
		"id":1,
        "key":"B",
	    "city":"北京",
	    "citycode":"010"
	},{
		"id":2,
        "key":"C",
	    "city":"成都",
	    "citycode":"028"
	},{
		"id":3,
        "key":"C",
	    "city":"重庆",
	    "citycode":"023"
	},{
		"id":4,
        "key":"S",
	    "city":"上海",
	    "citycode":"021"
	},{
		"id":5,
        "key":"T",
	    "city":"天津",
	    "citycode":"022"
    }]
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - key	|城市的拼音首字母
|Data - city	|城市名称
|Data - citycode|城区编码（国家统一编码，和电话区号相同）

<h2 id="5">5.城区列表：</h2>

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

<h2 id="6">6.验证客户端授权令牌是否有效：</h2>

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

<h2 id="7">7.获取安卓B端最新版信息：</h2>

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

<h2 id="8">8.获取系统支持的妆束类型列表：</h2>

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



<h2 id="9">9. 获取最新版信息V1.3</h2>

请求方法：nggirl/app/version/latestInfo/1.3

请求URL：接口地址/nggirl/app/version/latestInfo/1.3

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|appType|app类型,枚举值。见以下说明（必填）
|market|应用市场，枚举值。见以下说明。当且仅当appType为安卓C端时为必填，其余情况不填）

app类型传入值为：

|appType传入值|意义
|---|---
|android-b|安卓B端
|android-c|安卓C端
|ios-b|IOS B端
|ios-c|IOS C端

应用市场market为用户应用下载来源。传入值需为以下值：

|market传入值|意义
|---|---
|huawei|华为
|baidu|百度
|wandoujia|豌豆荚
|xiaomi|小米
|yingyongbao|应用宝
|sougouzhushou|搜狗助手
|_360|360

请求示例：

> http://localhost/nggirl/app/version/latestInfo/1.3?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&appType=android-c&market=_360

返回结果示例：
```json
{
    "code": 0,
	"data": {
	        "appType":"android-b",
		"updateTime":"2015-04-12",
		"versionCode": 10002,
		"versionName": "1.0.2",
		"downloadUrl": " http://nggirl-product-res.oss-cn-beijing.aliyuncs.com/ngdresser-v1.0.2.apk",
		"market":"_360",
         	"updateLog": [
        	 {
                "id": 9,
                "seq": 1,
                "content": "【 Happy】“美妆沙龙”详情页效果升级，对图片失真say no！"
        	  },
        	 {
                "id": 10,
                "seq": 2,
                "content": "【New】傲娇产品汪为追求完美，调整了“资讯”和“美妆”位置。"
        	  },
        	 {
                "id": 11,
                "seq": 3,
                "content": "【Year】“晒单”功能超进化~晒出你的靓照，分分钟惊呆小伙伴！"
        	  },
        	 {
                "id": 12,
                "seq": 4,
                "content": "【新!】支持支付宝客户端支付啦！支付方式更easy。"
        	 },
        	 {
                "id": 13,
                "seq": 5,
                "content": "【年!】技术猴欧巴新年奋发图强，修复近100项BUG！南瓜小妹只想说：你咋不上天呢！"
        	 },
        	  {
                "id": 14,
                "seq": 6,
                "content": "【快!】“美妆沙龙”版块诞生！其实你只需一个下午茶的时间，化妆技巧就能up！up！up！"
        	 },
        	   {
                "id": 15,
                "seq": 7,
                "content": "【乐!】偷偷告诉你~新用户首次下单部分妆容可享受五折优惠！南瓜姑娘就是有钱任性。"
        	 },
        	  {
                "id": 16,
                "seq": 8,
                "content": "南瓜姑娘微信公众号也支持首单五折功能啦，下单渠道随你任性选~ \n欢迎小主们参加南瓜姑娘“后宫团”。作为试妆用户，协同南瓜姑娘完成化妆师的考核工作。如果您有意向，请关注“南瓜姑娘”微信公众号（nanguagirl)，回复“后宫团”，根据提示操作即可。\n意见和反馈欢迎向我们砸来！新浪微博@南瓜姑娘APP，南瓜姑娘微信号:nanguagirl"
                 }
                 ],
	}
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data -appType|app类型
|Data - updateTime	|更新时间
|Data - market	|应用市场
|Data - versionCode	|版本号（数字类型），每2位数字代表版本名称1位数字字符（当首位数字为0时省略首位）例：版本名为1.3.2，versionCode为10302，版名名为10.2.2时versionCode为100202
|Data - versionName	|版本名称
|Data - downloadUrl	|下载地址
|Data -updateLog | 更新说明
|data-updateLog -id |更新日志id
|data -updateLog -seq|日志排序编号
|data -updateLog -content|日志内容

<h2 id="10">10.图片上传V1.3.2：</h2>

请求方法：uploadserver/app/image/uploadsCompress

请求URL：接口地址/uploadserver/app/image/uploadsCompress

支持格式：JSON

HTTP请求方式：POST


应用请求参数：

|参数名称	|参数含义|
|---|---|
|file	|上传的文件。为上传文件表单name固定为file。|

请求示例：
> http://localhost/uploadserver/app/image/uploadsCompress

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "md5":"F1D42BCFAB94A7EB4C59327011C9E5F4",
	"url":"http://nggirl-userres.oss-cn-beijing.aliyuncs.com/work/25affbc087ac471d98598d406591cbb8.png",
	"width":640,
	"height":640
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|Data - md5	|上传文件的md5码|
|Data - url	|上传后文件路径|
|Data - width	|图片宽度|
|Data - height	|图片高度|


<h2 id="11">11.文件上传：</h2>

>主要用于传mp4格式视频

请求方法：uploadserver/app/file/upload

请求URL：接口地址/uploadserver/app/file/upload

支持格式：JSON

HTTP请求方式：POST


应用请求参数：

|参数名称	|参数含义|
|---|---|
|file	|上传的文件。为上传文件表单name固定为file。|

请求示例：
> http://localhost/uploadserver/app/file/upload

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "md5":"F1D42BCFAB94A7EB4C59327011C9E5F4",
	"url":"http://nggirl-userres.oss-cn-beijing.aliyuncs.com/work/25affbc087ac471d98598d406591cbb8.mp4",
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|Data - md5	|上传文件的md5码|
|Data - url	|上传后文件路径|

<h2 id="12">12.日签生成接口：</h2>

>将给定的src图片和foot图片合并成一张图片

请求方法：uploadserver/app/image/createDailyCheck

请求URL：接口地址/uploadserver/app/image/createDailyCheck

支持格式：JSON

HTTP请求方式：POST


应用请求参数：

|参数名称	|参数含义|
|---|---|
|srcImg	|日签图片
footImg |包含二维码和logo的图片（这里直接使用http://photosd.nggirl.com.cn/work/3888db27ab0b424d9ad0ea8e49eb9b72.jpg即可）

请求示例：
> http://localhost/uploadserver/app/file/upload

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "md5":"F1D42BCFAB94A7EB4C59327011C9E5F4",
	"url":"http://nggirl-userres.oss-cn-beijing.aliyuncs.com/work/25affbc087ac471d98598d406591cbb8.mp4",
	"width":573,
	"height":800
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|Data - md5	|上传文件的md5码|
|Data - url	|上传后文件路径|
|Data - width	|合成图片的宽度|
|Data - height	|合成图片的高度|

<h2 id="13">13.获取全国城市列表V2.4.2</h2>


请求方法：nggirl/app/allCommonCity/2.4.2

请求URL：接口地址/nggirl/app/allCommonCity/2.4.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：
|参数名称	|参数含义|
|---|---|


请求示例：

> http://localhost/nggirl/app/allCommonCity/2.4.2

返回结果示例：

```json
{
  "code": 0,
	"data": [{
	  "provinceId":1,
	  "provinceName":"北京",
	  "cities":[{
        "cityId":12,
        "cityName":"北京市",
        "cityKey":"010",
        "provinceId":"1",
        "cityCode":"0352"
      },{
      }]
	},{
	  "provinceId":3,
	  "provinceName":"河北省",
	  "cities":[{
        "cityId":12,
        "cityName":"廊坊市",
        "cityKey":"0316",
        "provinceId":"3",
        "cityCode":"0355"
      },{
        "cityId":13,
        "cityName":"文安县",
        "cityKey":"0317",
        "provinceId":"3",
        "cityCode":"0359"
      }]
	}]
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - provinceId	|省编号
|Data - provinceName	|省名称
|Data - cities|省内的城市列表
|Data - cities - cityId|城市编号
|Data - cities - cityName|城市名
|Data - cities - cityKey|城市名第一个字的拼音首字母
|Data - cities - provinceId|城市所属省编号


<h2 id="14">14.获取最新版本信息和软硬更新V4.0.0</h2>

>与 "9. 获取最新版信息V1.3" 接口相比 入参无变化,添加出参isHardUpdate

请求方法：nggirl/app/version/latestInfo/4.0.0

请求URL：接口地址/nggirl/app/version/latestInfo/4.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|appType|app类型,枚举值。见以下说明（必填）
|market|应用市场，枚举值。见以下说明。当且仅当appType为安卓C端时为必填，其余情况不填）

app类型传入值为：

|appType传入值|意义
|---|---
|android-b|安卓B端
|android-c|安卓C端
|ios-b|IOS B端
|ios-c|IOS C端

应用市场market为用户应用下载来源。传入值需为以下值：

|market传入值|意义
|---|---
|huawei|华为
|baidu|百度
|wandoujia|豌豆荚
|xiaomi|小米
|yingyongbao|应用宝
|sougouzhushou|搜狗助手
|_360|360

请求示例：

> http://localhost/nggirl/app/version/latestInfo/4.0.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&appType=android-c&market=_360

返回结果示例：
```json
{
    "code": 0,
	"data": {
	        "appType":"android-b",
		"updateTime":"2015-04-12",
		"versionCode": 10002,
		"versionName": "1.0.2",
		"isHardUpdate": 1,
		"downloadUrl": " http://nggirl-product-res.oss-cn-beijing.aliyuncs.com/ngdresser-v1.0.2.apk",
		"market":"_360",
         	"updateLog": [
        	 {
                "id": 9,
                "seq": 1,
                "content": "【 Happy】“美妆沙龙”详情页效果升级，对图片失真say no！"
        	  },
        	 {
                "id": 10,
                "seq": 2,
                "content": "【New】傲娇产品汪为追求完美，调整了“资讯”和“美妆”位置。"
        	  },
        	 {
                "id": 11,
                "seq": 3,
                "content": "【Year】“晒单”功能超进化~晒出你的靓照，分分钟惊呆小伙伴！"
        	  },
        	 {
                "id": 12,
                "seq": 4,
                "content": "【新!】支持支付宝客户端支付啦！支付方式更easy。"
        	 },
        	 {
                "id": 13,
                "seq": 5,
                "content": "【年!】技术猴欧巴新年奋发图强，修复近100项BUG！南瓜小妹只想说：你咋不上天呢！"
        	 },
        	  {
                "id": 14,
                "seq": 6,
                "content": "【快!】“美妆沙龙”版块诞生！其实你只需一个下午茶的时间，化妆技巧就能up！up！up！"
        	 },
        	   {
                "id": 15,
                "seq": 7,
                "content": "【乐!】偷偷告诉你~新用户首次下单部分妆容可享受五折优惠！南瓜姑娘就是有钱任性。"
        	 },
        	  {
                "id": 16,
                "seq": 8,
                "content": "南瓜姑娘微信公众号也支持首单五折功能啦，下单渠道随你任性选~ \n欢迎小主们参加南瓜姑娘“后宫团”。作为试妆用户，协同南瓜姑娘完成化妆师的考核工作。如果您有意向，请关注“南瓜姑娘”微信公众号（nanguagirl)，回复“后宫团”，根据提示操作即可。\n意见和反馈欢迎向我们砸来！新浪微博@南瓜姑娘APP，南瓜姑娘微信号:nanguagirl"
                 }
                 ],
	}
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data -appType|app类型
|Data - updateTime	|更新时间
|Data - market	|应用市场
|Data - versionCode	|版本号（数字类型），每2位数字代表版本名称1位数字字符（当首位数字为0时省略首位）例：版本名为1.3.2，versionCode为10302，版名名为10.2.2时versionCode为100202
|Data - versionName	|版本名称
|Data - isHardUpdate |是否硬更新(1 是, 2 否)
|Data - downloadUrl	|下载地址
|Data -updateLog | 更新说明
|data-updateLog -id |更新日志id
|data -updateLog -seq|日志排序编号
|data -updateLog -content|日志内容
