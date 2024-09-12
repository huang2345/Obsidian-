HTTP 消息是服务器和客户端之间交换数据的方式：请求request和响应response

HTTP请求和响应有相似的结构：
1. 一行起始行用于描述要执行的请求，或者是对应的状态。这个起始行总是单行的。
2. 一个可选的 HTTP 标头集合指明请求或描述消息主体（body）。
3. 一个空行指示所有关于请求的元数据已经发送完毕。
4. 一个可选的包含请求相关数据的主体（比如 HTML 表单内容），或者响应相关的文档。主体的大小有起始行的 HTTP 头来指定。
 ![](Pasted%20image%2020240912142955.png)
#### HTTP请求
##### 起始行
1. HTTP方法(GET、POST等)
2. 请求目标：
	- URL
	- 相对地址
3. HTTP版本
##### 标头(Header)
请求标头很多，它们可以分为几组：
- 通用标头(General header)
	- 例如 [`Via`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Via)，适用于整个消息。
- 请求标头(Request header)
	- 例如`User-Agent`、`Accept-Type`，通过进一步的定义（例如 [`Accept-Language`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Accept-Language)）、给定上下文（例如 [`Referer`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Referer)）或者进行有条件的限制来修改请求。
- 表示标头(Representation header)
	- 例如 [`Content-Type`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Content-Type) 描述了消息数据的原始格式和应用的任意编码（仅在消息有主体时才存在）。
![](Pasted%20image%2020240912144946.png)
##### 主体(Body)
不是所有的请求都有body，只有需要将数据发送到服务器上的请求有body。
主体大致分为两类：
- 单一资源(Single-resource)主体，由一个单文件组成。该类型的主体由两个标头定义：`Content-Type`和`Content-Length`
- 多资源(Multiple-resource)主体，由多部分主体组成，每一部分包含不同的信息位。通常与表单有关。

#### HTTP响应
##### 状态行
HTTP响应的起始行被称为状态行(status line)，包含以下信息：
1. 协议版本
2. 状态码(status code)
3. 状态文本(status text)，简短的状态信息
##### 标头(Header)
- 通用标头(General header)
	- 例如 [`Via`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Via)，适用于整个消息。
- 请求标头(Request header)
	- 例如 [`Vary`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Vary) 和 [`Accept-Ranges`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Accept-Ranges)，提供有关服务器的其他信息
- 表示标头(Representation header)
	- 例如 [`Content-Type`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Content-Type) 描述了消息数据的原始格式和应用的任意编码（仅在消息有主体时才存在）。
![](Pasted%20image%2020240912145000.png)
##### 主体(Body)
响应的最后一部分是主体。不是所有的响应都有主体
- 单资源主体，由**已知**长度的单个文件组成。该类型主体由两个标头定义：`Content-Type`和`Content-Length`
- 单资源主体，由**未知**长度的单个文件组成。通过将`Transfer-Encoding`标头设置为`chunked`来使用分块编码
- 多资源主体，由多部分 body 组成，每部分包含不同的信息段。但是很少
