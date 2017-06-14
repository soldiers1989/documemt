# 首页推荐专栏和帖子列表V3.0.0
---

* [1.推荐分类按钮列表](#1)
* [2.推荐帖子列表](#2)
* [3.某个专栏对应帖子列表](#3)
* [4.推荐过的商品列表](#4)

<h2 id="1">1.推荐分类按钮列表</h2>

请求方法：nggirl/app/cli/homePage/getSortButtonList/3.0.0

请求url：接口地址/nggirl/app/cli/homePage/getSortButtonList/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：无

请求示例：
> http://localhost/nggirl/app/cli/homePage/getSortButtonList/3.0.0

返回结果示例：
```json
{
    "code":0,
    "data":[
        {
            "sortButtonId":1,
            "name":"原创视频",
            "photoUrl":"",
            "webPageUrl":"",
            "forwardType":"",
            "forwardKey":"",
            "shareImg":"",
            "shareContent":""
        },
        {
            "sortButtonId":1,
            "name":"原创视频",
            "photoUrl":"",
            "webPageUrl":"",
            "forwardType":"",
            "forwardKey":"",
            "shareImg":"",
            "shareContent":""
        },
        {
            "sortButtonId":1,
            "name":"原创视频",
            "photoUrl":"",
            "webPageUrl":"",
            "forwardType":"",
            "forwardKey":"",
            "shareImg":"",
            "shareContent":""
        }
    ]
}
```
返回结果说明：

|字段名称|字段含义|
|---|---|
|Code|错误标识码，0标识正确|
|Data - sortButtonId|分类按钮编号|
|Data - name|名称|
|Data - photoUrl|图片|
|Data - webPageUrl|跳转页面|
|Data - forwardType|跳转类型|
|Data - forwardKey|跳转参数|
|Data - shareImg|分享小图|
|Data - shareContent|分享内容|

[forwardType和forwardKey对应关系说明文档](https://github.com/nggirl/ngdocs/blob/master/nggirl/web%E8%B7%B3%E8%BD%AC%E5%88%B0app%E8%AF%B7%E6%B1%82%E6%A0%BC%E5%BC%8F%E5%AE%9A%E4%B9%89.md)

<h2 id="2">2.推荐帖子列表</h2>

请求方法：nggirl/app/cli/homePage/getRecommendPostList/3.0.0

请求url：接口地址/nggirl/app/cli/homePage/getRecommendPostList/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|----|----|
|accessToken|【选填】用户授权令牌，登录时必填|
|recommendDate|【选填】推荐日期，默认不填，上拉的时候传入；十三位毫秒数；用于分页返回某一天的推荐帖子|

请求示例：
> http://localhost/nggirl/app/cli/homePage/getRecommendPostList/3.0.0

返回结果示例：
```json
{
    "code":0,
    "data":
        {
            "isFirstPage":1,
            "recommendDate":1320718222932,
            "recommendDateStr":"11月24日",
            "recommendList":[
                {
                    "recommendTypeId":1,
                    "type":1,
                    "columnId":1,
                    "columnName":"原创视频",
                    "isFirst":1,
                    "posts":[
                        {
                            "postId":1,
                            "postType":1,
                            "userId":1,
                            "nickName":"nike",
                            "profile":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
                            "userRole":"官方",
                            "userLevel":1,
                            "detailImg":"http://photosd.nggirl.com.cn/work/5a9e15e564f94d688370c8ee1af4913d.jpg",
                            "title":"兰蔻 玫瑰轻柔润唇膏口红唇彩",
                            "descrip":"这款兰蔻精华",
                            "commentNum":200,
                            "likeNum":422,
                            "viewNum":699,
                            "isEssential":1
                        }
                    ],
                    "products":[
                    ]
                },
                {
                    "recommendTypeId":1,
                    "type":2,
                    "columnId":0,
                    "columnName":"",
                    "isFirst":0,
                    "posts":[
                    ],
                    "products":[
                        {
                            "seedProductId":1,
                            "name":"纪梵希 2016圣诞限定",
                            "picture":"",
                            "price":56.5,
                            "seedNum":20,
                            "isSeed":1,
                            "recommendation":5,
                            "tb_item_id":"",
                            "tb_detail_url":"",
                            "isAllowBuy":1
                        },
                        {
                            "seedProductId":1,
                            "name":"纪梵希 2016圣诞限定",
                            "picture":"",
                            "price":56.5,
                            "seedNum":20,
                            "isSeed":1,
                            "recommendation":5,
                            "tb_item_id":"",
                            "tb_detail_url":"",
                            "isAllowBuy":1
                        }
                    ]
                }
            ]
        }
}
```
返回字段说明：

|字段名称|字段含义|
|---|---|
|Code|错误标识码|
|Data - isFirstPage|是不是第一页数据，1是，0否|
|Data - recommendDate|推荐日期，十三位毫秒数，用于传给后台|
|Data - recommendDateStr|推荐日期，字符串形式，用于显示；如果是当年的话只返回月日，否则返回年月日|
|Data - recommendList|推荐列表，包括帖子和种草商品|
|Data - recommendList - recommendTypeId|推荐模块记录编号|
|Data - recommendList - type|类型：1帖子专栏，2商品|
|Data - recommendList - columnId|推荐模块编号，如果type=1，则是专栏编号|
|Data - recommendList - columnName|推荐模块名称|
|Data - recommendList - isFirst|是不是第一个推荐模块，0不是，1是|
|Data - recommendList - posts|帖子列表|
|Data - recommendList - posts - postId|帖子编号|
|Data - recommendList - posts - postType|帖子类型：1文章帖子，2视频帖子|
|Data - recommendList - posts - userId|用户编号|
|Data - recommendList - posts - nickName|用户昵称|
|Data - recommendList - posts - profile|用户头像|
|Data - recommendList - posts - userRole|用户角色（南瓜CEO,南瓜小编,客座小编,普通用户不显示身份）|
|Data - recommendList - posts - userLevel|用户等级 0-Lv0,1-Lv1,2-Lv2....|
|Data - recommendList - posts - detailImg|头图|
|Data - recommendList - posts - title|标题|
|Data - recommendList - posts - descrip|描述|
|Data - recommendList - posts - commentNum|评论数|
|Data - recommendList - posts - likeNum|喜欢的人数|
|Data - recommendList - posts - viewNum|浏览数|
|Data - recommendList - posts - isEssential|是否加精帖：0否，1是|
|Data - recommendList - products|后花园商品|
|Data - recommendList - products - seedProductId|商品编号|
|Data - recommendList - products - name|商品名称|
|Data - recommendList - products - picture|配图|
|Data - recommendList - products - price|参考价格|
|Data - recommendList - products - seedNum|种草人数|
|Data - recommendList - products - isSeed|是否已种草：0未种草，1已种草|
|Data - recommendList - products - recommendation|推荐度：0-10|
|Data - recommendList - products - tb_item_id|淘宝商品id|
|Data - recommendList - products - tb_detail_url|商品链接|
|Data - recommendList - products - isAllowBuy|是否可以购买：0不可购买，1可购买|



<h2 id="3">3.某个专栏对应帖子列表</h2>

请求方法：nggirl/app/cli/homePage/getPostListByColumn/3.0.0

请求url：接口地址/nggirl/app/cli/homePage/getPostListByColumn/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|----|----|
|columnId|【必填】专栏id|
|pageNum|第几页，从0开始|
|pageSize|每页多少条，默认20|

请求示例：
> http://localhost/nggirl/app/cli/homePage/getPostListByColumn/3.0.0

返回结果示例：
```json
{
    "code":0,
    "data":[
        {
            "postId":1,
            "postType":1,
            "detailImg":"",
            "userId":269,
            "nickName":"hahha",
            "profile":"",
            "userRole":"官方",
            "userLevel":2,
            "columnId":1,
            "columnName":"美妆课堂",
            "title":"",
            "descrip":"",
            "commentNum":100,
            "likeNum":200,
            "viewNum":1000,
            "isEssential":0
        },
        {
            "postId":1,
            "postType":1,
            "detailImg":"",
            "userId":269,
            "nickName":"hahha",
            "profile":"",
            "userRole":"官方",
            "userLevel":3,
            "title":"",
            "columnId":1,
            "columnName":"美妆课堂",
            "descrip":"",
            "commentNum":100,
            "likeNum":200,
            "viewNum":1000,
            "isEssential":1
        }
    ]
}
```
返回结果说明：

|字段名称|字段含义|
|---|---|
|Code|错误标识码，0标识正确|
|Data - postId|帖子编号|
|Data - postType|帖子类型：1文章帖子，2视频帖子|
|Data - detailImg|头图|
|Data - userId|用户编号|
|Data - nickName|用户昵称|
|Data - profile|用户头像|
|Data - userRole|用户角色（南瓜CEO,南瓜小编,客座小编,普通用户不显示身份）|
|Data - userLevel|用户等级：0-Lv0,1-Lv1,2-Lv2....|
|Data - title|标题|
|Data - columnId|专栏id|
|Data - columnName|专栏名称|
|Data - descrip|描述|
|Data - commentNum|评论数|
|Data - likeNum|喜欢的人数|
|Data - viewNum|浏览数|
|Data - isEssential|是否加精贴：0否，1是|


<h2 id="4">4.推荐过的商品列表</h2>

> 查询推荐过的商品列表，并进行排重

请求方法：nggirl/app/cli/homePage/getMoreProductList/3.0.0

请求url：接口地址/nggirl/app/cli/homePage/getMoreProductList/3.0.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|【选填】用户授权令牌，登录时必填|
|pageNum|第几页，从0开始|
|pageSize|每页多少条，默认20|


请求示例：
> http://localhost/nggirl/app/cli/homePage/getMoreProductList/3.0.0

返回结果示例：
```json
{
    "code":0,
    "data":[
        {
            "seedProductId":1,
            "name":"Mac唇膏",
            "picture":"",
            "price":"",
            "seedNum":20,
            "isSeed":1,
            "recommendation":4,
            "tb_item_id":"3243432",
            "tb_detail_url":"",
            "isAllowBuy":1
        },
        {
            "seedProductId":1,
            "name":"Mac唇膏",
            "picture":"",
            "price":"",
            "seedNum":20,
            "isSeed":1,
            "recommendation":4,
            "tb_item_id":"3243432",
            "tb_detail_url":"",
            "isAllowBuy":1
        }
    ]
}
```
返回字段说明：

|字段名称|字段含义|
|---|---|
|Code|错误标识码，0表示正确|
|Data - seedProductId|商品编号|
|Data - name|商品名称|
|Data - picture|配图|
|Data - price|参考价格|
|Data - seedNum|种草人数|
|Data - isSeed|是否已种草：0未种草，1已种草|
|Data - recommendation|推荐图：0-10|
|Data - tb_item_id|淘宝商品编号|
|Data - tb_detail_url|商品购买链接|
|Data - isAllowBuy|是否允许购买：0不可以买，1可以买|
