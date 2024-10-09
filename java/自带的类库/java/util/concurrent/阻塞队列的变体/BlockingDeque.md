# BlockingDeque\<E>

#### void putFirst(E element)
#### void putLast(E element)
在队头或队尾添加元素，必要时阻塞

#### E takeFirst()
#### E takeLast()
移除并返回队头或队尾元素，必要时阻塞

#### boolean offerFirst(E element,long time,TimeUnit unit)
#### boolean offerLast(E element,long time,TimeUnit unit)
在队头或队尾添加给定的元素，成功返回true，必要时阻塞，直至元素已经添加或时间已到

#### boolean pollFirst(long time,TimeUnit unit)
#### boolean pollLast(long time,TimeUnit unit)
移除并返回队头或队尾元素，失败时返回null，必要时阻塞，直至元素已经添加或时间已到