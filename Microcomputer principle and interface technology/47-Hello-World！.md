---
title: Hello World！
tag: [汇编]
category: 微型计算机原理与接口技术
---

>接触汇编语言的第一个程序：Hello Wold！ 

<!--more-->

### 程序

```assembly
;完整段的Hello World程序
DATA  SEGMENT
     STRING  DB  'Hello World!',13,10,'$'
DATA  ENDS
 
CODE  SEGMENT
     ASSUME    CS:CODE,DS:DATA
START:
     MOV  AX,DATA
     MOV  DS,AX
     LEA  DX,STRING
     MOV  AH,9
     INT  21H
   
     MOV  AH,4CH
     INT  21H
CODE  ENDS
    END   START
```

<u>本文于 2018 年 6 月 15 日首发于 [CSDN](https://blog.csdn.net/Wonz5130/article/details/80705385)。</u>

