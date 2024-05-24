#include "stdio.h"

int main()
{
	const double ONE = 1.0;
	//Zeno的箭飞行问题，假设箭飞行number个序列，求第number个序列时的时间
	int number,double_2 = 1;
	double time = 0;
	printf("请输入X个序列：");
	scanf_s("%d", &number);
	for (int times = 1; times <= number; times++, double_2 *= 2)
	{
		time += ONE / double_2;
		printf("当前为:%d序列，箭飞行时长为:%.20lf\n", times, time);
	}
	return 0;
}
