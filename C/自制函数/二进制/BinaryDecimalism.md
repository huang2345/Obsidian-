```
Decimalism：十进制
//十进制字符串转int
int BinaryDecimalism(char* Array)
{
	int sum = 0;
	int k = 0;

	for (int i = strlen(Array) - 1; i >= 1; i--)
	{
		int j = Array[i] - '0';
		if (j)
		{
			sum += pow(2, k);
		}
		k++;
	}
	return sum;
}
```