# InputStream
抽象类
### 抽象方法
#### abstract int read()
从数据中读入一个字节并返回，该`read`方法在碰到输入流结尾时返回`-1`
### 实例方法
#### int read(byte\[] b)
试图读取`b.length`个字节(将其写入到数组b中)并返回实际读入的字节数。在碰到输入流的结尾时返回`-1`。最多只能读取`b.length`个字节
#### int read(byte\[] b,int off,int len)
与`read(byte[] b)`几乎一样，但是可以用`off`指定读取的数据在数组`b`中的起始位置；`len`指定最多能够读取的字节数，该参数必须小于数组`b`的大小
#### int readNBytes(byte\[] b,int off,int len)
从java9引入的`read(byte[] b,int off,int len)`的语义化版本。但是没有要求`InputStream`的子类必须实现。
#### byte\[] readAllBytes()
读取输入流中读入的所有字节，将其写入一个字节数组。返回该字节数组
#### long transferTo(OutputStream out)
将当前输入流中的所有字节发送给输出流`out`，返回发送的字节数。
#### long skip(long n)
尝试在输入流中跳过`n`个字节，返回实际跳过的字节数
#### long skipNBytes(long n)
`skip`方法的语义化版本
#### int available()
返回当前在不阻塞情况下可获取的字节数。
#### void close()
关闭流
#### void mark(int readlimit)
在输入流的当前位置打一个标记。如果从输入流中已读取得到字节多于`readlimit`个，则这个流允许忽略这个标记
#### void reset()
返回到最后一个标记。位置将被重置到标记时的位置。如果当前没有任何标记，则这个流不被重置。
#### boolean markSupported()
如果这个流支持打标记，返回`true`。
### 静态方法
#### InputStream nullInputStream()
返回一个空的输入流。
