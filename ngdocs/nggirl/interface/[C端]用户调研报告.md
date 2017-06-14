# 用户调研报告



* [1.提交调研报告](#1)


<h2 id="1">1.提交调研报告</h2>

请求方法：nggirl/app/cli/question/submitQuestionReport

请求url：服务器地址/nggirl/app/cli/question/submitQuestionReport

支持格式:JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义|
|----|----|
|accessToken|[非必填，登录时必填]用户授权令牌|
|openId     |[非必填，在微信中打开时必填]微信openId|
|realName   |[选填]姓名|
|age        |[必填]年龄范围|
|profession |[必填]职业|
|city       |[必填]城市|
|attentionWay|[必填]关注方式,英文逗号分隔“,”|
|advice     |[选填]建议|

请求示例：
> localhost/nggirl/app/cli/question/submitQuestionReport

返回结果示例：
```json
{
  "code":0,
  "data":null
}
```


