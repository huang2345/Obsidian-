typedef可以为某一类型自定义名称，与#define有三处不同

	typedef创建的标识名只受限于类型，不同用于值
	typedef由编译器处理，#define由预处理器处理
	在一定范围内，比#define灵活

通常，typedef使用大写字母表示被定义的名称

typedef还能提高程序的可移植性，比如size_t,time_t

为某一类型自定义名称时，typedef更好用：
例如：
```
#define S char*
typedef char* A;

...

S a,b;
A c,d;

//用#define定义的名称只是直接替换
//所以S那一行实际上时 char *a,b
//这导致b其实是char
```
