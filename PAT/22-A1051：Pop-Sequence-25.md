---
title: A1051：Pop Sequence(25')
tag: [数据结构,栈的应用]
category: PAT
---

>[A1051：Pop Sequence(25')](https://pintia.cn/problem-sets/994805342720868352/problems/994805427332562944)

<!--more-->

### 题目

![](22-A1051：Pop-Sequence-25\1.png)

### 思路

利用数据结构栈的知识解决。每次压栈，用 top 处的值和输入的出栈序列进行比较，是否相等。不等，继续压栈。相等，则出栈，并且让 current 后移一位，指向出栈序列的下一位下标。用 bool 型变量 flag 记录是否合法，最后再判断 flag 值是否为 true。

### 注意

1.每次进行输入出栈序列前，要让栈清空，C++ 没有 clear 功能，只能循环 pop。
2.如果栈超出了大小，则不合法，直接退出循环。
3.每次用到 top 和 pop，都要先判断栈是否为空，否则会出现 “答案错误” 或者 “段错误”。
4.最后判断 flag 是否为 true 前，还要再判断一次栈内元素是否全部出栈，否则会出现 “答案错误”。
5.开的数组要尽量大一点，否则会出现段错误。我试了一下，开 800 以下都是错的，开 1000 就没问题了。

### 代码

```C++
#include<cstdio>
#include<stack>
using namespace std;
stack<int> st;
#define N 1000  //数组小于1000会出现段错误
// bool flag = false;
int main(){
    int m,n,x;
    scanf("%d %d %d",&m,&n,&x);
    int a[N]={0};
    // int current = 1;  //放进循环里，因为每一次循环current都要从1开始
    for(int i = 1;i <= x;i++){
		while(!st.empty()) st.pop();  // C++中没有直接清楚stack的功能，所以要用pop
    	for(int j = 1;j <= n;j++){
    		scanf("%d",&a[j]);
    	}
		int current = 1;  //每一次循环开始，current置为1
		bool flag = true;  //每一次循环开始，flag置为true
    	for(int k = 1;k <= n;k++){  //这里是k和n进行比较
    		st.push(k);  //把k压入栈
    		if(st.size() > m){  //如果栈内元素数目大小大于最大容量m，则表示栈已满，不合法，退出循环
    			flag = false;
    			break;
    		}
        	while(!st.empty()&&st.top() == a[current]){  //做top前要先判断栈是否为空，这里要用循环，因为只要一直满足条件，就一直出栈
        		flag = true;
        		st.pop();  //出栈
        		current ++;  //current指向数组a下一个下标
        	}
        }
        if(st.empty() == true&&flag == true){  //判空，表示栈内元素已经全部出栈
        	printf("YES");
        	if(i!=x) printf("\n");
        }
        else{
			printf("NO");
        	if(i!=x) printf("\n");
		}
    }
    return 0;
}
```

<u>本文于 2018 年 4 月 11 日首发于 [CSDN](https://blog.csdn.net/Wonz5130/article/details/79894496)。</u>