# 应用缓存导致的错误
### 错误的场景
1. 作品集-头部轮播图片-显示的图片和服务器要展示的图片不一致
2. 曾经在使用应用时登录成功，再次使用时崩溃。比如查看优惠券时崩溃。

### 解决的办法
1. 系统-应用-南瓜姑娘-清理缓存
2. 删除SD卡上的nggirl文件夹

# 系统推送导致的错误
### 错误的场景
1. 服务器端有环信聊天信息推送到用户端时，首次打开应用导致崩溃

### 解决的办法
1. 可能是JSON解析出错导致的，在代码中解决

# SD卡读取或者写入导致的错误
### 错误的场景
1. SD卡不可写

### 解决的办法
1. 重启手机
2. 断开USB连接


# 网络异常导致的错误
### 错误的场景
1. 断网时
2. 网络较慢时，数据加载未完成时，用户执行某些需要加载到本地的数据的操作时导致崩溃

### 解决的办法
1. 添加对网络异常的判断

### 解决的办法
