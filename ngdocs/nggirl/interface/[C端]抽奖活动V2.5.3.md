# 抽奖活动V2.5.3

---

* [1.获取抽奖活动基本信息V2.5.3](#1)
* [2.获取获奖用户名单V2.5.3](#2)
* [3.获取抽奖活动奖品列表V2.5.3](#3)
* [4.用户抽奖V2.5.3](#4)
* [5.为奖品填写收货地址V2.5.3](#5)
* [6.我的奖品列表V2.5.3](#6)
* [7.奖品详情V2.5.3](#7)

<h2 id="1">1.获取抽奖活动基本信息V2.5.3</h2>

请求方法：nggirl/app/cli/lottery/getLotteryInfo/2.5.3

请求URL：接口地址/nggirl/app/cli/lottery/getLotteryInfo/2.5.3

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|-----|-----|
|accessToken|【非必填】用户登录时必填|
|activityId|【必填】抽奖活动编号|

请求示例：localhost/nggirl/app/cli/lottery/getLotteryInfo/2.5.3?activityId=1

返回结果示例：

```json
{
    "code":0,
    "data":{
        "activityId":1,
        "userScore":20000,
        "headImg":"http://photosd.nggirl.com.cn/work/18b0677ced9646149e77a61199c7865f.jpg",
        "title":"国庆抽奖活动",
        "shareContent":"分享内容分享内容分享内容分享内容",
        "shareImg":"http://photosd.nggirl.com.cn/work/18b0677ced9646149e77a61199c7865f.jpg",
        "rotaryTableImg":"http://photosd.nggirl.com.cn/work/18b0677ced9646149e77a61199c7865f.jpg",
        "pointerImg":"http://photosd.nggirl.com.cn/work/18b0677ced9646149e77a61199c7865f.jpg",
        "startTime":1434354541000,
        "endTime":1434354541000,
        "currentTime":1434354541000,
        "dailyFreeTimes":2,
        "remainFreeTimes":1,
        "costScore":200,
        "rules":"抽奖规则抽奖规则抽奖规则抽奖规则抽奖规则",
        "appDownloadUrl":""
    }
}
```

返回字段说明：

|字段名称|字段含义|
|----|----|
|activityId|抽奖活动编号|
|userScore|用户当前积分|
|headImg|活动头图|
|title|标题|
|shareContent|分享内容|
|shareImg|分享小图|
|rotaryTableImg|转盘图片|
|pointerImg|指针图片|
|startTime|抽奖活动开始时间，13位毫秒数|
|endTime|抽奖活动结束时间，13位毫秒数|
|currentTime|系统当前时间，13位毫秒数|
|dailyFreeTimes|每人每天免费抽奖次数|
|remainFreeTimes|当前用户剩余免费抽奖次数|
|costScore|抽奖一次花费积分|
|rules|抽奖规则|
|appDownloadUrl|app下载地址|


<h2 id="2">2.获取获奖用户名单V2.5.3</h2>

请求方法：nggirl/app/cli/lottery/getAwardUserList/2.5.3

请求URL：接口地址/nggirl/app/cli/lottery/getAwardUserList/2.5.3

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|----|----|
|activityId|【必填】抽奖活动编号|

请求示例：localhost/nggirl/app/cli/lottery/getAwardUserList/2.5.3?activityId=1

返回结果示例：

```json
{
    "code":0,
    "data":[
        {
            "userId":1,
            "profile":"http://testphotosd.nggirl.com.cn/work/57b0a6defc0d41d681fc700b0c7400ef.png",
            "nickName":"agao",
            "awardName":"国庆节大奖"
        },
        {
            "userId":1,
            "profile":"http://testphotosd.nggirl.com.cn/work/57b0a6defc0d41d681fc700b0c7400ef.png",
            "nickName":"agao",
            "awardName":"国庆节大奖"
        }
    ]
}
```

返回结果说明：

|字段名称|字段含义|
|----|-----|
|userId|用户比俺还|
|profile|用户头像|
|nickName|用户昵称|
|awardName|抽中的奖品名称|



<h2 id="3">3.获取抽奖活动奖品列表V2.5.3</h2>

请求方法：nggirl/app/cli/lottery/getAwardList/2.5.3

请求URL：接口地址/nggirl/app/cli/lottery/getAwardList/2.5.3

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|----|----|
|activityId|【必填】抽奖活动编号|

请求示例：localhost/nggirl/app/cli/lottery/getAwardList/2.5.3?activityId=1

返回结果示例：

```json
{
    "code":0,
    "data":[
        {
            "awardId":1,
            "awardName":"南瓜玩偶",
            "awardImg":"http://testphotosd.nggirl.com.cn/work/57b0a6defc0d41d681fc700b0c7400ef.png",
            "awardNum":7
        },
        {
            "awardId":1,
            "awardName":"南瓜玩偶",
            "awardImg":"http://testphotosd.nggirl.com.cn/work/57b0a6defc0d41d681fc700b0c7400ef.png",
            "awardNum":7
        }
    ]
}
```

返回字段说明：

|字段名称|字段含义|
|----|----|
|awardId|抽奖活动（联合）奖品编号|
|awardName|奖品名称|
|awardImg|奖品配图|
|awardNum|奖品数量|

<h2 id="4">4.用户抽奖V2.5.3</h2>

请求方法：nggirl/app/cli/lottery/userDraw/2.5.3

请求URL：接口地址/nggirl/app/cli/lottery/userDraw/2.5.3

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|[必填]用户授权令牌
|activityId	|[必填]抽奖活动id

请求示例：
> http://localhost/nggirl/app/cli/lottery/userDraw/2.5.3?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：

```json
{
    "code": 0,
    "data":{
      "userId":101,
      "userScore":150,
      "remainFreeTimes":1,
      "hintType":1,
      "hint":"抽奖时间已过",
      "awardSeq":2,
      "awardRecordId":1,
      "awardId":1,
      "awardType":1,
      "awardName":"回家吃饭优惠券",
      "couponName":"南瓜券",
      "fitProduct":"仅限上门美妆使用",
      "limitPrice":199,
      "price":30
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|Data - userId | 用户id |
|Data - userScore	|用户当前积分|
|Data - hintType|提示类型，0未中奖，1商品，2南瓜券，3第三方优惠券，4积分不足，5其他|
|Data - hint|[hintType=5]提示信息|
|Data - remainFreeTimes	|[hintType=0,1,2,3]用户免费抽奖剩余次数|
|Data - awardSeq|[hintType=0,1,2,3]用户抽到的奖品在转盘上时第几个（从1开始）|
|Data - awardRecordId	|[hintType=0,1,2,3]用户获奖记录id|
|Data - awardId	|[hintType=0,1,2,3]用户获奖的奖品id|
|Data - awardType	|[hintType=0,1,2,3]用户获奖的奖品类型，0谢谢参与，1商品，2南瓜券，3优惠券|
|Data - awardName	|[hintType=1,2,3]奖品名称|
|Data - couponName	|[hintType=2]南瓜券名称|
|Data - fitProduct	|[hintType=2]南瓜券适用类型|
|Data - limitPrice	|[hintType=2]南瓜券最低消费价格|
|Data - price	|[hintType=2]南瓜券金额|

<h2 id="5">5.为奖品填写收货地址V2.5.3</h2>

请求方法：nggirl/app/cli/lottery/fillLotteryAwardAddress/2.5.3

请求URL：接口地址/nggirl/app/cli/lottery/fillLotteryAwardAddress/2.5.3

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|[必填]用户授权令牌
|awardRecordId	|[必填]用户获奖记录id
|realName	|[必填]收货人
|phoneNum	|[必填]手机号
|address	|[必填]收货地址

请求示例：
> http://localhost/nggirl/app/cli/lottery/fillLotteryAwardAddress/2.5.3?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

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
|Code	|错误码，0表示正确|

<h2 id="6">6.我的奖品列表V2.5.3</h2>

请求方法：nggirl/app/cli/lottery/myLotteryAwards/2.5.3

请求URL：接口地址/nggirl/app/cli/lottery/myLotteryAwards/2.5.3

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|[必填]用户授权令牌
|page	|[可选]页数,非必需参数，默认第一页
|num	|[可选]每页信息数目,非必须参数，默认20

请求示例：
> http://localhost/nggirl/app/cli/lottery/myLotteryAwards/2.5.3?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：

```json
{
    "code": 0,
    "data":{
        "activityId":1,
        "awards":[
            {
                "awardRecordId":1,
                "awardId":1,
                "awardType":1,
                "awardName":"南瓜玩偶",
                "awardImg":"http://testphotosd.nggirl.com.cn/work/57b0a6defc0d41d681fc700b0c7400ef.png"
            },
            {
                "awardRecordId":1,
                "awardId":1,
                "awardType":1,
                "awardName":"南瓜玩偶",
                "awardImg":"http://testphotosd.nggirl.com.cn/work/57b0a6defc0d41d681fc700b0c7400ef.png"
            }
        ]
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|Data - activityId|抽奖活动编号，如果返回的结果为null，则置为0，并隐藏“去抽奖”这个按钮|
|Data - awards - awardRecordId|用户获奖记录id|
|Data - awards - awardId|奖品id|
|Data - awards - awardType|奖品类型，0谢谢参与(不会出现在该列表中)，1商品，2南瓜券，3优惠券|
|Data - awards - awardName|奖品名称|
|Data - awards - awardImg|奖品配图|


<h2 id="7">7.奖品详情V2.5.3</h2>

请求方法：nggirl/app/cli/lottery/myLotteryAwardDetail/2.5.3

请求URL：接口地址/nggirl/app/cli/lottery/myLotteryAwardDetail/2.5.3

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|[必填]用户授权令牌
|awardRecordId	|[必填]用户获奖记录id

请求示例：
> http://localhost/nggirl/app/cli/lottery/myLotteryAwardDetail/2.5.3?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：

```json
{
    "code": 0,
    "data":{
      "awardRecordId":1,
      "status":0,
      "awardId":1,
      "awardType":1,
      "awardName":"南瓜玩偶",
      "inviteCode":"ABCD123",
      "awardHeadImg":"http://testphotosd.nggirl.com.cn/work/57b0a6defc0d41d681fc700b0c7400ef.png",
      "activityTime":"2016-08-02 至 2016-09-10",
      "isInActivity":1,
      "details":[
        {
          "type":2,
          "content":"商品详情介绍.....",
          "descrip":"",
          "extend":""
        },{
          "type":3,
          "content":"http://testphotosd.nggirl.com.cn/work/57b0a6defc0d41d681fc700b0c7400ef.png",
          "descrip":"",
          "extend":"200_100"
        }
      ]
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|Data - awardRecordId|用户获奖记录id|
|Data - status|订单状态，0未填写完整收货人信息（此时可以完善商品收货人信息）；1已填写完整收货人信息，但是未发货；2已发货|
|Data - awardId|奖品id|
|Data - awardType|奖品类型，0谢谢参与(不会出现在该接口中)，1商品，2南瓜券，3优惠券|
|Data - awardName|奖品名称|
|Data - inviteCode|awardType=2,3时，商品兑换码|
|Data - awardHeadImg|奖品头图|
|Data - activityTime|抽奖活动时间|
|Data - isInActivity|当前是否在活动期间，1在活动期间，0不在活动期间|
|Data - details|商品详情|
|Data - details -type|元件类型，2段落，3图片|
|Data - details -content|type=2段落文字，type=3图片url|
|Data - details -descrip|空|
|Data - details -extend|type=3图片-宽_高|
