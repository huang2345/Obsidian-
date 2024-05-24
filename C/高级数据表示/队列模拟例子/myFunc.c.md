```
#include "myFunc.h"

//增删改查

//初始化队列
void InitiallzationQueue(Queue* queue)
{
	queue->head = NULL;
	queue->end = NULL;
	queue->queueCount = 0;
}
//检查队列有没有到达设置的上限，或者到达栈的大小
bool QueueIsFull(const Queue* queue, int size)
{
	if (queue->queueCount >= size)
		return true;

	Queue* temp = (Queue*)malloc(sizeof(Queue));
	if (temp == NULL)
	{
		fprintf(stderr, "栈满");
		return true;
	}
	free(temp);
	return false;
}

//检查队列是否为空
bool QueueIsEmpty(const Queue* queue)
{
	if (queue->head == NULL)
		return true;
	return false;
}
//返回节点数量
int QueueCount(const Queue* queue)
{
	return queue->queueCount;
}
static void CopyToNode(Message m, Node* node)
{
	node->m = m;
}
static void CopyToMessage(Message* m, Node* node)
{
	*m = node->m;
}
bool QueueAdd(Message m, Queue* queue)
{
	//为节点分配空间
	Node* node = (Node*)malloc(sizeof(message) + sizeof(Node*));

	//检查分配空间是否成功
	if (!node)
	{
		fprintf(stderr, "栈满");
		return false;
	}
	//将形参输入的数据输出到节点中
	CopyToNode(m, node);
	//将下一个节点设置为NULL
	node->p = NULL;
	//判断头节点是否为空
	if (QueueIsEmpty(queue))
	{
		//将节点设置为头节点
		queue->head = node;
		//检查是否添加成功
		if (!QueueIsEmpty(queue))
		{
			queue->queueCount++;
			return true;
		}
		else
			return false;
	}
	else
	{
		//判断尾节点是否为空
		if (queue->end == NULL)
		{
			//将节点设置为尾节点
			queue->head->p = node;
			queue->end = node;
		}
		else
		{
			//设置尾节点的下一个节点
			queue->end->p = node;
			//重置尾节点
			queue->end = node;
		}
		queue->queueCount++;
		return true;
	}
}

bool QueueDel(Queue* queue)
{
	if (queue->head == NULL)
	{
		fprintf(stderr, "空对列");
		queue->end = NULL;
		return false;
	}
	else
	{
		//获取头节点的下一个节点
		Node* temp = queue->head->p;
		if (temp == NULL)
		{
			puts("队列已空");
			//return false;
		}
		//释放头节点
		free(queue->head);
		queue->queueCount--;
		//将下一个节点设置为头节点
		queue->head = temp;

		return true;
	}
}

//弹出节点信息
Message QueueEject(Queue* queue)
{
	if (queue->head == NULL)
	{
		fprintf(stderr, "队列已空");
		Message *m = NULL;
		return *m;
	}
	else
	{
		Message message{};
		CopyToMessage(&message, queue->head);
		//获取下一节点
		Node* temp = queue->head->p;
		if (temp == NULL)
		{
			fprintf(stderr, "队列已空");
		}
		free(queue->head);
		//队列节点数量减一
		queue->queueCount--;
		//重置头节点
		queue->head = temp;
		
		return message;
	}
}
//释放队列所有节点
void QueueFree(Queue* queue)
{
	while (!QueueIsEmpty(queue))
	{
		QueueDel(queue);
	}
}
```