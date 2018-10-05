---
title: Visual Studio 2017 配置 OpenGL
date: 2018-09-06 08:12:09
tags: [OpenGL,计算机图形学,C]
categories: 软件安装
---

>大三第一学期开了一门《计算机图形学》的课，老师让安装一下 VS，并进行 OpenGL 配置，以后上课带电脑到教室，课堂进行编程。这里安装的是 Visual Studio 2017 版本。

<!--more-->

### 一、下载 VS 2017

去[官网](https://visualstudio.microsoft.com/zh-hans/downloads/)，选择 VS 2017 社区版进行下载，并选择 C/C++ 模块进行安装。

![](161-Visual-Studio-2017-配置-OpenGL\0.png)

### 二、下载 GLEW

去[官网](http://glew.sourceforge.net/)，下载 Binaries Windows 32-bit and 64-bit。下载完记得解压，推荐使用 [Bandizip](https://www.bandisoft.com/bandizip/) 软件进行解压。

![](161-Visual-Studio-2017-配置-OpenGL\15.png)

### 三、下载GLFW

去[官网](http://www.glfw.org/download.html)，下载 Windows pre-compiled binaries 32-bit。推荐下 32 位，64 位会出现莫名其妙的问题。下载完记得解压。

![](161-Visual-Studio-2017-配置-OpenGL\16.png)

### 四、新建 C++ 空项目

打开 vs2017，新建 c++ 空项目。

**注：**如果新建 Windows 控制台应用程序，程序内部会自动包含 stdafx.h 的头文件，你必须在源文件的开头写上 “#include“stdafx.h” 相关语句，而且之后引入 glew，glfw 包会有莫名其妙的错误。所以创建一个空项目。

![](161-Visual-Studio-2017-配置-OpenGL\20.png)

如果不是创建的空项目，会出现这种情况。

![](161-Visual-Studio-2017-配置-OpenGL\9.png)

### 五、创建 main. cpp 源文件

点击右侧 “解决方案资源管理器”，右键点击源文件，添加新项，创建. cpp 源文件（我起名叫 main.cpp）。

![](161-Visual-Studio-2017-配置-OpenGL\17.png)

![](161-Visual-Studio-2017-配置-OpenGL\11.png)

### 六、配置 OpenGL

1.右键点击项目，在弹出的选项中，单击 “属性”。

![](161-Visual-Studio-2017-配置-OpenGL\18.png)

![](161-Visual-Studio-2017-配置-OpenGL\19.png)

2.点击 “VC++ 目录”，第二步会有下拉列表，单击 “编辑”。

![](161-Visual-Studio-2017-配置-OpenGL\2.png)

![](161-Visual-Studio-2017-配置-OpenGL\3.png)

3.点击添加头文件。分别添加下载的 glew 和 glfw 文件夹下的 include 文件夹 (include 文件夹下是我们需要的头文件)，点击 “确定”。

![](161-Visual-Studio-2017-配置-OpenGL\4.png)

4.同理，加入库文件。（库文件和头文件是相辅相成的），对应的路径就是 glew 和 glfw 文件夹下的 lib 文件夹。

**注：**

1.当添加 glew 时，当选到 lib 文件夹后请继续选择，lib->Release->Win32, 请选择 Win32 后点击 “选择文件夹”（x64 会有莫名其妙的问题）

2.当添加 glfw 时，低版本请选择对应版本，2015 以上版本请选择 “lib-vc2015”。

![](161-Visual-Studio-2017-配置-OpenGL\5.png)

![](161-Visual-Studio-2017-配置-OpenGL\6.png)

最后，点击一下右下角的**应用**，再点击**确定**。

### 七、配置链接器

1.包含的库文件 VS 还认不出来，我们需要指定一下。配置链接器。

![](161-Visual-Studio-2017-配置-OpenGL\7.png)

2.点击 “编辑” 后输入如下:

```C++
opengl32.lib
glfw3.lib
glew32s.lib
```

**注：**

行与行之间请按回车。

opengl32.lib 是系统自带的。

glfw3.lib,glew32.lib,glew32s.lib 如果你足够细心，你会发现这些就是之前包含的 lib 文件夹下的文件名

不包括：

```C++
glew32.lib
```

![](161-Visual-Studio-2017-配置-OpenGL\8.png)

最后，点击一下右下角的**应用**，再点击**确定**。

### 八、初步运行

1.在之前的 main.cpp 中添加如下代码：（即初始化一个 OpenGL 窗口）

```C++
#include<iostream>
#define GLEW_STATIC
#include <GL/glew.h>
#include<GLFW\glfw3.h>
 
using namespace std;
 
int main(int argc, char** argv[])
{
	/*glewExperimental = GL_TRUE;
	if (glewInit()!=GLEW_OK)
	{
		cout << "failed to initalize GLEW" << endl;
		return -1;
	}*/
 
	glfwInit();//初始化
	glfwWindowHint(GLFW_CONTEXT_VERSION_MAJOR, 3);//配置GLFW
	glfwWindowHint(GLFW_CONTEXT_VERSION_MINOR, 3);//配置GLFW
	glfwWindowHint(GLFW_OPENGL_PROFILE, GLFW_OPENGL_CORE_PROFILE);//
	glfwWindowHint(GLFW_RESIZABLE, GL_FALSE);
 
	GLFWwindow* window = glfwCreateWindow(800, 600, "LearnOpenGL", nullptr, nullptr);
	if (window==nullptr)
	{
		cout << "Failed to create GLFW window" << endl;
		glfwTerminate();
		return -1;
	}
	glfwMakeContextCurrent(window);
	while (!glfwWindowShouldClose(window))
	{
		glfwPollEvents();
		glfwSwapBuffers(window);
	}
	glfwTerminate();
	return 0;
 
 
}
```

或者

```C++
#include <iostream>
//GLEW
#define GLEW_STATIC
#include <GL/glew.h>
//GLFW
#include <GLFW/glfw3.h>
const GLint WIDTH = 800, HEIGHT = 600;
int main()
{
	glfwInit();
	glfwWindowHint(GLFW_CONTEXT_VERSION_MAJOR, 3);
	glfwWindowHint(GLFW_CONTEXT_VERSION_MINOR, 3);
	glfwWindowHint(GLFW_OPENGL_PROFILE, GLFW_OPENGL_CORE_PROFILE);
	glfwWindowHint(GLFW_OPENGL_FORWARD_COMPAT, GL_TRUE); // must for Mac
	glfwWindowHint(GLFW_RESIZABLE, GL_FALSE);
	GLFWwindow *window = glfwCreateWindow(WIDTH, HEIGHT, "Learn OpenGL", nullptr,
		nullptr);
	// next two lines are for mac retina display
	int screenWidth, screenHeight;
	glfwGetFramebufferSize(window, &screenWidth, &screenHeight);
	if (nullptr == window)
	{
		std::cout << "Failed to create GLFW window" << std::endl;
		glfwTerminate();
		return -1;
	}
	glfwMakeContextCurrent(window);
	glewExperimental = GL_TRUE;
	if (GLEW_OK != glewInit())
	{
		std::cout << "Failed to initialise GLEW" << std::endl;
		return -1;
	}
	glViewport(0, 0, screenWidth, screenHeight);
	while (!glfwWindowShouldClose(window))
	{
		glfwPollEvents();
		glClearColor(0.2f, 0.3f, 0.3f, 1.0f);
		glClear(GL_COLOR_BUFFER_BIT);
		glfwSwapBuffers(window);
	}
	glfwTerminate();
	return 0;
}
```

2.点击 “开始执行不调试”。

![](161-Visual-Studio-2017-配置-OpenGL\12.png)

### 九、完善

当我们关掉程序回到 “错误列表” 中会发现

![](161-Visual-Studio-2017-配置-OpenGL\13.png)

不用担心，解决方法如下：

1.还记得之前的链接器的那个页面吗？调出来

![](161-Visual-Studio-2017-配置-OpenGL\14.png)

2.点击 “编辑”，输入如下：

```C++
MSVCRT.lib
```

最后，点击一下右下角的**应用**，再点击**确定**。

注：如果往后还有库冲突，解决方法同理。

### 十、致谢

[OpenGL+VS2017 环境配置 (亲测好使)&lt; 附带必要知识点 & gt;](https://blog.csdn.net/AvatarForTest/article/details/79199807)

[Visual Studio 2017 配置 OpenGL](https://blog.csdn.net/qiangbizhi3622/article/details/79467994)

