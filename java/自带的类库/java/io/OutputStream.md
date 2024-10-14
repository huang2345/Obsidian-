# OutputStream
抽象类
### 抽象方法
#### void write(int n)
写入一个字节的数据
### 实例方法
#### void write(byte\[] b,?int off,?int len)
输出流中写入字节数组`b`中的数据。如果设置了`off`和`len`：指定了范围，`off`是起始索引，`len`是大小
#### void close()
冲刷并关闭输出流
#### void flush()
冲刷输出流。会将缓冲区中的数据发送到目的地
### 静态方法
#### OutputStream nullOutputStream()
返回一个会丢弃所有字节的输出流