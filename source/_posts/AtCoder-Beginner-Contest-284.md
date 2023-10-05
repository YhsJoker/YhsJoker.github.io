---
title: AtCoder Beginner Contest 284
date: 2023-01-08 09:18:13
tags:
	- [AtCoder]
categories: 题解
description: AtCoder Beginner Contest 284 A-E
---

### 原题链接：[戳这里](https://atcoder.jp/contests/abc284)

---

## A

### 题目大意
读入N个字符串，然后倒序输出

### 思路
使用vector，stack等容器实现

### 代码
```cpp
#include<iostream>
#include<string>
#include<vector>
using namespace std;

vector<string> v;

int main()
{
	int n;
	cin>>n;
	while(n--)
	{
		string s;
		cin>>s;
		v.push_back(s);
	}
	for(auto it=v.rbegin();it!=v.rend();it++)
		cout<<*it<<endl;
}
```

## B

### 题目大意
给定T组数据，对于每组数据，有N个整数，求出这N个整数中奇数的个数

### 思路
奇数即%2余1的数

### 代码
```cpp
#include<iostream>
using namespace std;

void solve()
{
	int n,ans=0;
	cin>>n;
	while(n--)
	{
		int x;
		cin>>x;
		if(x&1)
			ans++;
	}
	cout<<ans<<endl;
}

int main()
{
	int t;
	cin>>t;
	while(t--)
		solve();
}
```

## C

### 题目大意
给定N个点和M条边，求有多少个连通块

### 思路
用并查集来维护，初始有N个连通块，每当有两个不在一个集合内的点连一条边时，连通块的个数减一

### 代码
```cpp
#include<iostream>

using namespace std;

int p[105];
int find(int x)
{
	if(p[x]!=x) p[x]=find(p[x]);
	return p[x];
}

int main()
{
	int n,m;
	cin>>n>>m;
	int ans=n;
	for(int i=1;i<=n;i++) p[i]=i;
	while(m--)
	{
		int a,b;
		cin>>a>>b;
		int pa=find(a),pb=find(b);
		if(pa!=pb)
			p[pa]=pb,ans--;
	}
	cout<<ans;
}
```

## D

### 题目大意
给定T组数据，对于每组数据，有一个整数N，N可以被分解成p^2*q的形式，其中p和q都是质数，求p和q

### 思路
N的范围到达10^18次方，因此最差时间复杂度也基本是三次根号下N。考虑到N的形式，我们只需找到一个N的因子t，即可得到p和q，因为若t是p，则q是N/(t*t);若t是q，则p是sqrt(N/t)。那么问题就转移为了如何求出N的最小因子。考虑当N的最小因子最大时，也不过10^6级别，因为N=p^2\*q,若N的最小因子大于10^6，则N大于10^18。所以只需要从2开始枚举，找到第一个因子即可，时间复杂度为O(三次根号下N)。

### 代码
```cpp
#include<iostream>
#include<cmath>
using namespace std;
using ll=long long;
void solve()
{
	ll n;
	ll p,q;
	cin>>n;
	for(ll i=2;;i++)
	{
		if(n%i==0)
		{
			ll t=n/i;
			if(t%i==0)  //如果n是i*i的倍数，则i就是p
			{
				p=i;
				q=t/i;
			}
			else
			{
				q=i;
				p=sqrt(t);  //由于有精度问题，所以要找到正确的，或者此处可以写成round(sqrt(t));
				if(p*p<t) p++;
				if(p*p>t) p--;
			}
			break;
		}
	}
	cout<<p<<' '<<q<<endl;
}

int main()
{
	int t;
	cin>>t;
	while(t--)
		solve();
}
```

## E

### 题目大意
给定N个点和M条边，定义从1出发的路径数量为K，求min(K,10^6)。其中路径上不能有重复的点。

### 思路
图的dfs，通过手动模拟即可很容易了解

### 代码
```cpp
#include<iostream>
#include<cstring>
using  namespace std;

const int N=200010,M=N*2;

int h[N],e[M],ne[M],idx;
bool st[N];

int n,m;
int ans;

void add(int a,int b)
{
	e[idx]=b;
	ne[idx]=h[a];
	h[a]=idx++;
}

void dfs(int x)
{
	if(ans>=1000000) return;
	if(st[x]) return;   //当该点在路径当中时就不能使用
	st[x]=1;
	ans++;
	for(int i=h[x];i!=-1;i=ne[i])
	{
		int j=e[i];
		dfs(j);
	}
	st[x]=0;    //回溯，该点结束后可能有其他路线再次经过该点
}

int main()
{
	memset(h,-1,sizeof h);
	cin>>n>>m;
	for(int i=0;i<m;i++)
	{
		int a,b;
		cin>>a>>b;
		add(a,b);
		add(b,a);
	}
	
	dfs(1);
	
	cout<<ans;
}
```