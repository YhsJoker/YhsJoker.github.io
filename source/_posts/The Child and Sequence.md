---
title: The Child and Sequence
date: 2022-12-03 13:39:44
tags:
    - [codeforces]
    - [线段树]
    - [蓝]
categories: 题解
---

一棵裸的线段树,需要思考如何实现区间取模操作

<!-- more -->

## [原题戳这里](https://codeforces.com/problemset/problem/438/D)

## 题目描述

At the children's day, the child came to Picks's house, and messed his house up. Picks was angry at him. A lot of important things were lost, in particular the favorite sequence of Picks.

Fortunately, Picks remembers how to repair the sequence. Initially he should create an integer array a[1], a[2], ..., a[n]. Then he should perform a sequence of m operations. An operation can be one of the following:

1. Print operation l, r. Picks should write down the value of sum[l,r],sum[l,r]=a[l]+a[l+1]+...+a[r]
2. Modulo operation l, r, x. Picks should perform assignment a[i] = a[i] mod x for each i (l ≤ i ≤ r).
3. Set operation k, x. Picks should set the value of a[k] to x (in other words perform an assignment a[k] = x).

Can you help Picks to perform the whole sequence of operations?

## 输入格式

The first line of input contains two integer: n, m (1 ≤ n, m ≤ 105). The second line contains n integers, separated by space: a[1], a[2], ..., a[n] (1 ≤ a[i] ≤ 109) — initial value of array elements.

Each of the next m lines begins with a number type , type belongs to {1,2,3}.

+ If type = 1, there will be two integers more in the line: l, r (1 ≤ l ≤ r ≤ n), which correspond the operation 1.
+ If type = 2, there will be three integers more in the line: l, r, x (1 ≤ l ≤ r ≤ n; 1 ≤ x ≤ 109), which correspond the operation 2.
+ If type = 3, there will be two integers more in the line: k, x (1 ≤ k ≤ n; 1 ≤ x ≤ 109), which correspond the operation 3.

## 输出格式

For each operation 1, please print a line containing the answer. Notice that the answer may exceed the 32-bit integer.

## 输入输出样例

### 输入 #1

```
5 5
1 2 3 4 5
2 3 5 4
3 3 5
1 2 5
2 1 3 3
1 1 3
```

### 输出 #1

```
8
5
```

### 输入 #2

```
10 10
6 9 6 7 6 1 10 10 9 5
1 3 9
2 7 10 9
2 5 10 8
1 4 7
3 3 7
2 7 9 9
1 2 4
1 6 6
1 5 9
3 1 10
```

### 输出 #2
```
49
15
23
1
9
```

## 提示/说明

Consider the first testcase:

+ At first, a = {1, 2, 3, 4, 5}.
+ After operation 1, a = {1, 2, 3, 0, 1}.
+ After operation 2, a = {1, 2, 5, 0, 1}.
+ At operation 3, 2 + 5 + 0 + 1 = 8.
+ After operation 4, a = {1, 2, 2, 0, 1}.
+ At operation 5, 1 + 2 + 2 = 5.

---

## 题目大意

给定一个数列，实现区间查询和，区间取模，单点修改。

## 思路

很明显需要我们维护一颗线段树,那么求区间和和单点修改操作很容易实现,唯一的问题就是区间取模操作.由于区间取模操作无法用懒标记维护,所以我们需要暴力枚举区间内每一个点来取模,但是这样做时间复杂度很高.

不过我们可以知道,当一个区间内的最大值也比模数小的话,就不需要继续递归下去,因此我们可以再维护一个区间最大值,每当区间最大值小于模数后就停止递归下去,这样就可以降低时间复杂度.操作的整体次数也很少,因为x mod p < x/2(p<x) ,所以我们对每个数至多需要取模log x次即可.

## 代码
```
#include<iostream>

#define int long long
#define IOS ios::sync_with_stdio(0);\
cin.tie(0);\
cout.tie(0);

using namespace std;

const int N=100010;

struct Node
{
	int l,r;        //l是区间左端点,r是区间右端点
	int sum,mx;     //sum维护区间和,mx维护区间最大值
};

Node tr[N*4];
int w[N];

void pushup(Node& u,Node& l,Node& r)
{
	u.sum=l.sum+r.sum;
	u.mx=max(l.mx,r.mx);
}

void pushup(int u)
{
	pushup(tr[u],tr[u<<1],tr[u<<1|1]);
}

void build(int u,int l,int r)
{
	if(l==r)
		tr[u]={r,r,w[r],w[r]};
	else
	{
		tr[u]={l,r};
		int mid=l+r>>1;
		build(u<<1,l,mid);
		build(u<<1|1,mid+1,r);
		pushup(u);
	}
}

void modify(int u,int x,int k)
{
	if(tr[u].l==x&&tr[u].r==x)
		tr[u]={x,x,k,k};
	else
	{
		int mid=tr[u].l+tr[u].r>>1;
		if(x<=mid) modify(u<<1,x,k);
		else modify(u<<1|1,x,k);
		pushup(u);
	}
}

void modifyMod(int u,int l,int r,int k)
{
	if(tr[u].mx<k) return;
    //降低时间复杂度最关键的一步,当模数大于当前区间最大值时,就可以停止向下递归

	if(tr[u].l==tr[u].r)
		tr[u].mx=tr[u].sum=tr[u].sum%k;
	else
	{
		int mid=tr[u].l+tr[u].r>>1;
		if(l<=mid) modifyMod(u<<1,l,r,k);
		if(r>mid) modifyMod(u<<1|1,l,r,k);
		pushup(u);
	}
}

int query(int u,int l,int r)
{
	if(l<=tr[u].l&&tr[u].r<=r)
		return tr[u].sum;
	else
	{
		int mid=tr[u].l+tr[u].r>>1;
		int res=0;
		if(l<=mid) res+=query(u<<1,l,r);
		if(r>mid) res+=query(u<<1|1,l,r);
		return res;
	}
}

signed main()
{
	IOS
	int n,m;
	cin>>n>>m;
	for(int i=1;i<=n;i++)
		cin>>w[i];
	build(1,1,n);
	while(m--)
	{
		int op,l,r,k;
		cin>>op;
		if(op==1)
		{
			cin>>l>>r;
			cout<<query(1,l,r)<<'\n';
		}
		if(op==2)
		{
			cin>>l>>r>>k;
			modifyMod(1,l,r,k);
		}
		if(op==3)
		{
			cin>>l>>k;
			modify(1,l,k);
		}
	}
}
```