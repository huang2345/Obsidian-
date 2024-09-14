Cache-Control被用于在 http 请求和响应中，通过指定指令来实现缓存机制。
#### 语法
- 不区分大小写
- 多个指令逗号分隔
- 具有可选参数
##### 缓存请求指令
```
Cache-Control: max-age=<seconds>
Cache-Control: max-stale[=<seconds>]
Cache-Control: min-fresh=<seconds>
Cache-control: no-cache
Cache-control: no-store
Cache-control: no-transform
Cache-control: only-if-cached
```
##### 缓存响应指令
```
Cache-control: must-revalidate
Cache-control: no-cache
Cache-control: no-store
Cache-control: no-transform
Cache-control: public
Cache-control: private
Cache-control: proxy-revalidate
Cache-Control: max-age=<seconds>
Cache-control: s-maxage=<seconds>
```
#### 指令
##### 可缓存性
###### public
表示响应可以被任何对象缓存(客户端，代理等等)缓存，即使是通常不可缓存的内容
###### private
表明响应只能被单个用户缓存，不能作为共享缓存(即代理服务器不能缓存)。
###### no-cache
在使用缓存副本之前，强制要求缓存把请求提交给原始服务器进行验证 (协商缓存验证)。
即，不适用未经验证的缓存副本
###### no-store
不使用任何缓存
##### 到期
###### max-age=\<seconds>
设置缓存存储的最大周期，超过这个时间缓存被认为过期。如果设置为0，那么缓存会立即过期。
与`Expires`相反，时间是相对于请求的时间。
###### s-maxage=\<seconds>
覆盖`max-age`或者`Expires`头，但是仅适用于共享缓存(比如各个代理)，私有缓存会忽略它。
###### max-stale\[=\<seconds>]
表示客户端愿意接收过期的资源。可以设置一个可选的秒数，表示该响应过时后的时间不能超过该值
###### min-fresh=\<seconds>
表示客户端希望获取一个能在指定的秒数内保持其最新状态的响应。
##### 重新验证和重新加载
###### must-revalidate
一旦资源过期（比如已经超过`max-age`），在成功向原始服务器验证之前，缓存不能用该资源响应后续请求。
###### proxy-revalidate
与 must-revalidate 作用相同，但它仅适用于共享缓存，并被私有缓存忽略
##### 其他
###### no-transform
不得对资源进行转换或转变。`Content-Encoding`、`Content-Range`、`Content-Type`等 HTTP 头不能由代理修改。例如，非透明代理或者如[Google's Light Mode](https://support.google.com/webmasters/answer/6211428?hl=en)可能对图像格式进行转换，以便节省缓存空间或者减少缓慢链路上的流量。`no-transform`指令不允许这样做。
###### only-if-cached
表明客户端只接受已缓存的响应，并且不向原始服务器检查是否有更新的拷贝。