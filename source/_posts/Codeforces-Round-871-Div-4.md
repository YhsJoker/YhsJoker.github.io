---
title: Codeforces Round 871 (Div. 4)
date: 2023-05-21 21:05:39
tags:
  - [codeforces]
categories: 题解
description: Codeforces Round 871 A-H
---

## A. Love Story

### 思路

遍历判断即可

### 代码

```cpp
string s = "codeforces";
 
void solve(){
	string str;
	cin>>str;
	int res = 0;
	for(int i=0; i<s.size(); i++){
		if(s[i]!=str[i]) res++;
	}
	cout<<res<<'\n';
	
}
```



## B. Blank Space

### 思路

经典的计算连续个数的最大值

### 代码

```cpp
int n, a[N];
 
void solve(){
	cin>>n;
	for(int i=0; i<n; i++) cin>>a[i];
	int res = 0, k = 0;
	for(int i=0; i<n; i++){
		if(a[i]) k = 0;
		else{
			res = max(res, ++k);
		}
	}
	cout<<res<<'\n';
}
```



## C. Mr. Perfectly Fine

### 思路

找到11的最小值，10和01的最小值，计算取哪个即可。如果不存在11并且不同时存在01和10，则失败

```cpp
int n, a[N];
string s[N];
 
void solve(){
	cin>>n;
	int res = 2e10;
	
	int m1 = 2e10, m2 = 2e10;
	for(int i=0; i<n; i++){
		cin>>a[i]>>s[i];
		if(s[i] == "11") res = min(res, a[i]);
		if(s[i] == "10") m1 = min(m1, a[i]);
		if(s[i] == "01") m2 = min(m2, a[i]);
	}
	
	res = min(res, m1+m2);
	if(res == 2e10) cout<<-1<<'\n';
	else cout<<res<<'\n';
}
```



## D. Gold Rush

### 思路

判断n能否通过乘以任意个1/3和2/3得到m，只要求出n和m差的3的因子个数和2的因子个数即可。

如果n无法通过除以有限个2和3得到m，或者除以的2的因子个数大于3的，则不可以，其余情况均可。

### 代码

```cpp
int n, m;
 
void solve(){
	int n, m;
	cin>>n>>m;
	int n3 = 0, m3 = 0;
	while(n%3==0) n3++, n/=3;
	while(m%3==0) m3++, m/=3;
	if(n3<m3) {cout<<"NO\n"; return;}
	int d = n3-m3;
	if(m%n!=0) {cout<<"NO\n"; return;}
	int dv = m/n, n2 = 0;
	while(dv%2==0) dv/=2, n2++;
	if(dv!=1) {cout<<"NO\n"; return;}
	if(n2>d){cout<<"NO\n";}
	else cout<<"YES\n";
}	
```



## E. The Lakes

### 思路

简单的Flood Fill算法

### 代码

```cpp
int n, m;
int a[1005][1005];
 
int dfs(int x, int y){
	if(a[x][y] == 0) return 0;
	int sum = a[x][y];
	a[x][y] = 0;
	sum+=dfs(x-1, y)+dfs(x+1, y)+dfs(x, y-1)+dfs(x, y+1);
	return sum;
}
 
void solve(){
	cin>>n>>m;
	for(int i=0; i<=n+1; i++){
		for(int j=0; j<=m+1; j++){
			a[i][j] = 0;
		}
	}
	for(int i=1; i<=n; i++){
		for(int j=1; j<=m; j++){
			cin>>a[i][j];
		}
	}
	
	int res = 0;
	
	for(int i=1; i<=n; i++){
		for(int j=1; j<=m; j++){
			res = max(res, dfs(i, j));
		}
	}
	cout<<res<<'\n';
}	
```



## F. Forever Winter

### 思路

判断该图是否有如下性质：

1. x*(y+1) == m
2. 度为x的点的个数>=1
3. 度为y+1的点的个数>=x
4. 度为1的点的个数>=x*y

### 代码

```cpp
int in[205], nu[1005];
 
int n, m;
 
void solve(){
	cin>>n>>m;
	memset(in, 0, sizeof in);
	memset(nu, 0, sizeof nu);
	for(int i=0; i<m; i++){
		int a, b; cin>>a>>b;
		in[a]++, in[b]++;
	}
	
	for(int i=1; i<=n; i++){
		nu[in[i]]++;
	}
	
	for(int x = 1; x<=m; x++){
		if(m%x) continue;
		int y = m/x - 1;
		if(nu[x]>=1&&nu[y+1]>=x&&nu[1]>=x*y){
			cout<<x<<' '<<y<<'\n';
			return;
		}
		
	}
}	
```



## G. Hits Different

### 思路

预处理出斜向右下的前缀和即可

### 代码

```cpp
int f[2025][2025];
int s[2025][2025];
 
void init(){
	int x = 1, r = 1, c = 1;
	while(x<=1e6){
		f[r][c] = x*x;
		if(++c>r) r++, c = 1;
		x++;
	}
	for(int k=1; k<=2023; k++){
		for(int i=k, j = 1; i<=2023; i++, j++){
			s[i][j] = s[i-1][j-1] + f[i][j];
		}
	}
}
 
const int N = 2e5+10, P = 1e9+7;
 
int n;
 
void solve(){
	cin>>n;
	int res = 0;
	int sum = 0, r, c;
	for(int i=0; i<=2022; i++){
		sum+=i;
		if(sum+i+1>=n){
			r = i+1;
			c = n - sum;
			break;
		}
	}
	for(int i=r; i>=c; i--){
		res+=s[i][c];
	}
	cout<<res<<'\n';
}	
```



## H. Don't Blame Me

### 思路

经典的状态压缩DP

f\[i]\[j]表示在前i个数中，位与和为j的子序列的个数。

f\[i]\[j]=sum(f\[i-1]\[k]), 其中k的条件是a[i]&k == j

### 代码

```cpp
int n, k, a[N];
int f[N][1<<6];
 
int get(int x){
	int sum = 0;
	for(int i=0; i<6; i++)
		if((x>>i)&1)
			sum++;
	return sum;
}
 
void solve(){
	cin>>n>>k;
	for(int i=1; i<=n; i++) cin>>a[i];
	for(int i=1; i<=n; i++){
		for(int j=0; j<(1<<6); j++){
			f[i][j] = 0;
		}
	}
	for(int i=1; i<=n; i++){
		f[i][a[i]] = 1;
		for(int j=0; j<(1<<6); j++){
			f[i][j] = (f[i][j] + f[i-1][j])%P;
			for(int k=0; k<(1<<6); k++){
				if((a[i]&k) != j) continue;
				f[i][j] = (f[i][j] + f[i-1][k])%P;
			}
		}
	}
	int res = 0;
	for(int i=0; i<(1<<6); i++){
		if(get(i)!=k) continue;
		res = (res + f[n][i])%P;
	}
	cout<<res<<'\n';
}	
```

