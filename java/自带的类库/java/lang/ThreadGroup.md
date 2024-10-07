# ThreadGroup implements Thread.UncaughtExceptionHandler
类
### 实例方法
#### uncaughtException(Thread t,Throwable e)
如果有父线程组，调用父线程组的这个方法；或者，如果有默认处理器；否则，将栈轨迹打印到标准错误流。如果e是一个`ThreadDeath`对象，就什么都不做