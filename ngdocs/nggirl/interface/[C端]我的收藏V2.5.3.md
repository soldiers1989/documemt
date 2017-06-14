# 我的收藏V2.5.3

* [1. 对帖子的收藏、取消收藏V2.5.3](#1)
* [2. 对帖子的喜欢、取消喜欢V2.5.3](#2)
* [3. 收藏的帖子列表](#3)
* [4. 收藏的作品列表](#4)


<h2 id="1">1. 对帖子的收藏、取消收藏V2.5.3</h2>

>出参增加addScore字段

请求方法：nggirl/app/cli/column/collectPost/2.5.3

请求URL：接口地址/nggirl/app/cli/column/collectPost/2.5.3

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken|授权令牌（必填）
|postId|帖子id（必填）
|postType|帖子类型（必填）
|flag|标志，0为取消收藏，1为收藏（必填）|


请求示例：

> http://localhost/nggirl/app/cli/column/collectPost/2.5.3

返回结果示例：
```json
{
  "code": 0,
  "data": {
    "addScore":1
  }
}
```
返回字段说明：


|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|Data - addScore|用户本次操作增加的积分数|

<h2 id="2">2. 对帖子的喜欢、取消喜欢V2.5.3</h2>

>出参增加addScore字段

请求方法：nggirl/app/cli/column/praisePost/2.5.3

请求URL：接口地址/nggirl/app/cli/column/praisePost/2.5.3

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken|授权令牌（必填）
|postId|帖子id（必填）
|postType|帖子类型（必填）
|flag|标志，0为取消点赞，1为点赞（必填）|


请求示例：

> http://localhost/nggirl/app/cli/column/praisePost/2.5.3

返回结果示例：
```json
{
  "code": 0,
  "data": {
    "addScore":1
  }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|Data - addScore|用户本次操作增加的积分数|


<h2 id="3">3. 收藏的帖子列表</h2>


请求方法：nggirl/app/cli/personalInfo/collect/listColumnPost/2.0.0

请求URL：接口地址/nggirl/app/cli/personalInfo/collect/listColumnPost/2.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken|授权令牌（必填）
|pageSize|每页大小，默认20（选填）
|pageNum|页数，默认为0（选填）


请求示例：

> http://localhost/nggirl/app/cli/personalInfo/collect/listColumnPost/2.0.0

返回结果示例：
```json
{
    "code": 0,
  	"data": [
  	 {
  	   "postId":231,
  	   "postType":1,
  	   "title":"教你如何3分钟做出好发型",
  	   "picture":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
  	   "viewNum":998,
  	   "commentNum":1000
  	 },{
  	   "postId":231,
  	   "postType":1,
  	   "title":"教你如何3分钟做出好发型",
  	   "picture":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
  	   "viewNum":998,
  	   "commentNum":1000
  	 },{
  	   "postId":231,
  	   "postType":1,
  	   "title":"教你如何3分钟做出好发型",
  	   "picture":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
  	   "viewNum":998,
  	   "commentNum":1000
  	 }
	]
}
```
返回字段说明：


|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - postId|	帖子id
|Data - postType	|帖子类型，1为文章，2为视频
|Data - title	|帖子标题
|Data - picture|	帖子封面图
|Data - viewNum|	浏览数
|Data - commentNum|	评论数




<h2 id="4">4. 收藏的作品列表</h2>

请求方法：nggirl/app/cli/personalInfo/collect/listWork/2.0.0

请求URL：接口地址/nggirl/app/cli/personalInfo/collect/listWork/2.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken|授权令牌（必填）
|pageSize|每页大小，默认20（选填）
|pageNum|页数，默认为0（选填）


请求示例：

> http://localhost/nggirl/app/cli/personalInfo/collect/listWork/2.0.0

返回结果示例：
```json
{
    "code": 0,
  	"data": [
  	 {
  	    "workId": 766,
        "cover": null,
        "content": null,
        "likeNum": 0,
        "resNum": 17,
        "ornament": "http://testphotosd.nggirl.com.cn/sysres/dressTypeImage/makeup-list-2.png",
        "cost": 170,
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
  	     "workId": 766,
          "cover": null,
            "content": null,
            "likeNum": 0,
            "resNum": 17,
            "ornament": "http://testphotosd.nggirl.com.cn/sysres/dressTypeImage/makeup-list-2.png",
            "cost": 170,
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
  	      "workId": 766,
          "cover": null,
           "content": null,
            "likeNum": 0,
            "resNum": 17,
            "ornament": "http://testphotosd.nggirl.com.cn/sysres/dressTypeImage/makeup-list-2.png",
            "cost": 170,
            "hasDiscount": 0,
             "discount":{
                "id":1,
                "workId":123,
                "name":"首单五折",
                "desc":"新用户首次下单五折优惠，还可叠加使用优惠券",
                "cost":50,
                "icon":"http://testphotosd.nggirl.com.cn/work/aee4e7c292094a24a72ac8da401bbd7d.png"
          }
  	 }
	]
}
```
返回字段说明：


|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - workId|	作品id
|Data - cover|	作品封面
|Data - content|	作品名称
|Data - likeNum	|喜欢的人总数
|Data - resNum	|预约人数
|Data - ornament|	装饰图
|Data - cost|	作品价格
|Data -hasDiscount|	专题作品是否有折扣
|Data discount - id|	折扣活动编号
|Data discount - workId|	参与活动的作品编号
|Data discount - name	|活动名称，显示在作品的活动栏（红底部分）
|Data discount - desc|	活动描述，显示在作品的活动栏
|Data discount - cost|	参与活动后的价格
|Data discount - icon|	活动的图标，用于放在作品的图片右上角
|Data discount - allow|	该用户是否可享受该活动，0为否，1为是
