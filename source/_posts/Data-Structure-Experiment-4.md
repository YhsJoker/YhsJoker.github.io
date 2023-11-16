---
title: 数据结构实验四
date: 2023-11-17 00:07:11
tags:
  - [数据结构]
  - [C++]
categories: 作业
description: 数据结构实验四作业，发布在头歌平台，共计十一题
---

## 第1关 基于哈夫曼树的数据压缩算法

### 代码

```cpp
#include<iostream>
#include<string.h>
#define MAXSIZE 100
using namespace std;
typedef struct
{//哈夫曼树结点的形式
	int weight;               //结点的权值
	int parent,lchild,rchild;  //结点的双亲、左孩子、右孩子的下标
}HTNode,*HuffmanTree;       //动态分配数组存储哈夫曼树
typedef char **HuffmanCode;   //定义编码表类型
int Search(char a[],char ch)
{//查找数组中字符ch所在的位置，返回数组下标，否则返回-1
	for(int i = 0; a[i]; i++){
        if(a[i] == ch) return i;
    }
    return -1;
}
void Sort(char a[],int b[],int len)
{//按ASCII码冒泡排序
    for(int i = len - 1; i >= 0; i--){
        for(int j = 0; j < i; j++){
            if(a[j] > a[j + 1]){
                swap(a[j], a[j + 1]);
                swap(b[j], b[j + 1]);
            }
        }
    }
}
void Select_min(HuffmanTree HT,int n,int &s1,int &s2)
{// 在HT[k](1≤k≤i-1）中选择两个其双亲域为0且权值最小的结点，并返回它们在HT中的序号s1和s2
    int m_1 = MAXSIZE, m_2 = MAXSIZE;
    for(int i = 1; i <= n; i++){
        if(HT[i].parent == 0){
            if(HT[i].weight < m_1){
                m_1 = HT[i].weight;
                s1 = i;
            }
        }
    }
    for(int i = 1; i <= n; i++){
        if(HT[i].parent == 0 && i != s1){
            if(HT[i].weight < m_2){
                m_2 = HT[i].weight;
                s2 = i;
            }
        }
    }
}
int m;
void CreateHuffmanTree(HuffmanTree &HT,int n,int b[])
{//构造哈夫曼树HT
    if(n <= 1) return;
    int s1, s2;
    m = 2 * n - 1;
    HT = new HTNode[m + 1];
    for(int i = 1; i <= m; i++){
        HT[i].parent = 0;
        HT[i].lchild = 0;
        HT[i].rchild = 0;
    }
    for(int i = 1; i <= n; i++)
        HT[i].weight = b[i - 1];
  
    for(int i = n + 1; i <= m; i++)
    {
        Select_min(HT, i - 1, s1, s2);
       
        HT[s1].parent = i;
        HT[s2].parent = i;
        HT[i].lchild = s1;
        HT[i].rchild = s2;
        HT[i].weight = HT[s1].weight + HT[s2].weight;
    }
}
void CreateHuffmanCode(HuffmanTree HT,HuffmanCode &HC,int n)
{//从叶子到根逆向求每个字符的哈夫曼编码，存储在编码表HC中
    HC = new char*[n + 1];
    char* cd;
    int c,f,start;
    cd = new char[n];
    cd[n - 1] = '\0';
    for(int i = 1; i <= n; i++)
    {
        start = n - 1;   
        c = i;
        f = HT[i].parent; 
        while(f != 0)   
        {
            --start;
            if(HT[f].lchild == i)
                cd[start] = '0';
            else        
                cd[start] = '1';
            c = f;
            f = HT[c].parent;      
        }                       
        HC[i] = new char[n - start];
        strcpy(HC[i], &cd[start]);
    }
    delete cd;
}
void CharFrequency(char ch[],char a[],int b[],int &j)
{//统计词频
    int pos;
    for(int i = 0; ch[i] != '\0'; i++){
        pos = Search(a,ch[i]);
        if(pos == -1)  
        {
            a[j] = ch[i];  
            a[j+1] = '\0';
            b[j]++;
            j++; 
        }
        else
        {
            b[pos]++;
        }
    }
}
void PrintHT(HuffmanTree HT)
{//输出哈夫曼树的存储结构的终态
    for(int i = 1; i <= m; i++){
        cout << i << " " << HT[i].weight << " " << HT[i].parent << " " << HT[i].lchild << " " << HT[i].rchild << '\n';
    }
}
void PrintHC(HuffmanCode HC,char a[],int j)
{//输出每个字符的哈夫曼编码
    for(int i = 1; i <= j; i++){
        if(i != j)
            cout << a[i - 1] << ":" << HC[i] << " ";
        else
            cout << a[i - 1] << ":" << HC[i] << '\n';
    }
}


```



## 第2关 基于二叉链表的树结构相等的判断

### 代码

```cpp
 #include<iostream>
using namespace std;
typedef struct BiTNode
{
	char data;
	struct BiTNode *lchild,*rchild;
}BiTNode,*BiTree;
void CreateBiTree(BiTree &T,char S[],int &i)
{////先序建立二叉树
/**************begin************/
    if(S[i] == '0'){
        T = nullptr;
        return;
    }
    T = new BiTNode;
    T -> data = S[i];
    CreateBiTree(T -> lchild, S, ++i);
    CreateBiTree(T -> rchild, S, ++i);
    /**************end************/
}

int Compare(BiTree T1,BiTree T2)
{//判断两棵二叉树是否相等，不相等返回0，相等返回1
/**************begin************/
    if(!T1 && !T2) return 1;
    if(T1 && !T2) return 0;
    if(!T1 && T2) return 0;
    if(T1 -> data != T2 -> data) return 0;
    return Compare(T1 -> lchild, T2 -> lchild) && Compare(T1 -> rchild, T2 -> rchild);
    /**************end************/
}
```



## 第3关 基于二叉链表的二叉树左右孩子的交换

### 代码

```cpp
 #include<iostream>
#include<cstring>
using namespace std;
typedef struct BiTNode
{
	char data;
	struct BiTNode *lchild,*rchild;
}BiTNode,*BiTree;
void CreateBiTree(BiTree &T,char S[],int &i)
{//先序建立二叉树
	if(S[i]=='0')
		T=NULL;
	else
	{
		T=new BiTNode;
		T->data=S[i];
		CreateBiTree(T->lchild,S,++i);
		CreateBiTree(T->rchild,S,++i);
	}
}

void ChangeRL(BiTree &T)
{//二叉树左右孩子的交换
/**************begin************/
	if(!T) return;
    swap(T -> lchild, T -> rchild);
    ChangeRL(T -> lchild);
    ChangeRL(T -> rchild);

    
    /**************end************/
}

void PreOrderTraverse(BiTree T)
{//先序遍历
	if(T)
	{
    	cout<<T->data;
		PreOrderTraverse(T->lchild);
		PreOrderTraverse(T->rchild);
	}
}
```



## 第4关 基于二叉链表的二叉树的双序遍历

### 代码

```cpp
 #include<iostream>
#include <string.h>
using namespace std;
typedef struct BiTNode
{
	char data;
	struct BiTNode *lchild,*rchild;
}BiTNode,*BiTree;
void CreateBiTree(BiTree &T,char S[],int &i)
{//先序建立二叉树
	if(S[i]=='0')
		T=NULL;
	else
	{
		T=new BiTNode;
		T->data=S[i];
		CreateBiTree(T->lchild,S,++i);
		CreateBiTree(T->rchild,S,++i);
	}
}
void DoubleTraverse(BiTree T)
{//双序遍历二叉树T的递归算法
/**************begin************/
    if(!T) return;
    cout << T -> data;
    DoubleTraverse(T -> lchild);
    cout << T -> data;
    DoubleTraverse(T -> rchild);

    /**************end************/
}
```



## 第5关 基于二叉链表的二叉树最大宽度的计算

### 代码

```cpp
 #include <iostream>
#include <string.h>
using namespace std;

typedef struct BiTNode
{
    char data;
    struct BiTNode *lchild,*rchild;
}BiTNode,*BiTree;

BiTree CreateBiTree(int &pos, char *str)
{// 先序建立二叉树
    if(str[pos] == '0') return nullptr;
    BiTree T = new BiTNode;
    T -> data = str[pos];
    T -> lchild = CreateBiTree(++pos, str);
    T -> rchild = CreateBiTree(++pos, str);
    return T;
}

int Width(BiTree T)
{// 求二叉树T最大宽度
   static BiTree q[10000];
   int hh = 0, tt = -1;
   q[++tt] = T;
   int max_width = 0;
   while(hh <= tt){
        int width = tt - hh + 1;
        max_width = max(max_width, width);
        for(int i = 0; i < width; i++){
            auto u = q[hh++];
            if(u -> lchild) q[++tt] = u -> lchild;
            if(u -> rchild) q[++tt] = u -> rchild;
        }
   }
   return max_width;
}
```



## 第6关 基于二叉链表的二叉树最长路径的求解

### 代码

```cpp
 #include<iostream>
#define MAXSIZE 100
using namespace std;
typedef struct BiTNode
{
	char data;
	struct BiTNode *lchild,*rchild;
}BiTNode,*BiTree;

void CreateBiTree(BiTree &T,char S[],int &i)
{//先序建立二叉树
	if(S[i]=='0')
		T=NULL;
	else
	{
		T=new BiTNode;
		T->data=S[i];
		CreateBiTree(T->lchild,S,++i);
		CreateBiTree(T->rchild,S,++i);
	}
}

int GetDepth(BiTree T){
    if(!T) return 0;
    return max(GetDepth(T -> lchild), GetDepth(T -> rchild)) + 1;
}

void GetPath(BiTree T, BiTree l[], int &longest, int length){
    if(longest == length) return;
    if(!T){
        return;
    }
    l[++longest] = T;
    if(longest == length) return;
    GetPath(T -> lchild, l, longest, length);
    if(longest == length) return;
    GetPath(T -> rchild, l, longest, length);
    if(longest == length) return;
    longest--;
}

void LongestPath(BiTree T,BiTree l[],int &longest)
{//二叉树最长路径的求解
    int depth = GetDepth(T);
    GetPath(T, l, longest, depth);
}
```



## 第7关 基于二叉链表的二叉树叶子结点到根结点的路径的求解

### 代码

```cpp
 #include<iostream>
using namespace std;
typedef struct BiTNode
{
	char data;
	struct BiTNode *lchild,*rchild;
}BiTNode,*BiTree;

void CreateBiTree(BiTree &T,char S[],int &i)
{//先序建立二叉树
	if(S[i]=='0')
		T=NULL;
	else
	{
		T=new BiTNode;
		T->data=S[i];
		CreateBiTree(T->lchild,S,++i);
		CreateBiTree(T->rchild,S,++i);
	}
}

void AllPath(BiTree T,char path[],int pathlen)
{//二叉树叶子结点到根结点的路径的求解
/**************begin************/
    if(!T) return;
    path[pathlen++] = T -> data;
    if(!T -> lchild && !T -> rchild){
        for(int i = pathlen - 1; i >= 0; i--){
            cout << path[i];
        }
        cout << '\n';
    }
    AllPath(T -> lchild, path, pathlen);
    AllPath(T -> rchild, path, pathlen);
    
    /**************end************/
}
```



## 第8关 基于二叉链表的二叉树的遍历

### 代码

```cpp
 #include<iostream>
#include<string.h>
using namespace std;
typedef struct BiTNode
{
	char data;
	struct BiTNode *lchild,*rchild;
}BiTNode,*BiTree;
void CreateBiTree(BiTree &T,char S[],int &i)
{//先序建立二叉树
	if(S[i]=='0')
		T=NULL;
	else
	{
		T=new BiTNode;
		T->data=S[i];
		CreateBiTree(T->lchild,S,++i);
		CreateBiTree(T->rchild,S,++i);
	}
}
void PreOrderTraverse(BiTree T)
{//二叉树的先序遍历
/**************begin************/
	if(!T) return;
    cout << T -> data;
    PreOrderTraverse(T -> lchild);
    PreOrderTraverse(T -> rchild);

    /**************end************/
}
void InOrderTraverse(BiTree T)
{//二叉树的中序遍历
/**************begin************/
    if(!T) return;
    InOrderTraverse(T -> lchild);
    cout << T -> data;
    InOrderTraverse(T -> rchild);

    /**************end************/
}
void PostOrderTraverse(BiTree T)
{//二叉树的后序遍历
/**************begin************/
    if(!T) return;
    PostOrderTraverse(T -> lchild);
    PostOrderTraverse(T -> rchild);
    cout << T -> data;

    /**************end************/
}
```



## 第9关 基于二叉链表的二叉树结点个数的统计

### 代码

```cpp
 #include<iostream>
#include<string.h>
using namespace std;

typedef struct BiTNode
{
	char data;
	struct BiTNode *lchild,*rchild;
}BiTNode,*BiTree;
void CreateBiTree(BiTree &T,char S[],int &i)
{//先序建立二叉树
	if(S[i]=='0')
		T=NULL;
	else
	{
		T=new BiTNode;
		T->data=S[i];
		CreateBiTree(T->lchild,S,++i);
		CreateBiTree(T->rchild,S,++i);
	}
}
void Count(BiTree T,int &a,int &b,int &c)
{//二叉树结点个数的统计
	int cnt = 0;
    if(T -> lchild){
        cnt++;
        Count(T -> lchild, a, b, c);
    }
    if(T -> rchild){
        cnt++;
        Count(T -> rchild, a, b, c);
    }

    if(cnt == 0) a++;
    else if(cnt == 1) b++;
    else c++;
}
```



## 第10关 基于二叉链表的二叉树高度的计算

### 代码

```cpp
 #include<iostream>
#include <string.h>
using namespace std;
typedef struct BiTNode
{
	char data;
	struct BiTNode *lchild,*rchild;
}BiTNode,*BiTree;
void CreateBiTree(BiTree &T,char S[],int &i)
{//先序建立二叉树
	if(S[i]=='0')
		T=NULL;
	else
	{
		T=new BiTNode;
		T->data=S[i];
		CreateBiTree(T->lchild,S,++i);
		CreateBiTree(T->rchild,S,++i);
	}
}
int Depth(BiTree T)
{//二叉树高度的计算
/**************begin************/
	if(!T) return 0;
    return max(Depth(T -> lchild), Depth(T -> rchild)) + 1;
    /**************end************/
}
```





## 第11关 基于二叉树的表达式求值

### 代码

```cpp
 #include<iostream>
#define MAXSIZE 100
using namespace std;
typedef struct BiTNode
{//二叉树的双链表存储表示
	double data;          //结点数据域
	bool ischaracter;      //判断结点是否为字符
	struct BiTNode *lchild,*rchild;    //左右孩子指针
}BiTNode,*BiTree;
typedef struct
{//字符栈的存储结构
	char *base;     //栈底指针
	char *top;       //栈顶指针
	int stacksize;   //栈可用的最大容量
}SqStack1;
typedef struct
{//结点栈的存储结构
	BiTree *base;
	BiTree *top;
	int stacksize;
}SqStack2;
void InitStack1(SqStack1 &s)
{//字符栈的初始化
	s.base = new char[MAXSIZE];
    s.top = s.base;
    s.stacksize = MAXSIZE;
}
void InitStack2(SqStack2 &s)
{//结点栈的初始化
	s.base = new BiTree[MAXSIZE];
    s.top = s.base;
    s.stacksize = MAXSIZE;
}
void Push1(SqStack1 &s,char ch)
{//字符入栈操作
	if(s.top - s.base == s.stacksize){
        return;
    }
    *s.top++ = ch;
}
void Push2(SqStack2 &s,BiTree t)
{//结点入栈操作
	if(s.top - s.base == s.stacksize){
        return;
    }
    *s.top++ = t;
}
void Pop1(SqStack1 &s,char &ch)
{//字符出栈操作
	if(s.top == s.base) return;
    ch = *(--s.top);
}
void Pop2(SqStack2 &s,BiTree &t)
{//结点出栈操作
	if(s.top == s.base) return;
    t = *(--s.top);
}
char GetTop(SqStack1 s)
{//取字符栈的栈顶元素
	return *(s.top - 1);
}
bool EmptyStack(SqStack1 s)
{//栈的判空操作
	return s.base == s.top;
}
char Precede(char a,char b)
{//判断符号的优先级
	if(a == '+' || a == '-'){
		if(b == '+' || b == '-' || b == ')' || b == '='){
			return '>';
		}
        else{
			return '<';
		}
	}
    else if(a == '*' || a == '/'){
		if(b == '+' || b == '-' || b == '*' || b == '/' || b == ')' || b == '='){
			return '>';
		}
        else{
			return '<';
		}
	}
    else if(a == '('){
		if(b == ')'){
			return '=';
		}
        else{
			return '<';
		}
	}
    else if(a == ')'){
		return '>';
	}
    else{
		if(b == '='){
			return '=';
		}
        else{
			return '<';
		}
	}
}
double Operate(double a,char ch,double b)
{//运算操作，返回相应的数值结果
	if(ch == '+') return a+b;
	if(ch == '-') return a-b;
	if(ch=='*') return a*b;
	return a/b;
}
bool IsCharacter(char ch)
{//判断ch是否为+、-、*、/、(、)、= 这类的字符，是则返回true
	if(ch == '+' || ch == '-' || ch == '*' || ch == '/' || ch == '(' || ch == ')' || ch == '=')
		return true;
	else
		return false;
}
double InOrder(BiTree T)
{//中序遍历二叉树并求表达式的值
	if(!T) return 0;
    if(T->ischaracter == false) return T->data;
    double x=InOrder(T->lchild);
    char op=(char)(T->data);
    double y=InOrder(T->rchild);
    return Operate(x,op,y);
}
void CreateBT(char ch[],BiTree &t,SqStack1 optr,SqStack2 expt)
{//创建二叉树
    int i = 0;
	char op;
	BiTree t1, t2;
	double num;
	while(ch[i] != '\0' || !EmptyStack(optr)){
		if(!IsCharacter(ch[i])){
			BiTree q = new BiTNode;
			num = ch[i]-'0';
			q->ischaracter = false;
			q->data = num;
			q->lchild = nullptr;
			q->rchild = nullptr;
			Push2(expt, q);
			i++;
		}
        else{
			char c = Precede(GetTop(optr), ch[i]);
			if(c == '<'){
				Push1(optr, ch[i]);
				i++;
			}
            else if(c == '>'){
				Pop1(optr, op);
				Pop2(expt, t2);
				Pop2(expt, t1);
				t = new BiTNode;
				t->ischaracter = true;
				t->data = op;
				t->lchild = t1;
				t->rchild = t2;
				Push2(expt, t);
			}
            else{
				Pop1(optr, op);
				i++;
			}
		}
	}
}
```







