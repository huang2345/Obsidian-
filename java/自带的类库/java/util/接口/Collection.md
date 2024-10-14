# Collection\<E>
接口
#### Iterator\<E> iterator()
返回迭代器
#### int size()
返回当前存储的元素个数
#### boolean isEmpty()
判断是否为空
#### boolean contains(Object obj)
判断集合中有没有obj对象
#### boolean containAll(Collection\<?> other)
如果集合中包含other集合中的所有元素，返回true
#### Object\[] toArray()
返回这个集合中的对象的数组
#### \<T> T\[] toArray(IntFunction\<T\[]> generator)
返回这个集合中的对象的数组。该数组实用generator构造，这通常是一个构造器引用
#### default Stream\<E> stream()
#### default Stream\<E> parallelStream()
产生当前集合中所有元素的顺序流或并行流。

### 增删
#### boolean add(E element)
添加
#### boolean addAll(Collection\<? extends E> other)
将other集合中的所有元素添加
#### remove(Object obj)
删除集合中的obj元素，成功返回true
#### removeAll(Collection\<?> other)
remove的addAll版
#### default boolean removeIf(Predicate\<? super E> filter)
筛除filter方法返回true的元素。
#### void clear()
删除所有元素
#### retainAll(Collection\<?> other)
删除所有与other集合中没有的元素。
