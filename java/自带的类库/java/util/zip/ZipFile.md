### 构造器
#### ZipFile(String name)
#### ZipFile(File file)
创建一个ZipFile
### 实例方法
#### Enumeration entries()
返回一个`Enumeration`对象，他枚举了描述这个`ZipFile`中各个项的`ZipEntry`对象。
#### ZipEntry getEntry(String name)
返回指定名字的项，在没有对应项的时候返回`null`
#### InputStream getInputStream(ZipEntry ze)
返回这个项的`InputStream`
#### String getName()
返回这个ZIP文件的路径