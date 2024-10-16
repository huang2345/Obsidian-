### 构造器
#### PushbackInputStream(InputStream in)
#### PushbackInputStream(InputStream in,int size)
构造一个可以预览一个或`size`个字节的回退缓冲区的输入流
### 实例方法
#### int read()
预览一个字节
#### void unread(int b)
回推一个字节