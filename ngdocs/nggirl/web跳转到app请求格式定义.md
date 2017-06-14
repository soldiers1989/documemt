# web浏览器跳转到app请求格式定义

推送消息、h5页面、短信中的链接，需要跳转到原生页面的数据格式

请求格式：
> schema://host/跳转页面标识?参数列表

iOS通过schema机制定义；安卓通过intent的filter机制定义。

请求格式中每段的含义：

请求|意义|示例
---|---|---
schema|请求协议名|设置为nggirl
host|请求域名|设置为nggirl
跳转页面标识|枚举值|special
参数列表|key=value&格式|specialId=123&specialName=青春特辑

请求标识中跳转页面标识的枚举值：

值|对应页面|对应的参数列表|参数说明|完整请求格式|
---|---|---|---|---
special|美妆专题|specialId=123&specialName=青春特辑||nggirl://nggirl/special?specialId=123&specialName=青春特辑
dresser|跳转到化妆师个人页面|dresserId=123&dresserName=小静||nggirl://nggirl/
afternoontea|跳转到下午茶页面|type=1&atId=123&atName=美妆下午茶（其中type固定为1）||nggirl://nggirl/afternoontea?type=1&atId=123&atName=美妆下午茶
webview|跳转到webview打开页面|url=http://cli.nggirl.com.cn/nggirl/h5/mobile/focuscontent.html?contentId=356 ||nggirl://nggirl/webview?url=http://cli.nggirl.com.cn/nggirl/h5/mobile/focuscontent.html?contentId=356
cosmOrder|跳转到上门美妆订单列表|无||nggirl://nggirl/cosmOrder
atorder|跳转到下午茶订单列表|无||nggirl://nggirl/atorder
coupon|跳转到南瓜券页面|无||nggirl://nggirl/coupon
column|帖子专栏页面|columnId=1&columnName=种草间||nggirl://nggirl/column?columnId=1&columnName=种草间
post|帖子详情页面|postId=1&postType=1&postTitle=补水又锁水的Bicelle全系列大放送||nggirl://nggirl/post?postId=1&postType=1&postTitle=补水又锁水的Bicelle全系列大放送
workType|上门美妆妆容作品列表页面|typeName=职业妆||nggirl://nggirl/workType?typeName=职业妆
work|上门美妆作品详情页|workId=1||nggirl://nggirl/work?workId=1
postMsg|我的评论消息页面|无||nggirl://nggirl/postMsg
checkin|日签页面|无||nggirl://nggirl/checkin
cosmeticTrial|试用活动页面|cosmeticId=1||nggirl://nggirl/cosmeticTrial?cosmeticId=1
hotTopic |热门话题页面 |topicId=1||nggirl://nggirl/hotTopic?topicId=1
itemDetail |商品详情页面|type=1&itemId=1|type=0跳到老商品详情页面，type=1跳到新的商品详情页面|nggirl://nggirl/itemDetail?type=1&itemId=1
labelPost | 标签对应帖子页面 | label=瘦身 |label是标签名称|nggirl://nggirl/labelPost?label=瘦身|


注意：

1，下午茶详情页afternoontea的入参atId要传入unionproduct表的id，而不是at_afternoontea表的id

2，日签跳转功能只能发送给2.3.0及以上版本的app

> 如果要借助url跳转到上述地址，需要依托于以下的h5页面。以下是跳转到优惠券页面的url：
>http://cli.nggirl.com.cn/nggirl/h5/mobile/loadAppHome.html?toUrl=nggirl://nggirl/coupon

# app内部的webview跳转到app原生页面

其他的请求格式和外部web浏览器跳转到app原生页面的请求格式一致。这里仅列出外部页面没有的跳转到登录页面的跳转格式。

## 内部webview跳转到app登录页面的url请求格式：

nggirl://nggirl/login?backUrl=http://cli.nggirl.com.cn/nggirl/h5/cosmetic/index.html

> 其中，backUrl是登录成功后，重新打开webview时，需要加载的页面地址。

# 帖子内容中的链接跳转

其他的请求格式和外部web浏览器跳转到app原生页面的请求格式一致。这里只这里只列出跳到用户主页的跳转格式

值|对应页面|对应的参数列表
---|---|---
userHome|用户主页|userId=232

----------------------------------------------------------

# H5直接调用app的接口

1.写入分享信息

App端方法签名： void configShareInfo(title, content, pictureUrl, pageUrl);

app中测试用h5页面：http://testcli.nggirl.com.cn/nggirl/h5/mobile/testShare.html

h5端调用方式：window.ngjsInterface.configShareInfo(title, content, pictureUrl, pageUrl);
