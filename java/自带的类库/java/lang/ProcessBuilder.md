### 构造器
#### ProcessBuilder(String... command)
#### ProcessBuilder(List\<String> command)
用给定的命令和参数构造一个进程构建器
### 实例方法
#### ProcessBuilder directory(File directory)
设置进程的工作目录
#### ProcessBuilder inheritIO()
让进程使用虚拟机的标准输入、输出和错误流。
#### ProcessBuilder redirectErrorStream(boolean redirectErrorStream)
如果参数为true，将进程的标准错误流和标准输出流合并
#### ProcessBuilder redirectInput(File file)
#### ProcessBuilder redirectOutput(File file)
#### ProcessBuilder redirectError(File file)
将进程的流重定向给指定的文件

#### ProcessBuilder redirectInput(ProcessBuilder.Redirect source)
#### ProcessBuilder redirectOutput(ProcessBuilder.Redirect destination)
#### ProcessBuilder redirectError(ProcessBuilder.Redirect destination)
重定向流，流可以是：
- Redirect.PIPE：默认
- Redirect.INHERIT：虚拟机的流
- Redirect.DISCARD
- Redirect.from(file)
- Redirect.to(file)
- Redirect.appendTo(file)

#### Map\<String,String> environment
生成一个可更改的映射，用于设置进程的环境变量
#### Process start()
启动进程

### 静态方法
#### List\<Process> startPipeLine(List\<ProcessBuilder> builders)
启动一个进程流水线，将各个进程的标准输出连接到下一个进程的标准输入。
