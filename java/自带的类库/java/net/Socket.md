### 构造器
#### Socket()
创建一个无连接的套接字
#### Socket(String host,int port)
创建一个连接指定主机端口的套接字
### 实例方法
#### InputStream getInputStream()
获取`Socket`的输入流
#### OutputStream getOutputStream()
获取`Socket`的输出流
#### void connect(SocketAddress address)
将套接字连接到指定的地址
#### void connect(SocketAddress address,int timeoutInMilliseconds)
将套接字连接到指定的地址。如果在指定的时间内没有响应，则返回。
#### void setSoTimeout(int timeoutInMilliseconds)
设置该套接字上读请求的阻塞时间。如果超出指定时间，则抛出`SocketTimeoutException`。
#### boolean isConnected()
如果该套接字已被连接，返回`true`
#### boolean isClosed()
如果套接字已被关闭，则返回`true`
#### void shutdownOutput()
将输出流设为流结束
#### void shutdownInput()
将输入流设为流结束
#### boolean isOutputShutdown()
如果输出流被关闭返回true
#### boolean isInputShutdown()
如果输入流被关闭返回true