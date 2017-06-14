<h1>微信端作品接口V1.3.2</h1>

目录

* [1. 获取某类型的所有作品（分页）](#1)
* [2. 根据条件查询作品（分页）](#2)
* [3. 获取作品详情](#3)
* [4. 获取微信首页作品类型列表](#4)
* [5. 模糊查询化妆师](#5)
* [6. 模糊查询作品](#6)
* [7. 我要预约-婚博会专场](#7)
* [8. 我要预约-直接接单](#8)
* [9. 我要预约-普通预约(预约日期增加到三十天)V1.3.2](#9)
* [10.取消预约(预约日期增加到三十天)V1.3.2](#10)
* [11.获取可预约时间(预约日期增加到三十天)V1.3.2](#11)
<h2 id="1">1. 获取某类型的所有作品（分页）</h2>

> 依据给定的workType返回属于该作品类型的所有作品
> 用于微信端按关键字查询出作品部分后的查看更多

请求方法：nggirl/app/cli/works/weixin/listWorksByType

请求URL:接口地址/nggirl/app/cli/works/weixin/listWorksByType

支持格式：JSON

HTTP请求：POST

|参数名称|参数含义
|---|---|
|workType|（字符串）作品类型
|page|（int）页数，非必须参数，默认第一页
|num|(int)每页条数，非必须参数，默认20

请求实例：

> http://localhost:8080/nggirl/app/cli/works/weixin/listWorksByType

返回结果示例：

```json
{
    "code": 0
    "data":[{
    	        "workId": 1234567,
            	"cover":"http://www.baidu.com/1.jpg",
            	"workType":"职业装",
            	"cost":100,
            	"descriptions":"肤质较佳的女生。强调重点：强调眼唇重点。以润色隔离霜作为底妆，然后以睫毛膏……",
            	 "hasDiscount": 1,
            	 "discount":{
                        "id":1,
                        "workId":123,
                        "name":"首单五折",
                        "desc":"新用户首次下单五折优惠，还可叠加使用优惠券",
                        "cost":50,
                        "icon":"http://testphotosd.nggirl.com.cn/work/aee4e7c292094a24a72ac8da401bbd7d.png"
                        },
            	"tags": [
                      {
                    "tagId": 1,
                    "workId": 382,
                    "tag": "欧美风"
                      }
                       ]
        	},
        	{
            	"workId": 1234567,
            	"cover":"http://www.baidu.com/1.jpg",
            	"workType":"职业装",
            	"cost":100,
            	"descriptions":"肤质较佳的女生。强调重点：强调眼唇重点。以润色隔离霜作为底妆，然后以睫毛膏…….",
            	 "hasDiscount": 1,
            	 "discount":{
                        "id":1,
                        "workId":123,
                        "name":"首单五折",
                        "desc":"新用户首次下单五折优惠，还可叠加使用优惠券",
                        "cost":50,
                        "icon":"http://testphotosd.nggirl.com.cn/work/aee4e7c292094a24a72ac8da401bbd7d.png"
                        },
            	"tags": [
                      {
                    "tagId": 3683,
                    "workId": 365,
                    "tag": "赫本"
                },
                {
                    "tagId": 3684,
                    "workId": 365,
                    "tag": "韩式公主"
                },
                {
                    "tagId": 3685,
                    "workId": 365,
                    "tag": "小清新"
                }
                       ]
               }]
}
```

返回字段说明：

|字段名称|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - workId	|作品编号
|Data - cover	|封面图片路径
|Data - workType|作品类型
|Data - cost	|费用
|Data - descriptions|作品描述
|Data - tags-tagId|标签id
|Data -tags-workId|标签的作品id
|Data - tags-tag|标签
|Data - hasDiscount|此作品是否参与了折扣活动，0没有，1有
|Data - discount - id|活动编号
|Data - discount - workId|参与活动的作品编号
|Data - discount - name|活动名称，显示在作品的活动栏（红底部分）
|Data - discount - desc|活动描述，显示在作品的活动栏
|Data - discount - cost|参与活动后的价格
|Data - discount - icon|活动的图标，用于放在作品的图片右上角



<h2 id="2">2.  根据条件查询作品（分页）</h2>

> 作品模糊查询。依据给定的key匹配作品的标签、类型、描述文字中的内容。
> 分别返回作品和化妆师两组信息，每组信息各返回不多于3条的数据。
> 用于微信端的搜索

请求方式:nggirl/app/cli/works/weixin/listInfoByKey

请求URL: 接口地址/nggirl/app/cli/works/weixin/listInfoByKey

支持格式：JSON

HTTP请求：POST

|参数名称|参数含义
|---|---|
|key|关键字|


请求实例：

> http://localhost:8080/nggirl/app/cli/works/weixin/listInfoByKey

返回结果示例：

```json
{
    "code": 0,
    "data": {
        "dressers": {
            "hasMore": 1,
            "data": [
                {
                    "dresserId": 60,
                    "dresserName": "郭宏斌",
                    "orderNum": 219,
                    "workType": [
                        "大片写真",
                        "特殊造型",
                        "约会妆",
                        "职业妆",
                        "VIP妆"
                    ],
                    "profile": "http://testphotosd.nggirl.com.cn/work/422da5cf651f4ddcb131d5d07bcee4cb.jpg",
                    "authentication": 1,
                    "starLevel": 5,
                    "isVDresser": 0
                },
                {
                    "dresserId": 56,
                    "dresserName": "薛熠敏",
                    "orderNum": 42,
                    "workType": [
                        "新娘妆",
                        "约会妆",
                        "特殊造型",
                        "VIP 妆"
                    ],
                    "profile": "http://testphotosd.nggirl.com.cn/work/e7a3d1bc97eb408abffcffe119a17f2d.jpg",
                    "authentication": 1,
                    "starLevel": 4,
                    "isVDresser": 0
                },
                {
                    "dresserId": 59,
                    "dresserName": "于鑫",
                    "orderNum": 95,
                    "workType": [
                        "年会妆",
                        "大片写真",
                        "约会妆",
                        "晚妆",
                        "亲子摄影妆"
                    ],
                    "profile": "http://testphotosd.nggirl.com.cn/work/1da701173ac84d6ca616de29159e58e4.png",
                    "authentication": 1,
                    "starLevel": 4,
                    "isVDresser": 0
                }
            ]
        },
        "works": {
            "hasMore": 1,
            "data": [
                {
                    "workId": 209,
                    "cover": "http://photosd.nggirl.com.cn/work/b5c257e152734477a1ba2c9a7f934f73.jpg",
                    "workType": "约会妆",
                    "cost": 1,
                    "descriptions": "清新自然，减龄卧蚕妆，微信电力十足约会必备呦！QQ",
                    "tags": [
                        {
                            "tagId": 1,
                            "workId": 209,
                            "tag": "韩式公主"
                        },
                        {
                            "tagId": 1,
                            "workId": 209,
                            "tag": "小清新"
                        },
                        {
                            "tagId": 1,
                            "workId": 209,
                            "tag": "森女"
                        }
                    ]
                },
                {
                    "workId": 211,
                    "cover": "http://photosd.nggirl.com.cn/work/bb57050e9c4f454c91c30986210ecf25.jpg",
                    "workType": "约会妆",
                    "cost": 1,
                    "descriptions": "适合逛街、约会、宴会等。 妆面特点：妆容相对生活妆稍浓，发型多变， 发型简约。服务内容：妆面，简约发型。 ",
                    "tags": [
                        {
                            "tagId": 1,
                            "workId": 211,
                            "tag": "欧美风"
                        },
                        {
                            "tagId": 1,
                            "workId": 211,
                            "tag": "气场女王"
                        },
                        {
                            "tagId": 1,
                            "workId": 211,
                            "tag": "烟熏妆"
                        }
                    ]
                },
                {
                    "workId": 212,
                    "cover": "http://photosd.nggirl.com.cn/work/8cc7ce42aac644b09c5837e090c3303d.jpg",
                    "workType": "约会妆",
                    "cost": 1,
                    "descriptions": "此妆面着重刻画眼部轮廓，日系色彩浓重，轻薄的粉底，微微修饰脸部轮廓，再加上淡橘色腮红点缀，丰满富有光泽的唇部勾勒出性感妩媚的日系感觉。免费提供日系睫毛上下各一副。",
                    "tags": [
                        {
                            "tagId": 1,
                            "workId": 212,
                            "tag": "欧美风"
                        },
                        {
                            "tagId": 1,
                            "workId": 212,
                            "tag": "英伦"
                        },
                        {
                            "tagId": 1,
                            "workId": 212,
                            "tag": "朋克"
                        }
                    ]
                }
            ]
        }
    },
}
```

返回字段说明：

|字段名称|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data -works-hasMore	|是否有更多数据（1表示有，0表示没有）
|Data -works-workId	|作品编号
|Data -works- cover	|封面图片路径
|Data -works workType|作品类型
|Data -works- cost	|费用
|Data -works- descriptions|作品描述
|Data -works- tags|作品标签
|Data -dressers- hasMore|是否有更多数据（1表示有，0表示没有）
|Data -dressers- dresserId|化妆师Id
|Data -dressers- dresserName	|化妆师姓名
|Data -dressers- orderNum|作品序号
|Data -dressers- workType|作品类型profile
|Data -dressers- profile|化妆师图片
|Data -dressers- authentication	|是否认证
|Data -dressers- starLevel|等级
|Data -dressers- isVDresser|是否加V




<h2 id="3" >3. 获取作品详情</h2>
详见 【C端】南瓜姑娘接口文档-作品   获取作品详情（一次获取所有信息）(#https://github.com/nggirl/ngdocs/blob/master/nggirl/interface/%5BC%E7%AB%AF%5D%E5%8D%97%E7%93%9C%E5%A7%91%E5%A8%98%E6%8E%A5%E5%8F%A3%E6%96%87%E6%A1%A3-%E4%BD%9C%E5%93%81.md#4)
> 用于微信端获取详情页面


<h2 id="4">4. 获取微信首页作品类型列表</h2>
> 注释：
1. 微信首页默认显示5类妆型，后台将全部（10类）查出后返回，点击查看更多再显示其余部分。
2. 后台实现时用sql语句(union)将全部类型作品一次性查出，整理类别后返回给前台。
> 用于微信公共号首页加载数据

请求方法：nggirl/app/cli/works/weixin/listWorksAtWxHome

请求URL: 接口地址/nggirl/app/cli/works/weixin/listWorksAtWxHome

支持格式：JSON

HTTP请求：GET

|参数名称|参数含义
|---|---|



请求实例：

> http://localhost:8080/nggirl/app/cli/works/weixin/listWorksAtWxHome?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&

返回结果示例：

```json
{
    "code": 0
    "data":
       {
        "晚妆": [
            {
                "workId": 210,
                "cover": "http://photosd.nggirl.com.cn/work/6e309e1f410a436abb7ef68c16caee65.jpg",
                "cost": 1,
                "workType": "晚妆",
                "hasDiscount": 1,
                "discount":{
                        "id":1,
                        "workId":123,
                        "name":"首单五折",
                        "desc":"新用户首次下单五折优惠，还可叠加使用优惠券",
                        "cost":50,
                        "icon":"http://testphotosd.nggirl.com.cn/work/aee4e7c292094a24a72ac8da401bbd7d.png"
                        },
                "tags": [
                    {
                        "tagId": 2854,
                        "workId": 210,
                        "tag": "欧美风"
                    },
                    {
                        "tagId": 2855,
                        "workId": 210,
                        "tag": "气场女王"
                    },
                    {
                        "tagId": 2856,
                        "workId": 210,
                        "tag": "烟熏妆"
                    }
                ]
            },
            {
                "workId": 219,
                "cover": "http://photosd.nggirl.com.cn/work/def6217577694aaa8e410e9e826a6e51.jpg",
                "cost": 1,
                "workType": "晚妆",
                 "hasDiscount": 0,
                "discount":{
                        "id":null,
                        "workId":null,
                        "name":null,
                        "desc":null,
                        "cost":null,
                        "icon":null
                        },
                "tags": [
                    {
                        "tagId": 1458,
                        "workId": 219,
                        "tag": "复古妆"
                    }
                ]
            },
            {
                "workId": 220,
                "cover": "http://photosd.nggirl.com.cn/work/7edbb5aee94e438fae45eb9fb71d8db4.jpg",
                "cost": 1,
                "workType": "晚妆",
                "hasDiscount": 0,
                "discount":{
                        "id":1,
                        "workId":123,
                        "name":"首单五折",
                        "desc":"新用户首次下单五折优惠，还可叠加使用优惠券",
                        "cost":50,
                        "icon":"http://testphotosd.nggirl.com.cn/work/aee4e7c292094a24a72ac8da401bbd7d.png"
                        },
                "tags": [
                    {
                        "tagId": 1374,
                        "workId": 220,
                        "tag": "复古妆"
                    }
                ]
            },
            {
                "workId": 233,
                "cover": "http://photosd.nggirl.com.cn/work/7b4b44e018d54e3986a59bffb040a223.jpg",
                "cost": 1,
                "workType": "晚妆",
                 "hasDiscount": 0,
                "discount":{
                        "id":1,
                        "workId":123,
                        "name":"首单五折",
                        "desc":"新用户首次下单五折优惠，还可叠加使用优惠券",
                        "cost":50,
                        "icon":"http://testphotosd.nggirl.com.cn/work/aee4e7c292094a24a72ac8da401bbd7d.png"
                        },
                "tags": [
                    {
                        "tagId": 1315,
                        "workId": 233,
                        "tag": "气场女王"
                    },
                    {
                        "tagId": 1316,
                        "workId": 233,
                        "tag": "复古妆"
                    },
                    {
                        "tagId": 1317,
                        "workId": 233,
                        "tag": "减龄妆"
                    }
                ]
            }
        ],
                 
         "年会妆":[...],
         "Party妆":[...],
         "晚妆":[...],
         "VIP妆":[...],
         "特殊造型":[...]...
         }
}
```

返回字段说明：

|字段名称|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - workId	|作品编号
|Data - cover	|封面图片路径
|Data - cost	|费用
|Data - tags|作品标签
|Data - hasDiscount|此作品是否参与了折扣活动，0没有，1有
|Data - discount - id|活动编号
|Data - discount - workId|参与活动的作品编号
|Data - discount - name|活动名称，显示在作品的活动栏（红底部分）
|Data - discount - desc|活动描述，显示在作品的活动栏
|Data - discount - cost|参与活动后的价格
|Data - discount - icon|活动的图标，用于放在作品的图片右上角


<h2 id="5" >5. 模糊查询化妆师</h2>
详见 【C端】南瓜姑娘接口文档-化妆师  
> 用于按关键字查询后化妆师的查看更多
化妆师模糊查询(#https://github.com/nggirl/ngdocs/blob/master/nggirl/interface/%5BC%E7%AB%AF%5D%E5%8D%97%E7%93%9C%E5%A7%91%E5%A8%98%E6%8E%A5%E5%8F%A3%E6%96%87%E6%A1%A3-%E5%8C%96%E5%A6%86%E5%B8%88.md#2)

<h2 id="6"> 6. 模糊查询作品</h2>
> 用于搜索关键字后作品部分查看更多

请求方法：nggirl/app/cli/works/weixin/listWorksBlur

请求URL: 接口地址/nggirl/app/cli/works/weixin/listWorksBlur

支持格式：JSON

HTTP请求：POST

|参数名称|参数含义
|---|---|
|key|搜索作品的关键字
|page|页数
|num|返回条数

```json
{
    "code": 0
    "data":[{
    	        "workId": 1234567,
            	"cover":"http://www.baidu.com/1.jpg",
            	"workType":"职业装",
            	"cost":100,
            	"descriptions":"肤质较佳的女生。强调重点：强调眼唇重点。以润色隔离霜作为底妆，然后以睫毛膏……",
            	"tags": [
                      {
                    "tagId": 1,
                    "workId": 382,
                    "tag": "欧美风"
                      }
                       ]
        	},
        	{
            	"workId": 1234567,
            	"cover":"http://www.baidu.com/1.jpg",
            	"workType":"职业装",
            	"cost":100,
            	"descriptions":"肤质较佳的女生。强调重点：强调眼唇重点。以润色隔离霜作为底妆，然后以睫毛膏…….",
            	"tags": [
                      {
                    "tagId": 3683,
                    "workId": 365,
                    "tag": "赫本"
                },
                {
                    "tagId": 3684,
                    "workId": 365,
                    "tag": "韩式公主"
                },
                {
                    "tagId": 3685,
                    "workId": 365,
                    "tag": "小清新"
                }
                       ]
               }]
}
```

返回字段说明：

|字段名称|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - workId	|作品编号
|Data - cover	|封面图片路径
|Data - workType|作品类型
|Data - cost	|费用
|Data - descriptions|作品描述
|Data - tags-tagId|标签id
|Data -tags-workId|标签的作品id
|Data - tags-tag|标签


<h2 id="7"> 7. 我要预约-婚博会专场</h2>
> 用于婚博会专场-我要预约，去除预约时间检验

请求方法：nggirl/app/cli/works/weixin/getReservationHbh

请求URL：接口地址/nggirl/app/cli/works/weixin/getReservationHbh

支持格式：JSON

HTTP请求：POST

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|授权令牌
|workId|作品Id
|reservationTime|预约时间
|reservationAddress|预约地址
|phoneNum|预约电话号码

请求示例：

> http://localhost/nggirl/app/cli/works/weixin/getReservationHbh?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&workId=10000&reservationTime=2015-12-04&reservationAddress=北京朝阳区&phoneNum=010888888

返回结果示例：

```json
{
    "code":0,
    "data":{
        "reservationId":123234324
    }
}
```


返回字段说明：

|字段名称|字段含义|
|----|----|
|Code | 错误码，0表示正确|
|Data - reservationId| 预约编号|

<h2 id="8"> 8. 我要预约-婚博会专场</h2>
> 直接生成已接单订单

请求方法：nggirl/app/cli/works/weixin/getReservationDirect

请求URL：接口地址/nggirl/app/cli/works/weixin/getReservationDirect

支持格式：JSON

HTTP请求：POST

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|授权令牌
|workId|作品Id
|reservationDate|预约时间
|reservationTime|预约时间
|reservationAddress|预约地址
|phoneNum|预约电话号码

请求示例：

> http://localhost/nggirl/app/cli/works/weixin/getReservationHbh?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&workId=10000&reservationDate=2015-12-04&reservationTime=12:00 - 14:00&reservationAddress=北京朝阳区&phoneNum=010888888

返回结果示例：

```json
{
    "code":0,
    "data":{
        "reservationId":123234324
    }
}
```


返回字段说明：

|字段名称|字段含义|
|----|----|
|Code | 错误码，0表示正确|
|Data - reservationId| 预约编号|



<h2 id="9"> 9. 我要预约-普通预约(预约日期增加到三十天)V1.3.2</h2>

请求方法：nggirl/app/cli/works/weixin/getReservation/1.3.2

请求URL：接口地址/nggirl/app/cli/works/weixin/getReservation/1.3.2

支持格式：JSON

HTTP请求：POST

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|授权令牌
|workId|作品Id
|reservationDate|预约日期
|reservationTime|预约时间段
|reservationAddress|预约地址
|phoneNum|预约电话号码

请求示例：

> http://localhost/nggirl/app/cli/works/weixin/getReservation/1.3.2?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&workId=10000&reservationDate=20160123&reservationTime=12:00 - 14:00&reservationAddress=北京朝阳区&phoneNum=010888888

返回结果示例：

```json
{
    "code":0,
    "data":{
        "reservationId":123234324
    }
}
```


返回字段说明：

|字段名称|字段含义|
|----|----|
|Code | 错误码，0表示正确|
|Data - reservationId| 预约编号|


<h2 id="10">10.取消预约(预约日期增加到三十天)V1.3.2</h2>

详见 【C端】南瓜姑娘接口文档-作品V1.3.2   取消预约(可预约时间改为30天)V1.3.2(#https://github.com/nggirl/ngdocs/blob/master/nggirl/interface/%5BC%E7%AB%AF%5D%E5%8D%97%E7%93%9C%E5%A7%91%E5%A8%98%E6%8E%A5%E5%8F%A3%E6%96%87%E6%A1%A3-%E4%BD%9C%E5%93%81V1.3.2.md#17)


<h2 id="11" >11.获取可预约时间(预约日期增加到三十天)V1.3.2</h2>

详见 【C端】南瓜姑娘接口文档-作品V1.3.2   可预约时间段(增加到30天)V1.3.2(#https://github.com/nggirl/ngdocs/blob/master/nggirl/interface/%5BC%E7%AB%AF%5D%E5%8D%97%E7%93%9C%E5%A7%91%E5%A8%98%E6%8E%A5%E5%8F%A3%E6%96%87%E6%A1%A3-%E4%BD%9C%E5%93%81V1.3.2.md#14)
