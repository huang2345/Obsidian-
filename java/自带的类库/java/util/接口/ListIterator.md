# ListIterator\<E> implements Iterator
#### void add(E newElement)
在当前位置-1添加一个元素
#### void set(E newElement)
替换上一次访问的元素。如果没有上一次调用的next或previous，将抛出`IllegalStateException`
#### boolean hasPrevious()
如果当前位置-1的元素存在，返回true
#### E previous()
返回当前位置-1的元素，并向左移动指针
#### int nextIndex()
返回当前位置+1的索引
#### int previousIndex()
返回当前位置-1的索引