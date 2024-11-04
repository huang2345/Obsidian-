### 实例方法
#### InetSocketAddress(String hostname,int port)
用指定的主机名和端口创建一个`InetSocketAddress`对象并解析主机名。如果主机名不能被解析，那么该地址对象的属性`unresolved`将被设置成`true`
#### boolean isUnresolved()
如果不能解析该地址，返回true