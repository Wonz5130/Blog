---
title: A1036：Boys vs Girls（25'）
tag: [入门模拟,查找元素]
category: PAT
---

>[A1036：Boys vs Girls（25'）](https://pintia.cn/problem-sets/994805342720868352/problems/994805453203030016)

<!--more-->

### 题目

![](PAT\A1036.png)

### 思路

每次输入，单独更新女生的最高分和男生的最低分，记录数组下标 i。输出时女生和男生都要判断是否为 Absent，所以 girl 和 boy 初值可以设为 - 1，便于判断。 

### 注意

gender 输入时要用 %c，如果设成了 %s，则要用 strcmp 进行比较。字符串输入不用 &。 

### 代码

```C++
#include<cstdio>
struct student{
	char name[20];  //数组大小要大于10
	char gender;
	char ID[20];
	int grade;
}student[100010];
 
int main(){
	int n,girl = -1,boy = -1;
	int fmax=0,mmin=100;
	scanf("%d",&n);
	for(int i = 0;i < n;i ++){
		scanf("%s %c %s %d",student[i].name,&student[i].gender,student[i].ID,&student[i].grade);  //字符串输入不用&
		if(student[i].gender == 'F'){  //字符直接用=比较,如果是字符串要用strcmp
			if(student[i].grade >= fmax){
				fmax = student[i].grade;
				girl = i;
			}
		}
		else{
			if(student[i].grade <= mmin){
				mmin = student[i].grade;
				boy = i;
			}
		}
	}
	if(girl == -1){
		printf("Absent\n");  //判断如果没有的话
	}
	else printf("%s %s\n",student[girl].name,student[girl].ID);
	if(boy == -1){
		printf("Absent\n");
	}
	else printf("%s %s\n",student[boy].name,student[boy].ID);
	if(girl == -1 || boy == -1){
		printf("NA\n");
	}
	else printf("%d",fmax-mmin);
	return 0;
}
```

<u>本文于 2018 年 7 月 21 日首发于 [CSDN](https://blog.csdn.net/wonz5130/article/details/81149414)。</u>	