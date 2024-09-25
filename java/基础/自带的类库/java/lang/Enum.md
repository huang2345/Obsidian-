### 静态方法
#### Enum valueOf(Class enumClass,String name)
返回给定类中指定名字的枚举常量。
#### String toString()
返回枚举常量名
#### int ordinal()
返回枚举常量在枚举类中声明的位置
#### int compareTo(T other)
比较枚举常量和other的位置，如果other在后返回一个负整数；如果this\=\=other，返回0；否则，返回一个正整数。