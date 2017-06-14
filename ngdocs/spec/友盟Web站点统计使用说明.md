# 友盟Web站点统计使用说明

##统计代码

##### 统计代码用于统计用户访问各个页面的访问情况。具体使用方法如下：

1. 站点统计页面可管理站点。如图已添加正式和测试两站点。
   ![站点统计](http://photosd.nggirl.com.cn/work/12d03c5bdd3e4b848c3c919ca665ff2e.png)
2. 将以下2段代码其中之一复制到到统计页面</body>前。（第一段为http代码；第二段为https加密代码。1259610672为本网站在友盟的id）

` <script src="http://s4.cnzz.com/z_stat.php?id=1259610672&web_id=1259610672" language="JavaScript"></script> `

`<script src="https://s4.cnzz.com/z_stat.php?id=1259610672&web_id=1259610672" language="JavaScript"></script>`

### 事件追踪
#####事件追踪统计页面上的按钮等元素的使用情况。例如：展开、收起、收藏、评分等，此统计依赖于上面统计代码的设置。
1. 先在页面的</head>之前添加如下代码。XXXXXXXX为本站点在友盟的WEB_ID。
 `<script>
//声明_czc对象:
var _czc = _czc || [];
//绑定siteid，请用您的siteid替换下方"XXXXXXXX"部分
_czc.push(["_setAccount", "XXXXXXXX"]);
</script>`
2. 在按钮等被点击触发的时候，调用_trackEvent()方法，语法如下：<br/>
   `_czc.push(["_trackEvent",category,action,label,value,nodeid]);`  <br/>

>各参数含义如下：
category：事件类别，必填项，表示事件发生在谁身上，如“视频”、“小说”、“轮显层”等等。<br/>
action：事件操作，必填项，表示访客跟元素交互的行为动作，如"播放"、"收藏"、"翻层"等等。<br/>
label：事件标签，选填项，用于更详细的描述事件，从各个方面都可以，比如具体是哪个视频，哪部小说，翻到了第几层等等。<br/>
value：事件值，选填项，整数型，用于填写打分型事件的分值，加载时间型事件的时长，订单型事件的价格等等。<br/>
nodeid：div元素id，选填项，填写网页中的div元素id值，用于在“用户视点”功能上重绘元素的事件发生情况。<br/>

**示例代码**
`<a href="#" onclick="_czc.push(['_trackEvent', '小说', '打分', '达芬奇密码','5','dafen']);">打分</a>`




