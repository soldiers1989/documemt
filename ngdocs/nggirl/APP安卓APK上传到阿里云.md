# 上传安卓APK到阿里云

每次新版本发布时，都需要将安卓最新版本apk文件上传到阿里云服务器上。用户下载APK，统一从阿里云上下载。

阿里云地址：[https://www.aliyun.com/](https://www.aliyun.com/)

阿里云账户和密码请询问对应负责人。

### 1，打开阿里云首页

![阿里云首页](https://photosd.nggirl.com.cn/work/dae5bf1216d841e3ac739c87682be1c7.jpg@800w_800h_70Q)

### 2，进入登录页面

![阿里云登录页面](https://photosd.nggirl.com.cn/work/a50e9822b6a1488bad8dad09ee9c5404.png@800w_800h_70Q)

### 3，选中`对象存储 OSS`

![点击对象存储OSS](https://photosd.nggirl.com.cn/work/826011aeca5948219c5e9c6afa932c17.png@800w_800h_70Q)

### 4，点击`nggirl-product-res`

![点击nggirl-product-res](https://photosd.nggirl.com.cn/work/1ca4ad610c9948538a8023f7e63c1acb.png@800w_800h_70Q)

### 5，点击`Object管理`>>`apks`

![点击Object管理](https://photosd.nggirl.com.cn/work/b5a85de022784369a76507d6781d2be0.png@800w_800h_70Q)

### 6，根据版本号新建文件夹

>应保持文件夹名称与版本号相同

>如果当前版本是`3.1.3`，则新版文件夹名称为`3.1.3`

![根据版本号新建文件夹](https://photosd.nggirl.com.cn/work/f97462eb7d544cbb9e47de8187a8b836.png@800w_800h_70Q)

### 7，进入新建文件夹

![进入新建文件夹](https://photosd.nggirl.com.cn/work/ab4abca763194723a0ba12e1fe0c93d1.png@800w_800h_70Q)

### 8，上传全部APK文件

![上传全部APK文件](https://photosd.nggirl.com.cn/work/95030b6b64dd4ec08740a128a77efc32.png@800w_800h_70Q)

### 9，退出登陆

![退出登陆](https://photosd.nggirl.com.cn/work/00750994c07a4455858bda889a2222d8.png@800w_800h_70Q)


### 10，APK下载路径

上传之后的APK下载路径为：`http://photosd.nggirl.com.cn/apks/<新建文件夹名称>/<APK文件名>`

假设新版本为`3.1.3`，用户新建的文件夹也是`3.1.3`，上传的文件名为`nguser_v3.1.3_yingyongbao_release.apk`

则下载路径为`http://photosd.nggirl.com.cn/apks/3.1.3/nguser_v3.1.3_yingyongbao_release.apk`

该路径支持http和https，所以下载路径也可以是：`https://photosd.nggirl.com.cn/apks/3.1.3/nguser_v3.1.3_yingyongbao_release.apk`
