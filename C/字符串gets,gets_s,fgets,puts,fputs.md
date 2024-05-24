#include "stdio.h"
int main()
{
	//字符串输入函数
	//gets_s(被输入的字符串，字符串大小)
	//fgets(被输入的字符串，限制输入大小，获取输入的流(例如stdin))
	限制输入包括\0

	//字符串输出函数
	//puts(要输出的字符串地址)	注意！puts输出时直到遇到空字符\0时才停止,char[]最后一个元素为'\0'的才是字符串
	//fputs(字符串地址，要输出的文件或流(例如stdout)),fputs不会自动添加'\n'
	return 0;
}
//读取整行输入并用\0替换\n，或者丢弃多余字符
char* s_gets(char* str, int n)
{
	int i = 0;
	char* Fstr = fgets(str, n, stdin);
	if (Fstr != NULL)
	{
		//遍历字符串str找到其中的\n或者\0字符
		while (str[i] != '\n' && str[i] != '\0')
			i++;
		//将\n替换成\0
		if (str[i] == '\n')
		{
			str[i] = '\0';
		}
		else
		{
			//没有换行符的情况丢弃多余字符
			while (getchar() != '\n')
				;
		}
		str = Fstr;
		return Fstr;
	}
}
