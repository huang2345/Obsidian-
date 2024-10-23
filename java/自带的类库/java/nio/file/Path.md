### 静态方法
#### Path of(String first,String... more)
构造Path对象
### 实例方法
#### Path resolve(Path other)
##### Path resolve(String other)
连接当前路径和`other`；如果`other`是绝对路径，返回`other`
#### Path resolveSibling(Path other)
##### Path resolveSibling(String other)
连接当前路径的父路径与`other`；如果`other`是绝对路径，返回`other`
#### Path relativize(Path other)
将`other`简化为当前目录下的相对目录
#### Path normalize()
删除诸如`.`和`..`等冗余的路径元素
#### Path toAbsolutePath()
返回当前路径的绝对路径
#### Path getParent()
返回父路径，没有时返回null
#### Path getFileName()
返回路径中的最后一个。没有时返回null
#### Path getRoot()
返回根目录。没有时返回null
#### toFile()
从该路径中创建一个`File`对象
