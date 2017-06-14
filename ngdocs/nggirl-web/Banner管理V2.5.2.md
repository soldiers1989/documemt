# Banner管理V2.5.2


* [1.banner图片的上传](#1)
* [2.获取banner列表V1.3.2](#2)
* [3.更新banner图片V2.4.0](#3)
* [4.添加banner图片V2.4.0](#4)
* [5.删除banner图片V1.3.2](#5)
* [6.发布首页BannerV1.3.2](#6)
* [7.获取首页已上线BannerV1.3.2](#7)
* [8.获取某一Banner详情V2.4.0](#8)
* [9.获取跳转类型V2.4.0](#9)
* [10.获取原生页面对应的H5跳转链接V2.4.0](#10)
* [11.发布积分商城BannerV2.5.2](#11)
* [12.获取积分商城已发布BannerV2.5.2](#12)


<h2 id="1">1.banner图片的上传</h2>

>`图片上传测试服务器请求地址：testphotos.nggirl.com.cn`

>`图片上传证书服务器请求地址：photos.nggirl.com.cn`

请求方法：/uploadserver/app/image/uploads

请求URL：服务器地址/uploadserver/app/image/uploads

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

参数名称	|参数含义
:------|:-------
file	|（必填）要上传的本地文件

请求示例：
`http://testphotos.nggirl.com.cn/uploadserver/app/image/uploads`

返回结果示例：

```json
{
    "data": {
        "url": "http://nggirl-product-res.oss-cn-beijing.aliyuncs.com/work/ba2510558f424780804ee62424045649.jpg",
        "md5": "7E6A2731829994AFA36E1ED1397FD210"
    },
    "code": 0
}
```
返回字段说明：

字段 | 说明
:------|:-------
Code	|错误码，0表示正确
Data - md5	|上传文件的md5码
Data - url	|上传后文件路径



<h2 id="2">2.获取banner列表V1.3.2</h2>

请求方法：nggirl-web/web/admin/banner/getBanners/1.3.2

请求URL：接口地址/nggirl-web/web/admin/banner/getBanners/1.3.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数意义|
|--|--|
|page|页数，默认第一页|
|num|每页条数,默认20|

请求示例：
`http://localhost/nggirl-web/web/admin/banner/getBanners/1.3.2?page=0&num=20`

返回结果示例：
```json
{
    "code": 0,
    "data": {
        "pageData": [
            {
                "scrollHeadId": 169,
                "photoUrl": "http://photosd.nggirl.com.cn/work/ccd7749cbd6949d18027584632ba0c5e.jpg",
                "webPageUrl": "http://cli.nggirl.com.cn/ng-mobile-web/tuiguang/activity_nggirl_gengmei.html",
                "shareContent": "南瓜姑娘倾情打造公主妆，8万花嫁礼包等你来拿！",
                "shareImage": "http://testphotosd.nggirl.com.cn/work/57a7be38accd466ba4b3fb949ceb6d73.jpg"
            },
            {
                "scrollHeadId": 174,
                "photoUrl": "http://photosd.nggirl.com.cn/work/92003948d430456185822964bfce6b91.jpg",
                "webPageUrl": "http://testcli1.nggirl.com.cn/nggirl-h5-test/testAccessTokenTansByApp.htm",
                "shareContent": "放肆学化妆--南瓜姑娘开通上门教学啦~",
                "shareImage": "http://testphotosd.nggirl.com.cn/work/57a7be38accd466ba4b3fb949ceb6d73.jpg"
            },
            {
                "scrollHeadId": 181,
                "photoUrl": "http://photosd.nggirl.com.cn/work/d88a4b796eed48b595d601a290a39adf.jpg",
                "webPageUrl": "http://testcli.nggirl.com.cn/nggirl/h5/mobile/focuscontent.html?contentId=89&title=%E5%9C%A3%E8%AF%9E%E8%8A%82%3D%E6%89%93%E6%8A%98%E5%AD%A3",
                "shareContent": "南瓜姑娘轮播图",
                "shareImage": "http://photosd.nggirl.com.cn/work/f63bd5d344f742e5903a26efe9b0ebba.jpg"
            }
        ],
        "totalPageNum": 6,
        "pageSize": 15,
        "currnetPageNum": 1
    }
}
```
返回字段说明：

字段 | 说明
:------|:-------
Code	|错误码，0表示正确
Data - pageData - scrollHeadId	|轮播头图id
Data - pageData - photoUrl	|头图图片地址
Data - pageData - webPageUrl	|跳转到的web页面链接地址。
Data - pageData - shareContent	|页面分享时的内容说明
Data - totalPageNum|总页数
Data - pageSize |每页大小
Data - currnetPageNum |当前页数

<h2 id="3">3.更新banner图片V2.4.0</h2>

>出参无变化，入参添加forwardtype、forwardkey字段

请求方法：nggirl-web/web/admin/banner/updateBanner/2.4.0

请求URL：接口地址/nggirl-web/web/admin/banner/updateBanner/2.4.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

参数名称	|参数含义
:------|:-------
scrollHeadId	|[必填]轮播头图id
photoUrl	|[必填]头图图片地址
webPageUrl	|跳转到的web页面链接地址。
shareContent|页面分享时的内容说明
shareImage |分享图片地址
forwardtype |跳转类型
forwardkey |跳转附加参数

请求示例：
`http://localhost/nggirl-web/web/admin/banner/updateBanner/2.4.0`

返回结果示例：
```json
{
    "data": null,
    "code": 0
}
```
返回字段说明：

字段 | 说明
:------|:-------
Code	| 错误码，0表示正确

<h2 id="4">4.添加banner图片V2.4.0</h2>

>出参无变化，入参添加forwardtype、forwardkey字段

请求方法：nggirl-web/web/admin/banner/addBanner/2.4.0

请求URL：接口地址/nggirl-web/web/admin/banner/addBanner/2.4.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

参数名称	|参数含义
:------|:-------
photoUrl	|[必填]头图图片地址
webPageUrl	|跳转到的web页面链接地址。
shareContent	|页面分享时的内容说明
shareImage|分享图片地址
forwardtype |跳转类型
forwardkey |跳转附加参数

请求示例：
`http://localhost/nggirl-web/web/admin/banner/addBanner/2.4.0`

返回结果示例：
```json
{
    "data": null,
    "code": 0
}
```
返回字段说明：

字段 | 说明
:------|:-------
Code	|错误码，0表示正确

<h2 id="5">5.删除banner图片V1.3.2</h2>

>若要删除Banner正在上线，则不能删除

请求方法：nggirl-web/web/admin/banner/deleteBanner/1.3.2

请求URL：接口地址/nggirl-web/web/admin/banner/deleteBanner/1.3.2

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

参数名称	|参数含义
:------|:-------
scrollHeadId	|（必填）轮播头图id

请求示例：
`http://localhost/nggirl-web/web/admin/banner/deleteBanner?scrollHeadId=111`

返回结果示例：
```json
{
    "data": null,
    "code": 0
}
```
返回字段说明：

字段 | 说明
:------|:-------
Code	|错误码，0表示正确


<h2 id="6">6.发布首页BannerV1.3.2</h2>

请求方法：nggirl-web/web/admin/banner/online/1.3.2

请求URL：接口地址/nggirl-web/web/admin/banner/online/1.3.2

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

参数名称	|参数含义
:------|:-------
scrollHeadIds	|（必填）要上线的Banner的id字符串集合（用","分割）

> 参数scrollHeadIds只能有6个id数字

请求示例：
`http://localhost/nggirl-web/web/admin/banner/online/1.3.2?scrollHeadIds=181,111,112,113,114,115`

返回结果示例：
```json
{
    "data": null,
    "code": 0
}
```
返回字段说明：

字段 | 说明
:------|:-------
Code	|错误码，0表示正确

<h2 id="7">7.获取首页已上线BannerV1.3.2</h2>

请求方法：nggirl-web/web/admin/banner/getOnlineBanner/1.3.2

请求URL：接口地址/nggirl-web/web/admin/banner/getOnlineBanner/1.3.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：无

请求示例：
`http://localhost/nggirl-web/web/admin/banner/getOnlineBanner/1.3.2`

返回结果示例：
```json
{
    "code": 0,
    "data": [
        169,
        173,
        174,
        175,
        176,
        181
    ]
}
```
返回字段说明：

字段 | 说明
:------|:-------
Code	|错误码，0表示正确
Data|上线的Banner的id,按Banner排序


<h2 id="8">8.获取某一Banner详情V2.4.0</h2>

>入参无变化，出参添加forwardtype、forwardkey字段

请求方法：nggirl-web/web/admin/banner/getDetails/2.4.0

请求URL：接口地址/nggirl-web/web/admin/banner/getDetails/2.4.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

参数名称	|参数含义
:------|:-------
id	|banner的id


请求示例：
`http://localhost/nggirl-web/web/admin/banner/getDetails/2.4.0?id=181`

返回结果示例：
```json
{

    "code": 0,
    "data": {
        "scrollHeadId": 174,
        "photoUrl": "http://photosd.nggirl.com.cn/work/92003948d430456185822964bfce6b91.jpg",
        "webPageUrl": "http://testcli1.nggirl.com.cn/nggirl-h5-test/testAccessTokenTansByApp.htm",
        "shareContent": "放肆学化妆--南瓜姑娘开通上门教学啦~",
        "shareImage": "http://testphotosd.nggirl.com.cn/work/57a7be38accd466ba4b3fb949ceb6d73.jpg",
        "forwardtype":"atorder",
        "forwardkey":""
    }
}
```
返回字段说明：

字段 | 说明
:------|:-------
Code	|错误码，0表示正确
Data - scrollHeadId	|轮播头图id
Data - photoUrl	|头图图片地址
Data - webPageUrl	|跳转到的web页面链接地址。
Data - shareContent	|页面分享时的内容说明
Data - forwardtype |跳转类型
Data - forwardkey |跳转附加参数

<h2 id="9">9.获取跳转类型V2.4.0</h2>

请求方法：nggirl-web/web/admin/banner/getForwardTypes/2.4.0

请求URL：接口地址/nggirl-web/web/admin/banner/getForwardTypes/2.4.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：无

请求示例：
`http://localhost/nggirl-web/web/admin/banner/getForwardTypes/2.4.0`

返回结果示例：
```json
{

    "code": 0,
    "data": [
      {
        "forwardtype":"special",
        "forwardtypeName":"美妆专题页面(原生页面)",
        "forwardkey":"specialId=123&specialName=青春特辑",
        "forwardkeyDesc":"specialId是专题id",
        "isForwardkeyRequired":1
      }
    ]
}
```
返回字段说明：

字段 | 说明
:------|:-------
Code	|错误码，0表示正确
Data - forwardtype	|跳转类型
Data - forwardtypeName	|跳转类型名称
Data - forwardkey	|跳转参数
Data - forwardkeyDesc	|跳转参数描述
Data – isForwardkeyRequired|forwardkey是否必填，1必填，0不填写

<h2 id="10">10.获取原生页面对应的H5跳转链接V2.4.0</h2>

请求方法：nggirl-web/web/admin/banner/getForwardH5Url/2.4.0

请求URL：接口地址/nggirl-web/web/admin/banner/getForwardH5Url/2.4.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

参数名称	|参数含义
:------|:-------
forwardtype |跳转类型
forwardkey |跳转附加参数


请求示例：
`http://localhost/nggirl-web/web/admin/banner/getForwardH5Url/2.4.0`

返回结果示例：
```json
{

    "code": 0,
    "data": {
      "h5url":"http://testcli.nggirl.com.cn/nggirl/h5/cosmetic/indexLookMore.html?columnId=40"
    }
}
```
返回字段说明：

字段 | 说明
:------|:-------
Code	|错误码，0表示正确
Data - h5url	| 原生页面对应的H5跳转链接


<h2 id="11">11.发布积分商城BannerV2.5.2</h2>

请求方法：nggirl-web/web/admin/banner/scoreShopBannerOnline/2.5.2

请求URL：接口地址/nggirl-web/web/admin/banner/scoreShopBannerOnline/2.5.2

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

参数名称	|参数含义
:------|:-------
scrollHeadIds	|（必填）要上线的Banner的id字符串集合（用","分割）

> 参数scrollHeadIds只能有6个id数字

请求示例：
`http://localhost/nggirl-web/web/admin/banner/scoreShopBannerOnline/2.5.2?scrollHeadIds=181,111,112,113,114,115`

返回结果示例：
```json
{
    "data": null,
    "code": 0
}
```
返回字段说明：

字段 | 说明
:------|:-------
Code	|错误码，0表示正确

<h2 id="12">12.获取积分商城已发布BannerV2.5.2</h2>

请求方法：nggirl-web/web/admin/banner/getScoreShopOnlineBanner/2.5.2

请求URL：接口地址/nggirl-web/web/admin/banner/getScoreShopOnlineBanner/2.5.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：无

请求示例：
`http://localhost/nggirl-web/web/admin/banner/getScoreShopOnlineBanner/2.5.2`

返回结果示例：
```json
{
    "code": 0,
    "data": [
        169,
        173,
        174,
        175,
        176,
        181
    ]
}
```
返回字段说明：

字段 | 说明
:------|:-------
Code	|错误码，0表示正确
Data|上线的Banner的id,按Banner排序
