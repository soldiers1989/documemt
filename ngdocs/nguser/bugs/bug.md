2015.09.11
---

- [ ] 登录后闪退
```mestamp=1440666930
E/messi   (13763): 批量获取用户信息返回={"data":{"error":"系统参数无效，请联系南瓜姑娘服务人员。"},"code":1}
E/MtaSDK  (13763):
E/MtaSDK  (13763): com.google.gson.JsonSyntaxException: java.lang.IllegalStateException: Expected BEGIN_ARRAY but was BEGIN_OBJECT at line 1 column 10
E/MtaSDK  (13763): 	at com.google.gson.internal.bind.ReflectiveTypeAdapterFactory$Adapter.read(ReflectiveTypeAdapterFactory.java:176)
E/MtaSDK  (13763): 	at com.google.gson.Gson.fromJson(Gson.java:795)
E/MtaSDK  (13763): 	at com.google.gson.Gson.fromJson(Gson.java:761)
E/MtaSDK  (13763): 	at com.google.gson.Gson.fromJson(Gson.java:710)
E/MtaSDK  (13763): 	at com.google.gson.Gson.fromJson(Gson.java:682)
E/MtaSDK  (13763): 	at com.iuxstudio.pumpkincarriagecustom.fragments.MessageFragment.apiOnSuccess(MessageFragment.java:257)
E/MtaSDK  (13763): 	at com.iuxstudio.pumpkincarriagecustom.network.NetworkRequest$1.onSuccess(NetworkRequest.java:55)
E/MtaSDK  (13763): 	at com.iuxstudio.pumpkincarriagecustom.network.NetworkRequest$1.onSuccess(NetworkRequest.java:1)
E/MtaSDK  (13763): 	at net.tsz.afinal.http.HttpHandler.onProgressUpdate(HttpHandler.java:154)
E/MtaSDK  (13763): 	at net.tsz.afinal.core.AsyncTask$InternalHandler.handleMessage(AsyncTask.java:503)
E/MtaSDK  (13763): 	at android.os.Handler.dispatchMessage(Handler.java:102)
E/MtaSDK  (13763): 	at android.os.Looper.loop(Looper.java:135)
E/MtaSDK  (13763): 	at android.app.ActivityThread.main(ActivityThread.java:5254)
E/MtaSDK  (13763): 	at java.lang.reflect.Method.invoke(Native Method)
E/MtaSDK  (13763): 	at java.lang.reflect.Method.invoke(Method.java:372)
E/MtaSDK  (13763): 	at com.android.internal.os.ZygoteInit$MethodAndArgsCaller.run(ZygoteInit.java:903)
E/MtaSDK  (13763): 	at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:698)
E/MtaSDK  (13763): Caused by: java.lang.IllegalStateException: Expected BEGIN_ARRAY but was BEGIN_OBJECT at line 1 column 10
E/MtaSDK  (13763): 	at com.google.gson.stream.JsonReader.expect(JsonReader.java:339)
E/MtaSDK  (13763): 	at com.google.gson.stream.JsonReader.beginArray(JsonReader.java:306)
E/MtaSDK  (13763): 	at com.google.gson.internal.bind.CollectionTypeAdapterFactory$Adapter.read(CollectionTypeAdapterFactory.java:79)
E/MtaSDK  (13763): 	at com.google.gson.internal.bind.CollectionTypeAdapterFactory$Adapter.read(CollectionTypeAdapterFactory.java:60)
E/MtaSDK  (13763): 	at com.google.gson.internal.bind.ReflectiveTypeAdapterFactory$1.read(ReflectiveTypeAdapterFactory.java:93)
E/MtaSDK  (13763): 	at com.google.gson.internal.bind.ReflectiveTypeAdapterFactory$Adapter.read(ReflectiveTypeAdapterFactory.java:172) 
```


- [ ] “收藏”和“已收藏”按钮的背景颜色同“点赞”和“未点赞”按钮的背景颜色风格不一致。前者为未操作时，按钮背景“红色高亮”，后者为操作后，按钮背景“红色高亮”
- [ ] （仅限英文系统）作品集-下拉刷新-下拉模块显示的有一部分英文
- [ ] （仅限英文系统）评论列表-下拉刷新-下拉模块显示的是英文
- [x] 横竖屏问题

- [ ] 作品详情-我要预约-“立即预约”按钮没有居中显示（6寸屏幕）点击立即预约按钮之后，显示的“取消预约”按钮也存在同样的问题
- [ ] 闪退

```
com.google.gson.JsonSyntaxException: java.lang.IllegalStateException: Expected BEGIN_ARRAY but was BEGIN_OBJECT at line 1 column 10
E/AndroidRuntime(13149): 	at com.google.gson.internal.bind.ReflectiveTypeAdapterFactory$Adapter.read(ReflectiveTypeAdapterFactory.java:176)
E/AndroidRuntime(13149): 	at com.google.gson.Gson.fromJson(Gson.java:795)
E/AndroidRuntime(13149): 	at com.google.gson.Gson.fromJson(Gson.java:761)
E/AndroidRuntime(13149): 	at com.google.gson.Gson.fromJson(Gson.java:710)
E/AndroidRuntime(13149): 	at com.google.gson.Gson.fromJson(Gson.java:682)
E/AndroidRuntime(13149): 	at com.iuxstudio.pumpkincarriagecustom.fragments.MessageFragment.apiOnSuccess(MessageFragment.java:259)
E/AndroidRuntime(13149): 	at com.iuxstudio.pumpkincarriagecustom.network.NetworkRequest$1.onSuccess(NetworkRequest.java:55)
E/AndroidRuntime(13149): 	at com.iuxstudio.pumpkincarriagecustom.network.NetworkRequest$1.onSuccess(NetworkRequest.java:1)
E/AndroidRuntime(13149): 	at net.tsz.afinal.http.HttpHandler.onProgressUpdate(HttpHandler.java:154)
E/AndroidRuntime(13149): 	at net.tsz.afinal.core.AsyncTask$InternalHandler.handleMessage(AsyncTask.java:503)
E/AndroidRuntime(13149): 	at android.os.Handler.dispatchMessage(Handler.java:102)
E/AndroidRuntime(13149): 	at android.os.Looper.loop(Looper.java:135)
E/AndroidRuntime(13149): 	at android.app.ActivityThread.main(ActivityThread.java:5254)
E/AndroidRuntime(13149): 	at java.lang.reflect.Method.invoke(Native Method)
E/AndroidRuntime(13149): 	at java.lang.reflect.Method.invoke(Method.java:372)
E/AndroidRuntime(13149): 	at com.android.internal.os.ZygoteInit$MethodAndArgsCaller.run(ZygoteInit.java:903)
E/AndroidRuntime(13149): 	at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:698)
E/AndroidRuntime(13149): Caused by: java.lang.IllegalStateException: Expected BEGIN_ARRAY but was BEGIN_OBJECT at line 1 column 10
E/AndroidRuntime(13149): 	at com.google.gson.stream.JsonReader.expect(JsonReader.java:339)
E/AndroidRuntime(13149): 	at com.google.gson.stream.JsonReader.beginArray(JsonReader.java:306)
E/AndroidRuntime(13149): 	at com.google.gson.internal.bind.CollectionTypeAdapterFactory$Adapter.read(CollectionTypeAdapterFactory.java:79)
E/AndroidRuntime(13149): 	at com.google.gson.internal.bind.CollectionTypeAdapterFactory$Adapter.read(CollectionTypeAdapterFactory.java:60)
E/AndroidRuntime(13149): 	at com.google.gson.internal.bind.ReflectiveTypeAdapterFactory$1.read(ReflectiveTypeAdapterFactory.java:93)
E/AndroidRuntime(13149): 	at com.google.gson.internal.bind.ReflectiveTypeAdapterFactory$Adapter.read(ReflectiveTypeAdapterFactory.java:172)
E/AndroidRuntime(13149): 	... 16 more
```
- [ ] 订单完成后，评价-提交评价按钮未居中显示（6寸屏手机测试）
- [ ] 评价-上传图片-上传四张图片时，加载时间太长（程序无响应）
- [ ] 闪退

```
java.lang.IndexOutOfBoundsException: Invalid index 0, size is 0
E/AndroidRuntime(18743): 	at java.util.ArrayList.throwIndexOutOfBoundsException(ArrayList.java:255)
E/AndroidRuntime(18743): 	at java.util.ArrayList.get(ArrayList.java:308)
E/AndroidRuntime(18743): 	at com.iuxstudio.pumpkincarriagecustom.fragments.MessageFragment$1.onItemClick(MessageFragment.java:103)
E/AndroidRuntime(18743): 	at android.widget.AdapterView.performItemClick(AdapterView.java:305)
E/AndroidRuntime(18743): 	at android.widget.AbsListView.performItemClick(AbsListView.java:1146)
E/AndroidRuntime(18743): 	at android.widget.AbsListView$PerformClick.run(AbsListView.java:3053)
E/AndroidRuntime(18743): 	at android.widget.AbsListView$3.run(AbsListView.java:3860)
E/AndroidRuntime(18743): 	at android.os.Handler.handleCallback(Handler.java:739)
E/AndroidRuntime(18743): 	at android.os.Handler.dispatchMessage(Handler.java:95)
E/AndroidRuntime(18743): 	at android.os.Looper.loop(Looper.java:135)
E/AndroidRuntime(18743): 	at android.app.ActivityThread.main(ActivityThread.java:5254)
E/AndroidRuntime(18743): 	at java.lang.reflect.Method.invoke(Native Method)
E/AndroidRuntime(18743): 	at java.lang.reflect.Method.invoke(Method.java:372)
E/AndroidRuntime(18743): 	at com.android.internal.os.ZygoteInit$MethodAndArgsCaller.run(ZygoteInit.java:903)
E/AndroidRuntime(18743): 	at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:698)
```
- [ ] 设置-修改密码-确定按钮颜色和其他页面按钮的颜色不一致
- [ ] 设置-关于-文字缩进有问题
- [ ] 设置-建议反馈 样式没有居中（6寸屏测试）
- [ ] 设置页面中几个子页面中的字体大小不一致

2015.08.30
---
- [x] 消息-聊天界面-每一条聊天信息的背景是白色的，而主背景是灰色的。并且下拉刷新的样式和其他模块的样式不同
- [x] 消息-系统消息-点击第一条就崩溃。而且打开一条消息，显示的却是上一条消息。
- [x] 作品详情-我要预约按钮-我要预约页面-预约地址页面，页面底端的按钮未居中显示。
- [x] 作品详情-我要预约按钮-我要预约页面-预约地址页面-详细地址，显示不完整。
- [x] 我的-个人资料-详细地址，修改详细地址时，键盘挡住了输入框，导致输入框不可见，地址无法方便地编辑。
- [x] 我的-我的南瓜券-领取南瓜券，不在“优惠码”输入框输入任何信息，点击“领取”按钮，提示“该优惠券号码不能使用”。另外，从分享页面粘贴过来的“优惠码”无法复制到输入框，没有实现复制的功能。
- [x] 内部不同模块之间刷新页面样式不一致，刷新时文字不统一。(环信聊天页面的刷新样式和其他模块刷新样式仍然不一致)
- [x] 设置页面中几个子页面中的字体大小不一致
- [x] 设置-关于-文字缩进有问题
- [x] 设置-建议反馈 样式没有居中
- [x] 聊天页面，给“图片上传”和“表情”两个图标设置边间距
- [ ] 订单完成后，评价订单，上传图片模块仍然有问题。拍照上传导致内存溢出（崩溃），相册上传，打开本地相册让用户选择照片时，漆黑一片，无法正确显示相册里的照片。上传四张图片时，加载时间太长（程序无响应）
- [ ] 我的-我的预约，列表中虽然显示的订单状态是“化妆师已确认，等待支付”，但是点击之后打开的页面显示的却是“预约已取消”。
- [ ] 分享焦点图的标题改错(不理解需求，无法测试)
- [ ] 由管理管理员完成。【注意：脸和确定之间有一个换行符】(不理解需求，无法测试)

2015.08.29
---
- [x] 登录有问题，点击键盘上的确定登录发出了两次请求，导致自己把自己下线。
- [x] 作品详情页面的右上角有分享功能，但是分享不能成功，微博、微信好友、朋友圈，都不能成功
- [x] 未登录用户的背景图错误，不应该是灰色的，应该有一个默认背景
- [x] 获取验证码时，用户已注册，不应开启倒计时。
- [x] 客户端注册后，填写个人资料时，手机号需要用户重新填写，这个太麻烦，应该直接填写上的
- [x] 作品详情--》收藏，已收藏 按钮背景颜色
- [x] 前端很多地方都还有“约练”、“教练”等类似的字眼，全部需要替换。（比如，IOS-C注册的2/2步）
- [x] 代金券，全部换成南瓜券
- [x] 预约输入地址的地方，点击同行的空白处无效。
- [x] 输入时间的地方，有时候选中的时间没有写上去。
- [x] 预约页面，收到消息后要刷新。
- [x] 化妆进行中也应该可以点击完成
- [x] 获取验证码时，用户已注册，不应开启倒计时。
- [x] 输入时间的地方，有时候选中的时间没有写上去。
- [x] 我的-个人资料-性别 （点击”性别“按钮后选择取消，性别处被清空，应该保留原值）
- [x] 输入时间的地方，有时候选中的时间没有写上去。
- [x] 作品列表页面禁用横屏。
- [x] 微信支付不成功。
- [x] 作品详情-我要预约-“立即预约”按钮没有居中显示（6寸屏幕）点击立即预约按钮之后，显示的“取消预约”按钮也存在同样的问题  
- [x] 订单完成后，评价-提交评价按钮未居中显示（6寸屏手机测试）
- [x] 设置-修改密码-确定按钮颜色和其他页面按钮的颜色不一致
- [x] 作品分享的跳转链接使用：http://cli.nggirl.com.cn/nggirl/h5/mobile/c_focus_content1.html
- [x] 轮播头图进入到“从今以后 你可以和明星”的页面，点击播放视频后，退出该页面视频仍然在播放。
- [x] 退款按钮不调用后台的退款接口，改为弹出提示用户“真要退款并取消预约吗？南瓜姑娘好桑心呢：（确定后请联系客服010-58140904。”的对话框。退款操作
- [x] 在我的页面中设置的下面添加“南瓜姑娘客服电话010-58140904”的浅灰色文字。
- [x] 分享的标题都确定为“南瓜姑娘-陪伴你人生的“美”一段旅程”；
- [x] 作品分享的描述内容：“化妆师你站住，快来让我也变这样可以吗~”
- [x] 邀请码分享的内容：“送你30元，最专业化妆师让你一秒变女神!”
- [x] 作品分享出去后，点击跳转的链接统一为：http://cli.nggirl.com.cn/nggirl/h5/mobile/c_focus_content1.html
- [x] 化妆师-搜索-点击搜索后的结果崩溃
- [x] 关注的化妆第一个点击崩溃
- [x] 消息-系统消息-第一条信息-崩溃
- [x] 点预约的系统消息崩溃---海威
- [x] 分享邀请码到朋友圈的  南瓜图标不对
- [x] 领取南瓜券，没有粘贴功能
- [x] 微信支付没有减去优惠券的金额
