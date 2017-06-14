<h1>我的接口v2.5.4</h1>

目录

* [1.个人资料显示V2.5.4](#1)
* [2.背景封面图修改](#2)
* [3.我的预约](#3)
* [4.我的预约(返回更多的信息)](#4)
* [5.关注的化妆师V1.5.0](#5)
* [6.我的收藏](#6)
* [7.我的邀请码](#7)
* [8.领取优惠券V1.4.2](#8)
* [9.设置](#9)
 * [9.1.修改密码V2.4.0](#9.1)
 * [9.2.预约与退约规则](#9.2)
 * [9.3.评价](#9.3)
 * [9.4.服务条款](#9.4)
* [10.注销](#10)
* [11.获取非绑定的优惠券V1.5.0](#11)
* [12.获取未读消息条数V2.0.0](#12)
* [14.我的帖子消息V2.2.0](#14)
* [15.删除帖子消息V2.0.0](#15)
* [16.分享成功V2.5.3](#16)
* [17.删除收藏的帖子V2.2.0](#17)
* [18.删除收藏的妆容V2.2.0](#18)
* [19.绑定其他账号V2.4.0](#19)
* [20.获取绑定关系V2.4.0](#20)
* [21.获取用户南瓜值页面数据V2.5.2](#21)
* [22.获取用户南瓜值增减记录V2.5.2](#22)


<h2 id="1">1.个人资料显示V2.5.4</h2>

> 出参添加userRole

请求方法：nggirl/app/cli/personalInfo/getUserInfo/2.5.4

请求URL：接口地址/nggirl/app/cli/personalInfo/getUserInfo/2.5.4

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|用户授权令牌

请求示例：
> http://localhost/nggirl/app/cli/personalInfo/getUserInfo/2.5.4?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "userId": 10000,
        "profile": "http://www.baidu.com/1.jpg",
        "nickName": "kevin1202",
        "userName": "杨凯",
        "sex":0,
        "birthday": "1991-12-02",
        "cover": "http://www.baidu.com/2.jpg",
        "score":100,
        "phoneNum":"134261294566",
        "addressNum":3,
        "userValue":150,
        "userLevel":2,
        "userRole":"南瓜小编"
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - userId	|用户id
|Data - profile	|用户头像
|Data - nickName	|用户昵称
|Data - userName	|用户的真实姓名
|Data - sex	|性别(0-男；1-女)
|Data - birthday	|用户生日
|Data - cover	|用户的背景封面图
|Data - score	|用户积分
|Data - phoneNum	|用户手机号
|Data - addressNum|地址数
|Data - userValue|用户南瓜值
|Data - userLevel|用户当前等级
|Data - userRole|用户角色

<h2 id="2">2.背景封面图修改</h2>

请求方法：nggirl/app/cli/personalInfo/updateBackgroud

请求URL：接口地址/nggirl/app/cli/personalInfo/updateBackgroud

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|background	|用户封面图片文件，为图片上传后返回的路径。

请求示例：
> http://localhost/nggirl/app/cli/personalInfo/updateBackgroud?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "url": "http://www.baidu.com/1.jpg",
        "md5": "pg12MQ68QFmdiqkPDE5Z8NKjUSksKg"
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - url	|上传文件网络地址
|Data - md5	|上传文件md5

<h2 id="3">3.我的预约</h2>

请求方法：nggirl/app/cli/personalInfo/listReservation

请求URL：接口地址/nggirl/app/cli/personalInfo/listReservation

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|用户授权令牌
|page	|页数,非必需参数，默认第一页
|num	|每页信息数目,非必须参数，默认20

请求示例：

> http://localhost/nggirl/app/cli/personalInfo/listReservation?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&page=0&num=20

返回结果示例：
```json
{
    "code": 0,
    "data": [{
        "reservationId": 1234567,
        "profile": "http://www.baidu.com/1.jpg",
        "name":"王子涵",
        "isVDresser":1,
        "workType": "职业装",
        "cost": 100,
        "status": 1,
        "reservationTime": "2015年5月16日 8:00-10：00",
        "lastUpdateTime":1435196075742
         },{
        "reservationId": 1234567,
        "profile": "http://www.baidu.com/1.jpg",
        "name":"王子涵",
        "isVDresser":1,
        "workType": "职业装",
        "cost": 100,
        "status": 0,
        "reservationTime": "2015年5月16日 8:00-10：00",
        "lastUpdateTime":1435196075742,
        "systemTime":1435196075742
    }]
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - reservationId	|预约编号
|Data - profile	|化妆师头像
|Data - name	|化妆师名称
|Data - workType	|妆束类型
|Data - cost	|化妆费用
|Data - reservationTime	|预约日期
|Data - status	|预约单状态，0预约初始状态,1已取消，2已结算，3已接收，4已拒绝，5已完成
|Data - isVDresser	|是否为加V化妆师，0为否，1为是
|Data - lastUpdateTime	|最后修改时间，如果status为已接收时，此值为接单时间；如果status为已支付时，此值为支付时间。
|Data - systemTime	|系统当前时间

<h2 id="4">4.我的预约(返回更多的信息)</h2>

请求方法：nggirl/app/cli/personalInfo/listReservationIos

请求URL：接口地址/nggirl/app/cli/personalInfo/listReservationIos

支持格式：JSON

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken|	用户授权令牌
|page|	页数，非必需参数，默认第一页
|num|	每页信息数目，非必须参数，默认20

请求示例：

http://localhost/nggirl/app/cli/personalInfo/listReservationIos?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&page=0&num=20

返回结果示例：

```json
{
    "code": 0,
    "data": [{
        "reservationId": 1234567,
        "dresserId":27,
        "authentication":1,
        "starLevel":4,
        "praised":0,
        "profile": "http://www.baidu.com/1.jpg",
        "name":"王子涵",
        "isVDresser":1,
        "workType": "职业装",
        "cost": 100,
        "status": 1,
        "reservationAddress":"北京市朝阳区大屯路",
        "reservationTime": "2015年5月16日 8:00-10：00",
        "lastUpdateTime":1435196075742
             },{
        "reservationId": 1234567,
        "dresserId":27,
        "authentication":1,
        "starLevel":4,
        "praised":0,
        "profile": "http://www.baidu.com/1.jpg",
        "name":"王子涵",
        "isVDresser":1,
        "workType": "职业装",
        "cost": 100,
        "status": 1,
        "reservationAddress":"北京市朝阳区大屯路",
        "reservationTime": "2015年5月16日 8:00-10：00",
        "lastUpdateTime":1435196075742
    }]
}
```
返回字段说明：

|字段名|字段含义
|---|---
|Code|	错误码，0表示正确
|Data - reservationId|预约编号
|Data - dresserId	|化妆师编号
|Data - authentication|	化妆师是否已经认证
|Data - starLevel	|化妆师星级
|Data - praised	|用户是否已经评价过预约
|Data - profile	|化妆师头像
|Data - name	|化妆师名称
|Data - workType|	妆束类型
|Data - cost|	化妆费用
|Data - reservationAddress|	预约地点
|Data - reservationTime|	预约日期
|Data - status|	预约单状态，0预约初始状态,1已取消，2已结算，3已接收，4已拒绝，5已完成
|Data - isVDresser	|是否为加V化妆师，0为否，1为是
|Data - lastUpdateTime|	最后修改时间，如果status为已接收时，此值为接单时间；如果status为已支付时，此值为支付时间。
|Data - systemTime	|系统当前时间


<h2 id="5">5.关注的化妆师V1.5.0</h2>

>入参无变化，出参删除workType，添加specials

请求方法：nggirl/app/cli/personalInfo/listInterestDresser/1.5.0

请求URL：接口地址/nggirl/app/cli/personalInfo/listInterestDresser/1.5.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|用户授权令牌
|page|页数(非必须，默认第1页)
|num|每页条数（非必须，默认20）

请求示例：

> http://localhost/nggirl/app/cli/personalInfo/listInterestDresser/1.5.0?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&page=0&num=20

返回结果示例：

```json
{
    "code": 0,
    "data": [{
        "dresserId": 100,
        "name": "王子涵",
        "orderNum":58,
        "specials":"专注古装,手推波纹,明星公告",
        "profile": "http://www.baidu.com/1.jpg",
        "authentication": 1,
        "starLevel": 5,
        "isVDresser":1
     },{
        "dresserId": 100,
        "name": "王子涵",
        "orderNum":58,
        "specials":"专注古装,手推波纹,明星公告",
        "profile": "http://www.baidu.com/1.jpg",
        "authentication": 1,
        "starLevel": 5,
        "isVDresser":0
    }]
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - dresserId	|化妆师id
|Data - name	|化妆师姓名
|Data - orderNum	|已完成订单数量
|Data - specials	|化妆师特长，以英文逗号分隔
|Data - profile	|化妆师头像
|Data - authentication	|是否认证，0未认证，1已认证
|Data - starLevel	|评价的星级
|Data - isVDresser	|是否为加V化妆师，0为否，1为是

<h2 id="6">6.我的收藏</h2>

请求方法：nggirl/app/cli/personalInfo/listCollection/1.3

请求URL：接口地址/nggirl/app/cli/personalInfo/listCollection/1.3

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|page	|页数，非必需参数，默认第一页
|num|每页信息数目，非必须参数，默认20

请求示例：

> http://localhost/nggirl/app/cli/personalInfo/listCollection/1.3?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&page=0&num=20

返回结果示例：

```json
{
    "code": 0,
    "data": [{
        "workId": 100,
        "cover": "http://www.baidu.com/1.jpg",
        "praiseNum":58,
        "workType": "职业装",
        "cost": 100,
        "praiseStatus":1,
        "dresserId":123,
        "hasDiscount": 0,
        "discount":{
            "id":1,
            "workId":123,
            "name":"首单五折",
            "desc":"新用户首次下单五折优惠，还可叠加使用优惠券",
            "cost":50,
            "icon":"http://testphotosd.nggirl.com.cn/work/aee4e7c292094a24a72ac8da401bbd7d.png"
          }
     },{
        "workId": 100,
        "cover": "http://www.baidu.com/1.jpg",
        "praiseNum":58,
        "workType": "淑女装",
        "cost": 100,
        "praiseStatus":0,
        "dresserId":123,
        "hasDiscount": 0,
        "discount":{
            "id":1,
            "workId":123,
            "name":"首单五折",
            "desc":"新用户首次下单五折优惠，还可叠加使用优惠券",
            "cost":50,
            "icon":"http://testphotosd.nggirl.com.cn/work/aee4e7c292094a24a72ac8da401bbd7d.png"
        }
    }]
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - workId	|作品编号
|Data - cover	|作品封面
|Data - praiseNum|点赞数量
|Data - workType|妆束类型
|Data - cost|费用
|Data - praiseStatus|是否已经点赞，0为未点赞，1为已点赞
|Data - dresserId|作品所属化妆师编号
|Data - hasDiscount|此作品是否参与了折扣活动，0没有，1有
|Data - discount - id|活动编号
|Data - discount - workId|参与活动的作品编号
|Data - discount - name|活动名称，显示在作品的活动栏（红底部分）
|Data - discount - desc|活动描述，显示在作品的活动栏
|Data - discount - cost|参与活动后的价格
|Data - discount - icon|活动的图标，用于放在作品的图片右上角

<h2 id="7">7.我的邀请码</h2>

请求方法：nggirl/app/cli/personalInfo/getInvitationCode

请求URL：接口地址/nggirl/app/cli/personalInfo/getInvitationCode

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|用户授权令牌

请求示例：

> http://localhost/nggirl/app/cli/personalInfo/getInvitationCode?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：

```json
{
     "code": 0,
     "data":{
        "invitationCode":"000H0R00",
        "leftTimes": 3
         }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - invitationCode	|邀请码
|Data - leftTimes	|剩余可用次数


<h2 id="8">8.领取优惠券V1.4.2</h2>

>相比原接口，出入参皆无变化

请求方法：nggirl/app/cli/personalInfo/receiveCoupon/1.4.2

请求URL：接口地址/nggirl/app/cli/personalInfo/receiveCoupon/1.4.2

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|[必填]用户授权令牌
|couponNum   |[必填]优惠券编码

请求示例：
> http://localhost/nggirl/app/cli/personalInfo/receiveCoupon/1.4.2?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&couponNum=Q2714141456

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


<h2 id="9">9.设置</h2>

<h2 id="9.1">9.1. 修改密码V2.4.0</h2>
> 接口入参出参没有变化，仅后台逻辑改变

请求方法：nggirl/app/cli/personalInfo/resetPassword/2.4.0

请求URL：接口地址/nggirl/app/cli/personalInfo/resetPassword/2.4.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|用户授权令牌
|oldPassword|旧密码MD5
|newPassword|新密码MD5

请求示例：
> http://localhost/nggirl/app/cli/personalInfo/resetPassword/2.4.0?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&oldPassword=1231213&newPassword=kevin1202

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


<h2 id="9.2">9.2. 预约与退约规则</h2>

请求方法：nggirl/app/cli/personalInfo/getRule

请求URL：接口地址/nggirl/app/cli/personalInfo/getRule

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌

请求示例：

> http://localhost/nggirl/app/clientPersonal/getRule?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "url": "http://www.baidu.com"
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - url	|上传文件网络地址


<h2 id="9.3">9.3. 反馈建议</h2>

请求方法：nggirl/app/cli/personalInfo/submitFeedback

请求URL：接口地址/nggirl/app/cli/personalInfo/submitFeedback

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|用户授权令牌
|opinionType	|反馈意见类型
|feedbackContent	|反馈内容

请求示例：
> http://localhost/nggirl/app/cli/personalInfo/submitFeedback?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&opinionType=0&feedbackContent=这个版本很好用

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


<h2 id="9.4">9.4. 服务条款</h2>

请求方法：nggirl/app/cli/personalInfo/serviceInfo

请求URL：接口地址/nggirl/app/cli/personalInfo/serviceInfo

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken|	用户授权令牌


请求示例：
http://localhost/nggirl/app/cli/personalInfo/serviceInfo?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：
```json
{
    "code": 0,
    "data": {
         "url": "http://www.baidu.com"
        }

}
```
返回字段说明：

|字段名|字段含义
|---|---
|Code|	错误码，0表示正确
|Data - url|服务条款url


<h2 id="10">10. 注销</h2>

请求方法：nggirl/app/cli/personalInfo/logout

请求URL：接口地址/nggirl/app/cli/personalInfo/logout

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|用户授权令牌

请求示例：

> http://localhost/nggirl/app/cli/personalInfo/logout?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

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

<h2 id="11">11.获取非绑定的优惠券V1.5.0</h2>

>与1.4.2接口相比，入参无变化，出参多了个coupons字段

>如果用户已经注册过，该方法会获取直接用手机号注册的用户和在个人信息中绑定过手机号的用户。

请求方法：nggirl/app/cli/personalInfo/createUnbindCoupon/1.5.0

请求URL：接口地址/nggirl/app/cli/personalInfo/createUnbindCoupon/1.5.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---
|phoneNum	|[必填]领券手机号
|code	|[必填]优惠码

请求示例：
> http://localhost/nggirl/app/cli/personalInfo/createUnbindCoupon/1.5.0?phoneNum=18518676735&code=abcdefgh&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：

```json
{
    "code": 0,
    "data": {
    	"error": "领取优惠券成功!",
      "coupons":[
        {
            "couponId": 100,
            "title": "南瓜券",
            "type":"全品类优惠券",
            "couponNum": "Q2714141456",
            "money":0,
            "isDiscount":1,
            "discount":7.5
        },{
            "couponId": 101,
            "title": "南瓜券",
            "type":"仅限上门美妆使用",
            "couponNum": "Q2714141411",
            "money": 30,
            "isDiscount":0,
            "discount":null
        }
      ]
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - error	| 返回的提示信息
|Data - coupons	| 成功领取的优惠券信息
|Data - coupons - couponId	|优惠券id
|Data - coupons - title	|优惠券标题
|Data - coupons - type	|优惠券类型
|Data - coupons - couponNum	|优惠券编号
|Data - coupons - money	|优惠券面值
|Data - coupons - isDiscount	|是否是折扣券，1是折扣券，0不是折扣券
|Data - coupons - discount	|折扣，0~10中间的数字

> code=0时，error="领取优惠券成功!";code=1时，error可能为："参数不正确!"、"您已经领过该优惠券了!"、"优惠券已经领光了!"、"找不到这个优惠券!"

>该接口使用于优惠券的h5页面领取页面（http://testcli.nggirl.com.cn/nggirl/h5/mobile/tuiguang/vouchers.html?amount=88&code=SC5HGBYOB），也可用于其他领取页面

>该页面有两个参数code是邀请码，amount是优惠券的金额(用户显示页面中优惠券的金额图片，需要配合images文件夹中上传对应的图片)

<h2 id="12">12.获取未读消息条数V2.0.0</h2>

请求方法：nggirl/app/cli/personalInfo/getMsgCount/2.0.0

请求URL：接口地址/nggirl/app/cli/personalInfo/getMsgCount/2.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|[必填]用户授权令牌

请求示例：

> http://localhost/nggirl/app/cli/personalInfo/getMsgCount/2.0.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0

返回结果示例：

```json
{
    "code": 0,
    "data":  {
      "systemMsgCount": 5,
      "postMsgCount":10
    }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data – systemMsgCount	|未读系统消息条数
|Data – postMsgCount	|未读帖子消息条数


<h2 id="14">14.我的帖子消息V2.2.0</h2>

> 与2.1.0接口相比，返回值增加了禁言状态和禁言截止时间

请求方法：nggirl/app/cli/personalInfo/getPostMessages/2.2.0

请求URL：接口地址/nggirl/app/cli/personalInfo/getPostMessages/2.2.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|[必填]用户授权令牌
|page	|[可选]页数,非必需参数，默认第一页
|num	|[可选]每页信息数目,非必须参数，默认20
|queryTime|[可选]查询时间，查询第一页时，不需要传入该参数；查询第二页及其他页时，则传入该参数，必填

请求示例：
> http://localhost/nggirl/app/cli/personalInfo/getPostMessages/2.2.0?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：

```json
{
    "code": 0,
    "data": {
      "isNoTalk":0,
      "noTalkTime":"2016年07月10日 00:00:00",
      "queryTime" : 1347634134983,
      "messages":[
        {
          "messageId":1,
          "postType":1,
          "postId":123,
          "postTitle":"教你如何3分钟搞定范冰冰的大波浪",
          "receiveTime":123456789012,
          "systemTime":1234567800001,
          "userId":123345,
          "nickName":"小清新",
          "profile":"http://testphotosd.nggirl.com.cn/work/68856d91c7674daca32e59c79bdd8a6c.png",
          "notifyType":1,
          "content":"你真的太可爱了！！！",
          "toNickName":"",
          "toUserId":0,
          "replyToContent":"教你如何3分钟搞定范冰冰的大波浪",
          "replyToNickName":"",
          "replyToUserId":0,
          "commentId":1,
          "replyId":1
        }
      ]
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - isNoTalk    |是否禁言 0未禁言，1已禁言
|Data - noTalkTime	|禁言截止时间 格式："yyyy年MM月dd日 HH:mm:ss"
|Data - queryTime	|查询的开始时间（第一次查询后，后台返回该时间，以后加载下一页时，需要将该时间回传给后台）
|Data - messageId	|消息id
|Data - postType	|贴子类型，1为文章，2为视频
|Data - postId	|贴子id(文章id或者视频id)
|Data - postTitle	|帖子标题
|Data - receiveTime	|消息接收时间
|Data - systemTime	|当前系统时间
|Data - userId	|发送消息用户id
|Data - nickName	|发送消息用户昵称
|Data - profile	|发送消息的用户头像
|Data - notifyType	|关联类型，1评论帖子（我是发帖人），2回复评论（我是楼主），3回复指定回复（我不是楼主，但是我是被回复者），4回复指定回复（我是楼主，我楼层中的人被回复了）
|Data - content	|发送的消息内容（白色背景文字内容）
|Data - replyToContent|被回复对象和内容（绿色背景文字内容）
|Data - commentId|评论id，[回复时调用回复接口，传入该值](https://github.com/nggirl/ngdocs/blob/master/nggirl/interface/%5BC%E7%AB%AF%5D-%E5%8D%97%E7%93%9C%E5%A7%91%E5%A8%98%E6%8E%A5%E5%8F%A3%E6%96%87%E6%A1%A3-%E5%B8%96%E5%AD%90%E8%AF%84%E8%AE%BAV2.0.0.md#3)
|Data - replyId|回复id，[回复时调用回复接口，传入该值](https://github.com/nggirl/ngdocs/blob/master/nggirl/interface/%5BC%E7%AB%AF%5D-%E5%8D%97%E7%93%9C%E5%A7%91%E5%A8%98%E6%8E%A5%E5%8F%A3%E6%96%87%E6%A1%A3-%E5%B8%96%E5%AD%90%E8%AF%84%E8%AE%BAV2.0.0.md#3)，且notifyType=1时该字段为空


<h2 id="15">15.删除帖子消息V2.0.0</h2>

请求方法：nggirl/app/cli/personalInfo/deletePostMessage/2.0.0

请求URL：接口地址/nggirl/app/cli/personalInfo/deletePostMessage/2.0.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|[必填]用户授权令牌
|messageId	|[必填]帖子消息id

请求示例：

> http://localhost/nggirl/app/cli/personalInfo/deletePostMessage/2.0.0

返回结果示例：

```json
{
    "code": 0,
    "data":  null
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确

<h2 id="16">16.分享成功V2.5.3</h2>

>出参增加addScore字段

请求方法：nggirl/app/cli/personalInfo/shareSuccess/2.5.3

请求URL：接口地址/nggirl/app/cli/personalInfo/shareSuccess/2.5.3

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义|
|---|---|
|accessToken	|[必填]用户授权令牌|
|shareType|[必填]分享类型，1微信分享到朋友圈，2微信发送给朋友，3分享到新浪微博|
|contentType	|[必填]分享内容类型|
|contentInfo	|[必填]分享内容信息，根据分享内容类型填写|

>contentType与contentInfo之间的对应关系如下

|contentType	|contentInfo|
|---|---|
|h5非固定模块的H5页面|h5页面的Url|
|wrok上门美妆作品|作品id|
|salon美妆沙龙|沙龙id|
|header轮播头图|头图id|
|dresser化妆师个人主页|化妆师id|
|coupon邀请码|邀请码编号|
|postarticle文章帖子|文章帖子id|
|postvideo视频帖子|视频帖子id|
|checkin日签|日签id|
|specials专栏|专栏id|
|seedproduct商品|商品id|
|aboutme化妆师主页关于我|化妆师id|
|userhome用户个人主页|用户id|
|scoreshopgoods积分商城商品详情页|商品id|
|cosmeticTrial妆品试用详情页|试用活动编号cosmeticId|


请求示例：

> http://localhost/nggirl/app/cli/personalInfo/shareSuccess/2.5.3

返回结果示例：

```json
{
    "code": 0,
    "data":{
      "addScore":1
    }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确|
|Data - addScore|用户本次操作增加的积分数|

<h2 id="17">17.删除收藏的帖子V2.2.0</h2>

请求方法：nggirl/app/cli/personalInfo/deleteCollectedPosts/2.2.0

请求URL：接口地址/nggirl/app/cli/personalInfo/deleteCollectedPosts/2.2.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|[必填]用户授权令牌
|posts|[必填]帖子信息，json格式

posts字段示例：

```json
[
  {"postType":1,"postId":1},
  {"postType":1,"postId":2},
  {"postType":1,"postId":3},
  {"postType":2,"postId":1},
  {"postType":2,"postId":2},
  {"postType":2,"postId":3}
]
```

请求示例：

> http://localhost/nggirl/app/cli/personalInfo/deleteCollectedPosts/2.2.0

返回结果示例：

```json
{
    "code": 0,
    "data":  null
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确

<h2 id="18">18.删除收藏的妆容V2.2.0</h2>

请求方法：nggirl/app/cli/personalInfo/deleteCollectedWorks/2.2.0

请求URL：接口地址/nggirl/app/cli/personalInfo/deleteCollectedWorks/2.2.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|[必填]用户授权令牌
|workIds|[必填]作品id字符串，以逗号分隔


请求示例：

> http://localhost/nggirl/app/cli/personalInfo/deleteCollectedWorks/2.2.0

返回结果示例：

```json
{
    "code": 0,
    "data":  null
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确


<h2 id="19">19.绑定其他账号V2.4.0</h2>

请求方法：nggirl/app/cli/personalInfo/bindAccount/2.4.0

请求URL：接口地址/nggirl/app/cli/personalInfo/bindAccount/2.4.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|[必填]用户授权令牌
|bindUserType|[必填]要绑定的账号类型，1手机号，2微信，3微博
|bindUserRecId|[必填]要绑定账号的识别码，手机号或者微信的unionid或者微博的uid
|validateCode|手机绑定时的验证码，仅绑定类型为手机时需要
|bindUserPassword|绑定手机号时，设定的手机号账号密码


请求示例：

> http://localhost/nggirl/app/cli/personalInfo/bindAccount/2.4.0

返回结果示例：

```json
{
    "code": 0,
    "data":  {
        "isPhoneBinded":1,
        "isWeixinBinded":0,
        "isWeiboBinded":1
    }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - isPhoneBinded|是否绑定了手机
|Data - isWeixinBinded|是否绑定了微信
|Data - isWeiboBinded|是否绑定了微博

<h2 id="20">20.获取绑定关系V2.4.0</h2>

请求方法：nggirl/app/cli/personalInfo/getBindRelationship/2.4.0

请求URL：接口地址/nggirl/app/cli/personalInfo/getBindRelationship/2.4.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|[必填]用户授权令牌


请求示例：

> http://localhost/nggirl/app/cli/personalInfo/getBindRelationship/2.4.0

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "isPhoneBinded":1,
        "isWeixinBinded":0,
        "isWeiboBinded":1
    }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - isPhoneBinded|是否绑定了手机
|Data - isWeixinBinded|是否绑定了微信
|Data - isWeiboBinded|是否绑定了微博


<h2 id="21">21.获取用户南瓜值页面数据V2.5.2</h2>

请求方法：nggirl/app/cli/personalInfo/getUserValuePage/2.5.2

请求URL：接口地址/nggirl/app/cli/personalInfo/getUserValuePage/2.5.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|[必填]用户授权令牌


请求示例：

> http://localhost/nggirl/app/cli/personalInfo/getUserValuePage/2.5.2

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "userId":101,
        "userValue":150,
        "userLevel":0,
        "hasNextLevel":1,
        "nextLevel":1,
        "needValue":157,
        "profile":"http://testphotosd.nggirl.com.cn/work/68856d91c7674daca32e59c79bdd8a6c.png",
        "jobs":{
          "checkin":0,
          "love":"2",
          "praise":1,
          "share":2,
          "collect":1,
          "comment":3,
          "invite":2
        }
    }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - userId|用户id
|Data - userValue|用户南瓜值
|Data - userLevel|用户身份级别
|Data - hasNextLevel|是否有下一个等级，1有下一个等级，0没有下个等级
|Data - nextLevel|用户的下一个级别
|Data - needValue|达到下一个级别还差的南瓜值
|Data - profile|用户头像
|Data - jobs|用户今日完成任务情况
|Data - jobs - checkin|签到次数
|Data - jobs - love|喜欢次数
|Data - jobs - praise|点赞次数
|Data - jobs - share|分享次数
|Data - jobs - collect|收藏次数
|Data - jobs - comment|评论次数
|Data - jobs - invite|邀请好友次数


<h2 id="22">22.获取用户南瓜值增减记录V2.5.2</h2>

请求方法：nggirl/app/cli/personalInfo/getUserValueRecords/2.5.2

请求URL：接口地址/nggirl/app/cli/personalInfo/getUserValueRecords/2.5.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|[必填]用户授权令牌
|page|页数(非必须，默认第1页)
|num|每页条数（非必须，默认20）


请求示例：

> http://localhost/nggirl/app/cli/personalInfo/getUserValuePage/2.5.2

返回结果示例：

```json
{
    "code": 0,
    "data": [
      {
        "recordTime":"2016-08-12 12:34",
        "type":"签到",
        "sign":"1",
        "userValue":23
      },{
        "recordTime":"2016-08-10 10:09",
        "type":"喜欢",
        "sign":"-1",
        "userValue":1
      }
    ]
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - recordTime|记录时间
|Data - type|增减积分的类型
|Data - sign|增减类别，1增加积分，-1减去积分
|Data - userValue|用户南瓜值增减的数量
