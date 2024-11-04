### 实例方法
#### byte get()
从当前位置获取一个字节，并将位置向后移动一个字节。
#### byte get(int index)
从指定索引获取一个字节。
#### ByteBuffer put(byte b)
向当前位置推入一个字节，并移动位置。返回对该缓冲区的引用
#### ByteBuffer put(int index,byte b)
向指定索引推入一个字节，并移动位置。返回对该缓冲区的引用
#### ByteBuffer get(byte\[] destination) throws BufferUnderflowException 
#### ByteBuffer get(byte\[] destination,int offset,int length) throws BufferUnderflowException 
将缓冲区中的字节填充到字节数组的某个区域中。如果缓冲区要读取的字节数与数组的指定区域不同，将不会读取任何字节并抛出`BufferUnderflowException`。

#### ByteBuffer put(byte\[] source) throws BufferUnderflowException
#### ByteBuffer put(byte\[] source,int offset,int length) throws BufferUnderflowException
将字节数组中的所有字节或指定区域的字节推入到缓冲区中。如果缓冲区不够大，将不会写入任何字节并抛出`BufferUnderflowException`

#### Xxx getXxx()
##### Xxx getXxx(int index)
##### ByteBuffer putXxx(Xxx value)
##### ByteBuffer putXxx(int index,Xxx value)
读写一个二进制数。`Int Long Short Char Float Double`中的一个

#### ByteBuffer order()
##### ByteBuffer order(ByteOrder order)
设置或获得字节顺序，`order`的值是`ByteOrder`类的常量`BIG_ENDIAN`或`LITTLE_ENDIAN`中的一个
### 静态方法
#### ByteBuffer allocate(int capacity)
创建指定容量的缓冲区
#### ByteBuffer wrap(byte\[] values)
创建指定容量的缓冲区，该缓冲区是对`values`数组的包装
#### CharBuffer asCharBuffer()
构建字符缓冲区，它是对当前缓冲区的包装。对字符缓冲区的变更将同步给缓冲区，但是字符缓冲区有自己的位置、界限和标记。