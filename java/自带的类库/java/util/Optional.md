# Optional\<T>
类
### 实例方法
#### \<U> Optional\<U> flatMap(Function\<? super T,? extends Optional\<? extends U>> mapper)
如果当前`Optional`值存在，将其传递给`mapper`函数并将`mapper`函数的返回值作为新的`Optional`值。在当前`Optional`值为空时，返回一个空`Optional`
#### T orElse(T other)
返回`Optional`的值。如果值为空，返回`other`
#### T orElseGet(Supplier\<? extends T> other)
返回`Optional`的值。如果值为空，调用`other`方法并将该方法的返回值作为`Optional`的值返回
#### \<X extends Throwable> T orElseThrow(Supplier\<? extends X> exceptionSupplier)
返回`Optional`的值。如果值为空，抛出`exceptionSupplier`方法返回的异常
#### T get() throws NoSuchElementException
产生这个`Optional`的值。如果值为空，抛出`NoSuchElementException`
##### T orElseThrow()
get方法的同一次，与get方法相同
#### boolean isEmpty()
#### boolean isPresent()
判断`Optional`的值是否为空或者是否存在。
