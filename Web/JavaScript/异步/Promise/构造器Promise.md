#### 描述
主要用于封装尚未支持 Promise 的基于回调的 API。

- executor(resolve,reject)
	- 在构造函数中执行的 function。它接收两个函数作为参数：resolve 和 reject。executor 中抛出的任何错误都会导致 Promise 被拒绝，并且返回值将被忽略。
当 `resolveFunc` 或 `rejectFunc` 被调用时，该Promise对象就会变为已解决。但是，如果在调用这两个函数时将另一个Promise对象作为参数，可以说该 Promise 对象“已解决”，但仍未“敲定（settled）”

`executor` 的完成状态对 Promise 的状态影响有限：
- `executor` 函数的返回值会被忽略。`executor` 函数中的 `return` 语句仅影响控制流程，调整函数某个部分是否执行，但不会影响 Promise 的兑现值。如果 `executor` 函数退出，且未来不可能调用 `resolveFunc` 或 `rejectFunc`（例如，没有安排异步任务），那么 Promise 将永远保持待定状态。
- 如果在 `executor` 函数中抛出错误，则 Promise 将被拒绝，除非 `resolveFunc` 或 `rejectFunc` 已经被调用。

以下是典型的 Promise 流程概述：
1. 构造函数在生成新的Promise对象时，会生成一对对应的 `resolveFunc` 和 `rejectFunc` 函数，它们将会作为executor的参数被传入
2. executor是同步调用的，在创建Promise对象时调用
3. 异步操作中最终通过调用 `resolve/reject` 引起的副作用与Promise实例进行通信
	- 只有第一次调用 `resolve/reject` 时会影响Promise实例的最终状态，后面调用的将被忽略
	- 如果 `resolve` 被传入另一个Promise对象，那么该Promise对象会保持待定状态
	- 如果executor抛出错误，则该Promise对象被拒绝。但是，如果 `resolveFunc/rejectFunc` 已经被调用，那么该错误将被忽略
>resolve 和 reject 回调仅在 executor 函数的作用域内可用，这意味着在构造 promise 之后无法访问它们。
>如果你想在决定如何解决之前先构造 promise，可以使用 Promise.withResolvers() 方法，该方法暴露了 resolve and reject 函数。

##### resolve函数
1. 如果它被调用时传入了新建的 Promise 对象本身（即它所“绑定”的 Promise 对象），则 Promise 对象会被拒绝并抛出一个 TypeError 错误。
2. 如果它使用一个非 `thenable` 的值（基本类型，或一个没有 then 属性或 then 属性不可调用的对象），则该 Promise 对象会被立即以该值兑现。
3. 如果它被调用时传入了一个 `thenable` 对象（包括另一个 Promise 实例），则该 `thenable` 对象的 `then` 方法将被保存并在未来被调用（它总是异步调用）。then 方法将被调用并传入两个回调函数，这两个函数的行为与传递给 executor 函数的 resolveFunc 和 rejectFunc 函数完全相同。如果调用 then 方法时出现错误，则当前的 Promise 对象会被拒绝并抛出这个错误。

调用 rejectFunc 函数会导致 Promise 对象被拒绝。然而，即使在调用 resolveFunc 回调函数时，也有两种方法可以使 Promise 对象立即被拒绝。

```
// 1. 传入 Promise 本身
const rejectedResolved1 = new Promise((resolve) => {
  // 注意：resolve 必须异步调用，以便初始化 rejectedResolved1 变量
  setTimeout(() => resolve(rejectedResolved1)); // TypeError: Chaining cycle detected for promise #<Promise>
});

// 2. 传入一个在访问 `then` 属性时抛出异常的对象
const rejectedResolved2 = new Promise((resolve) => {
  resolve({
    get then() {
      throw new Error("无法访问 then 属性");
    },
  });
});
```