### 实例方法
#### void lock()
获取锁。如果锁当前被其他线程占有，则阻塞
#### void unlock()
释放锁
#### Condition newCondition()
返回一个与这个锁相关联的条件对象。