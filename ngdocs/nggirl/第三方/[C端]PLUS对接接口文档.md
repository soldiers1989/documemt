<h1>PLUS对接接口文档</h1>
目录

* [1.概述](#1)
* [2.总体约束](#2)
* [3.接口协议](#3)  
 * [3.1用户登录接口](#3.1) 
 * [3.2获取PLUS用户信息接口](#3.2) 
 * [3.3订单状态变化通知接口](#3.3) 
 * [3.4我要预约](#3.4)

   



<h2 id="1">1.概述</h2>

> 1.1.关于PLUS

> PLUS作为一款由承影互联（北京）科技有限公司精心打造的摄影服务O2O APP，定位为“精选摄影服务”，旨在为用户提供最好的拍摄体验和服务，为用户定制专属影像记忆。
目前PLUS上能提供的摄影服务类型包括定制写真、个性婚纱、婚礼纪实、人物肖像、商业拍摄和旅行跟拍。同时PLUS也能根据用户个性化需求，提供拍摄服装、化妆造型、摄影棚等摄影相关服务，为用户打造高品质全方位的摄影体验。PLUS还开通了企业官方微信服务号，用户可以通过微信公众平台直接下单预约摄影服务并了解PLUS最新消息及活动。
在推出PLUS的同时，承影互联还推出了一款专门针对摄影师的应用：PLUS SPACE。PLUS SPACE不仅仅是PLUS上摄影师的接单工具，也是一款为专为摄影师设计的职业管理工具。通过PLUS SPACE，摄影师可以详细记录拍摄事项、设计摄影作品套系及导入订单等。除了工具的属性，PLUS SPACE也为入驻摄影师提供优质的摄影上下游资源，包括拍摄服装、道具、妆发造型服务、场地、摄影器材、及成品印刷输出等。

> 1.2.接口设计背景

> PLUS SPACE作为PLUS App面向摄影师的手机端应用，需要为摄影师提供一站式的上下游资源，南瓜姑娘（App）平台具备的大量优质化妆师资源是其中重要的一项。两者的对接具有互利互惠的双赢效益，一方面PLUS能够借助南瓜姑娘（App）的化妆师资源提供更好的整合效果，形成服务完善的平台优势；另一方面南瓜姑娘（App）可以借助PLUS的优质摄影师资源以及摄影订单，增加美妆接单数量。
该文档描述的是PLUS集成南瓜姑娘，双方需要互访的相关的接口。

> 1.3.文档范围

> 本文档描述了接口协议，以及数据示例。

> 1.4.阅读对象

> 南瓜姑娘（App）、PLUS App的产品经理、开发人员、测试人员、运维人员。




<h2 id="2">2.总体约束</h2>

> 2.1.传输方式

> 所有接口调用均以http协议进传输，一次web请求即为一次接口调用。

> 所有请求参数有2部分构成：系统参数+应用参数。系统参数见下表描述，应用参数每个接口不同，按照接口需要定义，应用参数需要加密传输，加密方式见2.2节。


系统参数：

|参数名称|	参数含义|
|---|---|
|app_id | 服务端定义的appid（不同的渠道有独立的appid值）
|nonce	|随机参数字符串（选填）
|timestamp|	请求时间戳（选填）
|version	|程序版本
|build	|程序构建版本

> 关于version和build的说明：1.0.4版本的version为1.0，build为4. 当前版本不被支持时，返回的错误码为2.前台需要提示“接口已经进行了较大的改进，请您更新到最新版本.”。

> 2.2.加密方式

> 形式：<接口url>?请求串

> 其中：

> （1）接口url，是双方约定的url地址

> （2）请求串 = params_encoded&sign=signvalue

> 其中：

> （A）params_encoded是系统参数和应用参数值的拼接串。

> （B）单个参数加密：所有应用参数（2.1中的系统参数不参与加密）取值使用3des加密算法加密并以base64编码，密钥由双方约定
> （C）校验码算法：signvalue=MD5（params_encoded&plusspace_secret）

参数举例：
假设平台A提供了一个接口 http://www.abc.com/interface ，按照该接口协议约定，PLUSSPACE需要在请求时携带如下参数：

|参数名	|取值|	特性|
|----|----|----|
|app_id	|plusspace|	原始值
|nonce	|uyxxd	|原始值
|timestamp|	1427814380|	原始值
|version|	1.3|	原始值
|build	|4	|原始值
|param1	|value1	|
|param2	|value2	|
|param3	|value3	|
|Sign	|hEnqQoYQgMX7BTurINs5BZ8InKI9FP	|参数签名


> 则此表的加密前的参数串params和加密后的参数串params_encoded的计算方法为：

> params = param1=value1&param2=value2&param3=value3

> params_encoded = app_id=plusspace&nonce=uyxxd&timestamp=1427814380&version=1.3&build=4&param1=base64_encode(3des(value1))&param2=base64_encode (3des(value2))&param3=base64_encode (3des(value3))

> 同时，signvalue=MD5(params_encoded&plusspace_secret)[需要特别注意，和投之家的接口不同]
其中plusspace_secret由双方约定。

> 随后，PLUS SPACE构造的的完整请求地址是：
http://www.abc.com/interface.php? params_encoded&sign= signvalue
以上是GET方式传输数据的加密方式，当以POST方式传输数据时，没有“参数串”形式，参数是直接post传输的，校验码算法与GET方式相同。

> 2.3.解密算法
接收方接收到数据，依照协议，进行解密进行校验码校验：

> （1）接收方取出请求串中的params_encoded 与signvalue；

> （2）从params_encoded中拿到请求来源参数app_id，查表得到约定的plusspace_secret和3des密钥；

> （3）计算params_encoded的MD5，验证是否与请求串中的signvalue一致；

> （4）根据3des密钥对params_encoded解密，得到请求字符串原文；

> （5）上述所有步骤完全通过，则解密完整，可以进行接口的具体处理逻辑

> 2.4.加密算法

> 请求串中的每一项应用参数（不包含系统参数），均单独使用3des加密算法加密，并以base64编码。3des密钥由双方在联调时约定。

> 字符集

> 所有URL参数字符集均使用UTF-8

> 2.5.时间表达

> 所有涉及到年月日时分秒具体的时间格式统一使用时间的毫秒表示，如2014/06/25 17:05:08:391应表达成整数：1403687768391


<h2 id="3">3.接口协议</h2>

![用户静默登录流程图](http://photosd.nggirl.com.cn/work/338cbf6249b94d55880cd65a3d6086ae.png "Title")

<h3 id="3.1">3.1用户登录接口</h3>

> 用户在PLUS平台登录南瓜姑娘App时，调用南瓜姑娘提供的第三方免密码登录接口，实现用户登录，登录成功后后台自动重定向到南瓜姑娘h5首页。

请求方法：平台url：/nggirl/app/thirdchannel/login?参数串

请求URL：平台url：/nggirl/app/thirdchannel/login?参数串

HTTP请求方式：POST

|参数名|描述|类型|参数取值|是否必填|
|---|---|---|---|---|
|app_id|	应用编号|	字符串|	plusspace|	必填
|nonce	|随机字符串	|字符串	|uyxxd	|必填
|timestamp|	时间戳	|字符串	|1427814380|	必填
|version|	版本	|字符串	|1.3	|必填
|build	|构建版本	|字符串	|4	|必填
|ptoken	|用户在PLUS的授权令牌|	字符串|	Jkldsfidkl2323|	必填
|sign	|签名|	字符串	|参考验证码算法	|必填

请求示例：
> localhost://nggirl/app/thirdchannel/login?app_id=plusspace&nonce=uyxxd&timestamp=1427814380
&version=1.3&build=4&ptoken=Jkldsfidkl2323&sign=Jkldsfidkl2323



<h3 id="3.2">3.2获取PLUS用户信息接口</h3>

> 南瓜姑娘服务器接受到来自PLUS的静默登录请求后，请求处理过程中使用请求携带的ptoken向PLUS服务器请求用户信息。

请求方法：平台url：url?参数串

请求URL：平台url：url?参数串

HTTP请求方式：POST

|参数名|描述|类型|参数取值|是否必填|
|----|----|----|----|----|
|app_id|应用编号|字符串|plusspace|必填
|nonce|随机字符串|字符串|uyxxd|必填
|timestamp|时间戳|字符串|1427814380|必填
|version|版本|字符串|1.3|必填
|build|构建版本|字符串|4|必填
|ptoken|PLUS用户授权令牌|字符串|Asdfasglasg|必填
|sign|签名|字符串|参考验证码算法|必填

请求示例:
> 平台url:url?app_id=plusspace&nonce=uyxxd&timestamp=1427814380
&version=1.3&build=4&ptoken=Jkldsfidkl2323&sign=Jkldsfidkl2323

返回结果示例：

```json
{
	"code":0,
	"data":{
		"thirdUserId":"User12345",
		"telephone":"18518676735",
		"username":"PLUS精选",
		"profile":"http://cli.nggirl.com.cn/ng-mobile-web/tuiguang/images/momo_sec/mo-04_03.png",
		"sex":0,
		"birthday":"2015-05-12",
		"district":"北京市朝阳区",
		"address":"团结湖嘉盛中心2006"
	}
}
```

返回值字段描述：

|参数名|描述|类型|参数取值|是否必填|
|----|----|----|----|----|
|thirdUserId|PLUS用户编号|字符串|User12345|必填
|telephone|PLUS用户电话|字符串|18518676735|必填
|username|PLUS用户名|字符串|PLUS精选|必填
|profile|PLUS用户头像|字符串|http://cli.nggirl.com.cn/ng-mobile-web/tuiguang/images/momo_sec/mo-04_03.png|必填
|sex|PLUS用户性别（0女，1男）|数值|0|必填
|birthday|PLUS用户生日|字符串|2015-05-12|必填
|district|PLUS用户城区|字符串|北京市朝阳区|必填
|address|PLUS用户地址|字符串|团结湖嘉盛中心2006|必填


<h3 id="3.3">3.3订单状态变化通知接口</h3>

> 当PLUS静默登录南瓜姑娘的用户下单及订单状态变化时，南瓜姑娘调用PLUS的该接口将消息推送给PLUS

请求方法：平台url：url?参数串

请求URL：平台url：url?参数串

HTTP请求方式：POST

|参数名|描述|类型|参数取值|是否必填|
|----|----|----|----|----|
|app_id|应用编号|字符串|plusspace|必填
|nonce|随机字符串|字符串|uyxxd|必填
|timestamp|时间戳|字符串|1427814380|必填
|version|版本|字符串|1.3|必填
|build|构建版本|字符串|4|必填
|thirdUserId|用户在PLUS编号|字符串|User12345|必填
|reservationId|订单编号|字符串|2015121202314569|必填
|dresserProfile|化妆师头像|字符串|http://testphotosd.nggirl.com.cn/work/327bc7039b3e4cce8daf711ca0dd63b3.jpg|必填
|dresserName|化妆师姓名|字符串|美丽海岸|必填
|workType|预约妆型名称|字符串|新娘妆|必填
|cost|花费金额|Decimal(10,2)|300.00|必填
|reservationTime|预约时间段|字符串|2015年12月23日 16:00-18:00|必填
|reservationAddress|预约地址|字符串|北京朝阳区常营蓝天小区2栋5单元|必填
|cover|预约妆型封面|字符串|http://testphotosd.nggirl.com.cn/work/11e458134d64410aa9d2f80101a7a776.jpg|必填
|statusDesc|预约状态描述|字符串|等待化妆师接单|必填
|sign|签名|字符串|参考验证码算法|必填


<h3 id="3.4">3.4我要预约</h3>

请求方法：nggirl/app/thirdchannel/getReservationForPlus

请求URL：接口地址/nggirl/app/thirdchannel/getReservationForPlus

支持格式：JSON

HTTP请求方式：POST

应用请求参数：

|参数名称|参数含义|
|---|---|
|app_id|应用编号
|nonce|随机字符串
|timestamp|时间戳
|version|版本
|build|构建版本
|accessToken|用户授权令牌
|workId|作品编号
|reservationTime|预约时间
|reservationAddress|预约地址
|phoneNum|预约电话号码

请求示例：

 > http://localhost/nggirl/app/app/thirdchannel/getReservationForPlus?accessToken=ACCESS_TOKEN&app_id=14314&nonce=uyxxd&timestamp=1427814380&version=1.0&build=4&reservationTime=2015
年6月8日15:30-16:00&reservationAddress=北京朝阳区&phoneNum=010888888

返回结果示例：

```json
{
	"code":0,
	"data":{
		"reservationId":123456
	}
}
```

返回字段说明：

|字段名称|字段含义|
|---|---|
|Code |错误码，0表示正确
|Data - reservationId|预约编号


