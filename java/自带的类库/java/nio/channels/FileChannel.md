### 静态方法
#### FileChannel open(Path path,OpenOption... options)
打开指定路径的文件通道。默认情况下，通道用于读取。参数`options`是`StandardOpenOption`枚举中的`WRITE`、`APPEND`、`TRUNCATE_EXISTING`、`CREATE`值
### 实例方法
#### MappedByteBuffer map(FileChannel.MapMode mode,long position,long size)
将文件的一个区域映射到内存中。
#### FileLock lock()
##### FileLock lock(long position,long size,boolean shared)
获取文件的独占锁。该方法将阻塞直至获得锁；
获取文件部分区域的锁，`shared`为`true`时为共享锁
#### FileLock tryLock()
##### FileLock tryLock(long position,long size,boolean shared)
获取文件的独占锁，在无法获得锁的情况下返回`null`
获取文件部分区域的锁，`shared`为`true`时为共享锁
