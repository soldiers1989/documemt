<h1>渠道推广标识吗统计接口文档</h1>
目录


* [1.钱咖对接]
 * [1.1.钱咖上传通知接口](#1.1)
 * [1.2.对比接口](#1.2)
* [2.我们app相关接口]
 * [2.1.用户激活app上传信息接口V2.0.0](#2.1)
 * [2.2.统计转化率接口](#2.2)
* [3.智汇推相关接口]
 * [3.1.收集智汇推提供的APP点击数据](#3.1)



<h2 id="1.1">1.1.钱咖上传通知接口</h2>

> 当用户点击广告开始下载应用前，钱咖通过该接口通知广告主，并且把传过来的idfa相关信息上传到我们的服务其中。此接口正是为钱咖提供，以供其调用。钱咖通过返回的http状态码确认广告主是否收到通知，200表示成功。

![对接流程图](http://photosd.nggirl.com.cn/work/903b8fc1ac164b4996ce0a34ce11fb63.jpg)

请求接口：nggirl/app/channel/ad/qiankaNotify

HTTP请求方式：POST

应用请求参数：

|参数名|描述|
|---|---|
|appid|广告主应用在App Store的编号|
|idfa|点击广告的用户的idfa或者imei|
|ip|点击广告用户的ip|

请求示例：
> localhost/nggirl/app/channel/ad/qiankaNotify?appid=idfa=ap=


<h2 id="1.2">1.2.对比接口</h2>

> 钱咖需要本接口来获取某一个idfa是否下载过广告主的应用，当接收到钱咖发起的请求时，返回对比结果。

请求接口：nggirl/app/channel/ad/getCompareResult

支持格式：JSON

HTTP请求方式:POST

应用请求参数：

|参数名|描述|
|---|---|
|appid|广告主应用在AppStore的编号|
|idfa|idfa列表，多个以逗号','分割。钱咖一次查询最多发送1000个|

请求示例：

> localhost/nggirl/app/channel/ad/getCompareResult?appid=idfa=

返回结果为json格式，idfa已存在标识为1，不存在标识为0

```json
{
"5A58EF1E-EFE2-278D-94EE-8398498":1,
"5A58EF1E-EFE2-278D-94EE-2343454":0
}
```


<h2 id="2.1">2.1.用户激活app上传信息接口V2.0.0</h2>

> 用户打开我们的app，我们会获取到当前用户手机的uid（idfa或imei）以及设备类型，并把这些信息上传到服务器上.
> 这个版本增加了一个字段channelId渠道号（针对安卓，比如应用宝市场apk上传的渠道号是yingyongbao）。

请求接口：nggirl/app/channel/ad/saveAppInfo/2.0.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名|描述|
|---|---|
|uid|用户设备的idfa或者imei|
|deviceType|用户设备类型ios或android|
|channelId|渠道号|

请求示例：localhost/nggirl/app/channel/ad/saveAppInfo/2.0.0?uid=deviceType=channelId=

返回结果示例：

```json
{
  "code":0,
  "data":null
}
```


<h2 id="2.2">2.2.统计转化率接口</h2>

> 统计各个渠道用户下载到激活的转化率

请求接口：nggirl/app/channel/ad/getTransRate

支持格式：JSON

HTTP请求方式：GET

请求示例：localhost/nggirl/app/channel/ad/getTransRate

返回结果示例：

```json
{
  "code":0,
  "data":[{
    "channelName":"钱咖",
    "transRate":0.6
  },
  {
    "channelName":"广点通",
    "tansRate":0.5
  }
  ]
}
```

返回字段说明


|字段名称|字段含义|
|---|---|
|Code|错误码 0表示正确|
|Data - channelName|渠道名称|
|Data - transRate|转化率|

<h2 id="3.1">3.1.收集智汇推提供的APP点击数据</h2>

> 用户点击广告时，智汇推通过此接口把相关信息传给我们后台

请求接口：nggirl/app/channel/ad/uploadZhiHuiInfo

支持格式：JSON

HTTP请求方式：GET

请求参数：

|参数名称|参数含义|
|----|----|
|muid|设备id|
|click_time|点击时间的时间戳|
|click_id|智汇推后台生成的追踪id|
|appid|android为开放平台移动应用appid；ios为appleid|
|app_type|app类型：值为android或ios，注意为小写|
|advertiser_id|广告主id（智汇推后台提供）|

请求示例：localhost/nggirl/app/channel/ad/uploadZhiHuiInfo?muid=xxxxx&click_time=1406276499&appid=00000&click_id
=00000&app_type=android&advertiser_id=0000

返回结果示例：

```json
{
  "ret":0,
  "msg":"错误提示"
}
```
返回码为 0 标识正常接收，其他返回码标识错误，返回值不能是 302，目前错误码仅-1














