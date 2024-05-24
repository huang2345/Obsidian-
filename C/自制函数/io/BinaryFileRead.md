文件地址

以二进制读取文件，并返回文件信息
```
//Binary:二进制
struct FileMessage* BinaryFileRead(char* fileName)
{
	FILE* file;

	static struct FileMessage fileMessage {};
	FileMessage* message = &fileMessage;
	//打开文件
	if (fopen_s(&file, fileName, "rb") != 0)
	{
		fprintf(stderr, "%s fopen_s打开失败！", fileName);
		exit(EXIT_FAILURE);
	}
	setvbuf(file, NULL, _IOLBF, 2048);
	//获取文件大小
	if (fseek(file, 0L, SEEK_END) != 0)
	{
		fprintf(stderr, "%s fseek失败！", fileName);
		exit(EXIT_FAILURE);
	}
	//部分文件读取疑似错误
	else if ((message->fileSize = (int)ftell(file)) == -1)
	{
		fprintf(stderr, "%s ftell失败！", fileName);
		exit(EXIT_FAILURE);
	}
	//还原文件指针位置
	rewind(file);
	message->fileArray = malloc(message->fileSize);

	if (message->fileArray != NULL)
	{
		if (fread((int*)message->fileArray, sizeof(int), message->fileSize / sizeof(int), file) < message->fileSize / sizeof(int))
		{
			fprintf(stderr, "%s fread错误", fileName);
			exit(EXIT_FAILURE);
		}
	}
	else
	{
		fprintf(stderr, "message->fileArrat为NULL");
		exit(EXIT_FAILURE);
	}
	return message;
}
```