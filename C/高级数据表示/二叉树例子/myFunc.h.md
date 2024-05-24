```
#pragma once

#include <stdio.h>
#include <stdlib.h>
#include <stdarg.h>


inline int Compare(const void* x, const void* y)
{
	const int* a = (const int*)x;
	const int* b = (const int*)y;

	if (*a > *b)
	{
		return 1;
	}
	else if(*a == *b)
	{
		return 0;
	}
	else
	{
		return -1;
	}
}

typedef struct message
{
	int value;
} Message;
//创建Message
inline Message MessageCreate(int value)
{
	Message message{};
	message.value = value;

	return message;
}
typedef struct trnode
{
	Message m;
	trnode* left;
	trnode* right;
} TrNode;
typedef struct tree
{
	TrNode* root;
	int Count;
} Tree;

//初始化
void InitiallzationTree(Tree* tree);
//检查队列有没有到达设置的上限，或者到达栈的大小
bool TreeIsFull(const Tree* tree, int size);
//检查队列是否为空
bool TreeIsEmpty(const Tree* tree);
//返回节点数量
int TreeCount(const Tree* tree);
//增
bool TreeAdd(Message m, Tree* tree);
//执行节点添加进树操作
bool DetermineRootNode(TrNode* node, TrNode* temp, TrNode* parent, Tree* tree);
//删
bool TreeDel(Message message,Tree* queue);
//遍历树
void DisplayTree(Tree* tree);
void DisplayTrNode(TrNode* node);
//清空树
////释放队列所有节点
//void TreeFree(Tree* queue);

```