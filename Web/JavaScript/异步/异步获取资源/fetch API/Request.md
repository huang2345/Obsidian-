该接口用于表示HTTP请求。可以用Request()构造函数创建该对象，但更多时候都是操作其他API返回的Request对象。

#### 构造函数
##### 参数
###### input
定义要fetch的资源：
- URL
- Request对象
###### init?
一个对象，包含与fetch()的可选参数一样的选项：
- `method`：请求方法
- `header`：HTTP标头
- `body`：请求主体
- `mode`：请求的模式，比如`cors`(默认值)、`no-cors`、`same-origin`和`navigate`
- `credentials`：请求凭据：`omit`(默认值), `same-origin`, 或 `include`。
- `cache`：请求中使用的cache mode
- `redirect`：对重定向处理的模式：`follow`, `error`, 或`manual`。
- `referrer`：
- `integrity`
#### 实例属性
##### body : ReadableStream(只读)
主体内容的
##### bodyUsed : boolean(只读)
表示请求主体是否被使用。由于body是`ReadableStream`，只能被读取一次。false表示未被读取
##### cache : string(只读)
请求的缓存模式：`default`、`no-store`、`reload`、`no-cache`、`force-cache`、`only-if-cached`
##### credentials : string(只读)
请求的凭据，`omit`、`same-origin`、`include`
##### destination : string(只读)
描述请求目的的字符串
##### headers : Headers(只读)
包含请求的Headers对象
##### integrity : string(只读)
请求的子资源完整性值。
##### method : string(只读)
请求方法
##### mode : string(只读)
请求的模式(例如，`cors`、`no-cors`、`same-origin`、`navigate`)。
##### redirect : 'follow' | 'error' | 'manual'(只读)
包含如何处理重定向的模式
##### referrer : string(只读)
表示用户代理从哪个网站请求的字符串
##### referrerPolicy : string(只读)
包含请求的 referrer 策略
##### signal : AbortSignal(只读)
与请求相关联的`AbortSignal`
##### url : string(只读)
包含请求的URL
#### 实例方法
##### 实现body接口的方法
- arrayBuffer
- blob
- formData
- json
- text
##### clone()
创建当前`Request`对象的副本
