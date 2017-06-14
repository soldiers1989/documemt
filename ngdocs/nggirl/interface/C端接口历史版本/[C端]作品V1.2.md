<h1>作品</h1>
目录

* [1.获取轮播头图列表](#1)
* [2.获取所有作品列表v1.2](#2)
* [3.获取作品详情(和化妆师端不同)v1.2](#3)
* [4.获取作品详情(一次获取所有信息)v1.2](#4)
* [5.获取评价总数](#5)
* [6.获取作品评论v1.2](#6)
* [7.获取喜欢的人总数](#7)
* [8.获取喜欢的人](#8)
* [9.作品推荐v1.2](#9)
* [10.收藏作品](#10)
* [11.取消收藏](#11)
* [12.作品点赞](#12)
* [13.取消点赞](#13)
* [14.可预约时间段](#14)
* [15.我要预约V1.2](#15)
* [16.我的预约](#16)
* [17.取消预约](#17)
* [18.支付](#18)
* [19.删除支付记录（支付失败时调用）](#19)
* [20.退款](#20)
* [21.完成预约](#21)
* [22.预约详情](#22)
* [23.写评价(对化妆师的评论，也可以说对预约单的评论)](#23)
* [24.获取评价(对化妆师的评论，也可以说对预约单的评论)](#24)
* [25.投诉](#25)
* [26.获取作品的用户晒单v1.2](#26)
* [27.获取活动对应的作品列表v1.2](#27)
* [28.退款操作通知](#28)

<h2 id="1">1.获取轮播头图列表</h2>

请求方法：nggirl/app/cli/works/listHeadScroll

请求URL：接口地址/nggirl/app/cli/works/listHeadScroll

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌


请求示例：

> http://localhost/nggirl/app/cli/works/listHeadScroll?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0

返回结果示例：

```json
{
   "code": 0
    "data":[{
	"photoUrl": " http://www.baidu.com/1.jpg",
		"webpageUrl":"http://www.nggirl.com.cn"
	},
	{
		"photoUrl": "http://www.baidu.com/1.jpg",
		"webpageUrl":"http://www.nggirl.com.cn"
     }]
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - photoUrl	|显示的图片路径
|Data - webpageUrl	|跳转到的web页面链接地址




<h2 id="2">2.获取所有作品列表v1.2</h2>

请求方法：nggirl/app/cli/works/listWorks/1.2

请求URL：接口地址/nggirl/app/cli/works/listWorks/1.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|page	|页数  非必需参数，默认第一页
|num	|每页信息数目 非必需参数，默认20

请求示例：

> http://localhost/nggirl/app/cli/works/listWorks/1.2?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&page=0&num=20

返回结果示例：

```json
{
    "code": 0
    "data":[{
	"workId": 1234567,
	"cover":"http://www.baidu.com/1.jpg",
	"workType":"职业装",
	"cost":100,
	"praiseNum":12,
	"dresserId":1234567,
	"dresserName":"于子涵",
	"dresserProfile":"http://www.baidu.com/1.jpg",
	"descriptions":"肤质较佳的女生。强调重点：强调眼唇重点。以润色隔离霜作为底妆，然后以睫毛膏……",
	"praiseStatus":1,
	"isVDresser":1,
	"recommendType":1,
    "hasDiscount":1,
    "discount":{
        "id":1,
        "workId":123,
    	"name":"首单五折",
        "desc":"新用户首次下单五折优惠，还可叠加使用优惠券",
        "cost":50,
        "icon":"http://testphotosd.nggirl.com.cn/work/aee4e7c292094a24a72ac8da401bbd7d.png"
    	}
	},
	{
	"workId": 1234567,
	"cover":"http://www.baidu.com/1.jpg",
	"workType":"职业装",
	"cost":100,
	"praiseNum":12,
	"dresserId":1234567,
	"dresserName":"于子涵",
	"dresserProfile":"http://www.baidu.com/1.jpg",
	"descriptions":"肤质较佳的女生。强调重点：强调眼唇重点。以润色隔离霜作为底妆，然后以睫毛膏…….",
	"praiseStatus":1,
	"isVDresser":0,
	"recommendType":1,
     "hasDiscount":0,
    "discount":{
        "id":"",
        "workId":"",
    	"name":"",
        "desc":"",
        "cost":,
        "icon":""
    	}
       }]
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - workId	|作品编号
|Data - cover	|封面图片路径
|Data - workType|作品类型
|Data - cost	|费用
|Data - praiseNum|点赞人数
|Data - dresserId|化妆师编号
|Data - dresserName|化妆师姓名
|Data - dresserProfile|化妆师头像
|Data - descriptions|作品描述
|Data - praiseStatus|点赞状态，0为未点赞，1为已点赞
|Data - isVDresser|是否为加V化妆师，0为否，1为是
|Data - recommendType|推荐类型，0为小图推荐，1为大图推荐
|Data - hasDiscount|此作品是否参与了活动，0没有，1有
|Data - discount - id|活动编号
|Data - discount - workId|参与活动的作品编号
|Data - discount - name|活动名称，显示在作品的活动栏（红底部分）
|Data - discount - desc|活动描述，显示在作品的活动栏
|Data - discount - cost|参与活动后的价格
|Data - discount - icon|活动的图标，用于放在作品的图片右上角




<h2 id="3">3.获取作品详情(和化妆师不同)v1.2</h2>

请求方法：nggirl/app/cli/works/getWorksDetail/1.2

请求URL：接口地址/nggirl/app/cli/works/getWorksDetail/1.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|workId	|作品编号

请求示例：

> http://localhost/nggirl/app/cli/works/getWorksDetail/1.2?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&workId=123456

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "workId": 211,
        "cover": "http://photosd.nggirl.com.cn/work/bb57050e9c4f454c91c30986210ecf25.jpg",
        "workType": "约会妆",
        "cost": 1,
        "reservationNum": 15,
        "timeUsed": 1204,
        "contentPhoto": [],
        "descriptions": "适合逛街、约会、宴会等。 妆面特点：妆容相对生活妆稍浓，发型多变， 发型简约。服务内容：妆面，简约发型。 ",
        "cosmetics": [
            {
                "cosmeticsClass": "粉底液",
                "cosmeticsBrand": [
                    "M.A.C（魅可）",
                    "Bobbi Brown 芭比布朗",
                    "NARS",
                    "rmk"
                ]
            },
            {
                "cosmeticsClass": "散粉",
                "cosmeticsBrand": [
                    "M.A.C（魅可）",
                    "Shu Uemura(植村秀)"
                ]
            },
            {
                "cosmeticsClass": "眼影",
                "cosmeticsBrand": [
                    "Dior迪奥",
                    "丝芙兰SEPHORA"
                ]
            },
            {
                "cosmeticsClass": "眼线笔",
                "cosmeticsBrand": [
                    "植村秀shu uemura"
                ]
            },
            {
                "cosmeticsClass": "眼线膏",
                "cosmeticsBrand": [
                    "Shu Uemura(植村秀)"
                ]
            },
            {
                "cosmeticsClass": "睫毛膏",
                "cosmeticsBrand": [
                    "兰蔻",
                    "魅可"
                ]
            },
            {
                "cosmeticsClass": "腮红",
                "cosmeticsBrand": [
                    "Shu Uemura植村秀"
                ]
            },
            {
                "cosmeticsClass": "眉笔",
                "cosmeticsBrand": [
                    "Bobbi Brown（芭比波朗）"
                ]
            },
            {
                "cosmeticsClass": "眉粉",
                "cosmeticsBrand": [
                    "NARS"
                ]
            },
            {
                "cosmeticsClass": "高光粉",
                "cosmeticsBrand": [
                    "make up for ever"
                ]
            },
            {
                "cosmeticsClass": "阴影粉",
                "cosmeticsBrand": [
                    "make up for ever"
                ]
            },
            {
                "cosmeticsClass": "口红",
                "cosmeticsBrand": [
                    "M.A.C（魅可）"
                ]
            },
            {
                "cosmeticsClass": "唇彩",
                "cosmeticsBrand": [
                    "M.A.C（魅可）"
                ]
            }
        ],
        "tags": [
            "欧美风",
            "气场女王",
            "烟熏妆"
        ],
        "publishTime": 1439377048000,
        "praiseStatus": 0,
        "collectStatus": 0,
        "dresserId": 58,
        "dresserName": "薛云梦（海威）",
        "dresserProfile": "http://nggirl-product-res.oss-cn-beijing.aliyuncs.com/work/97161288e0b342848210acd806721896.jpg",
        "starLevel": 4,
        "authentication": 0,
        "isVDresser": 0,
        "sex": 0,
        "hasDiscount":1,
        "discount":{
            "id":1,
            "workId":123,
            "name":"首单五折",
            "desc":"新用户首次下单五折优惠，还可叠加使用优惠券",
            "cost":50,
            "icon":"http://testphotosd.nggirl.com.cn/work/aee4e7c292094a24a72ac8da401bbd7d.png",
            "allow":1
            }
    }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - workId	|作品编号
|Data - cover	|封面图片路径
|Data - workType	|作品类型
|Data - cost	|费用
|Data - reservationNum	|预约人数
|Data - timeUsed	|作品耗时，以分钟为单位
|Data - contentPhoto|其他图片的路径列表
|Data -  descriptions|作品描述
|Data - cosmetics|使用的化妆品信息
|Data –cosmetics - cosmeticsClass	|化妆品品类
|Data –cosmetics - cosmeticsBrand|化妆品品牌列表
|Data -  tags|作品标签列表
|Data - publishTime|时间， 13位数字，代表自January 1, 1970 00:00:00 GMT开始到现在经历的毫秒数
|Data - praiseStatus | 点赞状态，0未点赞，1为点赞
|Data - collectStatus | 收藏状态，0未收藏，1已收藏
|Data - dresserId | 化妆师编号
|Data - dresserName|化妆师名称
|Data - dresserProfile|头像文件路径
|Data - starLevel|星级
|Data - authentication|是否已经认证，0未认证，1已认证
|Data - isVDresser|是否为加V化妆师，0为否，1为是
|Data - sex|化妆师性别，0为男，1为女。
|Data - hasDiscount|此作品是否参与了活动，0没有，1有
|Data - discount - id|活动编号
|Data - discount - workId|参与活动的作品编号
|Data - discount - name|活动名称，显示在作品的活动栏（红底部分）
|Data - discount - desc|活动描述，显示在作品的活动栏
|Data - discount - cost|参与活动后的价格
|Data - discount - icon|活动的图标，用于放在作品的图片右上角
|Data - discount - allow|该用户是否可享受折扣,0不可以，1可以





<h2 id="4">4.获取作品详情（一次获取所有信息）v1.2</h2>


请求方法：nggirl/app/cli/works/getWorksDetailIos/1.2

请求URL：接口地址/nggirl/app/cli/works/getWorksDetailIos/1.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|workId	|作品编号

请求示例：

> http://localhost/nggirl/app/cli/works/getWorksDetailIos/1.2?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&workId=123456

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "workId": 211,
        "cover": "http://photosd.nggirl.com.cn/work/bb57050e9c4f454c91c30986210ecf25.jpg",
        "workType": "约会妆",
        "cost": 1,
        "reservationNum": 15,
        "timeUsed": 1204,
        "contentPhoto": [
            "http://photosd.nggirl.com.cn/work/bb57050e9c4f454c91c30986210ecf25.jpg"
        ],
        "descriptions": "适合逛街、约会、宴会等。 妆面特点：妆容相对生活妆稍浓，发型多变， 发型简约。服务内容：妆面，简约发型。 ",
        "cosmetics": [
            {
                "cosmeticsClass": "粉底液",
                "cosmeticsBrand": [
                    "M.A.C（魅可）",
                    "Bobbi Brown 芭比布朗",
                    "NARS",
                    "rmk"
                ]
            },
            {
                "cosmeticsClass": "散粉",
                "cosmeticsBrand": [
                    "M.A.C（魅可）",
                    "Shu Uemura(植村秀)"
                ]
            },
            {
                "cosmeticsClass": "眼影",
                "cosmeticsBrand": [
                    "Dior迪奥",
                    "丝芙兰SEPHORA"
                ]
            },
            {
                "cosmeticsClass": "眼线笔",
                "cosmeticsBrand": [
                    "植村秀shu uemura"
                ]
            },
            {
                "cosmeticsClass": "眼线膏",
                "cosmeticsBrand": [
                    "Shu Uemura(植村秀)"
                ]
            },
            {
                "cosmeticsClass": "睫毛膏",
                "cosmeticsBrand": [
                    "兰蔻",
                    "魅可"
                ]
            },
            {
                "cosmeticsClass": "腮红",
                "cosmeticsBrand": [
                    "Shu Uemura植村秀"
                ]
            },
            {
                "cosmeticsClass": "眉笔",
                "cosmeticsBrand": [
                    "Bobbi Brown（芭比波朗）"
                ]
            },
            {
                "cosmeticsClass": "眉粉",
                "cosmeticsBrand": [
                    "NARS"
                ]
            },
            {
                "cosmeticsClass": "高光粉",
                "cosmeticsBrand": [
                    "make up for ever"
                ]
            },
            {
                "cosmeticsClass": "阴影粉",
                "cosmeticsBrand": [
                    "make up for ever"
                ]
            },
            {
                "cosmeticsClass": "口红",
                "cosmeticsBrand": [
                    "M.A.C（魅可）"
                ]
            },
            {
                "cosmeticsClass": "唇彩",
                "cosmeticsBrand": [
                    "M.A.C（魅可）"
                ]
            }
        ],
        "tags": [
            "欧美风",
            "气场女王",
            "烟熏妆"
        ],
        "publishTime": 1439377048000,
        "praiseStatus": 0,
        "collectStatus": 0,
        "dresserId": 58,
        "dresserName": "薛云梦（海威）",
        "dresserProfile": "http://nggirl-product-res.oss-cn-beijing.aliyuncs.com/work/97161288e0b342848210acd806721896.jpg",
        "starLevel": 4,
        "authentication": 0,
        "isVDresser": 0,
        "loverCount": 3,
        "lovers": [
            {
                "loverUserId": 193,
                "loverName": "郭宏斌",
                "loverProfile": "http://testphotosd.nggirl.com.cn/work/80cd838a02d7407195594c90856ea1a3.jpg"
            },
            {
                "loverUserId": 116,
                "loverName": "ZZzzzz",
                "loverProfile": "http://testphotosd.nggirl.com.cn/work/98b09cbc00804529a408c3e5fd061fd7.jpg"
            }
        ],
        "evaluationCount": 4,
        "evaluations": [
            {
                "evaluateUserId": 193,
                "evaluateName": "郭宏斌",
                "evaluateProfile": "http://testphotosd.nggirl.com.cn/work/80cd838a02d7407195594c90856ea1a3.jpg",
                "evaluation": "评论",
                "evaluateTime": 1443528371000
            },
            {
                "evaluateUserId": 116,
                "evaluateName": "ZZzzzz",
                "evaluateProfile": "http://testphotosd.nggirl.com.cn/work/98b09cbc00804529a408c3e5fd061fd7.jpg",
                "evaluation": "凡哥",
                "evaluateTime": 1441005585000
            },
            {
                "evaluateUserId": 116,
                "evaluateName": "ZZzzzz",
                "evaluateProfile": "http://testphotosd.nggirl.com.cn/work/98b09cbc00804529a408c3e5fd061fd7.jpg",
                "evaluation": "微博功能应该",
                "evaluateTime": 1440845903000
            },
            {
                "evaluateUserId": 116,
                "evaluateName": "ZZzzzz",
                "evaluateProfile": "http://testphotosd.nggirl.com.cn/work/98b09cbc00804529a408c3e5fd061fd7.jpg",
                "evaluation": "必要的交流是可以的",
                "evaluateTime": 1440845890000
            }
        ],
        "recommends": [
            {
                "workId": 229,
                "cover": "http://photosd.nggirl.com.cn/work/7f179d5cda094da89bcae0f6a79b695b.jpg",
                "praiseNum": 4,
                "praised": 1,
                "dresserId": 60,
                "hasDiscount":1,
                "discount":{
                	"id":1,
            		"workId":123,
            		"name":"首单五折",
            		"desc":"新用户首次下单五折优惠，还可叠加使用优惠券",
            		"cost":50,
            		"icon":"http://testphotosd.nggirl.com.cn/work/aee4e7c292094a24a72ac8da401bbd7d.png",
            		"allow":1
                }
            },
            {
                "workId": 365,
                "cover": "http://testphotosd.nggirl.com.cn/work/8a5162c03dcc4e33a2e8249be4f01a13.jpg",
                "praiseNum": 0,
                "praised": 0,
                "dresserId": 60,
                "hasDiscount":1,
                "discount":{
                	"id":1,
            		"workId":123,
            		"name":"首单五折",
            		"desc":"新用户首次下单五折优惠，还可叠加使用优惠券",
            		"cost":50,
            		"icon":"http://testphotosd.nggirl.com.cn/work/aee4e7c292094a24a72ac8da401bbd7d.png",
            		"allow":1
                }
            },
            {
                "workId": 302,
                "cover": "http://testphotosd.nggirl.com.cn/work/0dd5a2b2b3834679a8243b36a50d3a88.jpg",
                "praiseNum": 1,
                "praised": 0,
                "dresserId": 70,
                "hasDiscount":1,
                "discount":{
                	"id":1,
            		"workId":123,
            		"name":"首单五折",
            		"desc":"新用户首次下单五折优惠，还可叠加使用优惠券",
            		"cost":50,
            		"icon":"http://testphotosd.nggirl.com.cn/work/aee4e7c292094a24a72ac8da401bbd7d.png",
            		"allow":1
                }
            }
        ],
        "sex": 0,
        "hasDiscount":1,
        "discount":{
            "id":1,
            "workId":123,
            "name":"首单五折",
            "desc":"新用户首次下单五折优惠，还可叠加使用优惠券",
            "cost":50,
            "icon":"http://testphotosd.nggirl.com.cn/work/aee4e7c292094a24a72ac8da401bbd7d.png",
            "allow":1
            }
    }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - workId	|作品编号
|Data - cover	|封面图片路径
|Data - workType	|作品类型
|Data - cost	|费用
|Data - reservationNum	|预约人数
|Data - timeUsed	|作品耗时，以分钟为单位
|Data - contentPhoto|其他图片的路径列表
|Data - descriptions|作品描述
|Data - cosmetics|使用的化妆品信息
|Data –cosmetics - cosmeticsClass	|化妆品品类
|Data –cosmetics - cosmeticsBrand|化妆品品牌列表
|Data - tags|作品标签列表
|Data - publishTime|时间， 13位数字，代表自January 1, 1970 00:00:00 GMT开始到现在经历的毫秒数
|Data - praiseStatus | 点赞状态，0未点赞，1为点赞
|Data - collectStatus | 收藏状态，0未收藏，1已收藏
|Data - dresserId | 化妆师编号
|Data - dresserName|化妆师名称
|Data - dresserProfile|头像文件路径
|Data - starLevel|星级
|Data - authentication|是否已经认证，0未认证，1已认证
|Data - isVDresser|是否为加V化妆师，0为否，1为是
|Data - loverCount|喜欢的人数
|Data - lovers|喜欢的人列表
|Data - lovers- loverUserId |用户编号
|Data - lovers- loverName|用户名
|Data - lovers - loverProfile|用户头像
|Data - sex|化妆师性别
|Data - evaluationCount|评论数
|Data - evaluations-evaluateUserId|评论用户编号
|Data - evaluations-evaluateName|评论用户名
|Data - evaluations- evaluateProfile|用户头像
|Data - evaluations- evaluation|评论内容
|Data - evaluations- evaluateTime|评论时间
|Data - recommends|推荐作品列表
|Data - recommends-workId|workId
|Data - recommends- cover|封面
|Data - recommends-praiseNum|点赞数
|Data - recommends-praised|用户是否点赞
|Data - recommends-dresserId|化妆师id
|Data - hasDiscount|此作品是否参与了活动，0没有，1有
|Data - discount - id|活动编号
|Data - discount - workId|参与活动的作品编号
|Data - discount - name|活动名称，显示在作品的活动栏（红底部分）
|Data - discount - desc|活动描述，显示在作品的活动栏
|Data - discount - cost|参与活动后的价格
|Data - discount - icon|活动的图标，用于放在作品的图片右上角
|Data - discount - allow|该用户是否可享受折扣,0不可以，1可以

<h2 id="5">5.获取评论总数</h2>

请求方法：nggirl/app/cli/works/getEvaluationCount

请求URL：接口地址/nggirl/app/cli/works/getEvaluationCount

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义
|---|---
|accessToken|用户授权令牌
|workId|作品编号

请求示例：

> http://localhost/nggirl/app/cli/works/getEvaluationCount?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&workId=1234567

返回结果示例：

```json
{
"code": 0,
"data": {
	"count":10
	},
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - code	|评价总数

<h2 id="6">6.获取作品评价v1.2</h2>

请求方法：nggirl/app/cli/works/listWorkEvaluation/1.2

请求URL：接口地址/nggirl/app/cli/works/listWorkEvaluation/1.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|workId|作品编号
|page|页数 非必须参数，默认第一页
|num|每页信息数目，非必须参数，默认20

请求示例：

> http://localhost/nggirl/app/cli/works/listWorkEvaluation/1.2?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&workId=1234567&page=0&num=20

返回结果示例：

```json
{
    "code":0
    "data":{
        "hasMore":0,
         "evaluateList":[{
                    "evaluateUserId":1,
                    "evaluateName": "王明",
                    "evaluateProfile":"http://www.baidu.com/1.jpg",
                    "evaluation":"非常喜欢，想来一个",
                    "evaluateTime": 1435196075742
                },
                {
                    "evaluateUserId":1,
                    "evaluateName": "王明",
                    "evaluateProfile":"http://www.baidu.com/1.jpg",
                    "evaluation":"非常喜欢，想来一个",
                    "evaluateTime": 1435196075742
                 }
           ]
     }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确,1表示用户未注册
|hasMore	|是否还有更多的数据，0没有，1有
|Data - evaluateList - evaluateUserId	|用户编号
|Data - evaluateList - evaluateName|用户名
|Data - evaluateList - evaluateProfile|头像路径
|Data - evaluateList - evaluation|评价内容
|Data - evaluateList - evaluateTime|评论时间

<h2 id="7">7.获取喜欢的人总数</h2>

请求方法：nggirl/app/cli/works/getLoverCount

请求URL：接口地址/nggirl/app/cli/works/getLoverCount

支持格式：JSON

HTTP请求方式：POST
应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|workId	|作品编号

请求示例：

> http://localhost/nggirl/app/cli/works/getLoverCount?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&workId=1234567

返回结果示例：

```json
{
   "code": 0,
   "data": {
	"count":2
	},
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - count|喜欢的人总数

<h2 id="8">8.获取喜欢的人</h2>

请求方法：nggirl/app/cli/works/listWorkLover

请求URL：接口地址/nggirl/app/cli/works/listWorkLover

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|workId|作品编号
|page|页数 非必须参数，默认第一页
|num|每页信息数目，非必须参数，默认20

请求示例：

> http://localhost/nggirl/app/cli/works/listWorkLover?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&workId=1234567&page=0&num=20

返回结果示例：

```json
{
 "code":0,
 "data": [{
		"loverUserId":1,
		"loverName": "王明",
		"loverProfile":" http://www.baidu.com/1.jpg"
	},
	{
		"loverUserId":1,
		"loverName": "丽丽",
		"loverProfile":" http://www.baidu.com/1.jpg"
       }]
}
```
返回字段说明

|参数名称|参数含义
|---|---
|Code|错误码，0表示正确
|Data - loverUserId|用户编号
|Data - loverName|用户名
|Data - loverProfile|头像路径

<h2 id="9">9.作品推荐v1.2</h2>

请求方法：nggirl/app/cli/works/listRecommandWorks/1.2

请求URL：接口地址/nggirl/app/cli/works/listRecommandWorks/1.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|workId	|作品编号


请求示例：

> http://localhost/nggirl/app/cli/works/listRecommandWorks/1.2?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&workId=123456

返回结果示例：

```json
{
    "code": 0,
    "data": [{
		"workId": 1234567,
		"cover":" http://www.baidu.com/1.jpg",
		"praiseNum":12,
        	"praised":0,
        	"dresserId": 60,
        	"hasDiscount":1,
                "discount":{
                	"id":1,
            		"workId":123,
            		"name":"首单五折",
            		"desc":"新用户首次下单五折优惠，还可叠加使用优惠券",
            		"cost":50,
            		"icon":"http://testphotosd.nggirl.com.cn/work/aee4e7c292094a24a72ac8da401bbd7d.png",
            		"allow":1
                }
	},{
		"workId": 1234567,
		"cover":" http://www.baidu.com/1.jpg",
		"praiseNum":12,
        	"praised":0,
        	"dresserId": 60,
        	"hasDiscount":1,
                "discount":{
                	"id":1,
            		"workId":123,
            		"name":"首单五折",
            		"desc":"新用户首次下单五折优惠，还可叠加使用优惠券",
            		"cost":50,
            		"icon":"http://testphotosd.nggirl.com.cn/work/aee4e7c292094a24a72ac8da401bbd7d.png",
            		"allow":1
                }
	},
	{
		"workId": 1234567,
		"cover":" http://www.baidu.com/1.jpg",
		"praiseNum":12,
        	"praised":0,
        	"dresserId": 60,
        	"hasDiscount":1,
                "discount":{
                	"id":1,
            		"workId":123,
            		"name":"首单五折",
            		"desc":"新用户首次下单五折优惠，还可叠加使用优惠券",
            		"cost":50,
            		"icon":"http://testphotosd.nggirl.com.cn/work/aee4e7c292094a24a72ac8da401bbd7d.png",
            		"allow":1
                }
       }]
}

```
返回字段说明

|参数名称|参数含义
|---|---
|Code|错误码，0表示正确
|Data - workId|作品编号
|Data - cover|封面图片路径
|Data - praiseNum|点赞人数
|Data - praised|用户是否点赞
|Data - dresserId|化妆师id
|Data - hasDiscount|此作品是否参与了活动，0没有，1有
|Data - discount - id|活动编号
|Data - discount - workId|参与活动的作品编号
|Data - discount - name|活动名称，显示在作品的活动栏（红底部分）
|Data - discount - desc|活动描述，显示在作品的活动栏
|Data - discount - cost|参与活动后的价格
|Data - discount - icon|活动的图标，用于放在作品的图片右上角
|Data - discount - allow|该用户是否可享受折扣,0不可以，1可以


<h2 id="10">10.收藏作品</h2>

请求方法：nggirl/app/cli/ works /collectWork

请求URL：接口地址/nggirl/app/cli/ works /collectWork

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|workId	|作品编号


请求示例：

> http://localhost/nggirl/app/cli/works/collectWork?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0& workId=1234567

返回结果示例：

```json
{
    "code": 0
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确


<h2 id="11">11.取消收藏</h2>

请求方法：nggirl/app/cli/ works /cancelCollectWork

请求URL：接口地址/nggirl/app/cli/ works /cancelCollectWork

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|workId|作品编号

请求示例：

> http://localhost/nggirl/app/cli/works/cancelCollectWork?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0& workId=1234567

返回结果示例：

```json
{
    "code": 0
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确

<h2 id="12">12.作品点赞</h2>

请求方法：nggirl/app/cli/works/praiseWork

请求URL：接口地址/nggirl/app/cli/works/praiseWork

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|workId	|作品编号


请求示例：

> http://localhost/nggirl/app/cli/works/praiseWork?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&workId=1234567

返回结果示例：

```json
{
    "code": 0
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确

<h2 id="13">13.取消点赞</h2>

请求方法：nggirl/app/cli/works/cancelPraiseWork

请求URL：接口地址/nggirl/app/cli/works/cancelPraiseWork

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|workId|作品编号

请求示例：

> http://localhost/nggirl/app/cli/works/cancelPraiseWork?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&workId=1234567

返回结果示例：

```json
{
    "code": 0
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确



<h2 id="14" >14. 可预约时间段</h2>

请求方法：nggirl/app/cli/ works /getReservationTimes

请求URL：接口地址/nggirl/app/cli/works/getReservationTimes

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|dresserId|化妆师编号


请求示例：

> http://localhost/nggirl/app/app/cli/works/getReservationTimes?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&workId=10000

返回结果示例：

```json
{
   "code": 0,
   "data": [{
    "date": "今天",
    "times":[{
        "name":"9:00 - 12:00",
        "status":"0"
       },{
        "name":"12:00 - 14:00",
        "status":"0"
        },{
        "name":"14:00 - 16:00",
        "status":"0"
      },{
        "name":"16:00 - 20:00",
        "status":"0"
    }]
    },{
     "date": "明天",
     "times":[{
     "name":"9:00 - 12:00",
     "status":"0"
    },{
        "name":"12:00 - 14:00",
        "status":"0"
    },{
        "name":"14:00 - 16:00",
        "status":"0"
    },{
        "name":"16:00 - 20:00",
        "status":"0"
    }]
    },{
      "date": "后天",
      "times":[{
        "name":"9:00 - 12:00",
        "status":"0"
    },{
        "name":"12:00 - 14:00",
        "status":"0"
    },{
        "name":"14:00 - 16:00",
        "status":"0"
    },{
        "name":"16:00 - 20:00",
        "status":"0"
        }]
    }]
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - date	|日期
|Data - times	|时段
|Data - times-name|时段名
|Data - times-status|时段状态，0是未预约，1是已预约




<h2 id="15">15.我要预约V1.2</h2>

请求方法：nggirl/app/cli/works/getReservation/1.2

请求URL：接口地址/nggirl/app/cli/works/getReservation/1.2

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|workId	|作品id
|PeservationTime|预约的时间
|reservationAddress|预约地址
|phoneNum	|预约电话号码

请求示例：

> http://localhost/nggirl/app/app/cli/works/getReservation/1.2?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&dresserId=10000&reservationTime=2015
年6月8日15:30-16:00&reservationAddress=北京朝阳区&phoneNum=010888888

返回结果示例：

```json
{
     "code": 0,
     "data": {
        "reservationId": 12345678
         }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - reservationId|预约单号


<h2 id="16">16. 我的预约</h2>

请求方法：nggirl/app/cli/works/listReservation

请求URL：接口地址/nggirl/app/cli/works/listReservation

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|page|页数 ，非必须参数，默认第一页
|num|每页信息数目，非必须参数，默认20

请求示例：

> http://localhost/nggirl/app/app/cli/works/listReservation?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&page=0&num=20

返回结果示例：

```json
{
   "code": 0,
   "data":[ {
		"reservationId":12345,
        "dresserId": 41000,
        "profile": "http://www.baidu.com/2.jpg",
        "name": "王子涵",
        "starLevel": 5,
        "authentication":1,
        "workType": "职业装",
        "cost": 100,
        "status": 0,
        "lastUpdateTime":1435196075742,
        "systemTime":1435196075742
    },{
        "reservationId":12345,
        "dresserId": 41000,
        "profile": "http://www.baidu.com/2.jpg",
        "name": "王子涵",
        "starLevel": 5,
        "authentication":1,
        "workType": "职业装",
        "cost": 100,
        "status": 0,
        "lastUpdateTime":1435196075742,
        "systemTime":1435196075742
    },{
        "reservationId":12345,
        "dresserId": 41000,
        "profile": "http://www.baidu.com/2.jpg",
        "name": "王子涵",
        "starLevel": 5,
        "authentication":1,
        "workType": "职业装",
        "cost": 100,
        "status": 0,
        "lastUpdateTime":1435196075742,
        "systemTime":1435196075742
    }]
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - reservationId	|预约单编号
|Data - dresserId	|化妆师编号
|Data - profile	|头像照片路径
|Data - cost	|费用
|Data - name	|化妆师姓名
|Data - starLevel	|化妆师星级
|Data - authentication|化妆师是否认证
|Data - workType|装束类型
|Data – cost	|费用
|Data – status|预约状态，0新预约（等待化妆师确认），1已取消，2已结算，3（化妆师）已接收（等待支付），4（化妆师）已拒绝，5已完成
|Data - lastUpdateTime|最后修改时间，如果status为已接收时，此值为接单时间；如果status为已支付时，此值为支付时间。
|Data - systemTime | 系统当期时间


<h2 id="17">17.取消预约</h2>

请求方法：nggirl/app/cli/ works /cancelReservation

请求URL：接口地址/nggirl/app/cli/works/cancelReservation

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|[必填]用户授权令牌
|reservationId	|[必填]预约编号
|reason	|[选填]取消原因

>reason取消原因字段，是在1.4.1版本新添加的，在当前版本中可以为空

请求示例：

> http://localhost/nggirl/app/app/cli/works/cancelReservation?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&reservationId=10000

返回结果示例：

```json
{
   "code": 0
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确


<h2 id="18">18. 支付</h2>

请求方法：nggirl/app/cli/works/payReservation

请求URL：接口地址/nggirl/app/cli/works/payReservation

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义
|---|---
|accessToken|用户授权令牌
|reservationId|预约编号
|couponId|优惠券编号[可选]
|payType|支付类型，1微信支付，2支付宝支付

请求示例：

> http://localhost/nggirl/app/cli/works/payReservation?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&reservationId=1&cuponId=1&payType=1

返回结果示例：

```json
{
"data": {
        "order_no": "2015080715191800006",
        "total_fee": 0.02,
        "left_fee": 0.01,
        "order_status": 1,
        "weixin_prepay_id": "wx20150807151928305dde4e400559257714",
        "weixin_appid": "wxfe8754d4e19d9c85",
        "weixin_partnerid": "1259003701",
        "weixin_package": "Sign=WXPay",
        "weixin_noncestr": "636138788e564044b7c2b63b1cec0aea",
        "weixin_timestamp": "1438931958",
        "weixin_sign": "D9F92DC0B05AA670A71B6E15F2FEBD54",
        "product": "化妆师张树凡作品，约会妆",
        "product_detail": "南瓜姑娘美妆服务，化妆师张树凡作品，约会妆"
    },
    "code": 0
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - order_no	|本系统的支付编号
|Data - total_fee|本订单总金额
|Data - left_fee|本订单剩余需支付的金额
|Data - order_status|本订单的支付状态，1未支付，2已支付
|Data - weixin_prepay_id|微信的预支付id
|Data - weixin_appid|微信分配的公众账号ID
|Data - weixin_partnerid|微信的预支付id
|Data - weixin_package|暂填写固定值Sign=WXPay
|Data -  weixin_noncestr|随机字符串，不长于32位
|Data -  weixin_timestamp|时间戳
|Data - weixin_sign|签名
|Data - product|商品名称，最长为128个汉字
|Data - product_detail|商品详情，最长为512个汉字


<h2 id="19">19. 删除支付记录（支付失败时调用）</h2>


请求方法：nggirl/app/cli/works/deletePayRecord

请求URL：接口地址/nggirl/app/cli/works/deletePayRecord

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|reservationId	|预约编号

请求示例：

> http://localhost/nggirl/app/cli/works/payReservation?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&reservationId=1

返回结果示例：

```json
{
    "code":0
    "data":null
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确




<h2 id="20">20.退款</h2>

请求方法：nggirl/app/cli/works/withdrawReservation

请求URL：接口地址/nggirl/app/cli/works/withdrawReservation

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|reservationId	|预约编号

请求示例：

> http://localhost/nggirl/app/app/cli/works/withdrawReservation?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&reservationId=10000

返回结果示例：

```json
{
  "code": 0,
  "data":{
	"hint":"预约费用将在7-10个工作日退回到原账户，请注意查收"
    }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - hint|退款提示（退款已完成，钱款将在1个工作日内到账！）


<h2 id="21">21. 完成预约</h2>

请求方法：nggirl/app/cli/works/finishReservation

请求URL：接口地址/nggirl/app/cli/works/finishReservation

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义
|---|---
|accessToken|用户授权令牌
|reservationId|预约编号

请求示例：

> http://localhost/nggirl/app/cli/works/finishReservation?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&reservationId=10000

返回结果示例：

```json
{
"code": 0,
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确

<h2 id="22">22.预约详情</h2>

请求方法：nggirl/app/cli/works/reservationDetails

请求URL：接口地址/nggirl/app/cli/works/reservationDetails

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|reservationId|预约id

请求示例：

> http://localhost/nggirl/app/cli/works/reservationDetails?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&reservationId=10000

返回结果示例：

```json
{
    "code": 0,
    "data": {
         "dresserId": 41000,
         "profile": "http://www.baidu.com/2.jpg",
         "name": "王子涵",
         "authentication": 1,
         "starLevel": 5,
         "workType": "职业装",
         "cost": 100,
         "reservationTime": "2015年6月8日15:30-16:00",
         "reservationAddress": "北京市朝阳区",
         "lastUpdateTime":1435196075742,
         "systemTime":1435196075742,
         "praised":0
    }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确,1表示用户未注册
|Data - dresserId	|化妆师id
|Data - profile|化妆师头像图片
|Data - name|化妆师姓名
|Data - authentication|化妆师是否认证,0未认证，1已认证
|Data - starLevel|化妆师星级
|Data - workType|化妆师类型名称
|Data - cost|化妆费用
|Data - reservationTime|预约日期
|Data - reservationAddress|预约地址
|Data - lastUpdateTime|最后修改时间，如果status为已接收时，此值为接单时间；如果status为已支付时，此值为支付时间。
|Data - systemTime|系统当前时间
|Data - praised|用户是否已经评价，0为未评价，1为已评价


<h2 id="23">23. 写评价(对化妆师的评论，也可以说对预约单的评论)</h2>

请求方法：nggirl/app/cli/works/evaluate

请求URL：接口地址/nggirl/app/cli/works/evaluate

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|reservationId	|预约的单号
|onTimeEvaluation|准时情况评价（1-5）
|descriptionEvaluation|描述一致情况评价（1-5）
|tecniqueEvaluation|技法娴熟情况评价（1-5）
|serviceEvaluation|服务态度情况评价（1-5）
|evaluation|评价的内容
|photos|图片的集合，为图片上传后返回的路径组成的json数组。示例：["url","url","url"]

请求示例：

> http://localhost/nggirl/app/cli/works/evaluate?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&reservationId=10000&onTimeEvaluation=5&descriptionEvaluation=5&tecniqueEvaluation=5&serviceEvaluation=5&evaluation=41545good

返回结果示例：

```json
{
   "code": 0
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确

<h2 id="24">24. 获取评价(对化妆师的评论，也可以说对预约单的评论)</h2>

请求方法：nggirl/app/cli/works/getReservationEvaluate

请求URL：接口地址/nggirl/app/cli/works/getReservationEvaluate

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|reservationId|预约的单号


请求示例：

> http://localhost/nggirl/app/cli/works/getReservationEvaluate?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&reservationId=10000

返回结果示例：

```json
{
 "code": 0,
 "date":{
        "onTimeEvaluation":4,
        "descriptionEvaluation":5,
        "tecniqueEvaluation":5,
        "serviceEvaluation":3,
        "sumEvaluation":4,
        "evaluation":"特别细心，特别用心，见过最好的妆师",
        "evaluationTime":1438247918000,
        "photos":[
            "http://www.nggirl.com.cn",
            "http://www.nggirl.com.cn"
                ]
        }
}
```
返回字段说明

|参数名称|参数含义
|---|---
|Code|错误码，0表示正确
|onTimeEvaluation|准时情况评价（1-5）
|descriptionEvaluation|描述一致情况评价（1-5）
|tecniqueEvaluation|技法娴熟情况评价（1-5）
|serviceEvaluation|服务态度情况评价（1-5）
|evaluation|评价的内容
|evaluationTime|评价时间
|photos|图片的集合，为图片上传后返回的路径组成的json数组。示例：[“url”,”url”,”url”]

<h2 id="25">25. 投诉</h2>

请求方法：nggirl/app/cli/works/createComplaint

请求URL：接口地址/nggirl/app/cli/works/createComplaint

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|reservationId	|预约单编号
|complaintContent|投诉的内容


请求示例：

> http://localhost/nggirl/app/cli/works/createComplaint?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&reservationId=10000&complaintContent=41545bad

返回结果示例：

```json
{
    "code": 0
}

```
返回字段说明

|参数名称|参数含义
|---|---
|Code|错误码，0表示正确

<h2 id="26">26.获取作品的用户晒单v1.2</h2>

请求方法：nggirl/app/cli/works/getWorkEvaluateList/1.2

请求URL：接口地址/nggirl/app/cli/works/getWorkEvaluateList/1.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|workId	|作品编号
|page	|页数。非必需参数，默认第一页
|num	|每页信息数目。非必须参数，默认20

请求示例：

> http://localhost/nggirl/app/cli/works/getWorkEvaluateList/1.2?app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=0c0cf4990aa72f3a75b961c21bab61d51f682f68&workId=316&page=1&num=3

返回结果示例：

```json
{
    "code": 0,
    "data": {
    	"hasMore":0,
        "evaluateList":[
                {
                "evaluationId": 341,
                "userName": "美丽",
                "profile": "http://photosd.nggirl.com.cn/work/f40b2e3d9b3c4bbb8641e0d46732450f.png",
                "workType": null,
                "evaluation": "不错",
                "startLevel": 2,
                "datetime": 1446172381000,
                "photos": [
                        "http://testphotosd.nggirl.com.cn/work/33ee636fd2854dac8bcc344626564315.jpg",
                        "http://testphotosd.nggirl.com.cn/work/ca46c24f0dbc4ce48c1d8f2c427c50cc.jpg"
                        ]
                }
        ]
   	}
}
```

返回字段说明：

|字段名称|字段含义
|---|---
|Code	|错误码，0表示正确
|hasMore	|是否还有更多数据，0没有，1有
|Data - evaluateList - userName	|用户名
|Data - evaluateList - profile	|用户头像路径
|Data- evaluateList - reservationType	|预约类型名称
|Data - evaluateList - evaluation	|评价内容
|Data - evaluateList - startLevel	|星级
|Data - evaluateList - datetime	|时间。13位数字，代表自January 1, 1970 00:00:00 GMT开始到现在经历的毫秒数
|Datat - evaluateList - photos	|照片列表

<h2 id="27">27.获取活动对应作品列表v1.2</h2>

请求方法：nggirl/app/cli/works/getPromotionWorks/1.2

请求URL：接口地址/nggirl/app/cli/works/getPromotionWorks/1.2

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|promotionName   |活动名称
|page	|页数  非必需参数，默认第一页
|num	|每页信息数目 非必需参数，默认20

请求示例：

> http://localhost/nggirl/app/cli/works/getPromotionWorks/1.2?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&promotionName=首单五折&page=0&num=20

返回结果示例：

```json
{
    "code": 0
    "data":[{
	"workId": 1234567,
	"cover":"http://www.baidu.com/1.jpg",
	"workType":"职业装",
	"cost":100,
	"praiseNum":12,
	"dresserId":1234567,
	"dresserName":"于子涵",
	"dresserProfile":"http://www.baidu.com/1.jpg",
	"descriptions":"肤质较佳的女生。强调重点：强调眼唇重点。以润色隔离霜作为底妆，然后以睫毛膏……",
	"praiseStatus":1,
	"isVDresser":1,
	"tags": [
                "欧美风",
                "英伦",
                "朋克"
            ],
    "hasDiscount":1,
    "discount":{
        "id":1,
        "workId":123,
    	"name":"首单五折",
        "desc":"新用户首次下单五折优惠，还可叠加使用优惠券",
        "cost":50,
        "icon":"http://testphotosd.nggirl.com.cn/work/aee4e7c292094a24a72ac8da401bbd7d.png"
    	}
	},
	{
	"workId": 1234567,
	"cover":"http://www.baidu.com/1.jpg",
	"workType":"职业装",
	"cost":100,
	"praiseNum":12,
	"dresserId":1234567,
	"dresserName":"于子涵",
	"dresserProfile":"http://www.baidu.com/1.jpg",
	"descriptions":"肤质较佳的女生。强调重点：强调眼唇重点。以润色隔离霜作为底妆，然后以睫毛膏…….",
	"praiseStatus":1,
	"isVDresser":0,
	"tags": [
                "欧美风",
                "英伦",
                "朋克"
            ],
     "hasDiscount":0,
    "discount":{
        "id":"",
        "workId":"",
    	"name":"",
        "desc":"",
        "cost":,
        "icon":""
    	}
       }]
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - workId	|作品编号
|Data - cover	|封面图片路径
|Data - workType|作品类型
|Data - cost	|费用
|Data - praiseNum|点赞人数
|Data - dresserId|化妆师编号
|Data - dresserName|化妆师姓名
|Data - dresserProfile|化妆师头像
|Data - descriptions|作品描述
|Data - praiseStatus|点赞状态，0为未点赞，1为已点赞
|Data - isVDresser|是否为加V化妆师，0为否，1为是
|Data - tags|作品标签
|Data - hasDiscount|此作品是否参与了活动，0没有，1有
|Data - discount - id|活动编号
|Data - discount - workId|参与活动的作品编号
|Data - discount - name|活动名称，显示在作品的活动栏（红底部分）
|Data - discount - desc|活动描述，显示在作品的活动栏
|Data - discount - cost|参与活动后的价格
|Data - discount - icon|活动的图标，用于放在作品的图片右上角


<h2 id="28">28.退款操作通知</h2>

> 用户点击确认退款，会向后台运营人员发送通知

请求方法：nggirl/app/cli/works/refundOperationNotify

请求URL：接口地址/nggirl/app/cli/works/refundOperationNotify

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken | [必填]授权令牌
|reservationId | [必填]预约编号
|reason	|[选填]取消原因

>reason退款原因字段，是在1.4.1版本新添加的，在当前版本中可以为空

请求示例：

> http://localhost/nggirl/app/cli/works/refundOperationNotify?accessToken=ACCESSTOKEN&reservationId=12323343

返回结果示例：

```json
{
	"code":0,
	"data":null
}
```

返回字段说明：

|字段名称|字段含义|
|---|---|
|Code |错误码，0表示正确
|Data |返回数据，null表示无返回数据
