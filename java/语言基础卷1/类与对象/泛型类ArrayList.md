java允许在运行时确定数组的大小，但并没有完全解决运行时动态修改数组的问题。为此，泛型类ArrayList类应运而生。
该泛型类会自动调整空间，通过重新创建数组和复制源数组
```java
ArrayList<Test> test = new ArrayList<Test>();
var test = new ArrayList<Test>();
```
通过这种形式使用泛型。
>ArrayList元素的类型不能是基础类型，但可以是它们的包装类

#### 构造器
##### ArrayList(int number)
起到与ensureCapacity方法一样的作用
#### 实例方法
##### boolean add(T obj)
添加到数组列表中，总是返回true
##### void add(int index,T obj)
将obj插入指定位置
##### void ensureCapacity(int number)
在自动分配空间前，手动为其分配可能储存的元素数量，减少重新分配空间带来的开销。
##### int size()
返回当前存储在数组列表中的元素个数
##### void trimToSize()
将ArrayList的存储容量削减到当前的实际大小
##### T set(int index,T value)
设置元素
##### T get(int index)
获取元素
##### T remove(int index)
删除指定位置的元素，并将后面的元素前移