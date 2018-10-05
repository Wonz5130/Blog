---
title: Prim 算法
date: 2018-09-01 10:48:43
tags: [图论,最小代价生成树]
categories: 数据结构
---

>普里姆（Prim）算法

<!--more-->

### 代码

```C++
#include <iostream>
#include <string.h>
 
using namespace std;
const int MAXN = 2010;
const int INF = 1 << 30;
int map[MAXN][MAXN];
int N, M;
int lowcost[MAXN];
 
void init()
{
  for(size_t i = 0; i <= N; ++i)
    for(size_t j = 0; j <= N; ++j)
      map[i][j] = INF;
}
 
int prim()
{
  for(size_t i = 1; i <= N; ++i)
    lowcost[i] = map[1][i];
  int min;
  bool visited[N + 1];// index begin from 1 not 0
  int ans = -1;
  memset(visited, false, sizeof(visited));
  lowcost[1] = 0;
  visited[1] = true;
  for(size_t i = 1; i < N; ++i)//loop N - 1 times
  {
    min = INF;
    int k;
    for(size_t j = 1; j <= N; ++j)// find the minimun edge between two edge set
    {
      if(!visited[j] && min > lowcost[j])
      {
        min = lowcost[j];
        k = j;
      }
    }
    visited[k] = true;
    ans = ans > min ? ans : min; 
    for(size_t j = 1; j <= N; ++j)// update the array of lowcost 
    {
      if(!visited[j] && lowcost[j] > map[k][j])
        lowcost[j] = map[k][j];
    }
  }
  return ans;
}
 
int main()
{
  while(cin >> N >> M)
  {
    init();
    int x, y, c;
    for(size_t i = 0; i < M; ++i)
    {
      cin >> x >> y >> c;
      if(map[x][y] > c)
        map[x][y] = c;
      if(map[y][x] > c)
        map[y][x] = c;
    }
    cout << prim() << endl;
  }
}
```

