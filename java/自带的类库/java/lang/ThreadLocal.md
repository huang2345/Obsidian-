# ThreadLocal\<T>
类
### 静态方法
#### \<S> ThreadLocal\<S> withInitial(Supplier\<? extends S> supplier)
创建一个线程局部变量，其初始值为lambda表达式的返回值
### 实例方法
#### T get()
获取当前值。首次调用会调用`withInitial`的参数：一个lambda表达式来构造局部变量。
#### void set(T t)
设置一个新的值
#### void remove()
删除值。