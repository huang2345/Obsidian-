除了使用`Comparable`接口的`compareTo()`方法来进行排序，还可以使用该接口。
通过将实现该接口的类的实例传递给`Arrays.sort()`的第二个参数实现排序
### 方法
#### int compare(T first,T second);
first在前：返回正整数；在后：返回负整数；相同：返回0