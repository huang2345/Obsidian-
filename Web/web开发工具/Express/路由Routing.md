路由是指后端如何根据URI和请求方式响应客户端的请求。

`app.<HTTP请求方法>(path,handle)`
#### 路由方法
路由方法在检测到指定URI的指定请求方法时，调用`handle`
>路由方法可以有多个回调函数作为参数，回调函数需要添加`next`作为参数并在函数体内调用。
##### all
路由方法`all`，会对所有的HTTP请求响应。
#### 路由路径
路由路径可以是字符串、字符串模式或正则表达式。
#### 路由参数
路由参数是命名的`URL`段，用于捕获在`URL`中其位置指定的值。捕获的值填充在 `req.params` 对象中，路径中指定的路由参数的名称作为它们各自的键。

```js
//Request :http://localhost:3000/src/book/10
//req.params :["id":10];
app.get("/src/book/:id",...)
```
由于`-`和`.`是按字面解释的，所以可以将它们与路由参数一起使用。
```js
//Request :http://localhost:3000/100-10
//req.params :["book":100,"id":10];
app.get("src/:book-:id",...);
app.get("src/:book.:id",...);
```
要更好的控制路由参数的值，可以通过在`()`中添加正则表达式来匹配。
`app.get("src/:book-:id(\\d+)`
>由于正则表达式字符串的一部分因此应使用`\`对`\`进行转义，`...(\\d+)`

#### Response
下表中的`Response`对象的方法可以向客户端发送响应并终止请求响应周期。如果`handle`没有调用这些方法，则客户端请求将被挂起。

| 方法         | 描述                 |
| ---------- | ------------------ |
| download   | 提示下载文件             |
| end        | 结束响应               |
| json       | 发送JSON响应           |
| jsonp      | 使用JSONP支持发送JSON    |
| redirect   | 重定向请求              |
| render     | 渲染视图模板             |
| send       | 发送各种类型的响应          |
| sendFile   | 以八位字节流的形式发送文件      |
| sendStatus | 设置响应状态并将其字符串作为响应返回 |
#### 模块化路由
使用 `express.Router` 类创建模块化、可安装的路由处理程序。一个 `Router` 实例是一个完整的中间件和路由系统；因此，它通常被称为“mini-app”。
```js
var express = require('express');
var route = express.Router();
//设置中间件
route.use("/",...);
//设置路由
...
module.exports = route;
```
然后通过在`app`实例上使用`use`将路由注册，在这里给`use`方法传递的`path`将作为路由模块根目录。
##### 链式路由
可以使用`app.route(path)`来为某一路径创建多种HTTP访问时的路由处理：
```js
app.route("/").get(...).post(...) ...;
```
