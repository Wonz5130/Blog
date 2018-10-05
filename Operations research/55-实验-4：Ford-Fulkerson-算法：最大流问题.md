---
title: 实验 4：Ford-Fulkerson 算法：最大流问题
tag: [实验,NJUPT]
category: 运筹学
---

>**题目：**求发点 1 到收点 7 的最大流量，括号中数据为给定初始可行流。 
>
>![](55-实验-4：Ford-Fulkerson-算法：最大流问题\1.png)

<!--more-->

### 解：

##### 一、计算过程：

###### 1. Excel

先写出容量表，如下图所示。

![](55-实验-4：Ford-Fulkerson-算法：最大流问题\2.png)

然后，在如下图所示位置输入公式：=SUM（D30:J30），下拉复制公式，另一行的流出量也是如此。 

![](55-实验-4：Ford-Fulkerson-算法：最大流问题\3.png)

建立约束条件，流量不能超过容量，且要是大于等于 0 的整数。两个位置流出量值要一致。 

![](55-实验-4：Ford-Fulkerson-算法：最大流问题\4.png)

得出结果： 

![](55-实验-4：Ford-Fulkerson-算法：最大流问题\5.png)

###### 2. Lingo

```lingo
MODEL:
sets:
nodes/s,1,2,3,4,5,t/;
arcs(nodes,nodes)/
s,1 s,2 2,1 2,5 2,3 1,4 1,3 3,4 3,t 4,t 5,3 5,t/:c,f;
endsets
data:
c=8 13 5 8 3 7 4 4 10 7 3 6;
enddata
max = flow;
n=@size(nodes);!顶点的个数;
@for(nodes(i)|i#ne#1#and#i#ne#n:
@sum(arcs(j,i):f(j,i))=@sum(arcs(i,j):f(i,j)));
!@for(nodes(i)|i#eq#s;
@sum(arcs(i,j)|i#eq#1:f(i,j))=flow;
!@for(nodes(i)|i#eq#t;
@sum(arcs(i,j)|j#eq#n:f(i,j))=flow;
@for(arcs:@bnd(0,f,c));
END
```

![](55-实验-4：Ford-Fulkerson-算法：最大流问题\6.png)

###### 3. Matlab

```matlab
clc,clear
u(1,2)=8;u(1,3)=13;u(2,4)=4;u(2,5)=7;u(3,2)=5;u(3,4)=3;u(3,6)=8;u(4,5)=4;u(4,7)=10;u(5,7)=7;u(6,4)=3;u(6,7)=6;
f(1,2)=6;f(1,3)=10;f(2,4)=3;f(2,5)=6;f(3,2)=3;f(3,4)=0;f(3,6)=7;f(4,5)=1;f(4,7)=3;f(5,7)=7;f(6,4)=1;f(6,7)=6;
n=length(u);
list=[];
maxf(n)=1;
while maxf(n)>0;
    maxf=zeros(1,n);
    pred=zeros(1,n);
    list=1;
    record=list;
    maxf(1)=inf;
    %list是未检查邻接点的标号点，record是已标号点
    while(~isempty(list))&(maxf(n)==0)
        flag=list(1);
        list(1)=[];
        label1=find(u(flag,:)-f(flag,:));
        label1=setdiff(label1,record);
        list=union(list,label1);
        pred(label1)=flag;
        maxf(label1)=min(maxf(flag),u(flag,label1)...
            -f(flag,label1));
        record=union(record,label1);
        label2=find(f(:,flag));
        label2=label2';
        label2=setdiff(label2,record);
        list=union(list,label2);
        pred(label2)=-flag;
        maxf(label2)=min(maxf(flag),f(label2,flag));
        record=union(record,label2);
    end
    if maxf(n)>0
        v2=n;
        v1=pred(v2);
        while v2~=1
            if v1>0
                f(v1,v2)=f(v1,v2)+maxf(n);
            else
                v1=abs(v1);
                f(v2,v1)=f(v2,v1)-maxf(n);
            end
            v2=v1;
            v1=pred(v2);
        end
    end
end
f
f(1,2)+f(1,3)
```

u 表示路线上的容量。

f 表示路线上的流量。

![](55-实验-4：Ford-Fulkerson-算法：最大流问题\7.png)

<u>本文于 2018 年 6 月 24 日首发于 [CSDN](https://blog.csdn.net/Wonz5130/article/details/80683979)。</u>