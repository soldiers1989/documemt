# nggirl项目配置文件spring/config/configuration.properties文件说明

>local下配置文件，是测试环境配置，只是适用于testcli.nggirl.com.cn服务器

>remote下配置文件，是正式环境配置，只适用于cli.nggirl.com.cn服务器


## 参数

|key|value|备注|
|:---|:---|:---|
|application.parameter.sys.minsupport.version|1.0||
|application.parameter.sys.admin.phones|18518676735||
|application.parameter.sys.default.check.code.len|4||
|application.parameter.sys.default.check.code.range|10000||
|application.parameter.sys.image.upload.server|http://testphotos.nggirl.com.cn||
|application.parameter.check.AppIds|123456;789012;_360;baidu||
|application.parameter.check.AppSecrets|123456;123456;Nguser_123||
|application.parameter.regist.validate.code.expire|1800000||
|application.parameter.ihuyi.url| http://106.ihuyi.cn/webservice/sms.php?method Submit||
|application.parameter.ihuyi.account|cf_xiaofan||
|application.parameter.ihuyi.password|fan860412503||
|application.parameter.chuanglan.url|http://222.73.117.158/msg/HttpBatchSendSM||
|application.parameter.chuanglan.account|vipbjxyqm||
|application.parameter.chuanglan.password|Tch123456||
|application.parameter.im.user.url|http://a1.easemob.com/nggirl/nggirl/users||
|application.parameter.im.token.url|https://a1.easemob.com/nggirl/nggirl/token||
|application.parameter.im.client.id|YXA6jLR6YDaAEeWipHUPn-41yw||
|application.parameter.im.client.secret|YXA68liPBkb-uOsEOq58mqX7s1-J2Ic||
|application.parameter.im.dresser.prefix|test_dresser_||
|application.parameter.im.user.prefix|test_user_||
|application.parameter.dresser.default.profile|||
|application.parameter.dresser.default.bgimage|http://photosd.nggirl.com.cn/sysres/bgimage.jpg||
|application.parameter.dresser.default.start.level|2||
|application.parameter.dresser.default.authentication|0||
|application.parameter.user.default.profile|||
|application.parameter.user.default.bgimage|http://photosd.nggirl.com.cn/sysres/bgimage.jpg||
|application.parameter.user.default.score|0||
|application.parameter.user.default.nick.prefix|||
|application.parameter.user.invitation.default.allowed.times|3||
|application.parameter.upload.user.endpoint|http://oss-cn-qingdao.aliyuncs.com/||
|application.parameter.upload.accessid|w2TmyqngBesZxCcH||
|application.parameter.upload.accesskey|MHgjrP8VsOIImiwzazuChV2sFd3Mm7||
|application.parameter.upload.sys.buck.name|sysresources||
|application.parameter.upload.user.buck.name|userresources||
|application.parameter.upload.user.buck.work.directory|work||
|application.parameter.coupon.isValidForver|1||
|application.parameter.coupon.validTime|30||
|application.parameter.coupon.initialMoney|30.0||
|application.parameter.coupon.first.regist.amount|30||
|application.parameter.reservation.times|06:00 - 06:20;06:20 - 06:40;06:40 - 07:00;07:00 - 07:20;07:20 - 07:40;07:40 - 08:00;08:00 - 08:20||
|application.parameter.reservation.expire.time|900000||
|application.parameter.reservation.autofinish.time|21600000||
|application.parameter.score.max.perday|20||
|application.parameter.score.evaluation|3||
|application.parameter.score.share|5||
|application.parameter.score.regist|10||
|application.parameter.score.praise|1||
|application.parameter.score.collect|1||
|application.parameter.third.logon.weibo.url|https://api.weibo.com/2/users/show.json||
|application.parameter.third.logon.weixin.url|https://api.weixin.qq.com/sns/userinfo|||


## 百度推送配置信息

|key|value|备注|
|:---|:---|:---|
|application.parameter.baidu.push.android.bus.apikey|f1voS4P4hD0FNYhYWPboujV7|安卓B端APIKEY
|application.parameter.baidu.push.android.bus.secret|oupN4BYKtXZn7rIjadFCuTUUN47sj0aw|安卓B端SECRET
|application.parameter.baidu.push.android.cli.apikey|xBAvp9M9OHH7RCZi0TiYX6Gp|安卓C端APIKEY
|application.parameter.baidu.push.android.cli.secret|NDRbflWue9AAPDHQsV5IpWkePm3bHX6Y|安卓C端SECRET
|application.parameter.baidu.push.hosts|api.push.baidu.com,api.tuisong.baidu.com|百度推送服务器地址
|application.parameter.baidu.push.ios.bus.apikey||IOS B端APIKEY
|application.parameter.baidu.push.ios.bus.secret||IOS B端SECRET
|application.parameter.baidu.push.ios.cli.apikey|nhwviyO0mfxF7gmz9oz5AbEX|IOS C端APIKEY
|application.parameter.baidu.push.ios.cli.secret|fFzxn4hG4LiBR3QuXYIT9smdneGURmqW|IOS C端SECRET
|application.parameter.baidu.push.ios.deploy.status|2|IOS证书类型状态，1开发状态，2生产状态

## 支付宝APP支付配置

|key|value|备注|
|:---|:---|:---|
|application.parameter.alipay.config.partner|2088021065468954|合作者身份ID（PID）是商户与支付宝签约后，商户获得的支付宝商户唯一识别码
|application.parameter.alipay.seller.email|postmaster@nggirl.com.cn|商户登陆邮箱
|application.parameter.alipay.config.secure.key| |商户安全校验码
|application.parameter.alipay.private.key| |商户私钥
|application.parameter.alipay.private.key.pkcs8| |商户pkcs8格式的私钥
|application.parameter.alipay.public.key| |商户公钥
|application.parameter.alipay.refund.url|http://115.28.23.93/nggirl/app/charge/alipay/refund/confirm|支付成功后的异步通知地址

## 支付宝WEB支付配置

|key|value|备注|
|:---|:---|:---|
|application.parameter.alipayweb.itbpay.time|5m|化妆师上门教学（个人版），未付款交易的超时时间
|application.parameter.alipayweb.show.url|http://testcli.nggirl.com.cn/nggirl/h5/cosmteach/teaching-page.html|化妆师上门教学（个人版），商品展示页面
|application.parameter.alipayweb.busteach.show.url|http://testcli.nggirl.com.cn/nggirl/h5/busteach/teaching-page.html|化妆师上门教学（企业版），商品展示页面
|application.parameter.alipayweb.double11.show.url|http://testcli.nggirl.com.cn/nggirl/h5/cosmteach/teaching-page-double11.html|化妆师上门教学（个人版）-双十一活动，商品展示页面
|application.parameter.alipayweb.notify.url|http://testcli.nggirl.com.cn/nggirl/app/charge/alipayweb/confirm|化妆师上门教学（个人版），支付成功后的异步通知地址
|application.parameter.alipayweb.busteach.notify.url|http://testcli.nggirl.com.cn/nggirl/app/charge/alipayweb/busteach/confirm|化妆师上门教学（企业版），支付成功后的异步通知地址
|application.parameter.alipayweb.return.url|http://testcli.nggirl.com.cn/nggirl/app/charge/alipayweb/return|化妆师上门教学（个人版），支付成功后的返回商户地址
|application.parameter.alipayweb.busteach.return.url|http://testcli.nggirl.com.cn/nggirl/app/charge/alipayweb/busteach/return|化妆师上门教学（企业版），支付成功后的返回商户地址
|application.parameter.alipayweb.return.redirect.url|http://testcli.nggirl.com.cn/nggirl/h5/cosmteach/teaching-page.html|化妆师上门教学（个人版），支付成功后的返回商户地址后，提示成功页面
|application.parameter.alipayweb.busteach.return.redirect.url|http://testcli.nggirl.com.cn/nggirl/h5/busteach/teaching-page.html|化妆师上门教学（企业版），支付成功后的返回商户地址后，提示成功页面
|application.parameter.alipayweb.double11.return.redirect.url|http://testcli.nggirl.com.cn/nggirl/h5/cosmteach/teaching-page-double11.html|化妆师上门教学（个人版）-双十一活动，支付成功后的返回商户地址后，提示成功页面


## 微信APP支付配置

|key|value|备注|
|:---|:---|:---|
|application.parameter.weixinpay.appid|wxfe8754d4e19d9c85|微信APPID
|application.parameter.weixinpay.mchid|1259003701|微信商户id
|application.parameter.weixinpay.unified.order.url|https://api.mch.weixin.qq.com/pay/unifiedorder||
|application.parameter.weixinpay.notify.url|http://115.28.23.93/nggirl/app/charge/weixin/confirm|微信支付成功后，异步通知地址
|application.parameter.weixinpay.appkey|1a4531b137550d040c6c26ff3a26f288|微信APPKEY
|application.parameter.weixinpay.sub.mchid||微信子商户id
|application.parameter.weixinpay.cert.local.path|/wxcert/apiclient_cert.p12|微信安全证书存储路径


## 其他
|key|value|备注|
|:---|:---|:---|
|application.parameter.focus.content.preurl|http://testcli.nggirl.com.cn/nggirl/h5/mobile/focuscontent.html||
|application.parameter.jiaoxue.pay.notify.phone|18518676735||
|application.parameter.operation.staff.tel|010-58140904||
|application.parameter.feed.nanguagirl.weixinnum|nanguagirl|||
