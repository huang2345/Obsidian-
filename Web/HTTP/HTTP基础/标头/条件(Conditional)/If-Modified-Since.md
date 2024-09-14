当响应过时并不能复用时，客户端发送带有`If-Modified-Since`请求标头的请求，以询问服务器自指定时间以来被请求资源是否有改变。
如果没有改变，服务器将返回一个状态码为`304`的无body的响应表示没有变化。
如果有改变，服务器将在响应的body中包含新的资源，正常返回时状态码为`200`。
>不同于`If-Unmodified-Since`，`If-Modified-Since`只能用在`GET`或`HEAD`请求中
>当与`If-None-Match`一起使用时，`If-Modified-Since`标头将被忽略，除非服务器不支持`If-None-Match`标头

语法与指令与`Last-Modified`标头相同