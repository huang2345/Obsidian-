## 静态方法
#### Stream\<String> lines(Path path)
##### Stream\<String> lines(Path path,Charset cs)
产生一个流，其元素是指定文件中的行。默认字符集为UTF-8。
### 读写文件
#### byte\[] readAllBytes(Path path)
#### String readString(Path path,Charset charset)
#### List\<String> readAllLines(Path path,Charset charset)
读取文件
#### Path write(Path path,byte\[] contents,OpenOption... options)
##### Path write(Path path,String contents,Charset charset,OpenOption... options)
##### Path write(Path path,CharSequence contents,Charset cs,OpenOption... options)
##### Path write(Path path,Iterable\<? extends CharSequence> contents,OpenOption options)
将给定内容写入到文件中。将`options`设置为`StandardOpenOption.APPEND`可以从文件末尾添加。

### 创建文件或目录
#### Path createFile(Path path,FileAttribute\<?>... attrs)
创建文件
#### Path createDirectory(Path path,FileAttribute\<?>... attrs)
创建一个目录，父目录必须存在
#### Path createDirectories(Path path,FileAttribute\<?>... attrs)
将路径中的所有部分作为目录创建
#### Path createTempFile(String prefix,String suffix,FileAttribute\<?>... attrs)
##### Path createTempFile(Path parentDir,String prefix,String suffix,FileAttribute\<?>... attrs)
#### Path createTempDirectory(String prefix,FileAttribute\<?>... attrs)
##### Path createTempDirectory(Path parentDir,String prefix,FileAttribute\<?>... attrs)
在适合临时文件的位置，或者指定的父目录下创建临时文件或目录。`prefix`和`suffix`是可以为`null`的字符串
### 复制、移动和删除
#### Path copy(Path from,Path to,CopyOption... options)
#### Path move(Path from,Path to,CopyOption... options)
将`from`复制或移动到给定位置。如果目标存在将抛出`FileAlreadyExistsException`
#### long copy(InputStream from,Path to,CopyOption... options)
#### long copy(Path to,OutputStream from,CopyOption... options)
从输入流复制到文件中，或从文件复制到输出流中。返回复制的字节数。
#### void delete(Path path)
#### boolean deleteIfExists(Path path)
删除指定文件或空目录。`delete`方法在文件或目录不存在的情况下抛出异常，而`deleteIfExists`会返回`false`

### 其他
#### long mismatch(Path path1,Path path2)
返回两个文件中第一个不相同字节的位置
#### String probeContentType(Path path)
返回针对文件内容的MIME类型的最佳匹配，在无法确定时返回null。
#### long size(Path path)
获取字节单位的文件大小

#### InputStream newInputStream(Path path,OpenOption... options)
#### OutputStream newOutputStream(Path path,OpenOption... options)
#### BufferedReader newBufferedReader(Path path,Charset charset)
#### BufferedWriter newBufferedWriter(Path path,Charset charset,OpenOption... options)
打开文件，用于输入输出。