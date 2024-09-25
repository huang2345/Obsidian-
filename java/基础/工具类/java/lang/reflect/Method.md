### 实例方法
#### Class getDeclaringClass()
返回一个Class对象，表示定义了这个构造器、方法或字段的类
#### Class\[] getExceptionTypes()
数组中各个对象表示该方法所抛出的异常的类型
#### int getModifiers()
返回一个供`java.lang.reflect.Modifier`类解析的整数，描述该构造器、方法或字段的修饰符。
#### String getName()
返回一个表示构造器名、方法名或字段名的字符串\
#### Class\[] getParameterTypes()
数组中的Class对象表示参数的类型
#### Class getReturnType()
表示返回类型的Class对象。
#### public Object invoke(Object implicitParameter,Object\[] explicitParameters)
调用该Method对象描述的方法。`impliciParameter`是具体的实例对象，第二个参数为函数的参数列表。
该方法对于基础类型将以包装器来返回。如果调用的是静态方法，第一个参数为`null`