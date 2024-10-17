### 构造器
#### ObjectOutputStream(OutputStream out)
创建一个对象输出流。
### 实例方法
#### void writeObject(Object obj)
将序列化对象输出到流中。该方法将存储指定对象的类、类的签名以及这个类及其超类中所有非静态和非瞬时的域的值。