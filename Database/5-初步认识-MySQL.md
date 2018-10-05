---
title: 初步认识 MySQL
tag: [MySQL]
category: 数据库
---

>这学期刚开始学《数据库原理与应用》这门课。老师布置了课后作业，安装一个数据库软件，并且进行创建数据库、创建数据表、插入数据、查询数据等操作。于是，我选择了 MySQL。
>
>安装过程见[这篇博客](https://wonz5130.github.io/2018/08/13/4-MySQL%E5%AE%89%E8%A3%85/)。 

<!--more-->

### 首先，进入数据库

![](5-初步认识-MySQL\1.png)

### 创建数据库

进行后面操作的时候，会出现这样的错误：Error Code: 1007.Can't create database 'b16112011'; database exists。因此，在创建成功数据库之后，要把第一行创建数据库注释掉。

![](5-初步认识-MySQL\2.png)

### 创建数据表

注意用的是键盘左上角的那个反引号`，不是单引号’。还有，数据类型要写上去。VARCHAR 是字符串类型，INT 是整型。

![](5-初步认识-MySQL\3.png)

### 插入数据

**注意：**插入的元素都要加‘’。前面加个 VALUES。

![](5-初步认识-MySQL\4.png)

### 查询数据

![](5-初步认识-MySQL\5.png)

### 代码

```mysql
CREATE DATABASE TEST;
SHOW DATABASES;  # 展示当前已有的数据库，windows自带三个数据库
USE TEST;  # 使用数据库
CREATE TABLE `Student`(
`NAME` VARCHAR(10),
`XUEHAO` INT,
`SEX` VARCHAR(3),
`AGE` INT,
`HOME` VARCHAR(20)
);
INSERT Student VALUES('Wonz','2011','man','21','Jiangsu');
SELECT * FROM Student
```

<u>本文于 2018 年 3 月 11 日 首发于 [CSDN](https://blog.csdn.net/Wonz5130/article/details/79519154)。</u>