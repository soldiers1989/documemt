#情况说明
由于ios的2.3以前的版本在实现浏览器通过nggirl://nggirl/XXX的schema机制跳转到app内部使用webview打开指定页面功能时，使用了如下类似的代码片段：

```java
String[] splits = url.queryString.split("=");
String toUrl = splits[1];
```

跳转时的schema如下：

```java
nggirl://nggirl/webview?url=http://cli.nggirl.com.cn/nggirl/h5/cosmetic/freeTrial.html?cosmeticId=7
```

问题就是，ios采用上述方法获取到的url其实是“http://cli.nggirl.com.cn/nggirl/h5/cosmetic/freeTrial.html?cosmeticId”，丢掉了“=7”，从而h5页面没有办法获取到当前试用的编号，也就获取不到数据了。


#处理方法
这里采用的处理方法是，对这个页面做特殊处理，把查询参数中的等号全部换成%3d，然后在h5页面中获取查询参数值的地方采用%3d做分割，从而跳过ios这里的坑。
也就是实际上传给ios的跳转链接变成了：http://cli.nggirl.com.cn/nggirl/h5/cosmetic/freeTrial.html?cosmeticId%3d7

这样就可以保证所有的查询参数能够被完整的传给h5了。

#遇到的问题
但是当遇到微信的时候，这里就有了更多的问题。

1.采用上述方案时，从app中分享该页面到微信时，微信会自动把%3d这个编码转换成=，因为两者确实是对应的。[编码的对照关系可以参照这里](http://www.w3school.com.cn/tags/html_ref_urlencode.html)

所以，我们不能用%3d了，这里我们改成了_3d作为替代，就没有问题了。

2.当该页面在微信中再次被分享的时候，微信会给加上from等参数，从而导致url变成了http://cli.nggirl.com.cn/nggirl/h5/cosmetic/freeTrial.html?cosmeticId_3d7=&from=singlemessage&isappinstalled=1的样式。

也就是在7后边多出来一个=号，也就需要在解析的时候把=号去掉。

#最终的获取_3d替代=场景下的获取查询参数函数
```java
function getParamHack(name) {
    var reg = new RegExp("(^|&)" + name + "_3d([^&]*)(&|$)");
    var r = window.location.search.substr(1).match(reg);
    if (r != null)
    	var val = decodeURI(r[2]);
    //微信分享后会给这里添加等号
    	if(val.indexOf('=') == (val.length-1)){
    		val = val.substring(0,val.length-1);
    	}
        return val;
    return '';
}

```

