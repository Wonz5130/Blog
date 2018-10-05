---
title: 调用 DOS 的 9 号功能，在屏幕上输出：I AM A STUDENT！
tag: [汇编]
category: 微型计算机原理与接口技术
---

>**题目：**在屏幕上输出：I AM A STUDENT！ 

<!--more-->

### 分析

将'I AM A STUDENT！'定义在数据段，并在'!'后加一个字符'$'，利用 9 号 DOS 功能调用，即可完成显示。 

### 程序

```assembly
.486
DATA	SEGMENT USE16            ;定义数据段
MESG    DB	'I AM A STUDENT!','$'
DATA    ENDS
CODE    SEGMENT USE16            ;定义代码段
		ASSUME  CS:CODE,DS:DATA
 
BEG:
	MOV	AX,DATA
	MOV	DS,AX
 
LAST:
	MOV	AH,9
	MOV	DX,OFFSET MESG           ;取MESG的偏移地址
	INT	21H
	MOV	AH,4CH           
	INT	21H                      ;返回DOS
 
CODE	ENDS
	END	BEG
```

<u>本文于 2018 年 6 月 15 日首发于 [CSDN](https://blog.csdn.net/Wonz5130/article/details/80706333)。</u>

