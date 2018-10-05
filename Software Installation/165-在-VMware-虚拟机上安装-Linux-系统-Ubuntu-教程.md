---
title: 在 VMware 虚拟机上安装 Linux 系统 (Ubuntu)  教程
date: 2018-09-22 23:04:13
tags: [虚拟机,Linux,Ubuntu]
categories: 软件安装
---

>之前装过双系统，用的 Deepin，虽然体验很好，但是不能关机，一直没解决。这次就装虚拟机了，选择的是 Ubuntu 18.04.1 TS 版本。

<!--more-->

### 一、前期准备

首先，安装一个虚拟机软件，这里选择的是 [VMware Workstation 12 破解版](https://pan.baidu.com/s/1ymwPu3rZnk3ZGq4FZscDjw) ，密码是 a9sz 。

里面有两个激活码，只适合 VM 12 。

```txt
VY1DU-2VXDH-08DVQ-PXZQZ-P2KV8 
VF58R-28D9P-0882Z-5GX7G-NPUTF
```

去[官网](https://www.ubuntu.com/download/desktop)下载安装一个 Ubuntu 镜像文件。这里选择的是 Ubuntu 18.04.1 TS 版本。

### 二、安装

##### 1.创建虚拟机

这里选择 `自定义` ，第一次装的时候用的是上面的 `典型` ，出问题了。

![](165-在-VMware-虚拟机上安装-Linux-系统-Ubuntu-教程\15.png)

##### 2.安装过程选项配置

![](165-在-VMware-虚拟机上安装-Linux-系统-Ubuntu-教程\16.png)

![](165-在-VMware-虚拟机上安装-Linux-系统-Ubuntu-教程\17.png)

![](165-在-VMware-虚拟机上安装-Linux-系统-Ubuntu-教程\18.png)

![](165-在-VMware-虚拟机上安装-Linux-系统-Ubuntu-教程\19.png)

##### 3.处理器配置

![](165-在-VMware-虚拟机上安装-Linux-系统-Ubuntu-教程\20.png)

![](165-在-VMware-虚拟机上安装-Linux-系统-Ubuntu-教程\21.png)

![](165-在-VMware-虚拟机上安装-Linux-系统-Ubuntu-教程\22.png)

![](165-在-VMware-虚拟机上安装-Linux-系统-Ubuntu-教程\23.png)

![](165-在-VMware-虚拟机上安装-Linux-系统-Ubuntu-教程\24.png)

![](165-在-VMware-虚拟机上安装-Linux-系统-Ubuntu-教程\25.png)

![](165-在-VMware-虚拟机上安装-Linux-系统-Ubuntu-教程\26.png)

![](165-在-VMware-虚拟机上安装-Linux-系统-Ubuntu-教程\27.png)

##### 4.编辑虚拟机设置

![](165-在-VMware-虚拟机上安装-Linux-系统-Ubuntu-教程\28.png)

![](165-在-VMware-虚拟机上安装-Linux-系统-Ubuntu-教程\29.png)

### 三、安装 Ubuntu

##### 1.选择语言并安装

![](165-在-VMware-虚拟机上安装-Linux-系统-Ubuntu-教程\30.png)

![](165-在-VMware-虚拟机上安装-Linux-系统-Ubuntu-教程\31.png)

![](165-在-VMware-虚拟机上安装-Linux-系统-Ubuntu-教程\32.png)

##### 2.清除整个磁盘并安装

注意，最好选一个没什么文件的盘，我是分了一个 20G 的区专门给这个虚拟机用的。

![](165-在-VMware-虚拟机上安装-Linux-系统-Ubuntu-教程\33.png)

![](165-在-VMware-虚拟机上安装-Linux-系统-Ubuntu-教程\34.png)

##### 3.设置用户

![](165-在-VMware-虚拟机上安装-Linux-系统-Ubuntu-教程\35.png)

##### 4.重启虚拟机

![](165-在-VMware-虚拟机上安装-Linux-系统-Ubuntu-教程\36.png)

##### 5.安装 VMware Tools

![](165-在-VMware-虚拟机上安装-Linux-系统-Ubuntu-教程\37.png)

发现，一直不能连接上去，关掉桌面居然有一个 `VMware Tools` 的文件。

双击打开 `VMwareTools-10.0.5-3228253.tar.gz` 文件, 解压缩（提取）到桌面后，打开桌面的文件夹，在空白处右键，选择 `在终端打开` 。

输入

```bash
sudo ./vmware-install.pl
```

输入密码

看到有 `yes` 的，输入 `yes` ，其他一路回车就可以了。

不过我遇到一个问题 `what is the location of the ifconfig program` ，找到一篇[百度经验](https://jingyan.baidu.com/article/25648fc163778e9191fd00c7.html)，还是不成功。

### 四、致谢

[VMware12 安装虚拟机教程、Ubuntu16.04 安装教程](https://jingyan.baidu.com/article/c275f6ba07e269e33d756714.html)

[VMware 虚拟机安装 Ubuntu 简单教程](https://www.jianshu.com/p/3379892948da)

[在 VMware 虚拟机中安装 Ubuntu 系统](https://blog.csdn.net/wumumang/article/details/54099997)

[vmware workstation 12 pro 虚拟机安装系统教程](https://jingyan.baidu.com/article/86fae346ce751b3c48121a6d.html)

[怎样在 VMware 虚拟机中使用安装并设置 Ubuntu 系统](https://jingyan.baidu.com/article/14bd256e0ca52ebb6d26129c.html)

[如何在你的虚拟机上面安装 linux 系统](https://jingyan.baidu.com/article/48a42057bc8dd3a92425049f.html?tdsourcetag=s_pctim_aiomsg&qq-pf-to=pcqq.c2c)