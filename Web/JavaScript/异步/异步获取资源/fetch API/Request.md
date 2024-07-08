[Fetch API](https://developer.mozilla.org/zh-CN/docs/Web/API/Fetch_API) 的 **`Request`** 接口用来表示资源请求。

你可以使用 [`Request()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Request/Request "Request()") 构造函数创建一个新的 `Request` 对象，但是你更可能会遇到作为其他 API 操作结果返回的 Request 对象，比如 service worker 的 [`FetchEvent.request`](https://developer.mozilla.org/zh-CN/docs/Web/API/FetchEvent/request)。

## 实例属性

[`Request.body`](https://developer.mozilla.org/zh-CN/docs/Web/API/Request/body) 只读
主体内容的 [`ReadableStream`](https://developer.mozilla.org/zh-CN/docs/Web/API/ReadableStream)。

[`Request.bodyUsed`](https://developer.mozilla.org/zh-CN/docs/Web/API/Request/bodyUsed) 只读
存储 `true` 或 `false`，以指示请求是否仍然未被使用。

[`Request.cache`](https://developer.mozilla.org/zh-CN/docs/Web/API/Request/cache) 只读
包含请求的缓存模式（例如，`default`、`reload`、`no-cache`）。

[`Request.credentials`](https://developer.mozilla.org/zh-CN/docs/Web/API/Request/credentials) 只读
包含请求的凭据（例如，`omit`、`same-origin`、`include`）。默认是 `same-origin`。

[`Request.destination`](https://developer.mozilla.org/en-US/docs/Web/API/Request/destination "此页面目前仅提供英文版本") 只读
返回一个描述请求的目的字符串。这是一个字符串，指示所请求的内容类型。

[`Request.headers`](https://developer.mozilla.org/zh-CN/docs/Web/API/Request/headers) 只读
包含请求相关联的 [`Headers`](https://developer.mozilla.org/zh-CN/docs/Web/API/Headers) 对象。

[`Request.integrity`](https://developer.mozilla.org/en-US/docs/Web/API/Request/integrity "此页面目前仅提供英文版本") 只读
包含请求的[子资源完整性](https://developer.mozilla.org/zh-CN/docs/Web/Security/Subresource_Integrity)值（例如 `sha256-BpfBw7ivV8q2jLiT13fxDYAe2tJllusRSZ273h2nFSE=`）。

[`Request.method`](https://developer.mozilla.org/zh-CN/docs/Web/API/Request/method) 只读
包含请求的方法（`GET`、`POST` 等）。

[`Request.mode`](https://developer.mozilla.org/zh-CN/docs/Web/API/Request/mode) 只读
包含请求的模式（例如，`cors`、`no-cors`、`same-origin`、`navigate`）。

[`Request.redirect`](https://developer.mozilla.org/en-US/docs/Web/API/Request/redirect "此页面目前仅提供英文版本") 只读
包含如何处理重定向的模式。它可能是 `follow`、`error` 或 `manual` 之一。

[`Request.referrer`](https://developer.mozilla.org/en-US/docs/Web/API/Request/referrer "此页面目前仅提供英文版本") 只读
包含请求的 referrer（例如，`client`）。

[`Request.referrerPolicy`](https://developer.mozilla.org/en-US/docs/Web/API/Request/referrerPolicy "此页面目前仅提供英文版本") 只读
包含请求的 referrer 策略（例如，`no-referrer`）。

[`Request.signal`](https://developer.mozilla.org/en-US/docs/Web/API/Request/signal "此页面目前仅提供英文版本") 只读
返回与请求相关联的 [`AbortSignal`](https://developer.mozilla.org/zh-CN/docs/Web/API/AbortSignal)。

[`Request.url`](https://developer.mozilla.org/en-US/docs/Web/API/Request/url "此页面目前仅提供英文版本") 只读
包含请求的 URL。

## 实例方法

- `Request.arrayBuffer()`
	返回 promise，其兑现值为请求主体的 [`ArrayBuffer`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer) 表示形式。
- `Request.blob()`
- `Request.clone()` 创建一个当前对象的副本
- `Request.formData()`
- `Request.json()`
- `Request.text()`