### 构造器
#### FileOutputStream(String name,?boolean append)
#### FileOutputStream(File file,?boolean append)
创建一个新的文件输出流。如果指定了`append`参数并且为`true`，那么写入的数据将被添加到文件尾；否则，会删除具有相同名字的文件
### 实例方法
#### FileChannel getChannel()
返回用于访问这个输出流的通道。