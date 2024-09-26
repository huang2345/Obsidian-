#### if ... else if ... else
与其他语言一样
#### switch表达式
java中有四种形式，且java新增的`->`的case语句可以使用大括号
>Java核心技术卷1中将C中的switch表达式中的：如果case语句中没有break，将会直接运行下一个case中的代码，该书将这种能力称为==直通==
```java
switch(变量){
	case 0 -> ...
	case 1 -> ...
	default -> ...
}
```
>在Java中，可以直接使用switch表达式为变量选择值(java14中引入)，并且可以使用`yield`关键字返回值
>switch 表达式中使用枚举常量时，不需要为各个标签提供枚举名

