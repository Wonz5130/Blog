---
title: 阿里云 ECS Ubuntu 系统配置
tag: [服务器]
category: 软件安装
---
>偶然了解到阿里云，正好要做大创跑深度学习，加上大三会学 Linux，就用学生优惠买了个阿里云 ECS 服务器，记录一下 Ubuntu 系统配置。

<!--more-->

成功购买之后，记住远程连接密码，不是登录密码，两个不是同一个东西。然后去[官网](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)下一个 Putty，根据电脑配置选择 32 位/64 位。

安装之后，先在阿里云官网登录账户，进行远程连接。

![](144-阿里云 ECS Ubuntu 系统配置\1.png)

然后，输入刚才记下来的远程连接密码。

![](144-阿里云 ECS Ubuntu 系统配置\2.png)

这时，再输入账户和密码，账户默认是 root 。

![](144-阿里云 ECS Ubuntu 系统配置\4.png)

这时，就可以进行系统操作了。

但是这种方式操作不方便，所以推荐第二种：使用 ssh 进行管理操作。

阿里云系统已经自带了 ssh 服务, 我们用 ssh client 连接进来即可。

SSH 方式远程管理

Windows 用户可以安装 putty, 通过 putty 进行 SSH 操作。

Mac OS 及 Linux 用户可以直接通过控制台进行 ssh 操作。

打开 PuTTY，输入公网 IP 地址，再点击 open。

![](144-阿里云 ECS Ubuntu 系统配置\5.png)

然后，需要输入 root 和登录密码，同上。

![](144-阿里云 ECS Ubuntu 系统配置\6.png)

接下来新建一个管理账户, 以后使用这个管理账户进行远程 ssh 管理, 并禁用 root 账户的 ssh 远程管理功能

添加一个新账户

```linux
adduser username 
```

之后会要输入新密码，然后就是默认 Enter 键，之后再输入 y 确认。

![](144-阿里云 ECS Ubuntu 系统配置\7.png)

创建普通用户 “wonz” 成功, 接下来为用户 “wonz” 赋予 sudo 功能。

找到 User privilege specification，在 root 下面输入

```linux
username ALL=(ALL:ALL) ALL
```

然后，按 ESC 键，确保当前 vi 的状态为命令方式，然后再键入 

```linux
:wq!
```

强制保存并退出 vi。 

![](144-阿里云 ECS Ubuntu 系统配置\8.png)

3.系统更新

```linux
apt-get update
apt-get upgrade
```

4.修改 SSH 配置，提升安全性

首先备份一下配置文件

```linux
cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak
```

输入

```linux
vim /etc/ssh/sshd_config
```

编辑配置文件

配置内容如下：

修改默认的 22 登录端口号为你想要的登陆端口, 最好是大于 1024, 如 2002。(因为还没有学 TCP/IP ，所以我这里端口就和别人的经验贴一样，改为2002)

![](144-阿里云 ECS Ubuntu 系统配置\9.png)

* 禁止 root 用户登陆(这个我没有做)

> PermitRootLogin no

* 禁止使用密码认证

> PasswordAuthentication no

* 禁止空密码登录

> PermitEmptyPasswords no

- 采用 RSA 公钥认证

> StrictModes yes # 检查密钥的用户和权限是否正确, 默认打开的
>
> RSAAuthentication yes # 启用 RSA 认证
>
> PubkeyAuthentication yes # 启用公钥认证
>
> ServerKeyBits 1024 # 将 ServerKey 强度改为 1024 比特

然后，同样先按 ESC，再输入

```linux
:wq!
```

接下来生成 RSA 公钥及秘钥

在本机的控制台下输入

> ssh-keygen

并回车, 可以给 key 文件起个名字 例如 “wonz”

![](144-阿里云 ECS Ubuntu 系统配置\10.png)

接下来一路回车即可

在~/.ssh / 路径下会生成两个文件, 其中后缀为. pub 的为公钥文件, 将其上传只服务器用户目录下(未成功)

> scp ~/.ssh/wonz/@wonz.pub wonz@XXX.XXX.XXX.XXX:~/

以新创建的管理用户登录 ssh, 并在改用户目录下添加. ssh 目录，注意 . 前面有空格

```linux
mkdir .ssh
ls -al
```

![](144-阿里云 ECS Ubuntu 系统配置\11.png)

安装 MySQL

```linux
sudo apt-get install mysql-server
```

键入 mysql 管理员账户密码

![](144-阿里云 ECS Ubuntu 系统配置\12.png)安装 Apache 

```linux
sudo apt-get install apache2
```

在浏览器里键入 http:// 阿里云服务器公网 IP   验证一下

如看到 WEB 页面, 则表示 Apache 服务已经安装成功(未成功)。

安装 PHP 5 环境

```linux
sudo apt-get install libapache2-mod-php5
sudo a2enmod php5
```

### 致谢

[阿里云服务器 ECS Ubuntu 系统安装配置](https://www.aliyun.com/jiaocheng/190620.html)