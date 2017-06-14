# 分支管理
1. 查看当前所在分支  
  `git branch`
2. 切换到（已经存在的）指定分支  
  `git checkout <已存在的分支名称>`  
  *注：如果本地暂存区内有内容（即你运行过git add命令，或者使用git status查看，存在绿色文件），则会切换失败，需要提交暂存区内容或者将暂存区内容丢弃，才能切换*
3. 以本地当前分支为起点，创建新分支  
  `git branch <要创建的新分支名称>`  
  *注：也有可能创建失败，理由同切换分支功能。*
4. 以本地当前分支为起点，创建新分支并切换到新分支  
  `git checkout -b <要创建并切换的新分支名称>`  
   其实这个命令是一个组合命令：
    - `git branch <要创建的新分支名称>`
    - `git checkout <已存在的分支名称>`
5. 以远程仓库的远程分支为起点，创建新分支并切换到新分支  
  `git checkout -b <要创建并切换的新分支名称> <远程仓库名称>/<远程分支名称>`  
    例如：
    `git checkout -b develop origin/develop`
    *第一个develop是要创建的本地分支名称，origin是远程仓库名称，第二个develop是远程分支名称*
6. 当从远程拉取内容时，直接使用`git pull`即可，不需要指定远程仓库和分支名称。
    当从本地向远程推送内容时，直接使用`git push`即可，不需要指定远程仓库和分支名称。

    *但是当`git remote -v`列出的结果有多个时，需要加上<远程仓库名称>/<远程分支名称>
    前提是你先前配置多个账户的追踪(`git remote add`)，此应用场景适用于review别人代码时。*
7. 将本地分支与远程分支设置关联（追踪tracking）  
`git branch —set-upstream-to=<远程仓库名称>/<远程分支名称> <本地分支名称>`  
    例如：
    `git branch —set-upstream-to=origin/develop develop`  
    *origin是远程仓库名称，第一个develop是远程分支名称，第二个develop是本地创建的分支名称*

    *当从远程拉取内容时，直接使用git pull即可，不需要指定远程仓库和分支名称
    当从本地向远程推送内容时，直接使用git push即可，不需要指定远程仓库和分支名称*
8. 查看本地分支与远程分支的追踪关系  
`git branch -vv`
    *！注意是两个v*
9. 合并其他分支到当前分支  
`git merge <需要合并进来的分支名称>`
10. 从远程仓库拉取内容  
    将远程仓库的所有分支的最新修改，全部取回到本地  
    `git fetch <远程仓库名称>`  
     将远程仓库指定分支的最新修改，取回到本地  
    `git fetch <远程仓库名称> <远程分支名称>`  
11. 拉取远程仓库的远程分支，并合并到当前分支中  
    `git pull <远程主机名> <远程分支名>:<本地分支名>`  
    由于远程分支与本地分支名称相同，则可以简化为  
    `git pull <远程主机名> <远程分支名>`  
    当设置了本地分支对应关联的远程分支时，又可以简化为`git pull`  
    注：git pull命令是一个组合命令，相当于  
    - `git fetch <远程仓库名称>`
    - `git merge  <远程仓库名称>/<远程分支名称>`

    示例：
    ```
    git pull origin develop:develop
    git pull origin develop
    git pull
    ```
    当你设置本地分支和远程分支相同名称，并且设置了关联关系（就是追踪关系tracking），则这三个命令效果相同

11. rebase合并`git rebase -i <要合并进来的分支名称>`
    适用场景
    `使用 git rebase -i HEAD~<次数>`进入commit管理模式，根据提示有如下操作
    - 合并多次提交
    - 修改提交的commit message
    - 删除某个commit，通过commit id

    rebase中间态可执行的操作
    ```
    git add <filename>
    git rebase —continue
    git rebase --abort
    ```

# 冲突解决
1. 有可能产生冲突的命令
    - git merge <需要合并进来的分支名称>
    - git pull <远程仓库> <远程分支>
    - git rebase -i <要合并进来的分支名称>

2. 解决冲突
    发生冲突后，使用git status可以查看到冲突文件是红色字体显示的。打开文件，冲突部分会有特定表示如下
    ```
    <<<<<<< HEAD
    冲突发生前，没有进行合并时，当前位置的代码
    =======
    合并进来的冲突代码
    >>>>>>>
    ```
    *注：用户需要根据具体业务删除或者保留对应的代码，同时将<< HEAD == >> 这些标示去掉。
    有时>>>>>>>后面会跟一些描述信息，比如分支名称、提交时的注释等等。*

# 替换撤销命令
**！！需要谨慎使用的一些命令，因为如果这些命令使用不当会导致数据丢失，而且丢失的数据再也找不回来了，使用前可以咨询我和郭宏斌**

1. 删除分支

  ```
    git branch -D <要删除的分支名称> 强制删除，即便没有被合并到主分支
    git branch -d <要删除的分支名称> 非强制删除，如果没有被合并到主分支，则无法删除
  ```

2. 替换掉工作目录中的某一个文件,放弃对它的所有修改，将该文件更新到最近的一次提交版本`git checkout <文件路径>`  
    *注：替换之后，则该文件再也找不回来了，需谨慎使用！*

3. 清除暂存区内的指定文件的暂存内容  
    `git reset HEAD <文件路径>`  
    注：清除之后，则该文件再也找不回来了，需谨慎使用！

4. 撤销提交到指定的版本`git reset <指定版本编号>`  
    *注：撤销后，指定版本之后的所有提交都会被撤销，并回退到当前工作目录，执行git status可以看到，所有已修改的文件都是红色字体显示。
    3，4可以使用`git reflog`查看日志改动*

# 常用使用场景举例
1. 日常性工作
    - 工作之前使用git branch查看当前分支，使用git status查看我们工作目录中是否有未提交的修改，使用git diff查看我们都修改了哪些内容
    - 使用git pull或者git fetch 、git merge命令将远程内容拉取到本地，并合并到当前分支中
    - 使用git add将我们的修改添加到暂存区内，使用git commit提交本次修改（注意使用-m添加提交说明）关于commit提交的信息，如果深究的话，是有很多要求的，而且它的功能很强大。
    - 使用 git status查看是否提交完成
    - 使用git pull拉取远程分支的修改
    - 使用git push推送本次修改
2. 不能快速解决的任务，或者需要紧急修复的bug
    - 使用git branch查看当前分支
    - 使用git checkout切换到需要紧急修复的分支
    - 使用git checkout -b迁出一个修复分支（例如叫fix）
    - 在fix分支上修复bug，使用git add、git commit提交修改
    - 使用git checkout切换到需要紧急修复的分支，使用git pull拉取远程内容，使用git merge fix合并修改
    - 使用git status查看合并是否产生冲突
    - 使用git push推送修改到远程仓库


# 处理单个文件
1. 恢复删除的文件
    找到修改待恢复文件的最后一次提交  
    `git rev-list -n 1 HEAD -- <file_path>`  
    然后签出这次提交之前的提交  
    `git checkout <deleting_commit>^ -- <file_path>`  
    或者使用合并之后的命令（这里的`$file` 指的是待恢复的文件）  
    `git checkout $(git rev-list -n 1 HEAD -- "$file")^ -- "$file"`  
2. 重置或者还原某次提交的某个文件  
    `git checkout commit_id _file/to/restore`
3. 去掉对某个文件的更改  
    `git show commit_id -- <file> | git apply -R`
