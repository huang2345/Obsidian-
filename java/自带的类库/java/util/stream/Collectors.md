类
### 工厂方法
#### \<T> Collector\<T,?,List\<T>> toList()
#### \<T> Collector\<T,?,List\<T>> toUnmodifiableList()
产生一个将元素收集到列表中的收集器
#### \<T> Collector\<T,?,Set\<T>> toSet()
#### \<T> Collector\<T,?,Set\<T>> toUnmodifiableSet()
产生一个将元素收集到集中的收集器

#### \<T,C extends Collection\<T>> Collector\<T,?,C> toCollection(Supplier\<C> collectionFactory)
产生一个将元素收集到任意的指定的集合中的收集器，`collectionFactory`是指返回集合的函数，可以传递诸如`TreeSet::new`的构造器引用。

#### Collector\<charSequence,?,String> joining()
#### Collector\<charSequence,?,String> joining(CharSequence delimiter)
#### Collector\<charSequence,?,String> joining(CharSequence delimiter,CharSequence prefix,CharSequence suffix)
产生一个连接字符串的收集器。分隔符(`delimiter`)；第一个字符串之前的前缀(`prefix`)；最后一个字符串之后的后缀(`suffix`)

#### \<T> Collector\<T,?,IntSummaryStatistics> summarizingInt(ToIntFunction\<? super T> mapper)
#### \<T> Collector\<T,?,LongSummaryStatistics> summarizingLong(ToLongFunction\<? super T> mapper)
#### \<T> Collector\<T,?,DoubleSummaryStatistics> summarizingDouble(ToDoubleFunction\<? super T> mapper)
产生能够生成`(Int/Long/Double)SummaryStatistics`对象的收集器。`SummaryStatistics`对象会存储当前流的所有元素在被`mapper`函数遍历后所产生的结果的数量、总和、平均值、最大最小值。
```java
//产生总数量
long getCount()
//返回总和，在没有任何元素时返回0
(int | long | double) getSum();
//返回平均值，在没有任何元素时返回0
double getAverage();
//返回最大最小值，在没有任何元素时，返回(Integer | Long | Double).(MAX | MIN)_VALUE
(int | long | double) getMax();
(int | long | double) getMin();
```