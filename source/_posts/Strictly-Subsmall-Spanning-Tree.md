---
title: 严格次小生成树
date: 2022-11-30 22:53:44
tags:
	- [洛谷]
	- [Kruskal重构树]
	- [倍增]
	- [紫]
categories: 题解
description: 很综合的一道题目,代码较长,且细节比较多
---

## [原题戳这里](https://www.luogu.com.cn/problem/P4180)


## 题目描述
小 C 最近学了很多最小生成树的算法，Prim 算法、Kruskal 算法、消圈算法等等。正当小 C 洋洋得意之时，小 P 又来泼小 C 冷水了。小 P 说，让小 C 求出一个无向图的次小生成树，而且这个次小生成树还得是严格次小的,也就是说,严格次小生成树的边权值和要严格大于最小生成树的边权之和.

这下小 C 蒙了，他找到了你，希望你帮他解决这个问题。

## 输入格式

第一行包含两个整数N和M,表示无向图的点数与边数。

接下来M行,每行3个数x,y,z表示，点x和点y之间有一条边，边的权值为z。

## 输出格式

包含一行，仅一个数，表示严格次小生成树的边权和。

## 输入输出样例

### 输入#1
```
5 6
1 2 1 
1 3 2 
2 4 3 
3 5 4 
3 4 3 
4 5 6 
```

### 输出#1
```
11
```

## 提示/说明

数据中无向图不保证无自环

对于100%的数据, N<=10^5, M<=3*10^5,0<=z<=10^9,数据保证必定存在严格次小生成树

---

## 题目大意

找到严格次小生成树,输出它的边权和

## 思路

首先需要知道,严格次小生成树和最小生成树有且仅有一条边不同,可以通过反证法证明

> **证明**:
> 假设存在严格次小生成树S2,有k(k≥2)条边与最小生成树S1不同,则我们删去不同的这k条边,就会出现k+1个连通块,然后我们再选择k个部分用最小生成树中的边将它们连接成一个连通块,此时它显然与最小生成树只有一个边的差距,最后选择次小生成树的边将它们连接.此时,新连通的生成树S0会满足以下关系,S1<S0<S2,因此,与假设矛盾,证得严格次小生成树和最小生成树有且仅有一条边不同

然后,我们需要做的就是在最小生成树外找到一条边,替换掉最小生成树中的一条边,令新的生成树为次严格最小生成树.

我们的做法就是枚举每一条不在最小生成树中的边e,权重为w,然后将它添加进最小生成树中.当我们在添加一条边e后,树的局部就会形成一个环,如果我们要想使新的生成树尽可能的小,我们就需要将环中非e的最大边e_max删除,得到的就是其中一个局部最优的生成树,然后我们将每个局部最优生成树进行比较,最终得到全局的次严格最小生成树.


由于要求的是次严格最小生成树,所以当删除环内最大边e_max时,如果其w_max==w,则我们需要删除环内的严格次大边.

如何快速得到环内的最大边和严格次大边,我们可以使用倍增来维护

代码的整体流程就是:求出最小生成树,枚举不在树上的每一条边,从边上的两个顶点开始跑倍增算法,求出环上要删除的边,求得此生成树的大小,更新严格次小生成树

## 代码
```cpp
#include<iostream>
#include<cstring>
#include<algorithm>

using namespace std;
using ll=long long;

const int N=100010,M=300010,INF=0x3f3f3f3f;

int n,m;

struct edge
{
	int u,v,w;
	bool st;    //储存此边是否在最小生成树中
	bool operator<(edge r)
	{
		return w<r.w;
	}
};

edge edg[M];    //储存全部边
int p[N];   //跑kruskal使用的并查集
int h[N],e[M],ne[M],w[M],idx;   //链式向前星储存最小生成树
int depth[N],fa[N][18],d1[N][18],d2[N][18]; 
//depth[i]:储存i节点深度 fa[j][k]:j节点向上第2^k个父节点 
//d1[j][k]:j节点向上2^k条边中的最大值 d2[j][k]:j节点向上2^k条边中的严格次大值

int q[N];   //跑bfs用的队列

int find(int x)
{
	if(p[x]!=x) p[x]=find(p[x]);
	return p[x];
}

ll kruskal()
{
	for(int i=1;i<=n;i++)
		p[i]=i;
	ll res=0;
	sort(edg,edg+m);
	for(int i=0;i<m;i++)
	{
		int a=find(edg[i].u),b=find(edg[i].v);
		if(a!=b)
		{
			edg[i].st=1;
			res+=edg[i].w;
			p[a]=b;
		}
	}
	return res;
}

void add(int a,int b,int c)
{
	e[idx]=b;
	w[idx]=c;
	ne[idx]=h[a];
	h[a]=idx++;
}

void build()
{
	memset(h,-1,sizeof h);
	
	for(int i=0;i<m;i++)
	{
		if(edg[i].st)
		{
			add(edg[i].u,edg[i].v,edg[i].w);
			add(edg[i].v,edg[i].u,edg[i].w);
		}
	}
}

void bfs()
{
	memset(depth,0x3f,sizeof depth);
	depth[1]=1;
	depth[0]=0;
	int hh=0,tt=0;
	q[0]=1;
	while(hh<=tt)
	{
		int u=q[hh++];
		for(int i=h[u];~i;i=ne[i])
		{
			int j=e[i];
			if(depth[j]>depth[u]+1)
			{
				depth[j]=depth[u]+1;
				q[++tt]=j;
				fa[j][0]=u;
				d1[j][0]=w[i];
				d2[j][0]=-INF;  //次大值不存在时,设为-INF
				for(int k=1;k<18;k++)
				{
					int anc=fa[j][k-1];

					int distance[4]={d1[j][k-1],d1[anc][k-1],d2[j][k-1],d2[anc][k-1]};  
					//整段的最大值和次大值只能在两个小段的最大值和次大值中出现

					fa[j][k]=fa[anc][k-1];
					int m1=-INF,m2=-INF;    //m1:储存最大值,m2:储存次大值
					for(int t=0;t<4;t++)
					{
						int d=distance[t];
						if(d>m1) m2=m1,m1=d;
						else if(d<m1&&d>m2) m2=d;
					}
					d1[j][k]=m1,d2[j][k]=m2;
				}
			}
		}
	}
	
}

int lca(int a,int b,int w)
{
	int d[N*2],cnt=0;
	if(depth[a]<depth[b]) swap(a,b);
	for(int k=17;k>=0;k--)
	{
		if(depth[fa[a][k]]>=depth[b])
		{
			d[cnt++]=d1[a][k];
			d[cnt++]=d2[a][k];
			a=fa[a][k];
		}
	}
	if(a!=b)
	{
		for(int k=17;k>=0;k--)
		{
			if(fa[a][k]!=fa[b][k])
			{
				d[cnt++]=d1[a][k];
				d[cnt++]=d2[a][k];
				d[cnt++]=d1[b][k];
				d[cnt++]=d2[b][k];
				a=fa[a][k];
				b=fa[b][k];
			}
		}
		d[cnt++]=d1[a][0];
		d[cnt++]=d2[a][0];
		d[cnt++]=d1[b][0];
		d[cnt++]=d2[b][0];
	}
	int m1=-INF,m2=-INF;
	for(int i=0;i<cnt;i++)
	{
		int dd=d[i];
		if(dd>m1) m2=m1,m1=dd;
		else if(dd<m1&&dd>m2) m2=dd;
	}
	
	if(w>m1) return w-m1;
	if(w>m2) return w-m2;
	return INF;
}

int main()
{
	cin>>n>>m;
	for(int i=0;i<m;i++)
	{
		int a,b,c;
		cin>>a>>b>>c;
		edg[i]={a,b,c};
	}
	ll sum=kruskal();
	build();
	bfs();
	ll res=1e18;
	for(int i=0;i<m;i++)
	{
		if(!edg[i].st)
		{
			int t=lca(edg[i].u,edg[i].v,edg[i].w);
			res=min(res,sum+t);
		}
	}
	cout<<res;
}
```

