# 制作EDM邮件

EDM格式邮件其实邮件发送的内容是html文件，里面嵌套了文字、图片、视频、音频等。

1，Out Look邮箱客户端默认禁止所有图片下载，除非发件人已被加入到`安全发件人列表`中、或者再`首选项`>`信任`中勾选能够下载图片的选项。所以如果遇到Out Look邮箱客户端提示下载的情况，这个不算bug。

2，发送邮件之前，请在各种环境下查看邮件是否显示正常，例如FoxMail客户端、Out Look客户端、邮箱大师客户端、各个手机邮箱客户端。

3，网上有很多能够设计EDM邮件的网站，[详情请点击查看](https://www.zhihu.com/question/20556280)


## 1.制作原则

>图片裁剪规则参照：[图片实时加载尺寸设定](../nggirl/图片实时加载尺寸设定.md)

1，图片大小不能过大，最好不要超过100k。图片上传时使用压缩上传接口。加载图片时使用`@80Q`等限定图片大小。

2，图片宽高最好不要超过1200

## 2.制作步骤

我选择的制作网站是[Mailchimp](https://mailchimp.com/)

跟负责人索要登陆账户和密码

1，依次点击`Templates`>>`Create Template`，根据需要选择对应的模板。一般选择`Basic`中的`1 Column`就行了

2，拖动添加或者三处对应的元素

3，点击右上角的`Preview and Test`>>`Send a test mail`，检查当前模板和内容是否正确

4，点击右下角的`Save and Exit`退出

5，在模板列表中点击按钮`Export as HTML`，获得要发送的EDM文件，暂时取名为a.html

## 3.修改图片地址

### 3.1.上传图片到服务器上

使用`http://cli.nggirl.com.cn/uploadserver/app/image/uploadsCompress/3.0.0`接口上传图片

返回结果：

```json
{
  "code": 0,
  "data": {
    "url": "https://photosd.nggirl.com.cn/work/086b28aa6c03438c870ecd232c614c9e.jpg",
    "md5": "05F2FFB288B27545738A4D4D6A7EDE57",
    "height": 991,
    "width": 750
  }
}
```

记录各个图片的url和显示顺序。

### 3.2 替换html文件中的图片链接地址

根据图片显示的顺序修改对应的html文件中的图片链接


## 4.发送EDM格式邮件

EDM格式邮件其实就是HTML格式邮件。

不同的邮箱或者邮箱客户端对HTML格式邮件的支持不同，咱们的网页版企业邮箱不支持发送HTML格式邮件，但是Windows下的Foxmail支持发送HTML格式邮件、163邮箱网页版、QQ邮箱网页版都支持HTML格式邮件发送。

按照HTML格式邮件，直接粘贴源代码进去就行了。
