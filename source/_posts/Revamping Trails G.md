---
title: Revamping Trails G
date: 2022-12-01 21:32:14
tags:
	- [洛谷]
	- [分层图]
	- [蓝]
categories: 题解
---

一道分层图最短路模板题

<!-- more -->

## [原题戳这里](https://www.luogu.com.cn/problem/P2939)

## 题目描述

Farmer John dutifully checks on the cows every day. He traverses some of the M (1 <= M <= 50,000) trails conveniently numbered 1..M from pasture 1 all the way out to pasture N (a journey which is always possible for trail maps given in the test data). The N (1 <= N <= 10,000) pastures conveniently numbered 1..N on Farmer John's farm are currently connected by bidirectional dirt trails. Each trail i connects pastures P1_i and P2_i (1 <= P1_i <= N; 1 <= P2_i <= N) and requires T_i (1 <= T_i <= 1,000,000) units of time to traverse.

He wants to revamp some of the trails on his farm to save time on his long journey. Specifically, he will choose K (1 <= K <= 20) trails to turn into highways, which will effectively reduce the trail's traversal time to 0. Help FJ decide which trails to revamp to minimize the resulting time of getting from pasture 1 to N.

TIME LIMIT: 2 seconds

## 输入格式

Line 1: Three space-separated integers: N, M, and K

Lines 2..M+1: Line i+1 describes trail i with three space-separated integers: P1_i, P2_i, and T_i

## 输出格式

Line 1: The length of the shortest path after revamping no more than K edges

## 输入输出样例

### 输入 #1
```
4 4 1 
1 2 10 
2 4 10 
1 3 1 
3 4 100 
```

### 输出 #1
```
1 
```

## 提示/说明

K is 1; revamp trail 3->4 to take time 0 instead of 100. The new shortest path is 1->3->4, total traversal time now 1.

---

## 题目大意

在一张无向图中,将至多k条边的边权变为零,使得从1号点到n号点的最短路最小

## 思路

分层图是什么东西呢?分层图是将一个图复制粘贴多次,然后叠在一起,就形成了一个多层的图,每一层的节点和边完全相同,不同的只有从当前层到下一层的连边方式,我们可以通过改变每一层之间的联系来实现本题中对一些边的修改.

在本题中,我们定义第0层为初始层,第i层为改变了i条边后层.注意改边时不是改边第i层的边,而是控制从第i-1层到第i层的连边方式.我们将第i-1层的每一个点u能到达的点v和第i层中与u位置相同的点v'连接,边权设为0,表示从u到v的路径被设为了0,这样每跑到下一层后,就有一条边的边权变为了0,然后跑从1到每一个点的最短路即可.

注意,由于是至多改变k次,所以最小值可能是dist[n*i+n]中的任意一个,其中,0<=i<=k


## 代码
```cpp
#include<iostream>
#include<queue>
#include<cstring>

using namespace std;
using pii=pair<int,int>;
const int N=10010,M=200010,K=25;    //M要开四倍,因为无向图两倍,向下一层建边两倍

int h[N*K],e[M*K],ne[M*K],w[M*K],idx;   //第k层的i点为:n*(k-1)+i,n为一层的点数
bool st[N*K];
int dist[N*K];
int n,m,k;

int u[M],v[M],ww[M];

void add(int a,int b,int c)
{
	e[idx]=b,w[idx]=c,ne[idx]=h[a],h[a]=idx++;
}

void dijkstra()
{
	memset(dist,0x3f,sizeof dist);
	priority_queue<pii,vector<pii>,greater<pii>> q;
	dist[1]=0;
	q.push({0,1});
	
	while(q.size())
	{
		int u=q.top().second;
		q.pop();
		if(st[u]) continue;
		st[u]=1;
		for(int i=h[u];~i;i=ne[i])
		{
			int j=e[i];
			if(dist[j]>dist[u]+w[i])
			{
				dist[j]=dist[u]+w[i];
				q.push({dist[j],j});
			}
		}
	}
}

int main()
{
	memset(h,-1,sizeof h);
	cin>>n>>m>>k;
	for(int i=1;i<=m;i++)
		cin>>u[i]>>v[i]>>ww[i];

	for(int i=0;i<=k;i++)   //对每一层建边
	{
		for(int j=1;j<=m;j++)   对当前层的所有点连边
		{
            //将当前层连边
			add(n*i+u[j],n*i+v[j],ww[j]);
			add(n*i+v[j],n*i+u[j],ww[j]);

            //将当前层与下一层连边
			add(n*i+u[j],n*(i+1)+v[j],0);
			add(n*i+v[j],n*(i+1)+u[j],0);
		}
	}

	dijkstra();

	int ans=2e9;
	for(int i=0;i<=k;i++)
	{
		ans=min(ans,dist[n*i+n]);
	}
	cout<<ans;
}
```