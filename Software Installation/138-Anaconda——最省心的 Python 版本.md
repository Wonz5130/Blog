---
title: Anaconda——最省心的 Python 版本
tag: [经验,Python]
category: 软件安装
---
>大二第一学期的时候，开始自学 Python，早就听说这门语言的强大。跟着教程，当时编译器是用的 Pycharm。在大二的寒假，意外知道了 anaconda 这个软件，然后试着安装了一下，虽然中间出过一些问题，不过安装成功之后，使用确实很省心，很多库都不需要自己手动装了。但是最近，更新的时候，出了点问题，又卸载了重装一下，顺便记录一下。

<!--more-->

# 一、卸载 Python
当时在有 Python 的环境下安装 anaconda 的，但是网上说会出问题，所以建议卸载掉之前的 Python 环境，再装 anaconda，而且 anaconda 自带 Python环境。
我试了两种办法卸载 Python。
## 方法1：重新安装 Python 的时候进行卸载
试试照着原来的安装 Python 的版本和步骤，重新安装，打开界面，会出现三个选项：Modify、Repair、Uninstall。然后选择 Uninstall 卸载原来的环境。但是我没成功，所以选择了方法2。
![](138-Anaconda——最省心的 Python 版本\0.png)

## 方法2：手动删除
找到原来的 Python 安装路径，删除下面的所有文件
我的路径是：C:\Users\Wonz\AppData\Local\Programs\Python
然后，我就把 Python 下面的所有文件剪切到 F 盘当备份了，防止下面的安装步骤出问题。
![](138-Anaconda——最省心的 Python 版本\1.png)

卸载后，不妨打开 cmd 命令行，输入：python，回车。如果出现：'Python'不是内部或外部命令，也不是可运行的程序。
![](138-Anaconda——最省心的 Python 版本\2.png)
恭喜你，终于卸载成功了！

# 二、安装 anaconda
anaconda 的安装推荐用国内清华大学开源软件镜像站进行下载，因为官网是从国外下载，速度慢而且经常下载失败，[清华镜像站地址在这里](https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/)。

安装的步骤比较简单，选默认路径 C 盘，一路 next 就行，不过有几个注意的地方。
* 路径不能加任何空格，网上有人反应加了空格会出现很多问题，而且要是英文路径，就是说你要把用户这个文件夹改为英文，否则后面也会出现问题。
我的路径就是：C:\Users\Wonz\Anaconda3
![](138-Anaconda——最省心的 Python 版本\3.png)
Wonz 对应到的就是你的用户名文件夹，要改成英文。

![](138-Anaconda——最省心的 Python 版本\4.png)
* 第一个勾是说：是否把 Anaconda 加入环境变量，这涉及到能否直接在 cmd 中使用 conda、jupyter、ipython 等命令，推荐打勾，如果不打勾话问题也不大，可以在之后使用 Anaconda 提供的命令行工具进行操作。
* 第二个勾是说：是否设置 Anaconda 所带的 Python 3.6 为系统默认的 Python 版本，这个自己看着办，问题不大。

因为我把之前的 Python 卸载了，所以我两个都打勾了。

接近快安装好的时候，会跳出一个类似于 cmd 命令框的东西，那个是 Anaconda Prompt，你后面安装库都要用它的。
注意，这里就让它自动跳出来好了，不用管它，它会自动关掉的。我记得在哪里看到，有人动了一下这个框，后面出了问题，所以最好别碰它。

一切安装好后，打开 cmd 测试一下安装结果。
分别输入：python、ipython、conda、jupyter notebook。注意前两个每测试一个都要再输 exit() 退出再测试下一个。
![](138-Anaconda——最省心的 Python 版本\5.png)

# 三、修改 anaconda 包管理镜像为国内源
在 cmd 中分别运行下面两个命令。
```bash
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --set show_channel_urls yes
```
然后，检查一下 .condarc 文件是否是下面这样的内容(推荐使用 everything 进行搜索这个文件，注意带.的)，或者你可以直接修改该文件的内容设置镜像。
```
channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
  - defaults
show_channel_urls: true
ssl_verify: true

```

# 四、增加 Python2.7 环境
创建一个新环境 Python2.7，并且安装 pandas 库
```bash
conda create -n py27 python=2.7 pandas
```
终端会询问 y/n，输入 y 回车。

在 Windows 系统中，使用 activate env_name 和 deactivate 来进入和退出某个环境。Linux 和 Mac 要在前面加一个 source。

进入名为 env_name 的环境：
```bash
activate py27
```

为新环境下安装巨难装的 lxml：
```bash
conda install -n py27 lxml
```

为新环境装上 Anaconda 的科学计算包，会装很多很多包，慎用：
```bash
conda install -n py27 anaconda
```

查看已有环境：
```bash
conda info -e
```
或者：
```bash
conda env list
```

退出当前环境：
```bash
deactivate
```

删除名为 env_name 的环境：
```bash
conda env remove -n env_name
```

当分享代码的时候，同时也需要将运行环境分享给大家，执行如下命令可以将当前环境下的 package 信息存入名为 environment 的 YAML 文件中。
```bash
conda env export > environment.yaml
```

同样，当执行他人的代码时，也需要配置相应的环境。这时你可以用对方分享的 YAML 文件来创建一摸一样的运行环境。
```bash
conda env create -f environment.yaml
```

# 五、一些 conda 命令
* 查看所有的 packages：
```bash
conda list
```

* 安装包，conda 比 pip 好用！一般都是 conda 安装包，不行转 pip ，pip 不行转 whl 文件手动安装。
```bash
conda install package_name
```

* 可以同时安装多个包，比如 numpy 、scipy 和 pandas，则执行如下命令：
```bash
conda install numpy scipy pandas
```

* 指定安装的版本，比如安装 1.1 版本的 numpy ：
```bash
conda install numpy=1.10
```

* 移除一个 package：
```bash
conda remove package_name
```

* 升级 package 版本：
```bash
conda update package_name
```

* 你也可以升级 conda、anaconda、python，要保持 conda 为最新：
```bash
conda update conda
```

* 如果你记不清 package 的具体名称，也可以进行模糊查询：
```bash
conda  search search_term
```

* 最后来个大招，一键更新！
```bash
conda upgrade --all
```
在终端询问是否安装如下升级版本时，输入 y。
有的情况下，你可能会遇到找不到 conda 命令的错误提示，这很可能是环境路径设置的问题，需要添加 conda 环境变量：export PATH=xxx/anaconda/bin:$PATH, 其中 xxx 替换成 anaconda 的安装路径。

# 六、使用技巧
## Spyder 等软件更新
推荐直接打开 Anaconda Navigator，点击 Spyder 右上角的设置按钮，有 update 选项。

## Pycharm 应用 anaconda 下的 python 环境
首先打开 Pycharm，然后在左上角文件里面，打开 setting，找到 “Project:python程序” 下面的 “Project Interpreter”，然后在右侧下拉环境里面，找到 anaconda 下的 python 环境，点击右下角的 Apply 即可。
![](138-Anaconda——最省心的 Python 版本\6.png)

# 七、总结
经网上大佬们推荐，单文件用 Jupyter Notebook，项目组织开 Pycharm，还有一个 Spyder 也用得顺手。

# 八、致谢
[清华镜像站](https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/)
[最省心的 Python 版本和第三方库管理——初探 Anaconda](https://zhuanlan.zhihu.com/p/25198543)
[致 Python 初学者：Anaconda 入门使用指南](http://python.jobbole.com/87522/?repeat=w3tc)
[如何在已安装 Python 条件下，安装 Anaconda,，并将原有 Python 添加到 Anaconda 中](https://www.cnblogs.com/yamin/p/7111397.html)
[conda 与 Anaconda](https://blog.csdn.net/pfm685757/article/details/74995517)
[Anaconda 安装及使用教程](http://www.360doc.com/content/16/1029/18/25664332_602357786.shtml)
[Anaconda 的安装与测试实例](https://blog.csdn.net/wumenglu1018/article/details/53405991)
[windows 上安装 Anaconda 和 python 的教程详解](https://www.jb51.net/article/109726.htm)
[Anaconda 使用总结](http://python.jobbole.com/86236/)
[Windows 下 Anaconda 的安装和简单使用](https://www.jianshu.com/p/cd35110f1ed0)