指示资源的MIME类型。
>当浏览器执行 MIME 嗅探时，该标头的值可能会被忽略；将 [`X-Content-Type-Options`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/X-Content-Type-Options) 标头值设置为 `nosniff` 可防止这种行为。

#### 语法
```HTTP
Content-Type: text/html; charset=utf-8
Content-Type: multipart/form-data; boundary=something
```
#### 指令
- media-type
	- MIME类型
- charest
	- 字符编码标准
- boundary
	- 对于多部分实体，必须使用 `boundary` 指令。该指令由 1 至 70 个字符组成，这些字符选自一套已知能通过电子邮件网关的、非常健壮的字符集（并且不以空白字符结束）。它用于封装信息多个部分的边界。通常情况下，开头的边界前会加上两个破折号，而末尾边界的后面也会加上两个破折号。
