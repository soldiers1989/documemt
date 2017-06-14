# 为Github账户设置SSH key

如果你的git命令使用的是https方式连接，那么每次pull、push操作时git都会让你输入密码。
通过为Github账户设置SSH key，可以使得以后提交代码时不再反复输入密码，提高开发效率。

# 生成新的SSH key

1. 打开终端

2. 粘贴下面的文本，替换成你自己的邮箱

	`ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`

3. 回车会创建一个新的ssh key，提示信息

	`Generating public/private rsa key pair.`

4. 询问把key保存到哪里，回车，使用默认位置即可，提示信息

	`Enter a file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]`

    windows平台显示如下

    `Enter a file in which to save the key (/c/Users/you/.ssh/id_rsa):[Press enter]`

5. 输入密码

	```
	Enter passphrase (empty for no passphrase): [Type a passphrase]
	Enter same passphrase again: [Type passphrase again]
	```

# 把SSH key添加到GitHub账户

1. 在终端中输入如下命令，复制上面生成的ssh key

	Mac平台

	`pbcopy < ~/.ssh/id_rsa.pub`

	windows平台

	`clip < ~/.ssh/id_rsa.pub`

2. 浏览器中打开GitHub网站，进入GitHub账户，选择Settings -->  SSH and GPG keys --> New SSH key 或 Add SSH key

3. 输入一个标题，比如`Personal MacBook Air`

4. 在Key文本框中粘贴上文拷贝的key

5. 点击`Add SSH key`按钮

6. 如果弹出对话框，输入GitHub密码即可。

# 测试SSH Key登录

1. 打开终端, 测试`ssh -T git@github.com`

2. 成功信息

   ```
   Hi your_email! You've successfully authenticated, but GitHub does not provide shell access.
   ```

# 参考资料

1. https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/#platform-mac

2. https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/#platform-mac

3. http://www.jianshu.com/p/ddd3122cb351
