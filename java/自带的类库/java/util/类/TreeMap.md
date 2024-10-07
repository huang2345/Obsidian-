# TreeMap\<K,V>
类
### 构造器
#### TreeMap()
构造一个空的树映射，key都实现了`Comparable`接口
#### TreeMap(Comparator\<? super K> c)
构造一个空的树映射，并使用一个指定的比较器
#### TreeMap(Map\<? extends K,? extends V> entries)
构造一个树映射，并将entries映射中的元素添加到树中
#### TreeMap(SortedMap\<? extends K,? extends V> entries)
构造一个树映射，将有序映射中的所有元素添加到树中，并使用有序映射entries的比较器
