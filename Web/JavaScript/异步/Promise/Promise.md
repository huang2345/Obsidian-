**Promise** 是现代 JavaScript 中异步编程的基础。它是一个由异步函数返回的对象，可以指示操作当前所处的状态。
- 待处理(pending)
- 已兑现(fulfilled)
- 已拒绝(rejected)
如果一个 Promise 已经被兑现或拒绝，即不再处于待定状态，那么则称之为已敲定（settled）。

一个 Promise 的终止条件决定了链中下一个 Promise 的“已敲定”状态。链中每个已兑现的 Promise 的返回值会传递给下一个 .then()，而已拒绝的 Promise 会把失败原因传递给链中下一个拒绝处理函数。

在 Promise 返回给调用者的时候，操作往往还没有完成，但 Promise 对象提供了方法来处理操作最终的成功或失败。
#### 链式调用
##### `then`
进行异步处理
两个参数：onFulfilled 和 onRejected
- `onFulfilled` 兑现时执行的异步函数
	- 参数：value，链式调用中上一个返回的兑现值
- `onRejected` 拒绝时执行的异步函数
	- 参数：reason，Promise对象被拒绝的理由

##### `catch`
处理Promise链上被拒绝的对象
一个参数：onRejected。

##### `finally`
在 promise 敲定时进行一些处理或者清理


#### 静态方法
##### Promise.all
接收一个Promise数组，返回一个单一的Promise
当数组中所有的Promise都被兑现时，才通知then()处理函数并提供一个包含所有响应的数组。数组中响应的顺序与被传入 all() 的 Promise 的顺序相同。
