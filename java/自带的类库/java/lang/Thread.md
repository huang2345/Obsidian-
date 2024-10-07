# Thread
类
### 接口
#### UncaughtExceptionHandler
##### void uncaughtException(Thread t,Throwable e)
定义未捕获异常的处理器
### 构造器
#### Thread(Runable target)
构造一个线程对象，启动后会调用`target`的`run`方法
### 实例方法
#### void run()
调用`Runnable`对象的`run`方法
#### void start()
启动该线程，从而调用`run`方法。该方法立刻返回，新线程会并发运行。
#### void join()
#### void join(long miillis)
等待指定的线程终止或者等待经过指定的毫秒数。
#### Thread.State getState()
获取线程的状态：`NEW、RUNNABLE、BLOCKED、WAITING、TIMED_WAITING、TERMINATED`。
#### void interrupt()
将该线程的中断状态标志设置为true。如果该线程被一个`sleep`调用阻塞，则抛出一个`InterruptedException`异常
#### boolean isInterrupted()
获取该线程的中断状态标志
#### void setDaemon(boolean isDaemon)
标记该线程为守护线程或用户线程。必须在线程启动前调用。
#### void setUncaughtExceptionHandler(Thread.UncaughtExceptionHandler handler)
为该线程设置未捕获异常的处理器
#### Thread.UncaughtExceptionHandler getUncaughtExceptionHandler()
获取该线程的未捕获异常的处理器。如果没有安装，则将线程组对象作为处理器返回
#### void setPriority(int newPriority)
设置线程优先级，值在1~10之间
### 静态方法
#### void sleep(long millis)
当前线程休眠指定的毫秒。
#### boolean interrupted()
获取当前线程的中断标志状态。会将标志重置为false
#### Thread currentThread()
返回当前正在执行的线程对象
#### void setDefaultUncaughtExceptionHandler(Thread.UncaughtExceptionHandler handler)
设置所有线程的未捕获异常的默认处理器
#### Thread.UncaughtExceptionHandler getDefaultUncaughtExceptionHandler()
获取未捕获异常的默认处理器
### 静态常量
#### int MIN_PRIORITY
Thread的最小优先级，值为1
#### int MAX_PRIORITY
Thread的最大优先级，值为10
#### int NORM_PRIORITY
Thread的默认优先级，值为5。