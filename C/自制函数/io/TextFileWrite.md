被输入文件地址，被输出字符串，打开文件模式

输出文件
```
void TextFileWrite(const char* fileName, char* string,const char* model)
{
	FILE* file;
	int size = (int)strlen(string);
	//打开文件
	if (fopen_s(&file, fileName, model) != 0)
	{
		fprintf(stderr, "%s fopen_s打开失败！", fileName);
		exit(EXIT_FAILURE);
	}
	if (string != NULL && fwrite(string, sizeof(char), size, file) == NULL)
	{
		fprintf(stderr, "%s fwrite失败！", fileName);
		exit(EXIT_FAILURE);
	}
	//关闭文件流
	fclose(file);
}
```