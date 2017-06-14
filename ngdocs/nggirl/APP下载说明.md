# APP下载说明

## 一、跳转链接

|跳转地址URL|跳转地址|备注|
|---|---|---|
|`http://a.app.qq.com/o/simple.jsp?pkgname=cn.com.nggirl.nguser`|微信应用宝中的南瓜姑娘下载地址|如果是IOS中打开该地址，则会提示：是否跳转到苹果AppStore|
|`https://itunes.apple.com/cn/app/nan-gua-gu-niang-yi-jian-xia/id1014850829?l=en&mt=8`|苹果AppStore中的南瓜姑娘下载地址||


## 二、安卓APK下载地址

每次发版时都会将全部的安卓渠道包上传到阿里云服务器，可以根据最新的版本和渠道找到对应的渠道包

APK下载地址格式：

`https://photosd.nggirl.com.cn/apks/<版本号>/nguser_v<版本号>_<渠道代码>_release.apk`

例如，应用宝渠道，渠道代码`yingyongbao`，版本号`3.1.0`，则其下载地址为：

`https://photosd.nggirl.com.cn/apks/3.1.0/nguser_v3.1.0_yingyongbao_release.apk`

注意：

1，下载地址支持http和https，例如

`http://photosd.nggirl.com.cn/apks/3.1.0/nguser_v3.1.0_yingyongbao_release.apk`

和

`https://photosd.nggirl.com.cn/apks/3.1.0/nguser_v3.1.0_yingyongbao_release.apk`

均可以下载应用宝3.1.0版本APK

2，并不是每一个渠道都存在最新的APK包，例如太平洋（渠道代码`taipingyang`），该渠道早就不再更新了，每次发版该渠道不再打包，所以根据上面拼接的地址下载不到最新的APK。

所以，使用该APK地址之前，请先自行测试一下地址是否可用。

## 三、下载APP的H5页面

地址：https://cli.nggirl.com.cn/nggirl/h5/mobile/download-dailycheck.html

### 3.1 下载判断逻辑

1，如果当前位于IOS系统内：跳转到App Store：`https://itunes.apple.com/cn/app/nan-gua-gu-niang-yi-jian-xia/id1014850829?l=en&mt=8`

2，如果当前位于安卓系统内，且是微信内部，跳转提示使用浏览器打开

3，如果位于安卓系统内，且微信外部，直接下载最新渠道包

### 3.2 友盟统计

1，统计页面浏览量

2，统计页面中两个下载按钮（悬浮Banner下载按钮和页面底部的下载按钮）的点击次数

3，该页面的APK渠道为金针菇`jinzhengu`


## 四、相关接口

这些都是可以直接在浏览器中直接打开的地址

### 4.1 `/getapp`

请求地址：`<服务器地址>/nggirl/app/getapp`

请求方式：支持GET和POST

请求参数：无

处理方式：直接跳转到微信应用宝内的南瓜姑娘下载地址`http://a.app.qq.com/o/simple.jsp?pkgname=cn.com.nggirl.nguser`

### 4.2 `/getapp/ios`

请求地址：`<服务器地址>/nggirl/app/getapp/ios`

请求方式：支持GET和POST

请求参数：无

处理方式：直接跳转到苹果App Store内的南瓜姑娘下载地址`https://itunes.apple.com/cn/app/nan-gua-gu-niang-yi-jian-xia/id1014850829?l=en&mt=8`

### 4.3 `/getapp/costrial`

请求地址：`<服务器地址>/nggirl/app/getapp/costrial`

请求方式：支持GET和POST

请求参数：无

处理方式：

根据用户浏览器类型进行判断

1，微信内部，直接跳转到微信应用宝内的南瓜姑娘下载地址`http://a.app.qq.com/o/simple.jsp?pkgname=cn.com.nggirl.nguser`

2，微信外部，IOS系统内部，跳转到苹果App Store内的南瓜姑娘下载地址`https://itunes.apple.com/cn/app/nan-gua-gu-niang-yi-jian-xia/id1014850829?l=en&mt=8`

3，以上都不是，获取`cosmtrial`渠道的最新APK下载地址，跳转到该地址下载APK

4，如果找不到任何`cosmtrial`渠道的APK，则跳转到最新的`yignyongbao`渠道APK地址，下载APK

### 4.4 `/getapp/byChannel`

请求地址：`<服务器地址>/nggirl/app/getapp/byChannel`

请求方式：支持GET和POST

请求参数：

`channel`为指定的渠道代码

处理方式：

根据用户浏览器类型进行判断

1，微信内部，直接跳转到微信应用宝内的南瓜姑娘下载地址`http://a.app.qq.com/o/simple.jsp?pkgname=cn.com.nggirl.nguser`

2，微信外部，IOS系统内部，跳转到苹果App Store内的南瓜姑娘下载地址`https://itunes.apple.com/cn/app/nan-gua-gu-niang-yi-jian-xia/id1014850829?l=en&mt=8`

3，以上都不是，获取入参指定渠道的最新APK下载地址，跳转到该地址下载APK

4，如果找不到指定的任何入参渠道APK，则跳转到最新的`yignyongbao`渠道APK地址，下载APK

### 4.5 `/getapp/downloadAndroidApk/byChannel`

请求地址：`<服务器地址>/nggirl/app/getapp/downloadAndroidApk/byChannel`

请求方式：支持GET和POST

请求参数：

`channel`为指定的渠道代码

处理方式：

1，获取入参指定渠道的最新APK下载地址，跳转到该地址下载APK

2，如果找不到指定的任何入参渠道APK，则跳转到最新的`yignyongbao`渠道APK地址，下载APK
