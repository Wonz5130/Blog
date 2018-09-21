---
title: A1011：World Cup Betting（20'）
tag: [入门模拟,查找元素]
category: PAT
---

>[A1011：World Cup Betting（20'）](https://pintia.cn/problem-sets/994805342720868352/problems/994805504927186944)

<!--more-->

### 题目

![](PAT\A1011.png)

### 思路

每次输入一组数据，就比较得出 max，然后根据最大值输出对应的 WTL。sum 根据公式计算值。最后输出要按照四舍五入输出，Devc 中输出结果不是四舍五入，但是 PAT 却能 AC。  

### 代码

```C++
#include<cstdio>
int main(){
	double x,y,z,sum=1.0;
	for(int i = 0;i < 3;i ++){
		scanf("%lf%lf%lf",&x,&y,&z);
		double max = x;
		if(max < y) max = y;
		if(max < z) max = z;
		if(max == x) printf("W ");
		else if(max == y) printf("T ");
		else if(max == z) printf("L ");
		sum *= max;
	}
	sum *= 0.65;
	sum --;
	sum *= 2;
	/*
	sum *= 100;
	int sum1 = (int)sum+0.5;
	sum = sum1/100.0;
	*/
	printf("%.2f",sum);
	return 0;
}
```

<u>本文于 2018 年 7 月 18 日首发于 [CSDN](https://blog.csdn.net/wonz5130/article/details/81105662)。</u>	