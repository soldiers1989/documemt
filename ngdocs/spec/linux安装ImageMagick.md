# Imagemagick安装：
1.确保系统安装以下包
> yum install libjpeg

> yum install libjpeg-devel

> yum install libpng

> yum install libpng-devel

> yum install libtiff

> yum install libtiff-devel

> yum install libungif

> yum install libungif-devel

> yum install freetype

> yum install zlib


2.下载对应版本的压缩包ImageMagick-7.0.5-7.tar：http://www.imagemagick.org/download/。

> tar -xvf ImageMagick-7.0.5-7.tar

> cd ImageMagick-7.0.5-7

> ./configure

> make 

> make install 


3.测试是否安装成功：convert 命令默认安装到 /usr/local/bin 目录下

> convert -version 检查是否安装成功

> Version: ImageMagick 7.0.5-3 Q16 x86_64 2017-05-26 http://www.imagemagick.org
Copyright: © 1999-2017 ImageMagick Studio LLC
License: http://www.imagemagick.org/script/license.php
Features: Cipher DPC HDRI OpenMP
Delegates (built-in): jng jpeg png tiff zlib



参考文档：

http://www.linuxidc.com/Linux/2016-05/131331.htm

http://blog.csdn.net/fdipzone/article/details/9079143

http://blog.csdn.net/lisaem/article/details/50330953



