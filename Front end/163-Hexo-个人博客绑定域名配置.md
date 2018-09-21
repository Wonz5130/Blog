---
title: Hexo 个人博客绑定域名配置
date: 2018-09-09 20:59:53
tags: [博客]
categories: 前端
---

>纠结了许久，终于决定绑定一下域名了，配置还是比较简单的。

<!--more-->

### 1.Ping 出 GitHub Pages 的 IP

具体方法是打开 win 的命令行工具 CMD，输入

```cmd
ping yourname.github.io
```

![](163-Hexo-个人博客绑定域名配置\0.png)

返回的 `XXX.XXX.XXX.XXX` 就是 GitHub Pages 的 IP，然后用这个 IP 直接在浏览器输入，结果发现是 404。

![](163-Hexo-个人博客绑定域名配置\5.png)

### 2.绑定域名

之前在[阿里云](https://wanwang.aliyun.com/?spm=5176.8142029.selected.4.e9396d3eGd7SNF)买了个不错的域名。最近正好有空，就绑定了一下。

首先找到控制台 —> 产品与服务 —> 域名 —> 域名列表，点击 `解析` 。

![](163-Hexo-个人博客绑定域名配置\1.png)

因为是第一次用，所以根据`新手引导设置`，输入之前 Ping 出的 IP 地址进行配置就行。

![](163-Hexo-个人博客绑定域名配置\2.png)

尝试在浏览器输入 `www.wonz.wang` ，发现还是 404。

![](163-Hexo-个人博客绑定域名配置\4.png)

### 3.新建 CNAME

在 yourname.github.io 的根目录下添加 CNAME。具体就是在 Hexo 目录里的 source 文件下添加一个名为`CNAME`的文件，注意**这个文件是没有后缀的，千万不要设置成. txt 文本文件**，文件的内容就是域名，格式如：

```txt
www.wonz.wang
```

我是先新建了 CNAME.txt 文件，输入信息保存后，再把后缀 .txt 去掉。

最后再 `hexo g` 和 `hexo d` 部署一下，就不是 404 了。

![](163-Hexo-个人博客绑定域名配置\6.png)

但是一个很重要的事情是，绑定完域名后，网站的访客数从零开始计算了。好不容易的 500+ 访客数啊！！！

![](163-Hexo-个人博客绑定域名配置\7.png)

### 4.致谢

[搭建 Hexo 博客中碰到的坑](https://www.jianshu.com/p/a2fe56d11c4f)

### 5.欢迎经常来[我的博客](http://www.wonz.wang/)玩~

