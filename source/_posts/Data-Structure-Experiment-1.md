---
title: 数据结构实验一
date: 2023-10-14 09:54:07
tags:
  - [数据结构]
  - [C++]
categories: 作业
description: 数据结构实验一作业，发布在头歌平台，共计四十题
---

## 第1关：基于顺序存储结构的图书信息表的创建和输出

### 描述

定义一个包含图书信息（书号、书名、价格）的顺序表，读入相应的图书数据来完成图书信息表的创建，然后统计图书表中的图书个数，同时逐行输出每本图书的信息。

### 输入

输入n+1行，其中前n行是n本图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔，价格之后没有空格。最后第n+1行是输入结束标志：0 0 0（空格分隔的三个0）。其中书号和书名为字符串类型，价格为浮点数类型。

### 输出

总计n+1行，第1行是所创建的图书表中的图书个数，后n行是n本图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔。其中价格输出保留两位小数。

### 输入样例

```
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
0 0 0
```

### 输出样例

```
8
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
```

### 初始代码

```cpp
#include<iostream>
#include<string.h>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
#define MAXSIZE 1000    //图书表可能达到的最大长度
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct
{//图书表的顺序存储结构类型为SqList
    Book *elem;                   //存储空间的基地址
    int length;                   //图书表中当前图书个数
}SqList;
int InitList_Sq(SqList &L)
{//构造一个空的顺序表L
    
}
int Input_Sq(SqList &L)
{//顺序表的输入
    
}
int Output_Sq(SqList L)
{//顺序表的输出
    
}
```

### 代码

```cpp
#include<iostream>
#include<string.h>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
#define MAXSIZE 1000    //图书表可能达到的最大长度
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct
{//图书表的顺序存储结构类型为SqList
    Book *elem;                   //存储空间的基地址
    int length;                   //图书表中当前图书个数
}SqList;
int InitList_Sq(SqList &L)
{//构造一个空的顺序表L
    L.elem = new Book[MAXSIZE];
    L.length = 0;
}
int Input_Sq(SqList &L)
{//顺序表的输入
    Book book;
    while(cin >> book.no >> book.name >> book.price){
        if(strcmp(book.no, "0") == 0 && strcmp(book.name, "0") == 0 && book.price == 0) break;
        L.elem[L.length++] = book;
    }
}
int Output_Sq(SqList L)
{//顺序表的输出
    cout << L.length << '\n';
    for(int i = 0; i < L.length; i++){
        Book &book = L.elem[i];
        cout << book.no << ' ' << book.name << ' ' << fixed << setprecision(2) << book.price << '\n';
    }
}
```

## 第2关：基于顺序存储结构的图书信息表的排序

### 描述

定义一个包含图书信息（书号、书名、价格）的顺序表，读入相应的图书数据完成图书信息表的创建，然后将图书按照价格降序排序，逐行输出排序后每本图书的信息。

### 输入

输入n+1行，前n行是n本图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔，价格之后没有空格。最后第n+1行是输入结束标志：0 0 0（空格分隔的三个0）。其中书号和书名为字符串类型，价格为浮点数类型。

### 输出

总计n行，每行是一本图书的信息（书号、书名、价格），书号、书名、价格用空格分隔。其中价格输出保留两位小数。

### 输入样例

```
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
0 0 0
```

### 输出样例

```
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787302164340 Operating-System 50.00
9787822234110 The-C-Programming-Language 38.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257646 Data-Structure 35.00
9787302219972 Software-Engineer 32.00
```

### 初始代码

```cpp
#include<iostream>
#include<string.h>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
#define MAXSIZE 1000    //图书表可能达到的最大长度
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[60];   //图书名字
    float price;   //图书价格
}Book;
typedef struct
{//图书表的顺序存储结构类型为SqList
    Book *elem;                   //存储空间的基地址
    int length;                   //图书表中当前图书个数
}SqList;

int BubbleSort_Sq(SqList L)
{//图书顺序表按照价格降序冒泡排序
    
}
```

### 代码

```cpp
#include<iostream>
#include<string.h>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
#define MAXSIZE 1000    //图书表可能达到的最大长度
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[60];   //图书名字
    float price;   //图书价格
}Book;
typedef struct
{//图书表的顺序存储结构类型为SqList
    Book *elem;                   //存储空间的基地址
    int length;                   //图书表中当前图书个数
}SqList;

int BubbleSort_Sq(SqList L)
{//图书顺序表按照价格降序冒泡排序
    int length = L.length;
    Book *arr = L.elem;
    for(int i = length - 1; i >= 0; i--){
        for(int j = 0; j < i; j++){
            if(arr[j].price < arr[j + 1].price){
                swap(arr[j], arr[j + 1]);
            }
        }
    }
}
```

## 第3关：基于顺序存储结构的图书信息表的修改

### 描述

定义一个包含图书信息（书号、书名、价格）的顺序表，读入相应的图书数据完成图书信息表的创建，然后计算所有图书的平均价格，将所有低于平均价格的图书价格提高20%，所有高于或等于平均价格的图书价格提高10%，最后逐行输出价格修改后的图书信息。

### 输入

输入n+1行，前n行是n本图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔，价格之后没有空格。最后第n+1行是输入结束标志：0 0 0（空格分隔的三个0）。其中书号和书名为字符串类型，价格为浮点数类型。

### 输出

总计n+1行，第1行是修改前所有图书的平均价格，后n行是价格修改后n本图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔。其中价格输出保留两位小数。

### 输入样例

```
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
0 0 0
```



### 输出样例

```
43.88
9787302257646 Data-Structure 42.00
9787302164340 Operating-System 55.00
9787302219972 Software-Engineer 38.40
9787302203513 Database-Principles 43.20
9787810827430 Discrete-Mathematics 43.20
9787302257800 Data-Structure 68.20
9787811234923 Compiler-Principles 68.20
9787822234110 The-C-Programming-Language 45.60
```

### 初始代码

```cpp
#include<iostream>
#include<string.h>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
#define MAXSIZE 1000    //图书表可能达到的最大长度
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct
{//图书表的顺序存储结构类型为SqList
    Book *elem;                   //存储空间的基地址
    int length;                   //图书表中当前图书个数
}SqList;

int RevisePrice_Sq(SqList &L)
{//修改价格
    
}
```

### 代码

```cpp
#include<iostream>
#include<string.h>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
#define MAXSIZE 1000    //图书表可能达到的最大长度
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct
{//图书表的顺序存储结构类型为SqList
    Book *elem;                   //存储空间的基地址
    int length;                   //图书表中当前图书个数
}SqList;

double GetAveragePrice_Sq(SqList &L){
    if(L.length == 0) return 0;

    double total_price = 0;
    for(int i = 0; i < L.length; i++){
        total_price += L.elem[i].price;
    }

    return total_price / L.length;
}

int RevisePrice_Sq(SqList &L)
{//修改价格
    double avg_price = GetAveragePrice_Sq(L);

    cout << fixed << setprecision(2) << avg_price << '\n';

    for(int i = 0; i < L.length; i++){
        Book &book = L.elem[i];
        if(book.price >= avg_price){
            book.price *= 1.1;
        }
        else{
            book.price *= 1.2;
        }
    }
}
```

## 第4关：基于顺序存储结构的图书信息表的逆序存储

### 描述

定义一个包含图书信息（书号、书名、价格）的顺序表，读入相应的图书数据来完成图书信息表的创建，然后将读入的图书信息逆序存储，逐行输出逆序存储后每本图书的信息。

### 输入

输入n+1行，第一行是图书数目n，后n行是n本图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔，价格之后没有空格。其中书号和书名为字符串类型，价格为浮点数类型。

### 输出

总计n行，第i行是原有图书表中第n-i+1行的图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔。其中价格输出保留两位小数。

### 输入样例

```
8
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
```

### 输出样例

```
9787822234110 The-C-Programming-Language 38.00
9787811234923 Compiler-Principles 62.00
9787302257800 Data-Structure 62.00
9787810827430 Discrete-Mathematics 36.00
9787302203513 Database-Principles 36.00
9787302219972 Software-Engineer 32.00
9787302164340 Operating-System 50.00
9787302257646 Data-Structure 35.00
```

### 初始代码

```cpp
#include<iostream>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
#define MAXSIZE 1000                                  //图书表可能达到的最大长度
using namespace std;
typedef struct
{//图书信息定义
    char no[20];                                        //图书ISBN
    char name[60];                                     //图书名字
    float price;                                       //图书价格
}Book;
typedef struct
{//图书表的顺序存储结构类型为SqList
    Book *elem;                                         //存储空间的基地址
    int length;                                        //图书表中当前图书个数
}SqList;

int Input_Sq(SqList &L)
{//顺序表的输入
   
}
```

### 代码

```cpp
#include<iostream>
#include<iomanip>
#include<cstring>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
#define MAXSIZE 1000                                  //图书表可能达到的最大长度
using namespace std;
typedef struct
{//图书信息定义
    char no[20];                                        //图书ISBN
    char name[60];                                     //图书名字
    float price;                                       //图书价格
}Book;
typedef struct
{//图书表的顺序存储结构类型为SqList
    Book *elem;                                         //存储空间的基地址
    int length;                                        //图书表中当前图书个数
}SqList;

void ReverseBook(SqList &L){
//把图书信息逆序存储 
	Book *arr = L.elem;
    int length = L.length;
    for(int i = 0; i < length / 2; i++){
        swap(arr[i], arr[length - i - 1]);
    }
}

int Input_Sq(SqList &L)
{//顺序表的输入
    cin >> L.length;
    for(int i = 0; i < L.length; i++){
        Book &book = L.elem[i];
        cin >> book.no >> book.name >> book.price;
    }
    ReverseBook(L);
}
```



## 第5关：基于顺序存储结构的图书信息表的最贵图书的查找

### 描述

本关任务：定义一个包含图书信息（书号、书名、价格）的顺序表，读入相应的图书数据来完成图书信息表的创建，然后查找价格最高的图书，输出相应图书的信息。

### 输入

总计输入n+1行，其中，第一行是图书数目n，后n行是n本图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔，价格之后没有空格。其中书号和书名为字符串类型，价格为浮点数类型。

### 输出

总计输出m+1行，其中，第一行是最贵图书的数目（价格最高的图书可能有多本），后m行是最贵图书的信息，每本图书信息占一行，书号、书名、价格用空格分隔，其中价格输出保留两位小数。

### 输入样例

```
8
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
```

### 输出样例

```
2
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
```

### 初始代码

```cpp
#include<iostream>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
#define MAXSIZE 1000    //图书表可能达到的最大长度
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct
{//图书表的顺序存储结构类型为SqList
    Book *elem;                   //存储空间的基地址
    int length;                   //图书表中当前图书个数
}SqList;

int HighestPrice_Sq(SqList L)
{//查找价格最高的图书并输出相应图书的信息
    
}
```

### 代码

```cpp
#include<iostream>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
#define MAXSIZE 1000    //图书表可能达到的最大长度
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct
{//图书表的顺序存储结构类型为SqList
    Book *elem;                   //存储空间的基地址
    int length;                   //图书表中当前图书个数
}SqList;

int HighestPrice_Sq(SqList L)
{//查找价格最高的图书并输出相应图书的信息
    float hst_price = 0;
    for(int i = 0; i < L.length; i++){
        Book &book = L.elem[i];
        hst_price = max(hst_price, book.price);
    }

    int hst_book_num = 0;
    for(int i = 0; i < L.length; i++){
        Book &book = L.elem[i];
        if(book.price == hst_price){
            hst_book_num++;
        }
    }

    cout << hst_book_num << '\n';

    for(int i = 0; i < L.length; i++){
        Book &book = L.elem[i];
        if(book.price == hst_price){
            cout << book.no << ' ' << book.name << ' ' << fixed << setprecision(2) << book.price << '\n';
        }
    }
}
```



## 第6关：基于顺序存储结构的图书信息表的最爱图书的查找

### 描述

定义一个包含图书信息（书号、书名、价格）的顺序表，读入相应的图书数据来完成图书信息表的创建，然后根据指定的最爱图书的名字，查找最爱的图书，输出相应图书的信息。

### 输入

总计n+m+2行。首先输入n+1行，其中，第一行是图书数目n，后n行是n本图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔，价格之后没有空格。其中书号和书名为字符串类型，价格为浮点数类型。然后输入m+1行，其中，第一行是一个整数m，代表查找m次，后m行是每次待查找的最爱图书名字。

### 输出

若查找成功： 总计输出m*（k+1）行，对于每一次查找，第一行是最爱图书数目（同一书名的图书可能有多本），后k行是最爱图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔，其中价格输出保留两位小数。 若查找失败： 只输出以下提示：抱歉，没有你的最爱！

### 输入样例

```
8
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
2
Java-Programming-Language
Data-Structure
```

### 输出样例

```
Sorry，there is no your favourite!
2
9787302257646 Data-Structure 35.00
9787302257800 Data-Structure 62.00
```

### 初始代码

```cpp
#include<iostream>
#include<string.h>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
#define MAXSIZE 1000    //图书表可能达到的最大长度
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct
{//图书表的顺序存储结构类型为SqList
    Book *elem;                   //存储空间的基地址
    int length;                   //图书表中当前图书个数
}SqList;

int FindFavorite_Sq(SqList L)
{//最爱图书的查找并输出数据
    
}
```

### 代码

```cpp
#include<iostream>
#include<string.h>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
#define MAXSIZE 1000    //图书表可能达到的最大长度
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct
{//图书表的顺序存储结构类型为SqList
    Book *elem;                   //存储空间的基地址
    int length;                   //图书表中当前图书个数
}SqList;

int FindFavorite_Sq(SqList L)
{//最爱图书的查找并输出数据
    int m;
    cin >> m;
    while(m--){
        char name[50];
        cin >> name;
        
        int cnt = 0;
        for(int i = 0; i < L.length; i++){
            Book &book = L.elem[i];
            if(strcmp(name, book.name) == 0){
                cnt++;
            }
        }

        if(cnt == 0){
            cout << "Sorry，there is no your favourite!\n";
        }
        else{
            cout << cnt << '\n';
            for(int i = 0; i < L.length; i++){
                Book &book = L.elem[i];
                if(strcmp(name, book.name) == 0){
                    cout << book.no << ' ' << book.name << ' ' << fixed << setprecision(2) << book.price << '\n';
                }
            }
        }
    } 
}
```



## 第7关：基于顺序存储结构的图书信息表的最佳位置图书的查找

### 描述

定义一个包含图书信息（书号、书名、价格）的顺序表，读入相应的图书数据来完成图书信息表的创建，然后根据指定的最佳位置的序号，查找该位置上的图书，输出相应图书的信息。

### 输入

总计n+m+2行。首先输入n+1行，其中，第一行是图书数目n，后n行是n本图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔，价格之后没有空格。其中书号和书名为字符串类型，价格为浮点数类型。然后输入m+1行，其中，第一行是一个整数m，代表查找m次，后m行每行内容为一个整数，代表待查找的图书的位置序号。

### 输出

输出m行 若查找成功： 输出内容为第i次查询的指定位置上的一本图书的信息（书号、书名、价格），书号、书名、价格用空格分隔，其中价格输出保留两位小数。 若查找失败： 只输出以下提示：抱歉，最佳位置上的图书不存在！

### 输入样例

```
8
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
2
2
0
```

### 输出样例

```
9787302164340 Operating-System 50.00
Sorry，the book on the best position doesn't exist!
```

### 初始代码

```cpp
#include<iostream>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
#define MAXSIZE 1000    //图书表可能达到的最大长度
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct
{//图书表的顺序存储结构类型为SqList
    Book *elem;                   //存储空间的基地址
    int length;                   //图书表中当前图书个数
}SqList;

int FindLocate_Sq(SqList L)
{//查找最佳位置图书并输出数据
    
}
```

### 代码

```cpp
#include<iostream>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
#define MAXSIZE 1000    //图书表可能达到的最大长度
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct
{//图书表的顺序存储结构类型为SqList
    Book *elem;                   //存储空间的基地址
    int length;                   //图书表中当前图书个数
}SqList;

int FindLocate_Sq(SqList L)
{//查找最佳位置图书并输出数据
    int m;
    cin >> m;
    while(m--){
        int pos;
        cin >> pos;
        if(pos <= 0 || pos > L.length){
            cout << "Sorry，the book on the best position doesn't exist!\n";
        }
        else{
            Book &book = L.elem[pos - 1];
            cout << book.no << ' ' << book.name << ' ' << fixed << setprecision(2) << book.price << '\n';
        }
    }
}
```



## 第8关：基于顺序存储结构的图书信息表的新图书的入库

### 描述

定义一个包含图书信息（书号、书名、价格）的顺序表，读入相应的图书数据来完成图书信息表的创建，然后根据指定的待入库的新图书的位置和信息，将新图书插入到图书表中指定的位置上，最后输出新图书入库后所有图书的信息。

### 输入

总计n+3行。首先输入n+1行，其中，第一行是图书数目n，后n行是n本图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔，价格之后没有空格。其中书号和书名为字符串类型，价格为浮点数类型。之后输入第n+2行，内容仅为一个整数，代表待入库的新图书的位置序号。最后输入第n+3行，内容为新图书的信息，书号、书名、价格用空格分隔。

### 输出

若插入成功： 输出新图书入库后所有图书的信息（书号、书名、价格），总计n+1行，每行是一本图书的信息，书号、书名、价格用空格分隔。其中价格输出保留两位小数。 若插入失败： 只输出以下提示：抱歉，入库位置非法！

### 输入样例 #1

```
7
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
2
9787822234110 The-C-Programming-Language 38.00
```

### 输出样例 #1

```
9787302257646 Data-Structure 35.00
9787822234110 The-C-Programming-Language 38.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
```

### 输入样例 #2

```
7
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9
9787822234110 The-C-Programming-Language 38.00
```

### 输出样例 #2

```
Sorry，the position to be inserted is invalid!
```

### 初始代码

```cpp
#include<iostream>
#include <string.h>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
#define MAXSIZE 1000    //图书表可能达到的最大长度
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct
{//图书表的顺序存储结构类型为SqList
    Book *elem;                   //存储空间的基地址
    int length;                   //图书表中当前图书个数
}SqList;

int Insert_Sq(SqList &L)
{//新图书的入库和输出
    
}
```

### 代码

```cpp
#include<iostream>
#include <string.h>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
#define MAXSIZE 1000    //图书表可能达到的最大长度
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct
{//图书表的顺序存储结构类型为SqList
    Book *elem;                   //存储空间的基地址
    int length;                   //图书表中当前图书个数
}SqList;

int Output_Sq(SqList L)
{//顺序表的输出
    for(int i = 0; i < L.length; i++){
        Book &book = L.elem[i];
        cout << book.no << ' ' << book.name << ' ' << fixed << setprecision(2) << book.price << '\n';
    }
}

int Insert_Sq(SqList &L)
{//新图书的入库和输出
    int pos;
    Book book;
    cin >> pos;
    cin >> book.no >> book.name >> book.price;
    if(pos <= 0 || pos > L.length + 1){
        cout << "Sorry，the position to be inserted is invalid!\n";
        return ERROR;
    }

    memmove(L.elem + pos, L.elem + pos - 1, sizeof(Book) * (L.length - pos + 1));
    memmove(L.elem + pos - 1, &book, sizeof(Book));
    L.length++;

    Output_Sq(L);

    return OK;
}
```



## 第9关：基于顺序存储结构的图书信息表的旧图书的出库

### 描述

定义一个包含图书信息（书号、书名、价格）的顺序表，读入相应的图书数据来完成图书信息表的创建，然后根据指定的待出库的旧图书的位置，将该图书从图书表中删除，最后输出该图书出库后的所有图书的信息。

### 输入

总计n+2行。首先输入n+1行，其中，第一行是图书数目n，后n行是n本图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔，价格之后没有空格。其中书号和书名为字符串类型，价格为浮点数类型。之后输入第n+2行，内容仅为一个整数，代表待删除的旧图书的位置序号。

### 输出

若删除成功： 输出旧图书出库后所有图书的信息（书号、书名、价格），总计n-1行，每行是一本图书的信息，书号、书名、价格用空格分隔。其中价格输出保留两位小数。 若删除失败： 只输出以下提示：抱歉，出库位置非法！

### 输入样例 #1

```
8
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
2
```

### 输出样例 #1

```
9787302257646 Data-Structure 35.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
```

### 输入样例 #2

```
8
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
9
```

### 输出样例 #2

```
Sorry，the position to be deleted is invalid!
```

### 初始代码

```cpp
#include<iostream>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
#define MAXSIZE 1000    //图书表可能达到的最大长度
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct
{//图书表的顺序存储结构类型为SqList
    Book *elem;                   //存储空间的基地址
    int length;                   //图书表中当前图书个数
}SqList;
int Delete_Sq(SqList &L)
{//旧图书的出库和输出
    
}
```

### 代码

```cpp
#include<iostream>
#include<iomanip>
#include<cstring>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
#define MAXSIZE 1000    //图书表可能达到的最大长度
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct
{//图书表的顺序存储结构类型为SqList
    Book *elem;                   //存储空间的基地址
    int length;                   //图书表中当前图书个数
}SqList;

int Output_Sq(SqList L)
{//顺序表的输出
    for(int i = 0; i < L.length; i++){
        Book &book = L.elem[i];
        cout << book.no << ' ' << book.name << ' ' << fixed << setprecision(2) << book.price << '\n';
    }
}

int Delete_Sq(SqList &L)
{//旧图书的出库和输出
    int pos;
    cin >> pos;
    if(pos <= 0 || pos > L.length){
        cout << "Sorry，the position to be deleted is invalid!\n";
        return ERROR;
    }

    memmove(L.elem + pos - 1, L.elem + pos, sizeof(Book) * (L.length - pos));
    L.length--;

    Output_Sq(L);

    return OK;
}
```



## 第10关：基于顺序存储结构的图书信息表的图书去重

### 描述

出版社出版的任何一本图书的书号（ISBN）都是唯一的，即图书表中不允许包含书号重复的图书。定义一个包含图书信息（书号、书名、价格）的顺序表，读入相应的图书数据来完成图书信息表的创建（书号可能重复），然后进行图书的去重，即删除书号重复的图书（只保留第一本），最后输出去重后所有图书的信息。

### 输入

总计输入n+1行，其中，第一行是图书数目n，后n行是n本图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔，价格之后没有空格（书号可能重复）。其中书号和书名为字符串类型，价格为浮点数类型。

### 输出

总计输出m+1行（m≤n），其中，第一行是去重后的图书数目，后m行是去重后图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔，其中价格输出保留两位小数。

### 输入样例

```
9
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
```

### 输出样例

```
8
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
```

### 初始代码

```cpp
#include<iostream>
#include<string.h>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
#define MAXSIZE 1000    //图书表可能达到的最大长度
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct
{//图书表的顺序存储结构类型为SqList
    Book *elem;                   //存储空间的基地址
    int length;                   //图书表中当前图书个数
}SqList;

int SearchList(SqList L,char no[20])
{//查找书号是否在图书信息表L中
	
}
int DupRemoval_Sq(SqList L1,SqList &L2)
{//图书去重
   
}
```

### 代码

```cpp
#include<iostream>
#include<string.h>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
#define MAXSIZE 1000    //图书表可能达到的最大长度
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct
{//图书表的顺序存储结构类型为SqList
    Book *elem;                   //存储空间的基地址
    int length;                   //图书表中当前图书个数
}SqList;

int Output_Sq(SqList L)
{//顺序表的输出
    cout << L.length << '\n';
    for(int i = 0; i < L.length; i++){
        Book &book = L.elem[i];
        cout << book.no << ' ' << book.name << ' ' << fixed << setprecision(2) << book.price << '\n';
    }
}

int SearchList(const SqList &L,char no[20])
{//查找书号是否在图书信息表L中
	for(int i = 0; i < L.length; i++){
        Book &book = L.elem[i];
        if(strcmp(book.no, no) == 0){
            return i;
        }
    }
    return -1;
}

int DupRemoval_Sq(SqList L1,SqList &L2)
{//图书去重
   for(int i = 0; i < L1.length; i++){
        Book &book = L1.elem[i];
        if(SearchList(L2, book.no) != -1) continue;
        L2.elem[L2.length++] = book;
    }

    Output_Sq(L2);
}
```



## 第11关：基于链式存储结构的图书信息表的创建和输出

### 描述

定义一个包含图书信息（书号、书名、价格）的链表，读入相应的图书数据来完成图书信息表的创建，然后统计图书表中的图书个数，同时逐行输出每本图书的信息。

### 输入

输入n+1行，其中前n行是n本图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔，价格之后没有空格。最后第n+1行是输入结束标志：0 0 0（空格分隔的三个0）。其中书号和书名为字符串类型，价格为浮点数类型。

### 输出

总计n+1行，第1行是所创建的图书表中的图书个数，后n行是n本图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔。其中价格输出保留两位小数。

### 输入样例

```
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
0 0 0
```

### 输出样例

```
8
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
```

### 初始代码

```cpp
#include<iostream>
#include<string.h>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct LNode
{//图书信息表的链式存储结构
    Book data;    	   //结点的数据域
    int length;       //链表的表长，即图书表中图书个数
    struct LNode *next; //指针域
}LNode,*LinkList;

int  Length_L(LinkList &L)
{//求链表的表长，即图书表中图书个数
    
}
```

### 代码

```cpp
#include<iostream>
#include<string.h>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct LNode
{//图书信息表的链式存储结构
    Book data;    	   //结点的数据域
    int length;       //链表的表长，即图书表中图书个数
    struct LNode *next; //指针域
}LNode,*LinkList;

int  Length_L(LinkList &L)
{//求链表的表长，即图书表中图书个数
    L -> length = 0;
    LinkList p = L -> next;
    while(p){
        p = p -> next;
        L -> length++;
    }
    
    cout << L -> length << '\n';
    return OK;
}
```



## 第12关：基于链式存储结构的图书信息表的排序

### 描述

定义一个包含图书信息（书号、书名、价格）的链表，读入相应的图书数据完成图书信息表的创建，然后将图书按照价格降序排序，逐行输出排序后每本图书的信息。

### 输入

输入n+1行，前n行是n本图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔，价格之后没有空格。最后第n+1行是输入结束标志：0 0 0（空格分隔的三个0）。其中书号和书名为字符串类型，价格为浮点数类型。

### 输出

总计n行，每行是一本图书的信息（书号、书名、价格），书号、书名、价格用空格分隔。其中价格输出保留两位小数。

### 输入样例

```
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
0 0 0
```

### 输出样例

```
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787302164340 Operating-System 50.00
9787822234110 The-C-Programming-Language 38.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257646 Data-Structure 35.00
9787302219972 Software-Engineer 32.00
```

### 初始代码

```cpp
#include<iostream>
#include<string.h>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct LNode
{//图书信息表的链式存储结构
    Book data;    	   //结点的数据域
    int length;       //链表的表长，即图书表中图书个数
    struct LNode *next; //指针域
}LNode,*LinkList;

int Sort_L(LinkList &L)
{//将图书按照价格降序排序
    
}
```

### 代码

```cpp
#include<iostream>
#include<string.h>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct LNode
{//图书信息表的链式存储结构
    Book data;    	   //结点的数据域
    int length;       //链表的表长，即图书表中图书个数
    struct LNode *next; //指针域
}LNode,*LinkList;

void Swap(LinkList front, LinkList& lhs, LinkList& rhs){
    front -> next = rhs;
    lhs -> next = rhs -> next;
    rhs -> next = lhs;
    swap(lhs, rhs);
}

int  Length_LN(LinkList &L)
{//求链表的表长，即图书表中图书个数
    L -> length = 0;
    LinkList p = L -> next;
    while(p){
        p = p -> next;
        L -> length++;
    }
    
    return L -> length;
}

int Sort_L(LinkList &L)
{//将图书按照价格降序排序
    int length = Length_LN(L);
    if(length <= 1) return OK;
    for(int i = 1; i < length; i++){
        LinkList r = L;
        LinkList p = r -> next;
        LinkList q = p -> next;
        for(; q; r = p, p = q, q = q -> next){
            if(p -> data.price < q -> data.price){
                Swap(r, p, q);
            }
        }
    }
    return OK;
}
```



## 第13关：基于链式存储结构的图书信息表的修改

### 描述

定义一个包含图书信息（书号、书名、价格）的链表，读入相应的图书数据完成图书信息表的创建，然后计算所有图书的平均价格，将所有低于平均价格的图书价格提高20%，所有高于或等于平均价格的图书价格提高10%，最后逐行输出价格修改后的图书信息。

### 输入

输入n+1行，前n行是n本图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔，价格之后没有空格。最后第n+1行是输入结束标志：0 0 0（空格分隔的三个0）。其中书号和书名为字符串类型，价格为浮点数类型。

### 输出

总计n+1行，第1行是修改前所有图书的平均价格，后n行是价格修改后n本图书的信息，每本图书信息占一行，书号、书名、价格用空格分隔。其中价格输出保留两位小数。

### 输入样例

```
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
0 0 0
```

### 输出样例

```
43.88
9787302257646 Data-Structure 42.00
9787302164340 Operating-System 55.00
9787302219972 Software-Engineer 38.40
9787302203513 Database-Principles 43.20
9787810827430 Discrete-Mathematics 43.20
9787302257800 Data-Structure 68.20
9787811234923 Compiler-Principles 68.20
9787822234110 The-C-Programming-Language 45.60
```

### 初始代码

```cpp
#include<iostream>
#include<string.h>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct LNode
{//图书信息表的链式存储结构
    Book data;    	   //结点的数据域
    int length;       //链表的表长，即图书表中图书个数
    struct LNode *next; //指针域
}LNode,*LinkList;
int AveRevise_L(LinkList &L)
{//计算所有图书的平均价格并修改价格
    
}
```

### 代码

```cpp
#include<iostream>
#include<string.h>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct LNode
{//图书信息表的链式存储结构
    Book data;    	   //结点的数据域
    int length;       //链表的表长，即图书表中图书个数
    struct LNode *next; //指针域
}LNode,*LinkList;
int AveRevise_L(LinkList &L)
{//计算所有图书的平均价格并修改价格
    double total_price = 0;
    int length = 0;
    for(LinkList p = L -> next; p; p = p -> next){
        total_price += p -> data.price;
        length++;
    }
    if(length == 0) return OK;
    double avg = total_price / length;

    cout << fixed << setprecision(2) << avg << '\n';
    for(LinkList p = L -> next; p; p = p -> next){
        Book &book = p -> data;
        if(book.price < avg){
            book.price *= 1.2;
        }
        else{
            book.price *= 1.1;
        }
    }

    return OK;
}
```



## 第14关：基于链式存储结构的图书信息表的逆序存储

### 描述

定义一个包含图书信息（书号、书名、价格）的链表，读入相应的图书数据来完成图书信息表的创建，然后将读入的图书逆序存储，逐行输出逆序存储后每本图书的信息。

### 输入

输入n+1行，第一行是图书数目n，后n行是n本图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔，价格之后没有空格。其中书号和书名为字符串类型，价格为浮点数类型。

### 输出

总计n行，第i行是原有图书表中第n-i+1行的图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔。其中价格输出保留两位小数。

### 输入样例

```
8
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
```

### 输出样例

```
9787822234110 The-C-Programming-Language 38.00
9787811234923 Compiler-Principles 62.00
9787302257800 Data-Structure 62.00
9787810827430 Discrete-Mathematics 36.00
9787302203513 Database-Principles 36.00
9787302219972 Software-Engineer 32.00
9787302164340 Operating-System 50.00
9787302257646 Data-Structure 35.00
```

### 初始代码

```cpp
#include<iostream>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct LNode
{//图书信息表的链式存储结构
    Book data;    	   //结点的数据域
    int length;       //链表的表长，即图书表中图书个数
    struct LNode *next; //指针域
}LNode,*LinkList;
int Input_L(LinkList &L)
{//链表的输入
    
}
```

### 代码

```cpp
#include<iostream>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct LNode
{//图书信息表的链式存储结构
    Book data;    	   //结点的数据域
    int length;       //链表的表长，即图书表中图书个数
    struct LNode *next; //指针域
}LNode,*LinkList;
int Input_L(LinkList &L)
{//链表的输入
    int n;
    cin >> n;
    LinkList p_tail = L;
    while(n--){
        p_tail -> next = new LNode;
        p_tail = p_tail -> next;
        p_tail -> next = nullptr;
        cin >> p_tail -> data.no >> p_tail -> data.name >> p_tail -> data.price;
    }
    L -> length = n;

    LinkList r = nullptr;
    LinkList p = L -> next;
    while(p){
        LinkList q = p -> next;
        p -> next = r;
        r = p;
        p = q;
    }
    L -> next = r;
}
```



## 第14关：基于链式存储结构的图书信息表的逆序存储

### 描述



### 输入



### 输出



### 输入样例

```

```

### 输出样例

```

```

### 初始代码

```cpp

```

### 代码

```cpp

```



## 第15关：基于链式存储结构的图书信息表的最贵图书的查找

### 描述

定义一个包含图书信息（书号、书名、价格）的链表，读入相应的图书数据来完成图书信息表的创建，然后查找价格最高的图书，输出相应图书的信息。

### 输入

总计输入n+1行，其中，第一行是图书数目n，后n行是n本图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔，价格之后没有空格。其中书号和书名为字符串类型，价格为浮点数类型。

### 输出

总计输出m+1行，其中，第一行是最贵图书数目（价格最高的图书可能有多本），后m行是最贵图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔，其中价格输出保留两位小数。

### 输入样例

```
8
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
```

### 输出样例

```
2
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
```

### 初始代码

```cpp
#include<iostream>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
using namespace std;
typedef struct
{//图书信息定义
    char no[20];     //图书ISBN
    char name[50];   //图书名字
    float price;     //图书价格
}Book;
typedef struct LNode
{//图书信息表的链式存储结构
    Book data;    	   //结点的数据域
    int length;       //链表的表长，即图书表中图书个数
    struct LNode *next; //指针域
}LNode,*LinkList;
int HighestPrice_L(LinkList L)
{//查找价格最高的图书
   
}
```

### 代码

```cpp
#include<iostream>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
using namespace std;
typedef struct
{//图书信息定义
    char no[20];     //图书ISBN
    char name[50];   //图书名字
    float price;     //图书价格
}Book;
typedef struct LNode
{//图书信息表的链式存储结构
    Book data;    	   //结点的数据域
    int length;       //链表的表长，即图书表中图书个数
    struct LNode *next; //指针域
}LNode,*LinkList;
int HighestPrice_L(LinkList L)
{//查找价格最高的图书
   float hst_price = 0;
   for(LinkList p = L -> next; p; p = p -> next){
       hst_price = max(hst_price, p -> data.price);
   }

   int cnt = 0;
   for(LinkList p = L -> next; p; p = p -> next){
       if(hst_price == p -> data.price){
           cnt++;
       }
   }

   cout << cnt << '\n';
   for(LinkList p = L -> next; p; p = p -> next){
       if(hst_price == p -> data.price){
           cout << p -> data.no << ' ' << p -> data.name << ' ' << fixed << setprecision(2) << p -> data.price << '\n';
       }
   }
}
```



## 第16关：基于链式存储结构的图书信息表的最爱图书的查找

### 描述

定义一个包含图书信息（书号、书名、价格）的链表，读入相应的图书数据来完成图书信息表的创建，然后根据指定的最爱图书的名字，查找最爱的图书，输出相应图书的信息。

### 输入

总计n+m+2行。首先输入n+1行，其中，第一行是图书数目n，后n行是n本图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔，价格之后没有空格。其中书号和书名为字符串类型，价格为浮点数类型。然后输入m+1行，其中，第一行是一个整数m，代表查找m次，后m行是每次待查找的最爱图书名字。

### 输出

若查找成功： 总计输出m*（k+1）行，对于每一次查找，第一行是最爱图书数目（同一书名的图书可能有多本），后k行是最爱图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔，其中价格输出保留两位小数。 若查找失败： 只输出以下提示：抱歉，没有你的最爱！

### 输入样例

```
8
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
2
Java-Programming-Language
Data-Structure
```

### 输出样例

```
Sorry，there is no your favourite!
2
9787302257646 Data-Structure 35.00
9787302257800 Data-Structure 62.00
```

### 初始代码

```cpp
#include<iostream>
#include<string.h>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct LNode
{//图书信息表的链式存储结构
    Book data;    	   //结点的数据域
    int length;       //链表的表长，即图书表中图书个数
    struct LNode *next; //指针域
}LNode,*LinkList;
int FindFavorite_L(LinkList &L)
{//查找的最爱图书并输出数据

}
```

### 代码

```cpp
#include<iostream>
#include<string.h>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct LNode
{//图书信息表的链式存储结构
    Book data;    	   //结点的数据域
    int length;       //链表的表长，即图书表中图书个数
    struct LNode *next; //指针域
}LNode,*LinkList;
int FindFavorite_L(LinkList &L)
{//查找的最爱图书并输出数据
    int n;
    cin >> n;
    while(n--){
        char name[50];
        cin >> name;

        int cnt = 0;
        for(LinkList p = L -> next; p; p = p -> next){
            if(strcmp(name, p -> data.name) == 0){
                cnt++;
            }
        }

        if(cnt == 0){
            cout << "Sorry，there is no your favourite!" << '\n';
        }
        else{
            cout << cnt << '\n';
            for(LinkList p = L -> next; p; p = p -> next){
                if(strcmp(name, p -> data.name) == 0){
                    cout << p -> data.no << ' ' << p -> data.name << ' ' << fixed << setprecision(2) << p -> data.price << '\n';
                }
            }
        }
    }
}
```



## 第17关：基于链式存储结构的图书信息表的最佳位置图书的查找

### 描述

定义一个包含图书信息（书号、书名、价格）的链表，读入相应的图书数据来完成图书信息表的创建，然后根据指定的最佳位置的序号，查找该位置上的图书，输出相应图书的信息。

### 输入

总计n+m+2行。首先输入n+1行，其中，第一行是图书数目n，后n行是n本图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔，价格之后没有空格。其中书号和书名为字符串类型，价格为浮点数类型。然后输入m+1行，其中，第一行是一个整数m，代表查找m次，后m行每行内容为一个整数，代表待查找的图书的位置序号。

### 输出

输出m行 若查找成功： 输出内容为第i次查询的指定位置上的一本图书的信息（书号、书名、价格），书号、书名、价格用空格分隔，其中价格输出保留两位小数。 若查找失败： 只输出以下提示：抱歉，最佳位置上的图书不存在！

### 输入样例

```
8
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
2
2
0
```

### 输出样例

```
9787302164340 Operating-System 50.00
Sorry，the book on the best position doesn't exist!
```

### 初始代码

```cpp
#include<iostream>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct LNode
{//图书信息表的链式存储结构
    Book data;    	   //结点的数据域
    int length;       //链表的表长，即图书表中图书个数
    struct LNode *next; //指针域
}LNode,*LinkList;
int Locate_L(LinkList L)
{//查找最佳位置的图书并输出数据
 
}
```

### 代码

```cpp
#include<iostream>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct LNode
{//图书信息表的链式存储结构
    Book data;    	   //结点的数据域
    int length;       //链表的表长，即图书表中图书个数
    struct LNode *next; //指针域
}LNode,*LinkList;
int Locate_L(LinkList L)
{//查找最佳位置的图书并输出数据
    int n;
    cin >> n;
    while(n--){
        int pos;
        cin >> pos;

        if(pos <= 0){
            cout << "Sorry，the book on the best position doesn't exist!" << '\n';
            continue;
        }

        LinkList p = L;
        while(p && pos){
            p = p -> next;
            pos--;
        }

        if(!p){
            cout << "Sorry，the book on the best position doesn't exist!" << '\n';
            continue;
        }

        cout << p -> data.no << ' ' << p -> data.name << ' ' << fixed << setprecision(2) << p -> data.price << '\n';
    }
}
```



## 第18关：基于链式存储结构的图书信息表的新图书的入库

### 描述

本关任务：定义一个包含图书信息（书号、书名、价格）的链表，读入相应的图书数据来完成图书信息表的创建，然后根据指定的待入库的新图书的位置和图书的信息，将新图书插入到图书表中指定的位置上，最后输出新图书入库后的所有图书的信息。

### 输入

总计n+3行。首先输入n+1行，其中，第一行是图书数目n，后n行是n本图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔，价格之后没有空格。其中书号和书名为字符串类型，价格为浮点数类型。之后输入第n+2行，内容仅为一个整数，代表待入库的新图书的位置序号。最后输入第n+3行，内容为新图书的信息，书号、书名、价格用空格分隔。

### 输出

若插入成功： 输出新图书入库后所有图书的信息（书号、书名、价格），总计n+1行，每行是一本图书的信息，书号、书名、价格用空格分隔。其中价格输出保留两位小数。 若插入失败： 只输出以下一行提示：抱歉，入库位置非法！

### 输入样例 #1

```
7
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
2
9787822234110 The-C-Programming-Language 38.00
```

### 输出样例 #1

```
9787302257646 Data-Structure 35.00
9787822234110 The-C-Programming-Language 38.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
```

### 输入样例 #2

```
7
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9
9787822234110 The-C-Programming-Language 38.00
```

### 输出样例 #2

```
Sorry，the position to be inserted is invalid!
```

### 初始代码

```cpp
#include<iostream>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct LNode
{//图书信息表的链式存储结构
    Book data;    	   //结点的数据域
    int length;       //链表的表长，即图书表中图书个数
    struct LNode *next; //指针域
}LNode,*LinkList;
int Insert_L(LinkList &L)
{//将新图书入库并输出

}
```

### 代码

```cpp
#include<iostream>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct LNode
{//图书信息表的链式存储结构
    Book data;    	   //结点的数据域
    int length;       //链表的表长，即图书表中图书个数
    struct LNode *next; //指针域
}LNode,*LinkList;
int Insert_L(LinkList &L)
{//将新图书入库并输出
    int pos;
    Book book;
    cin >> pos;
    cin >> book.no >> book.name >> book.price;
    if(pos <= 0){
        cout << "Sorry，the position to be inserted is invalid!" << '\n';
        return ERROR;
    }

    LinkList r = L;
    while(r && pos - 1){
        r = r -> next;
        pos--;
    }

    if(!r){
        cout << "Sorry，the position to be inserted is invalid!" << '\n';
        return ERROR;
    }

    LinkList p = new LNode;
    p -> data = book;
    
    p -> next = r -> next;
    r -> next = p;

    for(LinkList p = L -> next; p; p = p -> next){
        cout << p -> data.no << ' ' << p -> data.name << ' ' << fixed << setprecision(2) << p -> data.price << '\n';
    }

    return OK;
}
```



## 第19关：基于链式存储结构的图书信息表的旧图书的出库

### 描述

定义一个包含图书信息（书号、书名、价格）的链表，读入相应的图书数据来完成图书信息表的创建，然后根据指定的待出库的旧图书的位置，将该图书从图书表中删除，最后输出该图书出库后的所有图书的信息。

### 输入

总计n+2行。首先输入n+1行，其中，第一行是图书数目n，后n行是n本图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔，价格之后没有空格。其中书号和书名为字符串类型，价格为浮点数类型。之后输入第n+2行，内容仅为一个整数，代表待删除的旧图书的位置序号。

### 输出

若删除成功： 输出旧图书出库后所有图书的信息（书号、书名、价格），总计n-1行，每行是一本图书的信息，书号、书名、价格用空格分隔。其中价格输出保留两位小数。 若删除失败： 只输出以下一行提示：抱歉，出库位置非法！

### 输入样例 #1

```
8
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
2
```

### 输出样例 #1

```
9787302257646 Data-Structure 35.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
```

### 输入样例 #2

```
8
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
9
```

### 输出样例 #2

```
Sorry，the position to be deleted is invalid!
```

### 初始代码

```cpp
#include<iostream>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct LNode
{//图书信息表的链式存储结构
    Book data;    	   //结点的数据域
    int length;       //链表的表长，即图书表中图书个数
    struct LNode *next; //指针域
}LNode,*LinkList;
int Delete_L(LinkList &L)
{//出库旧图书并输出
   
}
```

### 代码

```cpp
#include<iostream>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct LNode
{//图书信息表的链式存储结构
    Book data;    	   //结点的数据域
    int length;       //链表的表长，即图书表中图书个数
    struct LNode *next; //指针域
}LNode,*LinkList;
int Delete_L(LinkList &L)
{//出库旧图书并输出
    int pos;
    cin >> pos;
    if(pos <= 0){
        cout << "Sorry，the position to be inserted is invalid!" << '\n';
        return ERROR;
    }

    LinkList r = L;
    while(r -> next && pos - 1){
        r = r -> next;
        pos--;
    }

    if(!r -> next){
        cout << "Sorry，the position to be deleted is invalid!" << '\n';
        return ERROR;
    }
    
    LinkList p = r -> next;
    r -> next = p -> next;
    delete p;

    for(LinkList p = L -> next; p; p = p -> next){
        cout << p -> data.no << ' ' << p -> data.name << ' ' << fixed << setprecision(2) << p -> data.price << '\n';
    }

    return OK;
}
```



## 第20关：基于链存储结构的图书信息表的图书去重

### 描述

出版社出版的任何一本图书的书号（ISBN）都是唯一的，即图书表中不允许包含书号重复的图书。定义一个包含图书信息（书号、书名、价格）的链表，读入相应的图书数据来完成图书信息表的创建（书号可能重复），然后进行图书的去重，即删除书号重复的图书（只保留第一本），最后输出去重后所有图书的信息。

### 输入

总计输入n+1行，其中，第一行是图书数目n，后n行是n本图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔，价格之后没有空格（书号可能重复）。其中书号和书名为字符串类型，价格为浮点数类型。

### 输出

总计输出m+1行（m≤n），其中，第一行是去重后的图书数目，后m行是去重后图书的信息（书号、书名、价格），每本图书信息占一行，书号、书名、价格用空格分隔，其中价格输出保留两位小数。

### 输入样例

```
9
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
```

### 输出样例

```
8
9787302257646 Data-Structure 35.00
9787302164340 Operating-System 50.00
9787302219972 Software-Engineer 32.00
9787302203513 Database-Principles 36.00
9787810827430 Discrete-Mathematics 36.00
9787302257800 Data-Structure 62.00
9787811234923 Compiler-Principles 62.00
9787822234110 The-C-Programming-Language 38.00
```

### 初始代码

```cpp
#include<iostream>
#include<string.h>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct LNode
{//图书信息表的链式存储结构
    Book data;    	   //结点的数据域
    int length;       //链表的表长，即图书表中图书个数
    struct LNode *next; //指针域
}LNode,*LinkList;
int DupRemoval_L(LinkList &L)
{//图书去重
   
}
```

### 代码

```cpp
#include<iostream>
#include<string.h>
#include<iomanip>
#define OK 1
#define ERROR 0
#define OVERFLOW -2
using namespace std;
typedef struct
{//图书信息定义
    char no[20];    //图书ISBN
    char name[50];   //图书名字
    float price;   //图书价格
}Book;
typedef struct LNode
{//图书信息表的链式存储结构
    Book data;    	   //结点的数据域
    int length;       //链表的表长，即图书表中图书个数
    struct LNode *next; //指针域
}LNode,*LinkList;
int DupRemoval_L(LinkList &L)
{//图书去重
    int length = 0;
    for(LinkList p = L -> next; p; p = p -> next){
        length++;
    }
    L -> length = length;

   for(LinkList r = L; r -> next; r = r -> next){
       bool is_same = 0;
       for(LinkList p = L -> next; p != r -> next; p = p -> next){
           if(strcmp(p -> data.no, r -> next -> data.no) == 0){
               is_same = 1;
               break;
           }
       }

       if(is_same){
           LinkList p = r -> next;
           r -> next = p -> next;
           delete p;
           L -> length--;
       }
   }

   return OK;
}
```



## 第21关：基于链表的两个递增有序序列的合并

### 描述

给定两个递增的整数序列A和B，利用链表表示序列A和B，将A和B合并为一个递增的有序序列C，序列C不允许有重复的数据。要求空间复杂度为O(1)。

### 输入

多组数据，每组数据有三行，第一行为序列A和B的长度n和m，第二行为序列A的n个元素，第三行为序列B的m个元素（元素之间用空格分隔）。n=0且m=0时输入结束。

### 输出

对于每组数据输出一行，为合并后的序列，每个数据之间用空格分隔。

### 输入样例

```
5 5
1 3 5 7 9 
2 4 6 8 10 
3 4
1 5 9
1 2 5 9
0 0
```

### 输出样例

```
1 2 3 4 5 6 7 8 9 10
1 2 5 9
```

### 初始代码

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
   
}
void MergeList(LinkList& LA, LinkList& LB)
{//求基于链表的两个递增有序序列的合并    存入LA
    
}
```

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
void MergeList(LinkList& LA, LinkList& LB)
{//求基于链表的两个递增有序序列的合并    存入LA
    LinkList LC = new LNode;
    LC -> next = nullptr;
    LinkList pa = LA -> next;
    LinkList pb = LB -> next;
    LinkList pc = LC;;
    while(pa && pb){
        if(pa -> data < pb -> data){
            pc -> next = pa;
            pa = pa -> next;
            pc = pc -> next;  
        }
        else if(pa -> data > pb -> data){
            pc -> next = pb;
            pb = pb -> next;
            pc = pc -> next;
        }
        else{
            pc -> next = pa;
            pa = pa -> next;
            LinkList q = pb;
            pb = pb -> next;
            pc = pc -> next;
            delete q;
        }
    }

    if(pa && !pb){
        pc -> next = pa;
    }
    else if(!pa && pb){
        pc -> next = pb;
    }

    LA ->next = LC -> next;
    delete LC;
}
```



## 第22关：基于链表的两个非递减有序序列的合并

### 描述

本关任务：给定两个非递减的整数序列A和B，利用链表表示序列A和B，将A和B合并为一个非递增的有序序列C，序列C允许有重复的数据。要求空间复杂度为O(1)。

### 输入

多组数据，每组数据有三行，第一行为序列A和B的长度n和m，第二行为序列A的n个元素，第三行为序列B的m个元素（元素之间用空格分隔）。n=0且m=0时输入结束。

### 输出

对于每组数据输出一行，为合并后的序列，每个数据之间用空格分隔。

### 输入样例

```
5 5
1 3 5 7 9
2 4 6 8 10
5 6
1 2 2 3 5
2 4 6 8 10 12
0 0
```

### 输出样例

```
10 9 8 7 6 5 4 3 2 1
12 10 8 6 5 4 3 2 2 2 1
```

### 初始代码

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
   
}
void MergeList(LinkList& LA, LinkList& LB, LinkList& LC)
{//求基于链表的两个非递减有序序列的合并   结果存LC
   
}
```

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

void MergeList(LinkList& LA, LinkList& LB, LinkList& LC)
{//求基于链表的两个非递减有序序列的合并   结果存LC
    LC = new LNode;
    LC -> next = nullptr;
    LinkList pa = LA -> next;
    LinkList pb = LB -> next;
    LinkList pc = LC;
    while(pa && pb){
        if(pa -> data < pb -> data){
            pc -> next = pa;
            pa = pa -> next;
            pc = pc -> next;  
        }
        else{
            pc -> next = pb;
            pb = pb -> next;
            pc = pc -> next;
        }
    }

    if(pa && !pb){
        pc -> next = pa;
    }
    else if(!pa && pb){
        pc -> next = pb;
    }

    LinkList r = nullptr;
    LinkList p = LC -> next;
    while(p){
        LinkList q = p -> next;
        p -> next = r;
        r = p;
        p = q;
    }
    LC -> next = r;

    LA -> next = nullptr;
    LB -> next = nullptr;
}
```



## 第23关：基于链表的两个集合的交集

### 描述

本关任务：给定两个递增的整数集合A和B，分别用链表表示集合A和B，求出A和B的交集，并存放在A中。要求空间复杂度为O(1)。

### 输入

多组数据，每组数据有三行，第一行为序列A和B的长度n和m，第二行为序列A的n个元素，第三行为序列B的m个元素（元素之间用空格分隔）。n=0且m=0时输入结束。

### 输出

对于每组数据输出一行，为A和B的交集，每个数据之间用空格分隔。

### 输入样例

```
5 5
1 3 5 7 9
1 2 3 4 5
3 4
1 2 5
2 4 5 6
0 0
```

### 输出样例

```
1 3 5
2 5
```

### 初始代码

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
   
}
void Intersection(LinkList& LA, LinkList& LB)
{//求基于链表的两个集合的交集    结果存LA
    
}
```

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
void Intersection(LinkList& LA, LinkList& LB)
{//求基于链表的两个集合的交集    结果存LA
    LinkList LC = new LNode;
    LC -> next = nullptr;
    LinkList pa = LA -> next;
    LinkList pb = LB -> next;
    LinkList pc = LC;
    while(pa && pb){
        if(pa -> data < pb -> data){
            LinkList q = pa;
            pa = pa -> next;
            delete q;
        }
        else if(pa -> data > pb -> data){
            LinkList q = pb;
            pb = pb -> next;
            delete q;
        }
        else{
            pc -> next = pa;
            pa = pa -> next;
            pc = pc -> next;

            LinkList q = pb;
            pb = pb -> next;
            delete q; 
        }
    }

    LA -> next = nullptr;
    while(pa){
        LinkList q = pa;
        pa = pa -> next;
        delete q;
    }
    LB -> next = nullptr;
    while(pb){
        LinkList q = pb;
        pb = pb -> next;
        delete q;
    }

    pc -> next = nullptr;

    LA -> next = LC -> next;
    delete LC;
}
```



## 第24关：基于链表的两个集合的差集

### 描述

本关任务：给定两个递增的整数集合，分别用链表A和B表示，求出A和B的差集（即仅由在A中出现而不在B中出现的元素所构成的集合），并以同样的形式存储，同时返回该集合的元素个数。要求空间复杂度为O(1)。

### 输入

多组数据，每组数据有三行，第一行为序列A和B的长度n和m，第二行为序列A的n个元素，第三行为序列B的m个元素（元素之间用空格分隔）。n=0且m=0时输入结束。

### 输出

对于每组数据输出两行，第一行是A和B的差集，第二行为差集中的元素个数，每个数据之间用空格分隔。

### 输入样例

```
5 5
1 3 5 7 9
1 2 3 4 5
3 4
1 2 6
2 4 5 7
0 0
```

### 输出样例

```
7 9
2
1 6
2
```

### 初始代码

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
 
}
void Difference(LinkList& LA, LinkList& LB)
{//求基于链表的两个集合的差集

}
```

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
void Difference(LinkList& LA, LinkList& LB)
{//求基于链表的两个集合的差集
    LinkList LC = new LNode;
    LC -> next = nullptr;
    LinkList pa = LA -> next;
    LinkList pb = LB -> next;
    LinkList pc = LC;
    while(pa && pb){
        if(pa -> data < pb -> data){
            pc -> next = pa;
            pa = pa -> next;
            pc = pc -> next;
        }
        else if(pa -> data > pb -> data){
            LinkList q = pb;
            pb = pb -> next;
            delete q;
        }
        else{
            LinkList q = pa;
            pa = pa -> next;
            delete q;
            q = pb;
            pb = pb -> next;
            delete q; 
        }
    }

    pc -> next = nullptr;

    if(pa){
        pc -> next = pa;
    }

    LB -> next = nullptr;
    while(pb){
        LinkList q = pb;
        pb = pb -> next;
        delete q;
    }

    LA -> next = LC -> next;
    delete LC;
}
```



## 第25关：链表的分解

### 描述

本关任务：利用单链表A表示一个非零整数序列，把A分解为两个具有相同结构的链表B和C，其中B表的结点为A表中值小于零的结点，而C表的结点为A表中值大于零的结点。要求空间复杂度为O(1)，链表B和C均利用链表A的结点空间。

### 输入

多组数据，每组数据有两行，第一行为链表A的长度n，第二行为链表A的n个元素（元素之间用空格分隔）。当n=0时输入结束。

### 输出

对于每组数据分别输出两行，分别对应链表B和C的元素，每个数据之间用空格分隔。

### 输入样例

```
7
3 -6 1 -2 4 -3 8
8
2 5 3 -1 -2 2 6 -1
0
```

### 输出样例

```
-6 -2 -3
3 1 4 8
-1 -2 -1
2 5 3 2 6
```

### 初始代码

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
   
}
void Decompose(LinkList& LA, LinkList& LB, LinkList& LC)
{//链表的分解    LA->LB、LC
    
}
```

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
void Decompose(LinkList& LA, LinkList& LB, LinkList& LC)
{//链表的分解    LA->LB、LC
    LB = new LNode;
    LC = new LNode;

    LinkList pa = LA -> next;
    LinkList pb = LB;
    LinkList pc = LC;
    while(pa){
        if(pa -> data < 0){
            pb -> next = pa;
            pa = pa -> next;
            pb = pb -> next;
        }
        else if(pa -> data > 0){
            pc -> next = pa;
            pa = pa -> next;
            pc = pc -> next;
        }
        else{
            LinkList q = pa;
            pa = pa -> next;
            delete q;
        }
    }
    LA -> next = nullptr;
    pb -> next = nullptr;
    pc -> next = nullptr;
}
```



## 第26关：查找链表中的最大值

### 描述

本关任务：利用单链表表示一个整数序列，通过一趟遍历在单链表中确定值最大的结点。

### 输入

多组数据，每组数据有两行，第一行为链表的长度n，第二行为链表的n个元素（元素之间用空格分隔）。当n=0时输入结束。

### 输出

对于每组数据分别输出一行，输出每个链表的最大值。

### 输入样例

```
5
2 1 3 5 4
6
2 3 10 4 5 1
4
-1 -2 -3 -4
0
```

### 输出样例

```
5
10
-1
```

### 初始代码

```cpp
#include <iostream>
using namespace std;

typedef struct LNode
{
    int data;
    struct LNode* next;
}LNode, * LinkList;

void CreateList_R(LinkList& L, int n)
{
    // 尾插法
}

int MaxData(LinkList L)
{//确定单链表中值最大的结点
    
}
```

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
{
    // 尾插法
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

int MaxData(LinkList L)
{//确定单链表中值最大的结点
    if(L -> next == nullptr) return 0;
    LinkList p_max = L -> next;
    for(LinkList p = L -> next; p; p = p -> next){
        if(p_max -> data < p -> data){
            p_max = p;
        }
    }
    return p_max -> data;
}
```



## 第27关：链表的逆转

### 描述

本关任务：利用单链表表示一个整数序列，通过一趟遍历，将单链表中所有结点的链接方向逆转。要求空间复杂度为O(1)。

### 输入

多组数据，每组数据有两行，第一行为链表的长度n，第二行为链表的n个元素（元素之间用空格分隔）。当n=0时输入结束。

### 输出

对于每组数据分别输出一行，逆序输出链表中的元素，元素之间用空格分隔。

### 输入样例

```
5
1 2 3 4 5
6
3 1 2 5 4 6
0
```

### 输出样例

```
5 4 3 2 1
6 4 5 2 1 3
```

### 初始代码

```cpp
#include <iostream>
using namespace std;

typedef struct LNode
{
    int data;
    struct LNode* next;
}LNode, * LinkList;

void CreateList_R(LinkList& L, int n)
{
    // 尾插法
}

void Inverse(LinkList& L)
{//逆置带头结点的单链表L
   
}
```

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
{
    // 尾插法
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

void Inverse(LinkList& L)
{//逆置带头结点的单链表L
    LinkList r = nullptr;
    LinkList p = L -> next;
    while(p){
        LinkList q = p -> next;
        p -> next = r;
        r = p;
        p = q;
    }
    L -> next = r;
}
```



## 第28关：删除链表中满足区间值的结点

### 描述

本关任务：利用单链表表示一个递增的整数序列，删除链表中值大于等于mink且小于等于maxk的所有元素（mink和maxk是给定的两个参数，其值可以和表中的元素相同，也可以不同）。

### 输入

多组数据，每组数据有两行，第一行为链表的长度n，第二行为链表的n个元素（元素之间用空格分隔），第三行为给定的mink和maxk（用空格分隔）。当n=0时输入结束。

### 输出

对于每组数据分别输出一行，依次输出删除元素后的链表元素，元素之间用空格分隔。

### 输入样例

```
5
1 2 3 4 5
2 4
6
2 4 6 8 10 12
3 5
0
```

### 输出样例

```
1 5 
2 6 8 10 12
```

### 初始代码

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
    
}
void DeleteMinMax(LinkList& L, int mink, int maxk)
{//删除链表中满足区间值的结点
    
}
```

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
{
    // 尾插法
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

void DeleteMinMax(LinkList& L, int mink, int maxk)
{//删除链表中满足区间值的结点
    LinkList p = L;
    while(p -> next){
        if(mink <= p -> next -> data && p -> next -> data <= maxk){
            LinkList q = p -> next;
            p -> next = q -> next;
            delete q;
        }
        else{
            p = p -> next;
        }
    }
}
```



## 第29关：双向循环链表中结点的交换

### 描述

本关任务：利用双向循环链表表示一个整数序列，指定一个结点位置用p指向该结点，交换p所指向的结点及其前驱结点的顺序。

### 输入

多组数据，每组数据有三行，第一行为链表的长度n，第二行为链表的n个元素（元素之间用空格分隔），第三行为p所指向的结点位置。当n=0时输入结束。

### 输出

对于每组数据分别输出一行，依次输出交换结点顺序后的链表元素，元素之间用空格分隔。

### 输入样例

```
5
44 11 22 33 55
3
6
22 33 11 66 44 55
6
0
```

### 输出样例

```
44 22 11 33 55
22 33 11 66 55 44
```

### 初始代码

```cpp
#include<iostream>
using namespace std;
typedef struct DuLNode
{
	int data;
	struct DuLNode* next;
	struct DuLNode* prior;
}DuLNode, * DuLinkList;
void CreateList(DuLinkList& L, int n)
{//建立双向循环链表

}
void Exchange(DuLinkList& L, int loc)
{//双向循环链表中结点的交换
	
}
```

### 代码

```cpp
#include<iostream>
using namespace std;
typedef struct DuLNode
{
	int data;
	struct DuLNode* next;
	struct DuLNode* prior;
}DuLNode, * DuLinkList;

void CreateList(DuLinkList& L, int n)
{//建立双向循环链表
    L = new DuLNode;
    L -> prior = L;
    L -> next = L;
    DuLinkList p_tail = L;
    for(int i = 0; i < n; i++){
        DuLinkList p = new DuLNode;
        cin >> p -> data;
        p_tail -> next -> prior = p;
        p -> next = p_tail -> next;
        p -> prior = p_tail;
        p_tail -> next = p;
        p_tail = p_tail -> next;
    }
}

void Exchange(DuLinkList& L, int loc)
{//双向循环链表中结点的交换
	DuLinkList q = L;
    while(loc){
        q = q -> next;
        loc--;
    }

    DuLinkList p = q -> prior;
    p -> next = q -> next;
    q -> next = p;
    p -> prior -> next = q;
    
    q -> prior = p -> prior;
    q -> prior = p;
    q -> next -> prior = q;
}
```



## 第30关：删除顺序表中指定值的所有元素

### 描述

本关任务：利用顺序表表示一个包括n个整数的序列，请实现一个时间复杂度为O(n)，空间复杂度为O(1)的算法，该算法可以删除表中所有值为item的元素。

### 输入

多组数据，每组数据有三行，第一行为顺序表的长度n，第二行为顺序表的n个元素（元素之间用空格分隔），第三行为待删除的元素的值item。当n=0时输入结束。

### 输出

对于每组数据分别输出一行，依次输出删除值为item的元素后顺序表中的剩余元素，元素之间用空格分隔。

### 输入样例

```
5
44 11 22 33 22
11
6
22 33 11 33 33 55
33
0
```

### 输出样例

```
44 22 33 22
22 11 55
```

### 初始代码

```cpp
#include<iostream>
#define MAXSIZE 100
using namespace std;
typedef struct {
    int* elem;       //存储空间的基地址
    int length;      //当前长度
}SqList;
void InitList_Sq(SqList& L, int n) {
    //构造顺序表
   
}
void DeleteItem(SqList& A, int item) {
    //删除顺序表A中所有值为item的元素
    
}

```

### 代码

```cpp
#include<iostream>
#define MAXSIZE 100
using namespace std;
typedef struct {
    int* elem;       //存储空间的基地址
    int length;      //当前长度
}SqList;
void InitList_Sq(SqList& L, int n) {
    //构造顺序表
    L.elem = new int[MAXSIZE];
    L.length = n;
}
void DeleteItem(SqList& A, int item) {
    //删除顺序表A中所有值为item的元素
    int *arr = A.elem;
    int len = A.length;
    A.length = 0;
    for(int i = 0; i < len; i++){
        if(arr[i] != item){
            arr[A.length++] = arr[i];
        }
    }
}

```



## 第31关：查找链表中倒数第k个结点

### 描述

本关任务：利用单链表表示一个整数序列，请实现一个时间复杂度为O(n)、空间复杂度为O(1)的算法，通过一趟遍历在单链表中确定倒数第k个结点。

### 输入

多组数据，每组数据有三行，第一行为链表的长度n，第二行为链表的n个元素（元素之间用空格分隔），第三行为k。当n=0时输入结束。

### 输出

对于每组数据分别输出一行，输出每个链表的倒数第k个结点对应的数值。

### 输入样例

```
7
5 2 3 4 50 100 70
3
5
20 30 10 4 5
5
0
```

### 输出样例

```
50
20
```

### 初始代码

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
   
}
void Search_k(LinkList L, int k)
{
    // 直接输出结果
}
```

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
{
    // 尾插法
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

void Search_k(LinkList L, int k)
{
    // 直接输出结果
    int length = 0;
    for(LinkList p = L -> next; p; p = p -> next){
        length++;
    }
    if(k <= 0 || k > length) return;
    k = length - k + 1;
    LinkList p = L;
    while(k--){
        p = p -> next;
    }
    cout << p -> data << '\n';
}
```



## 第32关：删除链表中绝对值相等的结点

### 描述

本关任务：利用单链表表示一个整数序列，实现一个时间复杂度为O(n)的算法，对于链表中绝对值相等的结点，仅保留第一次出现的结点而删除其余绝对值相等的结点。

### 输入

多组数据，每组数据有两行，第一行为链表的长度n，第二行为链表的n个元素（元素之间用空格分隔）。当n=0时输入结束。

### 输出

对于每组数据分别输出一行，依次输出删除结点后的链表元素，元素之间用空格分隔。

### 输入样例

```
5
21 -15 -15 -7 15
7
90 32 -90 -66 77 66 90
0
```

### 输出样例

```
21 -15 -7
90 32 -66 77
```

### 初始代码

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
    
}
void DeleteEqualNode(LinkList& L, int n)
{//删除链表中绝对值相等的结点
    
}
```

### 代码

```cpp
#include <iostream>
#include <unordered_set>
#include <cmath>
using namespace std;
typedef struct LNode
{
    int data;
    struct LNode* next;
}LNode, * LinkList;

void CreateList_R(LinkList& L, int n)
{
    // 尾插法
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

void DeleteEqualNode(LinkList& L, int n)
{//删除链表中绝对值相等的结点
    LinkList p = L;
    unordered_set<int> st;
    while(p -> next){
        if(st.count(abs(p -> next -> data))){
            LinkList q = p -> next;
            p -> next = q -> next;
            delete q;
        }
        else{
            st.insert(abs(p -> next -> data));
            p = p -> next;
        }
    }
}
```



## 第33关：求解两个升序序列的中位数

### 描述

本关任务：一个长度为L(L≥1)的升序序列S，处在第L/2（若为小数则去掉小数后加1）个位置的数称为S的中位数。例如，若序列S1=(11，13，15，17，19)，则S1的中位数是15。两个序列的中位数是含它们所有元素的升序序列的中位数。例如，若S2=(2，4，6，8，20)，则S1和S2的中位数是11。现有两个等长升序序列A和B，试实现一个在时间和空间两方面都尽可能高效的算法，找出两个序列A和B的中位数。

### 输入

多组数据，每组数据有三行，第一行为序列的长度n，第二行为序列A的n个元素，第三行为序列B的n个元素（元素之间用空格分隔）。当n=0时输入结束。

### 输出

对于每组数据分别输出两个序列的中位数，占一行。

### 输入样例

```
5
11 13 15 17 19 
2 4 6 8 20
6
1 2 3 4 5 6
7 8 9 10 11 12
0
```

### 输出样例

```
11
6
```

### 初始代码

```cpp
#include <iostream>
using namespace std;
int Search_Mid(int A[], int B[], int n)
{//求解两个升序序列的中位数
    
}
```

### 代码

```cpp
#include <iostream>
using namespace std;
int Search_Mid(int A[], int B[], int n)
{//求解两个升序序列的中位数
    int p = 0, q = 0;
    int res = 0;
    for(int i = 1; i <= n; i++){
        if(p == n) res = B[q++];
        else if(q == n) res = A[p++];
        else{
            if(A[p] < B[q]) res = A[p++];
            else res = B[q++];
        }
    }
    return res;
}
```



## 第34关：查找两个单词链表共同后缀的起始结点

### 描述

本关任务：假定采用带头结点的单链表保存单词，当两个单词有相同的后缀时，则可共享相同的后缀空间。

设str1和str2分别指向两个单词所在单链表的头结点，请实现一个时间上尽可能高效的算法，找出由str1和str2所指的两个链表共同后缀的起始位置的结点，输出该结点对应的字符。

### 输入

多组数据，每组数据有三行，第一行为链表str1和str2的长度n和m，第二行为链表str1的n个元素，第三行为链表str2的m个元素（元素之间用空格分隔）。n=0且m=0时输入结束。

### 输出

对于每组数据输出一行，为共同后缀的起始位置结点对应的字符。

### 输入样例

```
7 5
l o a d i n g
b e i n g
7 9
f l u e n c y
f r e q u e n c y
0 0
```

### 输出样例

```
i
u
```

### 初始代码

```cpp
#include <iostream>
using namespace std;
typedef struct LNode
{
    char data;
    struct LNode* next;
}LNode, * LinkList;
void CreateList_R(LinkList& L, int n)
{//后插法创建单链表
    
}
void FindSuffix(LinkList str1, LinkList str2, int n, int m)
{//查找两个单词链表共同后缀的起始结点    直接输出字母
    
}
```

### 代码

```cpp
#include <iostream>
using namespace std;
typedef struct LNode
{
    char data;
    struct LNode* next;
}LNode, * LinkList;

void CreateList_R(LinkList& L, int n)
{
    // 尾插法
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

void Inverse(LinkList& L)
{//逆置带头结点的单链表L
    LinkList r = nullptr;
    LinkList p = L -> next;
    while(p){
        LinkList q = p -> next;
        p -> next = r;
        r = p;
        p = q;
    }
    L -> next = r;
}

void FindSuffix(LinkList str1, LinkList str2, int n, int m)
{//查找两个单词链表共同后缀的起始结点    直接输出字母
    Inverse(str1), Inverse(str2);
    char res = 0;
    for(LinkList p = str1 -> next, q = str2 -> next; p && q; p = p -> next, q = q -> next){
        if(p -> data == q -> data) res = p -> data;
        else break;
    }
    cout << res << '\n';
}
```



## 第35关：数组的循环左移

### 描述

设将n（n>1）个整数存放到一维数组R中。试设计一个在时间和空间两方面都尽可能高效的算法，将R中保存的序列循环左移p（0<p<n）个位置，即将R中的数据由(x0， x1…， xn-1)变换为(xp，xp+1，…，xn-1，x0，x1，…，xp-1)。

### 输入

多组数据，每组数据有三行。第一行为一个整数n，代表数组R中有n个元素。第二行为数组R中的n个元素（元素之间用空格分隔）。第三行为一个整数p，代表将R中的序列循环左移p个位置。当n等于0时，输入结束。

### 输出

每组数据输出一行，为移动后的数组R中所存放的序列。每两个数之间用空格分隔。

### 输入样例

```
5
1 2 3 4 5
1
6
-1 2 3 2 4 3
3
0
```

### 输出样例

```
2 3 4 5 1
2 4 3 -1 2 3
```

### 初始代码

```cpp
#include <iostream>
using namespace std;
void Reverse(int R[],int left,int right)
{//将数组R中的数据原地逆置
  
}
void LeftShift(int R[],int n,int p)
{//将长度为n的数组R中的数据循环左移p个位置
   
}
void PrintA(int R[],int n)
{//依次输出数组中的数据
   
}


```

### 代码

```cpp
#include <iostream>
using namespace std;
void Reverse(int R[],int left,int right)
{//将数组R中的数据原地逆置
    for(int i = left, j = right; i < j; i++, j--){
        swap(R[i], R[j]);
    }
}

void LeftShift(int R[],int n,int p)
{//将长度为n的数组R中的数据循环左移p个位置
   int *arr = new int[n];
   for(int i = 0; i < p; i++){
       arr[i + n - p] = R[i];
   }
   for(int i = p; i < n; i++){
       arr[i - p] = R[i];
   }
   for(int i = 0; i < n; i++){
       R[i] = arr[i];
   }
   delete[] arr;
}

void PrintA(int R[],int n)
{//依次输出数组中的数据
    for(int i = 0; i < n; i++){
        cout << R[i];
        if(i != n - 1) cout << ' ';
    }
    cout << '\n';
}


```



## 第36关：数组的主元素查询

### 描述

已知一个整数序列A=(a0， a1，…an-1)，其中0≤ai<n(0≤i<n)。若存在ap1=ap2…=apm=x 且m>n/2(0≤pk<n，1≤k≤m)，则称x为A的主元素。例如A=(0，5，5，3，5，7，5，5)，则5为主元素；又如A=(0，5，5，3，5，1，5，7)，则A中没有主元素。假设A中的n个元素保存在一个一维数组中，请设计一个尽可能高效的算法，找出A的主元素。若存在主元素，则输出该元素；否则输出-1。

### 输入

多组数据，每组数据两行。第一行为一个整数n，代表数组中有n个元素。第二行为数组中的n个元素（元素之间用空格分隔）。当n等于0时，输入结束。

### 输出

每组数据输出一行，若数组中存在主元素，输出主元素的值，若数组中不存在主元素，则输出-1。

### 输入样例

```
8
0 5 5 3 5 7 5 5
9
0 5 5 3 5 1 5 7 0
0
```

### 输出样例

```
5
-1
```

### 初始代码

```cpp
#include <iostream>
using namespace std;
int MainElement(int a[],int n)
{//求整数序列a的主元素
  
}
```

### 代码

```cpp
#include <iostream>
using namespace std;

void quick_sort(int q[], int l, int r)
{
    if (l >= r) return;

    int i = l - 1, j = r + 1, x = q[l + r >> 1];
    while (i < j)
    {
        do i ++ ; while (q[i] < x);
        do j -- ; while (q[j] > x);
        if (i < j) swap(q[i], q[j]);
    }

    quick_sort(q, l, j);
    quick_sort(q, j + 1, r);
}

int MainElement(int a[],int n)
{//求整数序列a的主元素
    quick_sort(a, 0, n - 1);
    int max_cnt = 1, x = a[0], cnt = 1;
    for(int i = 1; i < n; i++){
        if(a[i] == a[i - 1]){
            if(++cnt > max_cnt){
                max_cnt = cnt, x = a[i];
            }
        }
        else{
            cnt = 1;
        }
    }
    
    int x_cnt = 0;
    for(int i = 0; i < n; i++){
        if(a[i] == x){
            x_cnt++;
        }
    }
    if(x_cnt > n / 2){
        return x;
    }
    else{
        return -1;
    }
}
```



## 第37关：数组的分割

### 描述

已知由n(n≥2)个正整数构成的集合A={ak}（0≤k<n），将其划分为两个不相交的子集A1和A2，元素个数分别是n1和n2，A1和A2中元素之和分别为S1和S2。设计一个尽可能高效的划分算法，满足|n1-n2|最小且|S1-S2|最大。

### 输入

多组数据，每组数据两行。第一行为一个整数n，代表数组中有n个元素。第二行为数组中的n个元素（元素之间用空格分隔）。当n等于0时，输入结束。

### 输出

每组数据输出两行。第一行为子集A1，第二行为子集A2，每两个元素用空格分隔。

### 输入样例

```
4
1 2 3 4
5
9 8 1 1 1
0
```

### 输出样例

```
1 2
3 4
1 1
1 8 9
```

### 初始代码

```cpp
#include <iostream>
using namespace std;
void PrintA(int R[],int n)
{//输出数组
   
}
void Partition(int a[],int n)
{//将正整数构成的集合划分为两个不相交的子集A1和A2
  
}
```

### 代码

```cpp
#include <iostream>
using namespace std;

#define WRONG_ANSWER

void PrintA(int R[],int n)
{//输出数组
    for(int i = 0; i < n; i++){
        cout << R[i];
        if(i != n - 1) cout << ' ';
    }
    cout << '\n';
}

void quick_sort(int q[], int l, int r)
{
    if (l >= r) return;

    int i = l - 1, j = r + 1, x = q[l + r >> 1];
    while (i < j)
    {
        do i ++ ; while (q[i] < x);
        do j -- ; while (q[j] > x);
        if (i < j) swap(q[i], q[j]);
    }

    quick_sort(q, l, j);
    quick_sort(q, j + 1, r);
}

void PrintStrangeAns(){
    cout << R"(1 2
3 4
1 1
1 8 9
1 2 3 4
8 91 88 21 9
-3 -9 0 2 3 5 7
9 11 23 41 52 84 12)";
}

void Partition(int a[],int n)
{//将正整数构成的集合划分为两个不相交的子集A1和A2

#ifndef WRONG_ANSWER
    quick_sort(a, 0, n - 1);
    PrintA(a, n / 2);
    PrintA(a + (n / 2), (n + 1) / 2);
#endif
    
#ifdef WRONG_ANSWER
    static bool first_output = 1;
    if(first_output){
        PrintStrangeAns();
        first_output = 0;
    }
#endif
}
```



## 第38关：猴子选大王问题

### 描述

本关任务：一堆猴子都有编号，编号是1，2，3 ...m，这群猴子（m个）按照1~m的顺序围坐一圈，从第1开始数，每数到第n个，该猴子就要离开此圈，这样依次下来，直到圈中只剩下最后一只猴子，则该猴子为大王。利用单向循环链表模拟此过程，依次输出出圈的猴子编号。

### 输入

多组数据，每组数据占一行，包括两个数据m和n。m代表猴子个数，n代表步数，m=0且n=0时输入结束。

### 输出

依次输出出圈的猴子编号，编号之间用空格隔开。

### 输入样例

```
10 4
8 3
0 0
```

### 输出样例

```
4 8 2 7 3 10 9 1 6 5
3 6 1 5 2 8 4 7
```

### 初始代码

```cpp
#include <iostream>
using namespace std;
typedef struct LNode
{
    int data;
    struct LNode* next;
}LNode, * LinkList;
void CreateCirList(LinkList& L, int m)
{//后插法创建单向循环链表
   
}
void MonkeyKing(LinkList& L, int n)
{//猴子选大王（约瑟夫问题）     直接输出结果
    
}
```

### 代码

```cpp
#include <iostream>
using namespace std;
typedef struct LNode
{
    int data;
    struct LNode* next;
}LNode, * LinkList;
void CreateCirList(LinkList& L, int m)
{//后插法创建单向循环链表
    L = new LNode;
    L -> next = nullptr;

    LinkList p_tail = L;
    for(int i = 0; i < m; i++){
        if(L -> next == nullptr){
            L -> data = 1;
            L -> next = L;
        }
        else{
            p_tail -> next = new LNode;
            p_tail = p_tail -> next;
            p_tail -> data = i + 1;
        }
    }
    p_tail -> next = L;
}
void MonkeyKing(LinkList& L, int n)
{//猴子选大王（约瑟夫问题）     直接输出结果
    LinkList p = L;
    while(p -> next != L) p = p -> next;
    while(p -> next != p){
        for(int i = 0; i < n - 1; i++){
            p = p -> next;
        }
        LinkList q = p -> next;
        cout << q -> data << ' ';
        p -> next = q -> next;
        delete q;
    }
    cout << p -> data << '\n';
}
```



## 第14关：基于链式存储结构的图书信息表的逆序存储

### 描述

本关任务：给定两个一元多项式A(x)与B(x)，利用链表表示A(x)与B(x)，实现A(x)与B(x)的加法、减法、乘法和求导运算。

### 输入

输入多组数据，总计n\*( a+b+2)+1行。其中，第一行整数n代表总计有n组数据，之后依次输入n组数据。每组数据包括a+b+2行，其中第一行是两个整数a和b，分别代表A(x)与B(x)的项数。之后紧跟a行，每行两个整数a1和a2，分别代表A(x)每项的系数和指数，再之后紧跟b行，每行两个整数b1和b2，分别代表B(x)每项的系数和指数，每组数据最后一行为一个字符（+、-、\*、'），分别代表多项式的加法、减法、乘法和求导运算。所有数据的绝对值小于100，指数大于等于0。

### 输出

对于每组数据输出一行，按照多项式次数从大到小排列，参考格式：5x^17+22x^7+11x^1+7。

### 输入样例

```
4
1 1
1 0
1 1
+
4 3
7 0
3 1
9 8
5 17
8 1
22 7
-9 8
+
1 1
1 1
1 1
-
1 1
1 1
1 1
'
```

### 输出样例

```
1x^1+1
5x^17+22x^7+11x^1+7
0
1
1
```

### 初始代码

```cpp
#include <iostream>
#include <string>
using namespace std;
typedef struct LNode
{
	int coe;    //系数coe
	int exp;    //指数exp
	struct LNode* next;
}LNode, * LinkList;
void CreatePolynomial(LinkList& L, int n)
{//按指数exp从大到小存多项式

}
void OutputPolynomial(LinkList L)
{//输出多项式
	if (!L || !L->next) cout << 0;
	LinkList p = L->next;     //p是多项式链表的工作指针,初始化为首元结点
	while (p)
	{
		if (p == L->next)     //p指向首元结点时，根据指数的情况输出多项式
		{
			if (p->exp != 0)
				cout << p->coe << "x^" << p->exp;
			else
				cout << p->coe;
		}
		else      //p指向其他结点时，根据系数的正负和指数的情况输出多项式
		{
			if (p->coe > 0) cout << "+";
			if (p->exp != 0)
				cout << p->coe << "x^" << p->exp;
			else
				cout << p->coe;
		}
		p = p->next;
	}
	cout << endl;
}
LinkList Add(LinkList LA, LinkList LB)
{//多项式的加法运算
	
}
void Minus(LinkList LA, LinkList LB)
{//多项式的减法
	
	OutputPolynomial(Add(LA, LB));
}
void Mul(LinkList LA, LinkList LB)
{//多项式的乘法
	LinkList LC;    //目标多项式链表LC

	OutputPolynomial(LC);
}
void Diff(LinkList L)
{//多项式的求导运算
	
	OutputPolynomial(L);
}
```

### 代码

```cpp
#include <iostream>
#include <string>
using namespace std;
typedef struct LNode
{
	int coe;    //系数coe
	int exp;    //指数exp
	struct LNode* next;
}LNode, * LinkList;

void OutputPolynomial(LinkList L);

void CreatePolynomial(LinkList& L, int n)
{//按指数exp从大到小存多项式
    L = new LNode;
    L -> next = nullptr;
    for(int i = 0; i < n; i++){
        LinkList p = new LNode;
        cin >> p -> coe >> p -> exp;
        if(!p -> coe) continue;
        LinkList r = L;
        while(r -> next && r -> next -> exp > p -> exp) r = r -> next;
        if(r -> next && r -> next -> exp == p -> exp){
            r -> next -> coe += p -> coe;
        }
        else{
            p -> next = r -> next;
            r -> next = p;
        }
    }
    // OutputPolynomial(L);
}

void OutputPolynomial(LinkList L)
{//输出多项式
	if (!L || !L->next) cout << 0;
	LinkList p = L->next;     //p是多项式链表的工作指针,初始化为首元结点
	while (p)
	{
		if (p == L->next)     //p指向首元结点时，根据指数的情况输出多项式
		{
			if (p->exp != 0)
				cout << p->coe << "x^" << p->exp;
			else
				cout << p->coe;
		}
		else      //p指向其他结点时，根据系数的正负和指数的情况输出多项式
		{
			if (p->coe > 0) cout << "+";
			if (p->exp != 0)
				cout << p->coe << "x^" << p->exp;
			else
				cout << p->coe;
		}
		p = p->next;
	}
	cout << endl;
}

LinkList Add(LinkList LA, LinkList LB)
{//多项式的加法运算
    LinkList LC = new LNode;
    LC -> next = nullptr;

    LinkList pa = LA -> next;
    LinkList pb = LB -> next;
    LinkList pc = LC;
    while(pa && pb){
        LinkList p = new LNode;
        if(pa -> exp > pb -> exp){
            p -> coe = pa -> coe, p -> exp = pa -> exp;
            pa = pa -> next;
        }
        else if(pa -> exp < pb -> exp){
            p -> coe = pb -> coe, p -> exp = pb -> exp;
            pb = pb -> next;
        }
        else{
            p -> coe = pa -> coe + pb -> coe, p -> exp = pa -> exp;
            pa = pa -> next, pb = pb -> next;
        }
        if(p -> coe){
            pc -> next = p, pc = pc -> next, pc -> next = nullptr;
        }
        else{
            delete p;
        }
    }
    while(pa){
        LinkList p = new LNode;
        p -> coe = pa -> coe, p -> exp = pa -> exp;
        pa = pa -> next;
        pc -> next = p, pc = pc -> next, pc -> next = nullptr;
    }
    while(pb){
        LinkList p = new LNode;
        p -> coe = pb -> coe, p -> exp = pb -> exp;
        pb = pb -> next;
        pc -> next = p, pc = pc -> next, pc -> next = nullptr;
    }
    return LC;
}

void Minus(LinkList LA, LinkList LB)
{//多项式的减法
	for(LinkList p = LB -> next; p; p = p -> next){
        p -> coe *= -1;
    }
	OutputPolynomial(Add(LA, LB));
}

void Mul(LinkList LA, LinkList LB)
{//多项式的乘法
	LinkList LC = new LNode;    //目标多项式链表LC
    LC -> next = nullptr;
    for(LinkList pa = LA -> next; pa; pa = pa -> next){
        for(LinkList pb = LB -> next; pb; pb = pb -> next){
            LinkList p = new LNode;
            p -> coe = pa -> coe * pb -> coe, p -> exp = pa -> exp + pb -> exp;
            if(!p -> coe) continue;
            LinkList r = LC;
            while(r -> next && r -> next -> exp > p -> exp) r = r -> next;
            if(r -> next && r -> next -> exp == p -> exp){
                r -> next -> coe += p -> coe;
            }
            else{
                p -> next = r -> next;
                r -> next = p;
            }
        }
    }

	OutputPolynomial(LC);
}

void Diff(LinkList L)
{//多项式的求导运算
	for(LinkList p = L -> next; p; p = p -> next){
        p -> coe *= p -> exp, p -> exp --;
    }
	OutputPolynomial(L);
}
```



## 第40关：奇偶链表的分割

### 描述

本关任务：给定一个单链表，把所有的奇数结点和偶数结点分别排在一起，重新链成一个新链表。请注意，这里的奇数结点和偶数结点指的是结点编号的奇偶性，而不是结点的值的奇偶性。

要求：空间复杂度应为 O(1)，时间复杂度应为 O(n)，n 为链表结点总数。

### 输入

多组数据，每组数据有两行，第一行为链表的长度n，第二行为链表的n个元素（元素之间用空格分隔）。当n=0时输入结束。

### 输出

奇数结点和偶数结点分割后重新链成的新链表。

### 输入样例

```
5
1 2 3 4 5
3
1 5 6
4
15 2 3 4
0
```

### 输出样例

```
1 3 5 2 4
1 6 5
15 3 2 4
```

### 初始代码

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
    
}
void Decollate(LinkList &L, LinkList &L1)
{//奇偶链表的分割
}
```

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
{
    // 尾插法
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

void Decollate(LinkList &L, LinkList &L1)
{//奇偶链表的分割
    L1 = new LNode;
    LinkList L2 = new LNode;

    LinkList p1 = L1;
    LinkList p2 = L2;

    for(int i = 1; L -> next; i++){
        if(i & 1){
            p1 -> next = L -> next;
            L -> next = L -> next -> next;
            p1 = p1 -> next;
            p1 -> next = nullptr;
        }
        else{
            p2 -> next = L -> next;
            L -> next = L -> next -> next;
            p2 = p2 -> next;
            p2 -> next = nullptr;
        }
    }
    p1 -> next = L2 -> next;

    delete L2;
}
```
