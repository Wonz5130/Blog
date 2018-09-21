---
title: A1005：Spell It Right（20'）
tag: [入门模拟,字符串处理]
category: PAT
---

>[A1005：Spell It Right（20'）](https://pintia.cn/problem-sets/994805342720868352/problems/994805519074574336)

<!--more-->

### 题目

![](PAT\A1005.png)

### 思路

将输出单独存进一个二维字符串数组中，遍历求各位上数的和，再用辗转相除法求出和的每一位数字，存进数组，最后逆序输出。 

### 注意

特判 sum=0。 

### 代码

```C++
#include<cstdio>
#include<cstring>
int main(){
	char a[10][10] = {"zero","one","two","three","four","five","six","seven","eight","nine"};
	char n[10010];
	scanf("%s",n);
	int len = strlen(n);
	int sum = 0;
	for(int i = 0; i < len ; ++i){
		sum += n[i] - '0';  //字符化为整数
	}
	int x[10010] = {0};  //要加{}
	int i = 0;
	//特判
	if(sum == 0){
		printf("zero");
		return 0;
	}
	do{
		x[i++] = sum % 10;
		sum /= 10;
	}while(sum != 0);  //用do while
	for(i-- ; i >= 0 ; --i){
		printf("%s",a[x[i]]);
		if(i != 0) printf(" ");
	}
	return 0;
}
```

<u>本文于 2018 年 8 月 3 日首发于 [CSDN](https://blog.csdn.net/wonz5130/article/details/81393714)。</u>	