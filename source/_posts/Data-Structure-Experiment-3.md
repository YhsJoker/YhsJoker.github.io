---
title: 数据结构实验三
date: 2023-11-17 00:01:11
tags:
  - [数据结构]
  - [C++]
categories: 作业
description: 数据结构实验三作业，发布在头歌平台，共计八题
---

## 第1关：基于栈的中缀算术表达式求值

### 代码

```cpp
 #include<iostream>
#include<fstream>
#include<string.h>
using namespace std;
#define MAXSIZE 2000

//- - - - - 串的堆式顺序存储结构- - - - - 
typedef struct
{   
   char *ch;				//若是非空串，则按串长分配存储区，否则ch为NULL   
   int length;			//串的当前长度   
}HString; 

int IndexBF(HString S,HString T,int pos)
{//返回模式T在主串S中第pos个字符开始第一次出现的位置。若不存在，则返回值为0 
 //其中，T非空，1≤pos≤StrLength(S) 
   for(int i = pos - 1; i < S.length - T.length + 1; i++){
      bool is_same = 1;
      for(int j = 0; j < T.length; j++){
         if(S.ch[i + j] != T.ch[j]){
            is_same = 0;
            break;
         }
      }
      if(is_same) return i + 1;
   }
   return 0;
} 


bool VirusDetection(HString Virus,HString Person)
{//判断是否匹配，如果可以，返回true，否则返回false 
//模式匹配算法调用Index_BF函数 
   for(int i = 0; i < Virus.length; i++){
      if(IndexBF(Person, Virus, 1)) return true;
      char c = Virus.ch[0];
      memmove(Virus.ch, Virus.ch + 1, Virus.length - 1);
      Virus.ch[Virus.length - 1] = c;
   }
   return false;
}
```



## 第1关 基于BF算法的病毒感染检测

### 代码

```cpp
#include<iostream>
#include<cstring>
#include<stdlib.h>
#include<regex>
using namespace std;


#define MAXLEN 5000			//串的最大长度
typedef struct{   
	char *ch;			//存储串的一维数组
	int length;				//串的当前长度   
}HString;


void InputRule(HString ip[],int n)
{//输入n条规则，并将其中的n个ip地址存放到ip数组 
	string pattern(R"(\d+.\d+.\d+.\d+)");
	regex r(pattern);
	
	for(int i = 0; i < n; i++){
		ip[i].ch = new char[MAXLEN];
		string pro;
		getline(cin, pro);
		
		smatch result;
		regex_search(pro, result, r);
		string s_ip = result[0];
		strcpy(ip[i].ch, s_ip.c_str());
		ip[i].length = s_ip.size();
	}
	
}

void InputLog(HString &log,int m)
{//输入m条日志，并合并存放到log
   delete log.ch;
   log.ch = new char[10000];
	for(int i = 0; i < m; i++){
		string str;
		getline(cin, str);
		strcat(log.ch, str.c_str());
	}
	log.length = strlen(log.ch);
}

int IndexBF(HString S, HString T)
{//简单模式匹配算法,S为主串(目标串)，T为子串(模式串)。
	//匹配成功返回主串中所含子串第一次出现的位置，否则返回-1。
	for(int i = 0; i < S.length - T.length + 1; i++){
		bool is_same = 1;
		for(int j = 0; j < T.length; j++){
			if(S.ch[i + j] != T.ch[j]){
				is_same = 0;
				break;
			}
		}
		if(is_same) return i;
	}
	return -1;
}
```



## 第2关 基于BF算法的网络入侵检测

### 代码

```cpp
#include<iostream>
#include<cstring>
#include<stdlib.h>
#include<regex>
using namespace std;


#define MAXLEN 5000			//串的最大长度
typedef struct{   
	char *ch;			//存储串的一维数组
	int length;				//串的当前长度   
}HString;


void InputRule(HString ip[],int n)
{//输入n条规则，并将其中的n个ip地址存放到ip数组 
	string pattern(R"(\d+.\d+.\d+.\d+)");
	regex r(pattern);
	
	for(int i = 0; i < n; i++){
		ip[i].ch = new char[MAXLEN];
		string pro;
		getline(cin, pro);
		
		smatch result;
		regex_search(pro, result, r);
		string s_ip = result[0];
		strcpy(ip[i].ch, s_ip.c_str());
		ip[i].length = s_ip.size();
	}
	
}

void InputLog(HString &log,int m)
{//输入m条日志，并合并存放到log
   delete log.ch;
   log.ch = new char[10000];
	for(int i = 0; i < m; i++){
		string str;
		getline(cin, str);
		strcat(log.ch, str.c_str());
	}
	log.length = strlen(log.ch);
}

int IndexBF(HString S, HString T)
{//简单模式匹配算法,S为主串(目标串)，T为子串(模式串)。
	//匹配成功返回主串中所含子串第一次出现的位置，否则返回-1。
	for(int i = 0; i < S.length - T.length + 1; i++){
		bool is_same = 1;
		for(int j = 0; j < T.length; j++){
			if(S.ch[i + j] != T.ch[j]){
				is_same = 0;
				break;
			}
		}
		if(is_same) return i;
	}
	return -1;
}
```



## 第3关 基于KMP算法的网络入侵检测

### 代码

```cpp
#include "iostream"
#include "cstring"
#include<stdlib.h>
#include<regex>
using namespace std;


#define MAXLEN 5000			//串的最大长度
typedef struct{   
	char *ch;			//存储串的一维数组
	int length;				//串的当前长度   
}HString;


void InputRule(HString ip[],int n)
{//输入n条规则，并将其中的n个ip地址存放到ip数组 
	string pattern(R"(\d+.\d+.\d+.\d+)");
	regex r(pattern);
	
	for(int i = 0; i < n; i++){
		ip[i].ch = new char[MAXLEN];
		string pro;
		getline(cin, pro);
		
		smatch result;
		regex_search(pro, result, r);
		string s_ip = result[0];
		strcpy(ip[i].ch, s_ip.c_str());
		ip[i].length = s_ip.size();
	}
}

void InputLog(HString &log,int m)
{//输入m条日志，并合并存放到log，返回log的length
	for(int i = 0; i < m; i++){
		string str;
		getline(cin, str);
		strcat(log.ch, str.c_str());
	}
	log.length = strlen(log.ch);
}

void GetNext(HString pattern,int* next)
{//求模式串pattern的next函数值并存入数组next
	next[0] = -1;
	char* p = pattern.ch;
	for (int i = 1, j = -1; i < pattern.length; i ++ )
	{
		while (j >= 0 && p[j + 1] != p[i]) j = next[j];
		if (p[j + 1] == p[i]) j ++ ;
		next[i] = j;
	}
}

int IndexKMP(HString target,HString pattern,int* next)
{//KMP匹配算法,target为主串，pattern为子串。
	//匹配成功返回主串中所含子串第一次出现的位置，否则返回-1。
	//调用GetNext函数获取模式串的next数组
	GetNext(pattern, next);
	char* s = target.ch;
	char* p = pattern.ch;
	for (int i = 0, j = -1; i < target.length; i++)
	{
		while (j != -1 && s[i] != p[j + 1]) j = next[j];
		if (s[i] == p[j + 1]) j ++ ;
		if (j == pattern.length - 1)
		{
			return i - j;
		}
	}
	return -1;
}
```



## 第4关 基于BM算法的网络入侵检测

### 代码

```cpp
#include<iostream>
#include<string>
#include<regex>
#include "cstring"
using namespace std;

#define ASCII_SIZE 256     //ASCII码共256位，可表示所有字符，作为坏字符数组的大小
#define MAXLEN 5000			//串的最大长度
typedef struct{   
	char *ch;				   //存储串的一维数组
	int length;				   //串的当前长度   
}HString;

void InputRule(HString ip[],int n)
{//将输入的n个ip地址存放到ip数组
	string pattern(R"(\d+.\d+.\d+.\d+)");
	regex r(pattern);
	
	for(int i = 0; i < n; i++){
		ip[i].ch = new char[MAXLEN];
		string pro;
		getline(cin, pro);
		
		smatch result;
		regex_search(pro, result, r);
		string s_ip = result[0];
		strcpy(ip[i].ch, s_ip.c_str());
		ip[i].length = s_ip.size();
	}
}

void InputLog(HString &log,int m)
{//将输入的m条日志合并存放到log，返回log的总长度
	for(int i = 0; i < m; i++){
		string str;
		getline(cin, str);
		strcat(log.ch, str.c_str());
	}
	log.length = strlen(log.ch);
}

void GetBC(HString pattern,int *bc)
{//得到坏字符bc数组
	int n = pattern.length;
	for(int i = 0; i < ASCII_SIZE; i++){
		bc[i] = -1;
	}
	for(int i = 0; i < n; i++){
		bc[pattern.ch[i]] = i;
	}
}

void GetGS(HString pattern,int *suffix,bool *prefix)
{//得到好后缀gs，其中suffix为int类型数组存储后缀字符对应前面的位置，prefix为bool类型数组存储是否存在匹配的前缀字符串
	//suffix和prefix共同构成好后缀数组
	int n = pattern.length;
	for(int i = 0; i < n; i++){
		suffix[i] = -1;
		prefix[i] = 0;
	}
	for(int i = 0; i < n - 1; i++){
		int j = i, k = 0;
		while(j >= 0 && pattern.ch[j] == pattern.ch[n - 1 - k]){
			j--, k++;
			suffix[k] = j + 1;
		}
		if(j == -1){
			prefix[k] = true;
		}
	}
}

int GetGSMove(int *suffix,bool *prefix,int bc_pos,int pattern_length)
{//利用suffix和prefix数组，返回好后缀移动的次数
	//bc_pos表示坏字符BC的位置（后一位为好后缀起点位置）
	int k = pattern_length - 1 - bc_pos;
	if(suffix[k] != -1) return bc_pos - suffix[k] + 1;
	for(int r = bc_pos + 2; bc_pos < pattern_length; r++){
		if(prefix[pattern_length - r]) return r;
	}
	return pattern_length;
}

int IndexBM(HString str,HString pattern)
{//在str.ch中匹配pattern.ch，匹配成功返回主串中所含子串第一次出现的位置，否则返回-1。
	//分别求坏字符数组bc和好字符数组suffix、prefix，分别计算两个策略的移动位数，取大值作为最终移动位数
	int *bc = new int[MAXLEN];
	GetBC(pattern, bc);
	int *suffix = new int[pattern.length];
	bool *prefix = new bool[pattern.length];
	GetGS(pattern, suffix, prefix);
	for(int i = 0, ml1, ml2; i < str.length - pattern.length + 1; i += max(ml1, ml2)){
		int j;
		for(j = pattern.length - 1; j >= 0; j--){
			if(str.ch[i + j] != pattern.ch[j]){
				break;
			}
		}
		if(j < 0){
			delete[] bc;
			delete[] suffix;
			delete[] prefix;
			return i;
		}
		ml1 = j - bc[str.ch[i + j]];
		ml2 = 0;
		if(j < pattern.length - 1){
			ml2 = GetGSMove(suffix, prefix, j, pattern.length);
		}
	}
	delete[] bc;
	delete[] suffix;
	delete[] prefix;
	return -1;
}
```



## 第5关 统计字符出现的频度

### 代码

```cpp
#include<iostream>
#include<cstring>
using namespace std;

int Ascii2Idx(char x){
    if(isdigit(x)) return x - '0';
    return x - 'A' + 10;
}

char Idx2Ascii(int x){
    if(x < 10) return x + '0';
    return x + 'A' - 10;
}

void Count(string c,int b[])
{//统计字符出现的频度
    for(auto e : c){
        b[Ascii2Idx(e)]++;
    }
    for(int i = 0; i < 36; i++){
        if(b[i]){
            cout << Idx2Ascii(i) << ":" << b[i] << '\n';
        }
    }
}
```



## 第6关 递归实现字符串的逆序存储

### 代码

```cpp
#include<iostream>
#include<cstring>
#define MAXSIZE 100
using namespace std;
void Reverse(char *a,int n)
{//递归实现字符串的逆序存储
    if(n <= 1) return;
    swap(a[0], a[n - 1]);
    Reverse(a + 1, n - 2);
}
```



## 第7关 字符串的插入

### 代码

```cpp
#include<iostream>
#define MAXSIZE 100
using namespace std;
void Insert(char s[],char t[],int pos,int LenS,int LenT)
{//字符串的插入
    for(int i = LenS - 1; i >= pos - 1; i--){
        s[i + LenT] = s[i];
    }
    for(int i = 0; i < LenT; i++){
        s[pos - 1 + i] = t[i];
    }
    s[LenS + LenT] = '\0';
    cout << s << '\n';
}
```



## 第8关 查找子串第一次出现的位置

### 代码

```cpp
#include<iostream>
#include<string.h>
using namespace std;

const int N = 10000;

int ne[N];

int IndexSubstring(string s1,string s2)
{//查找子串第一次出现的位置
    ne[0] = -1;
    for (int i = 1, j = -1; i < s2.size(); i ++ )
    {
        while (j >= 0 && s2[j + 1] != s2[i]) j = ne[j];
        if (s2[j + 1] == s2[i]) j ++ ;
        ne[i] = j;
    }

    for (int i = 0, j = -1; i < s1.size(); i ++ )
    {
        while (j != -1 && s1[i] != s2[j + 1]) j = ne[j];
        if (s1[i] == s2[j + 1]) j ++ ;
        if (j == s2.size() - 1)
        {
            return i - j;
        }
    }
    return -1;
}
```



