# 使用微信SDK遇到的问题汇总

在正式开始之前这里要着啰嗦一下，进来的同学一定要看，在申请应用的时候要填一个签名，这个签名是由应用的签名文件keystore决定的，那么你在填这个签名的时候，一定要把你的应用用正式的keyStore生成apk，安装到手机，然后用微信提供的获取应用签名的apk工具获取你应用的签名，然后这会生成的这个签名才是正确的，千万记得，不要使用dubug的ketStore测试，不然后面虽然可以修改，修改了后要审核，但是审核也是需要时间的，会很麻烦。
还有一点，你在测试微信分享的时候可能会直接在Eclipse好或者Studio运行项目，那样使用的肯定是dubug的keyStore了，这样分享的时候会被微信拒绝，微信会生成缓存，就算你这会换了正式的keystore来分享显示的还会是被微信拒绝，就算重启微信重启手机也不管用，那你就要清空微信的数据了；很多东西是不是丢了？好吧，啰嗦够了，正式进入主题。

今天会提供如果实现微信分享，并且对怎么成功接受回调结果做一个详细的介绍和教程，有回调结果失败的同学，往下看吧

首先就是要去开放平台申请应用，审核通过后会分配给你一个AppID：

然后，要下载微信开放平台的SDk，[下载页面地址](https://open.weixin.qq.com/cgi-bin/showdocument?action=dir_list&t=resource/res_list&verify=1&lang=zh_CN)，然后把libammsdk.jar这个包放在lib下；
下面我做了一个图片、文字、URL的封装，因为这几个是最常用的对吧，如果还需要其他的分享类型，那么你在这里添加几个方法就可以了，很方便修改：

```
/**
     * 利用微信SDK分享到微信
     */
    public abstract class ShareWechat {

        private ShareWechat() {
        }//abstract不可实例化也不可继承

        /**
         * 压缩图的大小
         **/
        private static final int THUMB_SIZE = 150;

        /**
         * 分享文字
         *
         * @param wxApi        微信分享对象
         * @param shareContent 分享内容
         * @param isToFriend   是否分享到朋友圈
         * @author YOLANDA
         */
        public static void shareText(IWXAPI wxApi, String shareContent, boolean isToFriend) {
            WXTextObject textObj = new WXTextObject();
            textObj.text = shareContent;
            WXMediaMessage msg = new WXMediaMessage();
            msg.mediaObject = textObj;
            // 发送文本类型的消息时，title字段不起作用
            // msg.title = "Title";
            msg.description = shareContent;
            // 构造一个Req
            SendMessageToWX.Req req = new SendMessageToWX.Req();
            req.transaction = buildTransaction("text"); // transaction字段用于唯一标识一个请求
            req.message = msg;
            req.scene = isToFriend ? SendMessageToWX.Req.WXSceneTimeline : SendMessageToWX.Req.WXSceneSession;
            wxApi.sendReq(req);
        }

        /**
         * 分享一个图片
         *
         * @param wxApi
         * @param shareBitmap 要分享的图片
         * @param isToFriend  是否是分享到朋友圈
         * @author YOLANDA
         */
        public static void shareImg(IWXAPI wxApi, Bitmap shareBitmap, boolean isToFriend) {
            WXImageObject imgObj = new WXImageObject(shareBitmap);

            WXMediaMessage msg = new WXMediaMessage();
            msg.mediaObject = imgObj;

            Bitmap thumbBmp = Bitmap.createScaledBitmap(shareBitmap, THUMB_SIZE, THUMB_SIZE, true);
            msg.thumbData = bmpToByteArray(thumbBmp);  // 设置缩略图

            SendMessageToWX.Req req = new SendMessageToWX.Req();
            req.transaction = buildTransaction("img");
            req.message = msg;
            req.scene = isToFriend ? SendMessageToWX.Req.WXSceneTimeline : SendMessageToWX.Req.WXSceneSession;
            wxApi.sendReq(req);
        }

        /**
         * 分享一个网页
         *
         * @param wxApi
         * @param httpUrl     要分享的连接
         * @param isToFriend  是否是分享到朋友圈
         * @param iconRes     ICON
         * @param title       标题
         * @param description 描述
         * @author YOLANDA
         */
        public static void shareWebPage(IWXAPI wxApi, String httpUrl, boolean isToFriend, int iconRes, String title, String description) {
            Bitmap icon = BitmapFactory.decodeResource(Application.getInstance().getResources(), iconRes);
            shareWebPage(wxApi, httpUrl, isToFriend, icon, title, description);
        }

        /**
         * 分享一个网页
         *
         * @param wxApi
         * @param httpUrl
         * @param isToFriend
         * @param icon
         * @param title
         * @param description
         * @author YOLANDA
         */
        public static void shareWebPage(IWXAPI wxApi, String httpUrl, boolean isToFriend, Bitmap icon, String title, String description) {
            WXWebpageObject webpage = new WXWebpageObject();
            webpage.webpageUrl = httpUrl;
            WXMediaMessage msg = new WXMediaMessage(webpage);
            msg.title = title;
            msg.description = description;
            msg.thumbData = bmpToByteArray(icon);

            SendMessageToWX.Req req = new SendMessageToWX.Req();
            req.transaction = buildTransaction("webpage");
            req.message = msg;
            req.scene = isToFriend ? SendMessageToWX.Req.WXSceneTimeline : SendMessageToWX.Req.WXSceneSession;
            wxApi.sendReq(req);
        }

        /**
         * 得到Bitmap的byte
         *
         * @param bmp
         * @param needRecycle
         * @return
         * @author YOLANDA
         */
        private static byte[] bmpToByteArray(Bitmap bmp) {
            ByteArrayOutputStream output = new ByteArrayOutputStream();
            bmp.compress(CompressFormat.PNG, 100, output);

            byte[] result = output.toByteArray();
            try {
                output.close();
            } catch (Exception e) {
                e.printStackTrace();
            }
            return result;
        }

        /**
         * 构建一个唯一标志
         *
         * @param type
         * @return
         * @author YOLANDA
         */
        private static String buildTransaction(String type) {
            return (type == null) ? String.valueOf(System.currentTimeMillis()) : (type + System.currentTimeMillis());
        }

    }

```

如果你看了上面的方法的封装，想必你一定看到了分享的方法都需要一个IWXAPI的参数，那么现在就是要生成这个参数，在你分享之前或者在OnCreate的方法中可以：
IWXAPI wxapi = WXAPIFactory.createWXAPI(context, Constants.WECHAT_APP_ID);

注意，应该使用
IWXAPI wxapi = WXAPIFactory.createWXAPI(context, Constants.WECHAT_APP_ID);
而不是
mWxApi = WXAPIFactory.createWXAPI(context, Constants.WECHAT_APP_ID, false);

为什么呢，原因在下面会解释到。
其实现在已经可以分享成功了，但是我们怎么知道是不是分享成功了呢？那就是要接受微信的分享结果回调了，我们需要提供一个专门的Activity，并且实现微信SDK的IWXAPIEventHandler接口
收不到微信的分享结果回调？很多人在这里就出问题了，我们的Activity实现了微信的IWXAPIEventHandler接口，但是收不到微信的回调，那么问题出在哪里呢？且听我细细道来
看过微信分享的demo的人就知道，微信接受的入口类在**packagename.wxapi**包下，它的分享结果回调也在这个类，那么我们实现这个IWXAPIEventHandler接口怎么就不行呢？往下看

原来，我们在开放平台注册应用的时候要填包名，然后微信会在packagename.wxapi找这个回调接口的类，并且这个类必须是集成了Activity的类，并且实现IWXAPIEventHandler接口，而且最重要的是：这个类的名字一定要是WXEntryActivity.java；这样，你就可以接受到微信回调结果了：
那么注意的几点总结出来就是：
1. 我们必须有一个类继承Activity，且实现微信SDK提供的IWXAPIEventHandler接口
2. 实现IWXAPIEventHandler接口的Activity的文件名称必须是：WXEntryActivity.java
3. 这个WXEntryActivity.java类必须在packagename.wxapi包下，比如说我的程序包名是com.yoalnda.wechat，那么这个文件就放在com.yolanda.wechat.wxapi下
4. 这个类WXEntryActivity.java在onCreate中
mWxApi = WXAPIFactory.createWXAPI(context, Constants.WECHAT_APP_ID, false);
		mWxApi.handleIntent(getIntent(), this);
上边是生成解析回调结果的wxapi对象，下面就是把接受到的Intent给wxapi这个对象，它会解析回调结果，通过我们实现的IWXAPIEventHandler接口回调给我们，这个接口有两个方法，大家可以看我下面的代码就清楚了
5. 不要忘记了onNewIntent这个方法，也要写上，为了防止这个Activity处于栈顶的时候微信回调我们

刚才 说到不能使用
`IWXAPI wxapi = WXAPIFactory.createWXAPI(context, Constants.WECHAT_APP_ID, false);`

下面就是原因，WXAPIFactory提供了两个实例化WXAPI的方法，含有第三个Boolean参数的这个是接受回调结果的时候用的，虽然前面用这个也可以成功。
```
/**
     * @author YOLANDA
     * @Time 2015年3月30日 下午4:55:56
     */
    public class WXEntryActivity extends BaseActivity implements IWXAPIEventHandler {

        /**
         * 分享到微信接口
         **/
        private IWXAPI mWxApi;
        /**
         * 分享结果信息
         **/
        private TextView txtShareResult;
        /**
         * 分享结果图片
         **/
        private ImageView imgShareResult;

        @Override
        protected void onActivityCreate(Bundle savedInstanceState) {
            setContentLayout(R.layout.activity_share2wechat_result);
            setBackButtonVisibility(true);

            mWxApi = WXAPIFactory.createWXAPI(context, Constants.WECHAT_APP_ID, false);
            mWxApi.registerApp(Constants.WECHAT_APP_ID);
            mWxApi.handleIntent(getIntent(), this);
        }

        @Override
        protected void onNewIntent(Intent intent) {
            super.onNewIntent(intent);
            setIntent(intent);
            mWxApi.handleIntent(intent, this);
        }

        /***
         * 请求微信的相应码
         *
         * @param arg0
         * @author YOLANDA
         */
        @Override
        public void onResp(BaseResp baseResp) {
            txtShareResult = (TextView) findViewById(R.id.txt_share2wechat_result);
            imgShareResult = (ImageView) findViewById(R.id.img_share2wechat_result);
            imgShareResult.setImageResource(R.drawable.operation_failed);
            setTitle("分享失败");
            int result = 0;
            Log.i("错误号：" + baseResp.errCode + "；信息：" + baseResp.errStr);
            switch (baseResp.errCode) {
                case BaseResp.ErrCode.ERR_OK:
                    setTitle("分享成功");
                    result = R.string.sharewechat_success;//成功
                    imgShareResult.setImageResource(R.drawable.operation_succeed);
                    break;
                case BaseResp.ErrCode.ERR_USER_CANCEL:
                    result = R.string.sharewechat_cancel;//取消
                    break;
                case BaseResp.ErrCode.ERR_AUTH_DENIED:
                    result = R.string.sharewechat_deny;//被拒绝
                    break;
                default:
                    result = R.string.sharewechat_back;//返回
                    break;
            }
            txtShareResult.setText(result);
        }

        /**
         * 微信主动请求我们
         **/
        @Override
        public void onReq(BaseReq baseResp) {
            try {
                Intent intent = new Intent(Application.getInstance(), MainActivity.class);
                intent.addFlags(Intent.FLAG_ACTIVITY_NEW_TASK);
                Application.getInstance().startActivity(intent);
            } catch (Exception e) {
            }
        }
    }
```

至此，微信分享和接口回调结果都完成了。
