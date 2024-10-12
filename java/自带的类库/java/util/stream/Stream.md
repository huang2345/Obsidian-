# Stream\<T>
类
### 实例方法
#### Stream\<T> filter(Predicate\<? super T> p)
产生一个流，其中包含当前流中满足p的所有元素
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