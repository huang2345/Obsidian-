# RandomAccessFile
类
### 构造器
#### RandomAccessFile(String file,String mode)
#### RandomAccessFile(File file,String mode)
`mode`表示模式：
```
mode:r只读
mode:w只写
//元数据是数据的数据，指示了一些东西
mode:rws读写，会更新元数据和文件
mode:rwd读写，只更新文件
```
### 实例方法
#### long getFilePointer
返回文件指针的当前位置
#### void seek(long pos)
将文件指针设置到距文件开头`pos`个字节处。
#### long length()
返回文件的大小(字节单位)