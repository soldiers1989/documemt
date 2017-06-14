<h1>由于uploadserver依赖于ImageMagick，所以我们使用它的时候不仅要引入相关jar包，还需要安装ImageMagick这个软件或者包</h1>
------
<h2>1.引入maven jar包</h2>

```java
<dependency>
            <groupId>org.im4java</groupId>
            <artifactId>im4java</artifactId>
            <version>1.4.0</version>
  </dependency>
```

光引入jar包还不够，还需要安装ImageMagick

<h2>2.安装ImageMagick</h2>

windows安装：
> ImageMagick-6.3.9-0-Q16-windows-dll.exe直接安装exe文件.在windows下运行，则需要配置ImageMagick的路径，在环境变量path添加（C:\Program Files\ImageMagick-6.7.5-
Q16）在config.properties文件里了，内容如下所示： imageMagickPath=C:\Program Files\ImageMagick-6.7.5-Q16
> windows下调用convert时，需要设置imageMagick路径
	      ConvertCmd convert = new ConvertCmd();  
        // linux下不要设置此值，不然会报错  
        convert.setSearchPath(imageMagickPath);  


linux下安装：
> 命令：yum install -y ImageMagick ImageMagick-devel，在linux平台下，不需要配置，不然会报错

<h2>3.部署</h2>
在把我们的uploadserver部署到服务器上时（linux），只需要安装ImageMagick。
安装命令yum install -y ImageMagick ImageMagick-devel。
安装完之后使用convert -version检查是否安装成功，显示如下信息，表示安装成功。

> Version: ImageMagick 6.7.2-7 2016-06-16 Q16 http://www.imagemagick.org
Copyright: Copyright (C) 1999-2011 ImageMagick Studio LLC
Features: OpenMP

安装之后，正常流程部署。
