# List\<E> implements Collection
接口
#### ListIterator\<E> listIterator()
返回迭代器对象，ListIterator是Iterator的子接口。
#### ListIterator\<E> listIterator(int index)
返回迭代器对象，并将指针移动到index。
#### void add(int i,E element)
在指定位置添加元素
#### void addAll(int i,Collection\<? extends E> elements)
将一个集合中的元素添加到指定位置。
#### E remove(int i)
删除并返回指定位置的元素
#### E get(int i)
获取指定位置的元素
#### E set(int i,E element)
将位置i的元素替换为element，并返回原来的元素。
#### int indexOf(Object element)
返回第一个与指定元素相等的元素在列表中的位置。如果没有匹配的，返回-1
#### lastIndexOf(Object element)
与indexOf相反