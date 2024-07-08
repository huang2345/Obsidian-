Request 接口的只读 body 属性包含一个 ReadableStream，其中包含已添加到请求中的主体内容。请注意，使用 GET 或 HEAD 方法的请求不能有主体，这些情况下返回 null。

