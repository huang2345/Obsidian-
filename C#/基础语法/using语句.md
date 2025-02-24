某些类型的非托管对象有数量限制或很耗费系统资源，例如I/O获取的File等资源。`using`语句有助于简化：获取-›使用-›释放资源的过程。
>资源是指实现了`System.IDisposable`接口的类或结构，该接口有`Dispose`方法，用于释放资源
>`using`语句与`using`指令是两个东西
#### 使用
```c#
//可以使用逗号分隔来获取多个资源
using(ResourceType Identifier = Expression) Statement
//使用已获取的资源
using(Identifier)
```
`using`语句会自动释放资源，`using`语句执行以下任务：
1. 分配资源
2. 将Statement放进try块
3. 在finally块中调用资源的Dispose