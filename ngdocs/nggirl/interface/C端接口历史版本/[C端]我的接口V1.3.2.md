<h1>我的接口v1.3.2</h1>
目录

* [1.个人资料显示](#1)
* [2.背景封面图修改](#2)
* [3.我的预约](#3)
* [4.我的预约(返回更多的信息)](#4)
* [5.关注的化妆师](#5)
* [6.我的收藏](#6)
* [7.我的邀请码](#7)
* [8.领取优惠券](#8)
* [9.设置](#9)
 * [9.1.修改密码](#9.1)
 * [9.2.预约与退约规则](#9.2)
 * [9.3.评价](#9.3)
 * [9.4.服务条款](#9.4)
* [10.注销](#10)
* [11.领取活动优惠券（支持未注册用户）](#11)
* [12.获取非绑定的优惠券](#12)


<h2 id="1">1.个人资料显示</h2>

请求方法：nggirl/app/cli/personalInfo/getUserInfo

请求URL：接口地址/nggirl/app/cli/personalInfo/getUserInfo

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|用户授权令牌

请求示例：
> http://localhost/nggirl/app/cli/personalInfo/getUserInfo?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

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
        "district": "北京朝阳",
        "address": "北京市朝阳区潘家园南里13-1-602",
        "cover": "http://www.baidu.com/2.jpg",
         "score":100,
    "phoneNum":"134261294566"
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
|Data - district	|用户所在城市
|Data - address	|用户的详细地址
|Data - cover	|用户的背景封面图
|Data - score	|用户积分
|Data - phoneNum	|用户手机号

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


<h2 id="5">5. 关注的化妆师</h2>

请求方法：nggirl/app/cli/personalInfo/listInterestDresser

请求URL：接口地址/nggirl/app/cli/personalInfo/listInterestDresser

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|用户授权令牌
|page|页数(非必须，默认第1页)
|num|每页条数（非必须，默认20）

请求示例：

> http://localhost/nggirl/app/cli/personalInfo/listInterestDresser?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&page=0&num=20

返回结果示例：

```json
{
    "code": 0,
    "data": [{
        "dresserId": 100,
        "name": "王子涵",
        "orderNum":58,
        "workType":["职业装","约会妆"],
        "profile": "http://www.baidu.com/1.jpg",
        "authentication": 1,
        "starLevel": 5,
        "isVDresser":1
     },{
        "dresserId": 100,
        "name": "王子涵",
        "orderNum":58,
        "workType":["职业装","约会妆"],
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
|Data - workType	|妆束类型
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


<h2 id="8">8.领取优惠券</h2>

请求方法：nggirl/app/cli/personalInfo/receiveCoupon

请求URL：接口地址/nggirl/app/cli/personalInfo/receiveCoupon

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|用户授权令牌
|couponNum   |优惠券编码

请求示例：
> http://localhost/nggirl/app/cli/personalInfo/receiveCoupon?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&couponNum=Q2714141456

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

<h2 id="9.1">9.1. 修改密码</h2>

请求方法：nggirl/app/cli/personalInfo/resetPassword

请求URL：接口地址/nggirl/app/cli/personalInfo/resetPassword

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken	|用户授权令牌
|oldPassword|旧密码MD5
|newPassword|新密码MD5

请求示例：
> http://localhost/nggirl/app/cli/personalInfo/resetPassword?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&oldPassword=1231213&newPassword=kevin1202

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

<h2 id="11">11.领取活动优惠券（支持未注册用户）</h2>

请求方法：nggirl/app/cli/personalInfo/createUnbindCoupon

请求URL：接口地址/nggirl/app/cli/personalInfo/createUnbindCoupon

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---
|phoneNum	|手机号
|code   |活动关联的邀请码

请求示例：
> http://localhost/nggirl/app/cli/personalInfo/createUnbindCoupon?phoneNum=13426129466&code=SOP12345N&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "info":"优惠券已经放到您的手机号账号中"
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - info	|领取成功或者失败的描述信息


<h2 id="12">12.获取非绑定的优惠券</h2>
>如果用户已经注册过，该方法会获取直接用手机号注册的用户和在个人信息中绑定过手机号的用户。

请求方法：nggirl/app/cli/personalInfo/createUnbindCoupon

请求URL：接口地址/nggirl/app/cli/personalInfo/createUnbindCoupon

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|phoneNum	|领券手机号
|code	|优惠码

请求示例：
> http://localhost/nggirl/app/cli/personalInfo/createUnbindCoupon?phoneNum=18518676735&code=abcdefgh&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：

```json
{
    "code": 0,
    "data": {
    	"error": "领取优惠券成功!"
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - error	|返回的提示信息

> code=0时，error="领取优惠券成功!";code=1时，error可能为："您已经领过该优惠券了!"、"优惠券已经领光了!"、"找不到这个优惠券!"
