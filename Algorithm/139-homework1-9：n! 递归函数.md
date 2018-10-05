---
title: homework1-9：n! 递归函数
tag: [作业]
category: 算法
---
>从今天开始，系统地自学算法，用的是学校教材：陈慧南老师的《算法设计与分析——C++ 语言描述》(第 3 版)。

<!--more-->

# 题目

设计一个递归函数计算 n!。

# 代码

```C++
//n! 递归函数
#include<iostream>
using namespace std;

int n_factorial(int n){
	if(n != 1){
		//--n;
		return(n * n_factorial(n-1));  //不是递减，而是参数为 n-1
	}
	else return 1;
}

int main(){
	int n;
	cin>>n;
	int result = n_factorial(n);
	cout<<result<<endl;
	return 0;
}
```

