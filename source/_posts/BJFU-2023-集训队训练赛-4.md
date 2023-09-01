---
title: BJFU-2023-集训队训练赛-4
date: 2023-01-13 21:04:47
tags:
    - [集训队训练赛]
categories: 题解
description: BJFU集训队寒假训练题目（部分）
---

## E

### 题目链接
https://codeforces.com/gym/103427/problem/J

### 题目大意
给定一个密码锁，问从abcd移动到efgh最少需要几步，每次可以转连续的齿轮，但每次只能走一步

### 思路
从abcd到efgh，其实转动的就是差值，相当于从0000走到一个状态C，状态C就是efgh-abcd的差值。因此我们可以从0000出发，跑bfs，得到从0000到所有状态的最短路，最后根据询问查表即可。

### 代码
```cpp
map<string,int> mp;
queue<string> q;

string s1,s2;

void init()
{
	q.push("0000");
	mp["0000"]=0;
	while(q.size())
	{
		string s=q.front();
		int step=mp[s];
		q.pop();
		for(int len=1;len<=4;len++)     //每次转动几个齿轮
		{
			for(int i=0,j=i+len-1;j<4;i++,j++)  //齿轮边界
			{
				string s1=s,s2=s;
				for(int k=i;k<=j;k++)   //转动齿轮，一个向下转，一个向上转
				{
					s1[k]=(s1[k]-'0'+1)%10+'0';
					s2[k]=(s2[k]-'0'+9)%10+'0';
				}
				if(!mp.count(s1)) q.push(s1),mp[s1]=step+1;
				if(!mp.count(s2)) q.push(s2),mp[s2]=step+1;
			}
		}
	}
}
void input()
{
	cin>>s1>>s2;
}

void solve()
{
	input();
	string s="0000";
    
	for(int i=0;i<4;i++)
		s[i]=(s2[i]-s1[i]+10)%10+'0';

	cout<<mp[s]<<'\n';
}
```