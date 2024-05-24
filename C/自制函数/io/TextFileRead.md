文件地址

获取文本内容
```
FileMessage * TextFileRead(char* fileName)
{
	char* GetText(FILE*, char*,int);

	static FileMessage fileMessage{};
	FileMessage* message = &fileMessage;
	FILE* file;
	//打开文件
	if (fopen_s(&file, fileName, "r") != 0)
	{
		fprintf(stderr, "%s fopen_s打开失败！", fileName);
		exit(EXIT_FAILURE);
	}
	//获取文件大小
	else if (fseek(file, 0L, SEEK_END) != 0)
	{
		fprintf(stderr, "%s fseek失败！", fileName);
		exit(EXIT_FAILURE);
	}
	//部分文件读取疑似错误
	else if ((message->fileSize = (int)ftell(file) + 1) == -1)
	{
		fprintf(stderr, "%s ftell失败！", fileName);
		exit(EXIT_FAILURE);
	}
	//还原文件指针位置
	rewind(file);
	//根据size创建动态数组
	(message->fileArray) = (char*)malloc(message->fileSize * sizeof(char));
	//问题：出现不正确字符，且每次运行时都略有差别
	//猜测：动态字符串创建时可能由于使用fseek和ftell获取的文件内容大小不准确导致多出一些未使用的内存，所以使用\0冲刷str
	for (int i = 0; i < message->fileSize; i++)
	{
		if(message->fileArray != NULL)
			((char*)(message->fileArray))[i] = '\0';
	}
	//防止str==NULL，检查malloc分配动态数组是否正常
	if (message->fileArray == NULL || GetText(file,(char*)(message->fileArray), message->fileSize) == NULL)
	{
		fprintf(stderr, "%s GetText失败！", fileName);
		exit(EXIT_FAILURE);
	}
	//关闭文件流
	fclose(file);
	return message;
}
```