`Request` 接口的只读属性，包含请求的模式。这用于确定跨域请求是否能得到有效的响应，以及响应的哪些属性是可读的。

- `same-origin`
	- 请求总是向当前的源发起，如果跨域，显而易见，结果会是一个错误。
- `no-cors`
	- 保证请求对应的 method 只有 `HEAD`，`GET` 或 `POST` 方法，并且请求的 headers 只能有简单请求头 ([simple headers](https://fetch.spec.whatwg.org/#simple-header))。如果 ServiceWorker 劫持了此类请求，除了 [simple header](https://fetch.spec.whatwg.org/#simple-header) 之外，不能添加或修改其他 header。另外 JavaScript 不会读取 [`Response`](https://developer.mozilla.org/zh-CN/docs/Web/API/Response) 的任何属性。这样将会确保 ServiceWorker 不会影响 Web 语义 (semantics of the Web)，同时保证了在跨域时不会发生安全和隐私泄露的问题。
- `cors`
	- 允许跨域请求，例如访问第三方供应商提供的各种 API。预期将会遵守 CORS protocol 。仅有有限部分的头部暴露在 Response ，但是 body 部分是可读的。
- `navigate`
	- 表示这是一个浏览器的页面切换请求 (request)。navigate 请求仅在浏览器切换页面时创建，该请求应该返回 HTML。