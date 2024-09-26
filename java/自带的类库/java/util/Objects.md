### 静态方法
#### \<T> void requireNonNull(T obj,?String message,?Supplier\<String> messageSupplier)
如果obj为null，该方法会抛出一个==NullPointerException异常==，可能有给定的消息
#### \<T> T requireNonNullElse(T obj,T defaultObj)
#### \<T> T requireNonNullElseGet(T obj,Supplier\<T> defaultSupplier)
如果obj不为null则返回obj，如果为null则返回默认对象
#### int hash(Object... obj)
返回散列码，由提供的所有对象的散列码组合获得
#### int hashCode(Object a)
如果a为null，返回0；否则返回a.hashCode()。