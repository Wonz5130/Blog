---
title: A1058：A+B in Hogwarts（20'）
tag: [入门模拟,进制转换]
category: PAT
---

>[A1058：A+B in Hogwarts（20'）](https://pintia.cn/problem-sets/994805342720868352/problems/994805416519647232)

<!--more-->

### 题目

![](PAT\A1058.png)

### 思路

和 B1037 类似，不过这题是计算和，所以要考虑溢出，就改用 long long 型变量。 

### 代码

```C++
#include<cstdio>
int main(){
	long long G1,S1,K1,G2,S2,K2;  //改用long long型,防止溢出
	scanf("%lld.%lld.%lld %lld.%lld.%lld",&G1,&S1,&K1,&G2,&S2,&K2);
	long long P = G1*17*29+S1*29+K1;  //统一到K位
	long long A = G2*17*29+S2*29+K2;
	A = A+P;
	long long G3,S3,K3;
	G3 = A/(17*29);  //是除不是取余
	S3 = (A-G3*17*29)/29;  //这里也是除
	//S3 = A%(17*29)/29;
	//K3 = A-G3*17*29-S3*29;
	K3 = A%29;  //这里是取余
	printf("%lld.%lld.%lld",G3,S3,K3);
	return 0;
}
```

<u>本文于 2018 年 7 月 23 日首发于 [CSDN](https://blog.csdn.net/wonz5130/article/details/81175426)。</u>	