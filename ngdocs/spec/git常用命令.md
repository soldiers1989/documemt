# Git常用命令

git相关文档：

1，GitBook https://git-scm.com/book/zh/v2/

2，GotGit Git权威指南 http://www.worldhello.net/gotgit/

3，GotGitHub http://www.worldhello.net/gotgithub/

### 1，取git仓库：git clone url

#### （1）详细说明：

http://git-scm.com/book/zh/v2/Git-%E5%9F%BA%E7%A1%80-%E8%8E%B7%E5%8F%96-Git-%E4%BB%93%E5%BA%93

#### （2）使用示例：

```shell
git clone git@github.com:mybatis/mybatis-3.git mybatis-3
git clone https://github.com/mybatis/mybatis-3.git mybatis-3
```

注：第二个参数(mybatis-3)是本地创建的仓库名字,不填写时默认是mybatis-3，与远程仓库名相同

#### （3）重点：

1，Git 克隆的是该 Git 仓库服务器上的几乎所有数据，而不是仅仅复制完成你的工作所需要文件。

当你执行 git clone 命令的时候，默认配置下远程 Git 仓库中的每一个文件的每一个版本都将被拉取下来。 事实上，如果你的服务器的磁盘坏掉了，你通常可以使用任何一个克隆下来的用户端来重建服务器上的仓库（虽然可能会丢失某些服务器端的挂钩设置，但是所有版本的数据仍在）

2，Git 支持多种数据传输协议。 上面的例子使用的是 https:// 协议，不过你也可以使用 git:// 协议或者使用 SSH 传输协议，比如 user@server:path/to/repo.git 。https和ssh的使用区别：http://www.linuxidc.com/Linux/2015-11/124752.htm

### 2，查看仓库中文件状态：git status

git四种状态说明及转换说明：http://git-scm.com/book/zh/v2/Git-%E5%9F%BA%E7%A1%80-%E8%AE%B0%E5%BD%95%E6%AF%8F%E6%AC%A1%E6%9B%B4%E6%96%B0%E5%88%B0%E4%BB%93%E5%BA%93

>注：使用git status -s命令，可以得到更紧凑的输出格式

### 3，显示修改文件后与修改文件前的不同：git diff

>注：该命令只是用于对比未暂存状态和已暂存状态两者的不同

### 4，加入暂存区：git add 文件路径

（1）将未跟踪过的新文件加入到暂存区

（2）将已跟踪且已修改的文件加入到暂存区

（3）将合并时发生冲突的文件加入到暂存区（冲突的文件需要自己手动解决）

>注：git add .  命令可以将以上三种情况的文件都加入到暂存区

### 5，将暂存区的文件，加入到本地仓库中：git commit

#### (1)，git commit -m "这里是注释"

将暂存区的文件，加入到本地仓库中。如果暂存区的文件被修改了，但是没有使用git add 命令再次添加到暂存区，则本次提交只会提交暂存区中已有的副本，不会提交用户最新的修改。

#### (2)，git commit -am "这里是注释"

将暂存区的文件，加入到本地仓库中。如果暂存区的文件被修改了，但是没有使用git add 命令再次添加到暂存区，则本次提交会提交用户最新的修改。

此命令相当于执行了：

```
git add .
git commit -m "这里是注释"
```

### 6，从远程仓库的指定分支拉取最新代码到本地仓库的当前分支：git pull origin develop

origin为远程仓库名称
develop为远程仓库分支名称

>注：使用git remote -v 可以查看远程仓库列表

### 7，将本地仓库的当前分支推送到远程仓库的制定分支：git push origin develop

origin为远程仓库名称
develop为远程仓库分支名称

>注：使用git remote -v 可以查看远程仓库列表
