---
title: BJFU-2023-集训队训练赛-2
date: 2023-01-12 08:23:43
tags:
    - [集训队训练赛]
categories: 题解
description: BJFU集训队寒假训练题目（部分）
---

## A

### 题目链接
https://codeforces.com/problemset/problem/1552/B

### 题目大意
有n个人，每个人有过去五场比赛的名次，问是否有人在这场比赛中能赢过所有人，赢过一个人的条件是在过去的五场比赛中排名比他高至少三次

### 思路
要判断是否会有运动员获得奖牌，只要判断最有可能的运动员能否获得奖牌即可，那我们可以用快排来将最有可能的人放在最前面，再判断是否符合即可。

### 代码
```cpp
struct p
{
	int ord;
	int sco[M];
	bool operator<(p r)
	{
		int win=0;
		for(int i=0;i<5;i++)
			if(sco[i]<r.sco[i])
				win++;
		return win>=3;
	}
};

int n;
p a[N];

void init()
{
	cin>>n;
	for(int i=1;i<=n;i++)
	{
		a[i].ord=i;
		for(int j=0;j<M;j++)
			cin>>a[i].sco[j];
	}
}

void solve()
{
	init();
	sort(a+1,a+1+n);
	for(int i=2;i<=n;i++)
	{
		if(!(a[1]<a[i]))
		{
			cout<<"-1\n";
			return;
		}
	}
	cout<<a[1].ord<<'\n';
	
}
```

## B

### 题目链接
https://codeforces.com/problemset/problem/1551/C

### 题目大意
给定n个只含有a,b,c,d,e的单词，在这n个单词中选择最大数目的单词，其中选择的单词需要满足如下规则：
+ 这些单词中某一个字母的数量要大于其他单词的数量和

### 思路
枚举每一种选择的字母，优先选择单词中这个字母数减其他字母数的差最大的单词，直到差值和小于等于零时，就不能选择了。

### 代码
```cpp
struct S
{
	int num[M];
	int tot;
	bool operator<(S r)
	{
		return num[base]-(tot-num[base])>r.num[base]-(r.tot-r.num[base]);
	}
};

int n;
S a[N];

void init()
{
	cin>>n;
	string s;
	for(int i=0;i<n;i++)
	{
		cin>>s;
		for(int j=0;j<5;j++)
			a[i].num[j]=0;
		for(auto e:s)
			a[i].num[e-'a']++;
		a[i].tot=s.size();
	}
}

void solve()
{
	init();
	int ans=0;
	for(base=0;base<M;base++)
	{
		sort(a,a+n);
		int dif=0;
		for(int i=0;i<n;i++)
		{
			dif+=a[i].num[base]-(a[i].tot-a[i].num[base]);
			if(dif<=0)
			{
				ans=max(ans,i);
				break;
			}
		}
		if(dif>0) ans=n;
	}
	cout<<ans<<'\n';
}
```

## C

### 题目链接
https://codeforces.com/problemset/problem/1548/A

### 题目大意
给定n个节点和m个边
接下来会有q次操作
+ 在u，v间添加一条边，保证此前u，v间无边
+ 在u，v间移除一条边，保证此前u，v间有边
+ 表示执行以下操作直至不可再执行为止。定义一个人的强度为其编号。在每个 大小大于 1 的连通块中找到强度最小的人，将这个人及其所连的边一同删去。在所有操作执行完毕后，请你输出还剩下多少人。注意，每个 3 操作之间彼此独立。即删人只是暂时的，这次操作结束之后所有被删的人连同边会复活。
### 思路
我们可以考虑什么人会存活到最后，1是独立的人，2是比相连的所有点都大，那么可以统一为一个信息，就是周围比它大的点数为0。因此我们可以统计每一个点周围比它大的点的个数。在统计时没有必要遍历一遍，我们只需统计这个信息从0变为1和从1变为0时的变化即可，从0变为1说明又有一个点要被删除，从1变为0说明又多了一个点存活下来。

### 代码
```cpp
int n,m,q;
int cnt[N];
int num=0;

void init()
{
	cin>>n>>m;
	for(int i=1;i<=m;i++)
	{
		int a,b;
		cin>>a>>b;
		if(a>b) swap(a,b);
		if(!cnt[a]) num++;
		cnt[a]++;
	}
}

void solve()
{
	init();
	cin>>q;
	while(q--)
	{
		int op,u,v;
		cin>>op;
		if(op==1)
		{
			cin>>u>>v;
			if(u>v) swap(u,v);
			if(!cnt[u])
				num++;
			cnt[u]++;
		}
		else if(op==2)
		{
			cin>>u>>v;
			if(u>v) swap(u,v);
			cnt[u]--;
			if(!cnt[u])
				num--;
		}
		else
		{
			cout<<n-num<<'\n';
		}
	}
}
```

## D

### 题目链接
https://codeforces.com/problemset/problem/1527/B1

### 题目大意
给定一个只含有0，1的回文串，两个人依次进行如下操作，问游戏结束后谁的花费最低
+ 选择一个0变为1，花费1
+ 若当前不是回文串，则可以翻转该回文串，花费为0
+ 当全为1后，游戏结束

### 思路
首先考虑含有偶数个0的情况，当Alice先手后，Bob可以选择在对称位置也改为1，依次进行，直到最后一个0时，Bob可以选择翻转字符串，让Alice再花费1，所以Bob必胜。接下来考虑奇数个1的情况，当只有1个1时，Bob必胜，否则，Alice选择把中间的0改为1，然后当Bob下完后，Alice在对称位置改为1，直到最后一个1时，Alice选择翻转字符串，就可以让Bob最终比自己多花费1，Alice获胜。

### 代码
```cpp
int n;
char s[N];

void init()
{
	cin>>n>>s;
}

void solve()
{
	init();
	int t=0;
	for(int i=0;i<n;i++)
		if(s[i]=='0')
			t++;
	if(t&1)
	{
		if(t==1) cout<<"BOB\n";
		else cout<<"ALICE\n";
	}
	else
	{
		cout<<"BOB\n";
	}
}
```

## E

### 题目链接
https://codeforces.com/problemset/problem/1521/B

### 题目大意
给定一个长度为n的序列，使其变为Good，序列为Good的条件为相邻两数互质，你可以进行的操作为
+ 选择两个数x,y，改变它们为x'，y'，其中min(x,y)==min(x',y')
你最多可以进行n次操作

### 思路
我们可以知道，k和k+1互质，所以，我们可以选择序列中最小的数m为基准，使整个序列变为如下形式：m+3，m+2,m+1,m,m+1,m+2,m+3.m+4即可，每次改变m和一个其他数，就可以保证更改前后最小数一定是m

### 代码
```cpp
int n;
int a[N];

void init()
{
	cin>>n;
	for(int i=1;i<=n;i++)
		cin>>a[i];
}

void solve()
{
	init();
	cout<<n-1<<'\n';
	int idx=1;
	for(int i=2;i<=n;i++)
	{
		if(a[i]<a[idx]) idx=i;
	}
	for(int i=1;i<=n;i++)
	{
		if(idx==i) continue;
		cout<<idx<<' '<<i<<' '<<a[idx]<<' '<<a[idx]+abs(i-idx)<<'\n';
	}
}
```

## F

### 题目链接
https://codeforces.com/problemset/problem/1520/A

### 题目大意
给定一个序列，求是否存在同一种字符出现在不连续的位置，如：ABA不连续，AAB连续

### 思路
当出现一个字符在之前出现过后，判断这个字符的前一个字符是否和它相同，不相同的话就一定是不连续的

### 代码
```cpp
int n;
char s[N];
set<char> st;

void init()
{
	cin>>n>>s;
	st.clear();
}

void solve()
{
	init();
	for(int i=0;i<n;i++)
	{
		if(!st.count(s[i]))
			st.insert(s[i]);
		else
		{
			if(s[i-1]!=s[i])
			{
				cout<<"NO\n";
				return;
			}
		}
	}
	cout<<"YES\n";
}
```

## G

### 题目链接
https://codeforces.com/problemset/problem/1514/C

### 题目大意
在[1,2,...,n-1]中选择任意个数，使得它们的乘积%n==1，打印出任一答案即可

### 思路
首先我们令乘积为m，则m%n==1可以推出gcd(m,n)==1（见证明1）,然后我们就可以求出所有与n互质的数，将它们乘起来模n，若结果不为1，则将结果w去除即可，w肯定在与n互质的数中（见证明2）

> 证明1：反证法，假设m,n不互质，则gcd(m,n)==d(d>1)。m%n==1可以表示为m==n*k+1,令m=ad，n=bd，则ad=nbd+1,(a-nb)d==1,由于a，b，n，d都为整数，且d>1，则此式不成立，所以证得若m%n==1,则gcd(m,n)==1

> 证明2：gcd(m,n)==1,则gcd(m%n,n)==1,则gcd(w,n)==1，由于w<n，所以w在与n互质的数中
### 代码
```cpp
int n;
set<int> ans;

int gcd(int x,int y){return y?gcd(y,x%y):x;}

void init()
{
	cin>>n;
}

void solve()
{
	init();
	int m=1;
	for(int i=1;i<n;i++)
		if(gcd(i,n)==1)
			ans.insert(i),m=m*i%n;
	if(m>1) ans.erase(m);
	cout<<ans.size()<<'\n';
	for(auto e:ans)
		cout<<e<<' ';
}
```

## H

### 题目链接
https://codeforces.com/problemset/problem/1512/D

### 题目大意
给定n+2长度的序列，是否能选择其中n个数，使得这n个数的和等于剩余两个数中的其中一个

### 思路
剩余的两个数只可能是序列中次大或最大的。若是次大的，则一定是前n个数，判断是否相等即可。若是最大的，则剩余的一个数一定是前面所有数的和减去最大数，判断是否存在这样一个数即可。

### 代码
```cpp
int n;
int a[N];
void init()
{
	cin>>n;
	for(int i=0;i<n+2;i++)
	{
		cin>>a[i];
	}
}

void solve()
{
	init();
	int tot=0;
	sort(a,a+n+2);
	for(int i=0;i<n;i++)
		tot+=a[i];
	if(tot==a[n])
	{
		for(int i=0;i<n;i++)
			cout<<a[i]<<' ';
		cout<<'\n';
		return;
	}
	tot+=a[n];
	int delidx=-1;
	for(int i=0;i<n+1;i++)
	{
		if(tot-a[i]==a[n+1])
			delidx=i;
	}
	if(delidx==-1)
	{
		cout<<"-1\n";
		return;
	}
	for(int i=0;i<n+1;i++)
	{
		if(i==delidx) continue;
		cout<<a[i]<<' ';
	}
	cout<<'\n';
}
```

## K

### 题目链接
https://codeforces.com/problemset/problem/1594/D

### 题目大意
给定n个人和m个描述，描述信息是a描述b是诚实者/说谎者，问在这种情况下说谎者最多是几个

### 思路
若a描述b是诚实者，则a和b身份相同。若a描述b是说谎者，则a和b身份相反。可以用并查集来维护，身份相同则在一个集合中，否则不在一个集合。若一个集合中出现了矛盾，则输出-1。

### 代码
```cpp
const int N=200010,M=500010;

int n,m;
int x[M],y[M];
bool same[M];
int p[N*2],sz[N*2];

char s[30];

int find(int x)
{
	if(p[x]==x) return p[x];
	p[x]=find(p[x]);
	sz[p[x]]+=sz[x];
	sz[x]=0;
	return p[x];
}

void merge(int a,int b)
{
	int pa=find(a),pb=find(b);
	if(pa==pb) return;
	p[pa]=pb;
	sz[pb]+=sz[pa];
	sz[pa]=0;
}

void init()
{
	cin>>n>>m;
	for(int i=1;i<=m;i++)
	{
		cin>>x[i]>>y[i]>>s;
		if(*s=='c') same[i]=1;
		else same[i]=0;
	}
	for(int i=1;i<=n*2;i++)
		p[i]=i;
	for(int i=1;i<=n;i++)
		sz[i]=1;
	for(int i=n+1;i<=n*2;i++)
		sz[i]=0;
}

void solve()
{
	init();
	for(int i=1;i<=m;i++)
	{
		if(same[i])
			merge(x[i],y[i]),merge(x[i]+n,y[i]+n);
		else
			merge(x[i],y[i]+n),merge(x[i]+n,y[i]);
	}
	int ans=0;
	for(int i=1;i<=n;i++)
	{
		if(find(i)==find(i+n))
		{
			cout<<"-1\n";
			return;
		}
		ans+=max(sz[find(i)],sz[find(i+n)]);
		sz[find(i)]=0;
		sz[find(i+n)]=0;
	}
	cout<<ans<<'\n';
	
}
```