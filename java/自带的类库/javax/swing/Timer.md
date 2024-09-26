### 构造器
#### Timer(int interval,ActionListener listener)
构造一个定时器，每隔interval毫秒通知listener对象一次。
listener对象的类需要实现`java.awt.event`包的`ActionListener`接口，实现`actionPerformed(ActionEvent event)`方法
listener对象被通知后会调用`actionPerformed`方法
### 实例方法
#### void start()
启动计时器
>该类启动的计时器不会造成线程阻塞，如果程序结束，那么listener对象将不会被通知。
#### void stop()
停止定时器