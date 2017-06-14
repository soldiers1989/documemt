<h1>美妆沙龙-作品V2.5.3</h1>

目录

* [1.获取所有产品列表V1.4.0](#1)
* [2.获取产品详情V1.5.0](#2)
* [3.获取产品评论](#3)
* [4.获取产品对应的晒单](#4)
* [5.喜欢沙龙V2.5.3](#5)
* [6.取消喜欢沙龙](#6)
* [7.评论产品(仅对当前产品评论)](#7)
* [8.准备预约信息](#8)
* [9.支付](#9)
* [10.获取喜欢的人](#10)
* [11.适用当前联合产品的优惠券(更新优惠券信息)V1.3.2](#11)
* [12.判断是否可约](#12)
* [13.删除无用的预支付记录V1.3.2](#13)
* [14.支付宝web支付](#14)


<h2 id="1">1.获取所有产品列表</h2>

请求方法：nggirl/app/cli/salon/works/listSalonProducts/1.4.0

请求URL：接口地址/nggirl/app/cli/salon/works/listSalonProducts/1.4.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|page	|页数  非必需参数，默认第一页
|num	|每页信息数目 非必需参数，默认20
|city|城市名称

请求示例：

> http://localhost/nggirl/app/cli/salon/works/listSalonProducts/1.4.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&page=0&num=20&city=北京

返回结果示例：

```json
{
    "code": 0,
    "data":[{
	"unionProductId": 1234567,
	"productType":1,
	"cover":"http://www.baidu.com/1.jpg",
	"title":"美妆下午茶-小白专场",
	"descr":"活动介绍巴拉巴拉巴拉巴拉巴拉",
	"price":99,
	"dresserId":1234567,
	"dresserName":"宝宝",
	"dresserProfile":"http://www.baidu.com/1.jpg",
	"sex":1,
	"starLevel":4,
	"holdTime":"2015.12.10 15:00-17:00",
	"holdPlace":"团结湖"
	},
	{
	"unionProductId": 1234567,
	"productType":1,
	"cover":"http://www.baidu.com/1.jpg",
	"title":"美妆下午茶-小白专场",
	"descr":"活动介绍巴拉巴拉巴拉巴拉巴拉",
	"price":99,
	"dresserId":1234567,
	"dresserName":"宝宝",
	"dresserProfile":"http://www.baidu.com/1.jpg",
	"sex":1,
	"starLevel":4,
	"holdTime":"2015.12.10 15:00-17:00",
	"holdPlace":"团结湖"
       }]
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - unionProductId|产品联合编号
|Data - productType|产品类型：1下午茶，2上门教学3，企业教学，4年会妆
|Data - cover	|封面图片路径
|Data - title   |产品标题
|Data - descr    |简介
|Data - price	|单价
|Data - dresserId|化妆师编号
|Data - dresserName|化妆师姓名
|Data - dresserProfile|化妆师头像
|Data - sex|化妆师性别，0为男，1为女
|Data - starLevel|化妆师星级
|Data - holdTime|活动时间 格式：”2015.12.10 13:00-17:00“
|Data - holdPlace|活动地点



<h2 id="2">2.获取产品详情V1.5.0</h2>

> 查询sql性能优化。去除dresserDescriptions字段，增加了portrait,sex,isVDresser,starLevel，dresserDesc，coartist，experience字段

请求方法：nggirl/app/cli/salon/works/salonProductDetail/1.5.0

请求URL：接口地址/nggirl/app/cli/salon/works/salonProductDetail/1.5.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|unionProductId |产品联合编号
|productType|产品类型 1下午茶，2上门教学，3企业教学，4年会妆

请求示例：

> http://localhost/nggirl/app/cli/salon/works/salonProductDetail/1.5.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&unionProductId=123456&productType=1

返回结果示例：

```json
{
	"code":0,
	"data":{
		"unionProductId":1234567,
		"productType":1,
		"isRegisterEnd":1,
		"cover":[
			"http://www.baidu.com/1.jpg",
			"http://www.baidu.com/1.jpg"
		],
		"title":"美妆下午茶-小白专场",
		"isPraised":0,
		"descr":"活动介绍巴拉巴拉巴拉巴拉巴拉",
		"holdTime":"2015.12.10 15:00-17:00",
		"registEndTime":"2015.12.09 17:00",
		"price":99,
		"holdPlace":"团结湖",
		"longitude":"",
		"lattitude":"",
		"peopleLow":3,
		"peopleHigh":5,
		"resUserCount":3,
		"resUsers":[
	    		{
            		"resUserId": 193,
            		"resUserName": "郭宏斌",
        		"resProfile": "http://testphotosd.nggirl.com.cn/work/80cd838a02d7407195594c90856ea1a3.jpg"
          },
        	{
        		 "resUserId": 116,
        		 "resUserName": "ZZzzzz",
        		 "resProfile": "http://testphotosd.nggirl.com.cn/work/98b09cbc00804529a408c3e5fd061fd7.jpg"
          }
		],
		"atDescription":[
			{
			 "title":"美妆下午茶-小白专场",
			 "paragraph":"美妆下午茶值小白专场，转为化妆小白贴心打造",
			 "picture":"http://testphotosd.nggirl.com.cn/work/80cd838a02d7407195594c90856ea1a3.jpg",
       			 "picWidth":200,
       			 "picHeight":100
			},
			{
			 "title":"美妆下午茶-小白专场",
			 "paragraph":"美妆下午茶值小白专场，转为化妆小白贴心打造",
			 "picture":"http://testphotosd.nggirl.com.cn/work/80cd838a02d7407195594c90856ea1a3.jpg",
       			 "picWidth":400,
       			 "picHeight":300
			}
		],
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
			"化妆师经历1","化妆师经历2","化妆师经历3"
		],
		"loverCount":10,
		"lovers":[
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
		"resRules":[
			"1......",
			"2......",
			"3......"
		]
	}
}
```

返回字段说明：

|字段名称|字段含义|
|------|------|
|Code  |0表示正确
|Data - unionProductId|产品联合编号
|Data - productType|产品类型 1下午茶，2上门教学，3企业教学，4年会妆
|Data - isRegisterEnd|产品是否到达报名截止日期，1为是，0为否.
|Data - cover|封面url地址
|Data - title|标题
|Data - isPraised|用户是否点赞 0未点赞，1已点赞
|Data - descr|简介
|Data - holdTime|举办时间 格式：”2015.12.10 13:00-17:00“
|Data - registEndTime|报名截止时间
|Data - price|单价
|Data - holdPlace|举办地点
|Data - longitude|经度
|Data - lattitude|纬度
|Data - peopleLow|成团人数下限
|Data - peopleHigh|成团人数上限
|Data - resUserCount|已预约人数
|Data - resUsers - resUserId|预约用户Id
|Data - resUsers - resUserName|预约用户昵称
|Data - resUsers - resProfile|预约用户头像
|Data - atDescription - title|图文介绍-标题
|Data - atDescription - paragraph|图文介绍-内容
|Data - atDescription - picture|图文介绍-图片
|Data - atDescription - picWidth|图片宽度
|Data - atDescription - picHeight|图片高度
|Data - dresserId|化妆师编号
|Data - dresserName|化妆师姓名
|Data - dresserProfile|化妆师头像
|Data - sex|化妆师性别 0为男，1为女
|Data - portrait|化妆师写真
|Data - isVDresser|化妆师是否加V
|Data - starLevel|化妆师星级
|Data - dresserDesc|化妆师简介
|Data - coartist|合作艺人
|Data - experience|化妆师工作经历
|Data - loverCount|喜欢的人数-移动端显示
|Data - lovers - loverUserId|用户编号
|Data - lovers - loverUserName|用户昵称
|Data - lovers - loverProfile|用户头像

|Data - resRules|预约需知-内容




<h2 id="3">3.获取产品评论</h2>

请求方法：nggirl/app/cli/salon/works/listProEvaluation/1.3

请求URL：接口地址/nggirl/app/cli/salon/works/listProEvaluation/1.3

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|unionProductId|产品联合编号
|productType|产品类型 1下午茶，2上门教学，3企业教学，4年会妆
|page|页数 非必须参数，默认第一页
|num|每页信息数目，非必须参数，默认20

请求示例：

> http://localhost/nggirl/app/cli/salon/works/listProEvaluation/1.3?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&unionProductId=1234567&page=0&num=20&productType=1

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
                    "content":"非常喜欢，想来一个",
                    "evaluateTime": 1435196075742
                },
                {
                    "evaluateUserId":1,
                    "evaluateName": "王明",
                    "evaluateProfile":"http://www.baidu.com/1.jpg",
                    "content":"非常喜欢，想来一个",
                    "evaluateTime": 1435196075742
                 }
           ]
     }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|hasMore	|是否还有更多的数据，0没有，1有
|Data - evaluateList - evaluateUserId	|用户编号
|Data - evaluateList - evaluateName|用户名
|Data - evaluateList - evaluateProfile|头像路径
|Data - evaluateList - content|评价内容
|Data - evaluateList - evaluateTime|评论时间


<h2 id="4">4.获取产品对应的晒单</h2>

请求方法：nggirl/app/cli/salon/works/getProEvaluations/1.3

请求URL：接口地址/nggirl/app/cli/salon/works/getProEvaluations/1.3

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|unionProductId	|产品联合编号
|productType|产品类型 1下午茶，2上门教学，3企业教学，4年会妆
|page	|页数。非必需参数，默认第一页
|num	|每页信息数目。非必须参数，默认20

请求示例：

> http://localhost/nggirl/app/salon/works/getProEvaluations/1.3?app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=0c0cf4990aa72f3a75b961c21bab61d51f682f68&unionProductId=316&page=1&num=3&productType=1

返回结果示例：

```json
{
    "code": 0,
    "data": {
    	"hasMore":0,
        "evaluations":[
                {
                "userId": 341,
                "userName": "美丽",
                "profile": "http://photosd.nggirl.com.cn/work/f40b2e3d9b3c4bbb8641e0d46732450f.png",
                "content": "不错",
                "starLevel": 2,
                "dateTime": 1435196075742,
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
|Data - evaluations - userId |用户编号
|Data - evaluations - userName	|用户名
|Data - evaluations - profile	|用户头像路径
|Data - evaluations - content	|评价内容
|Data - evaluations - starLevel	|星级
|Data - evaluations - dateTime	|晒单时间
|Data - evaluations - photos	|照片列表


<h2 id="5">5.喜欢沙龙V2.5.3</h2>

>出参增加addScore字段

请求方法：nggirl/app/cli/salon/works/praiseProduct/2.5.3

请求URL：接口地址/nggirl/app/cli/salon/works/praiseProduct/2.5.3

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|unionProductId	|产品联合编号
|productType|产品类型 1下午茶，2上门教学，3企业教学，4年会妆

请求示例：

> http://localhost/nggirl/app/cli/salon/works/praiseProduct/2.5.3?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&unionProductId=1234567&productType=1

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


<h2 id="6">6.取消喜欢沙龙</h2>

请求方法：nggirl/app/cli/salon/works/cancelPraiseProduct/1.3

请求URL：接口地址/nggirl/app/cli/salon/works/cancelPraiseProduct/1.3

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|unionProductId|产品联合编号
|productTtype|产品类型 1下午茶，2上门教学，3企业教学，4年会妆

请求示例：

> http://localhost/nggirl/app/cli/salon/works/cancelPraiseProduct/1.3?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&unionProductId=1234567&productTtype=1

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
|Data | null


<h2 id="7">7.评论产品(仅对当前产品评论)</h2>

请求方法：nggirl/app/cli/salon/works/commentProduct/1.3

请求URL：接口地址/nggirl/app/cli/salon/works/commentProduct/1.3

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|unionProductId |产品联合编号
|productType|产品类型 1下午茶，2上门教学，3企业教学，4年会妆
|content |评论内容

请求示例：

> http://localhost/nggirl/app/cli/salon/works/commentProduct/1.3?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&unionProductId=1234567&productType=1&content=地方地方

返回结果示例：

```json
{
    "code": 0,
    "data":{
    	 "evaluateUserId":1,
          "evaluateName": "王明",
          "evaluateProfile":"http://www.baidu.com/1.jpg",
          "content":"非常喜欢，想来一个",
          "evaluateTime": 1435196075742
    }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - evaluateUserId	|用户编号
|Data - evaluateName|用户名
|Data - evaluateProfile|头像路径
|Data - content|评价内容
|Data - evaluateTime|评论时间


<h2 id="8">8.准备预约信息</h2>

请求方法：nggirl/app/cli/salon/works/prepareReservationInfo/1.3

请求URL：接口地址/nggirl/app/cli/salon/works/prepareReservationInfo/1.3

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|unionProductId |产品联合编号
|productType    |产品类型 1下午茶，2上门教学，3企业教学，4年会妆

请求示例：

> http://localhost/nggirl/app/cli/salon/works/prepareReservationInfo/1.3?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&unionProductId=1234567&productType=1

返回结果示例：

```json
{
    "code": 0,
    "data":{
    	"unionProductId":12,
    	"productType":1,
    	"title":"美妆下午茶-小白专场",
    	"price":99,
    	"cover":"http://testphotosd.nggirl.com.cn/work/ca46c24f0dbc4ce48c1d8f2c427c50cc.jpg",
    	"dresserId":84,
    	"dresserName":"宝宝",
    	"profile":"http://testphotosd.nggirl.com.cn/work/ca46c24f0dbc4ce48c1d8f2c427c50cc.jpg",
    	"sex":1,
    	"starLevel":4,
    	"holdTime":"2015.11.25 15:00-17:00",
    	"holdPlace":"团结湖",
    	"resRules":[
    		"可以单人预约多个",
    		"成团之后不可再报名",
    		"。。"
    	]
    }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - unionProductId |产品联合编号
|Data - productType |产品类型 1下午茶，2上门教学，3企业教学，4年会妆
|Data - title|标题
|Data - cover|封面图片
|Data - price|单价
|Data - dresserId|化妆师编号
|Data - dresserName|化妆师姓名
|Data - profile|头像
|Data - sex|性别
|Data - starLevel|化妆师星级
|Data - holdTime|举办时间 格式：”2015.12.10 13:00-17:00“
|Data - holdPlace|举办地点
|Data - resRules|预约须知


<h2 id="9">9.支付</h2>

请求方法：nggirl/app/cli/salon/works/payProReservation/1.3

请求URL：接口地址/nggirl/app/cli/salon/works/payProReservation/1.3

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义
|---|---
|accessToken|[必填]用户授权令牌
|unionProductId|[必填]产品联合编号
|couponId|[可选]优惠券编号
|reservationNum|[必填]预约数量
|phoneNum|[必填]联系电话
|payType|[必填]支付类型，1微信支付，2支付宝支付
|weixinPayType|[当payType为1时必填]微信支付类型，1APP支付，2JSAPI支付，默认是APP支付
|weixinOpenId|[当weixinPayType为2时必填]微信openid

请求示例：

> http://localhost/nggirl/app/cli/salon/works/payProReservation/1.3?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&unionProductId=1&productType=1&reservationNum=6&phoneNum=18516993208&payType=1

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
|Data - weixin_noncestr|随机字符串，不长于32位
|Data - weixin_timestamp|时间戳
|Data - weixin_sign|签名
|Data - product|商品名称，最长为128个汉字
|Data - product_detail|商品详情，最长为512个汉字
|Data - unionResId|订单编号
|Data - notifyUrl|支付结果异步通知地址，该值只有在支付宝支付时有用
|Data - isComplete|支付成功之后是否可以成团，1可以成团，0不可成团




<h2 id="10">10.获取喜欢的人</h2>

请求方法：nggirl/app/cli/salon/works/listProductLover/1.3

请求URL：接口地址/nggirl/app/cli/salon/works/listProductLover/1.3

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌
|unionProductId |产品联合编号
|productType    |产品类型 1下午茶，2上门教学，3企业教学，4年会妆
|page|页数 非必须参数，默认第一页
|num|每页信息数目，非必须参数，默认20

请求示例：

> http://localhost/nggirl/app/cli/works/salon/works/listProductLover/1.3?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&workId=1234567&page=0&num=20

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



<h2 id="11">11.适用当前联合产品的优惠券(更新优惠券信息)V1.3.2</h2>

请求方法：nggirl/app/cli/salon/works/listCouponUse/1.3.2

请求URL：接口地址nggirl/app/cli/salon/works/listCouponUse/1.3.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---
|accessToken|	[必填]用户授权令牌
|unionProductId |[必填]产品联合编号
|reservationNum|[可选]预约人数，默认为1
|page|[可选]页数，非必需参数，默认第一页，页码从0开始
|num|[可选]每页信息数目，非必须参数，默认20

请求示例：
>
http://localhost/nggirl/app/cli/salon/works/listCouponUse/1.3.2?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&page=0&num=20

返回结果示例：
```json
{
    "code": 0,
    "data": [
        {
            "couponId": 151,
            "saleInfo": "88元",
            "lowPrice": 100,
            "deadline": "永久有效",
            "fromChannel": "杨凯",
            "fitProductName": "仅限美妆沙龙",
            "useStatus": 0,
            "cutCost":88
        },
        {
            "couponId": 151,
            "saleInfo": "5折",
            "lowPrice": 100,
            "deadline": "有效期：2015.10.21-2015.10.29",
            "fromChannel": "海威",
            "fitProductName": "仅限美妆沙龙",
            "useStatus": 2,
            "cutCost":50
        }
    ]
}
```
返回字段说明：

|字段名|字段含义
|---|---
|Code|	错误码，0表示正确
|Data - couponId|优惠券id
|Data - saleInfo|优惠金额或打几折
|Data - lowPrice|最低多少元起可以使用
|Data - deadLine	|有效期 "永久有效" 或者 "有效期：2015.10.21-2015.10.29"
|Data - fromChannel	|来自哪个渠道
|Data - fitProductName	|适用产品类型 "全品类","仅限上门美妆","仅限美妆沙龙"
|Data - useStatus	|使用状态 0未使用,1已使用,2已过期
|Data - cutCost	|需要减去的金额，方便移动端计算（当是打折时，四舍五入取整）


<h2 id="12">12.判断是否可约</h2>

请求方法：nggirl/app/cli/salon/works/isProductAllowRes/1.3

请求URL：接口地址/nggirl/app/cli/salon/works/isProductAllowRes/1.3

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|unionProductId |产品联合编号


请求示例：

> http://localhost/nggirl/app/cli/salon/works/isProductAllowRes/1.3?unionProductId=1

返回结果示例：

```json
{
 "code":0,
 "data": {
 	"isAllowRes":1,
 	"reason":"已达到成团人数上限或已到报名截止日期"
 }
}
```
返回字段说明

|参数名称|参数含义
|---|---
|Code|错误码，0表示正确
|Data - isAllowRes|是否可约 0可约，1不可约
|Data - reason|不可约原因，可约时为null，不可约时为“已达到成团人数上限或已到报名截止日期”


<h2 id="13">13.删除无用的预支付记录V1.3.2</h2>

请求方法：nggirl/app/cli/salon/works/deletePayRecord/1.3.2

请求URL：接口地址/nggirl/app/cli/salon/works/deletePayRecord/1.3.2

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|用户授权令牌|
|unionResId	|联合订单id|

请求示例：

> http://localhost/nggirl/app/cli/salon/works/deletePayRecord/1.3.2

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
|Data | null





<h2 id="14">14.支付宝web支付</h2>

> 此接口仅适用于支付宝web支付，支付成功之后，根据支付宝同步返回的商户地址，重定向到需要的页面

请求方法：nggirl/app/charge/alipay/h5/paySalonReservation

请求url：接口地址/nggirl/app/charge/alipay/h5/paySalonReservation

支持格式：HTML

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|unionResId|预约编号

请求示例：
> localhost/ngggirl/app/charge/alipay/h5/paySalonReservation

返回结果：


![支付页面](http://photosd.nggirl.com.cn/work/c962aa9f2b9c40e5b0682c6adee0ebbe.jpg)
