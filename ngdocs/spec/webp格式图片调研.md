# webp格式图片调研


------
webp格式图片，是google开发的一中旨在加快图片加载速度的图片格式。支持有损压缩和无损压缩，派生自图像编码格式VP8。根据 Google 的测试，无损压缩后的 WebP比PNG文件少了 45％ 的文件大小，即使这些 PNG 文件经过其他压缩工具压缩之后，WebP还是可以减少 28％ 的文件大小。

经过我们自己测试，发现jpg，png转webp格式之后，图片体积大小大概缩小为原来的1/6，而我们目前使用的80%质量压缩，也只是缩小为原来的1/4；所以考虑到网络流量的传输，以及图片的加载速度，webp格式图片确实占很大的优势。

不过现在支持webp格式的浏览器很有限，自己了解到的支持webp格式的浏览器有chrome，opera以及360浏览器。但是原生android4.0以上系统以及原生ios（[需要经过处理][3]）还是支持webp格式的。像app中webview打开H5以及ios系统微信服务号中的浏览器却是不支持webp格式的。H5支持webp也不是没有办法，第一种方式可以使用js直接在页面做特殊处理；第二种方式是使用原生android或ios处理webview中的webp图片，处理之后返回给webview。但是基于作者目前的技术水平以及公司的需要，这两种方式我们都不采用了。


经过调研：阿里云OSS支持图片格式转换和质量转换。我们最终的方案：原生android和ios使用webp格式，H5使用质量压缩。

* 支持webp格式图片的浏览器

    经过查资料以及自己的测试，得知支持webp的浏览器有:chrome,opera和360；
IE，edge，firefox并不支持，当然还有一些没有测试到的浏览器；
android4.0以及ios的第三方类库也支持；
手机中webview打开H5是不支持的；
微信服务号中：android支持，ios系统却不支持

* java处理webp格式图片的第三方类库

    * webp-imageio
    [webp-imageio下载地址][1]
    webp-imageio在linux和在windows上使用方法稍微不一样：
    windows：

        * 1.下载webp-imageio.jar和webp-imageio.dll               
        * 2.把webp-imageio.dll方到java的bin目录下；把webp-imageio.jar放入项目的w             eb-info的lib下，并以maven本地方式引入到maven中
        ```java
        <dependency>
			<groupId>com.webpimageio</groupId>
			<artifactId>webpimageio</artifactId>
			<version>0.4.2</version>
			<systemPath>${basedir}/src/main/webapp/WEB-INF/lib/webp-imageio.jar</systemPath>
			<scope>system</scope>
		</dependency>
        ```
        
        * 3.在项目中使用ImageIO即可读写webp格式文件了（webp和jpg，png格式图片可             以互转）
        
         ```java
            File file1= new File("/home/geeklei/Desktop/640_tp.webp");  
            File file2= new File("/home/geeklei/Desktop/640a.png");  
          
            System.out.println(System.getProperty("java.library.path"));  
          
            try {  
          
                BufferedImage im = ImageIO.read(file1);   
                ImageIO.write(im, "png", file2);  
              
              
                } catch (IOException e) {  
                e.printStackTrace();  
            }  
        ```
        linux下参考：http://blog.csdn.net/GeekLei/article/details/41147479
        
    * java VP8 decoder
    [VP8decoder下载地址][2]
    maven引入本地jar包:
    
        ```java
    <dependency>
			<groupId>com.java.V8</groupId>
			<artifactId>V8decoder</artifactId>
			<version>0.2.0</version>
			<systemPath>${basedir}/src/main/webapp/WEB-INF/lib/WebPViewer-0.2.jar</systemPath>
			<scope>system</scope>
		</dependency>
    	```
    昨天用这个测试没有测试成功，报了异常； 待研究。







* 测试结果webp-imageio，VP8 decoder 

    使用webp-imageio,把jpg，png图片转化成webp格式图片后，肉眼观察显示效果并没有影响，惊喜的是图片的大小缩小为大概原来的1/6。
    VP8decoder 有待研究。



* 阿里云OSS支持webp格式

    	* 图片格式转换：
    
    |名称|描述|
    |---|---|
    |jpg|将原图保存成jpg格式，如果原图是png,webp, bmp存在透明通道，默认会把透明填充成黑色。如果想把透明填充成白色可以指定1wh参数|
    |png|将原图保存成png格式|
    |webp|将原图保存成webp格式|
    |bmp|将原图保存成bmp格式|
    |gif|将gif格式保存成gif格式，非gif格式是按原图格式保存。|
    |src|按原图格式返回，如果原图是gif, 此时返回gif格式第一帧,保存成jpg格式，而非gif格式，如果我想保存成gif格式，必须增加1an参数|

    示例：将jpg转成webp格式
    http://photosd.nggirl.com.cn/work/72695d9003d04f13adddff6902749def.jpg@.webp
    
    
    	* 图片质量转换：
    
    |名称|描述|取值范围|
    |---|---|---|
    |q|决定图片的相对质量，对原图按照 q% 进行质量压缩。如果原图质量是 100%，使用 90q 会得到质量为 90％ 的图片；如果原图质量是 80%，使用 90q 会得到质量72%的图片只能在原图是 jpg格式的图片上使用，才有相对压缩的概念。如果原图为 webp，那么相对质量就相当于绝对质量。|1-100|
    |Q|决定图片的绝对质量，把原图质量压到Q%，如果原图质量小于指定数字，则不压缩。如果原图质量是100%，使用"90Q"会得到质量90％的图片；如果原图质量是95%，使用“90Q”还会得到质量90%的图片；如果原图质量是80%，使用“90Q”不会压缩，返回质量80%的原图。 只能在保存格式为jpg/webp效果上使用，其他格式无效果。 如果一个转换url里，同时指定了q和Q，按Q来处理|1-100|
    
    示例
    将原图缩略成100w_100h，相对原图质量的80%的jpg图
    http://image-demo.img-cn-hangzhou.aliyuncs.com/example.jpg@100w_100h_80q
   
   
    

    
* 综合总结：
    因为阿里云OSS支持webp格式，以及app原生也支持，综合以上结果，最终打算先测试的方案：app原生使用webp，H5使用阿里云OSS80Q（80q）质量压缩

  
  [1]: https://bitbucket.org/luciad/webp-imageio/
  [2]: https://sourceforge.net/projects/javavp8decoder/
  [3]: http://www.myexception.cn/operating-system/1980190.html
