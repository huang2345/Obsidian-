### 构造器
#### Throwable()
构造一个新的对象，但没有描述信息
#### Throwable(Throwable cause)
#### Throwable(String message,Throwable cause)
用给定的异常(cause原因)构造
#### Throwable(String message)
构造一个新的对象，带有描述信息。
按照惯例，所有派生的异常类都支持一个默认的无参构造器和一个带描述信息的构造器
### 实例方法
#### void printStackTrace()
将Throwable对象和栈轨迹打印到标准错误流
#### String getMessage()
获取Throwable对象的详细描述信息
#### Throwable initCause(Throwable cause)
为该对象设置原因，如果已经有原因了，则抛出一个异常。返回this
#### Throwable getCause()
获取设置为该对象的原因的异常对象。如果没有原因，返回null
#### StackTraceElement\[] getStackTrace()
获取构造这个对象时调用栈的轨迹
#### void addSuppressed(Throwable t)
添加一个“被抑制”的异常
#### Throwable\[] getSuppressed()
获取这个异常的所有“被抑制”的异常