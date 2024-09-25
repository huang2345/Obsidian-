### 实例方法
#### int intValue()
拆包
### 静态方法
#### String toString(int i)
#### String toString(int i,int radix)
返回数值i的radix进制字符串表示，默认十进制
#### int parseInt(String s)
#### int parseInt(String s,int radix)
转换为一个整数，字符串必须表示一个数字
#### Integer valueOf(String s)
#### Integer valueOf(String s,int radix)
一个包装器版本的parseInt
#### int compare(double x,double y)
如果x<y返回负整数；相等返回0；x>y返回正整数