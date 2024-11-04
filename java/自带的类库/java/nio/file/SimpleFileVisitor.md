# SimpleFileVisitor\<T>
### 静态方法
#### FileVisitResult visitFile(T path,BasicFileAttributes attrs)
在访问文件或目录时调用。默认实现是不做任何操作继续访问。
#### FileVisitResult preVisitDirectory(T path,BasicFileAttributes attrs)
#### FileVisitResult postVisitDirectory(T path,IOException e)
在访问目录前和访问目录结束时调用，默认实现是不做任何操作继续访问。
#### FileVisitResult visitFileFailed(T path,IOException exc)
如果在试图获取指定文件的信息时抛出异常，则该方法被调用。默认实现是重新抛出异常，这会导致访问操作以异常而终止
