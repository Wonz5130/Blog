---
title: A1073：Scientific Notation（20'）
tag: [入门模拟,字符串处理]
category: PAT
---

>[A1073：Scientific Notation（20'）](https://pintia.cn/problem-sets/994805342720868352/problems/994805395707510784)

<!--more-->

### 题目

![](PAT\A1073.png)

### 思路

**同乙级 1024。**先找到 E 的位置，用 flag_E 标记一下。然后计算 flag_E+2 位置一直到末尾的数，计算指数大小 exp。然后根据 E 后面的 “+-” 号分类讨论。

“-”：先判断字符串第一项是否为 “-”，“-” 输出，“+” 不输出。然后先输出 “0.”。再输出格式为 0.000XXX。小数点后连续 0 的个数为 exp-1，然后 XXX 就是原字符串 str[3] 一直到 str[flag_E-1] 的数字。

“+”：分三种情况讨论：

1.exp 小于小数点后的数字个数。照样先判断是否输出 “-”，然后从 str[3] 一直输出到 str[exp+2]，再输出一个 “.”，最后输出剩余数字。

2.exp 正好等于小数点后数字个数。那么就不用输出 “.”。

3.exp 大于小数点后的数字个数。照样先判断是否输出 “-”，然后从 str[3] 一直输出到 str[flag_E-1]，这里 exp 要递减。最后，输出 exp 更新后的个数的 “0”。

### 代码

```C++
#include<cstdio>
#include<cstring>
int main(){
	char str[10010];
	scanf("%s",str);
	int n = strlen(str);
	int flag_E = -1;
	for(int i = 0;i < n; i ++){
		if(str[i] == 'E'){
			flag_E = i;
			break;
		}
	}
	int exp = 0;
	//计算指数
	for(int i = flag_E + 2;i < n;i ++){
		exp = exp*10 + (str[i] - '0');
	}
	//特判
	if(exp == 0){
		for(int i = 0;i < n;i ++){
			printf("%c",str[i]);
		}
	}
	//负号
	if(str[flag_E + 1] == '-'){
		if(str[0] == '-'){  //判断首位是否为'-','-'要输出
			printf("%c",str[0]);
		}
		printf("0.");
		for(int i = 0;i < exp-1;i ++){  //小数点后连续0的个数
			printf("0");
		}
		printf("%c",str[1]);
		for(int i = 3;i < flag_E;i ++){
			printf("%c",str[i]);
		}
	}
	//正号
	else{
		if(exp < flag_E-3){
			if(str[0] == '-'){
				printf("-");
				printf("%c",str[1]);
			}
			else{
				printf("%c",str[1]);
			}
			for(int i = 3;i <= exp+2;i ++){
				printf("%c",str[i]);
			}
			printf(".");  //输出小数点
			for(int i = exp+3;i < flag_E;i ++){
				printf("%c",str[i]);
			}
		}
		else if(exp == flag_E-3){  //不用输出小数点
			if(str[0] == '-'){
				printf("-");
				printf("%c",str[1]);
			}
			else{
				printf("%c",str[1]);
			}
			for(int i = 3;i <= exp+2;i ++){
				printf("%c",str[i]);
			}
		}
		else{
			if(str[0] == '-'){
				printf("%c%c",str[0],str[1]);
			}
			else{
				printf("%c",str[1]);
			}
			for(int i = 3;i < flag_E;i ++){
			    printf("%c",str[i]);
			    exp --;  //exp要递减,进行更新
		    }
		    for(int i = 0;i < exp;i ++){  //输出0
			    printf("0");
		    }
		}
	}
	return 0;
}
```

<u>本文于 2018 年 7 月 26 日首发于 [CSDN](https://blog.csdn.net/Wonz5130/article/details/81228587)。</u>	