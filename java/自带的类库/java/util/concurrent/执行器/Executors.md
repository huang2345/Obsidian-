### 静态工厂方法
#### ExecutorService newCachedThreadPool()
返回一个缓存线程池，会在必要时创建线程，如果线程空闲60秒则终止该线程
#### ExecutorService newFixedThreadPool(int threads)
返回一个线程池，拥有threads个线程
#### ExecutorService newSingleThreadExecutor()
返回一个只有一个线程的线程池。

#### ScheduledExecutorService newScheduledThreadPool(int threads)
返回一个线程池
#### ScheduledExecutorService newSingleThreadScheduledExecutor(int threads)
返回一个执行器。