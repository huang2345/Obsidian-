# Stream\<T>
类
### 实例方法
#### Stream\<T> filter(Predicate\<? super T> p)
产生一个流，其中包含当前流中满足p的所有元素
#### map(Function\<? super T,? extends R> mapper)
流中的所有元素都应用`mapper`函数，所有返回值作为新的流的元素。
#### flatMap(Function\<? super T,? extends Stream\<? extends R>> mapper)
`mapper`函数同样是遍历所有元素，但是该方法的`mapper`会返回一个流。该方法通过连接所有`mapper`返回的流来产生一个流。
#### mapMulti(BiConsumer\<? super T,? super Consumer\<R>> mapper)
`mapper`遍历所有元素，并在调用期间要使用Consumer的`accept`方法来将最终结果添加到新的流中。
#### Stream\<T> limit(long maxSize)
产生一个流，获取当前流中的前maxSize个元素
#### Stream\<T> skip(long n)
产生一个流，跳过当前流的n个元素
#### Stream\<T> takeWhile(Predicate\<? super T> predicate)
按顺序从前往后的元素分别传入`predicate`函数，一旦`predicate`返回false，停止获取元素，该方法会用前面那些满足条件的元素产生一个新的流
#### Stream\<T> dropWhile(Predicate\<? super T> predicate)
该方法与`takeWhile`相反，一旦`predicate`返回true，停止获取元素并用前面返回false的元素产生一个流。
#### Stream\<T> distinct()
产生一个流，对当前流的元素去重
#### Stream\<T> sorted()
#### Stream\<T> sorted(Comparator\<? super T> comparator)
产生一个流，对当前流进行排序。第一个方法要求流的元素都是实现了`Comparable`接口的实例。
#### Stream\<T> peek(Consumer\<? super T> action)
产生一个流，它与当前流中的元素相同。但是在实际获取元素时，会将其传递给`action`函数。很适合用来调试。
### 约简操作
#### Optional\<T> max(Comparator\<? super T> comparator)
#### Optional\<T> min(Comparator\<? super T> comparator)
产生最大元素和最小元素，如果流为空，会返回空的`Optional`对象
#### Optional\<T> findFirst()
#### Optional\<T> findAny()
产生第一个或任意一个元素，如果流为空，返回空的`Optional`对象
#### boolean anyMatch(Predicate\<? super T> predicate)
任意元素在`predicate`方法中返回`true`时，返回`true`
#### boolean allMatch(Predicate\<? super T> predicate)
所有元素在`predicate`方法中返回`true`时，返回`true`
#### boolean noneMatch(Predicate\<? super T> predicate)
所有元素在`predicate`方法中返回`false`时，返回`true`
#### long count()
返回当前流中元素的数量。终止操作
### 静态方法
#### \<T> Stream\<T> of(T... values)
产生一个元素为给定值的流。
#### \<T> Stream\<T> empty()
产生一个不包含任何元素的流
#### \<T> Stream\<T> generate(Supplier\<T> s)
产生一个无限流，它的值是通过反复调用函数s构建，会用s的上一次的返回值当做这次的参数

#### Stream\<T> iterate(T seed,UnaryOperator\<T> f)
#### Stream\<T> iterate(T seed,Predicate\<? super T> hasNext,UnaryOperator\<T> f)
产生一个无限流，元素包含`seed`，然后将`seed`传入函数f，然后递归生成序列值

`hasNext`函数用于限制序列的长度，只要`hasNext`函数返回了false，这个流即将结束。

#### \<T> Stream\<T> ofNullable(T t)
如果t为null，返回一个空流。否则返回包含t的流
#### \<T> Stream\<T> concat(Stream\<? extends T> a,Stream\<? extends T> b)
连接两个流。