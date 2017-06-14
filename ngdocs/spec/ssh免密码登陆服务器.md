# SSH免密码登陆服务器

假设你自己的主机A，另一台主机B。且A主机中用户名为auser，B主机中有用户buser。

你想要使用SSH，以buser身份，进行免密码登陆B主机。

## 生成公钥、私钥

1，进入A主机auser用户的.ssh目录

```
cd ~/.ssh/
```

2，生成公钥和私钥

```
ssh-keygen -t rsa
```

中间会要求你输入公钥、私钥对应的文件名，以及密码，两者都可以为空。

建议文件名不要使用空，因为如果为空，默认文件名为id_rsa，有可能与你自己auser主目录已有的文件名重合了，原有的id_rsa被覆盖了

```
Generating public/private rsa key pair.
Enter file in which to save the key (<auser用户主目录>/.ssh/id_rsa):<文件名>
Enter passphrase (empty for no passphrase):<密码>
Enter same passphrase again:
Your identification has been saved in <文件名>.
Your public key has been saved in <文件名>.pub.
The key fingerprint is:
SHA256:miZvCVcuIGfy8GK9rADBVX18QUlqZJcaRyw82Cpj568 forest@bogon
The key's randomart image is:
+---[RSA 2048]----+
|   .... =o=*+    |
|. .    ooOo*     |
|..      ooB      |
| .+ ++ oo.       |
|.  X..=oS        |
|. o = o+.        |
|.. o.++o.        |
| .  o+o  .       |
|  .. ..E.        |
+----[SHA256]-----+
```

3，将auser的主目录的私钥文件加入到SSH中

```
ssh-add ~/.ssh/<文件名>
```

## 主机B用户中添加公钥

1，假设主机B的buser主目录中的.ssh文件夹下没有authorized_keys文件，则直接上传公钥即可

```
scp <A主机用户主目录>/.ssh/<文件名>.pub <B主机用户>@<B主机域名或者IP地址>:<B主机用户主目录>/.ssh/authorized_keys
```

示例：

```
scp /User/auser/.ssh/server.pub buser@www.baidu.com:/home/buser/.ssh/authorized_keys
```

2，假如主机B的buser主目录中的.ssh文件夹下已经存在了authorized_keys文件

1）上传公钥文件

```
scp <A主机用户主目录>/.ssh/<文件名>.pub <B主机用户>@<B主机域名或者IP地址>:<forest主目录>/.ssh/
```

示例

```
scp /User/auser/.ssh/server.pub buser@www.baidu.com:/home/buser/.ssh/
```

2）在B主机的buser用户主目录，备份authorized_keys文件

```
cd ~/.ssh
mv authorized_keys authorized_keys.backup
```

3）将新的公钥附加到authorized_keys中

```
cat <文件名>.pub >> authorized_keys
rm -f <文件名>.pub
```

## 无密码登陆

```
ssh <B主机中的用户名>@<B主机域名或者IP地址>
```

示例

```
ssh buser@www.baidu.com
```
