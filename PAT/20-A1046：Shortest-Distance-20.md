---
title: A1046：Shortest Distance(20')
tag: [入门模拟,简单模拟]
category: PAT
---

>[A1046：Shortest Distance(20')](https://pintia.cn/problem-sets/994805342720868352/problems/994805435700199424)

<!--more-->

### 题目

![](20-A1046：Shortest-Distance-20\1.png)

### 思路

一开始输入 N 结点时，把距离存进数组中，这样后面输出就不用循环遍历了，否则会超时。另外，输入时要用 1~n+1。

### 代码

```C++
#include<cstdio>
int main(){
    int n;
    scanf("%d",&n);
    int a[n+1],sum=0;
    int dis[n+1]={0};
    for(int i=1;i<=n;i++){  //用1~n+1
        scanf("%d",&a[i]);
        sum+=a[i];
        dis[i]=sum;  //先存下来，不然会运行超时
    }
    int m;
    scanf("%d\n",&m);
    int left,right;
    int add[m][2]={0};
    for(int i=0;i<m;i++){
        scanf("%d%d",&left,&right);
        if(left<right){
            add[i][0]=dis[right-1]-dis[left-1];  //最短路径就是dis相减，不过要注意下标要-1
            add[i][1]=sum-add[i][0];  //另一个方向的dis就是总和-上面的距离
            if(add[i][0]<add[i][1]) printf("%d\n",add[i][0]);
            else printf("%d\n",add[i][1]);
        }
        else{
            add[i][0]=dis[left-1]-dis[right-1];
            add[i][1]=sum-add[i][0];
            if(add[i][0]<add[i][1]) printf("%d\n",add[i][0]);
            else printf("%d\n",add[i][1]);
        }
    }
    return 0;
}
```

### 二刷代码

```C++
#include<cstdio>
#include<algorithm>
using namespace std;
int main(){
    int n,sum = 0;
    scanf("%d",&n);
    int a[100010] = {0};  //数组范围尽量设大一点,否则测试3过不去,段错误
    int dis[100010] = {0};
    for(int i = 1;i <= n;i ++){
        scanf("%d",&a[i]);
        sum += a[i];
        dis[i] = sum;
    }
    int m,left,right,road;
    scanf("%d",&m);
    for(int i = 0;i < m;i ++){
        road = 0;
        scanf("%d%d",&left,&right);
        if(left > right) swap(left,right);  //保证left < right
        road = dis[right-1]-dis[left-1];
        if(road <= sum-road) printf("%d\n",road);
        else printf("%d\n",sum-road);
    }
    return 0;
}
```

<u>本文于 2018 年 4 月 8 日首发于 [CSDN](https://blog.csdn.net/Wonz5130/article/details/79859772)。</u>

