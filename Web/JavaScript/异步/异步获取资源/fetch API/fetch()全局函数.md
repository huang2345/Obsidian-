用于发起获取资源的请求，它会返回一个会在请求响应后兑现的 promise。
该 promise 会兑现一个表示请求响应的 [`Response`](https://developer.mozilla.org/zh-CN/docs/Web/API/Response) 对象。

当遇到网络错误（因为权限或其他类似的问题）时，`fetch()` 返回的 promise 才会被拒绝。`fetch()` 的 promise 不会因为 HTTP 错误而被拒绝（比如 `404`、`504`，等）。因此，`then()` 处理器必须检查 `Response.ok`和/或 `Response.status`属性。只要服务器返回了信息，那么promise进入兑现状态。

> `fetch()` 方法由 [Content Security Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy "此页面目前仅提供英文版本") 的 `connect-src` 指令控制，而不是它请求的资源。

##### 请求的自定义设置
fetch有两种方法可以设置请求的自定义设置：
1. 使用第二个参数 `option` 设置
2. 第一个参数使用 `Request` 对象，在 new `Request` 时使用第二个参数
###### 两种方法的区别
1. 使用 `Request` 对象创建的请求可以多次复用
2. `Request` 对象 中的自定义设置会被 `option` 参数设置的覆盖
## 参数
- `resource`
	- 一个字符串或任何其他具有 [stringifier](https://developer.mozilla.org/en-US/docs/Glossary/Stringifier "此页面目前仅提供英文版本") 的对象，包括 [`URL`](https://developer.mozilla.org/zh-CN/docs/Web/API/URL) 对象——提供你想要获取的资源的 URL。
	- 一个Request对象
- `options`
	- `body`
		- 想要添加到请求中的任意消息主体：可以是一个 `Blob`、`ArrayBuffer`、`TypedArray`、`DataView`、`FormData`、`URLSearchParams`、字符串对象或者字符串字面量，或者 [`ReadableStream`](https://developer.mozilla.org/zh-CN/docs/Web/API/ReadableStream) 对象。注意 `GET` 或 `HEAD` 方法的请求不能包含消息主体。
	- [`browsingTopics`](https://developer.mozilla.org/zh-CN/docs/Web/API/fetch#browsingtopics) 实验性
		- 布尔值，表示当前用户选择的主题是否应该在关联请求的 [`Sec-Browsing-Topics`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Sec-Browsing-Topics "此页面目前仅提供英文版本") 标头中发送。有关更多详细信息，请参阅[使用 Topics API](https://developer.mozilla.org/en-US/docs/Web/API/Topics_API/Using "此页面目前仅提供英文版本")。
	- [`cache`](https://developer.mozilla.org/zh-CN/docs/Web/API/fetch#cache)
		- 字符串，表示请求如何与浏览器的 [HTTP 缓存](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Caching)进行交互。可能的值有 `default`、`no-store`、`reload`、`no-cache`、`force-cache` 和 `only-if-cached`，这些取值在 [`Request`](https://developer.mozilla.org/zh-CN/docs/Web/API/Request) 对象的 [`cache`](https://developer.mozilla.org/zh-CN/docs/Web/API/Request/cache "cache") 属性的文档中有记录。
	- [`credentials`](https://developer.mozilla.org/zh-CN/docs/Web/API/fetch#credentials)
		- 控制浏览器如何处理凭据（[cookie](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Cookies)、[HTTP authentication](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Authentication) 条目和 TLS 客户端证书）。必须是以下字符串之一：
			- `omit`：告诉浏览器在请求中排除凭据，并忽略响应中发送的任何凭据（例如，任何 [`Set-Cookie`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Set-Cookie) 标头）。
			- `same-origin`：告诉浏览器在请求同源 URL 时包含凭据，并使用来自同源 URL 响应中返回的凭据。**这是默认值。**
			- `include`：告诉浏览器在同源和跨源请求中都包含凭据，并始终使用响应中返回的凭据。
	- `header`
		- 任意你想要附加到请求的标头，可以是 [`Headers`](https://developer.mozilla.org/zh-CN/docs/Web/API/Headers) 对象或者带有[`字符串`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String)值的对象字面量。注意[有些标头是被禁止的](https://developer.mozilla.org/zh-CN/docs/Glossary/Forbidden_header_name)
		> **备注：** 请求中可能会有 [`Authorization`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Authorization) HTTP 标头，但是如果请求跨源重定向的话就会被删除。

	- [`integrity`](https://developer.mozilla.org/zh-CN/docs/Web/API/fetch#integrity)
		- 包含请求的[子资源完整性](https://developer.mozilla.org/zh-CN/docs/Web/Security/Subresource_Integrity)值（比如 `sha256-BpfBw7ivV8q2jLiT13fxDYAe2tJllusRSZ273h2nFSE=`）。
	- [`keepalive`](https://developer.mozilla.org/zh-CN/docs/Web/API/fetch#keepalive)
		- `keepalive` 选项可以允许请求持续保持连接，甚至页面已经关闭的情况。使用 `keepalive` 标志的 Fetch 是 [`Navigator.sendBeacon()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Navigator/sendBeacon) API 的一种替代方案。

	- [`method`](https://developer.mozilla.org/zh-CN/docs/Web/API/fetch#method)
		- 请求的方法，比如 `"GET"`、`"POST"`，默认值是 `"GET"`。注意 [`HEAD`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/HEAD) 或者 [`GET`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/GET) 的 Fetch 请求不会设置 [`Origin`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Origin) 标头（此行为已在 Firefox 65 中修正——参见 [Firefox bug 1508661](https://bugzil.la/1508661)）。不区分大小写的情况下能匹配上 [RFC 9110](https://www.rfc-editor.org/rfc/rfc9110#name-overview) 中的任意字符串都会自动被转成大小。如果你想使用自定义的方法（比如 `PATCH`），你应该将它变为大写。
	- [`mode`](https://developer.mozilla.org/zh-CN/docs/Web/API/fetch#mode)
		- 你想要使用的模式，比如 `cors`、`no-cors` 或 `same-origin`。

	- [`priority`](https://developer.mozilla.org/zh-CN/docs/Web/API/fetch#priority)
		- 指定相对于其他同类型的请求的 fetch 请求的优先级。必须是以下字符串之一：
			- [`high`](https://developer.mozilla.org/zh-CN/docs/Web/API/fetch#high)
				- 相对于其他同类型的请求而言，这是一个高优先级的 fetch 请求。
			- [`low`](https://developer.mozilla.org/zh-CN/docs/Web/API/fetch#low)
				- 相对于其他同类型的请求而言，这是一个低优先级的 fetch 请求。
			- [`auto`](https://developer.mozilla.org/zh-CN/docs/Web/API/fetch#auto)
				- 自动确定相对于同类型的其他请求的 fetch 请求的优先级（默认）。

	- [`redirect`](https://developer.mozilla.org/zh-CN/docs/Web/API/fetch#redirect)
		- 如何处理重定向（`redirect`）响应：
			- [`follow`](https://developer.mozilla.org/zh-CN/docs/Web/API/fetch#follow)
				- 自动跟随重定向。除非另有说明，否则重定向模式设置为 `follow`。
			- [`error`](https://developer.mozilla.org/zh-CN/docs/Web/API/fetch#error)
				- 如果发生重定向，则中止并显示错误。
			- [`manual`](https://developer.mozilla.org/zh-CN/docs/Web/API/fetch#manual)
				- 调用者打算在另一个上下文中处理响应。详细信息请参阅 [WHATWG fetch 规范](https://fetch.spec.whatwg.org/#concept-request-redirect-mode)。
	- [`referrer`](https://developer.mozilla.org/zh-CN/docs/Web/API/fetch#referrer)
		- 一个指定请求的引用者的字符串。这可以是同源 URL、`about:client` 或空字符串。
	- [`referrerPolicy`](https://developer.mozilla.org/zh-CN/docs/Web/API/fetch#referrerpolicy)
		- 指定请求所使用的 [referrer policy](https://w3c.github.io/webappsec-referrer-policy/#referrer-policies)。可能是以下其中之一 `no-referrer`、`no-referrer-when-downgrade`、`same-origin`、`origin`、`strict-origin`、`origin-when-cross-origin`、`strict-origin-when-cross-origin` 或者 `unsafe-url`。
	- [`signal`](https://developer.mozilla.org/zh-CN/docs/Web/API/fetch#signal)
		- 一个 [`AbortSignal`](https://developer.mozilla.org/zh-CN/docs/Web/API/AbortSignal) 对象实例；允许你通过 [`AbortController`](https://developer.mozilla.org/zh-CN/docs/Web/API/AbortController) 与 fetch 请求进行通信，并在需要时中止请求。