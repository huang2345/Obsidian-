# TransferQueue\<E>
接口
#### void transfer(E element)
#### boolean tryTransfer(E element,long time,TimeUnit unit)
传输一个值，或者尝试在给定的超时时间内传输这个值。这个调用将线程阻塞，直到另一个线程将元素删除。`tryTransfer`方法会在调用成功返回true。