---
title: A1027：Colors in Mars（20'）
tag: [入门模拟,进制转换]
category: PAT
---

>[A1027：Colors in Mars（20'）](https://pintia.cn/problem-sets/994805342720868352/problems/994805470349344768)

<!--more-->

### 题目

![](PAT\A1027.png)

### 思路

这是一道进制转换题，读懂题意就知道，只需把输入转化成 13 进制数就行。但要注意第一位没有数要输出 0，以及怎么输出 A,B,C 。

### 代码

（开始学 C++ 了，代码风格可能是 C 和 C++ 混搭，会慢慢调整的） 

```C++
#include<iostream>
using namespace std;
void output(int n){
	char n1;
	if(n/13 == 0){  //第一位没有数,输出0
		cout << 0;
		if(n%13>9){
			n1 = 'A'+n%13-10;  //如何输出A,B,C,只需令字符型A+1/2/3即可
			cout << n1;
		}
		else cout << n%13;
	}
	else{
		if(n/13>9){
			n1 = 'A'+n/13-10;
			cout << n1;
		}
		else cout << n/13;
		if(n%13>9){
			n1 = 'A'+n%13-10;
			cout << n1;
		}
		else cout << n%13;
	}
}
 
int main(){
	int r,g,b;
	cin >> r >> g >> b;
	cout << "#";
	//red
	output(r);
	//green
	output(g);
	//blue
	output(b);
	return 0;
}
```

<u>本文于 2018 年 7 月 23 日首发于 [CSDN](https://blog.csdn.net/wonz5130/article/details/81174862)。</u>	