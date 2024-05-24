```
#line重置__LINE__和__FILE__宏报告的行号和文件名
#line 10 "test.c"
```

```
#error让预处理器发送错误消息，可能的话，编译会中断
可以用if判断是否用#error处理错误
```

```
#pragma将编译器指令放在源代码

C99提供_Pragma预处理器运算符，该运算符把字符串转换成普通的编译指示
例如：
	_Pragma("c9x on")
	等于
	#pragma c9x on
```