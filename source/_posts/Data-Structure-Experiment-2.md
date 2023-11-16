---
title: 数据结构实验二
date: 2023-11-01 23:50:58
tags:
  - [数据结构]
  - [C++]
categories: 作业
description: 数据结构实验二作业，发布在头歌平台，共计十七题
---

## 第1关：基于栈的中缀算术表达式求值

### 代码

```cpp
#include <iostream>
#include <iomanip>
#include <cctype>
#include <cmath>
#define MAXSIZE 100
#define OK 1
#define ERROR 0
#define OVERFLOW -2
typedef int Status;
using namespace std;
typedef struct
{//运算符栈
    char *base;
	char *top;
	int stacksize;
}SqStack1;
Status InitStack1(SqStack1 &S)
{//运算符栈初始化
	S.base = new char[MAXSIZE];
    S.top = S.base;
    S.stacksize = 0;
    return OK;
}
Status Push1(SqStack1 &S, char e)
{//运算符栈入栈
    if(S.stacksize == MAXSIZE) return OVERFLOW;
    *S.top++ = e;
    S.stacksize++;
    return OK;
    
}
Status Pop1(SqStack1 &S)
{//运算符栈出栈
    if(S.stacksize == 0) return ERROR;
	S.top--;
    return OK;
}
char GetTop1(SqStack1 S)
{//运算符栈取栈顶元素
	return *(S.top - 1);
}
typedef struct
{//操作数栈
	double *base;
	double *top;
	int  stacksize;
}SqStack2;
Status InitStack2(SqStack2 &S)
{//操作数栈初始化
	S.base = new double[MAXSIZE];
    S.top = S.base;
    S.stacksize = 0;
    return OK;
}
Status Push2(SqStack2 &S,double e)
{//操作数栈入栈
	if(S.stacksize == MAXSIZE) return OVERFLOW;
    *S.top++ = e;
    S.stacksize++;
    return OK;
}
Status Pop2(SqStack2 &S)
{//操作数栈出栈
	if(S.stacksize == 0) return ERROR;
	S.top--;
    return OK;
}
double GetTop2(SqStack2 S)
{//操作数栈取栈顶元素
	return *(S.top - 1);
}
double Calculate(double a,char op,double b)
{//计算表达式“a op b”的值
    if(op == '+') return a + b;
    if(op == '-') return a - b;
    if(op == '*') return a * b;
    if(op == '/') return a / b;
}

char Precede(char a,char b)
{//比较运算符a和b的优先级
	int pr1 = 0, pr2 = 0;
    if(a == '+' || a == '-') pr1 = 1;
    else pr1 = 2;
    if(b == '+' || b == '-') pr2 = 1;
    else pr2 = 2;
    
    if(pr1 > pr2) return 1;
    else if(pr1 == pr2) return 0;
    else return -1;
}

void Evaluate(SqStack1& OPTR,SqStack2& OPND){
    char op = GetTop1(OPTR);
    Pop1(OPTR);
    double b = GetTop2(OPND);
    Pop2(OPND);
    double a = GetTop2(OPND);
    Pop2(OPND);
    double r = Calculate(a, op, b);
    Push2(OPND, r);
}

double EvaluateExpression(SqStack1 OPTR,SqStack2 OPND,char s[])
{//算术表达式求值的算符优先算法
 //设OPTR和OPND分别为运算符栈和操作数栈
 //表达式求值算法调用Precede函数和Calculate函数 
	for(int i = 0; s[i] != '='; i++){
        char c = s[i];
        if(c == '(') Push1(OPTR, c);
        else if(c == ')'){
            while(GetTop1(OPTR) != '(') Evaluate(OPTR, OPND);
            Pop1(OPTR);
        }
        else if(isdigit(c)){
            int j = i;
            double d = atof(s + i);
            while(isdigit(s[j]) || s[j] == '.') j++;
            i = j - 1;
            Push2(OPND, d);
        }
        else{
            while(GetTop1(OPTR) != '=' && GetTop1(OPTR) != '(' && Precede(GetTop1(OPTR), c) >= 0) Evaluate(OPTR, OPND);
            Push1(OPTR, c);
        }
    }
    while(GetTop1(OPTR) != '=') Evaluate(OPTR, OPND);
    return GetTop2(OPND);
}

```



## 第2关：中缀表达式转化为后缀表达式

### 代码

```cpp
#include<iostream>
#include<cctype>
using namespace std;
#define  MAXSIZE  100
#define OK 1
#define ERROR 0
#define OVERFLOW -2
typedef int Status;
typedef struct
{
	char *base;
	char *top;
	int stacksize;
}SqStack;
Status InitStack(SqStack &S)
{//初始化栈
    S.base = new char[MAXSIZE];
    S.top = S.base;
    S.stacksize = 0;
    return OK;
}
Status Push(SqStack &S, char e)
{//入栈
    if(S.stacksize == MAXSIZE) return OVERFLOW;
    *S.top++ = e;
    S.stacksize++;
    return OK;
}
Status Pop(SqStack &S)
{//出栈
    if(S.stacksize == 0) return ERROR;
	S.top--;
    S.stacksize--;
    return OK;
}
char GetTop(SqStack S)
{//取栈顶元素
    return *(S.top - 1);
}
char Precede(char a,char b)
{//比较运算符a和b的优先级
    int pr1 = 0, pr2 = 0;
    if(a == '+' || a == '-') pr1 = 1;
    else pr1 = 2;
    if(b == '+' || b == '-') pr2 = 1;
    else pr2 = 2;
    
    if(pr1 > pr2) return 1;
    else if(pr1 == pr2) return 0;
    else return -1;
}
void InfixToSuffix(SqStack OPTR,char s[])
{//将中缀表达式转化为后缀表达式并输出 
    for(int i = 0; s[i] != '='; i++){
        char c = s[i];
        if(c == '(') Push(OPTR, c);
        else if(c == ')'){
            while(GetTop(OPTR) != '('){
                cout << GetTop(OPTR);
                Pop(OPTR);
            }
            Pop(OPTR);
        }
        else if(isdigit(c)){
            int j = i;
            double d = atof(s + i);
            while(isdigit(s[j]) || s[j] == '.') j++;
            i = j - 1;
            cout << d;
        }
        else{
            while(GetTop(OPTR) != '=' && GetTop(OPTR) != '(' && Precede(GetTop(OPTR), c) >= 0){
                cout << GetTop(OPTR);
                Pop(OPTR);
            }
            Push(OPTR, c);
        }
    }
    while(GetTop(OPTR) != '='){
        cout << GetTop(OPTR);
        Pop(OPTR);
    }
    cout << '\n';
}

```



## 第3关：基于栈的后缀算术表达式求值

### 代码

```cpp
#include <iostream>
#include<iomanip>
#include <string>
#define MAXSIZE 100
#define OK 1
#define ERROR 0
#define OVERFLOW -2
typedef int Status;
using namespace std;
typedef struct
{//操作数栈
	double* base;
	double* top;
	int  stacksize;
}SqStack;
Status InitStack(SqStack& S)
{//操作数栈初始化
	S.base = new double[MAXSIZE];
    S.top = S.base;
    S.stacksize = 0;
	return OK;
}
Status Push(SqStack& S, double e)
{//操作数栈入栈
	if(S.stacksize == MAXSIZE) return OVERFLOW;
    *S.top++ = e;
    S.stacksize++;
	return OK;
}
Status Pop(SqStack& S)
{//操作数栈出栈
		if(S.stacksize == 0) return ERROR;
	S.top--;
    S.stacksize--;
	return OK;
}
double GetTop(SqStack S)
{//操作数栈取栈顶元素
	if(S.stacksize == 0)
	    return ERROR;	//若不存在栈顶元素则返回ERROR
    return *(S.top - 1);
}
double Calculate(double a, char op, double b)
{//计算表达式“a op b”的值
	if(op == '+') return a + b;
    if(op == '-') return a - b;
    if(op == '*') return a * b;
    if(op == '/') return a / b;
}
double EvaluateExpression(SqStack OPND,char s[])
{//后缀算术表达式求值
 //设OPND为操作数栈
 //表达式求值算法调用Calculate函数 
    for(int i = 0; s[i] != '='; i++){
        char c = s[i];
        if(c == ' ') continue;
        else if(isdigit(c)){
            int j = i;
            double d = atof(s + i);
            while(isdigit(s[j]) || s[j] == '.') j++;
            i = j - 1;
            Push(OPND, d);
        }
        else{
            double b = GetTop(OPND);
            Pop(OPND);
            double a = GetTop(OPND);
            Pop(OPND);
            Push(OPND, Calculate(a, c, b));
        }
    }
    return GetTop(OPND);
}
```



## 第4关：中缀表达式转化为前缀表达式

### 代码

```cpp
#include<iostream>
#include<cstring>
#include<cctype>
using namespace std;
#define  MAXSIZE  100
#define OK 1
#define ERROR 0
#define OVERFLOW -2
typedef int Status;
typedef struct
{
	char *base;
	char *top;
	int stacksize;
}SqStack;
Status InitStack(SqStack &S)
{//初始化栈
    S.base = new char[MAXSIZE];
    S.top = S.base;
    S.stacksize = 0;
    return OK;
}
Status Push(SqStack &S, char e)
{//入栈
    if(S.stacksize == MAXSIZE) return OVERFLOW;
    *S.top++ = e;
    S.stacksize++;
    return OK;
}
Status Pop(SqStack &S)
{//出栈
    if(S.stacksize == 0) return ERROR;
	S.top--;
    S.stacksize--;
    return OK;
}
char GetTop(SqStack S)
{//取栈顶元素
    return *(S.top - 1);
}
char Precede(char a,char b)
{//比较运算符a和b的优先级
    int pr1 = 0, pr2 = 0;
    if(a == '+' || a == '-') pr1 = 1;
    else pr1 = 2;
    if(b == '+' || b == '-') pr2 = 1;
    else pr2 = 2;
    
    if(pr1 > pr2) return 1;
    else if(pr1 == pr2) return 0;
    else return -1;
}
void InfixToPrefix(SqStack OPTR,char s[])
{//将中缀表达式转化为前缀表达式并输出 
    SqStack OPND;
    InitStack(OPND);
    Push(OPND, '=');
    int len = strlen(s);
    for(int i = len - 1; i >= 0; i--){
        char c = s[i];
        if(isdigit(c)){
            Push(OPND, c);
        }
        else if(c == ')'){
            Push(OPTR, c);
        }
        else if(c == '('){
            while(GetTop(OPTR) != ')'){
                Push(OPND, GetTop(OPTR));
                Pop(OPTR);
            }
            Pop(OPTR);
        }
        else{
            while(true){
                if(GetTop(OPTR) == '=' || GetTop(OPTR) == ')' || Precede(c, GetTop(OPTR)) >= 0) {
                    Push(OPTR, c);
                    break;
                }
                else{
                    Push(OPND, GetTop(OPTR));
                    Pop(OPTR);
                }
            }
        }
    }

    while(GetTop(OPTR) != '='){
        Push(OPND, GetTop(OPTR));
        Pop(OPTR);
    }

    while(GetTop(OPND) != '='){
        cout << GetTop(OPND);
        Pop(OPND);
    }
}

```



## 第5关：基于栈的前缀算术表达式求值

### 代码

```cpp
#include <iostream>
#include<iomanip>
#include <string>
#include<cstring>
#define MAXSIZE 100
#define OK 1
#define ERROR 0
#define OVERFLOW -2
typedef int Status;
using namespace std;
typedef struct
{//操作数栈
	double* base;
	double* top;
	int  stacksize;
}SqStack;
Status InitStack(SqStack& S)
{//操作数栈初始化
	S.base = new double[MAXSIZE];
    S.top = S.base;
    S.stacksize = 0;	
	return OK;
}
Status Push(SqStack& S, double e)
{//操作数栈入栈
	if(S.stacksize == MAXSIZE) return OVERFLOW;
    *S.top++ = e;
    S.stacksize++;
	return OK;
}
Status Pop(SqStack& S)
{//操作数栈出栈
	if(S.stacksize == 0) return ERROR;
	S.top--;	
    S.stacksize--;
	return OK;
}
double GetTop(SqStack S)
{//操作数栈取栈顶元素
	return *(S.top - 1);
	return ERROR;	//若不存在栈顶元素则返回ERROR
}
double Calculate(double a, char op, double b)
{//计算表达式“a op b”的值
	if(op == '+') return a + b;
    if(op == '-') return a - b;
    if(op == '*') return a * b;
    if(op == '/') return a / b;
}
double EvaluateExpression(SqStack OPND,char s[])
{//前缀算术表达式求值
 //设OPND为操作数栈
 //表达式求值算法调用Calculate函数 
	int len = strlen(s);
    for(int i = len - 2; i >= 0; i--){
        char c = s[i];
        if(isdigit(c)){
            int j = i;
            while(j >= 0 && (isdigit(s[j]) || s[j] == '.')) j--;
            i = j + 1;
            double d = atof(s + i);
            Push(OPND, d);
        }
        else if(c == ' ') continue;
        else{
            double a = GetTop(OPND);
            Pop(OPND);
            double b = GetTop(OPND);
            Pop(OPND);
            Push(OPND, Calculate(a, c, b));
        }
    }

    cout << fixed << setprecision(2) << GetTop(OPND);
    exit(0);

    return GetTop(OPND);
}
```



## 第6关：入栈和出栈的基本操作

### 代码

```cpp
#include<iostream>
using namespace std;
#define  MAXSIZE  100
#define OK 1
#define ERROR 0
#define OVERFLOW -2
typedef int Status;
typedef struct
{
	int* base;
	int* top;
	int stacksize;
}SqStack;
Status InitSqStack(SqStack& S)
{//栈的初始化
	S.base = new int[MAXSIZE];
    S.top = S.base;
    S.stacksize = 0;
	return OK;
}
Status Push(SqStack& S, int e)
{//入栈
	if(S.stacksize == MAXSIZE) return OVERFLOW;
    *S.top++ = e;
    S.stacksize++;
	return OK;
}
Status Pop(SqStack& S)
{//出栈
	if(S.stacksize == 0) return ERROR;
	S.top--;
    S.stacksize--;
	return OK;
}
bool Empty(SqStack& S){
    return !S.stacksize;
}
int GetTop(SqStack S)
{//取栈顶元素
	return *(S.top - 1);
}
void InOutS(SqStack& S, int a[], int n)
{//入栈和出栈的基本操作
	for(int i = 0; i < n; i++){
        if(a[i] != -1){
            Push(S, a[i]);
        }
        else{
            if(Empty(S)){
                cout << "POP ERROR\n";
                break;
            }
            else{
                cout << GetTop(S) << '\n';
                Pop(S);
            }
        }
    }
}
```



## 第7关：双栈的基本操作

### 代码

```cpp
#include<iostream>
using namespace std;
typedef int Status;
typedef struct
{
	int top[2], bot[2];//栈顶和栈底指针
	int* V;//栈数组
	int m;//栈最大可容纳元素个数
}DblStack;
void InitDblStack(DblStack& S, int m)
{//初始化一个大小为m的双向栈
	S.V = new int[m];
    S.m = m;
    S.top[0] = -1, S.bot[0] = -1;
    S.top[1] = m, S.bot[1] = m;
}
Status IsEmpty(DblStack S, int i)
{//判断指定的i号栈是否为空，空返回1，否则返回0
	return S.top[i] == S.bot[i];
}
Status IsFull(DblStack S)
{//判断栈是否满，满则返回1，否则返回0
	return S.top[0] + 1 == S.top[1];
}
void Push(DblStack& S, int i)
{//向指定的i号栈中插入元素x，先移动指针再入栈
    int x; cin >> x;
	if(i == 0) S.V[++S.top[i]] = x;
    else S.V[--S.top[i]] = x;
}

void Pop(DblStack& S, int i)
{//删除指定的i号栈的栈顶元素，先出栈再移动指针
	if(i == 0) cout << S.V[S.top[i]--] << ' ';
    else cout << S.V[S.top[i]++] << ' ';
}
```



## 第8关：基于栈的回文字符序列判断

### 代码

```cpp
#include <iostream>
#define MAXSIZE 100
#define OK 1
#define ERROR 0
#define OVERFLOW -2
typedef int Status;
using namespace std;
typedef struct
{
	char* base;
	char* top;
	int stacksize;
}SqStack;
Status InitStack(SqStack& S)
{//栈初始化
	S.base = new char[MAXSIZE];
    S.top = S.base;
    S.stacksize = 0;
	return OK;
}
Status Push(SqStack& S, char e)
{//入栈
	if(S.stacksize == MAXSIZE) return OVERFLOW;
    *S.top++ = e;
    S.stacksize++;
	return OK;
}
Status Pop(SqStack& S)
{//出栈返回栈顶元素
	if(S.stacksize == 0) return ERROR;
	S.top--;
    S.stacksize--;
    return OK;
}
char GetTop(SqStack S)
{//运算符栈取栈顶元素
	return *(S.top - 1);
}
Status IsPalindrome(SqStack& S, char* t)
{//判断栈的回文字符序列，不等则返回零, 相等则返回1
	for(int i = 0; t[i]; i++){
        Push(S, t[i]);
    }
    for(int i = 0; t[i]; i++){
        if(t[i] != GetTop(S)) return 0;
        Pop(S);
    }
    return 1;
}
```



## 第9关：基于栈的可操作判断

### 代码

```cpp
#include <iostream>
#define MAXSIZE 100
#define OK 1
#define ERROR 0
#define OVERFLOW -2
typedef int Status;
using namespace std;
typedef struct
{
    char* base;
    char* top;
    int stacksize;
}SqStack;
Status InitStack(SqStack& S)
{//初始化栈
    S.base = new char[MAXSIZE];
    S.top = S.base;
    S.stacksize = 0;
    return OK;
}
Status Push(SqStack& S)
{//入栈
    if(S.stacksize == MAXSIZE) return OVERFLOW;
    S.top++;
    S.stacksize++;
    return OK;
}
Status Pop(SqStack& S)
{//出栈
    if(S.stacksize == 0) return ERROR;
	S.top--;
    S.stacksize--;
    return OK;
}
Status IsEmpty(SqStack S)
{//判断栈是否为空，空返回1，否则返回0
    return !S.stacksize;
}
bool Judge(char a[], SqStack& S)
{//栈的可操作判断
    for(int i = 0; a[i]; i++){
        if(a[i] == 'I') Push(S);
        else{
            if(IsEmpty(S)) return 0;
            else Pop(S);
        }
    }
    return IsEmpty(S);
}
```



## 第10关：Ackermann函数的递归求值

### 代码

```cpp
#include<iostream>
using namespace std;
int Ack(int m, int n)
{//Ackermann函数的递归求值
	if(m == 0) return n + 1;
    if(m > 0 && n == 0) return Ack(m - 1, 1);
    return Ack(m - 1, Ack(m, n - 1));
}
```



## 第11关：Ackermann函数的非递归求值

### 代码

```cpp
#include<iostream>
using namespace std;
#define MAXSIZE 100

int Ack(int m, int n)
{//Ackermann函数的非递归求值
    static int f[MAXSIZE][MAXSIZE];
    for(int j = 0; j < MAXSIZE; j++) f[0][j] = j + 1;
    for(int i = 1; i <= m; i++){
        f[i][0] = f[i - 1][1];
        for(int j = 1; j < MAXSIZE; j++){
            f[i][j] = f[i - 1][f[i][j - 1]];
        }
    }
    return f[m][n];
}
```



## 第12关：递归求解单链表中的最大值

### 代码

```cpp
#include <iostream>
using namespace std;
typedef struct LNode
{
    int data;
    struct LNode* next;
}LNode, * LinkList;
void CreateList_R(LinkList& L, int n)
{//后插法创建单链表
    L = new LNode;
    L -> next = nullptr;

    LinkList p_tail = L;
    for(int i = 0; i < n; i++){
        p_tail -> next = new LNode;
        p_tail = p_tail -> next;
        p_tail -> next = nullptr;
        cin >> p_tail -> data;
    }
}
int GetMax(LinkList L)
{//递归求解单链表中的最大值
    if(L -> next == nullptr) return L -> data;
    else{
        return max(GetMax(L -> next), L -> data);
    }
}
```



## 第13关：递归求解单链表中的结点个数

### 代码

```cpp
#include <iostream>
using namespace std;
typedef struct LNode
{
    int data;
    struct LNode* next;
}LNode, * LinkList;
void CreateList_R(LinkList& L, int n)
{//后插法创建单链表
    L = new LNode;
    L -> next = nullptr;

    LinkList p_tail = L;
    for(int i = 0; i < n; i++){
        p_tail -> next = new LNode;
        p_tail = p_tail -> next;
        p_tail -> next = nullptr;
        cin >> p_tail -> data;
    }
}
int GetLength(LinkList L)
{//递归求解单链表中的结点个数
   if(L == nullptr) return 0;
   return GetLength(L -> next) + 1;
}
```



## 第14关：递归求解单链表中的平均值

### 代码

```cpp
#include <iostream>
using namespace std;
typedef struct LNode
{
    int data;
    struct LNode* next;
}LNode, * LinkList;
void CreateList_R(LinkList& L, int n)
{//后插法创建单链表
    L = new LNode;
    L -> next = nullptr;

    LinkList p_tail = L;
    for(int i = 0; i < n; i++){
        p_tail -> next = new LNode;
        p_tail = p_tail -> next;
        p_tail -> next = nullptr;
        cin >> p_tail -> data;
    }
}
double GetAverage(LinkList L, int n)
{//递归求解单链表中的平均值
    if(L -> next == nullptr) return L -> data;
    else{
        double avg = GetAverage(L -> next, n - 1);
        return (avg * (n - 1) + L -> data) / n;
    }
}
```



## 第15关：基于循环链表的队列的基本操作

### 代码

```cpp
#include<iostream>
using namespace std;
typedef int Status;
typedef struct QNode
{//队列的链式存储结构
    int data;
    struct QNode* next;
}QNode, * QueuePtr;
typedef struct
{
    QueuePtr rear;    //只设一个队尾指针
}LinkQueue;
Status EmptyQueue(LinkQueue Q)
{//判断队列是否为空，空返回1，否则返回0
//队列只有一个头结点，即当头结点的指针域指向自己时，队列为空
    return Q.rear -> next == Q.rear;
}
void EnQueue(LinkQueue& Q, int e)
{//入队，插入元素e为Q的新的队尾元素
    QueuePtr q = new QNode;
    q -> data = e;
    q -> next = Q.rear -> next;
    Q.rear -> next = q;
    Q.rear = Q.rear -> next;
}
void DeQueue(LinkQueue& Q)
{//出队，输出Q的队头元素值，后将其删除
    QueuePtr q = Q.rear -> next -> next;
    cout << q -> data << ' ';
    if(q == Q.rear){
        Q.rear = Q.rear -> next;
        Q.rear -> next = q -> next;
    }
    else Q.rear -> next -> next = q -> next;
    delete q;
}
```



## 第16关：附加判定标志的循环队列的基本操作

### 代码

```cpp
#include<iostream>
using namespace std;
#define MAXSIZE 100
#define OK 0
#define OVERFLOW -1
#define ERROR -2
typedef int Status;
typedef struct
{
	int* base;
	int front, rear, tag;
}SqQueue;
Status InitQueue(SqQueue& Q)
{//构造一个空队列Q
	Q.base = new int[MAXSIZE];
    if(!Q.base) return ERROR;
    Q.front = Q.rear = 0;
    Q.tag = 0;
	return OK;
}
Status EnQueue(SqQueue& Q, int e)
{//插入元素e为Q的新的队尾元素
	if(Q.tag == 1 && Q.rear == Q.front) return ERROR;
    Q.base[Q.rear] = e;
    Q.rear = (Q.rear + 1) % MAXSIZE;
    if(Q.tag == 0) Q.tag = 1;
	return OK;
}
Status DeQueue(SqQueue& Q)
{//删除Q的队头元素，用e返回其值
	if(Q.tag == 0 && Q.front == Q.rear) return ERROR;
    int e = Q.base[Q.front];
    Q.front = (Q.front + 1) % MAXSIZE;
    return e;
}
```



## 第17关：基于两端操作的循环队列的实现

### 代码

```cpp
#include<iostream>
using namespace std;
#define MAXSIZE 100
#define OK 1
#define ERROR 0
#define OVERFLOW -2
typedef int Status;
typedef struct
{
	int* base;
	int front;
	int rear;
}SqQueue;
Status InitQueue(SqQueue& Q)
{//构造一个空队列Q
	Q.base = new int[MAXSIZE];
    if(!Q.base) return ERROR;
    Q.front = 0;
    Q.rear = 0;
	return OK;
}
Status EnQueue(SqQueue& Q, int e)
{//在Q的队头插入新元素e
	if(Q.rear == (Q.front - 1 + MAXSIZE) % MAXSIZE)	return ERROR;
	Q.base[Q.front] = e;
	Q.front = (Q.front - 1 + MAXSIZE) % MAXSIZE;
	return OK;
}
Status DeQueue(SqQueue& Q)
{//删除Q的队尾元素，用e返回其值
	if(Q.front == Q.rear)	return 0;
	int e = Q.base[Q.rear];
	Q.rear = (Q.rear - 1 + MAXSIZE) % MAXSIZE;
    return e;
}
```

