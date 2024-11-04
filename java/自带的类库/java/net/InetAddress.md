### 静态方法
#### InetAddress getByName(String host)
#### InetAddress\[] getAllByName(String host)
为指定的名创建一个`InetAddress`对象，或者一个包含了该主机名所对应的所有因特网网址的数组。
#### InetAddress getLocalHost()
为本地主机创建一个`InetAddress`对象
### 实例方法
#### byte\[] getAddress()
返回一个包含因特网网址的字节数组
#### String getHostAddress()
返回包含因特网网址的字符串
#### String getHostName()
返回主机名