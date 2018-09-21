---
title: A1031：Hello World for U（20'）
tag: [入门模拟,图形输出]
category: PAT
---

>[A1031：Hello World for U（20'）](https://pintia.cn/problem-sets/994805342720868352/problems/994805462535356416)

<!--more-->

### 题目

![](PAT\A1031.png)

### 思路

列出前几种情况 (N=5,6,7,8,9,10)，找规律，发现 n1 始终是 (n+2)/3 向下取整 。n3 和 n1 相等，因为左右两边相等，利用公式 n2=n+2-n1-n3。 

### 注意

一开始我没想到找规律，而是根据题意，遍历找到 n1 的 max，但是失败了，看了晴神的思路，发现原来这么神奇。还是要学会打表找规律啊。 

### 代码

```C++
#include<cstdio>
#include<cstring>
int main(){
	char word[100010];
	scanf("%s",word);
	int n = strlen(word);
	int n1,n2,n3;
	//列出前几种情况,找到规律
	n1 = (n+2)/3;  //向下取整
	n3 = n1;  //左右两边相同
	n2 = n+2-n1-n3;
	for(int i = 0;i < n1-1;i ++){
		printf("%c",word[i]);
		for(int j = 0;j < n2-2;j ++){
			printf(" ");
		}
		printf("%c\n",word[n-1-i]);
	}
	//单独打印最下面一层
	for(int i = n1-1;i < n2+n1-1;i ++){
		printf("%c",word[i]);
	}
	printf("\n");
	return 0;
}
```

<u>本文于 2018 年 7 月 22 日首发于 [CSDN](https://blog.csdn.net/wonz5130/article/details/81158900)。</u>	