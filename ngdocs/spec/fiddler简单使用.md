# fiddler简单使用



---

 * [1.简介](#1)
 * [2.安装配置](#2)
 * [3.常用的一些点](#3)
    * [3.1.AutoResponder和willow重定向](#3.1)
    * [3.2.网速限制](#3.2)
    * [3.3.Fiddler替换HTTP Request Host](#3.3)
    * [3.4.使用Filters过滤host](#3.4)
    * [3.5.Fiddler中设置断点](#3.5)

<h2 id="1">1.简介</h2>

Fiddler是一个http协议调试代理工具，它能够记录并检查所有你的电脑和互联网之间的http通讯，设置断点，查看所有的“进出”Fiddler的数据（指cookie,html,js,css等文件，这些都可以让你胡乱修改的意思）。 Fiddler 要比其他的网络调试器要更加简单，因为它不仅仅暴露http通讯还提供了一个用户友好的格式。Fiddler是用C#写出来的,它包含一个简单却功能强大的基于JScript.NET事件脚本子系统，它的灵活性非常棒，可以支持众多的http调试任务，并且能够使用.net框架语言进行扩展。

<h2 id="2">2.安装配置</h2>
Fiddler有两个版本，下载地址 http://www.telerik.com/download/fiddler ，针对Fiddler2和Fiddler4，对应的Willow插件版本也是不一样的。本文使用和针对的主要是Fiddler4.

配置：打开fiddler，在菜单中选择Tools->Fiddler Options，如下图选择ok后，关闭Fiddler并重新打开Fiddler，就可以用Fiddler抓取本地所有的流量了。
![](http://img.blog.csdn.net/20160801181311573)

手机抓包：抓取手机数据包和抓去电脑上的数据包一样，只需要将手机的代理设置为Fiddler。具体操作：让手机连接的wifi和你安装Fiddler的电脑处于同一网段，然后在手机的wifi设置中，选择高级选项，设置代理，指向你电脑的ip，端口设置为8888即可。
![这里写图片描述](http://img.blog.csdn.net/20160801181525123)


<h2 id="3">3.常用的一些点</h2>

<h3 id="3.1">3.1 使用AutoResponder对回包进行重定向和使用Willow插件管理重定向规则</h3>


这两种操作方法是一样的，都是对服务器返回的数据包（下面简称回包）进行规则的设置，使得回包被替换成我们指定的文件。不过Willow插件用起来比较方便，所以我们一般都会安装Willow插件。

现在我们以Willow插件为例介绍这个非常好用的回包替换功能，我这里安装的是1.4版的Willow，支持Fiddler4.0版本。安装了Willow插件的Fiddler，在右侧的网络数据解析界面上会多出一个Willow标签菜单，如下图所示。
![这里写图片描述](http://img.blog.csdn.net/20160801181851018)

从图上看出，Willow的图标是一个小树，当回包重定向功能开启时，这颗小树会变成绿色，普通状态下小树是灰色的。

在下面的列表中，Fiddler、Temp 1、unclenought等都是一个一个的Willow project，这些project对应的是一组一组的规则，这里我们添加一个unclenought的project。在Willow菜单内右键可以选择Add Project、Edit Project以及Add Rule等等。![这里写图片描述](http://img.blog.csdn.net/20160801181955363)

其中我们最常用就是Add Rule功能了，通过这个我们可以设置一些规则，将回包进行重定向。右键选择Add Rule以后，我们在Match栏填写正则表达式来匹配网络请求，Action栏选择我们本地的一个文件来替换match栏对应的请求的回包,这里我选择了自己写的一个hello fiddler.html测试文件。记住，规则保存好了以后，必须勾选Willow菜单左上角的小勾，使得回包替换功能开启，确保Willow小树的图标变成了绿色的！![这里写图片描述](http://img.blog.csdn.net/20160801182047911)





<h3 id="3.2">3.2 网速限制</h3>

**第-种方法：**
需要的插件：Fiddler script，下载地址：http://www.telerik.com/download/fiddler/fiddlerscript-editor
下载完直接安装就行了，安装之前必须关闭fiddler，再打开fiddler就会在右侧tab看到fiddler script选项
fiddler script原理：把请求完全代码化
Eg：模拟延时3s发送请求：
选中会话，在fiddler-script——>Go to->OnBeforeRequest添加代码如下：
oSession["request-trickle-delay"] = "3000"
![这里写图片描述](http://img.blog.csdn.net/20160801182320243)
点击save script保存，再replay会话就会发现会话延迟了三秒才发送
延时响应同理

**第二种方法：**

![这里写图片描述](http://img.blog.csdn.net/20160801182442550)





<h3 id="3.3">3.3 Fiddler替换HTTP Request Host</h3>

替换的方法有两种，一种是暂时的，一种是永久的，暂时的方法是在Fiddler 左下角输入：
> urlreplace www.demo.com www.dev.demo.com

要清除转发，请在同一位置输入：
> urlreplace
按Enter 就可以了。


永久的方法是修改Fiddler的CustomRules.js ，注意是.js ！ 点下Fiddler 上方的Rules ，再点Customize Rules ：

如果有安装FiddlerScript Editor ，会用FiddlerScript Editor开启CustomRules.js ，否则会用笔记本开启。 或者也可以到「我的文件 Fiddler2 Scripts 」直接编辑CustomRules.js 。
```java
//请先在CustomRules.js 找到：
  static function OnBeforeRequest ( oSession : Session ) {
   // ...
   //在函式中加入：
  if ( oSession . HostnameIs ( 'www.demo.com' ) )
   oSession . hostname = 'www.dev.demo.com' ;
 }
```
将CustomRules.js 存档， Fiddler 会自动重新载入CustomRules.js ，原先发到www.demo.com 的HTTP Request 就会自动转发到www.dev.demo.com 。





<h3 id="3.4">3.4 使用Filters过滤host</h3>


如下路，多个host可以用分号隔开：
![这里写图片描述](http://img.blog.csdn.net/20160801182934253)
配置好之后点击Actions选中Run filterset now



<h3 id="3.5">3.5 Fiddler中设置断点</h3>

* 你可以修改httpRequest的任何信息包括host, cookie或者表单中的数据。
* Break request是用来阻断上行数据（客户端给服务器传输的参数），可以修改用户名或者密码来实现测试登陆的功能。
* Break response是用来阻断下行数据，例如修改点赞数，返回到手机可以查看该处数据有变化。
如下图，在fiddler左下角处，AllProcesses右边处可以切换上行，下行状态：
![此处输入图片的描述][1]
![此处输入图片的描述][2]

* break request上行，可以修改请求参数，比如登录的用户名密码
![此处输入图片的描述][3]
* break response下行，可以修改返回的数据结果，比如浏览数，订单数。
    * 可以检查气泡的ui展示效果
    * 客户端可以正常显示未读问题数目
    * 数字较大的处理

![此处输入图片的描述][4]






-----





参考资料：http://www.cnblogs.com/yuzhongwusan/archive/2012/07/20/2601306.html

http://unclechen.github.io/2015/04/30/%E4%BD%BF%E7%94%A8%E5%89%8D%E7%AB%AF%E5%BC%80%E5%8F%91%E5%88%A9%E5%99%A8Fiddler%E8%B0%83%E8%AF%95%E6%89%8B%E6%9C%BA%E7%A8%8B%E5%BA%8F/


http://blog.csdn.net/jasminecjc/article/details/51509997

https://segmentfault.com/a/1190000005899201


  [1]: http://photosd.nggirl.com.cn/work/4760dba37c2d4e37af96dce119c99685.png
  [2]: http://photosd.nggirl.com.cn/work/d6da76bf3d3f49b281e85a6e6fac774b.png
  [3]: http://photosd.nggirl.com.cn/work/fb064a01e7eb463381a79b0264f0481e.png
  [4]: http://photosd.nggirl.com.cn/work/a5673366bd954ccab64b3871403bd3f8.png
