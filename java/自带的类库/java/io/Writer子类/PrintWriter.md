### 构造器
#### PrintWriter(Writer out)
创建一个向指定写出器写出的`PrintWriter`
#### PrintWriter(String filename,String encoding)
#### PrintWriter(File file,String encoding)
创建一个使用给定编码格式向指定文件写出的`PrintWriter`
>`StandardCharasets.UTF_8`

### 实例方法
#### boolean checkError()
如果产生格式化或输出错误，返回`true`
#### void print(Object obj)
通过`obj`的`toString()`返回的字符串来打印对象。
#### void print(String s)
打印一个包含Unicode码元的字符串
##### void print(int i)
##### void print(long l)
##### void print(float f)
##### void print(double d)
##### void print(boolean b)
用文本格式打印给定值
#### void printf(String format,Object... args)
按照格式化字符指定的方式打印。
#### void println(String s)
打印一个字符串，行尾添加一个行终止符。如果流出于自动冲刷模式，冲刷这个流。
#### void print(char\[] s)
打印char数组中的所有Unicode码元
#### void print(char c)
打印单个码元。
