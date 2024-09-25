### 实例方法
#### String getName()
返回类名，包含包名。
#### Class getSuperclass()
以Class对象的形式返回这个类的父类。
#### Constructor getConstructor(Class... parameterTypes)
生成一个对象，描述有指定参数类型的构造器。
#### String getPackageName()
获取这个类型的包名，不包含类名。
#### Object get(Object obj)
返回obj对象中用这个Field对象描述的字段的值
#### void set(Object obj,Object newValue)
将obj对象中用Field对象描述的字段设置为一个新值

#### URL getResource(String name)
#### InputStream getResourceAsStream(String name)
寻找与类位于同一位置的资源，然后返回一个URL或者输入流。如果没有找到资源，则返回null，因此不会对I/O错误抛出异常

#### Field getField(String name)
获取指定名的公共字段。
#### Field\[] getFields()
数组中的对象对应这个类或其父类的`public`的字段。如果类没有这样的字段或者该Class对象表示基础类型或数组，则返回长度为0的数组
#### Field\[] getDeclaredFields(String name)
获取指定名的字段
#### Field\[] getDeclaredFields()
与getFields方法差不多，但是数组中的对象将对于这个类的全部字段。

#### Method getMethod(String name,Class... parameterTypes)
根据函数签名获取对象
#### Method\[] getMethods()
该方法返回所有的公共方法
#### MethodK\[] getDeclaredMethods()
该方法返回这个类或接口的全部方法，但不包括从父类继承而来的方法。

#### Constructor getConstructor(String name,Class... parameterTypes)
通过函数签名获取构造器的对象
#### Constructor\[] getConstructors()
数组中包含所以公共构造器
#### Constructor\[] getDeclaredConstructors()
数组中包含类的全部构造器

#### isInterface()
如果该Class对象描述一个接口，返回true
#### isEnum()
如果该Class对象描述一个枚举，返回true
#### isRecord()
如果该Class对象描述一个record，返回true
#### isArray()
如果该Class对象描述一个数组类型，返回true

#### RecordComponent\[] getRecordComponents()
返回的这些对象描述了记录字段，如果这个类不是一个记录，返回null
#### Class\<T> getComponentType()
#### Class \<T> componentType()
如果对象表示一个数组类型，则返回描述数组元素类型的Class。否则，返回false
#### Class\<T> arrayType()
返回描述数组类型的Class