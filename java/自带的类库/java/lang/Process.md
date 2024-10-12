# Process 
接口
#### OutputStream getOutputStream()
获取一个输出流(这里的输出流是相对于虚拟机的)，用于写入进程的输入流。
#### InputStream getInputStream()
获取一个输入流(这里的流是相对于虚拟机的)，用于获取进程的输出流。
#### InputStream getErrorStream()
获取一个异常流(这里的流是相对于虚拟机的)，用于获取进程的输出流。

#### int waitFor()
等待进程完成并生成退出值。
#### boolean waitFor(long timeout,TimeUnit unit)
等待进程完成，但是不能超出指定的超时时间。如果进程退出，返回true
#### int exitValue()
返回进程的退出值。按惯例，非0的退出值表示一个错误
#### boolean isAlive()
检查进程是否存活
#### void destroy()
#### Process destroyForcibly()
终止进程，可能正常终止，也可能强制终止
#### boolean supportsNormalTermination()
检查进程是否可以正常终止，或者是否必须强制撤销。
#### ProcessHandle toHandle()
生成该进程的`ProcessHandle`对象
#### CompletableFuture\<Process> onExit()
生成一个`CompletableFuture`任务，会在进程退出时执行。
