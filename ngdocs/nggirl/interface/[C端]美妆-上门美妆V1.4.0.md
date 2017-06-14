# V1.4.0版本美妆模块-上门美妆

* [1.获取系统支持的妆束类型列表V1.4.0](#1)
* [2.获取专题推荐列表V1.4.0](#2)
* [3.获取某一妆型列表V1.4.0](#3)
* [4.获取某一专题介绍信息V1.4.0](#4)
* [5.获取某一专题作品列表V1.4.0](#5)
* [6.获取作品详情v1.4.0](#6)
* [7.获取作品详情（IOS端）v1.4.0](#7)
* [8.获取全部预约日期时间V1.4.0](#8)


<h2 id="1">1.获取系统支持的妆束类型列表V1.4.0</h2>

请求方法：nggirl/app/sys/listWorkTypes/1.4.0

请求URL：接口地址/nggirl/app/sys/listWorkTypes/1.4.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|

请求示例：

> http://localhost/nggirl/app/sys/listWorkTypes?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP

返回结果示例：
```json
{
    "code": 0,
	"data": [{
		"typeName":"职业妆",
		"pictureSelected":"http://nggirl-product-res.oss-cn-beijing.aliyuncs.com/sysres/dressTypeImage/makeup-list-1-hl",
		"pictureUnselected": "http://nggirl-product-res.oss-cn-beijing.aliyuncs.com/sysres/dressTypeImage/makeup-list-1",
		"ornament":"http://nggirl-product-res.oss-cn-beijing.aliyuncs.com/sysres/dressTypeImage/makeup-list-1"
	},
	{
	        "typeName":"Party妆",
		"pictureSelected":"http://nggirl-product-res.oss-cn-beijing.aliyuncs.com/sysres/dressTypeImage/makeup-list-1-hl",
		"pictureUnselected": "http://nggirl-product-res.oss-cn-beijing.aliyuncs.com/sysres/dressTypeImage/makeup-list-1",
	        "ornament":"http://nggirl-product-res.oss-cn-beijing.aliyuncs.com/sysres/dressTypeImage/makeup-list-1"
	}]
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - typeName	|妆束类型
|Data - pictureSelected	|选中的高亮图片
|Data - pictureUnselected	|没有选中的灰度图片
|Data - ornament |装饰图

> 备注：要获取2x图片使用pictureSelected+@180w_180h.png，要获取3x图片使用pictureSelected+@340w_340h.png，要获取安卓的图使用pictureSelected+@340w_340h.png


<h2 id="2">2.获取专题推荐列表</h2>

请求方法：nggirl/app/cli/works/special/list/1.4.0

请求URL：接口地址/nggirl/app/cli/works/special/list/1.4.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|pageNum|页数|
|pageSize|每页条数,默认为10条|
|city|所在城市|

请求示例：

> http://localhost/nggirl/app/cli/works/special/list/1.4.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&page=0&num=10&city=北京

返回结果示例：
```json
{
    "code": 0,
    "data": [
        {
            "specialId": 1,
            "name": "情人节特辑",
            "cover": "http://cn.bing.com/images/search?q=%E6%9E%97%E5%85%81&view=detailv2&&id=5D7346E3227A92CF9180F280BE42D95A31914013&selectedIndex=0&ccid=Wqog9G1k&simid=608009770475392537&thid=OIP.M5aaa20f46d6490bf32b7508dd1fa98b7o2&ajaxhist=0",
            "seq": 1,
            "works": [
                {
                    "workId": 226,
                    "cover": "http://photosd.nggirl.com.cn/work/802951cf0fe0483594f9a914fc9d6ca1.jpg",
                    "content": "小编推荐",
                    "cost": 31,
                    "hasDiscount": 0,
                    "discount": {
                        "id": null,
                        "workId": 226,
                        "name": null,
                        "desc": null,
                        "icon": null,
                        "cost": null,
                        "allow": null
                    }
                },
                {
                    "workId": 225,
                    "cover": "http://photosd.nggirl.com.cn/work/3d09fd12d54444f3a059e4dfcab33040.jpg",
                    "content": "1",
                    "cost": 0,
                    "hasDiscount": 0,
                    "discount": {
                        "id": null,
                        "workId": 225,
                        "name": null,
                        "desc": null,
                        "icon": null,
                        "cost": null,
                        "allow": null
                    }
                },
                {
                    "workId": 217,
                    "cover": "http://photosd.nggirl.com.cn/work/3e4baa71fc33403ab2a1ccb96d45f8c5.jpg",
                    "content": "小编的话",
                    "cost": 60,
                    "hasDiscount": 1,
                    "discount": {
                        "id": 15,
                        "workId": 217,
                        "name": "首单五折",
                        "desc": "新用户首次下单享五折优惠,还可叠加使用优惠券",
                        "icon": "http://photosd.nggirl.com.cn/work/0ffbcb2ad9524a50ac482bcabb73e3e5.png",
                        "cost": 30,
                        "allow": 0
                    }
                }
            ],
            "hasMore":0
        },
        {
            "specialId": 2,
            "name": "元宵节特辑",
            "cover": "http://cn.bing.com/images/search?q=%E9%A3%8E%E6%99%AF%E5%9B%BE%E7%89%87&view=detailv2&&id=7C8D6923797B1AEF6E5707CD6589C5F76924C892&selectedIndex=1&ccid=pusuSkWW&simid=608026031221114371&thid=OIP.Ma6eb2e4a4596ae467c66a8fa44da4b9ao0&ajaxhist=0",
            "seq": 2,
            "works": [
                {
                    "workId": 220,
                    "cover": "http://photosd.nggirl.com.cn/work/81c5017b07614804b697b5904b51b31d.jpg",
                    "content": "小编的话",
                    "cost": 1,
                    "hasDiscount": 0,
                    "discount": {
                        "id": null,
                        "workId": 220,
                        "name": null,
                        "desc": null,
                        "icon": null,
                        "cost": null,
                        "allow": null
                    }
                }
            ],
            "hasMore":0
        }
    ]
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - specialId	|专题id
|Data - name	|专题名称
|Data - cover	|专题封面(4:3)
|Data - seq	|专题排序
|Data - works-workId	|作品id
|Data - works-content	|专题作品文案
|Data - works-cover	|专题作品封面
|Data - works-cost	|作品价格
|Data - works-hasDiscount	|专题作品是否有折扣
|Data -works- discount - id|折扣活动编号
|Data -works- discount - workId|参与活动的作品编号
|Data -works- discount - name|活动名称，显示在作品的活动栏（红底部分）
|Data -works- discount - desc|活动描述，显示在作品的活动栏
|Data -works- discount - cost|参与活动后的价格
|Data -works- discount - icon|活动的图标，用于放在作品的图片右上角
|Data -works- discount - allow|该用户是否可享受活动，0为否，1为是
|Data - hasMore|作品集是否多于6个，1为是，0为否


<h2 id="3">3.获取某一妆型列表</h2>

请求方法：nggirl/app/cli/works/workType/list/1.4.0

请求URL：接口地址/nggirl/app/cli/works/workType/list/1.4.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|typeName|妆型名称（必填）|
|city|所在城市（必填）|
|pageNum|第几页|
|pageSize|每页大小，默认20页|
|orderBy|排序类型（选填，为空时默认排序）|
|lowPrice|筛选最低价格（选填）|
|highPrice|筛选最高价格（选填）|
|resDate|预约日期（选填）|
|resTime|预约时间段（选填）|

> orderBy 排序类型：1为默认排序，2为销量排序，3为人气排序，4为价格从高到低排序，5为价格从低到高排序


请求示例：

> http://localhost/nggirl/app/cli/works/workType/list/1.4.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&typeName=约会妆&orderType=1&city=北京

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
            "workId": 334,
            "cover": null,
            "content": null,
            "likeNum": 1,
            "resNum": 13,
            "ornament": "http://testphotosd.nggirl.com.cn/sysres/dressTypeImage/makeup-list-2.png",
            "cost": 31,
            "hasDiscount": 0,
            "discount": {
                "id": null,
                "workId": 334,
                "name": null,
                "desc": null,
                "icon": null,
                "cost": null,
                "allow": null
            }
        },
        {
            "workId": 354,
            "cover": null,
            "content": null,
            "likeNum": 1,
            "resNum": 6,
            "ornament": "http://testphotosd.nggirl.com.cn/sysres/dressTypeImage/makeup-list-2.png",
            "cost": 298,
            "hasDiscount": 0,
            "discount": {
                "id": null,
                "workId": 354,
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

> 注：对于content字段，当数据库作品名称为空时，返回作品类型

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

<h2 id="4">4. 获取某一专题介绍信息</h2>

请求方法：nggirl/app/cli/works/special/info/1.4.0

请求URL：接口地址/nggirl/app/cli/works/special/info/1.4.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|specialId|专题id|


请求示例：

> http://localhost/nggirl/app/cli/works/special/info/1.4.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&specialId=12

返回结果示例：
```json
{
   "code": 0,
    "data": {
        "id": 1,
        "name": "情人节特辑",
        "cover": "http://cn.bing.com/images/search?q=%E6%9E%97%E5%85%81&view=detailv2&&id=5D7346E3227A92CF9180F280BE42D95A31914013&selectedIndex=0&ccid=Wqog9G1k&simid=608009770475392537&thid=OIP.M5aaa20f46d6490bf32b7508dd1fa98b7o2&ajaxhist=0",
        "descrip": "情人节特辑",
        "portrait": "http://wx.qlogo.cn/mmopen/5DLpwb6mDjTyMkUjhxibt7YXlFUHbwg5tPqSnN7wFstRkxuaO0ibJERNfVnWK9xz6a4VzUykvr4aG8toveuibVGpu8LXjibQXCnW/0",
        "nickName": "王同贺"
    }
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - id	|专题id
|Data - name	|专题名称
|Data - cover	|专题封面(2:1)
|Data - portrait|专题小编头像
|Data - nickName|专题小编昵称
|Data - descrip|专题文案


<h2 id="5">5.获取某一专题作品列表</h2>

请求方法：nggirl/app/cli/works/special/listWorks/1.4.0

请求URL：接口地址/nggirl/app/cli/works/special/listWorks/1.4.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|specialId|专题id|
|orderBy|排序类型（选填，为空时默认排序）|
|pageNum|第几页（默认为0）|
|pageSize|每页大小（默认为20）|
|lowPrice|筛选最低价格（选填）|
|highPrice|筛选最高价格（选填）|
|resDate|预约日期（选填）|
|resTime|预约时间段（选填）|

请求示例：

> http://localhost/nggirl/app/cli/works/special/listWorks/1.4.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&specialId=12

返回结果示例：
```json
{
    "code": 0,
    "data": [
        {
            "workId": 225,
            "cover": "http://photosd.nggirl.com.cn/work/3d09fd12d54444f3a059e4dfcab33040.jpg",
            "content": "1",
            "likeNum": 6,
            "resNum": 68,
            "ornament": "http://testphotosd.nggirl.com.cn/sysres/dressTypeImage/makeup-list-8.png",
            "cost": 0,
            "hasDiscount": 0,
            "discount": {
                "id": null,
                "workId": 225,
                "name": null,
                "desc": null,
                "icon": null,
                "cost": null,
                "allow": null
            }
        },
        {
            "workId": 226,
            "cover": "http://photosd.nggirl.com.cn/work/802951cf0fe0483594f9a914fc9d6ca1.jpg",
            "content": "小编推荐",
            "likeNum": 2,
            "resNum": 21,
            "ornament": "http://testphotosd.nggirl.com.cn/sysres/dressTypeImage/makeup-list-8.png",
            "cost": 31,
            "hasDiscount": 0,
            "discount": {
                "id": null,
                "workId": 226,
                "name": null,
                "desc": null,
                "icon": null,
                "cost": null,
                "allow": null
            }
        },
        {
            "workId": 217,
            "cover": "http://photosd.nggirl.com.cn/work/3e4baa71fc33403ab2a1ccb96d45f8c5.jpg",
            "content": "小编的话",
            "likeNum": 5,
            "resNum": 8,
            "ornament": "http://testphotosd.nggirl.com.cn/sysres/dressTypeImage/makeup-list-8.png",
            "cost": 60,
            "hasDiscount": 1,
            "discount": {
                "id": 15,
                "workId": 217,
                "name": "首单五折",
                "desc": "新用户首次下单享五折优惠,还可叠加使用优惠券",
                "icon": "http://photosd.nggirl.com.cn/work/0ffbcb2ad9524a50ac482bcabb73e3e5.png",
                "cost": 30,
                "allow": 1
            }
        }
    ]
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确
|Data - -workId	|作品id
|Data - -cover	|专题作品封面
|Data - -content|专题作品广告文案|
|Data - likeNum|喜欢的人数|
|Data - resNum|预约人数|
|Data - cost|作品价格|
|Data -ornament |装饰图|
|Data - -hasDiscount	|专题作品是否有折扣
|Data -- discount - id|折扣活动编号
|Data -- discount - workId|参与活动的作品编号
|Data -- discount - name|活动名称，显示在作品的活动栏（红底部分）
|Data -- discount - desc|活动描述，显示在作品的活动栏
|Data -- discount - cost|参与活动后的价格
|Data -- discount - icon|活动的图标，用于放在作品的图片右上角
|Data -- discount - allow|该用户是否可享受活动，0为否，1为是


<h2 id="6">6.获取作品详情v1.4.0</h2>

请求方法：nggirl/app/cli/works/getWorksDetail/1.4.0

请求URL：接口地址/nggirl/app/cli/works/getWorksDetail/1.4.0

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
        "workName":"约会特辑",
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

> 注：对于workName字段，当数据库作品名称为空时，返回作品类型

|字段名称|字段含义
|---|---|
|Code	|错误码，0表示正确
|Data - workId	|作品编号
|Data - cover	|封面图片路径
|Data - workType	|作品类型
|Data - workName	|作品名称
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


<h2 id="7">7.获取作品详情（IOS端）v1.4.0</h2>

> 与V1.2版本相比，只添加了workName参数出参

请求方法：nggirl/app/cli/works/getWorksDetailIos/1.4.0

请求URL：接口地址/nggirl/app/cli/works/getWorksDetailIos/1.4.0

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
        "workName":"约会妆型",
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
|Data - workName	|作品名称
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


<h2 id="8">8.获取全部预约日期时间V1.4.0</h2>

请求方法：nggirl/app/cli/works/getAllReservationTimes/1.4.0

请求URL：接口地址/nggirl/app/cli/works/getAllReservationTimes/1.4.0

支持格式：JSON

HTTP请求方式：GET


请求示例：

> http://localhost/nggirl/app/cli/works/getAllReservationTimes/1.4.0

返回结果示例：

```json
{
   "code": 0,
   "data": [{
    "reservationDate": "01月21号 星期四",
    "realDate":"20160121",
    "reservationTimes":[{
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
     "reservationDate": "01月22号 星期五",
     "realDate":"20160122",
     "reservationTimes":[{
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
      "reservationDate": "01月23号 星期六",
      "realDate":"20160123",
      "reservationTimes":[{
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
|Data - reservationDate	|预约日期 （用于显示在移动端的）
|Data - reservationTimes	|时段
|Data - realDate | 所代表的真实日期 “20160121” 标准八位字符串（用于传给后台的，方便处理）
|Data - reservationTimes-name|时段名
|Data - reservationTimes-status|时段状态，0是未预约，1是已预约
