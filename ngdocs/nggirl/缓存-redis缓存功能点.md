# Redis缓存功能点

## 数据库0中缓存的内容

>数据库0中的缓存在每次构建项目或者启动项目的时候会被清空一次，详见nggirl项目的定时任务ClearRedisKeysTask

>数据库0中缓存的内容，有效期为10分钟

>可以通过在接口中添加清除点，可以清除缓存

---

* [1.化妆师信息缓存](#1)
  * [1.1.作品详情-化妆师基本信息](#1.1)
  * [1.2.作品详情-化妆师商圈](#1.2)
  * [1.3.沙龙详情-化妆师基本信](#1.3)
* [2.作品信息缓存](#2)
  * [2.1.作品详情-作品基本信息](#2.1)
  * [2.2.作品详情-作品使用的化妆品品牌](#2.2)
* [3.沙龙信息缓存](#3)
  * [3.1.沙龙详情-沙龙基本信息](#3.1)
* [4.用户信息缓存](#4)
  * [4.1.用户个人资料](#4.1)
* [5.日签信息缓存](#5)
  * [5.1.日签基本信息](#5.1)
  * [5.2.日签推荐商品信息](#5.2)
  * [5.3.日签-用户本月日签签到记录](#5.3)
  * [5.4.日签-用户是否允许推送日签每日提醒](#5.4)
  * [5.5.日签-用户注册时间](#5.5)
* [6.帖子信息缓存](#6)
  * [6.1.文章帖子详情](#6.1)
  * [6.2.视频帖子详情](#6.2)
  * [6.3.首页-专栏列表一页数据](#6.3)
  * [6.4.首页-专栏列表-文章帖子列表](#6.4)
  * [6.5.首页-专栏列表-视频帖子列表](#6.5)

* [7.商品信息缓存](#7)

  * [7.1.商品详情缓存](#7.1)

* [8.缓存清除接口](#8)


<h2 id="1">1.化妆师信息缓存</h2>

<h3 id="1.1">1.1.作品详情-化妆师基本信息</h3>

>version接口版本，dresserId化妆师id

| 名 | 值 |
| :--- | :--- |
|缓存内容|作品详情-化妆师基本信息|
|value|CliDresserDetail|
|key|getCliDresserDetailV#{version}-#{dresserId}|
|nggirl缓存接口|/cli/works/getWorksDetail/1.5.0 <br/> /cli/works/getWorksDetailIos/1.5.0|
|nggirl清理接口|/bus/personalInfo/updateUserInfo/1.3.0 <br/> /bus/phoneUser/uploadUserInfo/1.3.0 |
|nggirl-web清理接口|/admin/dresser/updateDresser/#{version} <br/> /admin/dresser/addv <br/> /admin/dresser/cancelCertification <br/> /admin/dresser/certification <br/> /admin/dresser/subv|

<h3 id="1.2">1.2.作品详情-化妆师商圈</h3>

>version接口版本，dresserId化妆师id

| 名 | 值 |
| :--- | :--- |
|缓存内容|作品详情-化妆师商圈|
|value|DresserBizAreas|
|key|getBizAreasV#{version}-#{dresserId}|
|nggirl缓存接口|/cli/works/getWorksDetail/1.5.0 <br/> /cli/works/getWorksDetailIos/1.5.0|
|nggirl清理接口|/bus/personalInfo/saveDresserBizAreas/1.3.0 <br/> /bus/personalInfo/updateUserInfo/1.3.0|
|nggirl-web清理接口|/admin/dresser/saveDresserBizAreas/1.5.0|

<h3 id="1.3">1.3.沙龙详情-化妆师基本信</h3>

>version接口版本，dresserId化妆师id

| 名 | 值 |
| :--- | :--- |
|缓存内容|沙龙详情-化妆师基本信|
|value|CliSalonDresserDetail|
|key|getCliSalonDresserDetailV#{version}-#{dresserId}|
|nggirl缓存接口|/cli/works/getWorksDetail/1.5.0 <br/> /cli/works/getWorksDetailIos/1.5.0|
|nggirl清理接口|/bus/personalInfo/updateUserInfo/1.3.0 <br/> /bus/phoneUser/uploadUserInfo/1.3.0|
|nggirl-web清理接口|/admin/dresser/updateDresser/#{version} <br/> /admin/dresser/addv <br/> /admin/dresser/cancelCertification <br/> /admin/dresser/certification <br/> /admin/dresser/subv|

<h2 id="2">2.作品信息缓存</h2>

<h3 id="2.1">2.1.作品详情-作品基本信息</h3>

>version接口版本，workId作品id

| 名 | 值 |
| :--- | :--- |
|缓存内容|作品详情-作品基本信息|
|value|CliWorkDetail|
|key|getCliWorkDetailV#{version}-#{workId}|
|nggirl缓存接口|/cli/works/getWorksDetail/1.5.0 <br/> /cli/works/getWorksDetailIos/1.5.0|
|nggirl清理接口|/bus/works/deleteWork <br/> /bus/works/updateWork/1.1.0|
|nggirl-web清理接口|/admin/work/updateWork/#{version} <br/> /admin/work/deleteWork <br/> /admin/work/workRecommend <br/> /admin/work/cancelWorkRecommend <br/> /admin/work/audit/1.4.1|

<h3 id="2.2">2.2.作品详情-作品使用的化妆品品牌</h3>

>version接口版本，workId作品id

| 名 | 值 |
| :--- | :--- |
|缓存内容|作品详情-作品使用的化妆品品牌|
|value|CliDresserDetail|
|key|getWorkCosmeticsV#{version}-#{workId}|
|nggirl缓存接口|/cli/works/getWorksDetail/1.5.0 <br/> /cli/works/getWorksDetailIos/1.5.0|
|nggirl清理接口| /bus/works/deleteWork <br/> /bus/works/updateWork/1.1.0|
|nggirl-web清理接口|/admin/work/updateWork/#{version} <br/> /admin/work/deleteWork <br/> /admin/work/workRecommend <br/> /admin/work/cancelWorkRecommend <br/> /admin/work/audit/1.4.1|

<h2 id="3">3.沙龙信息缓存</h2>

<h3 id="3.1">3.1.沙龙详情-沙龙基本信息</h3>

>version接口版本，unionProductId联合产品id

| 名 | 值 |
| :--- | :--- |
|缓存内容|沙龙详情-沙龙基本信息|
|value|CliSalonDetail|
|key|getSalonDetailV#{version}-#{unionProductId}|
|nggirl缓存接口|/cli/salon/works/salonProductDetail/1.5.0|
|nggirl清理接口||
|nggirl-web清理接口|/admin/salon/work/addIntroduce/#{version} <br/> /admin/salon/work/addDresserInfo/#{version} <br/> /admin/salon/work/addResNotice <br/> /admin/salon/work/setOnline <br/> /admin/salon/work/updateWork/#{version} <br/> /admin/salon/work/updateIntroduce/#{version} <br/> /admin/salon/work/updateDresserInfo/#{version} <br/> /admin/salon/work/updateResNotice <br/> /admin/salon/work/delIntroduce <br/> /admin/salon/work/delDresserInfo <br/> /admin/salon/work/delResNotice |

<h2 id="4">4.用户信息缓存</h2>

<h3 id="4.1">4.1.用户个人资料</h3>

>version接口版本，userId用户id

| 名 | 值 |
| :--- | :--- |
|缓存内容|用户个人资料|
|value|CliUserInfo|
|key|getUserInfoV#{version}-#{userId}|
|nggirl缓存接口|/cli/personalInfo/getUserInfo/1.5.0|
|nggirl清理接口|/cli/phoneUser/uploadUserInfo/1.5.0 <br/>/cli/phoneUser/uploadUserInfo/2.1.0|
|nggirl-web清理接口||

<h2 id="5">5.日签信息缓存</h2>

<h3 id="5.1">5.1.日签基本信息</h3>

>version版本号，date是yyyy-MM-dd格式的日期

```java
expireCacheUtil.expireKeys("getCheckinEveryDayInfoV*")
```

| 名 | 值 |
| :--- | :--- |
|缓存内容|日签基本信息|
|value|CheckinEveryDayInfo|
|key|getCheckinEveryDayInfoV#{version}-#{date}|
|nggirl缓存接口|/cli/personalInfo/getCheckinPage/2.3.0 <br/> /cli/personalInfo/checkin/2.3.0|
|nggirl清理接口||
|nggirl-web清理接口|/admin/checkin/deleteCheckin/2.3.0 <br/> /admin/checkin/updateCheckin/2.3.0 |

<h3 id="5.2">5.2.日签推荐商品信息</h3>

>version版本号，date是yyyy-MM-dd格式的日期

```java
expireCacheUtil.expireKeys("getCheckinEveryDayDetailListV*")
```

| 名 | 值 |
| :--- | :--- |
|缓存内容|日签推荐商品信息|
|value|CheckinEveryDayDetails|
|key|getCheckinEveryDayDetailListV#{version}-#{checkinInfoId}|
|nggirl缓存接口|/cli/personalInfo/getCheckinPage/2.3.0 |
|nggirl清理接口||
|nggirl-web清理接口|/admin/checkin/deleteCheckin/2.3.0 <br/> /admin/checkin/updateCheckin/2.3.0 |

<h3 id="5.3">5.3.日签-用户本月日签签到记录</h3>

>version版本号，yearMonth是yyyyMM格式的年月

```java
expireCacheUtil.expireKeys("getCheckinRecordThisMonthV*-" + UserContext.getUser().getUserId() + "*")
```

| 名 | 值 |
| :--- | :--- |
|缓存内容|用户本月日签签到记录|
|value|CheckinRecord|
|key|getCheckinRecordThisMonthV#{version}-#{yearMonth}|
|nggirl缓存接口|/cli/personalInfo/getCheckinPage/2.3.0 <br> /cli/personalInfo/getCheckinCalendar/2.3.0 <br/> /cli/personalInfo/checkin/2.3.0 |
|nggirl清理接口|/cli/personalInfo/checkin/2.3.0 |
|nggirl-web清理接口||

<h3 id="5.4">5.4.日签-用户是否允许推送日签每日提醒</h3>

>version版本号，userId用户id

```java
@CacheEvict(value = "AllowCheckinPush", key = "'isAllowCheckinPushV230-'.concat(#root.args[0].toString())")
```

| 名 | 值 |
| :--- | :--- |
|缓存内容|用户是否允许推送日签每日提醒|
|value|AllowCheckinPush|
|key|isAllowCheckinPushV#{version}-#{userId}|
|nggirl缓存接口|/cli/personalInfo/getCheckinPage/2.3.0|
|nggirl清理接口|/cli/personalInfo/changePushStatus/2.3.0|
|nggirl-web清理接口||

<h3 id="5.5">5.5.日签-用户注册时间</h3>

>version版本号，userId用户id

>因为用户注册时间是永远不会变的，所以不需要显式的调用接口清除

| 名 | 值 |
| :--- | :--- |
|缓存内容|用户注册时间|
|value|UserRegisterTime|
|key|getUserRegisterTimeV#{version}-#{userId}|
|nggirl缓存接口||
|nggirl清理接口||
|nggirl-web清理接口||

<h2 id="6">6.帖子信息缓存</h2>

<h3 id="6.1">6.1.文章帖子详情</h3>

>version版本号，postId帖子id，postType帖子类型

| 名 | 值 |
| :--- | :--- |
|缓存内容|文章帖子详情|
|value|PostArticleDetailV#{version}|
|key|getArticlePostDetailV#{version}-#{postId}#{postType}|
|nggirl缓存接口|/cli/post/getArticlePostDetail/#{version}|
|nggirl清理接口||
|nggirl-web清理接口| /admin/column/addOrUpdateArticlePost/#{version} <br/> /admin/column/deletePost/2.0.0 |

<h3 id="6.2">6.2.视频帖子详情</h3>

>version版本号，postId帖子id，postType帖子类型

| 名 | 值 |
| :--- | :--- |
|缓存内容|视频帖子详情|
|value|PostVideoDetailV#{version}|
|key|getVideoPostDetailV#{version}-#{postId}#{postType}|
|nggirl缓存接口|/cli/post/getVideoPostDetail/#{version}|
|nggirl清理接口||
|nggirl-web清理接口|/admin/column/addOrUpdateVideoPost/#{version} <br/> /admin/column/deletePost/2.0.0 |


<h3 id="6.3">6.3.首页-专栏列表一页数据</h3>

>version版本号，pageNum页码，pageSize页面大小

| 名 | 值 |
| :--- | :--- |
|缓存内容|首页-专栏列表一页数据|
|value|SimpleViewColPostList|
|key|getSimpleAllColPostListV#{version}-#{pageNum}#{pageSize}|
|nggirl缓存接口|/cli/column/getPostList/2.0.0|
|nggirl清理接口||
|nggirl-web清理接口|/admin/column/updateBatchColIsOnline/2.0.0 <br/> /admin/column/addOrUpdateColumn/2.0.0 <br/> /admin/column/deleteColumn/2.0.0 <br/> /admin/column/addOrUpdateArticlePost/#{version} <br/> /admin/column/addOrUpdateVideoPost/#{version} <br/> /admin/column/deletePost/2.0.0 |

<h3 id="6.4">6.4.首页-专栏列表-文章帖子列表</h3>

>version版本号，ids文章帖子id列表

| 名 | 值 |
| :--- | :--- |
|缓存内容|首页-专栏列表-文章帖子列表|
|value|ArticlePostsList|
|key|getArticlePostsListByPostIdsV#{version}-#{ids}|
|nggirl缓存接口|/cli/column/getPostList/2.0.0 <br/> /cli/column/getPostListByColumn/2.0.0 |
|nggirl清理接口||
|nggirl-web清理接口|/admin/column/addOrUpdateArticlePost/#{version}|

<h3 id="6.5">6.5.首页-专栏列表-视频帖子列表</h3>

>version版本号，ids视频帖子id列表

| 名 | 值 |
| :--- | :--- |
|缓存内容|首页-专栏列表-视频帖子列表|
|value|VideoPostsList|
|key|getVideoPostsListByPostIdsV#{version}-#{ids}|
|nggirl缓存接口|/cli/column/getPostList/2.0.0 <br/> /cli/column/getPostListByColumn/2.0.0 |
|nggirl清理接口||
|nggirl-web清理接口|/admin/column/addOrUpdateVideoPost/#{version}|


<h2 id="7">7.商品信息缓存</h2>

<h3 id="7.1">7.1.商品详情缓存</h3>

>version版本号，seedProductId商品id

| 名 | 值 |
| :--- | :--- |
|缓存内容|商品详情|
|value|ViewSeedProductDetail|
|key|getSeedProductDetailV{version}-#{seedProductId}|
|nggirl缓存接口|/cli/post/getSeedProductDetail/#{version}|
|nggirl清理接口||
|nggirl-web清理接口| /admin/comodity/addOrEdit/#{version} <br/> /admin/comodity/delete/#{version} |






## 数据库1中缓存的内容

>数据库1中存的对象都是hash对象

### 1.日签

日签功能中需要判断一台设备在一天之内是否已经签到了

```java
//记录--签到设备信息
redisTemplateNonFlush.opsForHash().put("device_checkin", TimeUtils.getTime(now, "yyyyMMdd") + "-" + udid, "checkin");
```

device_checkin中的键是`yyyyMMdd-设备id`形式，值是字符串`checkin`

该信息在每日凌晨会被清理一次，详见nggirl项目的定时任务ClearDeviceCheckinRedisKeysTask

### 2.每日积分

|每日积分类型|数据库1中对应的key|
| :--- | :--- |
|今日点赞获取的积分|cnt:user:score:praise|
|今日收藏积分的积分|cnt:user:score:collect|
|今日评论积分的积分|cnt:user:score:comment|
|今日分享获取的积分|cnt:user:score:share|
|今日点赞、收藏、评论、分享获取的总积分|userGainScoreToday|

对象的键是`user_ + 用户id`，值是积分总数

每日积分会在每日凌晨清理一次，详见nggirl项目的定时任务ClearUserScoreRedisKeysTask

### 3.帖子浏览数量

帖子详情中的浏览数量存储在counter:postViewNum对象中，键是`postType:postId`形式，值是帖子浏览数量

创建帖子时会初始化一个随机值，获取帖子时将该值取出




<h2 id="8">8.缓存清除接口</h2>

接口地址：nggirl/app/cache/clearPatternKeys

参数:

|参数名称|参数含义|
|---|---|
|pattern|【必填】需要清除的key，支持正则匹配|
|userId|【必填】系统中用户id|
|accessToken|【必填】授权令牌|

> 只有通过accessToken查出来的userId跟传入的userId匹配上，才可以清除缓存
