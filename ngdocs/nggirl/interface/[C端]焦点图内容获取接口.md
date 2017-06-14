# 焦点图内容管理

* [1.获取焦点图内容列表](#1)
* [2.获取焦点图内容html片段](#2)


<h2 id="1">获取焦点图内容列表</h2>
请求方法：nggirl/app/focuscontent/list

请求URL：接口地址/nggirl/app/focuscontent/list

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

参数名称 | 参数含义
------------ | -------------
page|页数，默认第1页
num|每页的条数，默认20条

>按照创建时间逆序排列

请求示例：

`http://localhost/nggirl/app/focuscontent/list?page=2&num=20`

返回结果示例：
```json
{
    "data":[{
        "id":2015102709876548,
        "coverImage":"http://cli.nggirl.com.cn/ng-mobile-web/focusimages/images/post_info_zixun/18/banner_post_info_18.jpg",
        "title":"最美新娘季，甜蜜二连发",
        "description":"最美新娘季，甜蜜二连发",
        "contentUrl":"http://cli.nggirl.com.cn/nggirl/focuscontent?cid=2015102709876548",
        "createtime":1475656565000,
    },{
        "id":2015102709876549,
        "coverImage":"http://cli.nggirl.com.cn/ng-mobile-web/focusimages/images/post_info_zixun/18/banner_post_info_18.jpg",
        "title":"最美新娘季，甜蜜二连发",
        "description":"最美新娘季，甜蜜二连发",
        "contentUrl":"http://cli.nggirl.com.cn/nggirl/focuscontent?cid=2015102709876549",
        "createtime":1475656565000,
    },{
        "id":2015102709876550,
        "coverImage":"http://cli.nggirl.com.cn/ng-mobile-web/focusimages/images/post_info_zixun/18/banner_post_info_18.jpg",
        "title":"最美新娘季，甜蜜二连发",
        "description":"最美新娘季，甜蜜二连发",
        "contentUrl":"http://cli.nggirl.com.cn/nggirl/focuscontent?cid=2015102709876550",
        "createtime":1475656565000,
    }],
    "code": 0
}
```
返回字段说明：

字段| 说明
:------|:-------
code	|错误码，0表示正确
Data – coverImage | 焦点图封面图片
Data – id | 焦点图内容编号
Data – title | 焦点图的标题，标题将显示在网页的标题栏上，也会显示在微信分享的分享描述上。
Data – description | 备注说明，比如内容的主题，内容为了哪个活动而生成等等
Data – contentUrl | 访问该焦点图页面的链接地址
Data – createtime | 创建的时间

<h2 id="2">获取焦点图内容html片段</h2>
请求方法：nggirl/app/focuscontent/getContent

请求URL：接口地址/nggirl/app/focuscontent/getContent

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

参数名称 | 参数含义
------------ | -------------
contentId|焦点图内容编号

>返回为html片段

请求示例：

`http://localhost/nggirl/app/focuscontent/getContent?contentId=215102945612378`

返回结果示例：
```json
{
    "data": {
        "content": "<div>遇见最美的自己，在最美丽的季节。不在夜上海，就在秋北京。</div>"
    },
    "code": 0
}
```
返回字段说明：

字段| 说明
:------|:-------
code	|错误码，0表示正确
Data – content	| 焦点图内容的html片段
