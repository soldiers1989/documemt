<h1>部署环境说明</h1>

<h2 id="1">1.正式服务器接口地址：</h2>

```
1. C端：
> https://cli.nggirl.com.cn/nggirl/app/cli
2. B端
> https://bus.nggirl.com.cn/nggirl/app/cli
3. 图片服务器
> https://photos.nggirl.com.cn/nggirl/app/cli
```

<h2 id="2">2.测试服务器接口地址：</h2>

```
1. C端：
> https://testcli.nggirl.com.cn/nggirl/app/cli
2. B端
> https://testbus.nggirl.com.cn/nggirl/app/cli
3. 图片服务器
> https://testphotos.nggirl.com.cn/nggirl/app/cli
```

<h2 id="3">3.所有请求参数有2部分构成：系统参数+应用参数。其中绿色标明的参数为非必须参数
系统参数：</h2>

|参数名称	|参数含义|备注|
|---|---|---|
|app_id	|服务器端定义app id|例如：ios设备是123456，h5页面是h5gzh，安卓的是各个渠道代码|
|nonce	|随机参数字符串||
|timestamp	|请求时间戳|时间戳，一个十位的数字|
|sign	|请求签名|根据系统参数和应用参数，结合渠道密钥生成的一个字符串|
|version|程序版本|例如2.0，2.5|
|build|程序构建版本|例如0，1，2，3|
|udid|设备编号|安卓设备号IMEI码，ios的是IDFA，h5页面固定是h5|
|devicemodel|设备类别|安卓系统的h5页面是android，ios系统的h5页面固定是iphone|
|sysname|系统名称|安卓系统的h5页面是android，ios系统的h5页面固定是ios|
|sysversion|系统版本|h5页面请求为空|

> 示例：1.0.4版本的version为1.0，build为4.

> 当前版本不被支持时，返回的错误码为2.前台需要提示“接口已经进行了较大的改进，请您更新到最新版本.”。



<h2 id="4">4.签名算法说明：</h2>

```
1.	将请求的所有参数（包括系统参数和应用参数，不包含sign和资源类型文件）依照key name做快速排序
2.	将排序后的参数使用&符号，依照key=value的形式连接成一个字符串，并在字符串尾拼接app secret。示例：[app_id=123456&nonce=8g6a4op8&phoneNum=18701659901&timestamp=1436780669&123456]
3.	计算拼接后字符串的MD5值，作为本次请求的sign
```
