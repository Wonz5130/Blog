---
title: 在 VMware 虚拟机上安装 Linux 系统 (CentOS 不带界面版) 教程
date: 2018-09-25 20:11:49
tags: [虚拟机,Linux,CentOS]
categories: 软件安装
---

> Linux 老师建议安装不带界面的 Linux 系统，学习 Linux 就是要学命令行编程，于是我又装了一个不带界面，只有命令行的 CentOS 虚拟机。

<!--more-->

### 一、前期准备

首先，安装一个虚拟机软件，可以参考我的[这篇博客](https://www.wonz.wang/2018/09/22/165-%E5%9C%A8-VMware-%E8%99%9A%E6%8B%9F%E6%9C%BA%E4%B8%8A%E5%AE%89%E8%A3%85-Linux-%E7%B3%BB%E7%BB%9F-Ubuntu-%E6%95%99%E7%A8%8B/)。

再安装镜像文件。意外发现学校的[开源软件网站](http://mirrors.njupt.edu.cn/#)有 CentOS 镜像文件下，就不去官网下了。这里选择的是 CentOS 7 Minimal。

### 二、安装

##### 1.创建虚拟机

这里选择 `自定义` 。

![](167-在-VMware-虚拟机上安装-Linux-系统-CentOS-教程\1.png)

##### 2.安装过程选项配置

![](167-在-VMware-虚拟机上安装-Linux-系统-CentOS-教程\2.png)

![](167-在-VMware-虚拟机上安装-Linux-系统-CentOS-教程\3.png)

![](167-在-VMware-虚拟机上安装-Linux-系统-CentOS-教程\4.png)

![](167-在-VMware-虚拟机上安装-Linux-系统-CentOS-教程\5.png)

##### 3.处理器配置

![](167-在-VMware-虚拟机上安装-Linux-系统-CentOS-教程\6.png)

![](167-在-VMware-虚拟机上安装-Linux-系统-CentOS-教程\7.png)

![](167-在-VMware-虚拟机上安装-Linux-系统-CentOS-教程\8.png)

![](167-在-VMware-虚拟机上安装-Linux-系统-CentOS-教程\9.png)

![](167-在-VMware-虚拟机上安装-Linux-系统-CentOS-教程\10.png)

![](167-在-VMware-虚拟机上安装-Linux-系统-CentOS-教程\11.png)

![](167-在-VMware-虚拟机上安装-Linux-系统-CentOS-教程\12.png)

![](167-在-VMware-虚拟机上安装-Linux-系统-CentOS-教程\13.png)

![](167-在-VMware-虚拟机上安装-Linux-系统-CentOS-教程\14.png)

##### 4.编辑虚拟机设置

![](167-在-VMware-虚拟机上安装-Linux-系统-CentOS-教程\15.png)

![](167-在-VMware-虚拟机上安装-Linux-系统-CentOS-教程\16.png)

### 三、安装 CentOS

![](167-在-VMware-虚拟机上安装-Linux-系统-CentOS-教程\17.png)

##### 1.选择安装

“↑” “↓” 键选择第一个然后回车。

![](167-在-VMware-虚拟机上安装-Linux-系统-CentOS-教程\18.png)

##### 2.选择语言

![](167-在-VMware-虚拟机上安装-Linux-系统-CentOS-教程\19.png)

##### 3.安装配置

软件安装中的 `最小安装` 指的就是不带桌面的，纯命令行的安装。

![](167-在-VMware-虚拟机上安装-Linux-系统-CentOS-教程\20.png)

##### 4.设置 ROOT 密码和创建用户

![](167-在-VMware-虚拟机上安装-Linux-系统-CentOS-教程\21.png)

注意，如果密码过于简单，需要按两次 `完成` 。

![](167-在-VMware-虚拟机上安装-Linux-系统-CentOS-教程\22.png)

##### 5.重启

![](167-在-VMware-虚拟机上安装-Linux-系统-CentOS-教程\23.png)

##### 6.安装成功

![](167-在-VMware-虚拟机上安装-Linux-系统-CentOS-教程\24.png)

### 四、致谢

[在虚拟机中安装 CentOS7](https://jingyan.baidu.com/article/eae0782787b4c01fec548535.html)

[vmware 虚拟机安装 CentOS 教程](https://www.cnblogs.com/AlanLee/p/7686508.html)

