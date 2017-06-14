# git 设置存储用户名与密码

git是没有记录密码用户名的，于是乎只能自己设置，在命令行设置咋设置，代码如下

```shell
git config --global user.name "myusername"
git config --global user.email "myusername@myemaildomain.com"
git config --global credential.helper cache
```

但是最后一行  cache不是windows 下的，在windows平台上改成

`git config --global credential.helper wincred`
