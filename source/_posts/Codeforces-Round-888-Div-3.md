---
title: Codeforces Round 888 (Div. 3)
date: 2023-07-26 14:25:18
tags:
  - [codeforces]
categories: 题解
---

Codeforces Round 888 A-G, F和G有思路讲解

<!-- more -->

## A. Escalator Conversations

```cpp
const int N = 3e5+10;
int a[N];
int n,m,k,h;
 
void solve(){
	cin>>n>>m>>k>>h;
	set<int> se;
	while(m--)
	{
		se.insert(h+k*m);
		se.insert(h-k*m);
	}
	int res=0;
	for(int i=0;i<n;i++)
	{
		int x;
		cin>>x;
		if(se.count(x)&&x!=h)
		{
			res++;
		}
	}
	cout<<res<<'\n';
	
}
```



## B. Parity Sort

```cpp
const int N = 3e5+10;
 
int n, k;
int a[N];
bool st[N];
 
void solve(){
	cin>>n;
	vector<int> odd1,even1;
	queue<int> odd,even;
	for(int i=0;i<n;i++)
	{
		int x;
		cin>>x;
		if(x&1)
		{
			st[i]=1;
			odd1.push_back(x);
		}
		else
		{
			st[i]=0;
			even1.push_back(x);
		}
	}
	sort(even1.begin(),even1.end());
	sort(odd1.begin(),odd1.end());
	
	for(auto i:odd1)
	{
		odd.push(i);
	}
	for(auto i:even1)
	{
		even.push(i);
	}
	bool flag=1;
	for(int i=0;i<n;i++)
	{
		if(st[i])
		{
			a[i]=odd.front();
			odd.pop();
		}
		else
		{
			a[i]=even.front();
			even.pop();
		}
		if(i!=0&&a[i]<a[i-1])
		{
			flag=0;
			break;
		}
	}
	if(flag) cout<<"YES\n";
	else cout<<"NO\n";
}
```



## C. Tiles Comeback

```cpp
const int N = 3e5+10;
 
int n, k;
int a[N];
 
void solve(){
	cin>>n>>k;
	for(int i=1; i<=n; i++) cin>>a[i];
	int cnt1 = 0, cnt2 = 0;
	int p1 = -1, p2 = -1;
	for(int i=1; i<=n; i++){
		if(a[i] == a[1]){
			if(++cnt1 == k){
				p1 = i;
				break;
			}
		}
	}
	for(int i=n; i>=1; i--){
		if(a[i] == a[n]){
			if(++cnt2 == k){
				p2 = i;
				break;
			}
		}
	}
	if(p1==-1||p2==-1){
		cout<<"NO\n"; return;
	}
	if(a[1] == a[n]){
		cout<<"YES\n"; return;
	}
	if(p1<p2){
		cout<<"YES\n"; return;
	}
	if(p1>p2){
		cout<<"NO\n"; return;
	}
}
```



## D. Prefix Permutation Sums

```cpp
const int N = 3e5+10;
 
int n, k;
int a[N],b[N];
bool st[N];
 
void solve(){
	cin>>n;
	if(n==2)
	{
		int x;
		cin>>x;
		if(x==1||x==2||x==3) cout<<"YES\n";
		else cout<<"NO\n";
		return;
	}
	int extra=-1;
	set<int> se;
	bool flag=1;
	for(int i=1;i<=n-1;i++)
	{
		cin>>b[i];
		if(se.count(b[i]-b[i-1])||b[i]-b[i-1]>n)
		{
			if(extra!=-1)
			{
				flag=0;
			}
			extra=b[i]-b[i-1];
			if(extra==1||extra==2)
			{
				flag=0;
			}
		}
		else se.insert(b[i]-b[i-1]);
	}
	if(flag==0)
	{
		cout<<"NO\n";
		return;
	}
	if(extra==-1)
	{
		cout<<"YES\n";
		return;
	}
	int res=0;
	for(int i=1;i<=n;i++)
	{
		if(se.count(i)==0)
		{
			res+=i;
		}
	}
	if(res==extra) cout<<"YES\n";
	else cout<<"NO\n";
}
```



## E. Nastya and Potions

```cpp
const int N = 2e5+10,M=2*N;
 
int n, k;
int h[N],e[M],ne[M],idx;
int money[N];
bool have[N];
int ans[N];
 
void add(int a,int b)
{
	e[idx]=b,ne[idx]=h[a],h[a]=idx++;
}
 
int dfs(int u)
{
	if(have[u]) return 0;
	int res=0;
	bool flag=0;
	for(int i=h[u];~i;i=ne[i])
	{
		flag=1;
		int j=e[i];
		if(ans[j]!=-1) res+=ans[j];
		else
		{
			ans[j]=dfs(j);
			res+=ans[j];
		}
	}
	if(!flag) return money[u];
	return min(res,money[u]);
}
 
void solve(){
	cin>>n>>k;
	memset(h,-1,sizeof(int)*(n+1));
	memset(have,0,sizeof(int)*(n+1));
	memset(ans,-1,sizeof(int)*(n+1));
	idx=0;
	
	for(int i=1;i<=n;i++) cin>>money[i];
	
	while(k--)
	{
		int x;
		cin>>x;
		have[x]=true;
		ans[x]=0;
	}
	
	for(int i=1;i<=n;i++)
	{
		int x;
		cin>>x;
		while(x--)
		{
			int y;
			cin>>y;
			add(i,y);
		}
		if(x==0&&!have[i]) ans[i]=money[i];
	}
	
	for(int i=1;i<=n;i++)
	{
		if(ans[i]!=-1) cout<<ans[i]<<' ';
		else cout<<dfs(i)<<' ';
	}
	cout<<'\n';
	
}
```





## F. Lisa and the Martians

### 思路

对于ai与aj的每一位来说，若同为0或同为1，那么(ai^x)&(aj^x)对应的那一位可以取为1，否则为0。因此，题目转化为找到两个数ai和aj，它们拥有最长的相同前缀，因此可以使用字典树解决。本题与字典树板子题最大异或对基本相同。

### 代码

```cpp
const int N = 2e5+10, M = 4e6+10;
 
int n, k;
int a[N], son[M][2], idx, id[M];
int ra, rb, rx, res = -1; 
 
void insert(int x, int idd){
	int p = 0;
	for(int i=k-1; i>=0; i--){
		int& s = son[p][x>>i&1];
		if(!s) s = ++idx;
		p = s;
	}
	id[p] = idd;
}
 
void search(int x, int iddd){
	int p = 0, rxx = 0, re = 0;
	for(int i=k-1; i>=0; i--){
		int s = x >> i & 1;
		if(son[p][s]){
			re+=(1<<i);
			p = son[p][s];
			rxx+=((s==0)<<i);
		}
		else{
			p = son[p][!s];
		}
	}
	
	int idd = id[p];
	
	if(re>res){
		res = re, ra = idd, rb = iddd, rx = rxx;
	}
}
 
 
void solve(){
	cin>>n>>k;
	res = -1;
	idx = 0;
	for(int i=1; i<=n; i++) cin>>a[i];
	insert(a[1], 1);
	for(int i=2; i<=n; i++){
		search(a[i], i);
		insert(a[i], i);
	}
	cout<<ra<<' '<<rb<<' '<<rx<<'\n';
	for(int i=0; i<=idx; i++){
		son[i][0] = son[i][1] = 0;
	}
}
```



## G. Vlad and the Mountains

### 思路

我们发现，从山峰A到山峰B所需要消耗的体力的最大值就是从A到B路径中最高的山峰C的高度减去山峰A的高度，这一点不难证明。那么问题就转化为查找从A到B所有路径中的最高山峰高度的最小值。那么我们可以使用kruskal+lca来实现。首先将边的权值设定为边的两个顶点山峰中高度的最大值，然后建立最小生成树，所有路径都应在该树上。然后通过lca得到A到B路径上的最大值。最后若e>=lca(A, B) - h[A]，那么就可以到达。注意，题中的图不一定联通，因此需要判断给定两点是否联通。

### 代码

```cpp
int n, m;
struct edge{
    int u, v, w;
    bool operator<(edge r){
        return w<r.w;
    }
};
 
edge edges[M];
 
int p[N],p2[N];
 
int find(int x){
    if(p[x] != x) p[x] = find(p[x]);
    return p[x];
}
 
int find2(int x){
    return p2[x];
}
 
int h[N], e[M], ne[M], w[M], idx;
int depth[N], fa[N][18], d[N][18];
int hh[N];
 
 
void add(int a, int b, int c){
    e[idx] = b, ne[idx] = h[a], w[idx] = c, h[a] = idx++;
}
 
void bfs(int t){
    depth[0] = 0, depth[t] = 1;
    queue<int> q;
    q.push(t);
    while(q.size()){
        int u = q.front();
        p2[u] = t;
        q.pop();
        for(int i=h[u]; ~i; i=ne[i]){
            int j=e[i];
            // cout<<"j:"<<j<<'\n';
            if(depth[j]>depth[u]+1){
                depth[j]=depth[u]+1;
                q.push(j);
                fa[j][0] = u;
                d[j][0] = w[i];
                for(int k=1; k<=17; k++){
                    int anc = fa[j][k-1];
                    fa[j][k] = fa[anc][k-1];
                    d[j][k] = max(d[j][k-1], d[anc][k-1]);
                }
            }
        }
    }
}
 
int lca(int a, int b){
    int mx = 0;
    if(depth[a]<depth[b]) swap(a, b);
    for(int k=16; k>=0; k--){
        if(depth[fa[a][k]]>=depth[b]){
            mx = max(mx, d[a][k]);
            a = fa[a][k];
        }
    }
 
    if(a==b){
        return mx;
    }
 
    if(a!=b){
        for(int k=17; k>=0; k--){
            if(fa[a][k]!=fa[b][k]){
                mx = max({mx, d[a][k], d[b][k]});
                a = fa[a][k];
                b = fa[b][k];
            }
        }
    }
    mx = max({mx, d[a][0], d[b][0]});
    return mx;
}
 
void solve() {
    idx = 0;
    cin>>n>>m;
    memset(h, -1, sizeof(int)*(n+1));
	for(int i=0; i<=n; i++){
		for(int j=0; j<18; j++){
			fa[i][j] = d[i][j] = 0;
		}
	}
    for(int i=1; i<=n; i++) p[i] = i, p2[i] = i;
    for(int i=1; i<=n; i++){
        cin>>hh[i];
    }
    for(int i=0; i<m; i++){
        int a, b;
        cin>>a>>b;
        edges[i] = {a, b, max(hh[a], hh[b])};
    }
    sort(edges, edges+m);
    for(int i = 0; i<m; i++){
        int pa = find(edges[i].u), pb = find(edges[i].v);
        if(pa!=pb){
            p[pa] = pb;
            add(edges[i].u, edges[i].v, edges[i].w);
            add(edges[i].v, edges[i].u, edges[i].w);
        }
    }
 
    memset(depth, 0x3f, sizeof(int)*(n+1));
    for(int i=1; i<=n; i++){
        if(p2[i] == i){
            bfs(i);
        }
    }
 
    int q;
    cin>>q;
    while(q--){
        int u, v, e;
        cin>>u>>v>>e;
        if(find2(u)!=find2(v)){
            cout<<"No\n";
            continue;
        }
        if(e>=lca(u, v)-hh[u]){
            cout<<"Yes\n";
        }
        else{
            cout<<"No\n";
        }
    }
    cout<<'\n';
}
```

