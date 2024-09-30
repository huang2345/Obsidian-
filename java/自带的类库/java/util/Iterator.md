# Iterator\<E>
接口
#### boolean hasNext()
如果存在下一个可访问元素，返回true
#### E next()
返回下一个元素并移动指针，如果已经抵达末尾，抛出一个`NoSuchElementException`
#### void remove()
删除上次访问的对象。如果上次访问之后集合发生了变化，需要重新使用next，否则抛出一个`IllegalStateException`
#### default void forEachRemaining(Consumer\<? super E> action)
遍历所有元素，并传递指定的动作。action是一个实现了函数式接口Consumer的实例