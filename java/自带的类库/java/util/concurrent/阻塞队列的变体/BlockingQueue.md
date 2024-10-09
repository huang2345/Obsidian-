# BlockingQueue\<E>

#### void put(E element)
添加元素，如果队列已满，阻塞
#### E take()
移除并返回队头元素，如果队列为空，阻塞
#### boolean offer(E element,long time,TimeUnit unit)
添加给定的元素，成功返回true，必要时阻塞，直到元素已经添加或时间已到。unit表示时间单位
#### E poll(long time,TimeUnit unit)
移除并返回队头元素，必要时阻塞，直到元素可用或时间已到。失败时返回null。