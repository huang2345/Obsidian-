# ExecutorService
接口
#### Future\<T> submit(Callable\<T> task)
#### Future\<?> submit(Runnable task)
#### Future\<T> submit(Runnable task,T result)
提交任务
#### void shutdown()
关闭线程池。执行器不再接受新任务，所有任务完成时，线程池中的所有线程死亡
#### void shutdownNow()
与`shutdown`方法类似，但是会取消所有未开始的任务。
#### T invokeAny(Collection\<Callable\<T>> tasks
#### T invokeAny(Collection\<Callable\<T>> tasks,long timeout,TimeUnit unit)
执行`Callable`集合的所有任务，返回其中一个任务的结果。对于第二个方法，如果超时将抛出`TimeoutException`异常。
#### List\<Future\<T>> invokeAll(Collection\<Callable\<T>> tasks)
#### List\<Future\<T>> invokeAll(Collection\<Callable\<T>> tasks,long timeout,TimeUnit unit)
执行所有任务，返回所有任务的结果。如果超时，第二个方法会抛出`TimeoutException`。