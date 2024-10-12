这个接口只是作为一个标记，指示这个类可以克隆。
>Cloneable是Java提供的标记接口，不包含任何方法，只是作为一个标记

克隆使用从Object类继承而来的==clone()==方法，默认的`clone()`只能实现浅拷贝。
>Object中继承而来的`clone`无法直接调用，`clone`的访问级别是`protected`的，其他包的类不能访问。
>需要覆盖clone方法并给它声明更高的访问级别。

#### 浅拷贝
```java
class ClassName implements Cloneable{
	public XxxObject clone() throws CloneNotSupportedException{
		//通过super调用Object的clone方法
		return (XxxObject)super.clone();
	}
}
```
Object类的clone方法可能抛出`CloneNotSupportedException`异常，意为在没有实现Cloneable接口的对象上调用clone方法。
>在Java1.4之前，clone方法总是返回Object

#### 深拷贝
深拷贝需要将引用字段也调用它们的clone方法，这个过程会持续到对象中没有引用字段为止。
>深拷贝是递归的

