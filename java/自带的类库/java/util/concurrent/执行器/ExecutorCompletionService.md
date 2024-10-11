# ExecutorCompletionService\<V>
类
### 构造器
#### ExecutorCompletionService(Executor e)
构造一个执行器完成服务来收集执行器e的结果。
### 实例方法
#### Future\<V> submit(Callable\<V> task)
#### Future\<V> submit(Runnable task,V result)
向底层执行器提交一个任务
#### Future\<V> take()
弹出下一个已完成的结果，如果没有可用的已完成结果，线程阻塞
#### Future\<V> poll()
#### Future\<V> poll(long time,TimeUnit unit)
弹出下一个已完成的结果，如果没有可用的已完成结果，则返回null。第二个方法会等待指定的时间。