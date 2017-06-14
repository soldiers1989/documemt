# 妆品试用V3.0.2.md



---


* [1.当前试用活动列表V2.5.6](#1)
* [2.往期试用活动列表V2.5.6](#2)
* [3.试用活动详情V2.5.6](#3)
* [4.试用报告详情V2.5.6](#4)
* [5.新增/编辑试用报告V2.5.6](#5)
* [6.提交试用报告V3.0.2](#6)
* [7.某个试用活动的试用报告列表V2.5.6](#7)
* [8.试用活动列表V2.5.6(1和2合并android)](#8)
* [9.获取申请人留言列表V2.5.6](#9)


<h2 id="1">1.当前试用活动列表V2.5.6</h2>

请求方法：nggirl/app/cli/cosmetic/getCurrentCosmeticTrialList/2.5.6

请求URL：接口地址/nggirl/app/cli/cosmetic/getCurrentCosmeticTrialList/2.5.6

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|【非必填，登录时必填】用户授权令牌|
|isMine|【必填】0所有当前试用，1我的当前试用|

请求示例
> localhost/nggirl/app/cli/cosmetic/getCurrentCosmeticTrialList/2.5.6

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
        "shareImg":"",
        "shareContent":""
    },
    {
        "cosmeticId":1,
        "title":"mac口红",
        "headImg":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
        "limits":5,
        "applyNum":56,
        "leftTime":"1天14小时",
        "shareImg":"",
        "shareContent":""
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
|Data - shareImg|分享小图|
|Data - shareContent|分享内容|




<h2 id="2">2.往期试用活动列表V2.5.6</h2>

请求方法：nggirl/app/cli/cosmetic/getPastCosmeticTrialList/2.5.6

请求URL：接口地址/nggirl/app/cli/cosmetic/getPastCosmeticTrialList/2.5.6

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|【非必填，登录时必填】用户授权令牌|
|isMine|【必填】0所有往期试用，1我的往期试用|
|pageNum|第几页，从0开始（非必填）|
|pageSize|每页多少条，默认20（非必填）|

请求示例
> localhost/nggirl/app/cli/cosmetic/getPastCosmeticTrialList/2.5.6

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
        "shareImg":"",
        "shareContent":""
    },
    {
        "cosmeticId":1,
        "title":"mac口红",
        "headImg":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
        "limits":5,
        "applyNum":56,
        "leftTime":"1天14小时",
        "shareImg":"",
        "shareContent":""
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
|Data - shareImg|分享小图|
|Data - shareContent|分享内容|






<h2 id="3">3.试用活动详情V2.5.6</h2>

请求方法：nggirl/app/cli/cosmetic/getCosmeticTrialDetail/2.5.6

请求URL：接口地址/nggirl/app/cli/cosmetic/getCosmeticTrialDetail/2.5.6

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|【非必填，登录时必填】用户授权令牌|
|cosmeticId|【必填】试用活动编号|

请求示例
> localhost/nggirl/app/cli/cosmetic/getCosmeticTrialDetail/2.5.6?accessToken=&cosmeticId=1

返回结果示例：
```json
{
    "code":0,
    "data":{
        "cosmeticId":1,
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
        "reportStatus":0,
        "reportId":0,
        "cosmeticImg":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
        "applyTime":"2016年06月26日 13:32:40",
        "shareImg":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
        "shareContent":"我在南瓜姑娘申请了XXX，坐等中奖",
        "cosmeticDetail":[
            {
                "type":1,
                "content":"hahhahahah",
                "descrip":"",
                "extend":""
            },
             {
                "type":2,
                "content":"段落详情段落详情段落详情段落详情",
                "descrip":"",
                "extend":""
            },
             {
                "type":3,
                "content":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
                "descrip":"",
                "extend":"200_200"
            },
             {
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
|Data - reportStatus|试用报告状态：0未填写，1已填写未提交，2已提交|
|Data - reportId|试用报告编号，还没有试用报告的时候值为-1|
|Data - shareImg|分享小图|
|Data - shareContent|分享描述|
|Data - cosmeticImg|试用妆品图|
|Data - applyTime|申请时间 格式为："yyyy年MM月dd日 HH:mm:ss"|
|Data - cosmeticDetail - type|元件类型，2段落，3图片|
|Data - cosmeticDetail - content|相关类型的内容。2段落--段落文字，3图片-图片url|
|Data - cosmeticDetail - descrip|相关类型的描述。2段落--空，3图片-空|
|Data - cosmeticDetail - extend|扩展字段。2段落--空，3图片-宽_高（640_320）|




<h2 id="4">4.试用报告详情V2.5.6</h2>

请求方法：nggirl/app/cli/cosmetic/getReportDetail/2.5.6

请求URL：接口地址/nggirl/app/cli/cosmetic/getReportDetail/2.5.6

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|reportId|试用报告编号|

请求示例
> localhost/nggirl/app/cli/cosmetic/getReportDetail/2.5.6

返回结果示例：
```json
{
    "code":0,
    "data":{
        "reportId":1,
        "title":"kouhongshiyong",
        "userId":"269",
        "profile":"",
        "nickName":"hahha",
        "submitTime":1435196075742,
        "reportDetail":[
            {
                "type":2,
                "content":"sdfdshfkjhfds",
                "descrip":"",
                "extend":"",
            },
            {
                "type":3,
                "content":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
                "descrip":"",
                "extend":"640_320",
            }
        ]
    }
}
```

返回字段说明：

|字段名称|字段含义|
|---|---|
|Code|错误标识码，0标识正确|
|Data - reportId|试用报告编号|
|Data - title|试用活动标题|
|Data - userId|用户编号|
|Data - profile|用户头像|
|Data - nickName|用户昵称|
|Data - submitTime|提交时间或者创建时间|
|Data - reportDetail - type|2段落，3图片|
|Data - reportDetail - content|2段落内容，3图片url|
|Data - reportDetail - descrip|2空，3空|
|Data - reportDetail - extend|2空，3图片宽_高(640_320)|






<h2 id="5">5.新增/编辑试用报告V2.5.6</h2>

请求方法：nggirl/app/cli/cosmetic/addOrEdit/2.5.6

请求URL：接口地址/nggirl/app/cli/cosmetic/addOrEdit/2.5.6

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|【必填】用户授权令牌|
|cosmeticId|【非必填，如果是新增报告，则必填】试用活动编号|
|reportId|【非必填，如果是编辑已有的报告，则必填】试用报告编号|
|reportDetail|试用报告详情：包括段落和图片（JSON格式字符串）|

reportDetail示例：
```json
[
  {
    "type":2,
    "content":"段落详情段落详情",
    "descrip":"",
    "extend":""
  },{
    "type":3,
    "content":"http://photosd.nggirl.com.cn/work/5873566f4257414c9cec9b4ff0b27635.png",
    "descrip":"",
    "extend":"640_320"
  },{
  "type":2,
  "content":"段落详情段落详情",
  "descrip":"",
  "extend":""
  }
]
```
> type=3时，extend保存的是图片的宽_高(640_320)

请求示例
> localhost/nggirl/app/cli/cosmetic/addOrEdit/2.5.6

返回结果示例：
```json
{
    "code":0,
    "data":{
        "reportId":1
    }
}
```
返回结果说明：

|字段名称|字段含义|
|---|---|
|Code|错误标识码，0表示正确|
|Data - reportId|试用报告编号|


<h2 id="6">6.提交试用报告V3.0.2</h2>

> 返回字段增加addScore

请求方法：nggirl/app/cli/cosmetic/submit/3.0.2

请求URL：接口地址/nggirl/app/cli/cosmetic/submit/3.0.2

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|【必填】用户授权令牌|
|cosmeticId|【非必填，如果是新增报告，则必填】试用活动编号|
|reportId|【非必填，如果是编辑已有的报告，则必填】试用报告编号|
|reportDetail|试用报告详情：包括段落和图片（JSON格式字符串）|

reportDetail示例：
```json
[
  {
    "type":2,
    "content":"段落详情段落详情",
    "descrip":"",
    "extend":""
  },{
    "type":3,
    "content":"http://photosd.nggirl.com.cn/work/5873566f4257414c9cec9b4ff0b27635.png",
    "descrip":"",
    "extend":"640_320"
  },{
  "type":2,
  "content":"段落详情段落详情",
  "descrip":"",
  "extend":""
  }
]
```
> type=3时，extend保存的是图片的宽_高(640_320)

请求示例
> localhost/nggirl/app/cli/cosmetic/submit/3.0.2

返回结果示例：
```json
{
    "code":0,
    "data":{
        "reportId":1,
        "addScore":10
    }
}
```

返回结果说明：

|字段名称|字段含义|
|---|---|
|Code|错误标识码，0表示正确|
|Data - reportId|试用报告编号|
|Data - addScore|此次操作增加的积分|




<h2 id="7">7.某个试用活动的试用报告列表V2.5.6</h2>

请求方法：nggirl/app/cli/cosmetic/getCosmeticReportList/2.5.6

请求URL：接口地址/nggirl/app/cli/cosmetic/getCosmeticReportList/2.5.6

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|cosmeticId|【必填】试用活动编号|
|pageNum|第几页，从0开始（非必填）|
|pageSize|每页多少条，默认20（非必填）|

请求示例
> localhost/nggirl/app/cli/cosmetic/getCosmeticReportList/2.5.6

返回结果示例：
```json
{
    "code":0,
    "data":[{
        "reportId":1,
        "userId":269,
        "profile":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
        "nickName":"tom",
        "submitTime":1456788515544,
        "picList":[
            "http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
            "http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
            "http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg"
        ],
        "text":"完美的化妆品，很适合我的皮肤。。"
    },
    {
        "reportId":1,
        "userId":269,
        "profile":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
        "nickName":"tom",
        "submitTime":1456788515544,
        "picList":[
            "http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
            "http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
            "http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg"
        ],
        "text":"完美的化妆品，很适合我的皮肤。。"
    }]
}
```
返回结果说明：

|字段名称|字段含义|
|---|---|
|Code|错误标识码，0表示正确|
|Data - reportId|试用报告编号|
|Data - userId|用户编号|
|Data - profile|用户头像|
|Data - nickName|用户昵称|
|Data - submitTime|提交时间|
|Data - picList|图片列表（试用报告的前三章图片，最多三张，也可能没有）|
|Data - text|文字内容（试用报告的第一段文字）|



<h2 id="8">8.试用活动列表V2.5.6(1和2合并android用</h2>

请求方法：nggirl/app/cli/cosmetic/getCosmeticTrialList/2.5.6

请求URL：接口地址/nggirl/app/cli/cosmetic/getCosmeticTrialList/2.5.6

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|【非必填，登录时必填】用户授权令牌|
|isMine|【必填】0所有试用，1我的试用|
|pageNum|第几页，从0开始（非必填）|
|pageSize|每页多少条，默认20（非必填）|


请求示例
> localhost/nggirl/app/cli/cosmetic/getCosmeticTrialList/2.5.6

返回结果示例：
```json
{
    "code":0,
    "data":{
        "currList": [{
            "cosmeticId":1,
            "title":"mac口红",
            "headImg":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
            "limits":5,
            "applyNum":56,
            "leftTime":"1天14小时",
            "shareImg":"",
            "shareContent":""
        },
        {
            "cosmeticId":1,
            "title":"mac口红",
            "headImg":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
            "limits":5,
            "applyNum":56,
            "leftTime":"1天14小时",
            "shareImg":"",
            "shareContent":""
        }],
        "pastList":[{
            "cosmeticId":1,
            "title":"mac口红",
            "headImg":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
            "limits":5,
            "applyNum":56,
            "leftTime":"1天14小时",
            "shareImg":"",
            "shareContent":""
        },
        {
            "cosmeticId":1,
            "title":"mac口红",
            "headImg":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
            "limits":5,
            "applyNum":56,
            "leftTime":"1天14小时",
            "shareImg":"",
            "shareContent":""
        }]
    }
    
   
}
```
返回结果说明：

|字段名称|字段含义|
|---|---|
|Code|错误码，0表示正确|
|Data - currList - cosmeticId|试用妆品id|
|Data - currList - title|标题|
|Data - currList - headImg|头图|
|Data - currList - limits|申请限量多少份|
|Data - currList - applyNum|申请人数|
|Data - currList - leftTime|剩余时间,如果返回空字符串"",表示申请时间已经结束|
|Data - currList - shareImg|分享小图|
|Data - currList - shareContent|分享内容|
|Data - pastList - cosmeticId|试用妆品id|
|Data - pastList - title|标题|
|Data - pastList - headImg|头图|
|Data - pastList - limits|申请限量多少份|
|Data - pastList - applyNum|申请人数|
|Data - pastList - leftTime|剩余时间,如果返回空字符串"",表示申请时间已经结束|
|Data - pastList - shareImg|分享小图|
|Data - pastList - shareContent|分享内容|



<h2 id="9">9.获取申请人留言列表V2.5.6</h2>

请求方法：nggirl/app/cli/cosmetic/getLeaveMessageList/2.5.6

请求URL：接口地址/nggirl/app/cli/cosmetic/getLeaveMessageList/2.5.6

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|cosmeticId|试用妆品编号（必填）|
|pageNum|第几页，从0开始（非必填）|
|pageSize|每页多少条，默认20（非必填）|

请求示例
> localhost/nggirl/app/cli/cosmetic/getLeaveMessageList/2.5.6?cosmeticId=1&cosmeticStatus=0

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
            "applyTime":"18:20"
        },
        {
            "userId":2,
            "profile":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
            "nickName":"我又不甜",
            "message":"我想试试这个",
            "applyTime":"2015-11-11"
        },
        {
            "userId":3,
            "profile":"http://photosd.nggirl.com.cn/work/22b001b920f5439481b2b7e210906a28.jpg",
            "nickName":"我又不甜",
            "message":"我想试试这个",
            "applyTime":"2015-11-11"
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
