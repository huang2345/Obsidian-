# NavigableSet\<E>
类
### 实例方法
#### E higher(E value)
返回大于value的最小元素，没有返回null
#### E lower(E value)
返回小于value的最大元素，没有返回null
#### E ceiling(E value)
返回大于等于value的最小元素，没有返回null
#### E floor(E value)
返回小于等于value的最大元素，没有返回null

#### E pollFirst()
#### E pollLast()
删除并返回这个集中的最大或最小元素，集为空时返回null。
#### Iterator\<E> descendingIterator()
返回一个按照降序排序元素的迭代器