### 构造器
#### ZipInputStream(InputStream in)
创建
### 实例方法
#### ZipEntry getNextEntry()
返回表示下一项的`ZipEntry`对象，在没有更多项时返回`null`
#### void closeEntry()
关闭当前打开的项。下次调用`getNextEntry`会读取下一个项