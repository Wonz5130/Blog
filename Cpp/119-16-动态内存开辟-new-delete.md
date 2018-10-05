---
title: 16. 动态内存开辟 new_delete
tag: [new,动态内存分配,delete]
category: C++
---

>**动态分配数组的 3 个特点：**
>
>1.按运行时所需分配堆空间。
>
>2.释放数组要用 delete []pt;
>
>3.没有初始化语句，不能对数组初始化。构造函数有默认值才行。

<!--more-->

**malloc：**

1.自己计算大小。

2.做强制转换。

3.进行开辟成功与否的判断。

4.用 free 释放

**new：**

1.不需要进行强制转换。

2.不需要判断开辟成功与否。

3.new 释放用 delete。

4.释放数组，前面要加 []。

```C++
#include<iostream>
using namespace std;
#define SIZE 10
 
void main(){
	int *p = (int*)malloc(sizeof(int) * SIZE);
	if(p == NULL)
		exit(1);
	for(int i  = 0;i < SIZE; ++i){
		p[i] = i+1;
	}
	free(p);
 
	int *q = new int[SIZE];
	for(int j = 0;j < SIZE; ++j){
		q[j] = j+1;
	}
	delete []q;
}
```

new 允许申请空间的时候初始化。申请数组空间时一定要写成：new int[10]； 

```C++
#include<iostream>
using namespace std;
#define SIZE 10
 
void main(){
	int *p = (int *)malloc(sizeof(int));
	*p = 10;
	free(p);
 
	int *q = new int(10);  //new允许申请空间的时候初始化
	delete q;
}
```

malloc 和 new 比较。 

```C++
#include<iostream>
using namespace std;
#define SIZE 10
 
class Test{
public:
	Test(int d = 0):data(d){
		cout<<"Create Test Object!"<<endl;
	}
	~Test(){
		cout<<"Free Test Object!"<<endl;
	}
public:
	void InitObject(int d = 0){
		data = d;
		cout<<"Init Object!"<<endl;
	}
	void Destroy(){
		cout<<"Destroy Object!"<<endl;
	}
private:
	int data;
};
 
void Use_Malloc_Free(){
	Test *pt = (Test *)malloc(sizeof(Test));  //只负责对空间申请
	pt->InitObject(10);
	pt->Destroy();  //释放前要摧毁对象,防止内存泄露
	free(pt);
}
 
void Use_New_Delete(){
	Test *pt = new Test(10);  //先申请空间,再初始化
	delete pt;  //先摧毁对象,再释放空间
}
 
void main(){
	Use_Malloc_Free();
	cout<<"------------------"<<endl;
	Use_New_Delete();
}
```

C++ 一定要记得释放。 

```C++
#include<iostream>
using namespace std;
#define SIZE 10
 
class Test{
public:
	Test(int d = 0):data(d){
		cout<<"Create Test Object!"<<endl;
	}
	~Test(){
		cout<<"Free Test Object!"<<endl;
	}
public:
	void InitObject(int d = 0){
		data = d;
		cout<<"Init Object!"<<endl;
	}
	void Destroy(){
		cout<<"Destroy Object!"<<endl;
	}
private:
	int data;
};
 
void main(){
	Test *pt = new Test(100);
	delete pt;
 
	Test *pa = new Test[10];
	delete []pa;  //一定要释放数组
}
```

<u>本文于 2018 年 7 月 29 日首发于 [CSDN](https://blog.csdn.net/wonz5130/article/details/81268661)。</u>	