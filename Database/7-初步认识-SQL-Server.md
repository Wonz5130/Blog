---
title: 初步认识 SQL Server
tag: [SQL]
category: 数据库
---

>继续数据库老师布置的课后作业：下载一个数据库软件并进行创建数据库、表、插入等操作。之前用 MySQL 操作了一遍，现在用 SQL Server 操作一遍。 

<!--more-->

### 主要感想

和 MySQL 有点不一样。注释语句是--。而 MySQL 是#。另外，INSERT 后面要加个 INTO。其他暂时没看出区别。 

### 代码

```sql
CREATE DATABASE TEST
CREATE TABLE Student(
Name CHAR(10),
XUEHAO INT,
SEX CHAR(3),
AGE INT,
HOME CHAR(20)
);
INSERT INTO Student VALUES('Wonz',2011,'man',21,'Jiangsu');
SELECT * FROM Student
```

<u>本文于 2018 年 3 月 13 日首发于 [CSDN](https://blog.csdn.net/Wonz5130/article/details/79538906)。</u>

