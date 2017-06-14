#南瓜姑娘接口文档-我的关注V2.2.0




* [1.添加关注用户V2.2.0](#1)
* [2.获取关注用户列表V2.2.0](#2)
* [3.取消关注用户V2.2.0](#3)


<h2 id="1">1.添加关注用户V2.2.0</h2>

请求方法：nggirl/app/cli/personal/addFollowUser/2.2.0

请求URL：接口地址/app/cli/personal/addFollowUser/2.2.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]用户授权令牌|
|followedUserId|[必填]被关注的用户编号|

请求示例：localhost/nggirl/app/cli/personal/addFollowUser/2.2.0

返回结果示例：

```json
{
  "code":0,
  "data":null
}
```


<h2 id="2">2.获取关注用户列表V2.2.0</h2>

请求方法：nggirl/app/cli/personal/getFollowedUserList/2.2.0

请求URL：接口地址/nggirl/app/cli/personal/getFollowedUserList/2.2.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]用户授权令牌|
|page|[可选]页数,非必需参数，默认第一页|
|num|[可选]每页信息数目,非必须参数，默认20|

请求示例：localhost/nggirl/app/cli/personal/getFollowedUserList/2.2.0

返回结果示例：

```json
{
  "code":0,
  "data":[
    {
      "userId":1,
      "nickName":"大美",
      "profile":"http://testphotosd.nggirl.com.cn/work/57b0a6defc0d41d681fc700b0c7400ef.png",
      "userRole":"南瓜小编"
    },
    {
      "userId":1,
      "nickName":"大美",
      "profile":"http://testphotosd.nggirl.com.cn/work/57b0a6defc0d41d681fc700b0c7400ef.png",
      "userRole":"南瓜小编"
    }
  ]
}
```

返回字段说明：

|字段名称|字段含义|
|---|---|
|Code|错误标识码，0标识正确|
|Data - userId|被关注用户编号|
|Data - nickName|用户昵称|
|Data - profile|用户头像|
|Data - userRole|用户角色|

<h2 id="3">3.取消关注用户V2.2.0</h2>

请求方法：nggirl/app/cli/personal/cancelFollowUser/2.2.0

请求URL：接口地址/nggirl/app/cli/personal/cancelFollowUser/2.2.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]用户授权令牌|
|followedUserId|[必填]被关注的用户编号|

请求示例：localhost/nggirl/app/cli/personal/cancelFollowUser/2.2.0

返回结果示例：

```json
{
  "code":0,
  "data":null
}
```
