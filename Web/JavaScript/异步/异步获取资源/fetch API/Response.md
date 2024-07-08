[Fetch API](https://developer.mozilla.org/zh-CN/docs/Web/API/Fetch_API) 的 `Response` 接口呈现了对一次请求的响应数据。

你可以使用 [`Response.Response()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Response/Response) 构造函数来创建一个 `Response` 对象，但通常更可能遇到的情况是，其他的 API 操作返回了一个 Response 对象。例如一个 service worker 的 [`Fetchevent.respondWith`](https://developer.mozilla.org/zh-CN/docs/Web/API/FetchEvent/respondWith)，或者一个简单的 [`GlobalFetch.fetch()`](https://developer.mozilla.org/zh-CN/docs/Web/API/fetch)。

## 属性

 - [`Response.headers`](https://developer.mozilla.org/zh-CN/docs/Web/API/Response/headers) 只读
	包含此 Response 所关联的 [`Headers`](https://developer.mozilla.org/zh-CN/docs/Web/API/Headers) 对象。

 - [`Response.ok`](https://developer.mozilla.org/zh-CN/docs/Web/API/Response/ok) 只读
	包含了一个布尔值，标示该 Response 成功（HTTP 状态码的范围在 200-299）。

 - [`Response.redirected`](https://developer.mozilla.org/zh-CN/docs/Web/API/Response/redirected) 只读
	表示该 Response 是否来自一个重定向，如果是的话，它的 URL 列表将会有多个条目。

- [`Response.status`](https://developer.mozilla.org/zh-CN/docs/Web/API/Response/status) 只读
	包含 Response 的状态码（例如 `200` 表示成功）。

- [`Response.statusText`](https://developer.mozilla.org/en-US/docs/Web/API/Response/statusText "此页面目前仅提供英文版本") 只读
	包含了与该 Response 状态码一致的状态信息（例如，OK 对应 `200`）。

- [`Response.type`](https://developer.mozilla.org/zh-CN/docs/Web/API/Response/type) 只读
	包含 Response 的类型（例如，`basic`、`cors`）。

- [`Response.url`](https://developer.mozilla.org/zh-CN/docs/Web/API/Response/url) 只读
	包含 Response 的 URL。

- `Response.useFinalURL`
	包含了一个布尔值，来标示这是否是该 Response 的最终 URL。

`Response` 实现了 `Body` 接口，所以以下属性亦可用：

- [`Response.body`](https://developer.mozilla.org/zh-CN/docs/Web/API/Response/body) 只读
	一个简单的 getter，用于暴露一个 [`ReadableStream`](https://developer.mozilla.org/zh-CN/docs/Web/API/ReadableStream) 类型的 body 内容。

- [`Response.bodyUsed`](https://developer.mozilla.org/zh-CN/docs/Web/API/Response/bodyUsed) 只读
	包含了一个[`布尔值`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean "此页面目前仅提供英文版本")来标示该 Response 是否读取过 `Body`。
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
