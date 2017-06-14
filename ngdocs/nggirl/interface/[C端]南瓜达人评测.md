# 南瓜达人评测

* [1.用户提交评测题V3.0.2](#1)


<h2 id="1">1.用户提交评测题V3.0.2</h2>

请求方法：nggirl/app/cli/pumpkinexpert/submitTestQuestion/3.0.2

请求URL：接口地址/app/cli/pumpkinexpert/submitTestQuestion/3.0.2

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义|
|---|---|
|accessToken|[必填]用户授权令牌|
|testType|测评题类型：1彩妆类，2护肤类|
|testQuestions|[必填]测评题问题和答案，json格式字符串|

```json
[
  {
    "question":"",
    "answer":""
  },
  {
    "question":"",
    "answer":""
  }
  {
    "question":"",
    "answer":""
  }
]
```
请求示例：localhost/nggirl/app/cli/pumpkinexpert/submitTestQuestion/3.0.2

返回结果示例：
```json
{
  "code":0,
  "data":null
}
```
