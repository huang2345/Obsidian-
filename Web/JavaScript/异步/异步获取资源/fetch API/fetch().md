Fetch提供了对`Request(请求)`和`Response(响应)`对象的通用定义。
fetch()返回一个Promise，当接受到一个代表错误的HTTP状态码时，该promise**不会被标记为reject**，只有网络故障或请求被阻止时，才会标记为reject
fetch默认不会发送跨域cookie。

fetch有两个参数：
- resource，要获取的资源
	- URL
	- Request对象
- options?，应用到请求上的RequestInit对象