Object类是Java中继承链的最顶端的类，每个类都是由Object类扩展而来。
### 实例方法
#### equals(Object obj)
确认两个对象的是否是同一个引用
#### getClass()
返回一个类对象，其中包含有关对象的信息
#### hashCode()
返回对象的哈希值，Object类中默认的该方法的散列值是由对象的地址得出。equals与hashCode方法必须兼容
#### toString()
返回一个字符串表示对象的值
#### void notifyAll()
解除这个对象上内部条件的等待集中所有线程的阻塞。该方法只能在同步方法或同步块中使用。如果当前线程没有持有内部锁，该方法抛出一个`IllegalMonitorStateException`
#### void notify()
随机解除该对象上内部条件的等待集中的某个线程的阻塞。该方法只能在同步方法或同步块中使用。如果当前线程没有持有内部锁，该方法抛出一个`IllegalMonitorStateException`
#### void wait()
#### void wait(long millis)
#### void wait(long millis,int nanos)
使线程阻塞并放入内部条件的等待集中，直到被`notifyAll/notify`方法解除或者经过了指定的时间。`nanos`参数表示纳秒数，不能超过1_000_000。该方法只能在同步方法或同步块中使用。如果当前线程没有持有内部锁，该方法抛出一个`IllegalMonitorStateException`
