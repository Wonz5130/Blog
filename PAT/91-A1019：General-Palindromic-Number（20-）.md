---
title: A1019：General Palindromic Number（20'）
tag: [入门模拟,进制转换]
category: PAT
---

>[A1019：General Palindromic Number（20'）](https://pintia.cn/problem-sets/994805342720868352/problems/994805487143337984)

<!--more-->

### 题目

![](PAT\A1019.png)

### 思路

利用进制转换模板先转化为 b 进制数。这里注意要用 do while 型，用 while 型可能会部分正确。同时，得到转换后的位数 i。然后，进行回文判断，只需比较 i/2 次。只要有一次循环不符合回文条件，就输出 “No”，直接退出循环。最后输出 b 进制数要逆序输出，不是回文的话如果正序输出就会出错。 

### 代码

```C++
#include<cstdio>
int main(){
	int n,b;
	int n1[100010];
	scanf("%d %d",&n,&b);
	int i = 0;
	//应该改用do while,防止第一次就是0
	/*
	while(n!=0){
		n1[i++] = n%b;
		n /= b;
	}
	*/
	do{
		n1[i++] = n%b;
		n /= b;
	}while(n!=0);
	for(int j = 0;j <= i/2;j ++){  //这里是j<=i/2
		if(n1[j] != n1[i-j-1]){
			printf("No\n");
			break;
		}
		if( j == i/2 && n1[j] == n1[i-j-1]){
			printf("Yes\n");
		}
	}
	for(int j = i-1;j >= 0;j --){
		printf("%d",n1[j]);
		if(j != 0) printf(" ");
	}
	printf("\n");
	return 0;
}
```

<u>本文于 2018 年 7 月 22 日首发于 [CSDN](https://blog.csdn.net/Wonz5130/article/details/81159864)。</u>	