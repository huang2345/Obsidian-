### 静态方法
#### \<T> void requireNonNull(T obj,?String message,?Supplier\<String> messageSupplier)
如果obj为null，该方法会抛出一个==NullPointerException异常==，可能有给定的消息
#### \<T> T requireNonNullElse(T obj,T defaultObj)
#### \<T> T requireNonNullElseGet(T obj,Supplier\<T> defaultSupplier)
如果obj不为null则返回obj，如果为null则返回默认对象