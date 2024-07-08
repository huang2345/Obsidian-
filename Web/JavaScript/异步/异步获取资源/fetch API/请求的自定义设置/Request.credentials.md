`Request` 接口的只读属性，用于表示用户代理是否应该在跨域请求下从其他域发送 `cookies`
三个属性：
 - `omit` 
	 - 从不发送cookies
- `same-origin` (默认值)
	- 只有当被请求的URL与响应脚本同源才发送cookies、HTTP Basic authentication 等验证信息A
- `include`
	- 不论是不是跨域的请求，总是发送请求资源域在本地的 cookies、HTTP Basic authentication 等验证信息。