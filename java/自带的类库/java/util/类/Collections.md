### 静态方法
#### Xxx unmodifiableXxx(Xxx c)
构造一个集合视图。该视图不可修改元素
#### Xxx synchronizedXxx(Xxx c)
构造一个同步的视图
#### \<T extends Comparable\<? super T>> void sort(List\<T> elements)
排序，算法的时间复杂度为`O(n logn)`
#### void shuffle(List\<?> elements)
随机混排列表中的元素
#### \<T extends Comparable\<? super T>> int binarySearch(List\<T> elements,T key)
#### \<T> int binarySearch(List\<T> elements,T key,Comparator\<? super T> c)
二分法查找。
