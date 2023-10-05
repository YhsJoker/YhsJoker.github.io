---
title: BJFU-2023-集训队训练赛-1
date: 2023-01-10 08:29:40
tags:
    - [集训队训练赛]
categories: 题解
description: BJFU集训队寒假训练题目（部分）
---

## A

### 题目链接
https://codeforces.com/problemset/problem/1220/C

### 题目大意
给定字符串s，在一定规则下，求出每一次由谁获胜

规则如下：
+ k为起始l和r的坐标，k从0到strlen(s)
+ 每一次可以将l和r移动到l'和r'，其中l'<=l,r'>=r，并且s[l',r']的字典序要小于s[l,r]
+ Ann先移动
+ 谁无法移动谁就输了

### 思路
我们考虑当什么情况下可以移动，如果l前面存在一个数l'，使得s[l']<s[l]，则可以移动，否则无法移动。因此，若想要自己尽可能能赢，则一定会选择l'，使得l'尽可能小，则下一个人一定无法移动。因此，题目就可以转化为初始时Ann是否可以移动，若Ann可以移动，则一定可以移动到l'，使得在s[l']最小时，l'最小，Mike无法移动，则Ann获胜，若Ann初始时Ann无法移动，则Mike获胜。因此，题目可以进一步转化为是否存在l'，满足l'<k,且s[l']<s[k]。我们可以存储前0到k-1中最小的ascii值，判断是否小于当前的s[k]，若小于，则Ann赢，否则，Mike赢。

### 代码
```cpp
char s[500010];

void solve()
{
	cin>>s;
	char m=s[0];
	cout<<"Mike\n";
	for(int i=1;s[i];i++)
	{
		m=min(m,s[i-1]);
		if(s[i]<=m)
			cout<<"Mike\n";
		else
			cout<<"Ann\n";
	}
}
```

## D

### 题目链接
https://codeforces.com/problemset/problem/1092/D1

### 题目大意
给定一堵墙的每一处的高度，判断我们是否可以通过使用2*1的砖，使这堵墙水平

### 思路
我们可以考虑2*1的砖竖直放置时可以使得一堵墙成为每一处高度只差1的情况，如2,1,1,4,5可以变为6,5,5,6,5，也就相当于0,1,1,0,1。如何判断是否可以水平呢，我们发现，如果相邻两个数相等，则一定可以转化为任意高度，就可以忽略这两堵墙，如果这两处墙左右两边的墙高度也一致，则一定可以使这四处墙高度一致，因此我们可以使用栈来判断相邻处奇偶性。

```cpp
int n;
int a[N];
int sta[N],top;

void init()
{
	cin>>n;
	for(int i=1;i<=n;i++) cin>>a[i];
	for(int i=1;i<=n;i++) a[i]&=1;
}

void solve()
{
	init();
	for(int i=1;i<=n;i++)
	{
		sta[++top]=a[i];
		while(top>=2&&sta[top]==sta[top-1]) top-=2;
	}
	if(top>1)
		cout<<"NO\n";
	else
		cout<<"YES\n";
}
```

## H

### 题目链接
https://codeforces.com/problemset/problem/1481/C

### 题目大意
给定篱笆的颜色，新篱笆的颜色，以及每一个粉刷匠携带的颜色，其中粉刷匠按给定顺序来，并且每一个粉刷匠必须且只能喷一扇篱笆，问是否可以得到新篱笆的颜色，若可以，则输出每一个粉刷匠喷的篱笆是哪一个

### 思路
由于前面来的没有用的粉刷匠都可以让他们喷到后面会被再次喷的篱笆上，就可以使这些粉刷匠不污染颜色，因此我们从后往前找粉刷匠。优先喷与原篱笆颜色不符的篱笆，如果喷完后还有原篱笆的颜色与新篱笆不同，则一定失败。还有一种情况是比如当前面所有粉刷匠喷完篱笆后已经完全相同了，最后一个粉刷匠拿着一个与前面都不同的颜色，那一定失败。我们可以在喷完必须喷的颜色后，找到未喷的粉刷匠中与新色彩一致的满足条件的最后一个粉刷匠，如果在这个粉刷匠之前，就可以喷到这个粉刷匠粉刷的篱笆上，否则，就失败。

### 代码
```cpp
int n,m;
int a[N],b[N],c[N];
int ans[N];
multimap<int,int> mp;   //储存必须喷的篱笆，第一个int是颜色，第二个是坐标
map<int,int> mp2;       //储存新老篱笆颜色相同的篱笆，每种颜色只存储一个即可，int信息同上
void init()
{
	cin>>n>>m;
	for(int i=1;i<=m;i++) ans[i]=0;
	for(int i=1;i<=n;i++) cin>>a[i];
	for(int i=1;i<=n;i++) cin>>b[i];
	for(int i=1;i<=m;i++) cin>>c[i];
	mp.clear();
	mp2.clear();
	for(int i=n;i>=1;i--)
		if(a[i]!=b[i])
			mp.insert({b[i],i});
		else
			if(!mp2.count(b[i]))
				mp2.insert({b[i],i});
}

void solve()
{
	init();
	int mx_ord=-1,idx;
	for(int i=m;i>=1;i--)   //从后往前喷必须喷的
	{
		auto it=mp.find(c[i]);
		if(it!=mp.end())
		{
			ans[i]=it->second;
			if(mx_ord<i)
			{
				mx_ord=i;
				idx=it->second;
			}
			mp.erase(it);
		}
	}
	if(mp.size())   //如果还有需要喷的，则一定失败
	{
		cout<<"NO\n";
		return;
	}
	for(int i=m;i>=1;i--)   //从后往前给剩余未喷的粉刷匠找目标
	{
		if(ans[i]) continue;
		if(i<mx_ord)
		{
			ans[i]=idx;
			continue;
		}
		auto it=mp2.find(c[i]);
		if(it!=mp2.end())
		{
			ans[i]=it->second;
			if(mx_ord<i)
			{
				mx_ord=i;
				idx=it->second;
			}
			continue;
		}
		else
		{
			cout<<"NO\n";
			return;
		}
	}
	cout<<"YES\n";
	for(int i=1;i<=m;i++)
		cout<<ans[i]<<' ';
	cout<<"\n";
}
```

## I

### 题目链接
https://codeforces.com/problemset/problem/1481/B

### 题目大意
有n座高分别为hi的山，你需要进行k次操作，求出第k次操作结束后你的坐标，操作如下
+ 每次操作开始时，你在第一座山
+ 如果下一座山高度<=你所在山，则你到下一座山
+ 如果下一座山高度>你所在山，则你让当前山高度加一，回到起点，本次操作结束
+ 如果到最后第n座山没有拦住你，则你的坐标为-1

### 思路
纯模拟题，无需思路

### 代码
```cpp
int n,k;
int h[105];

void init()
{
	cin>>n>>k;
	for(int i=1;i<=n;i++)
		cin>>h[i];
}

void solve()
{
	init();
	h[n+1]=-1;
	for(int i=1;i<=k;i++)
	{
		for(int j=1;j<=n+1;j++)
		{
			if(j==n+1)
			{
				cout<<-1<<'\n';
				return;
			}
			if(h[j]<h[j+1])
			{
				if(i==k)
				{
					cout<<j<<'\n';
					return;
				}
				h[j]++;
				break;
			}
		}
	}
}
```

## J

### 题目链接
https://codeforces.com/problemset/problem/796/B

### 题目大意
给定n个杯子，m个洞和k次操作，给一个小球，初始时在1处，每次操作交换坐标为a,b的杯子。如果小球在的位置有洞，则掉进洞中，不再改变位置。求小球最后所在的位置。

### 思路
纯模拟，用set记录洞的位置，每次判断是否在洞中即可

### 代码
```cpp
int n,m,k;
set<int> hole;

void init()
{
	cin>>n>>m>>k;
	while(m--)
	{
		int x;
		cin>>x;
		hole.insert(x);
	}
}

void solve()
{
	int pos=1;
	bool in_hole=0;
	init();
	while(k--)
	{
		if(hole.count(pos)) in_hole=1;
		int x,y;
		cin>>x>>y;
		if(!in_hole)
		{
			if(pos==x)
				pos=y;
			else if(pos==y)
				pos=x;
		}
	}
	cout<<pos<<'\n';
}
```

## K

### 题目链接
https://codeforces.com/problemset/problem/1474/A

### 题目大意
给定一个长度为n的字符串b，求字符串a，满足以下规则
+ a,b长度相等，且只含有0,1，但这不是二进制
+ 使a+b尽可能大，但是，a+b中如果相邻的数相等，则会只保留一个

### 思路
贪心，使最高位尽可能的大。之后的位和前一个位比较，如果a为1时与前一位不同，则a为1，否则为0，这样就可以保证在高位尽可能大时不会发生合并

### 代码
```cpp
char s[100010];
void solve()
{
	int n;
	cin>>n>>s;
	s[0]++;
	cout<<1;
	for(int i=1;i<n;i++)
	{
		if(s[i]+1!=s[i-1])
		{
			cout<<1;
			s[i]++;
		}
		else
		{
			cout<<0;
		}
	}
	cout<<'\n';
}
```

## L

### 题目链接
https://codeforces.com/problemset/problem/1474/B

### 题目大意
给定t个数d，对每一个d，求出一个最小的数a，其中a的因子个数大于等于4，且a的任意因子的差值大于等于d

### 思路
a一定包含1和a本身，因此只需要再找出两个因子即可。若这两个因子中有非质因子仍满足条件，则只含其质因子也一定满足条件，所以两个因子都是质因子。可以用任意素数筛预处理出需要的素数，然后找到两个素数满足题目表述即可

### 代码
```cpp
const int N=1000000;
int prime[100000],sz;
bool is_prime[N];

void init() //预处理素数，写在主函数即可
{
	memset(is_prime,1,sizeof is_prime);
	is_prime[0]=0,is_prime[1]=0;
	for(int i=2;i<N;i++)
	{
		if(is_prime[i])
		{
			prime[sz++]=i;
			for(int j=i+i;j<N;j+=i)
			{
				is_prime[j]=0;
			}
		}
	}
}

void solve()
{
	int d,a,b;
	cin>>d;
	int i=0;
	while(prime[i]-1<d)
		i++;
	a=prime[i];
	while(prime[i]-a<d)
		i++;
	b=prime[i];
	cout<<(long long)a*b<<'\n'; //保险起见开long long
}

```

## M

### 题目链接
https://codeforces.com/problemset/problem/1474/C

### 题目大意
给定一个长度为n*2的数列，问是否存在一个数x，使得数列能清空，若可以，给出x和每一次的清除元素，清空规则如下：
+ 选择两个数a,b,使得a+b==x，清除a，b，并将x改为max(a,b)
+ 继续执行，直到数列为空

### 思路
由于x满足a+b==x，所以，每一次的x一定大于剩余数列中最大的数。因此，当确定x后，我们每次一定取剩余数列中最大数a和另一个数x-a，并将x改为a。当结束之前，我们无法在数列中取到x-a时，说明初始x不合法。确定检验x规则后，我们可以枚举所有可能的x，判断是否有成立的若都不成立，则不存在。x一定是初始数列中最大数和一个其他元素的和。

### 代码
```cpp
int n;
int a[2010];

vector<pii> check(int mx)
{
	vector<pii> ans;
	multiset<int> ms;
	for(int i=0;i<2*n;i++)
		ms.insert(a[i]);
	for(int i=0;i<n;i++)
	{
		auto e=*(--ms.end());
		ms.erase(--ms.end());
		auto it=ms.find(mx-e);
		if(it==ms.end())
			return {};
		ans.push_back({mx-e,e});
		ms.erase(it);
		mx=e;
	}
	return ans;
}

void solve()
{
	cin>>n;
	for(int i=0;i<2*n;i++)
		cin>>a[i];
	sort(a,a+2*n);
	for(int i=2*n-2;i>=0;i--)
	{
		auto ans=check(a[i]+a[2*n-1]);
		if(ans.empty()) continue;
		cout<<"YES\n";
		cout<<a[i]+a[2*n-1]<<'\n';
		for(auto e:ans)
		{
			cout<<e.first<<' '<<e.second<<'\n';
		}
		return;
	}
	cout<<"NO"<<'\n';
}
```