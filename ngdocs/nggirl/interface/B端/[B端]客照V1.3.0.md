# B端 客照

* [1. 获取客照列表](#1)
* [2. 发布客照](#2)
* [3. 删除客照](#3)


<h2 id="1">1.获取客照列表</h2>

> 获取化妆师客照列表

请求方法：nggirl/app/bus/post/list/1.3.0

请求URL：接口地址/nggirl/app/bus/post/list/1.3.0

支持格式：JSON

HTTP请求方式：GET

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken|登陆令牌（必填）
|pageNum|第几页，默认为0（选填）|
|pageSize|每页大小，默认20页（选填）|

请求示例：

> http://localhost/nggirl/app/bus/post/list/1.3.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&pageNum=1&pageSize=20&accessToken=ab3582cb4d3f45edb6e010359559f6e7

返回结果示例：
```json
{
    "code": 0,
	"data": [
	    {
    	    "postId":1,
    	    "descrip":"这是服务实拍的描述",
    	    "publishTime":123345344443,
    	    "likeNum":232,
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
    	    "postId":2,
    	    "descrip":"这是服务实拍的描述2",
    	    "publishTime":123345344443,
    	     "likeNum":232,
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
    	    "postId":3,
    	    "descrip":"这是服务实拍的描述3",
    	    "publishTime":123345344443,
    	     "likeNum":232,
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
|Data - likeNum|喜欢的人数
|Data - photoList-photoUrl|实拍图片url
|Data - photoList-width|实拍图片宽度
|Data - photoList-height|实拍图片高度


<h2 id="2">2.发布客照</h2>

> 化妆师发布客照

请求方法：nggirl/app/bus/post/publish/1.3.0

请求URL：接口地址/nggirl/app/bus/post/publish/1.3.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken|登陆令牌（必填）
|photoList|照片集合，json数组格式（必填）|
|descrip|描述内容（选填）|

photoList示例：

```json
 [
  {
    "photoUrl":"http://photosd.nggirl.com.cn/work/40a797b2614e4a13819197bc981ae1cf.jpg",
    "width":600,
    "height":800
   },{
     "photoUrl":"http://photosd.nggirl.com.cn/work/6731161484d049d4909de64ce870819f.jpg",
     "width":650,
     "height":800      
   }
 ]
```


请求示例：

> http://nggirl/app/bus/post/publish/1.3.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&pageNum=1&pageSize=20&accessToken=ab3582cb4d3f45edb6e010359559f6e7&descrip=很高兴与您合作&photoList=json数组集合&descrip=很好

返回结果示例：
```json
{
    "code": 0,
    "data":"null"
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确



<h2 id="3">3.删除客照</h2>

> 化妆师删除客照

请求方法：nggirl/app/bus/post/delete/1.3.0

请求URL：接口地址/nggirl/app/bus/post/delete/1.3.0

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称	|参数含义
|---|---|
|accessToken|登陆令牌（必填）
|postId|客照id


请求示例：

> http://nggirl/app/bus/post/delete/1.3.0?app_id=14316&nonce=uyxxd&timestamp=1427814380&sign=hEnqQoYQgMX7BTurINs5BZ8InKI9FP&pageNum=1&pageSize=20&accessToken=ab3582cb4d3f45edb6e010359559f6e7&postId=23

返回结果示例：
```json
{
    "code": 0,
    "data":"null"
}
```
返回字段说明：

|字段名|字段含义|
|---|---|
|Code	|错误码，0表示正确

