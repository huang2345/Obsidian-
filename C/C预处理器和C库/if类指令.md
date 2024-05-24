```
用上述指令可以告诉编译器根据编译时的条件执行或忽略代码块

#ifdef A
	#include B
	...
#else
	#include C
	...
#endif
```

```
ifndef与ifdef相反，他判断的是：是否未定义
因此用他来防止多次包含会比ifdef好用一些
```

```
if和elif

if后跟整形常量表达式，这两个与if差不多
```