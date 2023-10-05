---
title: 2023年BJFU寒假算法训练营DAY3
date: 2023-01-17 13:42:45
tags:
    - [BJFU寒假算法训练营]
categories: 题解
description: BJFU寒假算法训练复习题目。
---

## A

### 题目链接
https://www.luogu.com.cn/problem/P4913

### 题目大意
求二叉树的深度

### 思路
本代码采用朴素建树方式，即每一个节点存储其左右儿子节点下标
dfs：求出两个子树的深度，那么该树的深度就是最大子树深度+1
bfs：记录父节点深度，下一层深度为当前节点深度+1，到叶子节点时更新最大深度

### 代码
```cpp
#include <iostream>
#include <queue>

using namespace std;
using pii=pair<int,int>;

const int N = 1e6+10;

struct node
{
	int ord, l, r;  //ord： 节点编号  l：左儿子下标  r：右儿子下标
};

int n;
node tr[N]; //建树

void init()
{
	cin >> n;
	for(int i = 1; i <= n; i++)
	{
		int l, r;
		cin >> l >> r;
		tr[i] = {i, l, r};
	}
}

int dfs(int u)
{
	if(tr[u].ord == 0)  //空节点没有深度
		return 0;
	return max(dfs(tr[u].l), dfs(tr[u].r)) + 1;
}

int bfs(int u)
{
	int max_depth = 0;
	
	queue<pii> q;
	q.push({u, 1});
	while(!q.empty())
	{
		pii t = q.front();
		q.pop();
		
		int ord = t.first, depth = t.second;
		
		if(tr[ord].l==0 && tr[ord].r==0) {max_depth = max(max_depth, depth); continue;}
		if(tr[ord].l) q.push({tr[ord].l, depth + 1});
		if(tr[ord].r) q.push({tr[ord].r, depth + 1});
	}
	
	return max_depth;
}

int main()
{
	init();
	//cout << dfs(1);
	cout << bfs(1);
}
```

## B

### 题目链接
https://www.luogu.com.cn/problem/P1364

### 题目大意
选择一个点，使这个点到其他所有点的距离乘权重之和最小

### 思路
本题采用邻接表建树
由于数据范围很小，因此我们可以枚举每一个点，求出以该点为医院的距离和，更新最小距离和。dfs方式为返回该节点及其子树的距离和。

### 代码
```cpp
#include <iostream>
#include<cstring>

using namespace std;

const int N = 110, M =210; 

int h[N], w[N], e[M], ne[M], idx;

void add(int u, int v)
{
	e[idx] = v;
	ne[idx] = h[u];
	h[u] = idx++;
}

int dfs(int u, int fa, int dist)
{
	int tot_dist = w[u] * dist;
	for(int i = h[u]; ~i; i = ne[i])
	{
		int j = e[i];
		if(j != fa) tot_dist += dfs(j, u, dist + 1);
	}
	return tot_dist;
}

int n;

void init()
{
	memset(h, -1, sizeof h);
	cin >> n;
	for(int i = 1; i <= n; i++)
	{
		int u, v;
		cin >> w[i] >> u >> v;
		if(u) add(i, u), add(u, i);
		if(v) add(i, v), add(v, i);
	}
}

int main()
{
	init();
	int res = 0x3f3f3f3f;
	for(int i = 1; i <= n; i++)
		res = min(res, dfs(i, 0, 0));
	cout << res;
}
```

## C

### 题目链接
https://www.luogu.com.cn/problem/P2853

### 题目大意
求所有牛可以到达的点的个数

### 思路
对每头牛能走到的地方记录，如果某一点被记录了n次（n为牛的个数），那么这个点就是一个所有牛可以走到的点。

### 代码
```cpp
#include <iostream>
#include<cstring>

using namespace std;

const int K = 105, N = 1005, M = 10005;

int a[K];
int h[N], e[M], ne[M], idx;
bool st[N];     //记录某一头牛能走到的点
int num[N];     //记录该点能被几头牛走到

int k,n,m;

void add(int a, int b)
{
	e[idx] = b;
	ne[idx] = h[a];
	h[a] = idx++;
}

void init()
{
	memset(h, -1, sizeof h);
	cin >> k >> n >> m;
	for(int i = 0; i < k; i++)
		cin >> a[i];
	for(int i = 0; i < m; i++)
	{
		int a, b;
		cin >> a >> b;
		add(a, b);
	}
}

void dfs(int u, int fa)
{
	if(st[u]) return;   //如果已经走过该点，就不需要再走一遍了
	st[u] = 1;
	num[u]++;
	for(int i = h[u]; ~i; i=ne[i])
	{
		int j = e[i];
		dfs(j, u);
	}
}

int main()
{
	init();
	
	for(int i = 0; i < k; i++)
	{
		memset(st, 0, sizeof st);
		dfs(a[i], 0);
	}
	
	int res = 0;
	
	for(int i = 1; i <= n; i++)
		if(num[i] == k)
			res++;
	
	cout<<res;
}
```


## D

### 题目链接
https://www.luogu.com.cn/problem/P8604

### 题目大意
给定起点和终点，若失去某一点后无法从起点走到终点，那么称这一点为危险点。求危险点的个数。

### 思路
如果某一个点为危险点，那么从起点走到终点的过程中一定会经过。因此可以dfs遍历所有从起点到终点的路径，若某一点被经过的次数等于路径条数，那么该点就是危险点。

### 代码
```cpp
#include <iostream>
#include <cstring>

using namespace std;

const int N = 1005, M = 2005;

int h[N], e[M * 2], ne[M * 2], idx;
int num[N]; //某点被经过的次数
bool st[N]; //某点是否被经过

int n, m;
int tot, orig, dest;

void add(int u, int v)
{
	e[idx] = v;
	ne[idx] = h[u];
	h[u] = idx++;
}

void dfs(int u)
{
	if(st[u]) return;
	if(u == dest)   //到达终点
	{
		tot++;  //路径条数变化
		for(int i=1; i <= n; i++)   //将该路径下经过的点记入次数
			num[i] += st[i];
		return;
	}
	st[u] = 1;  //在该路径下不能重复经过某一点
	for(int i = h[u]; ~i; i=ne[i])
	{
		int j = e[i];
		dfs(j);
	}
	st[u] = 0;  //走过该点后，就可以再次走该点
}

void init()
{
	memset(h, -1, sizeof h);
	cin >> n >> m;
	for(int i = 0; i < m; i++)
	{
		int u, v;
		cin >> u >>v;
		add(u, v);
		add(v, u);
	}
	cin >> orig >> dest;
}

int main()
{
	init();
	dfs(orig);
	
	int res = 0;
	for(int i = 1; i <= n; i++)
		if(num[i] == tot)
			res++;

	cout << res - 1;
}
```


## E

### 题目链接
https://www.luogu.com.cn/problem/P1443

### 题目大意
求马走到每一个点最少需要几步

### 思路
bfs模板题，注意不要越界

### 代码
```cpp
#include<iostream>
#include<queue>

using namespace std;
using pii = pair<int, int>;

const int N = 405;

int n, m, x, y;
int dist[N][N];

int move_x[8] = {2, 1, -1, -2, -2, -1, 1, 2}, move_y[8] = {-1, -2, -2, -1, 1, 2, 2, 1};

void bfs()
{
	queue<pii> q;
	dist[x][y] = 0;
	q.push({x, y});
	while(!q.empty())
	{
		pii t = q.front();
		q.pop();
		int x = t.first, y = t.second;
		for(int i = 0; i < 8; i++)
		{
			int xx = x + move_x[i], yy = y + move_y[i];
			if(xx < 1 || xx > n) continue;
			if(yy < 1 || yy > m) continue;
			if(dist[xx][yy] != -1) continue;
			dist[xx][yy] = dist[x][y] + 1;
			q.push({xx, yy});
		}
	}
}

void init()
{
	cin >> n >> m >> x >> y;
	for(int i = 1; i <= n; i++)
		for(int j = 1; j <= m; j++)
			dist[i][j] = -1;
}

int main()
{
	init();
	bfs();
	for(int i = 1; i <= n; i++)
	{
		for(int j = 1; j <= m; j++)
		{
			printf("%-5d", dist[i][j]);     //除非你很清楚你在做什么，否则不要将cin/cout和scanf/printf混用
		}
		printf("\n");
	}
}
```



## F

### 题目链接
https://www.luogu.com.cn/problem/P1162

### 题目大意
将封闭图形内部的0变为2

### 思路
先将外围的0变为别的数，再将剩余的0变为2。可以选择任意搜索方式

### 代码
```cpp
#include <iostream>
#include <queue>

using namespace std;
using pii = pair<int, int>;

const int N = 40;

int n;
int a[N][N];

int move_x[4] = {1, 0, -1, 0}, move_y[4] = {0, -1, 0, 1};

void bfs(int x, int y, int color)
{
	queue<pii> q;
	a[x][y] = color;
	q.push({x,y});
	while(!q.empty())
	{
		pii t = q.front();
		q.pop();
		int x = t.first, y = t.second;
		for(int i = 0; i < 4; i++)
		{
			int xx = x + move_x[i], yy = y + move_y[i];
			if(xx < 0 || xx > n+1) continue;
			if(yy < 0 || yy > n+1) continue;
			if(a[xx][yy] != 0) continue;
			a[xx][yy] = color;
			q.push({xx, yy});
		}
	}
}

void init()
{
	cin >> n;
	for(int i = 1; i <= n; i++)
		for(int j = 1; j <= n; j++)
			cin >> a[i][j];
}

int main()
{
	init();
	bfs(0, 0, -1);
	
	for(int i = 1; i <= n; i++)
		for(int j = 1; j <= n; j++)
			if(a[i][j] == 0)
				bfs(i, j, 2);
	
	for(int i = 1; i <= n; i++)
	{
		for(int j = 1; j <= n; j++)
		{
			if(a[i][j] == -1) cout << 0 << ' ';
			else cout << a[i][j] << ' ';
		}
		cout << endl;
	}
}
```


## G

### 题目链接
https://www.luogu.com.cn/problem/P3370

### 题目大意
求不同的字符串的个数

### 思路
首先用字符串哈希将字符串变为数字，将题目转化为求一个数组中有多少个不同的数即可。
均采用自然溢出的哈希方式

### 代码
```cpp
#include <iostream>
#include <algorithm>

using namespace std;
using ull = unsigned long long;

const ull P = 13331, N = 10010, M = 1550;

int n;
ull a[N];
char s[M];

ull get_hash(char str[])
{
	ull res = 0;
	for(int i = 0; str[i]; i++)
		res = res * P + str[i];
	return res;
}

int main()
{
	cin>>n;
	for(int i = 0; i < n; i++)
	{
		cin >> s;
		a[i] = get_hash(s);
	}
	sort(a, a + n);
	
	int res = 1;
	for(int i = 1; i < n; i++)
		if(a[i] != a[i-1])
			res++;
	
	cout<<res;
}
```



## H

### 题目链接
https://www.luogu.com.cn/problem/P2580

### 题目大意
给定一份名单，再给定m组询问，每组询问回答该名字是否在名单中，以及是否已经被点过名。

### 思路
采用字符串哈希将名字转化为数字，由于有多组询问，我们可以将这一组数字以升序方式排序，然后二分查找即可。

### 代码
```cpp
#include <iostream>
#include<algorithm>

using namespace std;
using ull = unsigned long long;

const ull P = 13331, N = 10010, M = 100;

int n, m;
ull a[N];
bool st[N];

char s[M];

ull get_hash(char str[])
{
	ull res = 0;
	for(int i = 0; str[i]; i++)
		res = res * P + str[i];
	return res;
}

int find(int l, int r, ull k)
{
	while(l <= r)
	{
		int mid = (l + r) / 2;
		if(a[mid] == k) return mid;
		else if(a[mid] < k) l = mid +1;
		else r = mid - 1;
	}
	return -1;
}

int main()
{
	cin >> n;
	for(int i = 0; i < n; i++)
	{
		cin >> s;
		a[i] = get_hash(s);
	}
	sort(a, a + n);
	
	cin >> m;
	while(m--)
	{
		cin >> s;
		ull t = get_hash(s);
		int pos = find(0, n-1, t);
		if(pos == -1) 
			cout << "WRONG\n";
		else if(st[pos]) 
			cout << "REPEAT\n";
		else 
			cout << "OK\n", st[pos] = 1;
	}
}
```



## I

### 题目链接
https://www.luogu.com.cn/problem/P1816

### 题目大意
给定一个序列，再给定m组询问，对每组询问回答l-r区间的最小值。

### 思路
st表模板题

### 代码
```cpp
#include <iostream>
#include <cmath>

using namespace std;

const int N = 100010;

int n, m;

int f[N][18];

void init()
{
	for(int j = 1; 1<<j <= n; j++)
		for(int i = 1; i+(1<<j)-1 <= n; i++)
			f[i][j] = min(f[i][j - 1], f[i + (1<<(j-1))][j - 1]);
}

int get_min(int l, int r)
{
	int k = log2(r - l + 1);
	return min(f[l][k], f[r-(1<<k) + 1][k]);
}

int main()
{
	cin >> n >> m;
	for(int i = 1; i <= n; i++)
		cin >> f[i][0];
	
	init();
	
	while(m--)
	{
		int l, r;
		cin >> l >> r;
		cout << get_min(l, r) << ' ';
	}
	
}
```


## J

### 题目链接
https://www.luogu.com.cn/problem/P4392

### 题目大意
给定一组长度为n的序列，输出所有满足以下条件的长度为m的子序列的起始坐标
+ 该子序列最大值减最小值小于等于阈值c

### 思路
用st表维护最大最小值，依次判断序列是否满足条件即可

### 代码
```cpp
#include <iostream>
#include <cmath>

using namespace std;

const int N = 1000010, M = 10010;

int n, m, c;
int fmx[N][14], fmn[N][14];


void init()
{
	for(int j = 1; 1<<j <= m; j++)
		for(int i = 1; i+(1<<j)-1 <= n; i++)
			fmx[i][j] = max(fmx[i][j - 1], fmx[i + (1<<(j-1))][j-1]),
			fmn[i][j] = min(fmn[i][j - 1], fmn[i + (1<<(j-1))][j-1]);
}

int get_max(int l, int r)
{
	int k = log2(r - l + 1);
	return max(fmx[l][k], fmx[r - (1<<k) + 1][k]);
}

int get_min(int l, int r)
{
	int k = log2(r - l + 1);
	return min(fmn[l][k], fmn[r - (1<<k) + 1][k]);
}

int main()
{
	cin >> n >> m >> c;
	for(int i = 1; i <= n; i++)
		cin >> fmx[i][0], fmn[i][0] = fmx[i][0];
	
	init();
	
	bool have_mute = 0;
	for(int i = 1, j = m;j <= n; i++, j++)
	{
		if(get_max(i, j) - get_min(i, j) <= c)
			cout<<i<<'\n', have_mute = 1;
	}
	if(!have_mute)
		cout<<"NONE";
}
```


## K

### 题目链接
https://codeforces.com/problemset/problem/1775/A2

### 题目大意
将一个字符串分成三个字符串a,b,c。使之满足以下条件之一：
+ a<=b && c<=b
+ a>=b && c>=b

### 思路
首先判断字符串除首尾元素外是否有字符a，若有的话，那么字符a一定是字典序最小的，把字符串b设为这个字符a，剩余两部分给a和c即可，一定满足条件2.
若不含a，那么将除首尾元素的部分设为字符串b，这一部分也一定是字典序最大的，剩余首尾元素即是字符串a和c

### 代码
```cpp
#include<iostream>
#include<cstring>

using namespace std;

const int N = 200010;

char s[N];

void solve()
{
	cin >> s;
	int len = strlen(s);
	for(int i = 1; i < len-1; i++)
	{
		if(s[i] == 'a')
		{
			for(int j = 0; j < i; j++) cout << s[j];
			cout << " a ";
			for(int j = i + 1; j < len; j++) cout << s[j];
			cout << '\n';
			return;
		}
	}
	cout << s[0] << ' ';
	for(int i = 1; i < len-1; i++) cout << s[i];
	cout << ' ' << s[len - 1] << '\n';
}

int main()
{
	int t = 1;
	
	cin >> t;
	while(t--)
		solve();
	
	return 0;
}
```


## L

### 题目链接
https://codeforces.com/problemset/problem/1772/C

### 题目大意
用小于等于k的正整数构造一个长度是n的严格上升的序列，使这个序列相邻两数不同的差的个数尽可能多

### 思路
优先以1,2,3……作为差值，直到若当前数与上一数的差值为d时无法满足后续序列严格上升时，将公差改为1.

### 代码
```cpp
#include<iostream>

using namespace std;

void solve()
{
	int k, n;
	cin >> k >> n;
	for(int i = 1, d = 0, elem = 1; i <= k; i++)
	{
		cout << elem << ' ';
		d++;
		if(n -(elem+d) >= k-i-1)
			elem += d;
		else
			elem += 1;
	}
	cout << '\n';
}

int main()
{
	int t;
	cin >> t;
	while(t--)
		solve();
}
```


## M

### 题目链接
https://codeforces.com/problemset/problem/1741/B

### 题目大意
构造一个长度为n的排列，满足以下要求：
+ a[i]!=i
+ 对于a[i]，其相邻的数中至少有一个与其只差一

### 思路
当n等于2时，序列一定为 2,1
当n等于3时，序列一定不存在
当n大于等于4时，可以以如下方式构造序列，一定满足条件：
n-1,n,1,2,3……,n-2

### 代码
```cpp
#include<iostream>

using namespace std;

void solve()
{
	int n;
	cin>>n;
	
	if(n == 2)
		cout << "2 1\n";
	else if(n == 3)
		cout << "-1\n";
	else
	{
		cout << n-1 << " " << n << " ";
		for(int i = 1; i <= n-2; i++)
			cout << i << " ";
		cout << '\n';
	}
}

int main()
{
	int t = 1;
	
	cin>>t;
	while(t--)
		solve();
}
```

## N

### 题目链接
https://codeforces.com/problemset/problem/1741/A

### 题目大意
比较两个尺码的大小，其中：
+ 含有L的>含有M的>含有S的
+ 含有S的字符串中X越多，其尺码越小
+ 含有L的字符串中X越多，其尺码越大

### 思路
考虑字符串长度为len，将含L的len设为正数，含S的len设为负数，则含L字符串越长其大小越大，含S字符串越长其大小越小，满足条件。

### 代码
```cpp
#include <iostream>
#include <cstring>

using namespace std;

const int N=55;

char a[N], b[N];

int get_size(char s[])
{
	int len = strlen(s);
	char last_char = s[len - 1];
	if(last_char == 'M') return 0;
	else if(last_char == 'L') return len;
	else return -len;
}

void solve()
{
	cin >> a >> b;
	int s1 = get_size(a), s2 = get_size(b);
	if(s1 < s2) cout << "<\n";
	else if(s1 > s2) cout << ">\n";
	else cout << "=\n";
}

int main()
{
	int t=1;
	
	cin>>t;
	while(t--)
		solve();
}
```