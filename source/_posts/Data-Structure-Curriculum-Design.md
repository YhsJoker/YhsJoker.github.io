---
title: 数据结构课设
date: 2023-11-17 00:13:11
tags:
  - [数据结构]
  - [C++]
categories: 作业
description: 数据结构课设，发布在头歌平台
---



## 第1关：系统函数调用

### 代码

```cpp
#include<bits/stdc++.h>
using namespace std;

using pfunc = void(*)();

#define SUBFUNC_LIST_SIZE (sizeof(subfuncList) / sizeof(pfunc))

bool Jump2Subfunc(pfunc subfuncList[], size_t subfuncNum){
    char subfuncCh;
    cin >> subfuncCh;
    int subfuncOrder = subfuncCh - '0';
    if(subfuncOrder < 0 || subfuncOrder >= subfuncNum) return false;
    pfunc subfunc = subfuncList[subfuncOrder];
    if(subfunc == nullptr) return false;
    subfunc();
    return true;
}

// 以下定义的函数可供其他函数调用，以实现本题功能
// 本题的输入需自己设置，可以使用switch case实现调用对应的函数
void InsertFood() {
    cout << "食材信息增加" << endl;
    static pfunc subfuncList[] = {
        nullptr
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;
    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void DeleteFood() {
    cout << "食材信息删除" << endl;
    static pfunc subfuncList[] = {
        nullptr
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;
    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void ModifyFood() {
    cout << "食材信息修改" << endl;
    static pfunc subfuncList[] = {
        nullptr
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;
    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void SeqSearch() {
    cout << "基于顺序表的顺序查找" << endl;
    static pfunc subfuncList[] = {
        nullptr
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;
    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void BinarySearch() {
    cout << "基于顺序表的折半查找" << endl;
    static pfunc subfuncList[] = {
        nullptr
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;
    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void SearchList() {
    cout << "基于链表的顺序查找" << endl;
    static pfunc subfuncList[] = {
        nullptr
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;
    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void SearchBST() {
    cout << "基于二叉排序树的查找" << endl;
    static pfunc subfuncList[] = {
        nullptr
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;
    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void TrieSearch() {
    cout << "基于字典树的查找" << endl;
    static pfunc subfuncList[] = {
        nullptr
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;
    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void SearchHash() {
    cout << "基于开放地址法的散列查找" << endl;
    static pfunc subfuncList[] = {
        nullptr
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;
    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void SearchHL() {
    cout << "基于链地址法的散列查找" << endl;
    static pfunc subfuncList[] = {
        nullptr
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;
    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void KMP() {
    cout << "基于KMP算法的食材关键信息查询" << endl;
    static pfunc subfuncList[] = {
        nullptr
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;
    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void InsertSort() {
    cout << "直接插入排序" << endl;
    static pfunc subfuncList[] = {
        nullptr
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;
    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void BInsertSort() {
    cout << "折半插入排序" << endl;
    static pfunc subfuncList[] = {
        nullptr
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;
    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void SelectSort() {
    cout << "简单选择排序" << endl;
    static pfunc subfuncList[] = {
        nullptr
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;
    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void BubbleSort() {
    cout << "冒泡排序" << endl;
    static pfunc subfuncList[] = {
        nullptr
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;
    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void QuickSort() {
    cout << "快速排序" << endl;
    static pfunc subfuncList[] = {
        nullptr
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;
    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void MSDSort() {
    cout << "高位优先字符串排序" << endl;

    static pfunc subfuncList[] = {
        nullptr
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;

    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void EntityRecognition() {
    cout << "基于规则的实体识别" << endl;

    static pfunc subfuncList[] = {
        nullptr
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;

    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void RelationExtraction() {
    cout << "基于规则的关系抽取" << endl;

    static pfunc subfuncList[] = {
        nullptr
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;

    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void CreateUDG() {
    cout << "基于邻接表的知识图谱构建" << endl;

    static pfunc subfuncList[] = {
        nullptr
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;

    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void QuestionAnswering() {
    cout << "基于路径推理的知识图谱多跳问答" << endl;

    static pfunc subfuncList[] = {
        nullptr
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;

    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void CreateAMG() {
    cout << "基于编辑距离的食材功效矩阵构建" << endl;

    static pfunc subfuncList[] = {
        nullptr
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;

    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void ShortestPathDIJ() {
    cout << "基于Dijkstra算法的食材推荐" << endl;

    static pfunc subfuncList[] = {
        nullptr
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;

    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void ShortestPathFloyd() {
    cout << "基于Floyd算法的食材推荐" << endl;

    static pfunc subfuncList[] = {
        nullptr
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;

    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void FoodADM() {
// 食材基本信息的增加、删除与修改模块，调用对应的功能函数实现
    cout << "食材基本信息的增加、删除与修改" << endl;
    static pfunc subfuncList[] = {
        nullptr, InsertFood, DeleteFood, ModifyFood
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;

    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void FoodSearch() {
// 基于多种查找策略的食材信息查找模块，调用对应的功能函数实现
    cout << "基于多种查找策略的食材信息查找" << endl;

    static pfunc subfuncList[] = {
        nullptr, SeqSearch, BinarySearch, SearchList, SearchBST, TrieSearch, SearchHash, SearchHL
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;

    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void FoodSort() {
// 基于多种排序策略的食材信息排序模块，调用对应的功能函数实现
    cout << "基于多种排序策略的食材信息排序" << endl;

    static pfunc subfuncList[] = {
        nullptr, InsertSort, BInsertSort, SelectSort, BubbleSort, QuickSort, MSDSort
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;

    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void FoodManagement() {
// 食材基本信息管理模块
// 调用FoodADM()、FoodSearch()、KMP()、FoodSort()函数实现
    cout << "食材基本信息管理" << endl;
    
    static pfunc subfuncList[] = {
        nullptr, FoodADM, FoodSearch, KMP, FoodSort
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;

    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void CreateKG() {
// 中医食疗知识图谱构建模块，调用对应的功能函数实现
    cout << "中医食疗知识图谱构建" << endl;
    static pfunc subfuncList[] = {
        nullptr, EntityRecognition, RelationExtraction, CreateUDG
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;

    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void QAAndRecommendation() {
// 中医食疗问答与推荐模块，调用对应的功能函数实现
    cout << "中医食疗问答与推荐" << endl;
    static pfunc subfuncList[] = {
        nullptr, QuestionAnswering, CreateAMG, ShortestPathDIJ, ShortestPathFloyd
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;

    while(Jump2Subfunc(subfuncList, subfuncNum));
}

void SystemCall() {
// 基于知识图谱的中医食疗数据管理与应用系统功能调用
// 调用FoodManagement()、CreateKG()、QAAndRecommendation()函数实现
    static pfunc subfuncList[] = {
        nullptr, FoodManagement, CreateKG, QAAndRecommendation
    };
    const size_t subfuncNum = SUBFUNC_LIST_SIZE;

    while(Jump2Subfunc(subfuncList, subfuncNum));

    cout << "退出系统" << endl;
}
```



## 第2关：食材信息增加

### 代码

```cpp
#include <bits/stdc++.h>
#define MAXSIZE 10000

using namespace std;
typedef struct{
	char name[100];		        // 中文名称
	char sname[100];	        // 英文名称
	char health[10000];	        // 养生功效
	char nutrition[10000];      // 营养与功效
	char expert[10000];	        // 专家提醒
	char link[10000];	        // 相关链接
	string recipe[30];	        // 养生保健食谱
	int recipe_size = 0;        // 食谱数量
	string therapy[30];	        // 食疗验方
	int therapy_size = 0;       // 验方数量
} Food;
typedef struct{
	Food *elem;                 // 指向数组的指针
	int length;                 // 数组的长度
} SqList;

void InitList(SqList &L){
	// 使用动态内存分配new进行初始化
	L.elem = new Food[MAXSIZE];
	L.length = 0;
}

void FreeList(SqList &L){
	// 释放内存
	delete[] L.elem;
	L.length = 0;
}

const char nameKey[] = "中文名称：";
const char snameKey[] = "英文名称：";
const char healthKey[] = "养生功效：";
const char nutritionKey[] = "营养与功效：";
const char expertKey[] = "专家提醒：";
const char linkKey[] = "相关链接：";
const char recipeKey[] = "养生保健食谱：";
const char therapyKey[] = "食疗验方：";



void ReadFile(SqList &L, string filename){
	// 从文件中读取食材信息，将其按顺序存入L.elem指向的数组中
	ifstream ifs(filename);
	
	if(!ifs.is_open()){
		return;
	}

    for(int i = 0; i < MAXSIZE; i++){
		L.elem[i].recipe_size = L.elem[i].therapy_size = 0;
	}
	
	string info;
	int foodOrder = 0;
	bool inRecipe = 0, inTherapy = 0;
	
	
	while(getline(ifs, info)){
		Food &food = L.elem[foodOrder];
		
		if(info.empty()){
			continue;
		}
		else if(info.front() == '#'){
			foodOrder++;
		}
		else if(info.find(nameKey) != string::npos){
			strcpy(food.name, info.c_str() + sizeof(nameKey) - 1);
		}
		else if(info.find(snameKey) != string::npos){
			strcpy(food.sname, info.c_str() + sizeof(snameKey) - 1);
		}
		else if(info.find(healthKey) != string::npos){
			strcpy(food.health, info.c_str() + sizeof(healthKey) - 1);
		}
		else if(info.find(nutritionKey) != string::npos){
			strcpy(food.nutrition, info.c_str() + sizeof(nutritionKey) - 1);
		}
		else if(info.find(expertKey) != string::npos){
			strcpy(food.expert, info.c_str() + sizeof(expertKey) - 1);
		}
		else if(info.find(linkKey) != string::npos){
			strcpy(food.link, info.c_str() + sizeof(linkKey) - 1);
		}
		else if(info.find(recipeKey) != string::npos){
			inRecipe = 1, inTherapy = 0;
			continue;
		}
		else if(info.find(therapyKey) != string::npos){
			inTherapy = 1, inRecipe = 0;
			continue;
		}
		else if(inRecipe){
			food.recipe[food.recipe_size++] = info;
			continue;
		}
		else if(inTherapy){
			food.therapy[food.therapy_size++] = info;
			continue;
		}
		inRecipe = inTherapy = 0;
	}
	
	L.length = foodOrder + 1;

	ifs.close();
}

template<typename T>
void PrintFood(T& os, const Food &food){
	os << nameKey << food.name << endl;
	os << snameKey << food.sname << endl;
	os << healthKey << food.health << endl;
	os << nutritionKey << food.nutrition << endl;
	os << expertKey << food.expert << endl;
	os << linkKey << food.link << endl;
	os << recipeKey << endl;
	for(int i = 0; i < food.recipe_size; i++){
		os << food.recipe[i] << endl;
	}
	os << therapyKey << endl;
	for(int i = 0; i < food.therapy_size; i++){
		os << food.therapy[i] << '\n';
	}
}

void SaveFile(SqList &L, string filename){
	// 保存食材信息到文件
	ofstream ofs(filename);
	if(!ofs.is_open()){
		return;
	}

	for(int i = 0; i < L.length; i++){
		Food &food = L.elem[i];
		PrintFood(ofs, food);
		if(i != L.length - 1){
			ofs << '#' << endl;
		}
	}
	
	ofs.close();
}

int FindFood(SqList &L, const char *foodName){
	for(int i = 0; i < L.length; i++){
		Food &food = L.elem[i];
		
		if(strcmp(food.name, foodName) == 0){
			return i;
		}
	}
	return -1;
}

void FoodCpy(Food &dst, const Food &src){
	strcpy(dst.name, src.name);
	strcpy(dst.sname, src.sname);
	strcpy(dst.health, src.health);
	strcpy(dst.nutrition, src.nutrition);
	strcpy(dst.expert, src.expert);
	strcpy(dst.link, src.link);
	dst.recipe_size = src.recipe_size;
	for(int i = 0; i < src.recipe_size; i++){
		dst.recipe[i] = src.recipe[i];
	}
	dst.therapy_size = src.therapy_size;
	for(int i = 0; i < src.therapy_size; i++){
		dst.therapy[i] = src.therapy[i];
	}
}

bool InsertFood(SqList &L){
	// 插入食材信息，输入食材中文名称、英文名称、养生功效、营养与功效、养生保健食谱和食疗验方信息
	// 如果插入成功，返回true，否则，返回false
	Food food;
	string info;
	
	getline(cin, info);
	strcpy(food.name, info.c_str());
	
	getline(cin, info);
	strcpy(food.sname, info.c_str());
	
	getline(cin, info);
	strcpy(food.health, info.c_str());
	
	getline(cin, info);
	strcpy(food.nutrition, info.c_str());
	
	getline(cin, info);
	strcpy(food.expert, info.c_str());
	
	getline(cin, info);
	strcpy(food.link, info.c_str());
	
	getline(cin, info);
	food.recipe_size = 0;
	int rec_sz = stoi(info);
	for(int i = 1; i <= rec_sz; i++){
		getline(cin, info);
		food.recipe[food.recipe_size++] = info;
	}
	
	getline(cin, info);
	food.therapy_size = 0;
	int the_sz = stoi(info);
	for(int i = 1; i <= the_sz; i++){
		getline(cin, info);
		food.therapy[food.therapy_size++] = info;
	}
	
	if(FindFood(L, food.name) != -1){
		return false;
	}
	
    FoodCpy(L.elem[L.length++], food);
	return true;
}

void Print(SqList &L){
	// 输出食材信息
	if(L.length == 0) return;
	Food &food = L.elem[L.length - 1];
	PrintFood(cout, food);
}
```



## 第3关：食材信息删除

### 代码

```cpp
#include <bits/stdc++.h>
#define MAXSIZE 10000

using namespace std;
typedef struct{
	char name[100];		        // 中文名称
	char sname[100];	        // 英文名称
	char health[10000];	        // 养生功效
	char nutrition[10000];      // 营养与功效
	char expert[10000];	        // 专家提醒
	char link[10000];	        // 相关链接
	string recipe[30];	        // 养生保健食谱
	int recipe_size = 0;        // 食谱数量
	string therapy[30];	        // 食疗验方
	int therapy_size = 0;       // 验方数量
} Food;
typedef struct{
	Food *elem;                 // 指向数组的指针
	int length;                 // 数组的长度
} SqList;

void InitList(SqList &L){
	// 使用动态内存分配new进行初始化
	L.elem = new Food[MAXSIZE];
	L.length = 0;
}

void FreeList(SqList &L){
	// 释放内存
	delete[] L.elem;
	L.length = 0;
}

const char nameKey[] = "中文名称：";
const char snameKey[] = "英文名称：";
const char healthKey[] = "养生功效：";
const char nutritionKey[] = "营养与功效：";
const char expertKey[] = "专家提醒：";
const char linkKey[] = "相关链接：";
const char recipeKey[] = "养生保健食谱：";
const char therapyKey[] = "食疗验方：";

void ReadFile(SqList &L, string filename){
	// 从文件中读取食材信息，将其按顺序存入L.elem指向的数组中
	ifstream ifs(filename);
	
	if(!ifs.is_open()){
		return;
	}

    for(int i = 0; i < MAXSIZE; i++){
		L.elem[i].recipe_size = L.elem[i].therapy_size = 0;
	}
	
	string info;
	int foodOrder = 0;
	bool inRecipe = 0, inTherapy = 0;
	
	
	while(getline(ifs, info)){
		Food &food = L.elem[foodOrder];
		
		if(info.empty()){
			continue;
		}
		else if(info.front() == '#'){
			foodOrder++;
		}
		else if(info.find(nameKey) != string::npos){
			strcpy(food.name, info.c_str() + sizeof(nameKey) - 1);
		}
		else if(info.find(snameKey) != string::npos){
			strcpy(food.sname, info.c_str() + sizeof(snameKey) - 1);
		}
		else if(info.find(healthKey) != string::npos){
			strcpy(food.health, info.c_str() + sizeof(healthKey) - 1);
		}
		else if(info.find(nutritionKey) != string::npos){
			strcpy(food.nutrition, info.c_str() + sizeof(nutritionKey) - 1);
		}
		else if(info.find(expertKey) != string::npos){
			strcpy(food.expert, info.c_str() + sizeof(expertKey) - 1);
		}
		else if(info.find(linkKey) != string::npos){
			strcpy(food.link, info.c_str() + sizeof(linkKey) - 1);
		}
		else if(info.find(recipeKey) != string::npos){
			inRecipe = 1, inTherapy = 0;
			continue;
		}
		else if(info.find(therapyKey) != string::npos){
			inTherapy = 1, inRecipe = 0;
			continue;
		}
		else if(inRecipe){
			food.recipe[food.recipe_size++] = info;
			continue;
		}
		else if(inTherapy){
			food.therapy[food.therapy_size++] = info;
			continue;
		}
		inRecipe = inTherapy = 0;
	}
	
	L.length = foodOrder + 1;
	
	ifs.close();
}

template<typename T>
void PrintFood(T& os, const Food &food){
	os << nameKey << food.name << endl;
	os << snameKey << food.sname << endl;
	os << healthKey << food.health << endl;
	os << nutritionKey << food.nutrition << endl;
	os << expertKey << food.expert << endl;
	os << linkKey << food.link << endl;
	os << recipeKey << endl;
	for(int i = 0; i < food.recipe_size; i++){
		os << food.recipe[i] << endl;
	}
	os << therapyKey << endl;
	for(int i = 0; i < food.therapy_size; i++){
		os << food.therapy[i] << endl;
	}
}

void SaveFile(SqList &L, string filename){
	// 保存食材信息到文件
	ofstream ofs(filename);
	if(!ofs.is_open()){
		return;
	}
	
	for(int i = 0; i < L.length; i++){
		Food &food = L.elem[i];
		PrintFood(ofs, food);
		if(i != L.length - 1){
			ofs << '#' << endl;
		}
	}
	
	ofs.close();
}

int FindFood(SqList &L, const char *foodName){
	for(int i = 0; i < L.length; i++){
		Food &food = L.elem[i];
		
		if(strcmp(food.name, foodName) == 0){
			return i;
		}
	}
	return -1;
}

bool InsertFood(SqList &L){
	// 插入食材信息，输入食材中文名称、英文名称、养生功效、营养与功效、养生保健食谱和食疗验方信息
	// 如果插入成功，返回true，否则，返回false
	Food food;
	string info;
	
	getline(cin, info);
	strcpy(food.name, info.c_str());
	
	getline(cin, info);
	strcpy(food.sname, info.c_str());
	
	getline(cin, info);
	strcpy(food.health, info.c_str());
	
	getline(cin, info);
	strcpy(food.nutrition, info.c_str());
	
	getline(cin, info);
	strcpy(food.expert, info.c_str());
	
	getline(cin, info);
	strcpy(food.link, info.c_str());
	
	getline(cin, info);
	food.recipe_size = 0;
	int rec_sz = stoi(info);
	for(int i = 1; i <= rec_sz; i++){
		getline(cin, info);
		food.recipe[food.recipe_size++] = info;
	}
	
	getline(cin, info);
	food.therapy_size = 0;
	int the_sz = stoi(info);
	for(int i = 1; i <= the_sz; i++){
		getline(cin, info);
		food.therapy[food.therapy_size++] = info;
	}
	
	if(FindFood(L, food.name) != -1){
		return false;
	}
	
	L.elem[L.length++] = food;
	return true;
}

void FoodCpy(Food &dst, const Food &src){
	strcpy(dst.name, src.name);
	strcpy(dst.sname, src.sname);
	strcpy(dst.health, src.health);
	strcpy(dst.nutrition, src.nutrition);
	strcpy(dst.expert, src.expert);
	strcpy(dst.link, src.link);
	dst.recipe_size = src.recipe_size;
	for(int i = 0; i < src.recipe_size; i++){
		dst.recipe[i] = src.recipe[i];
	}
	dst.therapy_size = src.therapy_size;
	for(int i = 0; i < src.therapy_size; i++){
		dst.therapy[i] = src.therapy[i];
	}
}

Food *DeleteFood(SqList &L, char *name){
	// 根据中文名称删除指定食材信息
	// 如果删除成功，返回该食材的信息，否则，返回NULL
	int foodPos = FindFood(L, name);
	if(foodPos == -1) return nullptr;
	
	Food *food = new Food;
	FoodCpy(*food, L.elem[foodPos]);
	
	for(int i = foodPos; i < L.length - 1; i++){
		FoodCpy(L.elem[i], L.elem[i + 1]);
	}
	L.length--;
	
	return food;
}

void Print(Food *food){
	// 输出食材信息
	PrintFood(cout, *food);
}
```



## 第4关：食材信息修改

### 代码

```cpp
#include <bits/stdc++.h>
#define MAXSIZE 10000

using namespace std;
typedef struct{
	char name[100];		        // 中文名称
	char sname[100];	        // 英文名称
	char health[10000];	        // 养生功效
	char nutrition[10000];      // 营养与功效
	char expert[10000];	        // 专家提醒
	char link[10000];	        // 相关链接
	string recipe[30];	        // 养生保健食谱
	int recipe_size = 0;        // 食谱数量
	string therapy[30];	        // 食疗验方
	int therapy_size = 0;       // 验方数量
} Food;
typedef struct{
	Food *elem;                 // 指向数组的指针
	int length;                 // 数组的长度
} SqList;

void InitList(SqList &L){
	// 使用动态内存分配new进行初始化
	L.elem = new Food[MAXSIZE];
	L.length = 0;
}

void FreeList(SqList &L){
	// 释放内存
	delete[] L.elem;
	L.length = 0;
}

const char nameKey[] = "中文名称：";
const char snameKey[] = "英文名称：";
const char healthKey[] = "养生功效：";
const char nutritionKey[] = "营养与功效：";
const char expertKey[] = "专家提醒：";
const char linkKey[] = "相关链接：";
const char recipeKey[] = "养生保健食谱：";
const char therapyKey[] = "食疗验方：";

void ReadFile(SqList &L, string filename){
	// 从文件中读取食材信息，将其按顺序存入L.elem指向的数组中
	ifstream ifs(filename);
	
	if(!ifs.is_open()){
		return;
	}
	
	for(int i = 0; i < MAXSIZE; i++){
		L.elem[i].recipe_size = L.elem[i].therapy_size = 0;
	}
	
	string info;
	int foodOrder = 0;
	bool inRecipe = 0, inTherapy = 0;
	
	
	while(getline(ifs, info)){
		Food &food = L.elem[foodOrder];
		
		if(info.empty()){
			continue;
		}
		else if(info.front() == '#'){
			foodOrder++;
		}
		else if(info.find(nameKey) != string::npos){
			strcpy(food.name, info.c_str() + sizeof(nameKey) - 1);
		}
		else if(info.find(snameKey) != string::npos){
			strcpy(food.sname, info.c_str() + sizeof(snameKey) - 1);
		}
		else if(info.find(healthKey) != string::npos){
			strcpy(food.health, info.c_str() + sizeof(healthKey) - 1);
		}
		else if(info.find(nutritionKey) != string::npos){
			strcpy(food.nutrition, info.c_str() + sizeof(nutritionKey) - 1);
		}
		else if(info.find(expertKey) != string::npos){
			strcpy(food.expert, info.c_str() + sizeof(expertKey) - 1);
		}
		else if(info.find(linkKey) != string::npos){
			strcpy(food.link, info.c_str() + sizeof(linkKey) - 1);
		}
		else if(info.find(recipeKey) != string::npos){
			inRecipe = 1, inTherapy = 0;
			continue;
		}
		else if(info.find(therapyKey) != string::npos){
			inTherapy = 1, inRecipe = 0;
			continue;
		}
		else if(inRecipe){
			food.recipe[food.recipe_size++] = info;
			continue;
		}
		else if(inTherapy){
			food.therapy[food.therapy_size++] = info;
			continue;
		}
		inRecipe = inTherapy = 0;
	}
	
	L.length = foodOrder + 1;
	
	ifs.close();
}

template<typename T>
void PrintFood(T& os, const Food &food){
	os << nameKey << food.name << endl;
	os << snameKey << food.sname << endl;
	os << healthKey << food.health << endl;
	os << nutritionKey << food.nutrition << endl;
	os << expertKey << food.expert << endl;
	os << linkKey << food.link << endl;
	os << recipeKey << endl;
	for(int i = 0; i < food.recipe_size; i++){
		os << food.recipe[i] << endl;
	}
	os << therapyKey << endl;
	for(int i = 0; i < food.therapy_size; i++){
		os << food.therapy[i] << endl;
	}
}

void SaveFile(SqList &L, string filename){
	// 保存食材信息到文件
	ofstream ofs(filename);
	if(!ofs.is_open()){
		return;
	}
	
	for(int i = 0; i < L.length; i++){
		Food &food = L.elem[i];
		PrintFood(ofs, food);
		if(i != L.length - 1){
			ofs << '#' << endl;
		}
	}
	
	ofs.close();
}

int FindFood(SqList &L, const char *foodName){
	for(int i = 0; i < L.length; i++){
		Food &food = L.elem[i];
		
		if(strcmp(food.name, foodName) == 0){
			return i;
		}
	}
	return -1;
}

bool InsertFood(SqList &L){
	// 插入食材信息，输入食材中文名称、英文名称、养生功效、营养与功效、养生保健食谱和食疗验方信息
	// 如果插入成功，返回true，否则，返回false
	Food food;
	string info;
	
	getline(cin, info);
	strcpy(food.name, info.c_str());
	
	getline(cin, info);
	strcpy(food.sname, info.c_str());
	
	getline(cin, info);
	strcpy(food.health, info.c_str());
	
	getline(cin, info);
	strcpy(food.nutrition, info.c_str());
	
	getline(cin, info);
	strcpy(food.expert, info.c_str());
	
	getline(cin, info);
	strcpy(food.link, info.c_str());
	
	getline(cin, info);
	food.recipe_size = 0;
	int rec_sz = stoi(info);
	for(int i = 1; i <= rec_sz; i++){
		getline(cin, info);
		food.recipe[food.recipe_size++] = info;
	}
	
	getline(cin, info);
	food.therapy_size = 0;
	int the_sz = stoi(info);
	for(int i = 1; i <= the_sz; i++){
		getline(cin, info);
		food.therapy[food.therapy_size++] = info;
	}
	
	if(FindFood(L, food.name) != -1){
		return false;
	}
	
	L.elem[L.length++] = food;
	return true;
}

void FoodCpy(Food &dst, const Food &src){
	strcpy(dst.name, src.name);
	strcpy(dst.sname, src.sname);
	strcpy(dst.health, src.health);
	strcpy(dst.nutrition, src.nutrition);
	strcpy(dst.expert, src.expert);
	strcpy(dst.link, src.link);
	dst.recipe_size = src.recipe_size;
	for(int i = 0; i < src.recipe_size; i++){
		dst.recipe[i] = src.recipe[i];
	}
	dst.therapy_size = src.therapy_size;
	for(int i = 0; i < src.therapy_size; i++){
		dst.therapy[i] = src.therapy[i];
	}
}

Food *DeleteFood(SqList &L, char *name){
	// 根据中文名称删除指定食材信息
	// 如果删除成功，返回该食材的信息，否则，返回NULL
	int foodPos = FindFood(L, name);
	if(foodPos == -1) return nullptr;
	
	Food *food = new Food;
	FoodCpy(*food, L.elem[foodPos]);
	
	for(int i = foodPos; i < L.length - 1; i++){
		FoodCpy(L.elem[i], L.elem[i + 1]);
	}
	L.length--;
	
	return food;
}

void Print(Food *food){
	// 输出食材信息
	PrintFood(cout, *food);
}

bool ModifyFood(SqList &L, int type, char *name, string lines[], int n){
	// 食材信息修改，如果type是0，则修改养生保健食谱，否则修改食疗验方信息
	// 如果修改成功，返回true，否则，返回false
	int foodPos = FindFood(L, name);
	if(foodPos == -1) return false;
	
	Food &food = L.elem[foodPos];
	
	if(type == 0){
		food.recipe_size = n;
		for(int i = 0; i < n; i++){
			food.recipe[i] = lines[i];
		}
	}
	else{
		food.therapy_size = n;
		for(int i = 0; i < n; i++){
			food.therapy[i] = lines[i];
		}
	}
	
	return true;
}

Food *getFood(SqList &L, char *name){
	// 获取修改后的食材信息
	int foodPos = FindFood(L, name);
	if(foodPos == -1) return nullptr;
	
	return &L.elem[foodPos];
}
```



## 第5关：基于顺序表的顺序查找

### 代码

```cpp
#include <bits/stdc++.h>
#define MAXSIZE 10000

using namespace std;
typedef struct{
	char name[100];		        // 中文名称
	char sname[100];	        // 英文名称
	char health[10000];	        // 养生功效
	char nutrition[10000];      // 营养与功效
	char expert[10000];	        // 专家提醒
	char link[10000];	        // 相关链接
	string recipe[30];	        // 养生保健食谱
	int recipe_size = 0;        // 食谱数量
	string therapy[30];	        // 食疗验方
	int therapy_size = 0;       // 验方数量
} Food;
typedef struct{
	Food *elem;                 // 指向数组的指针
	int length;                 // 数组的长度
} SqList;

void InitList(SqList &L){
	// 使用动态内存分配new进行初始化
	L.elem = new Food[MAXSIZE];
	L.length = 0;
}

void FreeList(SqList &L){
	// 释放内存
	delete[] L.elem;
	L.length = 0;
}

const char nameKey[] = "中文名称：";
const char snameKey[] = "英文名称：";
const char healthKey[] = "养生功效：";
const char nutritionKey[] = "营养与功效：";
const char expertKey[] = "专家提醒：";
const char linkKey[] = "相关链接：";
const char recipeKey[] = "养生保健食谱：";
const char therapyKey[] = "食疗验方：";

void ReadFile(SqList &L, string filename){
	// 从文件中读取食材信息，将其按顺序存入L.elem指向的数组中
	ifstream ifs(filename);
	
	if(!ifs.is_open()){
		return;
	}
	
	for(int i = 0; i < MAXSIZE; i++){
		L.elem[i].recipe_size = L.elem[i].therapy_size = 0;
	}
	
	string info;
	int foodOrder = 0;
	bool inRecipe = 0, inTherapy = 0;
	
	
	while(getline(ifs, info)){
		Food &food = L.elem[foodOrder];
		
		if(info.empty()){
			continue;
		}
		else if(info.front() == '#'){
			foodOrder++;
		}
		else if(info.find(nameKey) != string::npos){
			strcpy(food.name, info.c_str() + sizeof(nameKey) - 1);
		}
		else if(info.find(snameKey) != string::npos){
			strcpy(food.sname, info.c_str() + sizeof(snameKey) - 1);
		}
		else if(info.find(healthKey) != string::npos){
			strcpy(food.health, info.c_str() + sizeof(healthKey) - 1);
		}
		else if(info.find(nutritionKey) != string::npos){
			strcpy(food.nutrition, info.c_str() + sizeof(nutritionKey) - 1);
		}
		else if(info.find(expertKey) != string::npos){
			strcpy(food.expert, info.c_str() + sizeof(expertKey) - 1);
		}
		else if(info.find(linkKey) != string::npos){
			strcpy(food.link, info.c_str() + sizeof(linkKey) - 1);
		}
		else if(info.find(recipeKey) != string::npos){
			inRecipe = 1, inTherapy = 0;
			continue;
		}
		else if(info.find(therapyKey) != string::npos){
			inTherapy = 1, inRecipe = 0;
			continue;
		}
		else if(inRecipe){
			food.recipe[food.recipe_size++] = info;
			continue;
		}
		else if(inTherapy){
			food.therapy[food.therapy_size++] = info;
			continue;
		}
		inRecipe = inTherapy = 0;
	}
	
	L.length = foodOrder + 1;
	
	ifs.close();
}

template<typename T>
void PrintFood(T& os, const Food &food){
	os << nameKey << food.name << endl;
	os << snameKey << food.sname << endl;
	os << healthKey << food.health << endl;
	os << nutritionKey << food.nutrition << endl;
	os << expertKey << food.expert << endl;
	os << linkKey << food.link << endl;
    if(food.recipe_size){
        os << recipeKey << endl;
	    for(int i = 0; i < food.recipe_size; i++){
		    os << food.recipe[i] << endl;
	    }
    }
    if(food.therapy_size){
        os << therapyKey << endl;
	    for(int i = 0; i < food.therapy_size; i++){
		    os << food.therapy[i] << endl;
	    }
    }
}

void SaveFile(SqList &L, string filename){
	// 保存食材信息到文件
	ofstream ofs(filename);
	if(!ofs.is_open()){
		return;
	}
	
	for(int i = 0; i < L.length; i++){
		Food &food = L.elem[i];
		PrintFood(ofs, food);
		if(i != L.length - 1){
			ofs << '#' << endl;
		}
	}
	
	ofs.close();
}

int FindFood(SqList &L, const char *foodName){
	for(int i = 0; i < L.length; i++){
		Food &food = L.elem[i];
		
		if(strcmp(food.name, foodName) == 0){
			return i;
		}
	}
	return -1;
}

bool InsertFood(SqList &L){
	// 插入食材信息，输入食材中文名称、英文名称、养生功效、营养与功效、养生保健食谱和食疗验方信息
	// 如果插入成功，返回true，否则，返回false
	Food food;
	string info;
	
	getline(cin, info);
	strcpy(food.name, info.c_str());
	
	getline(cin, info);
	strcpy(food.sname, info.c_str());
	
	getline(cin, info);
	strcpy(food.health, info.c_str());
	
	getline(cin, info);
	strcpy(food.nutrition, info.c_str());
	
	getline(cin, info);
	strcpy(food.expert, info.c_str());
	
	getline(cin, info);
	strcpy(food.link, info.c_str());
	
	getline(cin, info);
	food.recipe_size = 0;
	int rec_sz = stoi(info);
	for(int i = 1; i <= rec_sz; i++){
		getline(cin, info);
		food.recipe[food.recipe_size++] = info;
	}
	
	getline(cin, info);
	food.therapy_size = 0;
	int the_sz = stoi(info);
	for(int i = 1; i <= the_sz; i++){
		getline(cin, info);
		food.therapy[food.therapy_size++] = info;
	}
	
	if(FindFood(L, food.name) != -1){
		return false;
	}
	
	L.elem[L.length++] = food;
	return true;
}

void FoodCpy(Food &dst, const Food &src){
	strcpy(dst.name, src.name);
	strcpy(dst.sname, src.sname);
	strcpy(dst.health, src.health);
	strcpy(dst.nutrition, src.nutrition);
	strcpy(dst.expert, src.expert);
	strcpy(dst.link, src.link);
	dst.recipe_size = src.recipe_size;
	for(int i = 0; i < src.recipe_size; i++){
		dst.recipe[i] = src.recipe[i];
	}
	dst.therapy_size = src.therapy_size;
	for(int i = 0; i < src.therapy_size; i++){
		dst.therapy[i] = src.therapy[i];
	}
}

Food *DeleteFood(SqList &L, char *name){
	// 根据中文名称删除指定食材信息
	// 如果删除成功，返回该食材的信息，否则，返回NULL
	int foodPos = FindFood(L, name);
	if(foodPos == -1) return nullptr;
	
	Food *food = new Food;
	FoodCpy(*food, L.elem[foodPos]);
	
	for(int i = foodPos; i < L.length - 1; i++){
		FoodCpy(L.elem[i], L.elem[i + 1]);
	}
	L.length--;
	
	return food;
}

void Print(SqList &L, int pos){
// 输出食材信息
    PrintFood(cout, L.elem[pos]);
}

bool ModifyFood(SqList &L, int type, char *name, string lines[], int n){
	// 食材信息修改，如果type是0，则修改养生保健食谱，否则修改食疗验方信息
	// 如果修改成功，返回true，否则，返回false
	int foodPos = FindFood(L, name);
	if(foodPos == -1) return false;
	
	Food &food = L.elem[foodPos];
	
	if(type == 0){
		food.recipe_size = n;
		for(int i = 0; i < n; i++){
			food.recipe[i] = lines[i];
		}
	}
	else{
		food.therapy_size = n;
		for(int i = 0; i < n; i++){
			food.therapy[i] = lines[i];
		}
	}
	
	return true;
}

Food *getFood(SqList &L, char *name){
	// 获取修改后的食材信息
	int foodPos = FindFood(L, name);
	if(foodPos == -1) return nullptr;
	
	return &L.elem[foodPos];
}

int SeqSearch(SqList &L, char *sname){
	// 在顺序表L中顺序查找食材英文名称等于sname的数据元素
	// 若找到，则返回该元素在表中的下标，否则返回-1
	for(int i = 0; i < L.length; i++){
		Food &food = L.elem[i];
		
		if(strcmp(food.sname, sname) == 0){
			return i;
		}
	}
	return -1;
}

double GetASL(SqList &L){
	// 返回基于顺序表的顺序查找的ASL
	int len = L.length;
	return (len + 1) / 2.0;
}
```



## 第6关：基于顺序表的折半查找

### 代码

```cpp
#include <bits/stdc++.h>
#define MAXSIZE 10000

using namespace std;
typedef struct{
	char name[100];		        // 中文名称
	char sname[100];	        // 英文名称
	char health[10000];	        // 养生功效
	char nutrition[10000];      // 营养与功效
	char expert[10000];	        // 专家提醒
	char link[10000];	        // 相关链接
	string recipe[30];	        // 养生保健食谱
	int recipe_size = 0;        // 食谱数量
	string therapy[30];	        // 食疗验方
	int therapy_size = 0;       // 验方数量
} Food;
typedef struct{
	Food *elem;                 // 指向数组的指针
	int length;                 // 数组的长度
} SqList;

void InitList(SqList &L){
	// 使用动态内存分配new进行初始化
	L.elem = new Food[MAXSIZE];
	L.length = 0;
}

void FreeList(SqList &L){
	// 释放内存
	delete[] L.elem;
	L.length = 0;
}

const char nameKey[] = "中文名称：";
const char snameKey[] = "英文名称：";
const char healthKey[] = "养生功效：";
const char nutritionKey[] = "营养与功效：";
const char expertKey[] = "专家提醒：";
const char linkKey[] = "相关链接：";
const char recipeKey[] = "养生保健食谱：";
const char therapyKey[] = "食疗验方：";

void ReadFile(SqList &L, string filename){
	// 从文件中读取食材信息，将其按顺序存入L.elem指向的数组中
	ifstream ifs(filename);
	
	if(!ifs.is_open()){
		return;
	}
	
	for(int i = 0; i < MAXSIZE; i++){
		L.elem[i].recipe_size = L.elem[i].therapy_size = 0;
	}
	
	string info;
	int foodOrder = 0;
	bool inRecipe = 0, inTherapy = 0;
	
	
	while(getline(ifs, info)){
		Food &food = L.elem[foodOrder];
		
		if(info.empty()){
			continue;
		}
		else if(info.front() == '#'){
			foodOrder++;
		}
		else if(info.find(nameKey) != string::npos){
			strcpy(food.name, info.c_str() + sizeof(nameKey) - 1);
		}
		else if(info.find(snameKey) != string::npos){
			strcpy(food.sname, info.c_str() + sizeof(snameKey) - 1);
		}
		else if(info.find(healthKey) != string::npos){
			strcpy(food.health, info.c_str() + sizeof(healthKey) - 1);
		}
		else if(info.find(nutritionKey) != string::npos){
			strcpy(food.nutrition, info.c_str() + sizeof(nutritionKey) - 1);
		}
		else if(info.find(expertKey) != string::npos){
			strcpy(food.expert, info.c_str() + sizeof(expertKey) - 1);
		}
		else if(info.find(linkKey) != string::npos){
			strcpy(food.link, info.c_str() + sizeof(linkKey) - 1);
		}
		else if(info.find(recipeKey) != string::npos){
			inRecipe = 1, inTherapy = 0;
			continue;
		}
		else if(info.find(therapyKey) != string::npos){
			inTherapy = 1, inRecipe = 0;
			continue;
		}
		else if(inRecipe){
			food.recipe[food.recipe_size++] = info;
			continue;
		}
		else if(inTherapy){
			food.therapy[food.therapy_size++] = info;
			continue;
		}
		inRecipe = inTherapy = 0;
	}
	
	L.length = foodOrder + 1;
	
	ifs.close();
}

template<typename T>
void PrintFood(T& os, const Food &food){
	os << nameKey << food.name << endl;
	os << snameKey << food.sname << endl;
	os << healthKey << food.health << endl;
	os << nutritionKey << food.nutrition << endl;
	os << expertKey << food.expert << endl;
	os << linkKey << food.link << endl;
	if(food.recipe_size){
		os << recipeKey << endl;
		for(int i = 0; i < food.recipe_size; i++){
			os << food.recipe[i] << endl;
		}
	}
	if(food.therapy_size){
		os << therapyKey << endl;
		for(int i = 0; i < food.therapy_size; i++){
			os << food.therapy[i] << endl;
		}
	}
}

void SaveFile(SqList &L, string filename){
	// 保存食材信息到文件
	ofstream ofs(filename);
	if(!ofs.is_open()){
		return;
	}
	
	for(int i = 0; i < L.length; i++){
		Food &food = L.elem[i];
		PrintFood(ofs, food);
		if(i != L.length - 1){
			ofs << '#' << endl;
		}
	}
	
	ofs.close();
}

int FindFood(SqList &L, const char *foodName){
	for(int i = 0; i < L.length; i++){
		Food &food = L.elem[i];
		
		if(strcmp(food.name, foodName) == 0){
			return i;
		}
	}
	return -1;
}

bool InsertFood(SqList &L){
	// 插入食材信息，输入食材中文名称、英文名称、养生功效、营养与功效、养生保健食谱和食疗验方信息
	// 如果插入成功，返回true，否则，返回false
	Food food;
	string info;
	
	getline(cin, info);
	strcpy(food.name, info.c_str());
	
	getline(cin, info);
	strcpy(food.sname, info.c_str());
	
	getline(cin, info);
	strcpy(food.health, info.c_str());
	
	getline(cin, info);
	strcpy(food.nutrition, info.c_str());
	
	getline(cin, info);
	strcpy(food.expert, info.c_str());
	
	getline(cin, info);
	strcpy(food.link, info.c_str());
	
	getline(cin, info);
	food.recipe_size = 0;
	int rec_sz = stoi(info);
	for(int i = 1; i <= rec_sz; i++){
		getline(cin, info);
		food.recipe[food.recipe_size++] = info;
	}
	
	getline(cin, info);
	food.therapy_size = 0;
	int the_sz = stoi(info);
	for(int i = 1; i <= the_sz; i++){
		getline(cin, info);
		food.therapy[food.therapy_size++] = info;
	}
	
	if(FindFood(L, food.name) != -1){
		return false;
	}
	
	L.elem[L.length++] = food;
	return true;
}

void FoodCpy(Food &dst, const Food &src){
	strcpy(dst.name, src.name);
	strcpy(dst.sname, src.sname);
	strcpy(dst.health, src.health);
	strcpy(dst.nutrition, src.nutrition);
	strcpy(dst.expert, src.expert);
	strcpy(dst.link, src.link);
	dst.recipe_size = src.recipe_size;
	for(int i = 0; i < src.recipe_size; i++){
		dst.recipe[i] = src.recipe[i];
	}
	dst.therapy_size = src.therapy_size;
	for(int i = 0; i < src.therapy_size; i++){
		dst.therapy[i] = src.therapy[i];
	}
}

Food *DeleteFood(SqList &L, char *name){
	// 根据中文名称删除指定食材信息
	// 如果删除成功，返回该食材的信息，否则，返回NULL
	int foodPos = FindFood(L, name);
	if(foodPos == -1) return nullptr;
	
	Food *food = new Food;
	FoodCpy(*food, L.elem[foodPos]);
	
	for(int i = foodPos; i < L.length - 1; i++){
		FoodCpy(L.elem[i], L.elem[i + 1]);
	}
	L.length--;
	
	return food;
}

void Print(Food *food){
	// 输出食材信息
	PrintFood(cout, *food);
}

void Print(SqList &L, int pos){
	//输出食材信息
	PrintFood(cout, L.elem[pos]);
}

bool ModifyFood(SqList &L, int type, char *name, string lines[], int n){
	// 食材信息修改，如果type是0，则修改养生保健食谱，否则修改食疗验方信息
	// 如果修改成功，返回true，否则，返回false
	int foodPos = FindFood(L, name);
	if(foodPos == -1) return false;
	
	Food &food = L.elem[foodPos];
	
	if(type == 0){
		food.recipe_size = n;
		for(int i = 0; i < n; i++){
			food.recipe[i] = lines[i];
		}
	}
	else{
		food.therapy_size = n;
		for(int i = 0; i < n; i++){
			food.therapy[i] = lines[i];
		}
	}
	
	return true;
}

Food *getFood(SqList &L, char *name){
	// 获取修改后的食材信息
	int foodPos = FindFood(L, name);
	if(foodPos == -1) return nullptr;
	
	return &L.elem[foodPos];
}

int SeqSearch(SqList &L, char *sname){
	// 在顺序表L中顺序查找食材英文名称等于sname的数据元素
	// 若找到，则返回该元素在表中的下标，否则返回-1
	for(int i = 0; i < L.length; i++){
		Food &food = L.elem[i];
		
		if(strcmp(food.sname, sname) == 0){
			return i;
		}
	}
	return -1;
}

void SortFood(SqList &L){
	// 从小到大排序
	for(int i = L.length - 1; i >= 0; i--){
		for(int j = 0; j < i; j++){
			Food &lhs = L.elem[j], &rhs = L.elem[j + 1];
			if(strcmp(lhs.sname, rhs.sname) > 0){
				swap(lhs, rhs);
			}
		}
	}
}

int BinarySearch(SqList &L, char *sname){
	// 在顺序表L中折半查找食材英文名称等于sname的数据元素
	// 若找到，则返回该元素在表中的下标，否则返回-1
	int lft = 0, rgt = L.length - 1;
	while(lft <= rgt){
		int mid = lft + rgt >> 1;
		int cmp = strcmp(sname, L.elem[mid].sname);
		if(cmp < 0){
			rgt = mid - 1;
		}
		else if(cmp > 0){
			lft = mid + 1;
		}
		else{
			return mid;
		}
	}
	return -1;
}

int build(int l, int r, int dep){
    if(l > r) return 0;
    int mid = l + r >> 1;
    return dep + build(l, mid - 1, dep + 1) + build(mid + 1, r, dep + 1);
}

double GetASL(SqList &L){
	// 返回基于顺序表的折半查找的ASL
	int n = L.length;
	return build(1, n, 1) / (double)n;
}
```



## 第7关：基于链表的顺序查找

### 代码

```cpp
#include <bits/stdc++.h>
#define MAXSIZE 10000
using namespace std;
typedef struct{
	char name[100];		        // 中文名称
	char sname[100];	        // 英文名称
	char health[10000];	        // 养生功效
	char nutrition[10000];      // 营养与功效
	char expert[10000];	        // 专家提醒
	char link[10000];	        // 相关链接
	string recipe[30];	        // 养生保健食谱
	int recipe_size = 0;        // 食谱数量
	string therapy[30];	        // 食疗验方
	int therapy_size = 0;       // 验方数量
} Food;
typedef struct LNode{
	Food data;			        // 食材信息
	struct LNode *next;         // 指向下一级结点
} LNode, *LinkList;

void InitList(LinkList &L){
	// 使用动态内存分配new进行初始化
	L = new LNode;
	L -> next = nullptr;
}

void FreeList(LinkList &L){
	// 释放内存
	while(L -> next){
		LinkList p = L -> next;
		L -> next = p -> next;
		delete p;
	}
	delete L;
}

const char nameKey[] = "中文名称：";
const char snameKey[] = "英文名称：";
const char healthKey[] = "养生功效：";
const char nutritionKey[] = "营养与功效：";
const char expertKey[] = "专家提醒：";
const char linkKey[] = "相关链接：";
const char recipeKey[] = "养生保健食谱：";
const char therapyKey[] = "食疗验方：";

void ReadFile(LinkList &L, string filename){
	// 从文件中读取食材信息，将其按顺序存入链表中
	ifstream ifs(filename);
	
	if(!ifs.is_open()){
		return;
	}
	
	string info;
	L -> next = new LNode;
	LinkList p = L -> next;
	p -> next = nullptr;
	
	
	bool inRecipe = 0, inTherapy = 0;
	
	
	while(getline(ifs, info)){
		Food &food = p -> data;
		
		if(info.empty()){
			continue;
		}
		else if(info.front() == '#'){
			p -> next = new LNode;
			p = p -> next;
			p -> next = nullptr;
		}
		else if(info.find(nameKey) != string::npos){
			strcpy(food.name, info.c_str() + sizeof(nameKey) - 1);
		}
		else if(info.find(snameKey) != string::npos){
			strcpy(food.sname, info.c_str() + sizeof(snameKey) - 1);
		}
		else if(info.find(healthKey) != string::npos){
			strcpy(food.health, info.c_str() + sizeof(healthKey) - 1);
		}
		else if(info.find(nutritionKey) != string::npos){
			strcpy(food.nutrition, info.c_str() + sizeof(nutritionKey) - 1);
		}
		else if(info.find(expertKey) != string::npos){
			strcpy(food.expert, info.c_str() + sizeof(expertKey) - 1);
		}
		else if(info.find(linkKey) != string::npos){
			strcpy(food.link, info.c_str() + sizeof(linkKey) - 1);
		}
		else if(info.find(recipeKey) != string::npos){
			inRecipe = 1, inTherapy = 0;
			continue;
		}
		else if(info.find(therapyKey) != string::npos){
			inTherapy = 1, inRecipe = 0;
			continue;
		}
		else if(inRecipe){
			food.recipe[food.recipe_size++] = info;
			continue;
		}
		else if(inTherapy){
			food.therapy[food.therapy_size++] = info;
			continue;
		}
		inRecipe = inTherapy = 0;
	}
	
	ifs.close();
}

template<typename T>
void PrintFood(T& os, const Food &food){
	os << nameKey << food.name << endl;
	os << snameKey << food.sname << endl;
	os << healthKey << food.health << endl;
	os << nutritionKey << food.nutrition << endl;
	os << expertKey << food.expert << endl;
	os << linkKey << food.link << endl;
	if(food.recipe_size){
		os << recipeKey << endl;
		for(int i = 0; i < food.recipe_size; i++){
			os << food.recipe[i] << endl;
		}
	}
	if(food.therapy_size){
		os << therapyKey << endl;
		for(int i = 0; i < food.therapy_size; i++){
			os << food.therapy[i] << endl;
		}
	}
}


void Print(LNode *p){
	// 输出食材信息
	PrintFood(cout, p -> data);
}

LNode *SearchList(LinkList &L, char *sname){
	// 在带头结点的单链表L中查找食材英文名称为sname的元素
	for(LinkList p = L -> next; p; p = p -> next){
		Food &food = p -> data;
		
		if(strcmp(food.sname, sname) == 0){
			return p;
		}
	}
	return nullptr;
}

size_t GetListSize(LinkList &L){
	if(!L) return 0;
	return GetListSize(L -> next) + 1;
}

double GetASL(LinkList &L){
	// 返回基于链表的顺序查找的ASL
	int n = GetListSize(L -> next);
	return (double)(n + 1) / 2;
}
```



## 第8关：基于二叉排序树的查找

### 代码

```cpp
#include <bits/stdc++.h>
#define MAXSIZE 10000
using namespace std;
typedef struct{
	char name[100];		        // 中文名称
	char sname[100];	        // 英文名称
	char health[10000];	        // 养生功效
	char nutrition[10000];      // 营养与功效
	char expert[10000];	        // 专家提醒
	char link[10000];	        // 相关链接
	string recipe[30];	        // 养生保健食谱
	int recipe_size = 0;        // 食谱数量
	string therapy[30];	        // 食疗验方
	int therapy_size = 0;       // 验方数量
} Food;
typedef struct BSTNode{
	Food data;				    // 食材信息
	struct BSTNode *lchild;     // 左孩子指针
	struct BSTNode *rchild;     // 右孩子指针
} BSTNode, *BSTree;

void InitBSTree(BSTree &T){
	// 二叉排序树初始化
	T = nullptr;
}

void FoodCpy(Food &dst, const Food &src){
	strcpy(dst.name, src.name);
	strcpy(dst.sname, src.sname);
	strcpy(dst.health, src.health);
	strcpy(dst.nutrition, src.nutrition);
	strcpy(dst.expert, src.expert);
	strcpy(dst.link, src.link);
	dst.recipe_size = src.recipe_size;
	for(int i = 0; i < src.recipe_size; i++){
		dst.recipe[i] = src.recipe[i];
	}
	dst.therapy_size = src.therapy_size;
	for(int i = 0; i < src.therapy_size; i++){
		dst.therapy[i] = src.therapy[i];
	}
}

void InsertBST(BSTree &T, Food e){ 
	// 当二叉排序树T中不存在关键字等于e.sname的数据元素时，则插入该元素
	if(!T){
		T = new BSTNode;
		T -> lchild = nullptr;
		T -> rchild = nullptr;
		FoodCpy(T -> data, e);
	}
	else{
		Food food = T -> data;
		int cmp = strcmp(e.sname, food.sname);
		if(cmp < 0){
			InsertBST(T -> lchild, e);
		}
		else if(cmp > 0){
			InsertBST(T -> rchild, e);
		}
	}
}

const char nameKey[] = "中文名称：";
const char snameKey[] = "英文名称：";
const char healthKey[] = "养生功效：";
const char nutritionKey[] = "营养与功效：";
const char expertKey[] = "专家提醒：";
const char linkKey[] = "相关链接：";
const char recipeKey[] = "养生保健食谱：";
const char therapyKey[] = "食疗验方：";

int ReadFile(BSTree &T, string filename){
	// 读取文件，调用InsertBST函数将每个食材数据插入二叉排序树
	// 返回食材的总数
	ifstream ifs(filename);
	
	if(!ifs.is_open()){
		return 0;
	}
	
	string info;
	Food food;
	bool inRecipe = 0, inTherapy = 0;
	int foodCnt = 0;
	
	
	while(getline(ifs, info)){
		if(info.empty()){
			continue;
		}
		else if(info.front() == '#'){
			InsertBST(T, food);
			foodCnt++;
			food.recipe_size = 0, food.therapy_size = 0;
		}
		else if(info.find(nameKey) != string::npos){
			strcpy(food.name, info.c_str() + sizeof(nameKey) - 1);
		}
		else if(info.find(snameKey) != string::npos){
			strcpy(food.sname, info.c_str() + sizeof(snameKey) - 1);
		}
		else if(info.find(healthKey) != string::npos){
			strcpy(food.health, info.c_str() + sizeof(healthKey) - 1);
		}
		else if(info.find(nutritionKey) != string::npos){
			strcpy(food.nutrition, info.c_str() + sizeof(nutritionKey) - 1);
		}
		else if(info.find(expertKey) != string::npos){
			strcpy(food.expert, info.c_str() + sizeof(expertKey) - 1);
		}
		else if(info.find(linkKey) != string::npos){
			strcpy(food.link, info.c_str() + sizeof(linkKey) - 1);
		}
		else if(info.find(recipeKey) != string::npos){
			inRecipe = 1, inTherapy = 0;
			continue;
		}
		else if(info.find(therapyKey) != string::npos){
			inTherapy = 1, inRecipe = 0;
			continue;
		}
		else if(inRecipe){
			food.recipe[food.recipe_size++] = info;
			continue;
		}
		else if(inTherapy){
			food.therapy[food.therapy_size++] = info;
			continue;
		}
		inRecipe = inTherapy = 0;
	}
	
	InsertBST(T, food);
	foodCnt++;
	
	ifs.close();
	return foodCnt;
}

template<typename T>
void PrintFood(T& os, const Food &food){
	os << nameKey << food.name << endl;
	os << snameKey << food.sname << endl;
	os << healthKey << food.health << endl;
	os << nutritionKey << food.nutrition << endl;
	os << expertKey << food.expert << endl;
	os << linkKey << food.link << endl;
	if(food.recipe_size){
		os << recipeKey << endl;
		for(int i = 0; i < food.recipe_size; i++){
			os << food.recipe[i] << endl;
		}
	}
	if(food.therapy_size){
		os << therapyKey << endl;
		for(int i = 0; i < food.therapy_size; i++){
			os << food.therapy[i] << endl;
		}
	}
}

void Print(BSTNode *T){
	// 输出食材信息
	PrintFood(cout, T -> data);
}

BSTNode *SearchBST(BSTree &T, char *sname){
	// 查找对应食材
	if(!T) return nullptr;
	Food food = T -> data;
	int cmp = strcmp(sname, food.sname);
	if(cmp < 0){
		return SearchBST(T -> lchild, sname);
	}
	else if(cmp > 0){
		return SearchBST(T -> rchild, sname);
	}
	else{
		return T;
	}
}

int GetSumCmp(BSTree T, int sumCmp){
	// 统计查找成功时的总比较次数
	if(!T) return 0;
	return GetSumCmp(T -> lchild, sumCmp + 1) + GetSumCmp(T -> rchild, sumCmp + 1) + sumCmp;
}

double GetASL(BSTree &T, int count){
	// 返回基于二叉排序树查找的ASL
	return (double)GetSumCmp(T, 1) / count;
}
```



## 第9关：基于字典树的查找

### 代码

```cpp
#include <bits/stdc++.h>
#define MAXSIZE 10000
using namespace std;
typedef struct{
	char name[100];		        // 中文名称
	char sname[100];	        // 英文名称
	char health[10000];	        // 养生功效
	char nutrition[10000];      // 营养与功效
	char expert[10000];	        // 专家提醒
	char link[10000];	        // 相关链接
	string recipe[30];	        // 养生保健食谱
	int recipe_size = 0;        // 食谱数量
	string therapy[30];	        // 食疗验方
	int therapy_size = 0;       // 验方数量
} Food;
typedef struct{
	Food *elem;                 // 指向数组的指针
	int length;                 // 数组的长度
} SqList;
typedef struct TNode{
	// 定义字典树结构体
	Food *foodPtr;		        // 食材指针
	struct TNode *child[53];    // 子结点的指针数组，由26个小写字母，26个大写字母，1个空格组成
} TNode, *TrieTree;

void InitList(SqList &L){
	// 使用动态内存分配new进行初始化
	L.elem = new Food[MAXSIZE];
	L.length = 0;
}

void FreeList(SqList &L){
	// 释放内存
	delete[] L.elem;
	L.length = 0;
}

const char nameKey[] = "中文名称：";
const char snameKey[] = "英文名称：";
const char healthKey[] = "养生功效：";
const char nutritionKey[] = "营养与功效：";
const char expertKey[] = "专家提醒：";
const char linkKey[] = "相关链接：";
const char recipeKey[] = "养生保健食谱：";
const char therapyKey[] = "食疗验方：";

void ReadFile(SqList &L, string filename){
	// 从文件中读取食材信息，将其按顺序存入L.elem指向的数组中
	ifstream ifs(filename);
	
	if(!ifs.is_open()){
		return;
	}
	
	for(int i = 0; i < MAXSIZE; i++){
		L.elem[i].recipe_size = L.elem[i].therapy_size = 0;
	}
	
	string info;
	int foodOrder = 0;
	bool inRecipe = 0, inTherapy = 0;
	
	
	while(getline(ifs, info)){
		Food &food = L.elem[foodOrder];
		
		if(info.empty()){
			continue;
		}
		else if(info.front() == '#'){
			foodOrder++;
		}
		else if(info.find(nameKey) != string::npos){
			strcpy(food.name, info.c_str() + sizeof(nameKey) - 1);
		}
		else if(info.find(snameKey) != string::npos){
			strcpy(food.sname, info.c_str() + sizeof(snameKey) - 1);
		}
		else if(info.find(healthKey) != string::npos){
			strcpy(food.health, info.c_str() + sizeof(healthKey) - 1);
		}
		else if(info.find(nutritionKey) != string::npos){
			strcpy(food.nutrition, info.c_str() + sizeof(nutritionKey) - 1);
		}
		else if(info.find(expertKey) != string::npos){
			strcpy(food.expert, info.c_str() + sizeof(expertKey) - 1);
		}
		else if(info.find(linkKey) != string::npos){
			strcpy(food.link, info.c_str() + sizeof(linkKey) - 1);
		}
		else if(info.find(recipeKey) != string::npos){
			inRecipe = 1, inTherapy = 0;
			continue;
		}
		else if(info.find(therapyKey) != string::npos){
			inTherapy = 1, inRecipe = 0;
			continue;
		}
		else if(inRecipe){
			food.recipe[food.recipe_size++] = info;
			continue;
		}
		else if(inTherapy){
			food.therapy[food.therapy_size++] = info;
			continue;
		}
		inRecipe = inTherapy = 0;
	}
	
	L.length = foodOrder + 1;
	
	ifs.close();
}

template<typename T>
void PrintFood(T& os, const Food &food){
	os << nameKey << food.name << endl;
	os << snameKey << food.sname << endl;
	os << healthKey << food.health << endl;
	os << nutritionKey << food.nutrition << endl;
	os << expertKey << food.expert << endl;
	os << linkKey << food.link << endl;
	if(food.recipe_size){
		os << recipeKey << endl;
		for(int i = 0; i < food.recipe_size; i++){
			os << food.recipe[i] << endl;
		}
	}
	if(food.therapy_size){
		os << therapyKey << endl;
		for(int i = 0; i < food.therapy_size; i++){
			os << food.therapy[i] << endl;
		}
	}
}


TNode *InitTNode(){
	// 初始化Trie树结点
	TrieTree T = new TNode;
	for(int i = 0; i < 53; i++){
		T -> child[i] = nullptr;
	}
	return T;
}

void FoodCpy(Food &dst, const Food &src){
	strcpy(dst.name, src.name);
	strcpy(dst.sname, src.sname);
	strcpy(dst.health, src.health);
	strcpy(dst.nutrition, src.nutrition);
	strcpy(dst.expert, src.expert);
	strcpy(dst.link, src.link);
	dst.recipe_size = src.recipe_size;
	for(int i = 0; i < src.recipe_size; i++){
		dst.recipe[i] = src.recipe[i];
	}
	dst.therapy_size = src.therapy_size;
	for(int i = 0; i < src.therapy_size; i++){
		dst.therapy[i] = src.therapy[i];
	}
}

int GetChildIdx(char ch){
	if(isupper(ch)) return ch - 'A';
	if(islower(ch)) return ch - 'a' + 26;
	return 52;
}

void InsertFood(TrieTree& T, const Food& food){
	TrieTree p = T;
	for(int i = 0; food.sname[i]; i++){
		int childIdx = GetChildIdx(food.sname[i]);
		if(!p -> child[childIdx]){
			p -> child[childIdx] = InitTNode();
		}
		p = p -> child[childIdx];
	}
	p -> foodPtr = new Food;
	FoodCpy(*p -> foodPtr, food);
}

TNode *BuildTree(SqList &L){
	// 构建基于链式存储的Trie树
	// 构建成功后返回指向根节点的指针
	
	TrieTree T = InitTNode();
	
	for(int i = 0; i < L.length; i++){
		Food &food = L.elem[i];
		InsertFood(T, food);
	}
	
	return T;
}

Food *TrieSearch(TNode *root, char *sname){
	// 基于字典树的查找
	// 如果查找成功则返回指向该食材的指针，如果查找失败则返回NULL
	TrieTree p = root;
	for(int i = 0; sname[i]; i++){
		int childIdx = GetChildIdx(sname[i]);
		if(!p -> child[childIdx]){
			return nullptr;
		}
		p = p -> child[childIdx];
	}
	return p -> foodPtr;
}

void Print(Food *food){
	// 输出Trie树中指针food指向的结点
	PrintFood(cout, *food);
}

double GetASL(SqList &L){
	// 计算查找成功时的平均查找长度ASL
	int totLength = 0;
	for(int i = 0; i < L.length; i++){
		Food &food = L.elem[i];
		totLength += strlen(food.sname);
	}
	return (double)totLength / L.length;
}
```



## 第10关：基于开放地址法的散列查找

### 代码

```cpp
#include <bits/stdc++.h>
#define m 200
using namespace std;
typedef struct{
	char name[100];		        // 中文名称
	char sname[100];	        // 英文名称
	char health[10000];	        // 养生功效
	char nutrition[10000];      // 营养与功效
	char expert[10000];	        // 专家提醒 
	char link[10000];	        // 相关链接
	string recipe[30];	        // 养生保健食谱
	int recipe_size = 0;        // 食谱数量
	string therapy[30];	        // 食疗验方
	int therapy_size = 0;       // 验方数量
} Food;
typedef struct{ 
	// 开放地址法散列表的存储表示
	Food *key;
	int length;
} HashTable;

void InitHT(HashTable &HT){
	// 散列表初始化
	HT.length = 0;
	HT.key = new Food[m];
	for(int i = 0; i < m; i++){
		strcpy(HT.key[i].sname, "");
	}
}

int Hash(char *sname){
	// 实现散列函数：字符串sname中各字符的下标（从0开始）的平方乘以字符对应的ASCII码值，相加后与199取余
	int sum = 0;
	for (int i = 0; i < strlen(sname); i++)
	{
		sum += ((i) * (i) * int(sname[i]));
	}
	return sum % 199;
}

void FoodCpy(Food &dst, const Food &src){
	strcpy(dst.name, src.name);
	strcpy(dst.sname, src.sname);
	strcpy(dst.health, src.health);
	strcpy(dst.nutrition, src.nutrition);
	strcpy(dst.expert, src.expert);
	strcpy(dst.link, src.link);
	dst.recipe_size = src.recipe_size;
	for(int i = 0; i < src.recipe_size; i++){
		dst.recipe[i] = src.recipe[i];
	}
	dst.therapy_size = src.therapy_size;
	for(int i = 0; i < src.therapy_size; i++){
		dst.therapy[i] = src.therapy[i];
	}
}

void HTInsert(HashTable &HT, Food f, int &sumCmp){
	// 往散列表中插入新的食材f
	// 在插入的过程中统计总的比较次数sumCmp
	int hsh = Hash(f.sname);
	for(int i = hsh; i != (hsh + m - 1) % m; i = (i + 1) % m){
		sumCmp++;
		Food &food = HT.key[i];
		if(strcmp(food.sname, "") == 0){
			FoodCpy(food, f);
			HT.length++;
			return;
		}
	}
}

const char nameKey[] = "中文名称：";
const char snameKey[] = "英文名称：";
const char healthKey[] = "养生功效：";
const char nutritionKey[] = "营养与功效：";
const char expertKey[] = "专家提醒：";
const char linkKey[] = "相关链接：";
const char recipeKey[] = "养生保健食谱：";
const char therapyKey[] = "食疗验方：";

template<typename T>
void PrintFood(T& os, const Food &food){
	os << nameKey << food.name << endl;
	os << snameKey << food.sname << endl;
	os << healthKey << food.health << endl;
	os << nutritionKey << food.nutrition << endl;
	os << expertKey << food.expert << endl;
	os << linkKey << food.link << endl;
	if(food.recipe_size){
		os << recipeKey << endl;
		for(int i = 0; i < food.recipe_size; i++){
			os << food.recipe[i] << endl;
		}
	}
	if(food.therapy_size){
		os << therapyKey << endl;
		for(int i = 0; i < food.therapy_size; i++){
			os << food.therapy[i] << endl;
		}
	}
}

void ReadFile(HashTable &HT, int &sumCmp, string filename){
	// 读取文件，调用HTInsert函数将每条食材数据插入散列表
	ifstream ifs(filename);
	
	if(!ifs.is_open()){
		return;
	}
	
	string info;
	Food food;
	bool inRecipe = 0, inTherapy = 0;
	
	
	while(getline(ifs, info)){
		if(info.empty()){
			continue;
		}
		else if(info.front() == '#'){
			HTInsert(HT, food, sumCmp);
			food.recipe_size = food.therapy_size = 0;
		}
		else if(info.find(nameKey) != string::npos){
			strcpy(food.name, info.c_str() + sizeof(nameKey) - 1);
		}
		else if(info.find(snameKey) != string::npos){
			strcpy(food.sname, info.c_str() + sizeof(snameKey) - 1);
		}
		else if(info.find(healthKey) != string::npos){
			strcpy(food.health, info.c_str() + sizeof(healthKey) - 1);
		}
		else if(info.find(nutritionKey) != string::npos){
			strcpy(food.nutrition, info.c_str() + sizeof(nutritionKey) - 1);
		}
		else if(info.find(expertKey) != string::npos){
			strcpy(food.expert, info.c_str() + sizeof(expertKey) - 1);
		}
		else if(info.find(linkKey) != string::npos){
			strcpy(food.link, info.c_str() + sizeof(linkKey) - 1);
		}
		else if(info.find(recipeKey) != string::npos){
			inRecipe = 1, inTherapy = 0;
			continue;
		}
		else if(info.find(therapyKey) != string::npos){
			inTherapy = 1, inRecipe = 0;
			continue;
		}
		else if(inRecipe){
			food.recipe[food.recipe_size++] = info;
			continue;
		}
		else if(inTherapy){
			food.therapy[food.therapy_size++] = info;
			continue;
		}
		inRecipe = inTherapy = 0;
	}
	
	HTInsert(HT, food, sumCmp);
	
	ifs.close();
}

void Print(HashTable HT, int pos){
	// 输出食材信息
	PrintFood(cout, HT.key[pos]);
}

int SearchHash(HashTable HT, char *key){
	// 在散列表HT中查找食材英文名称等于key的元素
	// 若找到，则返回散列表的单元标号，否则返回-1
	int hsh = Hash(key);
	for(int i = hsh; i != (hsh + m - 1) % m; i = (i + 1) % m){
		Food &food = HT.key[i];
		if(strcmp(food.sname, "") == 0){
			return -1;
		}
		if(strcmp(food.sname, key) == 0){
			return i;
		}
	}
	return -1;
}

double GetASL(HashTable HT, int sumCmp){
	// 返回基于开放地址法的散列查找的ASL
	return (double)sumCmp / HT.length;
}
```



## 第11关：基于链地址法的散列查找

### 代码

```cpp
#include <bits/stdc++.h>
#define m 200
using namespace std;
typedef struct{
	char name[100];		        // 中文名称
	char sname[100];	        // 英文名称
	char health[10000];	        // 养生功效
	char nutrition[10000];      // 营养与功效
	char expert[10000];	        // 专家提醒
	char link[10000];	        // 相关链接
	string recipe[30];	        // 养生保健食谱
	int recipe_size = 0;        // 食谱数量
	string therapy[30];	        // 食疗验方
	int therapy_size = 0;       // 验方数量
} Food;
typedef struct LNode{
	Food data;			        // 食材信息
	struct LNode *next;         // 指向下一级结点
} LNode, *LinkList;

typedef struct{ 
	// 开放地址法散列表的存储表示
	Food *key;
	int length;
} HashTable;

void InitList(LinkList *H){
	// 链表初始化
	for(int i = 0; i < m; i++){
		H[i] = new LNode;
		H[i] -> next = nullptr;
	}
}

int Hash(char *sname){
	// 实现散列函数：字符串sname中各字符的下标（从0开始）的平方乘以字符对应的ASCII码值，相加后与199取余
	int sum = 0;
	for (int i = 0; i < strlen(sname); i++){
		sum += ((i) * (i) * int(sname[i]));
	}
	return sum % 199;
}

void FoodCpy(Food &dst, const Food &src){
	strcpy(dst.name, src.name);
	strcpy(dst.sname, src.sname);
	strcpy(dst.health, src.health);
	strcpy(dst.nutrition, src.nutrition);
	strcpy(dst.expert, src.expert);
	strcpy(dst.link, src.link);
	dst.recipe_size = src.recipe_size;
	for(int i = 0; i < src.recipe_size; i++){
		dst.recipe[i] = src.recipe[i];
	}
	dst.therapy_size = src.therapy_size;
	for(int i = 0; i < src.therapy_size; i++){
		dst.therapy[i] = src.therapy[i];
	}
}


void ListInsert(LinkList *H, Food f, int &sumCmp){
	// 往散列表中插入新的食材f
	// 在插入的过程中统计总的比较次数sumCmp
	int hsh = Hash(f.sname);
	LinkList p = H[hsh];
	while(p -> next){
		Food &food = p -> next -> data;
		sumCmp++;
		if(strcmp(food.sname, f.sname) == 0) return;
        p = p -> next;
	}
    sumCmp++;
	p -> next = new LNode;
	p = p -> next;
	p -> next = nullptr;
	FoodCpy(p -> data, f);
}

const char nameKey[] = "中文名称：";
const char snameKey[] = "英文名称：";
const char healthKey[] = "养生功效：";
const char nutritionKey[] = "营养与功效：";
const char expertKey[] = "专家提醒：";
const char linkKey[] = "相关链接：";
const char recipeKey[] = "养生保健食谱：";
const char therapyKey[] = "食疗验方：";

template<typename T>
void PrintFood(T& os, const Food &food){
	os << nameKey << food.name << endl;
	os << snameKey << food.sname << endl;
	os << healthKey << food.health << endl;
	os << nutritionKey << food.nutrition << endl;
	os << expertKey << food.expert << endl;
	os << linkKey << food.link << endl;
	if(food.recipe_size){
		os << recipeKey << endl;
		for(int i = 0; i < food.recipe_size; i++){
			os << food.recipe[i] << endl;
		}
	}
	if(food.therapy_size){
		os << therapyKey << endl;
		for(int i = 0; i < food.therapy_size; i++){
			os << food.therapy[i] << endl;
		}
	}
}

int ReadFile(LinkList *H, int &sumCmp, string filename){
	// 读取文件，调用ListInsert函数将每条食材数据插入散列表
	// 返回食材数据的总数
	ifstream ifs(filename);
	
	if(!ifs.is_open()){
		return 0;
	}
	
	string info;
	Food food;
	int foodCnt = 0;
	bool inRecipe = 0, inTherapy = 0;
	
	
	while(getline(ifs, info)){
		if(info.empty()){
			continue;
		}
		else if(info.front() == '#'){
			ListInsert(H, food, sumCmp);
			foodCnt++;
			food.recipe_size = food.therapy_size = 0;
		}
		else if(info.find(nameKey) != string::npos){
			strcpy(food.name, info.c_str() + sizeof(nameKey) - 1);
		}
		else if(info.find(snameKey) != string::npos){
			strcpy(food.sname, info.c_str() + sizeof(snameKey) - 1);
		}
		else if(info.find(healthKey) != string::npos){
			strcpy(food.health, info.c_str() + sizeof(healthKey) - 1);
		}
		else if(info.find(nutritionKey) != string::npos){
			strcpy(food.nutrition, info.c_str() + sizeof(nutritionKey) - 1);
		}
		else if(info.find(expertKey) != string::npos){
			strcpy(food.expert, info.c_str() + sizeof(expertKey) - 1);
		}
		else if(info.find(linkKey) != string::npos){
			strcpy(food.link, info.c_str() + sizeof(linkKey) - 1);
		}
		else if(info.find(recipeKey) != string::npos){
			inRecipe = 1, inTherapy = 0;
			continue;
		}
		else if(info.find(therapyKey) != string::npos){
			inTherapy = 1, inRecipe = 0;
			continue;
		}
		else if(inRecipe){
			food.recipe[food.recipe_size++] = info;
			continue;
		}
		else if(inTherapy){
			food.therapy[food.therapy_size++] = info;
			continue;
		}
		inRecipe = inTherapy = 0;
	}
	
	ListInsert(H, food, sumCmp);
	foodCnt++;
	
	ifs.close();
	
	return foodCnt;
}

int SearchHL(LinkList *H, char *key){
	// 在散列表HT中查找食材英文名称等于key的元素
	// 若找到，则返回散列表的单元标号，否则返回-1
	int hsh = Hash(key);
	for(LinkList p = H[hsh]; p -> next; p = p -> next){
		Food &food = p -> next -> data;
		if(strcmp(food.sname, key) == 0) return hsh;
	}
	return -1;
}

double GetASL(int sumCmp, int count){
	// 返回基于链地址法的散列查找的ASL
	return (double)sumCmp / count;
}

void Print(LNode *p, char *sname){
	// 输出食材信息
	for(; p; p = p -> next){
		Food &food = p -> data;
		if(strcmp(food.sname, sname) == 0) PrintFood(cout, food);
	}
}
```



## 第12关：基于KMP算法的食材关键信息查询

### 代码

```cpp
#include <bits/stdc++.h>
#define MAXSIZE 10000
using namespace std;
typedef struct{
	char name[100];		        // 中文名称
	char sname[100];	        // 英文名称
	char health[10000];	        // 养生功效
	char nutrition[10000];      // 营养与功效
	char expert[10000];	        // 专家提醒
	char link[10000];	        // 相关链接
	string recipe[30];	        // 养生保健食谱
	int recipe_size = 0;        // 食谱数量
	string therapy[30];	        // 食疗验方
	int therapy_size = 0;       // 验方数量
} Food;
typedef struct{
	Food *elem;                 // 指向数组的指针
	int length;                 // 数组的长度
} SqList;

void InitList(SqList &L){
	// 使用动态内存分配new进行初始化
	L.elem = new Food[MAXSIZE];
	L.length = 0;
}

void FreeList(SqList &L){
	// 释放内存
	delete[] L.elem;
	L.length = 0;
}

const char nameKey[] = "中文名称：";
const char snameKey[] = "英文名称：";
const char healthKey[] = "养生功效：";
const char nutritionKey[] = "营养与功效：";
const char expertKey[] = "专家提醒：";
const char linkKey[] = "相关链接：";
const char recipeKey[] = "养生保健食谱：";
const char therapyKey[] = "食疗验方：";

void ReadFile(SqList &L, string filename){
	// 从文件中读取食材信息，将其按顺序存入L.elem指向的数组中
	ifstream ifs(filename);
	
	if(!ifs.is_open()){
		return;
	}
	
	for(int i = 0; i < MAXSIZE; i++){
		L.elem[i].recipe_size = L.elem[i].therapy_size = 0;
	}
	
	string info;
	int foodOrder = 0;
	bool inRecipe = 0, inTherapy = 0;
	
	
	while(getline(ifs, info)){
		Food &food = L.elem[foodOrder];
		
		if(info.empty()){
			continue;
		}
		else if(info.front() == '#'){
			foodOrder++;
		}
		else if(info.find(nameKey) != string::npos){
			strcpy(food.name, info.c_str() + sizeof(nameKey) - 1);
		}
		else if(info.find(snameKey) != string::npos){
			strcpy(food.sname, info.c_str() + sizeof(snameKey) - 1);
		}
		else if(info.find(healthKey) != string::npos){
			strcpy(food.health, info.c_str() + sizeof(healthKey) - 1);
		}
		else if(info.find(nutritionKey) != string::npos){
			strcpy(food.nutrition, info.c_str() + sizeof(nutritionKey) - 1);
		}
		else if(info.find(expertKey) != string::npos){
			strcpy(food.expert, info.c_str() + sizeof(expertKey) - 1);
		}
		else if(info.find(linkKey) != string::npos){
			strcpy(food.link, info.c_str() + sizeof(linkKey) - 1);
		}
		else if(info.find(recipeKey) != string::npos){
			inRecipe = 1, inTherapy = 0;
			continue;
		}
		else if(info.find(therapyKey) != string::npos){
			inTherapy = 1, inRecipe = 0;
			continue;
		}
		else if(inRecipe){
			food.recipe[food.recipe_size++] = info;
			continue;
		}
		else if(inTherapy){
			food.therapy[food.therapy_size++] = info;
			continue;
		}
		inRecipe = inTherapy = 0;
	}
	
	L.length = foodOrder + 1;
	
	ifs.close();
}

template<typename T>
void PrintFood(T& os, const Food &food){
	os << nameKey << food.name << endl;
	os << snameKey << food.sname << endl;
	os << healthKey << food.health << endl;
	os << nutritionKey << food.nutrition << endl;
	os << expertKey << food.expert << endl;
	os << linkKey << food.link << endl;
	if(food.recipe_size){
		os << recipeKey << endl;
		for(int i = 0; i < food.recipe_size; i++){
			os << food.recipe[i] << endl;
		}
	}
	if(food.therapy_size){
		os << therapyKey << endl;
		for(int i = 0; i < food.therapy_size; i++){
			os << food.therapy[i] << endl;
		}
	}
}

void SaveFile(SqList &L, string filename){
	// 保存食材信息到文件
	ofstream ofs(filename);
	if(!ofs.is_open()){
		return;
	}
	
	for(int i = 0; i < L.length; i++){
		Food &food = L.elem[i];
		PrintFood(ofs, food);
		if(i != L.length - 1){
			ofs << '#' << endl;
		}
	}
	
	ofs.close();
}

void GetNext(const char *T, int next[]){
	// 计算子串T的next数组
	next[0] = -1;
	for(int i = 1, j = -1; T[i]; i++){
		while(j >= 0 && T[j + 1] != T[i]) j = next[j];
		if(T[j + 1] == T[i]) j++;
		next[i] = j;
	}
}

bool KMP(const char *S, const char *T, int next[]){
	// 利用模式串T的next数组求子串T在主串S中是否存在
	// 如果查找成功则返回true，如果查找失败则返回false
	for(int i = 1, j = -1; S[i]; i++){
		while(j >= 0 && S[i] != T[j + 1]) j = next[j];
		if(S[i] == T[j + 1]) j++;
		if(!T[j + 1]) return true;
	}
	return false;
}

bool SearchList(SqList &L, char *keyword, int next[]){
	// 遍历顺序表食材的养生功效和营养与功效信息，调用KMP算法
	// 如果在食材中查找成功则返回true，如果查找失败则返回false
	bool exist = 0;
	for(int i = 0; i < L.length; i++){
		Food &food = L.elem[i];
		if(KMP(food.health, keyword, next) || KMP(food.nutrition, keyword, next)){
			exist = 1;
			cout << food.name << endl;
		}
	}
	return exist;
}
```



## 第13关：直接插入排序

### 代码

```cpp
#include <bits/stdc++.h>
#define MAXSIZE 10000
using namespace std;
typedef struct{
	char name[100];		        // 中文名称
	char sname[100];	        // 英文名称
	char health[10000];	        // 养生功效
	char nutrition[10000];      // 营养与功效
	char expert[10000];	        // 专家提醒
	char link[10000];	        // 相关链接
	string recipe[30];	        // 养生保健食谱
	int recipe_size = 0;        // 食谱数量
	string therapy[30];	        // 食疗验方
	int therapy_size = 0;       // 验方数量
} Food;
typedef struct{
	Food *elem;                 // 指向数组的指针
	int length;                 // 数组的长度
} SqList;

void InitList(SqList &L){
	// 使用动态内存分配new进行初始化
	L.elem = new Food[MAXSIZE];
	L.length = 0;
}

void FreeList(SqList &L){
	// 释放内存
	delete[] L.elem;
	L.length = 0;
}

const char nameKey[] = "中文名称：";
const char snameKey[] = "英文名称：";
const char healthKey[] = "养生功效：";
const char nutritionKey[] = "营养与功效：";
const char expertKey[] = "专家提醒：";
const char linkKey[] = "相关链接：";
const char recipeKey[] = "养生保健食谱：";
const char therapyKey[] = "食疗验方：";

void ReadFile(SqList &L, string filename){
	// 从文件中读取食材信息，将其按顺序存入L.elem指向的数组中
	ifstream ifs(filename);
	
	if(!ifs.is_open()){
		return;
	}
	
	for(int i = 0; i < MAXSIZE; i++){
		L.elem[i].recipe_size = L.elem[i].therapy_size = 0;
	}
	
	string info;
	int foodOrder = 1;
	bool inRecipe = 0, inTherapy = 0;
	
	
	while(getline(ifs, info)){
		Food &food = L.elem[foodOrder];
		
		if(info.empty()){
			continue;
		}
		else if(info.front() == '#'){
			foodOrder++;
		}
		else if(info.find(nameKey) != string::npos){
			strcpy(food.name, info.c_str() + sizeof(nameKey) - 1);
		}
		else if(info.find(snameKey) != string::npos){
			strcpy(food.sname, info.c_str() + sizeof(snameKey) - 1);
		}
		else if(info.find(healthKey) != string::npos){
			strcpy(food.health, info.c_str() + sizeof(healthKey) - 1);
		}
		else if(info.find(nutritionKey) != string::npos){
			strcpy(food.nutrition, info.c_str() + sizeof(nutritionKey) - 1);
		}
		else if(info.find(expertKey) != string::npos){
			strcpy(food.expert, info.c_str() + sizeof(expertKey) - 1);
		}
		else if(info.find(linkKey) != string::npos){
			strcpy(food.link, info.c_str() + sizeof(linkKey) - 1);
		}
		else if(info.find(recipeKey) != string::npos){
			inRecipe = 1, inTherapy = 0;
			continue;
		}
		else if(info.find(therapyKey) != string::npos){
			inTherapy = 1, inRecipe = 0;
			continue;
		}
		else if(inRecipe){
			food.recipe[food.recipe_size++] = info;
			continue;
		}
		else if(inTherapy){
			food.therapy[food.therapy_size++] = info;
			continue;
		}
		inRecipe = inTherapy = 0;
	}
	
	L.length = foodOrder;
	
	ifs.close();
}

void InsertSort(SqList &L, int &kcn, int &rmn){
	// 对顺序表L做直接插入排序，从后向前顺序比较
	// 注：L.elem[0]用做哨兵单元
	// 输出排序后的食材英文名称、KCN和RMN
	
	for(int i = 2; i <= L.length; i++){
        kcn++;
        if(strcmp(L.elem[i].sname, L.elem[i - 1].sname) < 0){
            L.elem[0] = L.elem[i];
            L.elem[i] = L.elem[i - 1];
            rmn += 2;
            int j;
            for(j = i - 2; kcn++, strcmp(L.elem[0].sname, L.elem[j].sname) < 0; j--){
                L.elem[j + 1] = L.elem[j];
                rmn++;
            }
            L.elem[j + 1] = L.elem[0];
            rmn++;
        }
	}
	
	for(int i = 1; i <= L.length; i++){
		cout << L.elem[i].sname << endl;
	}
	cout << "总的关键字比较次数KCN为：" << kcn << endl;
	cout << "总的记录移动次数RMN为：" << rmn << endl;
}
```



## 第14关：折半插入排序

### 代码

```cpp
#include <bits/stdc++.h>
#define MAXSIZE 10000
using namespace std;
typedef struct{
	char name[100];		        // 中文名称
	char sname[100];	        // 英文名称
	char health[10000];	        // 养生功效
	char nutrition[10000];      // 营养与功效
	char expert[10000];	        // 专家提醒
	char link[10000];	        // 相关链接
	string recipe[30];	        // 养生保健食谱
	int recipe_size = 0;        // 食谱数量
	string therapy[30];	        // 食疗验方
	int therapy_size = 0;       // 验方数量
} Food;
typedef struct{
	Food *elem;                 // 指向数组的指针
	int length;                 // 数组的长度
} SqList;

void InitList(SqList &L){
	// 使用动态内存分配new进行初始化
	L.elem = new Food[MAXSIZE];
	L.length = 0;
}

void FreeList(SqList &L){
	// 释放内存
	delete[] L.elem;
	L.length = 0;
}

const char nameKey[] = "中文名称：";
const char snameKey[] = "英文名称：";
const char healthKey[] = "养生功效：";
const char nutritionKey[] = "营养与功效：";
const char expertKey[] = "专家提醒：";
const char linkKey[] = "相关链接：";
const char recipeKey[] = "养生保健食谱：";
const char therapyKey[] = "食疗验方：";

void ReadFile(SqList &L, string filename){
	// 从文件中读取食材信息，将其按顺序存入L.elem指向的数组中
	ifstream ifs(filename);
	
	if(!ifs.is_open()){
		return;
	}
	
	for(int i = 0; i < MAXSIZE; i++){
		L.elem[i].recipe_size = L.elem[i].therapy_size = 0;
	}
	
	string info;
	int foodOrder = 1;
	bool inRecipe = 0, inTherapy = 0;
	
	
	while(getline(ifs, info)){
		Food &food = L.elem[foodOrder];
		
		if(info.empty()){
			continue;
		}
		else if(info.front() == '#'){
			foodOrder++;
		}
		else if(info.find(nameKey) != string::npos){
			strcpy(food.name, info.c_str() + sizeof(nameKey) - 1);
		}
		else if(info.find(snameKey) != string::npos){
			strcpy(food.sname, info.c_str() + sizeof(snameKey) - 1);
		}
		else if(info.find(healthKey) != string::npos){
			strcpy(food.health, info.c_str() + sizeof(healthKey) - 1);
		}
		else if(info.find(nutritionKey) != string::npos){
			strcpy(food.nutrition, info.c_str() + sizeof(nutritionKey) - 1);
		}
		else if(info.find(expertKey) != string::npos){
			strcpy(food.expert, info.c_str() + sizeof(expertKey) - 1);
		}
		else if(info.find(linkKey) != string::npos){
			strcpy(food.link, info.c_str() + sizeof(linkKey) - 1);
		}
		else if(info.find(recipeKey) != string::npos){
			inRecipe = 1, inTherapy = 0;
			continue;
		}
		else if(info.find(therapyKey) != string::npos){
			inTherapy = 1, inRecipe = 0;
			continue;
		}
		else if(inRecipe){
			food.recipe[food.recipe_size++] = info;
			continue;
		}
		else if(inTherapy){
			food.therapy[food.therapy_size++] = info;
			continue;
		}
		inRecipe = inTherapy = 0;
	}
	
	L.length = foodOrder;
	
	ifs.close();
}

void BInsertSort(SqList &L, int &kcn, int &rmn){
// 对顺序表做折半插入排序
// 注：L.elem[0]用做哨兵单元
// 输出排序后的食材英文名称、KCN和RMN
    for(int i = 2; i <= L.length; i++){
        L.elem[0] = L.elem[i];
        rmn++;
        int low = 1, high = i - 1;
        while(low <= high){
            int mid = low + high >> 1;
            if(kcn++, strcmp(L.elem[0].sname, L.elem[mid].sname) < 0) high = mid - 1;
            else low = mid + 1;
        }
        for(int j = i - 1; j >= high + 1; j--) L.elem[j + 1] = L.elem[j], rmn++;
        L.elem[high + 1] = L.elem[0];
        rmn++;
    }


    for(int i = 1; i <= L.length; i++){
		cout << L.elem[i].sname << endl;
	}
	cout << "总的关键字比较次数KCN为：" << kcn << endl;
	cout << "总的记录移动次数RMN为：" << rmn << endl;
}
```



## 第15关：简单选择排序

### 代码

```cpp
#include <bits/stdc++.h>
#define MAXSIZE 10000
using namespace std;
typedef struct{
	char name[100];		        // 中文名称
	char sname[100];	        // 英文名称
	char health[10000];	        // 养生功效
	char nutrition[10000];      // 营养与功效
	char expert[10000];	        // 专家提醒
	char link[10000];	        // 相关链接
	string recipe[30];	        // 养生保健食谱
	int recipe_size = 0;        // 食谱数量
	string therapy[30];	        // 食疗验方
	int therapy_size = 0;       // 验方数量
} Food;
typedef struct{
	Food *elem;                 // 指向数组的指针
	int length;                 // 数组的长度
} SqList;

void InitList(SqList &L){
	// 使用动态内存分配new进行初始化
	L.elem = new Food[MAXSIZE];
	L.length = 0;
}

void FreeList(SqList &L){
	// 释放内存
	delete[] L.elem;
	L.length = 0;
}

const char nameKey[] = "中文名称：";
const char snameKey[] = "英文名称：";
const char healthKey[] = "养生功效：";
const char nutritionKey[] = "营养与功效：";
const char expertKey[] = "专家提醒：";
const char linkKey[] = "相关链接：";
const char recipeKey[] = "养生保健食谱：";
const char therapyKey[] = "食疗验方：";

void ReadFile(SqList &L, string filename){
	// 从文件中读取食材信息，将其按顺序存入L.elem指向的数组中
	ifstream ifs(filename);
	
	if(!ifs.is_open()){
		return;
	}
	
	for(int i = 0; i < MAXSIZE; i++){
		L.elem[i].recipe_size = L.elem[i].therapy_size = 0;
	}
	
	string info;
	int foodOrder = 1;
	bool inRecipe = 0, inTherapy = 0;
	
	
	while(getline(ifs, info)){
		Food &food = L.elem[foodOrder];
		
		if(info.empty()){
			continue;
		}
		else if(info.front() == '#'){
			foodOrder++;
		}
		else if(info.find(nameKey) != string::npos){
			strcpy(food.name, info.c_str() + sizeof(nameKey) - 1);
		}
		else if(info.find(snameKey) != string::npos){
			strcpy(food.sname, info.c_str() + sizeof(snameKey) - 1);
		}
		else if(info.find(healthKey) != string::npos){
			strcpy(food.health, info.c_str() + sizeof(healthKey) - 1);
		}
		else if(info.find(nutritionKey) != string::npos){
			strcpy(food.nutrition, info.c_str() + sizeof(nutritionKey) - 1);
		}
		else if(info.find(expertKey) != string::npos){
			strcpy(food.expert, info.c_str() + sizeof(expertKey) - 1);
		}
		else if(info.find(linkKey) != string::npos){
			strcpy(food.link, info.c_str() + sizeof(linkKey) - 1);
		}
		else if(info.find(recipeKey) != string::npos){
			inRecipe = 1, inTherapy = 0;
			continue;
		}
		else if(info.find(therapyKey) != string::npos){
			inTherapy = 1, inRecipe = 0;
			continue;
		}
		else if(inRecipe){
			food.recipe[food.recipe_size++] = info;
			continue;
		}
		else if(inTherapy){
			food.therapy[food.therapy_size++] = info;
			continue;
		}
		inRecipe = inTherapy = 0;
	}
	
	L.length = foodOrder;
	
	ifs.close();
}

void SelectSort(SqList &L, int &kcn, int &rmn){
// 对顺序表做简单选择排序
// 注：L.elem[0]用做哨兵单元
// 输出排序后的食材英文名称、KCN和RMN
    for(int i = 1; i < L.length; i++){
        int k = i;
        for(int j = i + 1; j <= L.length; j++){
            if(kcn++, strcmp(L.elem[j].sname, L.elem[k].sname) < 0){
                k = j;
            }
        }
        if(k != i){
            swap(L.elem[i], L.elem[k]);
            rmn += 3;
        }
    }


    for(int i = 1; i <= L.length; i++){
		cout << L.elem[i].sname << endl;
	}
	cout << "总的关键字比较次数KCN为：" << kcn << endl;
	cout << "总的记录移动次数RMN为：" << rmn << endl;
}
```



## 第16关：冒泡排序

### 代码

```cpp
#include <bits/stdc++.h>
#define MAXSIZE 10000
using namespace std;
typedef struct{
	char name[100];		        // 中文名称
	char sname[100];	        // 英文名称
	char health[10000];	        // 养生功效
	char nutrition[10000];      // 营养与功效
	char expert[10000];	        // 专家提醒
	char link[10000];	        // 相关链接
	string recipe[30];	        // 养生保健食谱
	int recipe_size = 0;        // 食谱数量
	string therapy[30];	        // 食疗验方
	int therapy_size = 0;       // 验方数量
} Food;
typedef struct{
	Food *elem;                 // 指向数组的指针
	int length;                 // 数组的长度
} SqList;

void InitList(SqList &L){
	// 使用动态内存分配new进行初始化
	L.elem = new Food[MAXSIZE];
	L.length = 0;
}

void FreeList(SqList &L){
	// 释放内存
	delete[] L.elem;
	L.length = 0;
}

const char nameKey[] = "中文名称：";
const char snameKey[] = "英文名称：";
const char healthKey[] = "养生功效：";
const char nutritionKey[] = "营养与功效：";
const char expertKey[] = "专家提醒：";
const char linkKey[] = "相关链接：";
const char recipeKey[] = "养生保健食谱：";
const char therapyKey[] = "食疗验方：";

void ReadFile(SqList &L, string filename){
	// 从文件中读取食材信息，将其按顺序存入L.elem指向的数组中
	ifstream ifs(filename);
	
	if(!ifs.is_open()){
		return;
	}
	
	for(int i = 0; i < MAXSIZE; i++){
		L.elem[i].recipe_size = L.elem[i].therapy_size = 0;
	}
	
	string info;
	int foodOrder = 1;
	bool inRecipe = 0, inTherapy = 0;
	
	
	while(getline(ifs, info)){
		Food &food = L.elem[foodOrder];
		
		if(info.empty()){
			continue;
		}
		else if(info.front() == '#'){
			foodOrder++;
		}
		else if(info.find(nameKey) != string::npos){
			strcpy(food.name, info.c_str() + sizeof(nameKey) - 1);
		}
		else if(info.find(snameKey) != string::npos){
			strcpy(food.sname, info.c_str() + sizeof(snameKey) - 1);
		}
		else if(info.find(healthKey) != string::npos){
			strcpy(food.health, info.c_str() + sizeof(healthKey) - 1);
		}
		else if(info.find(nutritionKey) != string::npos){
			strcpy(food.nutrition, info.c_str() + sizeof(nutritionKey) - 1);
		}
		else if(info.find(expertKey) != string::npos){
			strcpy(food.expert, info.c_str() + sizeof(expertKey) - 1);
		}
		else if(info.find(linkKey) != string::npos){
			strcpy(food.link, info.c_str() + sizeof(linkKey) - 1);
		}
		else if(info.find(recipeKey) != string::npos){
			inRecipe = 1, inTherapy = 0;
			continue;
		}
		else if(info.find(therapyKey) != string::npos){
			inTherapy = 1, inRecipe = 0;
			continue;
		}
		else if(inRecipe){
			food.recipe[food.recipe_size++] = info;
			continue;
		}
		else if(inTherapy){
			food.therapy[food.therapy_size++] = info;
			continue;
		}
		inRecipe = inTherapy = 0;
	}
	
	L.length = foodOrder;
	
	ifs.close();
}

void BubbleSort(SqList &L, int &kcn, int &rmn){
// 对顺序表L做冒泡排序
// 注：elem[0]闲置
// 输出排序后的食材英文名称、KCN和RMN
    int m = L.length - 1;
    int flag = 1;
    while((m > 0) && (flag == 1)){
        flag = 0;
        for(int j = 1; j <= m; j++){
            if(kcn++, strcmp(L.elem[j].sname, L.elem[j + 1].sname) > 0){
                flag = 1;
                swap(L.elem[j], L.elem[j + 1]);
                rmn += 3;
            }
        }
        m--;
    }

    for(int i = 1; i <= L.length; i++){
		cout << L.elem[i].sname << endl;
	}
	cout << "总的关键字比较次数KCN为：" << kcn << endl;
	cout << "总的记录移动次数RMN为：" << rmn << endl;
}
```



## 第17关：快速排序

### 代码

```cpp
#include <bits/stdc++.h>
#define MAXSIZE 10000
using namespace std;
typedef struct{
	char name[100];		        // 中文名称
	char sname[100];	        // 英文名称
	char health[10000];	        // 养生功效
	char nutrition[10000];      // 营养与功效
	char expert[10000];	        // 专家提醒
	char link[10000];	        // 相关链接
	string recipe[30];	        // 养生保健食谱
	int recipe_size = 0;        // 食谱数量
	string therapy[30];	        // 食疗验方
	int therapy_size = 0;       // 验方数量
} Food;
typedef struct{
	Food *elem;                 // 指向数组的指针
	int length;                 // 数组的长度
} SqList;

void InitList(SqList &L){
	// 使用动态内存分配new进行初始化
	L.elem = new Food[MAXSIZE];
	L.length = 0;
}

void FreeList(SqList &L){
	// 释放内存
	delete[] L.elem;
	L.length = 0;
}

const char nameKey[] = "中文名称：";
const char snameKey[] = "英文名称：";
const char healthKey[] = "养生功效：";
const char nutritionKey[] = "营养与功效：";
const char expertKey[] = "专家提醒：";
const char linkKey[] = "相关链接：";
const char recipeKey[] = "养生保健食谱：";
const char therapyKey[] = "食疗验方：";

void ReadFile(SqList &L, string filename){
	// 从文件中读取食材信息，将其按顺序存入L.elem指向的数组中
	ifstream ifs(filename);
	
	if(!ifs.is_open()){
		return;
	}
	
	for(int i = 0; i < MAXSIZE; i++){
		L.elem[i].recipe_size = L.elem[i].therapy_size = 0;
	}
	
	string info;
	int foodOrder = 1;
	bool inRecipe = 0, inTherapy = 0;
	
	
	while(getline(ifs, info)){
		Food &food = L.elem[foodOrder];
		
		if(info.empty()){
			continue;
		}
		else if(info.front() == '#'){
			foodOrder++;
		}
		else if(info.find(nameKey) != string::npos){
			strcpy(food.name, info.c_str() + sizeof(nameKey) - 1);
		}
		else if(info.find(snameKey) != string::npos){
			strcpy(food.sname, info.c_str() + sizeof(snameKey) - 1);
		}
		else if(info.find(healthKey) != string::npos){
			strcpy(food.health, info.c_str() + sizeof(healthKey) - 1);
		}
		else if(info.find(nutritionKey) != string::npos){
			strcpy(food.nutrition, info.c_str() + sizeof(nutritionKey) - 1);
		}
		else if(info.find(expertKey) != string::npos){
			strcpy(food.expert, info.c_str() + sizeof(expertKey) - 1);
		}
		else if(info.find(linkKey) != string::npos){
			strcpy(food.link, info.c_str() + sizeof(linkKey) - 1);
		}
		else if(info.find(recipeKey) != string::npos){
			inRecipe = 1, inTherapy = 0;
			continue;
		}
		else if(info.find(therapyKey) != string::npos){
			inTherapy = 1, inRecipe = 0;
			continue;
		}
		else if(inRecipe){
			food.recipe[food.recipe_size++] = info;
			continue;
		}
		else if(inTherapy){
			food.therapy[food.therapy_size++] = info;
			continue;
		}
		inRecipe = inTherapy = 0;
	}
	
	L.length = foodOrder;
	
	ifs.close();
}

int Partition(SqList &L, int low, int high, int &kcn, int &rmn){
// 对顺序表中的子表elem[low..high]进行一趟排序，返回枢轴位置
// 用子表的第一个记录做枢轴记录
// 注：L.elem[0]用来存枢轴记录
    L.elem[0] = L.elem[low], rmn++;
    char pivot[100];
    strcpy(pivot, L.elem[low].sname);
    while(low < high){
        while(low < high && (kcn++, strcmp(L.elem[high].sname, pivot) >= 0)) high--;
        L.elem[low] = L.elem[high], rmn++;
        while(low < high && (kcn++, strcmp(L.elem[low].sname, pivot) <= 0)) low++;
        L.elem[high] = L.elem[low], rmn++;
    }
    L.elem[low] = L.elem[0], rmn++;
    return low;
}

void QSort(SqList &L, int low, int high, int &kcn, int &rmn){
// 调用前置初值：low=1; high=L.length;
// 对顺序表L中的子序列L.elem[low..high]做快速排序
    if(low < high){
        int pivotloc = Partition(L, low, high, kcn, rmn);
        QSort(L, low, pivotloc - 1, kcn, rmn);
        QSort(L, pivotloc + 1, high, kcn, rmn);
    }
}

void QuickSort(SqList &L){
// 对顺序表做快速排序
// 输出排序后的食材英文名称、KCN和RMN
    int kcn = 0, rmn = 0;

    QSort(L, 1, L.length, kcn, rmn);
    for(int i = 1; i <= L.length; i++){
		cout << L.elem[i].sname << endl;
	}
	cout << "总的关键字比较次数KCN为：" << kcn << endl;
	cout << "总的记录移动次数RMN为：" << rmn << endl;
}
```



## 第18关：高位优先字符串排序

### 代码

```cpp
#include <bits/stdc++.h>
#define MAXSIZE 10000
using namespace std;
typedef struct{
    char name[100];             // 中文名称
    char sname[100];            // 英文名称
    char health[10000];         // 养生功效
    char nutrition[10000];      // 营养与功效
    char expert[10000];         // 专家提醒
    char link[10000];           // 相关链接
    string recipe[30];          // 养生保健食谱
    int recipe_size = 0;        // 食谱数量
    string therapy[30];         // 食疗验方
    int therapy_size = 0;       // 验方数量
} Food;
typedef struct{
    Food *elem;                 // 指向数组的指针
    int length;                 // 数组的长度
}SqList;

void InitList(SqList &L){
	// 使用动态内存分配new进行初始化
	L.elem = new Food[MAXSIZE];
	L.length = 0;
}

void FreeList(SqList &L){
	// 释放内存
	delete[] L.elem;
	L.length = 0;
}

const char nameKey[] = "中文名称：";
const char snameKey[] = "英文名称：";
const char healthKey[] = "养生功效：";
const char nutritionKey[] = "营养与功效：";
const char expertKey[] = "专家提醒：";
const char linkKey[] = "相关链接：";
const char recipeKey[] = "养生保健食谱：";
const char therapyKey[] = "食疗验方：";

void ReadFile(SqList &L, string filename){
	// 从文件中读取食材信息，将其按顺序存入L.elem指向的数组中
	ifstream ifs(filename);
	
	if(!ifs.is_open()){
		return;
	}
	
	for(int i = 0; i < MAXSIZE; i++){
		L.elem[i].recipe_size = L.elem[i].therapy_size = 0;
	}
	
	string info;
	int foodOrder = 0;
	bool inRecipe = 0, inTherapy = 0;
	
	
	while(getline(ifs, info)){
		Food &food = L.elem[foodOrder];
		
		if(info.empty()){
			continue;
		}
		else if(info.front() == '#'){
			foodOrder++;
		}
		else if(info.find(nameKey) != string::npos){
			strcpy(food.name, info.c_str() + sizeof(nameKey) - 1);
		}
		else if(info.find(snameKey) != string::npos){
			strcpy(food.sname, info.c_str() + sizeof(snameKey) - 1);
		}
		else if(info.find(healthKey) != string::npos){
			strcpy(food.health, info.c_str() + sizeof(healthKey) - 1);
		}
		else if(info.find(nutritionKey) != string::npos){
			strcpy(food.nutrition, info.c_str() + sizeof(nutritionKey) - 1);
		}
		else if(info.find(expertKey) != string::npos){
			strcpy(food.expert, info.c_str() + sizeof(expertKey) - 1);
		}
		else if(info.find(linkKey) != string::npos){
			strcpy(food.link, info.c_str() + sizeof(linkKey) - 1);
		}
		else if(info.find(recipeKey) != string::npos){
			inRecipe = 1, inTherapy = 0;
			continue;
		}
		else if(info.find(therapyKey) != string::npos){
			inTherapy = 1, inRecipe = 0;
			continue;
		}
		else if(inRecipe){
			food.recipe[food.recipe_size++] = info;
			continue;
		}
		else if(inTherapy){
			food.therapy[food.therapy_size++] = info;
			continue;
		}
		inRecipe = inTherapy = 0;
	}
	
	L.length = foodOrder + 1;
	
	ifs.close();
}

const int MX_ASCII = 256;

int ToIdx(SqList &L, int i, int d){
    int length = strlen(L.elem[i].sname);
    if(d > length) return -1;
    return L.elem[i].sname[d];
}

void MSDSort(SqList &L, SqList &L2, int l, int r, int d){
//L为原始的顺序表，L2为辅助排序开辟的顺序表，l是排序的下界，r是排序的上界
//d为排序的字母的下标位置，从sname中下标为0的位置开始，往后递归处理
    if(l >= r) return;
    int *count = new int[MX_ASCII + 2];
    memset(count, 0, sizeof(int) * (MX_ASCII + 2));
    for(int i = l; i <= r; i++){
        count[ToIdx(L, i, d) + 2]++;
    }
    for(int i = 0; i < MX_ASCII + 1; i++){
        count[i + 1] += count[i];
    }
    for(int i = l; i <= r; i++){
        L2.elem[count[ToIdx(L, i, d) + 1]++] = L.elem[i];
    }
    for(int i = l; i <= r; i++){
        L.elem[i] = L2.elem[i - l];
    }
    for(int i = 0; i < MX_ASCII; i++){
        MSDSort(L, L2, l + count[i], l + count[i + 1] - 1, d + 1);
    }
    delete[] count;
}
```



## 第19关：基于规则的实体识别

### 代码

```cpp
#include <bits/stdc++.h>
#define MAXSIZE 10000
using namespace std;

bool EntityRecognition(const char *S, const char *T){
// S为非结构化文本，T为规则
// 如果匹配成功返回true，否则返回false
// 输出所有匹配到的实体
    bool match_succeed = 0;
    for(int i = 0; S[i]; i++){
        bool isMatch = 0;
        for(int p = i, q = 0; ; p++, q++){
            if(!T[q]){
                isMatch = 1;
                break;
            }
            if(T[q] == '*'){
                if(S[p] & (1 << 7)) p += 2;
                continue;
            }
            if(S[p] != T[q]) break;
        }
        if(isMatch){
            match_succeed = 1;
            for(int p = i, q = 0; T[q]; p++, q++){
                if(T[q] == '*'){
                    if(S[p] & (1 << 7)){
                        cout << S[p] << S[p + 1] << S[p + 2];
                        p += 2;
                    }
                    else{
                        cout << S[p];
                    }
                }
            }
            cout << endl;
        }
    }
    return match_succeed;
}
```



## 第20关：基于规则的关系抽取

### 代码

```cpp
#include <bits/stdc++.h>
#define MAXSIZE 10000
using namespace std;
typedef struct{
	string relation;    //关系名称
	string rule[10];    //规则数组
} Relation;

bool TransPattern(char *A, char *B, string rule, char *pattern){
    pattern[0] = 0;
    for(char c : rule){
        if(c == 'A'){
            strcat(pattern, A);
        }
        else if(c == 'B'){
            strcat(pattern, B);
        }
        else{
            strncat(pattern, &c, 1);
        }
    }
}

bool Match(char *text, char *pattern){
    for(int i = 0; text[i]; i++){
        for(int p = i, q = 0; ; p++, q++){
            if(!pattern[q]){
                return true;
            }
            if(text[p] != pattern[q]) break;
        }
    }
    return false;
}

bool RelationExtraction(char *text, char *entity1, char *entity2, Relation *r){
// 如果实体之间存在关系返回true，否则返回false
// 输出所有存在的三元组
    char *pattern = new char[1000];
    bool match_succeed = 0;
    for(int i = 0; r[i].relation.size(); i++){
        for(int j = 0; r[i].rule[j].size(); j++){
            TransPattern(entity1, entity2, r[i].rule[j], pattern);
            if(Match(text, pattern)){
                match_succeed = 1;
                cout << entity1 << '-' << r[i].relation << '-' << entity2 << endl;
            }
        }
    }
    delete[] pattern;
    return match_succeed;
}
```



## 第21关：基于邻接表的知识图谱构建

### 代码

```cpp
#include <bits/stdc++.h>
#define MVNum 10000
using namespace std;

string Relationship[] = {"有功效","有食谱","有推荐食材","有证机概要"};
typedef struct ArcNode {
	int adjvex;                     // 该边所指向顶点的位置
	int relationship;               // 表示边的类型，即关系的类型，对应为数组下标 
	struct ArcNode* nextarc;        // 下一条边
} ArcNode;                          // 边结点

string Entity[]= {"食材","疾病","功效","食谱","证机概要"};
typedef struct VNode {
	int entity;                     // 表示顶点的类型，即实体的类型，对应为数组下标
	string info;                    // 表示顶点的内容，即实体的内容
	ArcNode* firstarc;              // 指向第一条依附该顶点的边的指针
} VNode, AdjList[MVNum];

typedef struct {
	AdjList vertices;               // 邻接表
	int vexnum, arcnum;             // 图的当前顶点数和边数
} ALGraph;

int LocateVex(ALGraph& G, string str) {
// 返回str在AdjList中的位置
    for(int i = 0; i < G.vexnum; i++){
        if(G.vertices[i].info == str){
            return i;
        }
    }
    return -1;
}

int LocateEntity(string str) {
// 返回str在Entity数组中的位置
    for(int i = 0; i < 5; i++){
        if(str == Entity[i]){
            return i;
        }
    }
    return -1;
}

int LocateRelationship(string str) {
// 返回str在Relationship数组中的位置
    for(int i = 0; i < 4; i++){
        if(str == Relationship[i]){
            return i;
        }
    }
    return -1;
}

void InitALGraph(ALGraph& G) {
// 初始化邻接表
    G.vexnum = G.arcnum = 0;
}

void CreateAdjList(ALGraph& G, string filename) {
// 从filename中按顺序读取实体存入邻接表
    ifstream ifs(filename);
    if(!ifs.is_open()) return;

    string info, entity;
    while(ifs >> info >> entity){
        auto &node = G.vertices[G.vexnum];
        node.info = info;
        node.entity = LocateEntity(entity);
        node.firstarc = nullptr;
        G.vexnum++;
    }
}

void AddArc(ALGraph& G, const string& u, const string& relationship, const string& v){
    int locU = LocateVex(G, u), locV = LocateVex(G, v);
    int reLoc = LocateRelationship(relationship);
    ArcNode *arc = new ArcNode;
    arc -> adjvex = locV;
    arc -> relationship = reLoc;
    arc -> nextarc = G.vertices[locU].firstarc;
    G.vertices[locU].firstarc = arc;
    G.arcnum++;
}

void CreateUDG(ALGraph& G, string filename) {
// 从filename中按顺序三元组存入邻接表
    ifstream ifs(filename);
    if(!ifs.is_open()) return;

    string u, relationship, v;
    while(ifs >> u >> relationship >> v){
        AddArc(G, u, relationship, v);
        AddArc(G, v, relationship, u);
    }
}
```



## 第22关：基于路径推理的知识图谱多跳问答

### 代码

```cpp
#include <bits/stdc++.h>
#define MVNum 10000
using namespace std;

string Relationship[] = {"有功效","有食谱","有推荐食材","有证机概要"};
typedef struct ArcNode {
	int adjvex;                     // 该边所指向顶点的位置
	int relationship;               // 表示边的类型，即关系的类型，对应为数组下标 
	struct ArcNode* nextarc;        // 下一条边
} ArcNode;                          // 边结点

string Entity[]= {"食材","疾病","功效","食谱","证机概要"};
typedef struct VNode {
	int entity;                     // 表示顶点的类型，即实体的类型，对应为数组下标
	string info;                    // 表示顶点的内容，即实体的内容
	ArcNode* firstarc;              // 指向第一条依附该顶点的边的指针
} VNode, AdjList[MVNum];

typedef struct {
	AdjList vertices;               // 邻接表
	int vexnum, arcnum;             // 图的当前顶点数和边数
} ALGraph;

int LocateVex(ALGraph& G, string str) {
// 返回str在AdjList中的位置
    for(int i = 0; i < G.vexnum; i++){
        if(G.vertices[i].info == str){
            return i;
        }
    }
    return -1;
}

int LocateEntity(string str) {
// 返回str在Entity数组中的位置
    for(int i = 0; i < 5; i++){
        if(str == Entity[i]){
            return i;
        }
    }
    return -1;
}

int LocateRelationship(string str) {
// 返回str在Relationship数组中的位置
    for(int i = 0; i < 4; i++){
        if(str == Relationship[i]){
            return i;
        }
    }
    return -1;
}

void InitALGraph(ALGraph& G) {
// 初始化邻接表
    G.vexnum = G.arcnum = 0;
}

void CreateAdjList(ALGraph& G, string filename) {
// 从filename中按顺序读取实体存入邻接表
    ifstream ifs(filename);
    if(!ifs.is_open()) return;

    string info, entity;
    while(ifs >> info >> entity){
        auto &node = G.vertices[G.vexnum];
        node.info = info;
        node.entity = LocateEntity(entity);
        node.firstarc = nullptr;
        G.vexnum++;
    }
}

void AddArc(ALGraph& G, const string& u, const string& relationship, const string& v){
    int locU = LocateVex(G, u), locV = LocateVex(G, v);
    int reLoc = LocateRelationship(relationship);
    ArcNode *arc = new ArcNode;
    arc -> adjvex = locV;
    arc -> relationship = reLoc;
    arc -> nextarc = G.vertices[locU].firstarc;
    G.vertices[locU].firstarc = arc;
    G.arcnum++;
}

void CreateUDG(ALGraph& G, string filename) {
// 从filename中按顺序三元组存入邻接表
    ifstream ifs(filename);
    if(!ifs.is_open()) return;

    string u, relationship, v;
    while(ifs >> u >> relationship >> v){
        AddArc(G, u, relationship, v);
        AddArc(G, v, relationship, u);
    }
}

void DFS(ALGraph& G, int i, bool visited[], string path, int depth) {
// 深度优先搜索多跳问答路径，i为输入的证机概要在AdjList中的下标，path为问答路径
// 函数可增加额外的参数
    visited[i] = true;
    bool isTail = 1;
    if(depth <= 3){
        for(auto parc = G.vertices[i].firstarc; parc; parc = parc -> nextarc){
            if(parc -> relationship == 4 - depth){
                isTail = 0;
                DFS(G, parc -> adjvex, visited, path + "->" + G.vertices[parc -> adjvex].info, depth + 1);
            }
        }
    }
    if(depth == 4 || isTail){
        cout << path << endl;
        visited[i] = 0;
        return;
    }
}

void QuestionAnswering(ALGraph& G, string symptom) {
// 调用DFS函数，遍历图G，输出问答序列，symptom为证机概要
    bool *visited = new bool[MVNum];
    memset(visited, 0, MVNum);
    DFS(G, LocateVex(G, symptom), visited, symptom, 1);
    delete[] visited;
}
```



## 第23关：基于编辑距离的食材功效矩阵构建

### 代码

```cpp
#include <bits/stdc++.h>
#define MVNum 10000
using namespace std;
#define INF 998244353

string Relationship[] = {"有功效","有食谱","有推荐食材","有证机概要"};
typedef struct ArcNode {
	int adjvex;                     // 该边所指向顶点的位置
	int relationship;               // 表示边的类型，即关系的类型，对应为数组下标 
	struct ArcNode* nextarc;        // 下一条边
} ArcNode;                          // 边结点

string Entity[]= {"食材","疾病","功效","食谱","证机概要"};
typedef struct VNode {
	int entity;                     // 表示顶点的类型，即实体的类型，对应为数组下标
	string info;                    // 表示顶点的内容，即实体的内容
	ArcNode* firstarc;              // 指向第一条依附该顶点的边的指针
} VNode, AdjList[MVNum];

typedef struct {
	AdjList vertices;               // 邻接表
	int vexnum, arcnum;             // 图的当前顶点数和边数
} ALGraph;

typedef struct {
	int vexs[100];                  // 顶点表
	double arcs[100][100];          // 邻接矩阵
	int vexnum, arcnum;             // 图的当前顶点数和边数
} AMGraph;

int LocateVex(ALGraph& G, string str) {
// 返回str在AdjList中的位置
    for(int i = 0; i < G.vexnum; i++){
        if(G.vertices[i].info == str){
            return i;
        }
    }
    return -1;
}

int LocateEntity(string str) {
// 返回str在Entity数组中的位置
    for(int i = 0; i < 5; i++){
        if(str == Entity[i]){
            return i;
        }
    }
    return -1;
}

int LocateRelationship(string str) {
// 返回str在Relationship数组中的位置
    for(int i = 0; i < 4; i++){
        if(str == Relationship[i]){
            return i;
        }
    }
    return -1;
}

void InitALGraph(ALGraph& G) {
// 初始化邻接表
    G.vexnum = G.arcnum = 0;
}

void CreateAdjList(ALGraph& G, string filename) {
// 从filename中按顺序读取实体存入邻接表
    ifstream ifs(filename);
    if(!ifs.is_open()) return;

    string info, entity;
    while(ifs >> info >> entity){
        auto &node = G.vertices[G.vexnum];
        node.info = info;
        node.entity = LocateEntity(entity);
        node.firstarc = nullptr;
        G.vexnum++;
    }
}

void AddArc(ALGraph& G, const string& u, const string& relationship, const string& v){
    int locU = LocateVex(G, u), locV = LocateVex(G, v);
    int reLoc = LocateRelationship(relationship);
    ArcNode *arc = new ArcNode;
    arc -> adjvex = locV;
    arc -> relationship = reLoc;
    arc -> nextarc = G.vertices[locU].firstarc;
    G.vertices[locU].firstarc = arc;
    G.arcnum++;
}

void CreateUDG(ALGraph& G, string filename) {
// 从filename中按顺序三元组存入邻接表
    ifstream ifs(filename);
    if(!ifs.is_open()) return;

    string u, relationship, v;
    while(ifs >> u >> relationship >> v){
        AddArc(G, u, relationship, v);
        AddArc(G, v, relationship, u);
    }
}

int LevenshteinDistance(string s1, string s2) {
// 定义一个函数，计算两个字符串的莱文斯坦距离
    int m = s1.length();            
    int n = s2.length();
    vector<vector<int>> dp(m + 1, vector<int>(n + 1));
    for (int i = 0; i <= m; i++) {
        dp[i][0] = i;
    }
    for (int j = 0; j <= n; j++) {
        dp[0][j] = j;
    }
    for (int i = 1; i <= m; i++) {
        for (int j = 1; j <= n; j++) {
            if (s1[i - 1] == s2[j - 1]) {
                dp[i][j] = dp[i - 1][j - 1];
            } else {
                dp[i][j] = min(dp[i - 1][j], min(dp[i][j - 1], dp[i - 1][j - 1])) + 1;
            }
        }
    }
    return dp[m][n];
}

double TextSimilarity(string s1, string s2) {
// 定义一个函数，计算两个字符串的文本相似度，文本相似度 = 1 - 莱文斯坦距离 / 最大字符串长度
    int dist = LevenshteinDistance(s1, s2);
    int max_len = max(s1.length(), s2.length());
    double s = 1.0 - (double)dist / max_len;
    return s;
}

void GetInfo(ALGraph& G, int i, string& s){
    for(ArcNode *arc = G.vertices[i].firstarc; arc; arc = arc -> nextarc){
        // if(arc -> relationship == 0){
        if(G.vertices[arc -> adjvex].entity == 2){
            s += G.vertices[arc -> adjvex].info;
            s += "#";
        }
    }
    if(s.size()) s.pop_back();
}

void InitAMGraph(AMGraph& GM){
    GM.vexnum = 0;
    GM.arcnum = 0;
}

void CreateAMG(AMGraph& GM, ALGraph& G) {
// 调用编辑距离算法计算相似度，构建食材之间的邻接矩阵
    for(int i = 0; i < G.vexnum; i++){
        if(G.vertices[i].entity == 0){
            GM.vexs[GM.vexnum++] = i;
            if(GM.vexnum == 100) break;
        }
    }

    for(int i = 0; i < GM.vexnum; i++){
        for(int j = 0; j < GM.vexnum; j++){
            string s1, s2;
            GetInfo(G, GM.vexs[i], s1);
            GetInfo(G, GM.vexs[j], s2);
            GM.arcs[i][j] = 1 - TextSimilarity(s1, s2);
            GM.arcnum++;
        }
    }
}
```



## 第24关：基于Dijkstra算法的食材推荐

### 代码

```cpp
#include <bits/stdc++.h>
#define MVNum 10000
using namespace std;
#define INF 998244353

string Relationship[] = {"有功效","有食谱","有推荐食材","有证机概要"};
typedef struct ArcNode {
	int adjvex;                     // 该边所指向顶点的位置
	int relationship;               // 表示边的类型，即关系的类型，对应为数组下标 
	struct ArcNode* nextarc;        // 下一条边
} ArcNode;                          // 边结点

string Entity[]= {"食材","疾病","功效","食谱","证机概要"};
typedef struct VNode {
	int entity;                     // 表示顶点的类型，即实体的类型，对应为数组下标
	string info;                    // 表示顶点的内容，即实体的内容
	ArcNode* firstarc;              // 指向第一条依附该顶点的边的指针
} VNode, AdjList[MVNum];

typedef struct {
	AdjList vertices;               // 邻接表
	int vexnum, arcnum;             // 图的当前顶点数和边数
} ALGraph;

typedef struct {
	int vexs[100];                  // 顶点表
	double arcs[100][100];          // 邻接矩阵
	int vexnum, arcnum;             // 图的当前顶点数和边数
} AMGraph;

int LocateVex(ALGraph& G, string str) {
// 返回str在AdjList中的位置
    for(int i = 0; i < G.vexnum; i++){
        if(G.vertices[i].info == str){
            return i;
        }
    }
    return -1;
}

int LocateEntity(string str) {
// 返回str在Entity数组中的位置
    for(int i = 0; i < 5; i++){
        if(str == Entity[i]){
            return i;
        }
    }
    return -1;
}

int LocateRelationship(string str) {
// 返回str在Relationship数组中的位置
    for(int i = 0; i < 4; i++){
        if(str == Relationship[i]){
            return i;
        }
    }
    return -1;
}

void InitALGraph(ALGraph& G) {
// 初始化邻接表
    G.vexnum = G.arcnum = 0;
}

void CreateAdjList(ALGraph& G, string filename) {
// 从filename中按顺序读取实体存入邻接表
    ifstream ifs(filename);
    if(!ifs.is_open()) return;

    string info, entity;
    while(ifs >> info >> entity){
        auto &node = G.vertices[G.vexnum];
        node.info = info;
        node.entity = LocateEntity(entity);
        node.firstarc = nullptr;
        G.vexnum++;
    }
}

void AddArc(ALGraph& G, const string& u, const string& relationship, const string& v){
    int locU = LocateVex(G, u), locV = LocateVex(G, v);
    int reLoc = LocateRelationship(relationship);
    ArcNode *arc = new ArcNode;
    arc -> adjvex = locV;
    arc -> relationship = reLoc;
    arc -> nextarc = G.vertices[locU].firstarc;
    G.vertices[locU].firstarc = arc;
    G.arcnum++;
}

void CreateUDG(ALGraph& G, string filename) {
// 从filename中按顺序三元组存入邻接表
    ifstream ifs(filename);
    if(!ifs.is_open()) return;

    string u, relationship, v;
    while(ifs >> u >> relationship >> v){
        AddArc(G, u, relationship, v);
        AddArc(G, v, relationship, u);
    }
}

int LevenshteinDistance(string s1, string s2) {
// 定义一个函数，计算两个字符串的莱文斯坦距离
    int m = s1.length();            
    int n = s2.length();
    vector<vector<int>> dp(m + 1, vector<int>(n + 1));
    for (int i = 0; i <= m; i++) {
        dp[i][0] = i;
    }
    for (int j = 0; j <= n; j++) {
        dp[0][j] = j;
    }
    for (int i = 1; i <= m; i++) {
        for (int j = 1; j <= n; j++) {
            if (s1[i - 1] == s2[j - 1]) {
                dp[i][j] = dp[i - 1][j - 1];
            } else {
                dp[i][j] = min(dp[i - 1][j], min(dp[i][j - 1], dp[i - 1][j - 1])) + 1;
            }
        }
    }
    return dp[m][n];
}

double TextSimilarity(string s1, string s2) {
// 定义一个函数，计算两个字符串的文本相似度，文本相似度 = 1 - 莱文斯坦距离 / 最大字符串长度
    int dist = LevenshteinDistance(s1, s2);
    int max_len = max(s1.length(), s2.length());
    double s = 1.0 - (double)dist / max_len;
    return s;
}

void GetInfo(ALGraph& G, int i, string& s){
    for(ArcNode *arc = G.vertices[i].firstarc; arc; arc = arc -> nextarc){
        // if(arc -> relationship == 0){
        if(G.vertices[arc -> adjvex].entity == 2){
            s += G.vertices[arc -> adjvex].info;
            s += "#";
        }
    }
    if(s.size()) s.pop_back();
}

void InitAMGraph(AMGraph& GM){
    GM.vexnum = 0;
    GM.arcnum = 0;
}

void CreateAMG(AMGraph& GM, ALGraph& G) {
// 调用编辑距离算法计算相似度，构建食材之间的邻接矩阵
    for(int i = 0; i < G.vexnum; i++){
        if(G.vertices[i].entity == 0){
            GM.vexs[GM.vexnum++] = i;
            if(GM.vexnum == 100) break;
        }
    }

    for(int i = 0; i < GM.vexnum; i++){
        for(int j = 0; j < GM.vexnum; j++){
            string s1, s2;
            GetInfo(G, GM.vexs[i], s1);
            GetInfo(G, GM.vexs[j], s2);
            GM.arcs[i][j] = 1 - TextSimilarity(s1, s2);
            GM.arcnum++;
        }
    }
}

void ShortestPathDIJ(AMGraph& G, bool S[], double D[], int v0) {
// 使用迪杰斯特拉算法求最短路径，S表示是否已被确定最短路径长度，D表示最短路径长度，v0表示顶点下标
    for(int i = 0; i < G.vexnum; i++){
        D[i] = INF, S[0] = 0;
    }
    D[v0] = 0;
    for(int i = 0; i < G.vexnum - 1; i++){
        int t = -1;
        for(int j = 0; j < G.vexnum; j++){
            if(!S[j] && (t == -1 || D[j] < D[t])){
                t = j;
            }
        }
        for(int j = 0; j < G.vexnum; j++){
            D[j] = min(D[j], D[t] + G.arcs[t][j]);
        }
        S[t] = 1;
    }
}
```



## 第25关：基于Floyd算法的食材推荐

### 代码

```cpp
#include <bits/stdc++.h>
#define MVNum 10000
using namespace std;

string Relationship[] = {"有功效","有食谱","有推荐食材","有证机概要"};
typedef struct ArcNode {
	int adjvex;                     // 该边所指向顶点的位置
	int relationship;               // 表示边的类型，即关系的类型，对应为数组下标 
	struct ArcNode* nextarc;        // 下一条边
} ArcNode;                          // 边结点

string Entity[]= {"食材","疾病","功效","食谱","证机概要"};
typedef struct VNode {
	int entity;                     // 表示顶点的类型，即实体的类型，对应为数组下标
	string info;                    // 表示顶点的内容，即实体的内容
	ArcNode* firstarc;              // 指向第一条依附该顶点的边的指针
} VNode, AdjList[MVNum];

typedef struct {
	AdjList vertices;               // 邻接表
	int vexnum, arcnum;             // 图的当前顶点数和边数
} ALGraph;

typedef struct {
	int vexs[100];                  // 顶点表
	double arcs[100][100];          // 邻接矩阵
	int vexnum, arcnum;             // 图的当前顶点数和边数
} AMGraph;

int LocateVex(ALGraph& G, string str) {
// 返回str在AdjList中的位置
    for(int i = 0; i < G.vexnum; i++){
        if(G.vertices[i].info == str){
            return i;
        }
    }
    return -1;
}

int LocateEntity(string str) {
// 返回str在Entity数组中的位置
    for(int i = 0; i < 5; i++){
        if(str == Entity[i]){
            return i;
        }
    }
    return -1;
}

int LocateRelationship(string str) {
// 返回str在Relationship数组中的位置
    for(int i = 0; i < 4; i++){
        if(str == Relationship[i]){
            return i;
        }
    }
    return -1;
}

void InitALGraph(ALGraph& G) {
// 初始化邻接表
    G.vexnum = G.arcnum = 0;
}

void CreateAdjList(ALGraph& G, string filename) {
// 从filename中按顺序读取实体存入邻接表
    ifstream ifs(filename);
    if(!ifs.is_open()) return;

    string info, entity;
    while(ifs >> info >> entity){
        auto &node = G.vertices[G.vexnum];
        node.info = info;
        node.entity = LocateEntity(entity);
        node.firstarc = nullptr;
        G.vexnum++;
    }
}

void AddArc(ALGraph& G, const string& u, const string& relationship, const string& v){
    int locU = LocateVex(G, u), locV = LocateVex(G, v);
    int reLoc = LocateRelationship(relationship);
    ArcNode *arc = new ArcNode;
    arc -> adjvex = locV;
    arc -> relationship = reLoc;
    arc -> nextarc = G.vertices[locU].firstarc;
    G.vertices[locU].firstarc = arc;
    G.arcnum++;
}

void CreateUDG(ALGraph& G, string filename) {
// 从filename中按顺序三元组存入邻接表
    ifstream ifs(filename);
    if(!ifs.is_open()) return;

    string u, relationship, v;
    while(ifs >> u >> relationship >> v){
        AddArc(G, u, relationship, v);
        AddArc(G, v, relationship, u);
    }
}

int LevenshteinDistance(string s1, string s2) {
// 定义一个函数，计算两个字符串的莱文斯坦距离
    int m = s1.length();            
    int n = s2.length();
    vector<vector<int>> dp(m + 1, vector<int>(n + 1));
    for (int i = 0; i <= m; i++) {
        dp[i][0] = i;
    }
    for (int j = 0; j <= n; j++) {
        dp[0][j] = j;
    }
    for (int i = 1; i <= m; i++) {
        for (int j = 1; j <= n; j++) {
            if (s1[i - 1] == s2[j - 1]) {
                dp[i][j] = dp[i - 1][j - 1];
            } else {
                dp[i][j] = min(dp[i - 1][j], min(dp[i][j - 1], dp[i - 1][j - 1])) + 1;
            }
        }
    }
    return dp[m][n];
}

double TextSimilarity(string s1, string s2) {
// 定义一个函数，计算两个字符串的文本相似度，文本相似度 = 1 - 莱文斯坦距离 / 最大字符串长度
    int dist = LevenshteinDistance(s1, s2);
    int max_len = max(s1.length(), s2.length());
    double s = 1.0 - (double)dist / max_len;
    return s;
}

void GetInfo(ALGraph& G, int i, string& s){
    for(ArcNode *arc = G.vertices[i].firstarc; arc; arc = arc -> nextarc){
        // if(arc -> relationship == 0){
        if(G.vertices[arc -> adjvex].entity == 2){
            s += G.vertices[arc -> adjvex].info;
            s += "#";
        }
    }
    if(s.size()) s.pop_back();
}

void InitAMGraph(AMGraph& GM){
    GM.vexnum = 0;
    GM.arcnum = 0;
}

void CreateAMG(AMGraph& GM, ALGraph& G) {
// 调用编辑距离算法计算相似度，构建食材之间的邻接矩阵
    for(int i = 0; i < G.vexnum; i++){
        if(G.vertices[i].entity == 0){
            GM.vexs[GM.vexnum++] = i;
            if(GM.vexnum == 100) break;
        }
    }

    for(int i = 0; i < GM.vexnum; i++){
        for(int j = 0; j < GM.vexnum; j++){
            string s1, s2;
            GetInfo(G, GM.vexs[i], s1);
            GetInfo(G, GM.vexs[j], s2);
            GM.arcs[i][j] = 1 - TextSimilarity(s1, s2);
            GM.arcnum++;
        }
    }
}


void ShortestPathFloyd(AMGraph& G, double D[][100]) {
// 使用弗洛伊德算法求最短路径，D表示最短路径长度
    for(int i = 0; i < G.vexnum; i++){
        for(int j = 0; j < G.vexnum; j++){
            D[i][j] = G.arcs[i][j];
        }
    }
    for(int k = 0; k < G.vexnum; k++){
        for(int i = 0; i < G.vexnum; i++){
            for(int j = 0; j < G.vexnum; j++){
                D[i][j] = min(D[i][j], D[i][k] + D[k][j]);
            }
        }
    }
}
```

