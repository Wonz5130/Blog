---
title: OpenGL SOIL2 环境配置
date: 2018-09-23 20:46:25
tags: [OpenGL,SOIL2]
categories: 软件安装
---

>继上次 OpenGL 环境配置之后，老师又教了纹理，现在又要进行 SOIL2 的环境配置了。

<!--more-->

### 一、下载 SOIL2、Premake

用 Google 搜索 SOIL2，直接点击下载。

这里推荐两个 Google 镜像网站，不用梯子可以直接当 Google 用。

[Google 镜像网站 1](https://plus.likeso.ml/)

[Google 镜像网站 2](https://busca.uol.com.br/)

![](166-OpenGL-SOIL2-环境配置\1.png)

去 [官网](https://premake.github.io/download.html) 下载 Permake Version 4.4 beta 版。

![](166-OpenGL-SOIL2-环境配置\2.png)

然后，解压这两个压缩包。把 premake 4.4 beta5 windows 文件夹里面的 premake4.exe 拷贝到 SOIL2 所在的文件夹中，见下图。

![](166-OpenGL-SOIL2-环境配置\3.png)

### 二、SOIL2 配置

打开 Command Prompt，cd 到 SOIL2 的目录下，见下图。

![](166-OpenGL-SOIL2-环境配置\4.png)

然后，输入

```bash
premake4.exe vs2012
```

vs2015 不能成功，就输 vs2012了。

然后，你会发现文件夹里面多了一个 `make` 的文件夹，双击进入，再进入 `windows` 文件夹，双击打开 `SOIL2.sln` 。

![](166-OpenGL-SOIL2-环境配置\5.png)

右击 `soil2-static-lib` ，选择 `Build` ，然后可以关闭了。

![](166-OpenGL-SOIL2-环境配置\6.png)

返回到 `SOIL2` 的文件夹，会发现有个 `lib` 文件夹，双击进入，再进入 `windows` 的文件夹，会发现一个 `soil2-debug.lib` 的文件。在之前 `glew` 和 `glfw` 的文件夹下，新建一个 `SOIL2` 的文件夹，在里面再新建一个 `lib` 的文件夹，把之前那个文件拷贝过去。

![](166-OpenGL-SOIL2-环境配置\7.png)

返回到之前的 `SpartanJ SOIL2` 的文件夹，进入 `src` 的文件夹，把 `SOIL2` 整个文件夹拷贝到 `main.cpp` 所在目录下。

![](166-OpenGL-SOIL2-环境配置\8.png)

### 三、链接配置

右击 `Project3` ，选择 `Properties` 。

![](166-OpenGL-SOIL2-环境配置\9.png)

在 `Linker` 中，点击 `General` ，选择 `Additional Library Directories` ，添加之前那个包含 `soil2-debug.lib`  的 `lib` 路径。

![](166-OpenGL-SOIL2-环境配置\10.png)

![](166-OpenGL-SOIL2-环境配置\11.png)

然后再在 `Linker` 的 `Input` 中，添加 `soil2-debug.lib` 。

![](166-OpenGL-SOIL2-环境配置\12.png)

![](166-OpenGL-SOIL2-环境配置\13.png)

点击 `应用` ，再点击 `OK` ，就可以了。

最后，在 `Project3` 中，添加头文件。

```C++
#include "SOIL2/SOIL2.h"
```

配置就完成了。