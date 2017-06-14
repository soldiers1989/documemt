<h1>日签V2.5.3</h1>

目录

* [1.获取日签页详情V3.1.0](#1)
* [2.获取签到日历V2.3.0](#2)
* [3.签到V2.3.0](#3)
* [4.开启或者关闭推送V2.3.0](#4)
* [5.获取日签排行榜V2.4.2](#5)
* [6.获取补签日历V2.5.2](#6)
* [7.补签V2.5.2](#7)
* [8.往期商品V3.1.0](#8)


<h2 id="1">1.获取日签页详情V3.1.0</h2>

>出参删除tb_item_id、tb_detail_url，添加productDetailType

请求方法：nggirl/app/cli/personalInfo/getCheckinPage/3.1.0

请求URL：接口地址/nggirl/app/cli/personalInfo/getCheckinPage/3.1.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|[必填]用户授权令牌

请求示例：
> http://localhost/nggirl/app/cli/personalInfo/getCheckinPage/3.1.0?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：

```json
{
    "code": 0,
    "data":{
      "checkinId":1,
      "checkinPicture":"http://photosd.nggirl.com.cn/work/ee1f4aeef9eb4acc877de10b6012441c.jpg",
      "sharePicture":"http://photosd.nggirl.com.cn/work/ee1f4aeef9eb4acc877de10b6012441c.jpg",
      "shareContent":"分享出去的内容！",
      "dayCount":6,
      "checkinHint":"连续签到7天将获得xxx奖励",
      "isCheckedIn":1,
      "isAllowPush":1,
      "recheckCardNum":1,
      "score":100,
      "details":[
        {
            "type":1,
            "content":"副标题",
            "descrip":"",
            "extend":"",
            "seedProductId":0,
            "name":"",
            "picture":"",
            "price":0,
            "seedNum":0,
            "isSeed":0,
            "recommendation":0,
            "productDetailType":1,
            "isAllowBuy":0
        },
        {
            "type":3,
            "content":"http://photosd.nggirl.com.cn/work/ee1f4aeef9eb4acc877de10b6012441c.jpg",
            "descrip":"",
            "extend":"320_480",
            "seedProductId":0,
            "name":"",
            "picture":"",
            "price":0,
            "seedNum":0,
            "isSeed":0,
            "recommendation":0,
            "productDetailType":1,
            "isAllowBuy":0
        },{
            "type":5,
            "content":"1",
            "descrip":"",
            "extend":"",
            "seedProductId":1,
            "name":"精美春装",
            "picture":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
            "price":20,
            "seedNum":90,
            "isSeed":0,
            "recommendation":5,
            "productDetailType":1,
            "isAllowBuy":1
        }
      ]
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|Data - checkinId | 日签id |
|Data - checkinPicture	|日签图片|
|Data - sharePicture	|分享出去的图片|
|Data - shareContent	|分享出去的内容|
|Data - dayCount |已经连续签到天数|
|Data - isCheckedIn	|今天是否已签到，1已签到，0未签到|
|Data - isAllowPush	|用户是否允许定时推送签到消息，1允许，0不允许|
|Data - recheckCardNum	|用户可用补签卡数量|
|Data - score	|用户当前积分|
|Data - details	|商品信息及描述|
|Data - details	- type	|元素类型,1标题，3图片，5商品|
|Data - details	- content	|元素内容 1标题-标题内容，3图片-图片url|
|Data - details	- descrip	|元素描述 1标题-空，3图片-空|
|Data - details	- extend	|扩展字段，1标题-空，3图片-图片宽_高(320_320)|
|Data - details - seedProductId|商品编号|
|Data - details - name|商品名称|
|Data - details - picture|商品图|
|Data - details - price|价格|
|Data - details - seedNum|种草人数|
|Data - details - isSeed|是否已种草，0未种草，1已种草|
|Data - details - recommendation|推荐度，0-10|
|Data - details - productDetailType|跳转商品详情类型，1老版本商品种草页面，2新版本商品详情页面|
|Data - details - isAllowBuy|0不可购买，1可购买|

<h2 id="2">2.获取签到日历V2.3.0</h2>

请求方法：nggirl/app/cli/personalInfo/getCheckinCalendar/2.3.0

请求URL：接口地址/nggirl/app/cli/personalInfo/getCheckinCalendar/2.3.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|[必填]用户授权令牌

请求示例：
> http://localhost/nggirl/app/cli/personalInfo/getCheckinCalendar/2.3.0?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：

```json
{
    "code": 0,
    "data":{
      "yearMonth":"2016-7",
      "calendar":[
        {
          "monthType":1,
          "day":31,
          "isCheckedIn":0,
          "isToday":0,
          "isShowGift":0,
        },
        {
          "monthType":2,
          "day":1,
          "isCheckedIn":1,
          "isToday":1,
          "isShowGift":0,
        },
        {
          "monthType":2,
          "day":2,
          "isCheckedIn":0,
          "isToday":0,
          "isShowGift":0,
        }
      ]
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - yearMonth |当前年月
|Data - calendar |日历
|Data - calendar - monthType|当前日期的月份类型，1上一月，2本月，3下一月
|Data - calendar - day |本月第几号
|Data - calendar - isCheckedIn	|本日是否已签到，1已签到，0未签到
|Data - calendar - isToday	|本日是否是今天，1是今天，0不是今天
|Data - calendar - isShowGift	|是否显示礼品图标，1显示，0不显示

<h2 id="3">3.签到V2.3.0</h2>

请求方法：nggirl/app/cli/personalInfo/checkin/2.3.0

请求URL：接口地址/nggirl/app/cli/personalInfo/checkin/2.3.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|[必填]用户授权令牌
|udid	|[必填]用户的设备编号，ios使用idfa，安卓使用imei

请求示例：
> http://localhost/nggirl/app/cli/personalInfo/checkin/2.3.0?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：

```json
{
    "code": 0,
    "data":{
      "type":2,
      "userScore":150,
      "info":"同一台设备每天只能签到一次！",
      "score":20,
      "couponTitle":"南瓜券",
      "faceValue":30,
      "fitProduct":"仅限上门美妆使用",
      "limitPrice":199,
      "giftTitle":"恭喜您已获得",
      "giftInfo":"额外的美妆大礼包奖励",
      "giftTips":"加微信号领取礼包（微信号：nggirl_yunying）"
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - type |提示类型，0文本提醒，1积分提醒，2南瓜券提醒，3美妆大礼包提醒
|Data - userScore |用户当前总积分数
|Data - info |[type=0]提醒内容
|Data - score |[type=1]用户获得的积分数
|Data - couponTitle |[type=2]优惠券标题
|Data - faceValue |[type=2]优惠券面值
|Data - fitProduct |[type=2]优惠券适用类型
|Data - limitPrice |[type=2]优惠券最低消费限额
|Data - giftTitle |[type=3]礼包标题
|Data - giftInfo |[type=3]礼包提示信息
|Data - giftTips |[type=3]礼包备注



<h2 id="4">4.开启或者关闭推送V2.3.0</h2>

请求方法：nggirl/app/cli/personalInfo/changePushStatus/2.3.0

请求URL：接口地址/nggirl/app/cli/personalInfo/changePushStatus/2.3.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|[必填]用户授权令牌
|isAllowPush	|[必填]是否允许推送，1允许，0不允许推送

请求示例：
> http://localhost/nggirl/app/cli/personalInfo/changePushStatus/2.3.0?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：

```json
{
    "code": 0,
    "data":null
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确

<h2 id="5">5.获取日签排行榜V2.4.2</h2>

请求方法：nggirl/app/cli/personalInfo/getCheckinRank/2.4.2

请求URL：接口地址/nggirl/app/cli/personalInfo/getCheckinRank/2.4.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|[必填]用户授权令牌

请求示例：
> http://localhost/nggirl/app/cli/personalInfo/getCheckinRank/2.4.2?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：

```json
{
  "code": 0,
  "data": {
    "topTenUsers": [
      {
        "nickName": "看看",
        "checkinCount": 3,
        "myRankHint": "",
        "rankNum": 1,
        "userId": 569,
        "profile": "http://photosd.nggirl.com.cn/work/9cdb09c972de4bcfb2eb888193668c4b.png",
        "isMyRank": 0
      },
      {
        "nickName": "不知道是什么",
        "checkinCount": 3,
        "myRankHint": "",
        "rankNum": 1,
        "userId": 452,
        "profile": "http://photosd.nggirl.com.cn/work/6d087ae802e248518c2aa106708b33db.jpg",
        "isMyRank": 0
      }
    ],
    "bottomUsers": [
      {
        "nickName": "希和",
        "checkinCount": 0,
        "myRankHint": "您已击败0%的用户，加油！",
        "rankNum": 390,
        "userId": 107,
        "profile": "http://photosd.nggirl.com.cn/work/6efb3db7f46c47329d35d9fbec41c50b.jpg",
        "isMyRank": 1
      }
    ]
  }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - topTenUsers	|榜单前10名用户信息
|Data - bottomUsers	|榜单中当前用户前后的用户信息
|Data - rankNum	|当前用户排名
|Data - userId	|用户id
|Data - profile	|用头像
|Data - nickName	|用户昵称
|Data - checkinCount	|用户本月连续签到次数
|Data - isMyRank	|当前用户是否是我
|Data - myRankHint	|用户击败人数提示



<h2 id="6">6.获取补签日历V2.5.2</h2>

请求方法：nggirl/app/cli/personalInfo/getRecheckCalendar/2.5.2

请求URL：接口地址/nggirl/app/cli/personalInfo/getRecheckCalendar/2.5.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|[必填]用户授权令牌

请求示例：
> http://localhost/nggirl/app/cli/personalInfo/getRecheckCalendar/2.5.2?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：

```json
{
    "code": 0,
    "data":{
      "yearMonth":"2016-7",
      "calendar":[
        {
          "monthType":1,
          "day":31,
          "recheckStatus":0
        },
        {
          "monthType":2,
          "day":1,
          "recheckStatus":1
        },
        {
          "monthType":2,
          "day":2,
          "recheckStatus":0
        }
      ]
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - yearMonth |当前年月
|Data - calendar |日历
|Data - calendar - monthType|当前日期的月份类型，1上一月，2本月，3下一月
|Data - calendar - day |本月第几号
|Data - calendar - recheckStatus	|补签状态，0已签到或不可补签，1可以补签


<h2 id="7">7.补签V2.5.2</h2>

请求方法：nggirl/app/cli/personalInfo/recheck/2.5.2

请求URL：接口地址/nggirl/app/cli/personalInfo/recheck/2.5.2

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|[必填]用户授权令牌
|recheckDate|[必填]补签日期，yyyy-M-d格式

请求示例：
> http://localhost/nggirl/app/cli/personalInfo/recheck/2.5.2?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：

```json
{
    "code": 0,
    "data":{
      "userScore":150,
      "userValue":150,
      "tips":[
        {
          "type":2,
          "info":"同一台设备每天只能签到一次！",
          "score":20,
          "couponTitle":"南瓜券",
          "faceValue":30,
          "fitProduct":"仅限上门美妆使用",
          "limitPrice":199,
          "giftTitle":"恭喜您已获得",
          "giftInfo":"额外的美妆大礼包奖励",
          "giftTips":"加微信号领取礼包（微信号：nggirl_yunying）"
        }
      ]
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - userScore |用户当前总积分数
|Data - userValue |用户当前南瓜值
|Data - tips - type |提示类型，0文本提醒，1积分提醒，2南瓜券提醒，3美妆大礼包提醒
|Data - tips - info |[type=0]提醒内容
|Data - tips - score |[type=1]用户获得的积分数
|Data - tips - couponTitle |[type=2]优惠券标题
|Data - tips - faceValue |[type=2]优惠券面值
|Data - tips - fitProduct |[type=2]优惠券适用类型
|Data - tips - limitPrice |[type=2]优惠券最低消费限额
|Data - tips - giftTitle |[type=3]礼包标题
|Data - tips - giftInfo |[type=3]礼包提示信息
|Data - tips - giftTips |[type=3]礼包备注

<h2 id="8">8.往期商品V3.1.0</h2>

>出参删除tb_item_id、tb_detail_url，添加productDetailType

请求方法：nggirl/app/cli/personalInfo/getCheckinPreviousSeedProducts/3.1.0

请求url：接口地址/nggirl/app/cli/personalInfo/getCheckinPreviousSeedProducts/3.1.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken	|[必填]用户授权令牌|
|pageNum|第几页，默认从0开始（非必填）|
|pageSize|每页条数，默认为20（非必填）|


请求示例：
> http://localhost/nggirl/app/cli/personalInfo/getCheckinPreviousSeedProducts/3.1.0

返回结果示例：

```json
{
    "code":0,
    "data":[
        {
            "seedProductId":1,
            "name":"商品名称",
            "picture":"http://photosd.nggirl.com.cn/work/c9138c508f5d49f0afddf324c9097f3a.png",
            "price":1209,
            "seedNum":32,
            "isSeed":1,
            "productDetailType":1,
            "isAllowBuy":1,
        },
        {
            "seedProductId":1,
            "name":"商品名称",
            "picture":"http://photosd.nggirl.com.cn/work/c9138c508f5d49f0afddf324c9097f3a.png",
            "price":1209,
            "seedNum":32,
            "isSeed":1,
            "productDetailType":1,
            "isAllowBuy":1,
        }
    ]
}
```

返回结果说明：

|字段名称|字段含义|
|----|----|
|Code|错误标识码，0标识正确|
|Data - seedProductId|商品编号|
|Data - name|商品名称|
|Data - picture|商品图|
|Data - price|商品价格|
|Data - seedNum|种草人数|
|Data - isSeed|是否已种草：0未种草，1已种草|
|Data - productDetailType|跳转商品详情类型，1老版本商品种草页面，2新版本商品详情页面|
|Data - isAllowBuy|0不可购买，1可购买|
