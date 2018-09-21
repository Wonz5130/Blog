---
title: A1006：Sign In and Sign Out（25'）
tag: [入门模拟,查找元素]
category: PAT
---

>[A1006：Sign In and Sign Out（25'）](https://pintia.cn/problem-sets/994805342720868352/problems/994805516654460928)

<!--more-->

### 题目

![](PAT\A1006.png)

### 思路

用结构体存储 person。输入的时间不用按小时、分钟、秒来比较，可以直接组合成一个 6 位整数，1-2 位为小时，3-4 位为分钟，5-6 位为秒，直接比较整数大小即可得到时间的先后。 然后每次输入，同时更新最早和最晚时间，并记录下标。最后直接根据下标输出号码。 

### 代码

```C++
#include<cstdio>
struct person{
	char number[20];  //学号,数组位数要超过15位,至少16位
}person[10010];
 
int main(){
	int n,In[10010],Out[10010];  //记录登入与登出
	int inhour,inminute,insecond;
	int outhour,outminute,outsecond;
	int earliest = 235959;  //开门时间初值设为边界max值
	int latest = 0;  //关门时间初值设为边界min值
	int early,late;  //记录下标
	scanf("%d",&n);
	for(int i = 0;i < n;i ++){
		scanf("%s %d:%d:%d %d:%d:%d",&person[i].number,&inhour,&inminute,&insecond,&outhour,&outminute,&outsecond);
		In[i] = inhour*10000+inminute*100+insecond;
		Out[i] = outhour*10000+outminute*100+outsecond;
		if(In[i] < earliest){
			earliest = In[i];
			early = i;
		}
		if(Out[i] > latest){
			latest = Out[i];
			late = i;
		}
	}
	printf("%s %s",person[early].number,person[late].number);
	return 0;
}
```

<u>本文于 2018 年 7 月 20 日首发于 [CSDN](https://blog.csdn.net/Wonz5130/article/details/81139774)。</u>	