# 化妆师主页接口V2.5.3


* [1.上门美妆列表](#1)
* [2.美妆沙龙列表](#2)
* [3.服务实拍列表](#3)
* [4.喜欢化妆师的实拍、取消喜欢实拍V2.5.3](#4)
* [5.对上门美妆评价列表](#5)
* [6.对美妆沙龙评价列表](#6)



<h2 id="1">1.上门美妆列表</h2>

> 获取某一化妆师所有作品列表

请求方法：nggirl/app/cli/dresser/listWork/1.5.0

请求URL：接口地址/nggirl/app/cli/dresser/listWork/1.5.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|dresserId|化妆师id（必填）
|pageNum|第几页，默认为0（选填）|
|pageSize|每页大小，默认20页（选填）|

请求示例：

> http://localhost/nggirl/app/cli/dresser/listWork/1.5.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&dresserId=120&pageNum=1&pageSize=20

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
            "discount": {
                "id": null,
                "workId": 766,
                "name": null,
                "desc": null,
                "icon": null,
                "cost": null,
                "allow": null
            }
        },
        {
            "workId": 783,
            "cover": null,
            "content": null,
            "likeNum": 1,
            "resNum": 5,
            "ornament": "http://testphotosd.nggirl.com.cn/sysres/dressTypeImage/makeup-list-2.png",
            "cost": 130,
            "hasDiscount": 0,
            "discount": {
                "id": null,
                "workId": 783,
                "name": null,
                "desc": null,
                "icon": null,
                "cost": null,
                "allow": null
            }
        }
    ]
}
```
返回字段说明：


|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - workId	|作品id
|Data - cover	|作品封面
|Data - content	|作品名称
|Data - likeNum	|喜欢的人总数
|Data - resNum	|预约人数
|Data - ornament|装饰图
|Data - cost|作品价格
|Data -hasDiscount	|专题作品是否有折扣
|Data  discount - id|折扣活动编号
|Data  discount - workId|参与活动的作品编号
|Data  discount - name|活动名称，显示在作品的活动栏（红底部分）
|Data  discount - desc|活动描述，显示在作品的活动栏
|Data  discount - cost|参与活动后的价格
|Data  discount - icon|活动的图标，用于放在作品的图片右上角
|Data  discount - allow|该用户是否可享受该活动，0为否，1为是


<h2 id="2">2.美妆沙龙列表</h2>

> 获取某一化妆师的所有沙龙活动
> 与之前沙龙列表比。去掉sex字段

请求方法：nggirl/app/cli/dresser/listSalon/1.5.0

请求URL：接口地址/nggirl/app/cli/dresser/listSalon/1.5.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|pageNum|第几页，默认为0（选填）|
|pageSize|每页大小，默认20页（选填）|
|dresserId|化妆师id（必填）

请求示例：

> http://nggirl/app/cli/dresser/listSalon/1.5.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&pageNum=0&pageSize=20&dresserId=120

返回结果示例：

```json
{
    "code": 0,
    "data":[
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
|Data - starLevel|化妆师星级
|Data - holdTime|活动时间 格式：”2015.12.10 13:00-17:00“
|Data - holdPlace|活动地点



<h2 id="3">3.服务实拍列表</h2>

> 获取某一化妆师所有服务实拍列表

请求方法：nggirl/app/cli/dresser/listPost/1.5.0

请求URL：接口地址/nggirl/app/cli/dresser/listPost/1.5.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken|授权令牌（选填）|
|pageNum|第几页，默认为0（选填）|
|pageSize|每页大小，默认20页（选填）|
|dresserId|化妆师id(必填)

请求示例：

> http://localhost/nggirl/app/cli/dresser/listPost/1.5.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&dresserId=12

返回结果示例：

```json
{
    "code": 0,
	"data": [
	    {
    		"postId":1,
	    	 "descrip":"这是服务实拍的描述",
	    	 "publishTime":123345344443,
	    	 "likeNum":343,
	    	 "isLiked":0,
	    	 "photoList":[
	    	         {
	    	          "photoUrl":"http://photosd.nggirl.com.cn/work/40a797b2614e4a13819197bc981ae1cf.jpg",
	    	          "width":600,
	    	          "height":800
	    	          },
	    	          {
	    	           "photoUrl":"http://photosd.nggirl.com.cn/work/6731161484d049d4909de64ce870819f.jpg",
	    	           "width":650,
	    	           "height":800
	    	          }
	    	   ]
    	    }, {
    	  	 "postId":1,
	    	 "descrip":"这是服务实拍的描述",
	    	 "publishTime":123345344443,
	    	 "likeNum":343,
	    	 "isLiked":0,
	    	 "photoList":[
	    	         {
	    	          "photoUrl":"http://photosd.nggirl.com.cn/work/40a797b2614e4a13819197bc981ae1cf.jpg",
	    	          "width":600,
	    	          "height":800
	    	          },
	    	          {
	    	           "photoUrl":"http://photosd.nggirl.com.cn/work/6731161484d049d4909de64ce870819f.jpg",
	    	           "width":650,
	    	           "height":800
	    	          }
	    	   ]
    	   },{
    	         "postId":1,
	    	 "descrip":"这是服务实拍的描述",
	    	 "publishTime":123345344443,
	    	 "likeNum":343,
	    	 "isLiked":0,
	    	 "photoList":[
	    	         {
	    	          "photoUrl":"http://photosd.nggirl.com.cn/work/40a797b2614e4a13819197bc981ae1cf.jpg",
	    	          "width":600,
	    	          "height":800
	    	          },
	    	          {
	    	           "photoUrl":"http://photosd.nggirl.com.cn/work/6731161484d049d4909de64ce870819f.jpg",
	    	           "width":650,
	    	           "height":800
	    	          }
	    	   ]
    	   }]
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - postId	|实拍id
|Data - descrip	|实拍描述
|Data - publishTime	|发布时间
|Data - likeNum	|喜欢人数
|Data - isLiked	|是否标记喜欢过，1为是，0为否
|Data - photoList-photoUrl|实拍图片url
|Data - photoList-width|实拍图片宽度
|Data - photoList-height|实拍图片高度


<h2 id="4">4.喜欢化妆师的实拍、取消喜欢实拍V2.5.3</h2>

>出参增加addScore字段

请求方法：nggirl/app/cli/dresser/likePost/2.5.3

请求URL：接口地址/nggirl/app/cli/dresser/likePost/2.5.3

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken|授权令牌(必填)
|postId|实拍id(必填)
|isLike|1为点赞，0为取消点赞(必填)

请求示例：

> http://localhost/nggirl/app/cli/dresser/likePost/2.5.3?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&postId=12&isLike=1

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

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确|
|Data - addScore|用户本次操作增加的积分数|


<h2 id="5">5.对上门美妆评价列表</h2>

> 获取用户对某一化妆师上门美妆的所有评价

请求方法：nggirl/app/cli/dresser/evaluate/listWork/1.5.0

请求URL：接口地址/nggirl/app/cli/dresser/evaluate/listWork/1.5.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|pageNum|第几页，默认为0（选填）|
|pageSize|每页大小，默认20页（选填）|
|dresserId|化妆师id

请求示例：

> http://localhost/nggirl/app/cli/dresser/evaluate/listWork/1.5.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&dresserId=12

返回结果示例：

```json
{
    "code":0,
    "data":[
       {
        "evaluateUserId":290,
        "evaluateName":"小明",
        "userProfile":"http://photosd.nggirl.com.cn/work/1d0a39d01c71431292b0d46de3723b74.jpg",
        "workName":"约会装",
        "evaluateContent":"真的很好",
        "evaluateTime":343434556,
        "evaluateStar":4,
        "photoList":[
                  {
                   "photoUrl":"http://photosd.nggirl.com.cn/work/40a797b2614e4a13819197bc981ae1cf.jpg",
                   "width":500,
                   "height":800
                   },{
    	           "photoUrl":"http://photosd.nggirl.com.cn/work/40a797b2614e4a13819197bc981ae1cf.jpg",
                   "width":500,
                   "height":800
    	          }
                ]
        }, {
        "evaluateUserId":291,
        "evaluateName":"小明",
        "userProfile":"http://photosd.nggirl.com.cn/work/1d0a39d01c71431292b0d46de3723b74.jpg",
        "workName":"约会装",
        "evaluateContent":"真的很好",
        "evaluateTime":343434556,
        "evaluateStar":4,
        "photoList":[
                  {
                   "photoUrl":"http://photosd.nggirl.com.cn/work/40a797b2614e4a13819197bc981ae1cf.jpg",
                   "width":500,
                   "height":800
                   },{
    	           "photoUrl":"http://photosd.nggirl.com.cn/work/40a797b2614e4a13819197bc981ae1cf.jpg",
                   "width":500,
                   "height":800
    	          }
                ]
        }
   ]
}
```


返回字段说明：

|字段名|字段含义|
|---|---|
|Code|	错误码，0表示正确
|Data - evaluateUserId|	用户编号
|Data - evaluateName	|用户名
|Data - userProfile |	头像路径
|Data - evaluateContent|	评价内容
|Data - evaluateTime	|评论时间
|Data - workName|装束名称
|Data - evaluateStar|评价星级
|Data - photoList-photoUrl|图片url
|Data - photoList-width|图片宽度
Data - photoList-height|图片高度




<h2 id="6">6.对美妆沙龙评价列表</h2>

> 获取用户对某一化妆师美妆沙龙的所有评价

请求方法：nggirl/app/cli/dresser/evaluate/listSalon/1.5.0

请求URL：接口地址/nggirl/app/cli/dresser/evaluate/listSalon/1.5.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|pageNum|第几页，默认为0（选填）|
|pageSize|每页大小，默认20页（选填）|
|dresserId|化妆师id

请求示例：

> http://localhost/nggirl/app/cli/dresser/evaluate/listSalon/1.5.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&accessToken=5db6ad15a16d3424845adb1ab8172e42066120f0&dresserId=12

返回结果示例：

```json
{
    "code":0,
    "data":[
       {
        "evaluateUserId":290,
        "evaluateName":"小明",
        "userProfile":"http://photosd.nggirl.com.cn/work/1d0a39d01c71431292b0d46de3723b74.jpg",
        "workName":"小白专场",
        "evaluateContent":"真的很好",
        "evaluateTime":343434556,
        "evaluateStar":4,
        "photoList":[
                  {
                   "photoUrl":"http://photosd.nggirl.com.cn/work/40a797b2614e4a13819197bc981ae1cf.jpg",
                   "width":500,
                   "height":800
                   },{
    	           "photoUrl":"http://photosd.nggirl.com.cn/work/40a797b2614e4a13819197bc981ae1cf.jpg",
                   "width":500,
                   "height":800
    	          }
                ]
        },
        {
        "evaluateUserId":290,
        "evaluateName":"小白专场",
        "userProfile":"http://photosd.nggirl.com.cn/work/1d0a39d01c71431292b0d46de3723b74.jpg",
        "workName":"约会装",
        "evaluateContent":"真的很好",
        "evaluateTime":343434556,
        "evaluateStar":4,
        "photoList":[
                  {
                   "photoUrl":"http://photosd.nggirl.com.cn/work/40a797b2614e4a13819197bc981ae1cf.jpg",
                   "width":500,
                   "height":800
                   },{
    	           "photoUrl":"http://photosd.nggirl.com.cn/work/40a797b2614e4a13819197bc981ae1cf.jpg",
                   "width":500,
                   "height":800
    	          }
              ]
        }
   ]
}
```


返回字段说明：

|字段名|字段含义|
|---|---|
|Code|	错误码，0表示正确
|Data - evaluateUserId|	用户编号
|Data - evaluateName	|用户名
|Data - userProfile |	头像路径
|Data - evaluateContent|	评价内容
|Data - evaluateTime	|评论时间
|Data - workName|活动名称
|Data - evaluateStar|评价星级
|Data - photoList-photoUrl|图片url
|Data - photoList-width|宽度
|Data - photoList-height|高度
