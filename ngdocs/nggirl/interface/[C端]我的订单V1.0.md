# 我的订单接口
* [1.我的订单](#1)
* [3.订单详情](#3)
* [4.订单详情IOS](#4)
* [5.作品详情IOS](#5)
* [6. 获取作品进行中及待评价的数目](#6)

<h2 id="1">1.我的订单：</h2>

请求方法：nggirl/app/cli/order/list/3.1.0

请求URL：接口地址nggirl/app/cli/order/list/3.1.0

支持格式：JSON

HTTP请求方式：GET


应用请求参数：

|参数名称	|参数含义|
|---|---|
|accessToken|授权令牌|
|reservationType	|订单类型（0全部，1待付款，2待发货，3待收货，4待评价）|
|pageNum|页码，从0开始|
|pageSize|页面大小，数据条数，默认为5|

请求示例：
> http://localhost/nggirl/app/cli/order/list/1.0?accessToken=ab3582cb4d3f45edb6e010359559f6e7&reservationType=0&pageNum=1&pageSize=5

返回结果示例：

```json
{
	"code":0,
	"data"[
		{"userId":107,
		"orderCode":"1",
		"imgUrl":"1",
		"reamTitle":"1",
		"payAmount":300,
		"orderStatus":0,
		"payStatus":1,
		"quantity":1,
		"remainTime":"908784",
		"status":0}]
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|Data - orderCode	|订单编号|
|Data - imgUrl	| 订单商品图片路径 |
|Data - reamTitle	| 订单商品的标题 |
|Data - payAmount	| 支付金额 |
|Date - orderStatus	| 订单状态，0-已完成，1-已关闭，2-退款中，3-倒计时，4-待发货，5-待收货，6-待评价|
|Date - payStatus	| 支付状态，0-待支付,1-支付成功,2-支付失败|
|Data - quantity	| 订单中商品的总数 |
|Date - remainTime	| 订单剩余时间 |
|Date - status	| 售后状态，0-不在售后状态，1-在售后状态 |

<h2 id="3">3.订单详情：</h2>
请求方法：nggirl/app/cli/works/reservationDetails/1.0

请求URL：接口地址/nggirl/app/cli/works/reservationDetails/1.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义|
|---|---|
|reservationId	|订单编号|

请求示例：
> http://nggirl/app/cli/works/reservationDetails/1.0?reservationId=2015082309836626

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "dresserId": 57,
        "profile": "http://testphotosd.nggirl.com.cn/work/327bc7039b3e4cce8daf711ca0dd63b3.jpg",
        "name": "杨凯",
        "starLevel": 4,
        "workType": "亲子摄影妆",
        "cost": 1,
        "reservationTime": "2015年月23日 16:00 - 18:00",
        "reservationAddress": "北京朝阳区常营",
        "lastUpdateTime": 1440579882000,
        "systemTime": 1446015642000,
        "praised": 0,
        "phoneNum": "18500192385",
        "imAccount": "product_dresser_57",
        "status": 2,
        "workId": 224,
        "reservationId": 2015082309836626,
        "cover": "http://testphotosd.nggirl.com.cn/work/11e458134d64410aa9d2f80101a7a776.jpg",
        "tags": [
            "欧美风",
            "烟熏妆",
            "减龄妆"
        ],
        "sex": 1,
        "sumEvaluation": null,
        "authentication": 1,
        "isVDresser": 1
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|Data - userId	| 用户id |
|Data - profile	| 化妆师头像图片 |
|Data - name	| 化妆师名称 |
|Data - starLevel	| 化妆师星级 |
|Data - workType	| 化妆师类型名称 |
|Data - cost	| 化妆费用 |
|Data - reservationTime	| 预约日期 |
|Data - reservationAddress	|预约地址  |
|Data - lastUpdateTime	| 最后修改时间，如果status为已接收时，此值为接单时间；如果status为已支付时，此值为支付时间。 |
|Data - systemTime	| 系统当前时间 |
|Data - praised	| 用户是否已经评价，0为未评价，1为已评价 |
|Data - phoneNum	| 化妆师的电话号码 |
|Data - imAccount	| 化妆师的im账号 |
|Data - status	| 订单状态0-11 |
|Data - workId	| 作品编号 |
|Data - reservationId	| 预约编号 |
|Data - cover	|作品封面  |
|Data - tags	| 作品标签 |
|Data - sex	| 化妆师性别，0为男，1为女 |
|Data - sumEvaluation	| 汇总评价 |
|Data - authentication	| 化妆师是否认证,0未认证，1已认证 |
|Data - isVDresser	| 是否是加V化妆师 |

<h2 id="4">4.订单详情IOS：</h2>
请求方法：nggirl/app/cli/works/reservationDetailsIos/1.0

请求URL：接口地址/nggirl/app/cli/works/reservationDetailsIos/1.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义|
|---|---|
|reservationId	|订单编号|

请求示例：
> http://nggirl/app/cli/works/reservationDetailsIos/1.0?reservationId=2015082309836626

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "reservationId": 2015082309836626,
        "dresserId": 57,
        "cover": "http://testphotosd.nggirl.com.cn/work/11e458134d64410aa9d2f80101a7a776.jpg",
        "name": "杨凯",
        "workType": "亲子摄影妆",
        "cost": 1,
        "status": 2,
        "lastUpdateTime": 1446083214000,
        "systemTime": 1446187023000,
        "workId": 224,
        "reservationTime": "2015年08月23日 16:00 - 18:00",
        "profile": "http://testphotosd.nggirl.com.cn/work/327bc7039b3e4cce8daf711ca0dd63b3.jpg",
        "tags": [
            "欧美风",
            "烟熏妆",
            "减龄妆"
        ],
        "praised": 0,
        "phoneNum": "18500192385",
        "imAccount": "product_dresser_57",
        "starLevel": 4,
        "reservationAddress": "北京朝阳区常营",
        "sex": 1,
        "sumEvaluation": null,
        "authentication": 1,
        "isVDresser": 1
    }
}
```

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
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
|Data - profile	| 化妆师头像 |
|Data - tags	| 作品标签 |
|Data - phoneNum	| 化妆师手机号 |
|Data - imAccount	| 化妆师的im账号 |
|Data - starLevel	| 化妆师星级 |
|Data - reservationAddress	| 预约地址 |
|Data - sex	| 化妆师性别，0为男，1为女 |
|Data - sumEvaluation	| 汇总评价 |
|Data - authentication	| 化妆师是否认证,0未认证，1已认证 |
|Data - isVDresser	| 是否是加V化妆师 |

<h2 id="5">5.作品详情IOS：</h2>

请求方法：nggirl/app/cli/works/getWorksDetailIos/1.0

请求URL：接口地址/nggirl/app/cli/works/getWorksDetailIos/1.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义	
|---|---|
|accessToken	|用户授权令牌
|workId	|作品编号

请求示例：

> http://localhost/nggirl/app/cli/works/getWorksDetailIos/1.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&workId=318

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "workId": 318,
        "cover": "http://testphotosd.nggirl.com.cn/work/65766285b6754186bc9dd2088e6e023b.jpg",
        "workType": "特殊造型",
        "cost": 1,
        "reservationNum": 10,
        "timeUsed": 60,
        "contentPhoto": [
            "http://testphotosd.nggirl.com.cn/work/65766285b6754186bc9dd2088e6e023b.jpg"
        ],
        "descriptions": "欧美范儿",
        "cosmetics": [
            {
                "cosmeticsClass": "粉底液",
                "cosmeticsBrand": [
                    "La Prairie蓓丽"
                ]
            }
        ],
        "tags": [
            "欧美风",
            "英伦"
        ],
        "publishTime": 1440564821000,
        "praiseStatus": 0,
        "collectStatus": 0,
        "dresserId": 68,
        "dresserName": "何昱成（树凡）",
        "dresserProfile": "http://nggirl-product-res.oss-cn-beijing.aliyuncs.com/work/4764cb90fcd84341ba53ee134c284f2b.jpg",
        "starLevel": 3,
        "authentication": 1,
        "isVDresser": 0,
        "loverCount": 3,
        "lovers": [
            {
                "loverUserId": 182,
                "loverName": "书虫Pro",
                "loverProfile": "http://tp3.sinaimg.cn/2136534274/50/5705153085/1"
            },
            {
                "loverUserId": 115,
                "loverName": "杨凯",
                "loverProfile": "http://testphotosd.nggirl.com.cn/work/a633202931cb4e1381e5505b32c6b4b7.jpg"
            },
            {
                "loverUserId": 160,
                "loverName": "美丽",
                "loverProfile": "http://photosd.nggirl.com.cn/work/f40b2e3d9b3c4bbb8641e0d46732450f.png"
            }
        ],
        "evaluationCount": 1,
        "evaluations": [
            {
                "evaluateUserId": 115,
                "evaluateName": "杨凯",
                "evaluateProfile": "http://testphotosd.nggirl.com.cn/work/a633202931cb4e1381e5505b32c6b4b7.jpg",
                "evaluation": "男男女女",
                "evaluateTime": 1446113322000
            }
        ],
        "recommends": [
            {
                "workId": 227,
                "cover": "http://photosd.nggirl.com.cn/work/cf700715a1ba49c7a3c87c0091e2ca0d.jpg",
                "praiseNum": 2,
                "praised": 0,
                "dresserId": 60
            },
            {
                "workId": 228,
                "cover": "http://photosd.nggirl.com.cn/work/fc3ba1e13b2140249802abbc044102d2.jpg",
                "praiseNum": 3,
                "praised": 0,
                "dresserId": 60
            },
            {
                "workId": 208,
                "cover": "http://photosd.nggirl.com.cn/work/cafc8a63326b43ea966593847bd683db.jpg",
                "praiseNum": 0,
                "praised": 0,
                "dresserId": 56
            }
        ],
        "sex": 0
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
|Data - sex|化妆师性别，0为男，1为女。
|Data - loverCount|喜欢的人数
|Data - lovers|喜欢的人列表
|Data - lovers- loverUserId |用户编号
|Data - lovers- loverName|用户名
|Data - lovers - loverProfile|用户头像
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

<h2 id="6">6. 获取订单中进行中和待评价数目：</h2>
请求方法：nggirl/app/cli/works/getReservationNum/1.0

请求URL：接口地址/nggirl/app//cli/works/getReservationNum/1.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义|
|---|---|
|accessToken	|用户授权令牌|

请求示例：
> http://localhost/nggirl/app//cli/works/getReservationNum/1.0

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
