**Promise** 是现代 JavaScript 中异步编程的基础。它是一个由异步函数返回的对象，可以指示操作当前所处的状态。
- 待处理(pending)
- 已兑现(fulfilled)
- 已拒绝(rejected)
如果一个 Promise 已经被兑现或拒绝，即不再处于待定状态，那么则称之为已敲定（settled）。

一个 Promise 的终止条件决定了链中下一个 Promise 的“已敲定”状态。链中每个已兑现的 Promise 的返回值会传递给下一个 `.then()`，已拒绝的 Promise 会把失败原因传递给链中下一个拒绝处理函数。

在 Promise 返回给调用者的时候，操作往往还没有完成，但 Promise 对象提供了方法来处理操作最终的成功或失败。
![](Pasted%20image%2020240908193911.png)
##### Thenable
在Promise成为JS的一部分之前已经有了多种Promise实现。尽管内部的表示方法不同，但至少所有类Promise的对象都实现了**Thenable**接口。
Thenable对象实现了`.then()`方法。Promise也是Thenable对象
```
const aThenable = {
  then(onFulfilled, onRejected) {
    onFulfilled({
      // thenable 对象被兑现为另一个 thenable 对象
      then(onFulfilled, onRejected) {
        onFulfilled(42);
      },
    });
  },
};

Promise.resolve(aThenable); // 一个兑现值为 42 的 Promise
```
为了与现有的 Promise 实现进行交互，JavaScript 语言允许在 Promise 的位置使用 thenable 对象。例如，[`Promise.resolve`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/resolve) 方法不仅可以解析 Promise 对象，还可以追踪 thenable 对象。

#### 链式调用
##### `then`
进行异步处理
两个参数：onFulfilled 和 onRejected
- `onFulfilled` 兑现时执行的异步函数
	- 参数：value，链式调用中上一个Promise的兑现值
- `onRejected` 拒绝时执行的异步函数
	- 参数：reason，Promise对象被拒绝的理由

##### `catch`
处理Promise链上被拒绝的对象
一个参数：onRejected。

##### `finally`
在 promise 敲定时进行一些处理或者清理


#### Promise并发
##### Promise.all()
在**所有**传入的 Promise 都被兑现时兑现；在**任意一个** Promise 被拒绝时拒绝。
##### Promise.allSettled()
在**所有**的 Promise 都被敲定时兑现。
##### Promise.any()
在**任意一个** Promise 被兑现时兑现；仅在**所有**的 Promise 都被拒绝时才会拒绝。
##### Promise.race()
在**任意一个** Promise 被敲定时敲定。换句话说，在**任意一个** Promise 被兑现时兑现；在**任意一个**的 Promise 被拒绝时拒绝。

---
以上方法都接受一个Promise(严格地说是Thenable)的可迭代对象，并返回一个新的Promise。
它们都可以在Promise的子类上调用，结果将是一个属于子类类型的Promise。为此，子类的构造函数必须与Promise()构造函数拥有相同的签名。除此之外，子类还必须有一个resolve静态方法，能想Promise.resolve()一样使用。

>JS的本质是单线程的。在JS中，真正的并行执行只能通过worker线程实现