# git使用中的一些问题

## 1，文件名大小写问题

可参考：`http://www.worldhello.net/gotgit/08-git-misc/030-case-insensitive.html`

Windows和Mac OS X（默认安装）的文件系统则是大小写不敏感的文件系统。

修改一个文件名`index.html`重命名为`Index.html`，git会认为这是同一个文件。所以，如果要将`index.html`重命名为`Index.html`，则需要这样做：

第一步，将`index.html`重命名为`index2.html`

第二步，将`index2.html`重命名为`Index.html`

第一步相当于删除了`index.html`,增加了`index2.html`

第二步相当于删除了`index2.html`,增加了`Index.html`

## 
