#include "stdio.h"
int main()
{
	double n = 10;
	int k = 3;
	double power(double, int, double);
	double num = power(n, k, 0);
	printf("%lf		%lf", n, num);
	return 0;
}
//计算double类型n的k次幂,value初始值必须为0
double power(double n, int k, double value)
{
	//0的任何次幂都为0
	if (n == 0)
	{
		return 0;
	}
	//当k>1
	if (k > 1)
	{
		//使用value在递归中传递值
		if (value == 0)
		{
			value = n * n;
			k--;
			power(n, k, value);
		}
		else if (value != 0)
		{
			value *= n;
			k--;
			power(n, k, value);
		}
	}
	//k<0
	else if (k < 0)
	{
		if (value == 0)
		{
			//求负次幂时，先得到n的倒数，再将n作为新的（n）值
			n = 1 / n;
			value = n;
			//求新n值的-k次幂即可求得负次幂
			power(n, -k, value);
		}
		else if (value != 0)
		{
			value *= n;
			k++;
			power(n, k, value);
		}
	}

	if (k == 0 || k == 1 && value != 0)
	{
		return value;
	}
	//任何数的零次幂为1
	else if (k == 0)
	{
		return 1;
	}
}