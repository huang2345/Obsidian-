表示清除当前请求网站有关的浏览器数据(cookie，存储，缓存)
#### 语法
`Clear-Site-Data` 可以接受一个或多个参数，如果想要清除所有类型的数据，可以使用通配符 (`"*"`)
```
Clear-Site-Data: "cache"
Clear-Site-Data: "cache", "cookies"
Clear-Site-Data: "*"
```
#### 指令
##### "cache"
表示服务端希望删除本 URL 原始响应的本地缓存数据(浏览器缓存)。根据浏览器的不同，可能还会清除预渲染页面，脚本缓存，WebGL 着色器缓存或地址栏建议等内容。
##### "cookies"
表示服务端希望删除 URL 响应的所有 cookie。HTTP 身份验证凭据也会被清除。会影响整个主域，包括子域。
##### "storage"
表示服务端希望删除 URL 原响应的所有 DOM 存储
##### "executionContexts"
表示服务端希望浏览器重新加载本请求