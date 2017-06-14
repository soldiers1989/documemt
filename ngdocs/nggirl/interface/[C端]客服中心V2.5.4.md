# 客服中心V2.5.4.md

* [1.获取问题列表V2.5.4](#1)
* [2.获取活动通知列表V2.5.4](#2)
* [3.点击“有用”或“无用”操作V2.5.4](#3)


<h2 id="1">1.获取问题列表</h2>

请求方法：nggirl/app/cli/callCenter/getProblems/2.5.4

请求URL：接口地址/nggirl/app/cli/callCenter/getProblems/2.5.4

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|[非必填，登录时必填]用户授权令牌

请求示例：

> http://localhost/nggirl/app/cli/callCenter/getProblems/2.5.4

返回结果示例：
```json
{
  "code":0,
  "data":[
    {
      "problemId":1,
      "problem":"",
      "answer":"",
      "isUseful":1,
    },
    {
      "problemId":1,
      "problem":"",
      "answer":"",
      "isUseful":1,
    }
  ]
}
```
返回结果说明:

|字段名称|字段含义|
|---|---|
|problemId|问题编号|
|problem|问题|
|answer|回答|
|isUseful|（为了是否显示高亮）是否有用：0无用，1有用，2还没有状态|


<h2 id="2">2.获取活动通知列表</h2>

请求方法：nggirl/app/cli/callCenter/getNotices/2.5.4

请求URL：接口地址/nggirl/app/cli/callCenter/getNotices/2.5.4

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|[非必填，登录时必填]用户授权令牌


请求示例：

> http://localhost/nggirl/app/cli/callCenter/getNotices/2.5.4

返回结果示例：
```json
{
  "code":0,
  "data":[
    {
      "problemId":1,
      "problem":"",
      "answer":"",
      "isUseful":1,
    },
    {
      "problemId":1,
      "problem":"",
      "answer":"",
      "isUseful":1,
    }
  ]
}
```
返回结果说明:

|字段名称|字段含义|
|---|---|
|problemId|问题编号|
|problem|问题|
|answer|回答|
|isUseful|（为了是否显示高亮）是否有用：0无用，1有用，2还没有状态|



<h2 id="3">3.点击“有用”或“无用”操作V2.5.4</h2>

请求方法：nggirl/app/cli/callCenter/clickOpr/2.5.4

请求URL：接口地址/nggirl/app/cli/callCenter/clickOpr/2.5.4

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken	|[非必填，登录时必填]用户授权令牌
|problemId	|问题编号
|isUseful	|是否有用：0无用，1有用

请求示例：

> http://localhost/nggirl/app/cli/callCenter/clickOpr/2.5.4

返回结果示例：
```json
{
  "code":0,
  "data":null
}
```
