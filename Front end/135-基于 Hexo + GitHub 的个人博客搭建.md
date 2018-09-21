---
title: 基于 Hexo + GitHub 的个人博客搭建
tag: [博客]
category: 前端
---
>作为一个学计算机的大学生，GitHub 自然是必须要有的，博客也是要得。之前一直用 CSDN 写的博客，偶然看到基于 Hexo + GitHub 可以搭建轻量级个人博客，于是心血来潮，折腾了一个星期，终于配置好了[个人博客](https://wonz5130.github.io/)。

<!--more-->

# 一、准备工作：下载并安装软件
下载 [Node.js](https://nodejs.org/en/) 和 [Git](https://git-scm.com/) 

# 二、注册 GitHub 账号并新建仓库
首先，注册 GitHub 账号，新建一个仓库。注意：username 改成你的 GitHub 账号的名字。(注意，是账号名字，不是昵称)
![](135-基于 Hexo + GitHub 的个人博客搭建\1.png)

# 三、配置 SSH Key
打开 Git Bash，输入

## 3.1 检查 SSH Keys 的设置
``` bash
$ cd ~/. ssh
```

如果显示 “No such file or directory”，说明这是你第一次使用 git。

## 3.2 生成新的 SSH

``` bash
$ ssh-keygen -t rsa -C "邮件地址@youremail.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/your_user_directory/.ssh/id_rsa):<回车就好>
```

邮件地址写你注册 GitHub 的邮箱地址，-C 是大写的 C。
然后系统会让你设置 SSH 密码。

``` bash
Enter passphrase (empty for no passphrase):<设置密码>
Enter same passphrase again:<再次输入密码>
```

在回车中会提示你输入一个密码，这个密码会在你提交项目时使用，如果为空的话提交项目时则不用输入。这个设置是防止别人往你的项目里提交内容。
### 注意：
输入密码的时候没有输入痕迹的，不要以为什么也没有输入。
最后看到如下图所示的界面，表示 SSH Key 就设置好了。

![](135-基于 Hexo + GitHub 的个人博客搭建\2.png)

## 3.3 添加 SSH Key 到 GitHub 中
在本地文件夹找到 id_rsa.pub 文件，路径在上面那张截图上。没找到的话，在查看里勾选一下文件扩展名和隐藏的项目。
将.ssh 文件夹里记事本打开这个 id_rsa.pub 文件，复制全部内容到 GitHub 相应位置。
GitHub 相应位置在：点击头像，再点击 Settings。

![](135-基于 Hexo + GitHub 的个人博客搭建\3.png)

找到 SSH，点击它。

![](135-基于 Hexo + GitHub 的个人博客搭建\4.png)
会出现一个 Title 和 Key。
Title 最好写，随便写。网上有说不写 title 也有可能后期出现乱七八糟的错误。
Key 部分就是粘贴刚才复制的内容，最后点击 Add SSH key。

## 3.4 测试
在 Git Bash 里
输入以下代码，注意不要改任何一个字。

``` bash
$ ssh -T git@github.com
```

如果显示以下信息：

``` bash
The authenticity of host 'GitHub.com (207.97.227.239)' can't be established.
RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
Are you sure you want to continue connecting (yes/no)
```

输入：yes 回车即可

``` bash
Enter passphrase for key '/c/Users/lenovo/.ssh/id_rsa':
```

输入刚才设置的密码回车即可。

# 四、开始搭建 Hexo 博客
打开 Git Bash，输入：

``` bash
$ cd
$ npm install -g hexo
```

## 4.1 创建独立博客项目文件夹
安装完成后，关掉前面那个 Git Bash 窗口。在本地创建一个与 Repository 中博客项目同名的文件夹（如 D:\Code\Wonz5130.github.io）在文件夹上点击鼠标右键，选择 Git bash here；

### 注意
在进行博客搭建工作时，每次使用命令都要在 D:\Code\Wonz5130.github.io 目录下。
执行下面的指令，Hexo 就会自动在 D:\Code\Wonz5130.github.io 文件夹建立独立博客所需要的所有文件。

``` bash
$ hexo init
```

## 4.2 安装依赖包

``` bash
$ npm install
```

## 4.3 确保 git 部署

``` bash
$ npm install hexo-deployer-git --save
```

## 4.4 本地查看
现在已经搭建好本地的 Hexo 博客了，执行完下面的命令就可以到浏览器输入 localhost:4000 查看预览效果了。

``` bash
$ hexo g
$ hexo s
```
hexo g：是 hexo generate 的缩写形式，每次进行相应改动都要 hexo g 生成一下。
hexo s：是 hexo serve 的缩写形式，启动服务预览。

![](135-基于 Hexo + GitHub 的个人博客搭建\5.png)

## 4.5 部署到 GitHub 上
然后，输入：

``` bash
$ hexo d
```
hexo d：是 hexo deploy 的缩写形式，将博客部署到 GitHub 上。这里会要输入 SSH 的密码。

![](135-基于 Hexo + GitHub 的个人博客搭建\6.png)

好了，到这里博客基本搭建好了，下一篇介绍配置好看的主题。

# 六、致谢
[技术小白搭建个人博客  github+hexo - kkl的文章 - 知乎](https://zhuanlan.zhihu.com/p/32957389)

