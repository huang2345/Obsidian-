`Optional<T>`对象是一种包装器对象
#### 获取Optional值
有效地使用`Optional`的关键是使用这种方法：在值不存在时生成一个替代值。
##### T orElse(T other)
返回`Optional`的值。如果值为空，返回`other`
##### T orElseGet(Supplier\<? extends T> other)
返回`Optional`的值。如果值为空，调用`other`方法并将该方法的返回值作为`Optional`的值返回
##### \<X extends Throwable> T orElseThrow(Supplier\<? extends X> exceptionSupplier)
返回`Optional`的值。如果值为空，抛出`exceptionSupplier`方法返回的异常
#### 消费Optional值
这种方法只在值存在时，才将值传递给参数。
##### void ifPresent(Consumer\<? super T> action)
如果`Optional`值存在，将其传递给`action`函数。
##### void ifPresentOrElse(Consumer\<? super T> action,Runnable emptyAction)
与`ifPresent`方法类似，但是在值不存在时会调用函数`emptyAction`。
#### 管道化Optinal值
不获取值，通过方法根据当前`Optional`对象返回一个新的`Optional`对象。
##### \<U> Optional\<U> map(Function\<? super T,? extends U> mapper)
如果当前的`Optional`值存在，那么返回的`Optional`的值是：将原`Optional`值传入`mapper`方法后，其返回值。否则，产生一个空的`Optional`
##### Optional\<T> filter(Predicate\<? super T> predicate)
产生一个`Optional`。如果当前`Optional`值满足`predicate`，那么产生的`Optional`值就是当前的那个值；否则产生一个空`Optional`。
##### Optional\<T> or(Supplier\<? extends Optional\<? extends T>> supplier)
如果当前`Optional`值存在，则返回当前`Optional`；否则，将调用`supplier`方法，它会返回一个`Optional`对象。
#### 创建Optional值
##### static \<T> Optional\<T> of(T value) throws NullPointerException
用给定值产生一个`Optional`。如果value为null，抛出一个`NullPointerException`
##### static \<T> Optional\<T> ofNullable(T value)
用给定值产生一个`Optional`。如果value为null，产生的`Optional`值为空
##### static \<T> Optional\<T> empty()
产生一个空`Optional`
#### 将Optional转换为流
`stream`方法会将一个`Optional<T>`对象转换为一个具有0个或1个元素的`Stream<T>`对象。
这会使得返回`Optional`的方法变得十分有用。可以用流的元素去创建`Optional`对象，使流的元素为`Optional`，再通过`flatMap(Optional::stream)`将转换的流组合成一个新的流。
>`flatMap`方法会将空的流丢弃。因此，可以使用：
>`Stream<User> users = ids.map(...).flatMap(Stream::ofNullable);`
>`Stream.ofNullable(obj)`方法在obj为null时返回空流，否则返回一个只包含obj的流

