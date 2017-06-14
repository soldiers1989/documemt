# 微信授权

* [1.微信静默授权-根据code获取OpenId](#1)
* [2.微信显式确认授权-注册并获取用户信息V1.4.2](#2)


<h2 id="1" >1.微信静默授权-根据code获取OpenId</h2>

请求方法：nggirl/app/cli/register/weixin/getOpenId

请求URL：接口地址/nggirl/app/cli/register/weixin/getOpenId

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|字段名称|字段含义
|---|---|
|code|[必填]h5页面通过静默授权获取的code

请求示例：

> http://localhost/nggirl/app/cli/register/weixin/getOpenId?code=sdfepnfdw

返回结果示例：

```json
{
    "code": 0,
    "data":{
    	"openid":"mxedfeinasdfedfdefdsceon"
	}

}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code  |0表示正确
|Data - openid|用户openid


<h2 id="2">2.微信显式确认授权-注册并获取用户信息V1.4.2</h2>

>如果用户已经在系统中进行了注册，则直接返回用户已注册的信息

>如果用户尚未注册，则先注册再返回注册的信息

请求方法：nggirl/app/cli/register/weixin/getInfo/1.4.2

请求URL：接口地址/nggirl/app/cli/register/weixin/getInfo/1.4.2

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|字段名称|字段含义
|---|---|
|code|[必填]h5页面通过用户确认授权获取的code
|marketChannel|[可选]市场地推渠道


请求示例：

> http://localhost/nggirl/app/cli/register/weixin/getInfo/1.4.2?code=dfiafad

返回结果示例：

```json
{
    "code": 0,
    "data":{
      "userId":1,
      "accessToken":"dkfeisdfaeccsefe",
      "refreshToken":"dkfeisdfaeccsefe",
      "expireTime":1234567890123,
      "imAccount":"test_user_124",
      "imPassword":"111111",
      "isUserInfoEnough":1
    }
}
```

返回字段说明：

|字段名称|字段含义
|---|---|
|Code  |0表示正确
|Data - userId|用户编号
|Data - accessToken|授权令牌
|Data - refreshToken|刷新授权令牌
|Data - expireTime|令牌过期时间
|Data - imAccount|im账号
|Data - imPassword|im账号密码
|Data - isUserInfoEnough|用户信息是否完善，0不完善，1完善
