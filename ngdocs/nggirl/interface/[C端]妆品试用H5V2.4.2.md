# 妆品试用H5 V2.4.2


---

* [1.获取试用妆品详情V2.4.2](#1)
* [2.获取申请人员列表或申请成功人员列表V2.1.0](#2)
* [3.获取申请人留言列表V2.1.0](#3)
* [4.用户提交申请V2.1.0](#4)
* [5.获取全部试用列表V2.4.0](#5)
* [6.获取我的试用列表V2.4.0](#6)
* [7.获取试用用户相关信息V2.4.0](#7)

<h2 id="1">1.获取试用妆品详情V2.4.2</h2>
> 出入参数均不变

请求方法：nggirl/app/cli/cosmetic/getCosmeticTrialDetail/2.4.2

请求URL：接口地址/nggirl/app/cli/cosmetic/getCosmeticTrialDetail/2.4.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|用户授权令牌（非必填，登录时必填）|
|cosmeticId|试用妆品编号（必填）|

请求示例
> localhost/nggirl/app/cli/cosmetic/getCosmeticTrialDetail/2.4.2?accessToken=&cosmeticId=1

返回结果示例：
```json
{
    "code":0,
    "data":{
        "id":1,
        "title":"纪梵希面膜试用哈哈哈",
        "headImg":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
        "name":"mac1.5",
        "limits":20,
        "applyNum":20,
        "startTime":1435196075742,
        "endTime":1435196075742,
        "leftTime":"1天10小时",
        "cosmeticStatus":,
        "applyStatus":,
        "applyResult":,
        "cosmeticImg":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
        "applyTime":"2016年06月26日 13:32:40",
        "shareImg":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
        "shareContent":"我在南瓜姑娘申请了XXX，坐等中奖",
        "cosmeticDetail":[
            {
                "cid":1,
                "type":1,
                "content":"hahhahahah",
                "descrip":"",
                "extend":""
            },
             {
                "cid":2,
                "type":2,
                "content":"段落详情段落详情段落详情段落详情",
                "descrip":"",
                "extend":""
            },
             {
                "cid":3,
                "type":3,
                "content":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
                "descrip":"",
                "extend":"200_200"
            },
             {
                "cid":4,
                "type":4,
                "content":"图片描述",
                "descrip":"",
                "extend":""
            }
        ]
    }
}
```

返回字段说明：

|字段名称|字段含义|
|---|---|
|Code|错误码，0表示正确|
|Data - cosmeticId|试用妆品编号|
|Data - title|标题|
|Data - headImg|头图|
|Data - name|妆品名称|
|Data - limits|限量X份|
|Data - applyNum|申请人个数|
|Data - startTime|开始时间|
|Data - endTime|结束时间|
|Data - leftTime|剩余时间|
|Data - cosmeticStatus|试用妆品活动状态 0开放试用，1名单确认，2结果公布|
|Data - applyStatus|申请状态 0未申请，1已申请|
|Data - applyResult|申请结果 0失败，1成功|
|Data - shareImg|分享小图|
|Data - shareContent|分享描述|
|Data - cosmeticImg|试用妆品图|
|Data - applyTime|申请时间 格式为："yyyy年MM月dd日 HH:mm:ss"|
|Data - cosmeticDetail - cid|元件编号|
|Data - cosmeticDetail - type|元件类型，1标题，2段落，3图片，4图片注释|
|Data - cosmeticDetail - content|相关类型的内容。1标题--标题文字，2段落--段落文字，3图片-图片url，4图片注释--注释文字|
|Data - cosmeticDetail - descrip|相关类型的描述。1标题--空，2段落--空，3图片-空，4图片注释--空|
|Data - cosmeticDetail - extend|扩展字段。1标题--空，2段落--空，3图片-宽_高（640_320），4图片注释--空|




<h2 id="2">2.获取申请人员列表或申请成功人员列表V2.1.0</h2>
请求方法：nggirl/app/cli/cosmetic/getApplyUserList/2.1.0

请求URL：接口地址/nggirl/app/cli/cosmetic/getApplyUserList/2.1.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|cosmeticId|试用妆品编号（必填）|
|cosmeticStatus|试用妆品活动状态 0开放试用，1名单确认，2结果公布，3收取试用（必填）|

请求示例
> localhost/nggirl/app/cli/cosmetic/getApplyUserList/2.1.0?cosmeticId=1&cosmeticStatus=0

返回结果示例：
```json
{
    "code":0,
    "data":[
        {
            "userId":269,
            "profile":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
            "nickName":"damon"
        },
        {
            "userId":270,
            "profile":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
            "nickName":"damon1"
        },
        {
            "userId":271,
            "profile":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
            "nickName":"damon2"
        }
    ]
}
```
返回字段说明：

|字段名称|字段含义|
|---|---|
|Code|错误码，0表示正确|
|Data - userId|用户id|
|Data - profile|声请人头像|
|Data - nickName|申请人昵称|


<h2 id="3">3.获取申请人留言列表V2.1.0</h2>
请求方法：nggirl/app/cli/cosmetic/getLeaveMessageList/2.1.0

请求URL：接口地址/nggirl/app/cli/cosmetic/getLeaveMessageList/2.1.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|cosmeticId|试用妆品编号（必填）|
|pageNum|第几页，从0开始（非必填）|
|pageSize|每页多少条，默认20（非必填）|

请求示例
> localhost/nggirl/app/cli/cosmetic/getLeaveMessageList/2.1.0?cosmeticId=1&cosmeticStatus=0

返回结果示例：
```json
{
    "code":0,
    "data":[
        {
            "userId":1,
            "profile":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
            "nickName":"我又不甜",
            "message":"我想试试这个",
            "applyTime":1435196075742
        },
        {
            "userId":2,
            "profile":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
            "nickName":"我又不甜",
            "message":"我想试试这个",
            "applyTime":1435196075742
        },
        {
            "userId":3,
            "profile":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
            "nickName":"我又不甜",
            "message":"我想试试这个",
            "applyTime":1435196075742
        }
    ]
}
```
返回字段说明：

|字段名称|字段含义|
|---|---|
|Code|错误码，0表示正确|
|Data - userId|用户id|
|Data - profile|用户头像|
|Data - nickName|用户昵称|
|Data - message|留言内容|
|Data - applyTime|留言时间|


<h2 id="4">4.用户提交申请V2.1.0</h2>
请求方法：nggirl/app/cli/cosmetic/commitApply/2.1.0

请求URL：接口地址/nggirl/app/cli/cosmetic/commitApply/2.1.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义|
|---|---|
|cosmeticId|试用妆品编号（必填）|
|accessToken|用户授权令牌（必填）|
|realName|用户姓名（必填）|
|sex|用户性别 0男，1女（非必填）|
|age|用户年龄（非必填）|
|phoneNum|用户手机号码（必填）|
|wechat|用户微信号码（必填）|
|skinType|肤质（非必填）|
|address|收货地址（必填）|
|message|留言内容（非必填）|

请求示例
> localhost/nggirl/app/cli/cosmetic/getLeaveMessageList/2.1.0

返回结果示例：
```json
{
    "code":0,
    "data":{
        "cosmeticId":1,
        "name":"mac口红",
        "cosmeticImg":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
        "applyTime":"2016年06月26日 13:32:40",
        "cosmeticStatus":0,
        "applyStatus":1,
        "applyResult":0
    }
}
```
返回结果说明：

|字段名称|字段含义|
|---|---|
|Code|错误码，0表示正确|
|Data - cosmeticId|试用妆品id|
|Data - name|试用妆品名称|
|Data - cosmeticImg|试用妆品图|
|Data - applyTime|申请时间|
|Data - cosmeticStatus|试用妆品活动状态 0开放试用，1名单确认，2结果公布，3收取试用|
|Data - applyStatus|申请状态 0未申请，1已申请|
|Data - applyResult|申请结果 0失败，1成功|


<h2 id="5">5.获取全部试用列表V2.4.0</h2>

请求方法：nggirl/app/cli/cosmetic/getAllCosmeticTrialList/2.4.0

请求URL：接口地址/nggirl/app/cli/cosmetic/getAllCosmeticTrialList/2.4.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|pageNum|第几页，从0开始（非必填）|
|pageSize|每页多少条，默认20（非必填）|

请求示例
> localhost/nggirl/app/cli/cosmetic/getAllCosmeticTrialList/2.4.0

返回结果示例：
```json
{
    "code":0,
    "data":[{
        "cosmeticId":1,
        "title":"mac口红",
        "headImg":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
        "limits":5,
        "applyNum":56,
        "leftTime":"1天14小时",
        "shareContent":"我在南瓜姑娘申请了精美妆品，坐等中奖，快来围观～",
        "shareImg":"http://photosd.nggirl.com.cn/work/48d5972821d6444ab8eabfe2d69c8b88.jpg"
    },
    {
        "cosmeticId":1,
        "title":"mac口红",
        "headImg":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
        "limits":5,
        "applyNum":56,
        "leftTime":"1天14小时",
        "shareContent":"我在南瓜姑娘申请了精美妆品，坐等中奖，快来围观～",
        "shareImg":"http://photosd.nggirl.com.cn/work/48d5972821d6444ab8eabfe2d69c8b88.jpg"
    }]
}
```
返回结果说明：

|字段名称|字段含义|
|---|---|
|Code|错误码，0表示正确|
|Data - cosmeticId|试用妆品id|
|Data - title|标题|
|Data - headImg|头图|
|Data - limits|申请限量多少份|
|Data - applyNum|申请人数|
|Data - leftTime|剩余时间,如果返回空字符串"",表示申请时间已经结束|
|Data - shareContent|分享内容|
|Data - shareImg|分享小图|



<h2 id="6">6.获取我的试用列表V2.4.0</h2>
请求方法：nggirl/app/cli/cosmetic/getMyCosmeticTrialList/2.4.0

请求URL：接口地址/nggirl/app/cli/cosmetic/getMyCosmeticTrialList/2.4.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|用户授权令牌（必填）|
|pageNum|第几页，从0开始（非必填）|
|pageSize|每页多少条，默认20（非必填）|

请求示例
> localhost/nggirl/app/cli/cosmetic/getMyCosmeticTrialList/2.4.0

返回结果示例：
```json
{
    "code":0,
    "data":[{
        "cosmeticId":1,
        "title":"mac口红",
        "headImg":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
        "limits":5,
        "applyNum":56,
        "leftTime":"1天14小时",
        "shareContent":"我在南瓜姑娘申请了精美妆品，坐等中奖，快来围观～",
        "shareImg":"http://photosd.nggirl.com.cn/work/48d5972821d6444ab8eabfe2d69c8b88.jpg"
    },
    {
        "cosmeticId":1,
        "title":"mac口红",
        "headImg":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
        "limits":5,
        "applyNum":56,
        "leftTime":"1天14小时",
        "shareContent":"我在南瓜姑娘申请了精美妆品，坐等中奖，快来围观～",
        "shareImg":"http://photosd.nggirl.com.cn/work/48d5972821d6444ab8eabfe2d69c8b88.jpg"
    }]
}
```
返回结果说明：

|字段名称|字段含义|
|---|---|
|Code|错误码，0表示正确|
|Data - cosmeticId|试用妆品id|
|Data - title|标题|
|Data - headImg|头图|
|Data - limits|申请限量多少份|
|Data - applyNum|申请人数|
|Data - leftTime|剩余时间，如果返回空字符串"",表示申请时间已经结束|
|Data - shareContent|分享内容|
|Data - shareImg|分享小图|


<h2 id="7">7.获取试用用户相关信息V2.4.0</h2>
请求方法：nggirl/app/cli/cosmetic/getCosmeticTrialUserInfo/2.4.0

请求URL：接口地址/nggirl/app/cli/cosmetic/getCosmeticTrialUserInfo/2.4.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|用户授权令牌（必填）|

请求示例：
> localhost:/nggirl/app/cli/cosmetic/getCosmeticTrialUserInfo/2.4.0

返回结果示例：
```json
{
    "code":0,
    "data":{
        "isFirstApply":1,
        "userId":269,
        "realName":"张刘洋",
        "sex":1,
        "age":18,
        "phoneNum":18516993208,
        "wechat":9452594148,
        "skinType":"油性",
        "address":"嘉盛中心2006"
    }
}
```

返回字段说明：

|字段名称|字段含义|
|----|----|
|Code|错误标识码，0表示正确|
|Data - isFirstApply|是否是第一次申请：0否，1是，如果不是第一次申请，就把下面的相关信息带入到申请表单里面|
|Data - userId|用户编号|
|Data - realName|用户真实姓名|
|Data - sex|性别0男，1女|
|Data - age|年龄|
|Data - phoneNum|手机号码|
|Data - wechat|微信号|
|Data - skinType|肤质类型|
|Data - address|收货地址|
















