在Java中不能直接传递一个函数。你必须以实例的形式去传递方法，以达到在类的方法中使用外来的方法。
lambda表达式就是一个简便写法，实质上依旧是用实例去传递方法。
```java
()->{};
```
>如果方法只有一个参数，并且该参数的类型可以通过表达式推导而出，可以省略小括号和类型

lambda表达式可以传递给**函数式接口**类型的参数和变量

`java.util.function`包中定义了很多通用的函数式接口，例如`BiFunction`、`Predicate`等
#### 值捕获
在Java中，lambda表达式跟JS的回调函数差不多，往往都是过一段时间或触发什么条件才执行。
而这在Java中会导致一个问题，如果lambda表达式使用了不是自己声明的变量，但是该变量早就被回收了。

针对该情况，lambda表达式实际上会**捕获**这些在lambda表达式中使用的值，这些变量被称为自由变量，构成lambda表达式的一部分。
>lambda表达式中捕获的变量必须是**事实最终变量**。也就是说，初始化之后不再改变的变量
#### 方法引用
方法引用指示编译器生成一个函数式接口的实例，然后对应的抽象方法会调用指定的方法，并将自己的参数传递给它。
```java
var timer = new Timer(1000,System.out::println);
```
在这个例子中，会生成一个ActionListener，它的抽象方法actionPerformed(ActionEvent e)会将参数e传递给指定的方法。
>只有lambda表达式只调用一个方法时，才能将其重写为方法引用
#### 构造器引用
与方法引用类似，只是方法名为`new`。例如：`ClassName::new`
构造器引用具体使用哪个构造器取决于上下文，取决与生成的函数式接口的实例对应的抽象方法提供什么参数。
