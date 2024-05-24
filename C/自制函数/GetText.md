获取文件中的文本

```
//与fgets相比，此函数读取到\n不会返回值，只有读取到EOF或到达MaxInputCount才会退出
//trendsString：动态字符串		MaxInputCount：能获取字符的最大数量
char* GetText(FILE* file,char* trendsString,int MaxInputCount)
{
	//判断file是否为NULL
	if (!file)
	{
		fprintf(stderr, "file==NULL");
	}
	else
	{
		//用\0冲刷动态字符串
		for (int i = 0; i < MaxInputCount; i++)
		{
			trendsString[i] = '\0';
		}
		char ch;
		//用num控制字符串指针移动
		int num = 0;
		rewind(file);
		while ((ch = getc(file)) != EOF)
		{
			//当num到达最大字符数-1时，退出循环
			if (num >= MaxInputCount - 1)
			{
				break;
			}
			*(trendsString+num) = ch;
			num++;
		}
		//feof正常返回值为非0，检查是否正常到达文件结尾
		//强制为最后一个字符赋值\0
		if (feof(file))
		{
			trendsString[MaxInputCount] = '\0';
			return trendsString;
		}
		else if (num >= MaxInputCount)
		{
			trendsString[MaxInputCount] = '\0';
			return trendsString;
		}
		else
		{
			fprintf(stderr, "GetText feof错误");
			exit(EXIT_FAILURE);
		}
	}
}
```