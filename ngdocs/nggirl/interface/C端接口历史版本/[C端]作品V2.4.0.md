<h1>作品V2.0.0</h1>

目录

* [1.获取轮播头图列表V2.4.0](#1)
* [2.焦点图历史列表V2.4.0](#2)
* [3.获取所有作品列表v1.2](#3)
* [4.获取作品详情(和化妆师端不同)v1.5.0](#4)
* [5.获取作品详情(一次获取所有信息)v1.5.0](#5)
* [6.获取评价总数](#6)
* [7.获取作品评论v1.2](#7)
* [8.获取喜欢的人总数](#8)
* [9.获取喜欢的人](#9)
* [10.作品推荐v1.5.0](#10)
* [11.收藏作品](#11)
* [12.取消收藏](#12)
* [13.作品点赞](#13)
* [14.取消点赞](#14)
* [15.获取某月预约时间段V1.4.2](#15)
* [16.我要预约V1.5.0](#16)
* [17.我的预约V1.4.2](#17)
* [17.5. 获取订单中进行中和待评价数目V1.4.2](#17.5)
* [18.取消预约(可预约时间改为30天)V1.4.2](#18)
* [19.支付](#19)
* [20.删除支付记录（支付失败时调用）](#20)
* [21.退款](#21)
* [22.完成预约](#22)
* [23.预约详情V1.4.2](#23)
* [24.写评价(对化妆师的评论，也可以说对预约单的评论)V1.5.0](#24)
* [25.获取评价(对化妆师的评论，也可以说对预约单的评论)](#25)
* [26.投诉](#26)
* [27.获取作品的用户晒单v1.2](#27)
* [28.获取活动对应的作品列表v1.2](#28)
* [29.退款操作通知V1.4.2](#29)
* [30.预约详情IOSV1.0(补充接口)](#30)
* [31.预约流程IOSV1.4.2](#31)
* [32.预约详情IOSV1.4.2](#32)
* [33.支付宝web支付(遗漏接口)](#33)
* [34.关于我（关于化妆师）1.5.0](#34)


<h2 id="1">1.获取轮播头图列表V2.4.0</h2>

>出参添加forwardtype和forwardkey字段

请求方法：nggirl/app/cli/works/listHeadScroll/2.4.0

请求URL：接口地址/nggirl/app/cli/works/listHeadScroll/2.4.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌


请求示例：

> http://localhost/nggirl/app/cli/works/listHeadScroll/2.4.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0

返回结果示例：

```json
{
   "code": 0,
    "data":[
      {
  	  "photoUrl": " http://www.baidu.com/1.jpg",
  		"webpageUrl":"http://www.nggirl.com.cn",
  		"shareContent":"cosm大赏，美美的彩妆品",
  		"shareImage":"http://www.baidu.com/2.jpg",
      "forwardtype":"coupon",
      "forwardkey":""
    	},
    	{
  		"photoUrl": " http://www.baidu.com/1.jpg",
  		"webpageUrl":"http://www.nggirl.com.cn",
  		"shareContent":"cosm大赏，美美的彩妆品",
  		"shareImage":"http://www.baidu.com/2.jpg",
      "forwardtype":"coupon",
      "forwardkey":""
       }
   ]
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - photoUrl	|显示的图片路径
|Data - webpageUrl	|跳转到的web页面链接地址
|Data - shareContent |分享描述内容
|Data - shareImage	|分享出去的小图（1:1小图片），替代之前的logo
|Data - forwardtype	|跳转类型
|Data - forwardkey	|跳转参数

<h2 id="2">2.焦点图历史列表V2.4.0</h2>

>出参添加forwardtype和forwardkey字段

请求方法：nggirl/app/cli/works/headScrollHistory/2.4.0

请求URL：接口地址/nggirl/app/cli/works/headScrollHistory/2.4.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|page	|页数  非必需参数，默认第一页
|num	|每页信息数目 非必需参数，默认20


请求示例：

> http://localhost/nggirl/app/cli/works/headScrollHistory/2.4.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：

```json
{
   "code": 0,
    "data":{
        "hasMore":1,
        "list":[{
	            "photoUrl": " http://www.baidu.com/1.jpg",
		          "webpageUrl":"http://www.nggirl.com.cn",
		          "shareContent":"cosm大赏，美美的彩妆品",
		          "shareImage":"http://www.baidu.com/2.jpg",
              "forwardtype":"coupon",
              "forwardkey":""
	       },
	       {
		          "photoUrl": " http://www.baidu.com/1.jpg",
		          "webpageUrl":"http://www.nggirl.com.cn",
		          "shareContent":"cosm大赏，美美的彩妆品",
		          "shareImage":"http://www.baidu.com/2.jpg",
              "forwardtype":"atorder",
              "forwardkey":""
        }]
    }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - photoUrl	|显示的图片路径
|Data - webpageUrl	|跳转到的web页面链接地址
|Data - shareContent |分享描述内容
|Data - shareImage	|分享出去的小图（1:1小图片），替代之前的logo
|Data - forwardtype	|跳转类型
|Data - forwardkey	|跳转参数


<h2 id="3">3.获取所有作品列表v1.2</h2>

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
    "code": 0,
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




<h2 id="4">4.获取作品详情(和化妆师不同)v1.5.0</h2>

> 返回字段增加specials，serviceYear，orderNum,bizArea,cityId字段

请求方法：nggirl/app/cli/works/getWorksDetail/1.5.0

请求URL：接口地址/nggirl/app/cli/works/getWorksDetail/1.5.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|workId	|作品编号

请求示例：

> http://localhost/nggirl/app/cli/works/getWorksDetail/1.5.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&workId=123456

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "workId": 211,
        "cover": "http://photosd.nggirl.com.cn/work/bb57050e9c4f454c91c30986210ecf25.jpg",
        "workType": "约会妆",
        "workName":"时尚淡雅",
        "cost": 1,
        "reservationNum": 15,
        "timeUsed": 1204,
        "contentPhoto": [],
        "descriptions": "适合逛街、约会、宴会等。 妆面特点：妆容相对生活妆稍浓，发型多变， 发型简约。服务内容：妆面，简约发型。 ",
        "bizArea":"三里屯、国贸、天安门、西单",
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
        "cityId":1,
        "specials":"专注古装,明星通告,手推波纹",
        "serviceYear":10,
        "orderNum":100,
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
|Data - workName|作品名称
|Data - cost	|费用
|Data - reservationNum	|预约人数
|Data - timeUsed	|作品耗时，以分钟为单位
|Data - contentPhoto|其他图片的路径列表
|Data - descriptions|作品描述
|Data - bizArea|化妆师对应商圈（以中文顿号分隔）
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
|Data - cityId|化妆师所在城市
|Data - specials|化妆师特长（英文逗号分隔）
|Data - serviceYear|化妆师从业年限
|Data - orderNum|化妆师接单数
|Data - hasDiscount|此作品是否参与了活动，0没有，1有
|Data - discount - id|活动编号
|Data - discount - workId|参与活动的作品编号
|Data - discount - name|活动名称，显示在作品的活动栏（红底部分）
|Data - discount - desc|活动描述，显示在作品的活动栏
|Data - discount - cost|参与活动后的价格
|Data - discount - icon|活动的图标，用于放在作品的图片右上角
|Data - discount - allow|该用户是否可享受折扣,0不可以，1可以





<h2 id="5">5.获取作品详情（一次获取所有信息）v1.5.0</h2>
> 返回字段增加specials，serviceYear，orderNum,bizArea,cityId字段,去除evaluationCount，evaluations字段，recommends中增加workName，price字段

请求方法：nggirl/app/cli/works/getWorksDetailIos/1.5.0

请求URL：接口地址/nggirl/app/cli/works/getWorksDetailIos/1.5.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|workId	|作品编号

请求示例：

> http://localhost/nggirl/app/cli/works/getWorksDetailIos/1.5.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&workId=123456

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "workId": 211,
        "cover": "http://photosd.nggirl.com.cn/work/bb57050e9c4f454c91c30986210ecf25.jpg",
        "workType": "约会妆",
        "workName":"时尚淡雅",
        "cost": 1,
        "reservationNum": 15,
        "timeUsed": 1204,
        "contentPhoto": [
            "http://photosd.nggirl.com.cn/work/bb57050e9c4f454c91c30986210ecf25.jpg"
        ],
        "descriptions": "适合逛街、约会、宴会等。 妆面特点：妆容相对生活妆稍浓，发型多变， 发型简约。服务内容：妆面，简约发型。 ",
        "bizArea":"三里屯、国贸、天安门、西单",
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
        "cityId":1,
        "specials":"专注古装,明星通告,手推波纹",
        "serviceYear":10,
        "orderNum":100,
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
        "recommends": [
            {
                "workId": 229,
                "cover": "http://photosd.nggirl.com.cn/work/7f179d5cda094da89bcae0f6a79b695b.jpg",
                "workName":"新娘妆",
                "price":100,
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
                "workName":"新娘妆",
                "price":100,
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
                "workName":"新娘妆",
                "price":100,
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
|Data - workName|作品名称
|Data - cost	|费用
|Data - reservationNum	|预约人数
|Data - timeUsed	|作品耗时，以分钟为单位
|Data - contentPhoto|其他图片的路径列表
|Data - descriptions|作品描述
|Data - bizArea|化妆师对应商圈（以中文顿号分隔）
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
|Data - sex|化妆师性别 0男，1女
|Data - cityId|化妆师所在城市
|Data - specials|化妆师特长（英文逗号分隔）
|Data - serviceYear|化妆师从业年限
|Data - orderNum|化妆师接单数
|Data - recommends|推荐作品列表
|Data - recommends - workId|作品编号
|Data - recommends - cover|封面
|Data - recommends - workName|装束类型
|Data - recommends - price|作品价格|
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

<h2 id="6">6.获取评论总数</h2>

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

<h2 id="7">7.获取作品评价v1.2</h2>

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
    "code":0,
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

<h2 id="8">8.获取喜欢的人总数</h2>

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

<h2 id="9">9.获取喜欢的人</h2>

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

<h2 id="10">10.作品推荐v1.5.0</h2>
> 返回字段增加workName,price字段

请求方法：nggirl/app/cli/works/listRecommandWorks/1.5.0

请求URL：接口地址/nggirl/app/cli/works/listRecommandWorks/1.5.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|workId	|作品编号


请求示例：

> http://localhost/nggirl/app/cli/works/listRecommandWorks/1.5.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&workId=123456

返回结果示例：

```json
{
    "code": 0,
    "data": [{
		"workId": 1234567,
		"cover":" http://www.baidu.com/1.jpg",
		"workName":"约会妆",
		"price":100,
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
		"workName":"约会妆",
		"price":100,
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
		"workName":"约会妆",
		"price":100,
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
|Data - workName|装束类型
|Data - price|作品价格|
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


<h2 id="11">11.收藏作品</h2>

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


<h2 id="12">12.取消收藏</h2>

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

<h2 id="13">13.作品点赞</h2>

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

<h2 id="14">14.取消点赞</h2>

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
    "code": 0,
    "data":null
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确



<h2 id="15">15. 获取某月预约时间段</h2>

> 预约时间由可预约1个月改为6个月，此接口返回传入年月所有可预约时间段，若为当月，返回当月余下所有可预约时间段。
>原接口为获取30天可预约时间段

请求方法：nggirl/app/cli/works/getReservationTimes/1.4.2

请求URL：接口地址/nggirl/app/cli/works/getReservationTimes/1.4.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|dresserId|所预约化妆师id
|month|年月,数字（1-6）1表示本月，2表示下个月，6表示第6个月

请求示例：

> http://localhost/nggirl/app/bus/schedule/listResTimeByMonth/1.4.2?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&dresserId=58&month=1

返回结果示例：

```json
{
   "code": 0,
   "data":
   {
    "monthStatus":-1,
    "reservationDates": [
            {
                "realDate": "20160328",
                "reservationDate": "03.28 周一",
                "reservationTimes": [
                    {
                        "name": "17:00 - 17:20",
                        "status": 1
                    },
                    {
                        "name": "17:20 - 17:40",
                        "status": 1
                    },
                    {
                        "name": "20:40 - 21:00",
                        "status": 1
                    },
                    {
                        "name": "21:00 - 21:20",
                        "status": 1
                    },
                    {
                        "name": "21:20 - 21:40",
                        "status": 1
                    },
                    {
                        "name": "21:40 - 22:00",
                        "status": 1
                    },
                ]
            },
            {
                "realDate": "20160329",
                "reservationDate": "03.29 周二",
                "reservationTimes": [
                    {
                        "name": "06:00 - 06:20",
                        "status": 1
                    },
                    {
                        "name": "06:20 - 06:40",
                        "status": 1
                    },
                    {
                        "name": "14:40 - 15:00",
                        "status": 1
                    },
                    {
                        "name": "15:00 - 15:20",
                        "status": 1
                    },
                    {
                        "name": "16:40 - 17:00",
                        "status": 1
                    },
                    {
                        "name": "17:00 - 17:20",
                        "status": 1
                    }
                ]
            }
         ]
       }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - monthStatus|请求月份状态，-1表示当月，0表示中间月，1表示最后一月
|Data -reservationDates- reservationDate	|预约日期 （用于显示在移动端的）
|Data -reservationDates- reservationTimes	|时段
|Data -reservationDates- realDate | 所代表的真实日期 “20160121” 标准八位字符串（用于传给后台的，方便处理）
|Data -reservationDates- reservationTimes-name|时段名
|Data -reservationDates- reservationTimes-status|时段状态，0未预约，1已预约或不可预约



<h2 id="16">16.我要预约V1.5.0</h2>
> 地址编号addressId

请求方法：nggirl/app/cli/works/getReservation/1.5.0

请求URL：接口地址/nggirl/app/cli/works/getReservation/1.5.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|workId	|作品id
|reservationDate|预约日期（"20160121" 标准八位字符串）
|reservationTime|预约时间段（"18:00 - 18:20"）
|addressId|地址编号|
|reservationAddress|预约地址
|phoneNum	|预约电话号码

请求示例：

> http://localhost/nggirl/app/app/cli/works/getReservation/1.5.0?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&dresserId=10000&reservationDate=20160123&reservationTime=15:30-16:00&reservationAddress=北京朝阳区&phoneNum=010888888

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


<h2 id="17">17. 我的预约V1.4.2</h2>

> 接口输入参数和返回值没有变化，变化的是进行中的订单增加了状态为11的退款中；已完成的订单增加了状态为12的已退款订单

请求方法：nggirl/app/cli/works/listReservation/1.4.2

请求URL：接口地址/nggirl/app/cli/works/listReservation/1.4.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|reservationType	|订单类型（1进行中，2待评价，3已完成）|
|page|页数 ，非必须参数，默认第一页
|num|每页信息数目，非必须参数，默认20

请求示例：

> http://localhost/nggirl/app/app/cli/works/listReservation/1.4.2?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&page=0&num=20

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "reservations": [
            {
                "reservationId": 2015103002708452,
                "dresserId": 60,
                "profile": "http://testphotosd.nggirl.com.cn/work/422da5cf651f4ddcb131d5d07bcee4cb.jpg",
                "cover": "http://photosd.nggirl.com.cn/work/fc3ba1e13b2140249802abbc044102d2.jpg",
                "name": "郭宏斌",
                "workType": "特殊造型",
                "cost": 1,
                "status": 2,
                "lastUpdateTime": 1446203608000,
                "systemTime": 1446547032000,
                "workId": 228,
                "reservationTime": "2015年10月30日 21:00 - 21:20",
                "authentication": 1,
                "isVDresser": 0,
                "praised": 0
            },
            {
                "reservationId": 2015103002337482,
                "dresserId": 60,
                "profile": "http://testphotosd.nggirl.com.cn/work/422da5cf651f4ddcb131d5d07bcee4cb.jpg",
                "cover": "http://photosd.nggirl.com.cn/work/fc3ba1e13b2140249802abbc044102d2.jpg",
                "name": "郭宏斌",
                "workType": "特殊造型",
                "cost": 1,
                "status": 2,
                "lastUpdateTime": 1446203237000,
                "systemTime": 1446547032000,
                "workId": 228,
                "reservationTime": "2015年10月30日 20:40 - 21:00",
                "authentication": 1,
                "isVDresser": 0,
                "praised": 0
            },
            {
                "reservationId": 2015082310607202,
                "dresserId": 57,
                "profile": "http://testphotosd.nggirl.com.cn/work/327bc7039b3e4cce8daf711ca0dd63b3.jpg",
                "cover": "http://testphotosd.nggirl.com.cn/work/22a4057f11594380a428ce55e21419b4.jpg",
                "name": "宝宝",
                "workType": "大片写真",
                "cost": 1,
                "status": 9,
                "lastUpdateTime": 1446202652000,
                "systemTime": 1446547032000,
                "workId": 284,
                "reservationTime": "2015年08月23日 18:00 - 20:00",
                "authentication": 1,
                "isVDresser": 1,
                "praised": 1
            }
        ],
        "totalNum": 14
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|Data - totalNum	|指定预约类型的总条数|
|Data - reservationId	|化妆师编号|
|Data - dresserId	| 化妆编号 |
|Data - cover	| 作品封面图片路径 |
|Data - name	| 化妆师姓名 |
|Data - workType	| 装束类型 |
|Data - cost	| 费用 |
|Data - status	| 订单状态0-11 |
|Data - lastUpdateTime	| 最后修改时间，如果status为已接收时，此值为接单时间；如果status为已支付时，此值为支付时间。|
|Data - systemTime	| 系统当前时间 |
|Data - workId	| 作品编号 |
|Data - reservationTime	| 预约时间 |
|Data - profile	| 化妆师头像 |
|Data - authentication	| 化妆师是否认证,0未认证，1已认证 |
|Data - isVDresser	| 是否是加V化妆师 |
|Data - praised	| 用户是否已经评价，0为未评价，1为已评价 |

<h3 id="17.5">17.5. 获取订单中进行中和待评价数目V1.4.2</h3>

> 接口输入参数和返回值没有变化。变化的是进行中的统计加入了状态11的订单。

请求方法：nggirl/app/cli/works/getReservationNum/1.4.2

请求URL：接口地址/nggirl/app//cli/works/getReservationNum/1.4.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义|
|---|---|
|accessToken	|用户授权令牌|

请求示例：
> http://localhost/nggirl/app/cli/works/getReservationNum/1.4.2

返回结果示例：

```json
{
    "data": {
        "reservationNum": {
            "running": 13,
            "notEvaluated": 1
        }
    },
    "code": 0
}
```

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|Data - reservationNum-running	|进行中|
|Data - reservationNum-notEvaluated	| 待评价|


<h2 id="18">18.取消预约(可预约时间改为30天)V1.4.2</h2>
> 增加：
>       入参：reason

请求方法：nggirl/app/cli/works/cancelReservation/1.4.2

请求URL：接口地址/nggirl/app/cli/works/cancelReservation/1.4.2

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|[必填]用户授权令牌
|reservationId	|[必填]预约编号
|reason	|[必填]取消原因

请求示例：

> http://localhost/nggirl/app/app/cli/works/cancelReservation/1.4.2?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&reservationId=10000

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


<h2 id="19">19. 支付</h2>

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


<h2 id="20">20. 删除支付记录（支付失败时调用）</h2>


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
    "code":0,
    "data":null
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确




<h2 id="21">21.退款</h2>

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


<h2 id="22">22. 完成预约</h2>

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
"data":null
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确

<h2 id="23">23.预约详情V1.4.2</h2>
> 增加：
>      返回值：resFlowsByDate、isRefundable、reason、originPrice、isUsePromotion、promotionTypeName、promotionCutMoney、isUseCoupon、couponCutMoney、actualCost

请求方法：nggirl/app/cli/works/reservationDetails/1.4.2

请求URL：接口地址/nggirl/app/cli/works/reservationDetails/1.4.2

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|reservationId|预约id

请求示例：

> http://localhost/nggirl/app/cli/works/reservationDetails/1.4.2?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&reservationId=10000

返回结果示例：

```json
{
    "code": 0,
    "data": {
    	 "reservationId":2016022667866647,
    	 "resStatus":4,
    	 "reservationTime":"2015年6月8日15:30-16:00",
    	 "reservationAddress":"北京市朝阳区",
         "dresserId": 410,
         "dresserProfile": "http://www.baidu.com/2.jpg",
         "dresserName":"宝宝",
         "imAccount":"test_dresser_72",
         "phoneNum":"18516993208",
         "sex":0,
         "starLevel": 5,
         "isVDresser":1,
         "workId":208,
         "workName":"你身上有股阳光味",
         "cover":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
         "workType": "职业装",
         "workCost": 100,
         "deleted":0,
         "workTags":[
         	"赫本",
         	"韩式公主",
         	"宋仲基"
         ],
         "originPrice":100,
         "isUsePromotion":1,
         "promotionTypeName":"首单五折优惠",
         "promotionCutMoney":20,
         "isUseCoupon":1,
         "couponCutMoney":20,
         "actualCost":60,
         "isPraised":1,
         "sumEvaluation":4,
         "resFlowsByDate":[
         	 {
                "recordDate": "2016.03.15",
                "reservationFlows": [
                    {
                        "majorDesc": "退款申请成功，正在退款中",
                        "minorDesc": "钱款将在1-3个工作日内退回至原账户，请注意查收",
                        "recordTime": 1458029454000
                    },
                    {
                        "majorDesc": "化妆师已接单，请尽快完成支付",
                        "minorDesc": "请在15分钟内完成支付",
                        "recordTime": 1458029235000
                    },
                    {
                        "majorDesc": "订单提交成功，请等待化妆师接单",
                        "minorDesc": "化妆师将在15分钟内确认您的订单",
                        "recordTime": 1458029215000
                    }
                ]
            },
            {
                "recordDate": "2016.03.15",
                "reservationFlows": [
                    {
                        "majorDesc": "退款申请成功，正在退款中",
                        "minorDesc": "钱款将在1-3个工作日内退回至原账户，请注意查收",
                        "recordTime": 1458029454000
                    },
                    {
                        "majorDesc": "化妆师已接单，请尽快完成支付",
                        "minorDesc": "请在15分钟内完成支付",
                        "recordTime": 1458029235000
                    },
                    {
                        "majorDesc": "订单提交成功，请等待化妆师接单",
                        "minorDesc": "化妆师将在15分钟内确认您的订单",
                        "recordTime": 1458029215000
                    }
                ]
            }
         ],
         "isRefundable":1,
         "reason":"化妆师太帅了！！！哈哈哈哈哈哈",
         "lastUpdateTime":1435196075742,
         "systemTime":1435196075742
    }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确,1表示用户未注册
|Data - reservationId	|预约编号
|Data - resStatus|预约状态,详情请看[预约状态码](https://github.com/nggirl/ngdocs/blob/master/nggirl/interface/%E9%A2%84%E7%BA%A6%E7%8A%B6%E6%80%81%E7%A0%81V1.4.2.md)
|Data - reservationTime|预约时间
|Data - reservationAddress|预约地址
|Data - dresserId|化妆师编号
|Data - dresserProfile|化妆师头像
|Data - dresserName|化妆师姓名
|Data - imAccount|im账号
|Data - phoneNum|化妆师手机号码
|Data - sex|化妆师性别：0为男，1为女。
|Data - starLevel|化妆师星级
|Data - isVDresser|化妆师是否加V 0否，1是
|Data - workId|作品编号
|Data - workName|作品名称
|Data - cover|封面
|Data - workType|化妆师类型名称
|Data - workCost|作品价格
|Data - deleted|作品是否下架 0未下架，1已下架
|Data - workTags|作品标签
|Data - originPrice|订单原价
|Data - isUsePromotion|是否使用了折扣 0没有使用，1有使用
|Data - promotionTypeName|折扣类型名称 "首单五折优惠"，"婚博会专场优惠"
|Data - promotionCutMoney|折扣优惠的金额
|Data - isUseCoupon|是否使用了优惠券 0没有使用，1有使用
|Data - couponCutMoney|优惠券抵消的金额
|Data - actualCost|实际支付的金额
|Data - isPraised|是否已评价 0为未评价，1为已评价
|Data - sumEvaluation|汇总评价
|Data - resFlowsByDate - recordDate|订单记录日期
|Data - resFlowsByDate - reservationFlows - majorDesc|订单状态-主描述
|Data - resFlowsByDate - reservationFlows - minorDesc|订单状态-次描述
|Data - resFlowsByDate - reservationFlows - recordTime|记录时间 13位毫秒数
|Data - isRefundable|是否可以退款 0不可以，1可以
|Data - reason|原因（取消、退款）
|Data - lastUpdateTime|最后修改时间，如果status为已接收时，此值为接单时间；如果status为已支付时，此值为支付时间
|Data - systemTime|系统当前时间


<h2 id="24">24.写评价(对化妆师的评论，也可以说对预约单的评论)V1.5.0</h2>

> 与原接口相比，入参没有变化，出参添加了hasReceivedCoupon和receivedCoupon

请求方法：nggirl/app/cli/works/evaluate/1.5.0

请求URL：接口地址/nggirl/app/cli/works/evaluate/1.5.0

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

> http://localhost/nggirl/app/cli/works/evaluate/1.5.0?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&reservationId=10000&onTimeEvaluation=5&descriptionEvaluation=5&tecniqueEvaluation=5&serviceEvaluation=5&evaluation=41545good

返回结果示例：

```json
{
   "code": 0,
   "data":{
     "sumEvaluation":5,
     "hasReceivedCoupon":1,
     "receivedCoupon":{
         "couponId": 100,
         "title": "南瓜券",
         "productType":"全品类",
         "couponNum": "Q2714141456",
         "money":0,
         "isDiscount":1,
         "discount":7.5,
         "limitPrice":10,
     }
   }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - sumEvaluation	|评价的汇总星级（1~5）
|Data - hasReceivedCoupon	|是否领取了优惠券，1已领取，0未领取
|Data - receivedCoupon	|已领取的优惠券信息
|Data - receivedCoupon - couponId	|优惠券id
|Data - receivedCoupon - title	|优惠券标题
|Data - receivedCoupon - productType	|优惠券类型
|Data - receivedCoupon - couponNum	|优惠券编号
|Data - receivedCoupon - money	|优惠券面值
|Data - receivedCoupon - isDiscount	|是否是折扣券，1是折扣券，0不是折扣券
|Data - receivedCoupon - discount	|折扣，0~10中间的数字
|Data - receivedCoupon - limitPrice	|最低消费限额

<h2 id="25">25. 获取评价(对化妆师的评论，也可以说对预约单的评论)</h2>

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

<h2 id="26">26. 投诉</h2>

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

<h2 id="27">27.获取作品的用户晒单v1.2</h2>

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

<h2 id="28">28.获取活动对应作品列表v1.2</h2>

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


<h2 id="29">29.退款操作通知V1.4.2</h2>

> 之前是：用户点击确认退款，会向后台运营人员发送通知；
> 当前为发送通知的同时，将订单状态修改为退款中；
> 新增：
>      入参：reason

请求方法：nggirl/app/cli/works/refundOperationNotify/1.4.2

请求URL：接口地址/nggirl/app/cli/works/refundOperationNotify/1.4.2

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken | [必填]授权令牌
|reservationId | [必填]预约编号
|reason |[必填]退款原因


请求示例：

> http://localhost/nggirl/app/cli/works/refundOperationNotify/1.4.2?accessToken=ACCESSTOKEN&reservationId=12323343

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

异常提示格式：

```json
{
  "code":1,
  "data":{
    "error":"此时段不允许退款"
  }
}
```


<h2 id="30">30.预约详情IOSV1.0(补充接口)</h2>

请求方法：nggirl/app/cli/works/reservationDetailsIos/1.0

请求URL：接口地址/nggirl/app/cli/works/reservationDetailsIos/1.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|reservationId|预约id

请求示例：

> http://localhost/nggirl/app/cli/works/reservationDetailsIos/1.0?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&reservationId=10000

返回结果示例：

```json
{
    "code": 0,
    "data": {
    	 "reservationId":2016022667866647,
    	 "dresserId":105,
    	 "cover":"http://photosd.nggirl.com.cn/work/88f285bc7f894368b617fff37dd31c03.png",
    	 "name":"宝宝",
    	 "workType":"新娘妆",
    	 "cost":200,
    	 "status":1,
    	 "lastUpdateTime":1320718222932,
    	 "systemTime":1320718222932,
    	 "workId":209,
    	 "reservationTime":"2016年02月03日 19:40 - 20:00",
    	 "profile":"http://photosd.nggirl.com.cn/work/88f285bc7f894368b617fff37dd31c03.png",
    	 "tags":[
    	 "赫本",
    	 "日常",
    	 "宋仲基"
    	 ],
    	 "praised":1,
    	 "phoneNum":"18516993208",
    	 "imAccount":"",
    	 "starLevel":5,
    	 "reservationAddress":"朝阳区团结湖",
    	 "sex":0,
    	 "sumEvaluation":4,
    	 "authentication":1,
    	 "isVDresser":1
    }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确,1表示用户未注册
|Data - reservationId	|预约编号
|Data - dresserId|化妆师编号
|Data - cover|作品封面
|Data - name|化妆师姓名
|Data - workType|装束类型
|Data - cost|花费
|Data - status|预约状态
|Data - lastUpdateTime|最后修改时间，如果status为已接收时，此值为接单时间；如果status为已支付时，此值为支付时间
|Data - systemTime|系统当前时间
|Data - workId|作品编号
|Data - reservationTime|预约时间
|Data - profile|化妆师头像
|Data - tags|作品标签
|Data - praised|是否评价 0为未评价，1为已评价
|Data - phoneNum|化妆师手机号码
|Data - imAccount|化妆师的im账号
|Data - starLevel|化妆师星级
|Data - reservationAddress|预约地址
|Data - sex|化妆师性别 0男 1女
|Data - sumEvaluation|汇总评价
|Data - authentication|化妆师是否认证,0未认证，1已认证
|Data - isVDresser|是否是加V化妆师

<h2 id="31">31.预约流程IOSV1.4.2</h2>
> 该版本新增接口

请求方法：nggirl/app/cli/works/reservationFlowsIos/1.4.2

请求URL：接口地址/nggirl/app/cli/works/reservationFlowsIos/1.4.2

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|reservationId|预约id

请求示例：

> http://localhost/nggirl/app/cli/works/reservationFlowsIos/1.4.2?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&reservationId=10000

返回结果示例：

```json
{
    "code": 0,
    "data": {
    	 "reservationId":2016022667866647,
    	 "status":4,
         "resFlowsByDate":[
         	 {
                "recordDate": "2016.03.15",
                "reservationFlows": [
                    {
                        "majorDesc": "退款申请成功，正在退款中",
                        "minorDesc": "钱款将在1-3个工作日内退回至原账户，请注意查收",
                        "recordTime": 1458029454000
                    },
                    {
                        "majorDesc": "化妆师已接单，请尽快完成支付",
                        "minorDesc": "请在15分钟内完成支付",
                        "recordTime": 1458029235000
                    },
                    {
                        "majorDesc": "订单提交成功，请等待化妆师接单",
                        "minorDesc": "化妆师将在15分钟内确认您的订单",
                        "recordTime": 1458029215000
                    }
                ]
            },
            {
                "recordDate": "2016.03.15",
                "reservationFlows": [
                    {
                        "majorDesc": "退款申请成功，正在退款中",
                        "minorDesc": "钱款将在1-3个工作日内退回至原账户，请注意查收",
                        "recordTime": 1458029454000
                    },
                    {
                        "majorDesc": "化妆师已接单，请尽快完成支付",
                        "minorDesc": "请在15分钟内完成支付",
                        "recordTime": 1458029235000
                    },
                    {
                        "majorDesc": "订单提交成功，请等待化妆师接单",
                        "minorDesc": "化妆师将在15分钟内确认您的订单",
                        "recordTime": 1458029215000
                    }
                ]
            }
         ],
         "isRefundable":1,
         "praised":0,
         "workId":401,
         "deleted":0,
         "profile":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg"
    }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确,1表示用户未注册
|Data - reservationId	|预约编号
|Data - status|预约状态,详情请看[预约状态码](https://github.com/nggirl/ngdocs/blob/master/nggirl/interface/%E9%A2%84%E7%BA%A6%E7%8A%B6%E6%80%81%E7%A0%81V1.4.2.md)
|Data - resFlowsByDate - recordDate|订单记录日期
|Data - resFlowsByDate - reservationFlows - majorDesc|订单状态-主描述
|Data - resFlowsByDate - reservationFlows - minorDesc|订单状态-次描述
|Data - resFlowsByDate - reservationFlows - recordTime|记录时间 13位毫秒数
|Data - isRefundable|是否可以退款 0不可以，1可以
|Data - praised|是否已评价 0为未评价，1为已评价
|Data - workId|作品编号
|Data - deleted|作品是否下架 0未下架，1已下架
|Data - profile|化妆师头像


<h2 id="32">32.预约详情IOSV1.4.2</h2>
> 新增：
>       返回值：isRefundable、reason、originPrice、isUsePromotion、promotionTypeName、promotionCutMoney、isUseCoupon、couponCutMoney、actualCost


请求方法：nggirl/app/cli/works/reservationDetailsIos/1.4.2

请求URL：接口地址/nggirl/app/cli/works/reservationDetailsIos/1.4.2

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|reservationId|预约id

请求示例：

> http://localhost/nggirl/app/cli/works/reservationDetailsIos/1.4.2?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&reservationId=10000

返回结果示例：

```json
{
    "code": 0,
    "data": {
    	 "reservationId":2016022667866647,
    	 "status":4,
    	 "reservationTime":"2015年6月8日15:30-16:00",
    	 "reservationAddress":"北京市朝阳区",
         "dresserId": 410,
         "profile": "http://www.baidu.com/2.jpg",
         "name":"宝宝",
         "imAccount":"test_dresser_72",
         "phoneNum":"18516993208",
         "sex":0,
         "starLevel": 5,
         "isVDresser":1,
         "workId":208,
         "workName":"你身上有股阳光味",
         "cover":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
         "workType": "职业装",
         "cost": 100,
         "deleted":1,
         "tags":[
         	"赫本",
         	"韩式公主",
         	"宋仲基"
         ],
         "originPrice":100,
         "isUsePromotion":1,
         "promotionTypeName":"首单五折优惠",
         "promotionCutMoney":20,
         "isUseCoupon":1,
         "couponCutMoney":20,
         "actualCost":60,
         "praised":1,
         "sumEvaluation":4,
         "isRefundable":1,
         "reason":"化妆师太帅了！！！哈哈哈哈哈哈",
         "lastUpdateTime":1435196075742,
         "systemTime":1435196075742
    }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确,1表示用户未注册
|Data - reservationId	|预约编号
|Data - status|预约状态,详情请看[预约状态码](https://github.com/nggirl/ngdocs/blob/master/nggirl/interface/%E9%A2%84%E7%BA%A6%E7%8A%B6%E6%80%81%E7%A0%81V1.4.2.md)
|Data - reservationTime|预约时间
|Data - reservationAddress|预约地址
|Data - dresserId|化妆师编号
|Data - profile|化妆师头像
|Data - name|化妆师姓名
|Data - imAccount|im账号
|Data - phoneNum|化妆师手机号码
|Data - sex|化妆师性别：0为男，1为女。
|Data - starLevel|化妆师星级
|Data - isVDresser|化妆师是否加V 0否，1是
|Data - workId|作品编号
|Data - workName|作品名称
|Data - cover|封面
|Data - workType|化妆师类型名称
|Data - cost|作品价格
|Data - deleted|作品是否下架 0未下架，1已下架
|Data - tags|作品标签
|Data - originPrice|订单原价
|Data - isUsePromotion|是否使用了折扣 0没有使用，1有使用
|Data - promotionTypeName|折扣类型名称 "首单五折优惠"，"婚博会专场优惠"
|Data - promotionCutMoney|折扣优惠的金额
|Data - isUseCoupon|是否使用了优惠券 0没有使用，1有使用
|Data - couponCutMoney|优惠券抵消的金额
|Data - actualCost|实际支付的金额
|Data - praised|是否已评价 0为未评价，1为已评价
|Data - sumEvaluation|汇总评价
|Data - isRefundable|是否可以退款 0不可以，1可以
|Data - reason|原因（取消、退款）
|Data - lastUpdateTime|最后修改时间，如果status为已接收时，此值为接单时间；如果status为已支付时，此值为支付时间
|Data - systemTime|系统当前时间



<h2 id="33">33.支付宝web支付(遗漏接口)</h2>

请求方法：nggirl/app/charge/alipay/h5/payReservation

请求url：接口地址/nggirl/app/charge/alipay/h5/payReservation

支持格式：HTML

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|reservationId|预约编号

请求示例：
> localhost/ngggirl/app/charge/alipay/h5/payReservation

返回结果：

![支付页面](http://photosd.nggirl.com.cn/work/c962aa9f2b9c40e5b0682c6adee0ebbe.jpg)




<h2 id="34">34.关于我(关于化妆师)1.5.0</h2>
> 该版本新增接口

请求方法：nggirl/app/cli/dresser/getAboutDresser/1.5.0

请求url：接口地址/nggirl/app/cli/dresser/getAboutDresser/1.5.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|dresserId|化妆师编号

请求示例：
> localhost/ngggirl/app/cli/dresser/getAboutDresser/1.5.0

返回结果示例：
```json
{
	"code":0,
	"data":{
		"dresserId":84,
        	"dresserName":"宝宝",
        	"portrait":"http://testphotosd.nggirl.com.cn/work/80cd838a02d7407195594c90856ea1a3.jpg",
        	"sex":0,
        	"dresserProfile":"http://testphotosd.nggirl.com.cn/work/80cd838a02d7407195594c90856ea1a3.jpg",
        	"isVDresser":1,
        	"starLevel":4,
        	"dresserDesc":"世界著名化妆师。、。。。zzzzzz",
        	"coartist":"章子怡，小李子，尼基塔，迈克",
        	"experience":[
            		{
            		"id":1,
            		"item":"hhhhhhhhh"
            		},
            		{
            		"id":2,
            		"item":"hhhhhhhhh"
            		},
            		{
            		"id":3,
            		"item":"hhhhhhhhh"
            		}
        ]
	}
}
```

返回字段说明：


|字段名称|字段含义|
|---|---|
|Code|错误码 0表示正确|
|Data - dresserId|化妆师编号|
|Data - dresserName|化妆师昵称|
|Data - portrait|化妆师写真|
|Data - sex|性别 0男，1女|
|Data - dresserProfile|化妆师头像|
|Data - isVDresser|是否加V 1是，0否|
|Data - starLevel|化妆师星级|
|Data - dresserDesc|化妆师简介|
|Data - coartist|合作艺人|
|Data - experience|从业经历|
|Data - experience - id|从业经历编号|
|Data - experience - item|从业经历条目|
