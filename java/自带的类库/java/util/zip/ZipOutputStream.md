### 构造器
#### ZipOutputStream(OutputStream out)
创建一个将压缩数据写出到指定输出流的ZipOutputStream
### 实例方法
#### void putNextEntry(ZipEntry ze)
将指定的`ZipEntry`中的信息写入到输出流中，这些数据通过输出流的`write`写入
#### void closeEntry()
关闭当前打开的项。下次调用`putNextEntry`写入下一项
#### void setLevel(int Level)
设置后续的`DEFLATED`项的默认压缩级别
#### void setMethod(int method)
设置用于这个`ZipOutputStream`的默认压缩方法