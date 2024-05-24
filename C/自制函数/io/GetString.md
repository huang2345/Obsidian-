终止符

动态获取字符串
```
char* GetString(const char endChar)
{
	char* GetText(FILE*, char*, int);

	FILE* fileName;
	char ch;
	//打开文件
	if (fopen_s(&fileName, "stdbuf", "w+") != 0)
	{
		fprintf(stderr, "stdbuf fopen_s错误");
		exit(EXIT_FAILURE);
	}
	//将文件名写入stdbuf 中
	while ((ch = getchar()) != endChar)
	{
		putc(ch, fileName);
	}
	//fseek+ftell获取动态数组大小
	if (fseek(fileName, 0L, SEEK_END) == -1)
	{
		fprintf(stderr, "fseek错误");
		exit(EXIT_FAILURE);
	}
	//
	 int strSize = (int)ftell(fileName) + 1;
	//检查ftell是否正常，所读文件是否超过2GB
	if (strSize == -1)
	{
		fprintf(stderr, "ftell错误");
		exit(EXIT_FAILURE);
	}
	rewind(fileName);
	char* name = (char*)malloc(strSize);
	//fgets自动加\0
	if (name != NULL)
	{
		GetText(fileName, name, strSize);
	}
	fclose(fileName);
	return name;
}
```