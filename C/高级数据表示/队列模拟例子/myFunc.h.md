```
#pragma once

#include <stdio.h>
#include <stdlib.h>

typedef struct message
{
	int addTime;
	int processTime;
} Message;
//用来給main()半自动创建Message
//创建Message
inline Message MessageCreate(int addTime, int processTime)
{
	Message message{};
	message.addTime = addTime;
	message.processTime = processTime;

	return message;
}
typedef struct node
{
	Message m;
	node* p;
} Node;
typedef struct queue
{
	Node* head;
	Node* end;
	int queueCount;
} Queue;

//接口函数
//初始化
void InitiallzationQueue(Queue* queue);
//检查队列有没有到达设置的上限，或者到达栈的大小
bool QueueIsFull(const Queue* queue, int size);
//检查队列是否为空
bool QueueIsEmpty(const Queue* queue);
//返回节点数量
int QueueCount(const Queue* queue);
//增
bool QueueAdd(Message m, Queue* queue);
//删
bool QueueDel(Queue* queue);
//释放队列所有节点
void QueueFree(Queue* queue);
//弹出节点信息
Message QueueEject(Queue* queue);
```