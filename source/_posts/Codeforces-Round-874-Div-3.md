---
title: Codeforces Round 874(Div.3)
date: 2023-05-20 11:01:02
tags:
  - [codeforces]
categories: 题解
description: Codeforces Round 874 A-G
---

## A. Musical Puzzle

### 思路

找到所有互不相同的长度为2的子串的个数。

### 代码

```cpp
int n;
string s;
 
void solve(){
	cin>>n>>s;
	set<string> st;
	for(int i=0; i<s.size()-1; i++){
		st.insert(s.substr(i, 2));
	}
	cout<<st.size()<<'\n';
	
}
```



## B. Restore the Weather

### 思路

可以推测出排序后的a，b数组一定满足需求。因此直接排序后找到与b对应的a的原始坐标即可。

### 代码

```cpp
int n, k;
pair<int, int> a[N], b[N];
int res[N];
 
void solve(){
	cin>>n>>k;
	for(int i=0; i<n; i++){
		int x; cin>>x; a[i] = {x, i};
	}
	for(int i=0; i<n; i++){
		int x; cin>>x; b[i] = {x, i};
	}
	sort(a, a+n);
	sort(b, b+n);
	for(int i=0; i<n; i++){
		res[a[i].second] = b[i].first;
	}
	for(int i=0; i<n; i++){
		cout<<res[i]<<' ';
	}
	cout<<'\n';
}
```



## C. Vlad Building Beautiful Array

### 思路

令最小的数为min_elem，我们可以发现：

1. 当min_elem为奇数时，一定满足条件。因为如果a[i]为偶数，则可以让其减去min_elem使之变为奇数。
2. 当min_elem为偶数时，如果a中出现奇数，不能满足条件。如果a中全为偶数，则可以。因为当a中出现奇数时，最小的那个奇数无法通过减去某个奇数变为严格大于零的偶数。

## 代码

```cpp
int n;
int a[N];
 
void solve(){
	cin>>n;
	for(int i=0; i<n; i++) cin>>a[i];
	int mn_elem = *min_element(a, a+n);
	if(mn_elem&1){
		cout<<"YES\n";
	}
	else{
		for(int i=0; i<n; i++){
			if(a[i]&1){
				cout<<"NO\n";
				return;
			}
		}
		cout<<"YES\n";
	}
}
```



## D. Flipper

### 思路

分为三种情况：

1. 最大的数在第一位。我们发现最大的数一定无法出现在更改后的第一位，因此我们假定次大的数为最大的数。
2. 最大的数的位置pos在[2, n-1]中。我们令[l, r]为翻转的序列，我们发现当r = pos-1时可以使最大的数出现在第一位，然后考虑l的值。可以从r-1处开始向前枚举，找到翻转后的最大值。
3. 最大的数的位置在最后一位。我们发现会出现两种情况，既可以翻转[l, n-1]，也可以翻转[l, n]都可以使得最大的数出现在第一位，找规律即可。

### 代码

```cpp
int n, a[N];
 
void solve(){
	cin>>n;
	for(int i=0; i<n; i++) cin>>a[i];
	if(n==1){
		cout<<a[0]<<'\n';
		return;
	}
	if(n==2){
		cout<<a[1]<<' '<<a[0]<<'\n';
		return;
	}
	int pos = find(a, a+n, n) - a;
	if(pos == 0)
		pos = find(a, a+n, n-1) - a;
	int l = pos - 1, r = pos - 1;
	for(int i=r; i>=1; i--){
		if(a[i-1]>a[0]){
			l = i - 1;
		}
		else{
			break;
		}
	}
	if(pos == n-1 && a[0]>a[pos-1]){
		l = pos, r = pos - 1;
		for(int i=pos; i>=1; i--){
			if(a[i-1]>a[0]) l = i - 1;
			else break;
		}
	}
	for(int i=pos; i<n; i++) cout<<a[i]<<' ';
	for(int i=r; i>=l; i--) cout<<a[i]<<' ';
	for(int i=0; i<l; i++) cout<<a[i]<<' ';
	cout<<'\n';
}
```



## E. Round Dance

### 思路

首先判断最多有几个环：

+ 令每个数都在只含有自己的集合中，如果某两个数是相邻的关系，那么把他们所在的两个集合合并，表示他们必须在一个环内。最终判断剩余几个集合即可。

然后判断最少有几个环：

+ 将相邻的数连边，我们发现最终的结果只可能是一条链或一个完整的环。两条链之间可以组合成一条更长的链，并且链能保证形成环。于是题目就转化成了求链的个数。一条链会贡献两个度数为1的点，环上的所有点度数均为2，因此可以通过计算度数为1的点的个数来求解链的个数，进而求解最多能合并几个集合，得出最少有几个环。

### 代码

```cpp
int n, a[N];
set<int> d[N];
int p[N];
 
int find(int x){
	if(p[x] != x) p[x] = find(p[x]);
	return p[x];
}
 
void solve(){
	cin>>n;
	for(int i=1; i<=n; i++){
		p[i] = i;
		d[i].clear();
	}
	
	int mn = 0, mx = n;
	
	for(int i=1; i<=n; i++){
		cin>>a[i];
		d[i].insert(a[i]);
		d[a[i]].insert(i);
		if(find(i)!=find(a[i])){
			mx--;
			p[find(i)] = find(a[i]);
		}
	}
	
	int nd = 0;
	
	for(int i=1; i<=n; i++){
		if(d[i].size()==1) nd++;
	}
	
	mn = mx - max(0ll, (nd - 2) / 2);
	cout<<mn<<' '<<mx<<'\n';
}
```



## F. Ira and Flamenco

### 思路

将题意简化后就是要求满足以下条件的集合的个数

+ 大小为m

+ 这m个数是连续的

因此我们可以先将数组中每个数的个数记录，然后去重排序，那么新得到的序列记为数组b。

当b中的某个区间[l, r]满足以下性质的时候，这一段就要计算到贡献中：

+ b[r] - b[l] == r - l
+ r - l + 1 == m

计算贡献的方法就是将l到r中每个数的个数乘起来即可。



接下来考虑优化，我们可以令mul[l, r] = num[b[l]] * num[b[l+1]] ... * num[b[r]]，num表示该数出现的个数。

那么如果[l+1, r+1]也满足性质的话，mul[l+1, r+1] = mul[l, r] / num[b[l]] * num[b[r+1]]，这样就可以将时间复杂度优化为O(n)。



### 代码

```cpp
int n, m;
 
int qmi(int a, int b, int p){
	int res = 1;
	while(b){
		if(b&1) res = res * a % p;
		b>>=1;
		a = a * a % p;
	}
	return res;
}
 
void solve(){
	vector<int> v;
	map<int, int> mp;
	cin>>n>>m;
	for(int i=1; i<=n; i++){
		int x; cin>>x; v.push_back(x);
		mp[x]++;
	}
	sort(v.begin(), v.end());
	v.erase(unique(v.begin(), v.end()), v.end());
	
	if(m == 1){
		cout<<n<<'\n';
		return;
	}
	
	int mul = mp[v[0]];
	int res = 0;
	int len = 1;
	
	for(int i=1; i<v.size(); i++){
		if(v[i]-1!=v[i-1]){
			mul = mp[v[i]], len = 1;
			continue;
		}
		len++;
		mul = mul * mp[v[i]] % P;
		if(len == m){
			res = (res + mul) % P;
			//cout<<"!!"<<res<<'\n';
			mul = mul * qmi(mp[v[i-m+1]], P-2, P) % P;
			len--;
		}
	}
	
	cout<<res<<'\n';
}
```



## G. Ksyusha and Chinchilla

### 思路

以任意一点为根构造一棵树，遍历该树。DFS回溯的过程中如果某一点所有的子树的点数和为2，那么就和该点组成一个branch，然后减掉这个branch。如果点数和为1或0，那么就和该点组合起来，继续向上回溯。如果和大于3，就是无解的。



### 代码

```cpp
int n;
int h[N], e[M], ne[M], id[M], idx;
 
void add(int a, int b, int c){
	e[idx] = b, id[idx] = c, ne[idx] = h[a], h[a] = idx++;
}
 
bool ok = 1;
vector<int> res;
int dfs(int u, int fa, int fid){
	if(!ok) return 0;
	
	int sum = 0;
	
	for(int i=h[u]; ~i; i=ne[i]){
		int j = e[i];
		if(j == fa) continue;
		sum+=dfs(j, u, id[i]);
	}
	
	if(sum>2){
		ok = 0; return 0;
	}
	if(sum == 2){
		if(fid) res.push_back(fid);
		return 0;
	}
	return sum+1;
}
 
void solve(){
	cin>>n;
	memset(h, -1, sizeof(int) * (n+1));
	idx = 0;
	for(int i=1; i<n; i++){
		int a, b; cin>>a>>b;
		add(a, b, i);
		add(b, a, i);
	}
	
	ok = 1;
	res.clear();
	int rem = dfs(1, 0, 0);
	
	if(ok && !rem){
		cout<<res.size()<<'\n';
		for(auto e:res){
			cout<<e<<' ';
		}
		cout<<'\n';
	}
	else{
		cout<<-1<<'\n';
	}
	
}
```

