[Fetch API](https://developer.mozilla.org/zh-CN/docs/Web/API/Fetch_API) 的 `Response` 接口呈现了对一次请求的响应数据。

可以用 `Response.Response()` 构造函数来创建一个 `Response` 对象，但一般都是其他的 API 操作返回了一个 Response 对象。例如一个 service worker 的 [`Fetchevent.respondWith`](https://developer.mozilla.org/zh-CN/docs/Web/API/FetchEvent/respondWith)，或者一个简单的 [`GlobalFetch.fetch()`](https://developer.mozilla.org/zh-CN/docs/Web/API/fetch)。
## 属性

 - `Response.headers:Headers` 只读
	包含此 Response 所关联的 `Headers` 对象。

 - `Response.ok:boolean` 只读
	包含一个布尔值，标示该 Response 成功（HTTP 状态码的范围在 200-299）。

 - `Response.redirected:boolean` 只读
	表示该 Response 是否来自一个重定向，如果是的话，该属性值为true并且它的 URL 列表将会有多个条目。

- `Response.status:number` 只读
	包含 Response 的状态码（例如 `200` 表示成功）。

- `Response.statusText` 只读
	包含了与该 Response 状态码一致的状态信息（例如，OK 对应 `200`）。

- `Response.type` 只读
	该属性包含一种响应的类型：
	- basic：标准值，同源响应，暴露除了“Set-Cookie”之外的所有标头。
	- cors：从有效的跨源请求接收到响应。某些标头和主体可以被访问
	- error：网络错误。没有有用的描述错误的信息。响应的状态为 0，header 为空且不可变。这是从 `Response.error()` 中获得的响应的类型。
	- opaque：对跨源资源的"no-cors"请求的响应
	- opaqueredirect：fetch 请求是通过 `redirect: "manual"` 发出的。响应的状态是 0，标头是空的，主体是 null，trailer 是空的。
- `Response.url` 只读
	包含 Response 的 URL。

- `Response.useFinalURL`
	包含了一个布尔值，来标示这是否是该 Response 的最终 URL。

`Response` 实现了 `Body` 接口，所以以下属性亦可用：

- `Response.body` 只读
	一个简单的 getter，用于暴露一个 `ReadableStream` 类型的 body 内容。

- `Response.bodyUsed`只读
	包含了一个布尔值来标示该 Response 是否读取过 `Body`。一个Response的body只能被读取一次
## 方法
`Response.clone()`
创建一个 `Response` 对象的克隆。

`Response.error()`
返回一个绑定了网络错误的新的 `Response` 对象。

`Response.redirect()`
用另一个 URL 创建一个新的 `Response`。

`Response` 实现了 `Body` 接口，所以以下方法同样可用：
- `Body.arrayBuffer()` 返回一个解析为ArrayBuffer格式的Promise
- `Body.blob()`
- `Body.formData()`
- `Body.json()`
- `Body.text()`
