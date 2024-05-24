```
#include "myFunc.h"
int main()
{
	Queue queue;
	InitiallzationQueue(&queue);

	int times = 1;
	Message messages[60];
	//由于对队列进行排序较为繁琐，所以选择先模拟出addTime再根据addTime排序以做到：队列以addTime大小顺序排序
	int addTimes[60];
	for (int i = 0; i < 60; i++)
	{
		addTimes[i] = rand() % 60 + 1;
	}
	for (int i = 0; i < 60; i++)
	{
		for (int j = i; j < 60; j++)
		{
			int temp = addTimes[j];
			if (addTimes[i] > addTimes[j])
			{
				addTimes[j] = addTimes[i];
				addTimes[i] = temp;
			}
		}
	}
	for (int i = 0; i < 60; i++)
	{
		//每一位需要多少接待时间
		int processTime = rand() % 3 + 1;
		messages[i] = MessageCreate(addTimes[i], processTime);
	}
	//模拟在60分钟内接待用户
	int user = 0;
	//模拟刚开始接待时接待前消耗的时间
	bool first = true;
	//模拟到上一次接待使用了多少时间
	int receptionTime = 0;
	while (times < 60)
	{
		//检查队列是否为空
		if (!QueueIsEmpty(&queue))
		{
			//模拟处理用户来了没有
			if(queue.head->m.addTime <= times)
			{
				if (first)
				{
					//模拟第一次接待用户时
					if (queue.head->m.addTime + queue.head->m.processTime == times)
					{
						QueueDel(&queue);
						user++;
						first = false;
						receptionTime += queue.head->m.addTime + queue.head->m.processTime;
					}
				}
				else
				{
					if (receptionTime + queue.head->m.processTime == times)
					{
						receptionTime += queue.head->m.processTime;
						QueueDel(&queue);
						user++;
					}
				}
			}
		}
		//遍历message数组以模拟用户随机加入
		for (int i = 0; i < 60; i++)
		{
			if (messages[i].addTime == times)
			{
				//如果达到排队上线
				if (QueueIsFull(&queue, 10))
				{
					fprintf(stderr, "队列已满\n");
				}
				else
				{
					QueueAdd(messages[i], &queue);
				}
			}
		}
		times++;
	}
	printf("已接待用户数量为：%d\n", user);
	puts("全部处理成功");
}
```