# PriorityBlockingQueue\<E>
类
### 构造器
#### PriorityBlockingQueue()
#### PriorityBlockingQueue(int initialCapacity)
#### PriorityBlockingQueue(int initialCapacity,Comparator\<? super E> comparator)
构造一个无上限阻塞优先队列，实现为一个堆。默认初始容量为11.如果没有指定比较器，元素必须实现`Comparable`接口