# 积分商城V2.5.3


* [1.获取积分商城banner列表V2.5.2](#1)
* [2.获取商品列表V2.5.3](#2)
* [3.获取商品详情V2.5.3](#3)
* [4.获取兑换记录V2.5.3](#4)
* [5.确认兑换V2.5.3](#5)
* [6.获取兑换详情V2.5.3](#6)
* [7.获取积分商城banner历史列表V2.5.2](#7)
* [8.获取用户收货地址V2.5.2](#8)
* [9.确认地址V2.5.2](#9)




<h2 id="1">1.获取banner列表V2.5.2</h2>

请求方法：nggirl/app/cli/scoreshop/listHeadScroll/2.5.2

请求URL：接口地址/nggirl/app/cli/scoreshop/listHeadScroll/2.5.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：无

请求示例：

> http://localhost/nggirl/app/cli/scoreshop/listHeadScroll/2.5.2?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0

返回结果示例：

```json
{
   "code": 0,
    "data":[
      {
      "headScrollId":1,
  	  "photoUrl": " http://www.baidu.com/1.jpg",
  		"webpageUrl":"http://www.nggirl.com.cn",
  		"shareContent":"cosm大赏，美美的彩妆品",
  		"shareImage":"http://www.baidu.com/2.jpg",
      "forwardtype":"coupon",
      "forwardkey":""
    	},
    	{
      "headScrollId":2,
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
|Data - headScrollId	|轮播头图编号
|Data - photoUrl	|显示的图片路径
|Data - webpageUrl	|跳转到的web页面链接地址
|Data - shareContent |分享描述内容
|Data - shareImage	|分享出去的小图（1:1小图片），替代之前的logo
|Data - forwardtype	|跳转类型
|Data - forwardkey	|跳转参数

<h2 id="2">2.获取商品列表V2.5.3</h2>

请求方法：nggirl/app/cli/scoreshop/getGoodsList/2.5.3

请求URL：接口地址/nggirl/app/cli/scoreshop/getGoodsList/2.5.3

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken|[必填]授权令牌
|pageNum|页数，默认为0（选填）
|pageSize|每页大小，默认10（选填）


请求示例：

> http://localhost/nggirl/app/cli/scoreshop/getGoodsList/2.5.3

返回结果示例：
```json
{
  "code":0,
  "data":{
    "userScore":200,
    "goodsList":[
      {
        "goodsId":1,
        "goodsType":0,
        "name":"南瓜洗面奶",
        "picture":"http://testphotosd.nggirl.com.cn/sysres/dressTypeImage/makeup-list-2.png",
        "costScore":200,
        "fitUserLevel":1
      },
      {
        "goodsId":2,
        "goodsType":1,
        "name":"补签卡",
        "picture":"http://testphotosd.nggirl.com.cn/sysres/dressTypeImage/makeup-list-2.png",
        "costScore":300,
        "fitUserLevel":1
      }
    ]
  }
}
```

返回字段说明：


|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - userScore|用户当前积分|
|Data - goodsList|兑换商品列表|
|Data - goodsList - goodsId|商品编号|
|Data - goodsList - goodsType|商品类型：0普通商品，1补签卡，2第三方兑换码商品|
|Data - goodsList - name|商品名称|
|Data - goodsList - picture|商品配图|
|Data - goodsList - costScore|花费积分|
|Data - goodsList - fitUserLevel|商品适用用户等级：0Lv0以上，1Lv1以上，2Lv2以上...|



<h2 id="3">3.获取商品详情V2.5.3</h2>

> 入参增加orderId, 添加返回字段thirdCode,instructions-type,instructions-content,instructions-descrip,instructions-extend

请求方法：nggirl/app/cli/scoreshop/getGoodsDetail/2.5.3

请求URL：接口地址/nggirl/app/cli/scoreshop/getGoodsDetail/2.5.3

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken|[非必填]授权令牌，登录时必填
|orderId|订单编号，从兑换记录进来时必填|
|goodsId|[必填]商品编号
|goodsType|[必填]商品类型，0普通商品，1补签卡，2第三方兑换码商品


请求示例：

> http://localhost/nggirl/app/cli/scoreshop/getGoodsDetail/2.5.3

返回结果示例：

```json
{
  "code":0,
  "data":{
    "userScore":9000,
    "userRole":"南瓜用户",
    "userLevel":1,
    "unionGoodsId":1,
    "goodsId":1,
    "goodsType":0,
    "name":"南瓜家洗面年",
    "headImg":"http://testphotosd.nggirl.com.cn/sysres/dressTypeImage/makeup-list-2.png",
    "shareImg":"http://testphotosd.nggirl.com.cn/sysres/dressTypeImage/makeup-list-2.png",
    "storeNum":20,
    "costScore":1000,
    "freight":0,
    "startTime":1473672586540,
    "endTime":1473672586540,
    "exchangeTime":2,
    "fitType":0,
    "fitUserRole":"南瓜小编,客座小编",
    "fitUserLevel":0,
    "status":1,
    "isScoreEnough":1,
    "isLeverHigh":0,
    "isFitUserRole":1,
    "isExchanged":0,
    "thirdCode":"kufdsfds",
    "goodsDetail":[
      {
        "type":2,
        "content":"hahhahahhaha",
        "descrip":"",
        "extend":""
      },
      {
        "type":3,
        "content":"http://testphotosd.nggirl.com.cn/sysres/dressTypeImage/makeup-list-2.png",
        "descrip":"",
        "extend":"640_320"
      }
    ], 
    "instructions":[
      {
        "type":2,
        "content":"hahhahahhaha",
        "descrip":"",
        "extend":""
      },
      {
        "type":3,
        "content":"http://testphotosd.nggirl.com.cn/sysres/dressTypeImage/makeup-list-2.png",
        "descrip":"",
        "extend":"640_320"
      }
    ]
  }
}
```

返回字段说明:

|字段名称|字段含义|
|-----|-----|
|Code|错误标识码，0表示正确|
|Data - userScore|用户当前积分|
|Data - userLevel|用户等级 0Lv0,1Lv1,2Lv2....|
|Data - userRole|用户角色|
|Data - unionGoodsId|商品联合编号|
|Data - goodsId|商品编号|
|Data - goodsType|商品类型：0普通商品，1补签卡,2第三方兑换码商品|
|Data - name|商品名称|
|Data - shareImg|商品分享图|
|Data - headImg|商品详情头图|
|Data - storeNum|库存数量|
|Data - costScore|需要花费积分|
|Data - freight|邮费：0表示包邮|
|Data - startTime|兑换开始时间|
|Data - endTime|兑换结束时间|
|Data - exchangeTime|每个用户允许兑换次数|
|Data - fitType|适用类型：0或，1与|
|Data - fitUserRole|适用人群（所有用户，南瓜小编，客座小编，南瓜CEO）|
|Data - fitUserLevel|适用用户等级，0Lv0以上，1Lv1以上，2Lv2以上...|
|Data - status|商品状态：1还未开始兑换,2库存不足,3可兑换,4兑换活动时间结束|
|Data - isScoreEnough|积分是否足够兑换此商品：0不足，1足够|
|Data - isLeverHigh|用户等级是否足够高兑换此商品：0不足，1足够|
|Data - isFitUserRole|该用户角色是否适用于此商品：0不适用，1适用|
|Data - isExchanged|该用户是否已兑换此商品：0未兑换，1已兑换|
|Data - thirdCode|兑换码|
|Data - goodsDetail - type|商品详情-类型：2段落，3图片|
|Data - goodsDetail - content|商品详情-内容：2段落内容，3图片url|
|Data - goodsDetail - descrip|商品详情-描述：空|
|Data - goodsDetail - extend|商品详情-扩充字段，2空，3图片宽_高|
|Data - instructions - type|使用说明-类型：2段落，3图片|
|Data - instructions - content|使用说明-内容：2段落内容，3图片url|
|Data - instructions - descrip|使用说明-描述：空|
|Data - instructions - extend|使用说明-扩充字段，2空，3图片宽_高|



<h2 id="4">4.获取兑换记录V2.5.3</h2>

> 返回字段增加orderId

请求方法：nggirl/app/cli/scoreshop/getExchangeRecord/2.5.3

请求URL：接口地址/nggirl/app/cli/scoreshop/getExchangeRecord/2.5.3

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken|[必填]授权令牌|
|pageNum|页数，默认为0（选填）
|pageSize|每页大小，默认10（选填）


请求示例：

> http://localhost/nggirl/app/cli/scoreshop/getExchangeRecord/2.5.3

返回结果示例：

```json
{
  "code":0,
  "data":[
    {
      "orderId":2016091445739129,
      "goodsId":1,
      "goodsType":1,
      "name":"南瓜家洗面奶",
      "picture":"http://testphotosd.nggirl.com.cn/sysres/dressTypeImage/makeup-list-2.png",
      "costScore":1000
    },
    {
      "orderId":2016091445739129,
      "goodsId":2,
      "goodsType":1,
      "name":"南瓜家洗面奶",
      "picture":"http://testphotosd.nggirl.com.cn/sysres/dressTypeImage/makeup-list-2.png",
      "costScore":1000
    }
  ]
}
```

返回结果说明：

|字段名称|字段含义|
|-----|-----|
|Code|错误码标识，0标识正确|
|Data - orderId|订单编号|
|Data - goodsId|商品编号|
|Data - goodsType|商品类型：0普通商品，1补签卡,2第三方兑换码|
|Data - name|商品名称|
|Data - picture|商品配图|
|Data - costScore|兑换商品所花费积分|




<h2 id="5">5.确认兑换V2.5.3</h2>

> 去除入参exchangeTime，返回字段增加orderId

请求方法：nggirl/app/cli/scoreshop/commitExchange/2.5.3

请求URL：接口地址/nggirl/app/cli/scoreshop/commitExchange/2.5.3

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken|[必填]授权令牌
|unionGoodsId|商品联合编号|
|goodsId|商品编号|
|goodsType|商品类型：0普通商品，1补签卡，2第三方兑换码商品|
|costScore|商品所需花费积分|
|freight|邮费，默认为0，表示包邮|
|realName|用户姓名|
|address|邮寄地址|
|phoneNum|用户手机号|
|remark|备注|



请求示例：

> http://localhost/nggirl/app/cli/scoreshop/commitExchange/2.5.3

返回结果示例：

```json
{
  "code":0,
  "data":{
    "orderId":"20165589655455"
  }
}
```

返回结果说明：

|字段名称|字段含义|
|---|---|
|Code|错误标识码，0表示正确|
|Data - orderId|订单编号|




<h2 id="6">6.获取兑换详情V2.5.3</h2>

>入参增加orderId, 添加返回字段thirdCode,instructions-type,instructions-content,instructions-descrip,instructions-extend,

请求方法：nggirl/app/cli/scoreshop/getExchangeDetail/2.5.3

请求URL：接口地址/nggirl/app/cli/scoreshop/getExchangeDetail/2.5.3

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken|[必填]授权令牌
|orderId|订单编号|
|goodsId|商品编号|
|goodsType|商品类型：0普通商品，1补签卡,2第三方兑换码商品|



请求示例：

> http://localhost/nggirl/app/cli/scoreshop/getExchangeDetail/2.5.3

返回结果示例：

```json
{
  "code":0,
  "data":{
    "goodsId":1,
    "goodsType":1,
    "name":"南瓜家洗面奶",
    "headImg":"http://testphotosd.nggirl.com.cn/sysres/dressTypeImage/makeup-list-2.png",
    "shareImg":"http://testphotosd.nggirl.com.cn/sysres/dressTypeImage/makeup-list-2.png",
    "storeNum":200,
    "costScore":200,
    "freight":0,
    "startTime":,
    "endTime":,
    "thirdCode":"kuhyfbt",
    "goodsDetail":[
      {
        "type":2,
        "content":"hahhahahhaha",
        "descrip":"",
        "extend":""
      },
      {
        "type":3,
        "content":"http://testphotosd.nggirl.com.cn/sysres/dressTypeImage/makeup-list-2.png",
        "descrip":"",
        "extend":"640_320"
      }
    ],
    "instructions":[
      {
        "type":2,
        "content":"hahhahahhaha",
        "descrip":"",
        "extend":""
      },
      {
        "type":3,
        "content":"http://testphotosd.nggirl.com.cn/sysres/dressTypeImage/makeup-list-2.png",
        "descrip":"",
        "extend":"640_320"
      }
    ]
    
  }
}
```

返回结果说明：

|字段名称|字段含义|
|---|---|
|Code|错误标识码，0表示正确|
|Data - goodsId|商品编号|
|Data - goodsType|商品类型：0普通商品，1补签卡|
|Data - name|商品名称|
|Data - headImg|详情头图|
|Data - shareImg|商品分享图|
|Data - storeNum|商品库存|
|Data - costScore|商品兑换所需花费积分|
|Data - freight|邮费：0表示包邮|
|Data - startTime|兑换开始时间|
|Data - endTime|兑换结束时间|
|Data - thirdCode|兑换码|
|Data - goodsDetail - type|商品详情-类型：2段落，3图片|
|Data - goodsDetail - content|商品详情-内容：2段落内容，3图片url|
|Data - goodsDetail - descrip|商品详情-描述：空|
|Data - goodsDetail - extend|商品详情-扩充字段，2空，3图片宽_高|
|Data - instructions - type |使用说明-类型：2段落，3图片|
|Data - instructions - content|使用说明-内容：2段落内容，3图片url|
|Data - instructions - descrip|使用说明-描述：空|
|Data - instructions - extend|使用说明-扩充字段，2空，3图片宽_高|



<h2 id="7">7.获取积分商城banner历史列表V2.5.2</h2>

请求方法：nggirl/app/cli/scoreshop/headScrollHistory/2.5.2

请求URL：接口地址/nggirl/app/cli/scoreshop/headScrollHistory/2.5.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|page	|页数  非必需参数，默认第一页
|num	|每页信息数目 非必需参数，默认20


请求示例：

> http://localhost/nggirl/app/cli/scoreshop/headScrollHistory/2.5.2?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

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





<h2 id="8">8.获取用户收货地址V2.5.2</h2>

请求方法：nggirl/app/cli/scoreshop/getUserReciveAddess/2.5.2

请求URL：接口地址/nggirl/app/cli/scoreshop/getUserReciveAddess/2.5.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义
|---|---|
|accessToken|[必填]授权令牌|

请求示例：

>  localhost:/nggirl/app/cli/scoreshop/getUserReciveAddess/2.5.2

 返回结果示例：

 ```json
 {
 	"code":0,
 	"data":{
 		"userId":269,
 		"realName":"tom",
 		"phoneNum":"18516993208",
 		"address":"SOhojiashengzhongxin2006"
 	}
 }
 ```

返回字段说明：

| 字段名称 | 字段含义 |
|----|----|
|userId|用户编号 |
|realName| 真实姓名 |
|phoneNum| 用户手机号 |
|address| 收货地址 |


<h2 id="9">9.确认地址V2.5.2</h2>

请求方法：nggirl/app/cli/scoreshop/confirmAddress/2.5.2

请求URL：接口地址/nggirl/app/cli/scoreshop/confirmAddress/2.5.2

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义
|---|---|
|accessToken|[必填]授权令牌
|realName|[必填] 真实姓名 |
|phoneNum|[必填] 用户手机号 |
|address|[必填] 收货地址 |

请求示例：

>  localhost:/nggirl/app/cli/scoreshop/confirmAddress/2.5.2

 返回结果示例：

 ```json
 {
 	"code":0,
 	"data":null
 }
 ```
 
 
