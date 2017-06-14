# C端广告展示接口

* [1. 随机获取广告信息](#1)
* [2. 上报广告成功展示](#2)


<h2 id="1" >1. 随机获取广告信息</h2>

> 成功调用此接口一次即表明完成一次广告展示

请求方法：nggirl/app/cli/advert/getAdRandomly

请求URL：接口地址/nggirl/app/cli/advert/getAdRandomly

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|字段名称|字段含义
|---|---|
|deviceType  |设备类型,1为安卓，2为IOS
|screenWidth|屏幕宽度，数值
|screenHeight|屏幕高度，数值


请求示例：

> http://localhost/nggirl/app/cli/advert/getAdRandomly?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&deviceType=1&screenWidth=600&screenHeight=800

返回结果示例：

```json
{
    "code": 0,
    "data":{
    	"adId": 1234567,
    	"photo":"http://www.baidu.com/1.jpg",
    	"photoWidth":600,
    	"photoHeight":800,
    	"hasLink":1,
    	"linkUrl":"http://www.baidu.com/1.jpg",
	}

}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code  |0表示正确
|data - adId|广告编号
|data - photo|广告图片
|data - photoWidth|图片宽度
|data - photoHeight|图片高度
|data - hasLink|图片点击是否有链接，1为是，0为否
|data - linkUrl	|图片链接地址

>若haslink为0，则linkUrl为null


<h2 id="2" >2.上报广告成功展示 </h2>

> 此接口暂时被废弃，获取广告信息即为成功展示

请求方法：nggirl/app/cli/advert/report

请求URL：接口地址/nggirl/app/cli/advert/report

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|字段名称|字段含义
|---|---|
|adId  |广告编号


请求示例：

> http://localhost/nggirl/app/cli/advert/report?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&adId=12

返回结果示例：

```json
{
    "code": 0,
    "data":"null"
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code  |0表示正确














