**Proxy** 对象用于创建一个对象的代理，从而实现基本操作的拦截和自定义（如属性查找、赋值、枚举、函数调用等）。
- `target` 需要代理的对象
- `handler` 处理器，内含 handler.xxxx()等的捕捉器。所有的捕捉器都是可选的。如果没有定义某个捕捉器，那么就会保留源对象的默认行为。
> `handler`对象的方法,各种捕捉器
>  `get/set`
###### 无操作转发代理
在以下例子中，我们使用了一个原生 JavaScript 对象，代理会将所有应用到它的操作转发到这个对象上。
```
let target = {};
let p = new Proxy(target, {});

p.a = 37; // 操作转发到目标

console.log(target.a); // 37. 操作已经被正确地转发
```
### 验证
通过代理，你可以轻松地验证向一个对象的传值。下面的代码借此展示了 [`set`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Proxy/Proxy/set) handler 的作用。
```
let validator = {
  set: function (obj, prop, value) {
    if (prop === "age") {
      if (!Number.isInteger(value)) {
        throw new TypeError("The age is not an integer");
      }
      if (value > 200) {
        throw new RangeError("The age seems invalid");
      }
    }

    // The default behavior to store the value
    obj[prop] = value;

    // 表示成功
    return true;
  },
};

let person = new Proxy({}, validator);

person.age = 100;

console.log(person.age);
// 100

person.age = "young";
// 抛出异常：Uncaught TypeError: The age is not an integer

person.age = 300;
// 抛出异常：Uncaught RangeError: The age seems invalid
```

### 可撤销的 `Proxy`
可以用 [`Proxy.revocable()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Proxy/revocable) 方法来创建可撤销的 `Proxy` 对象。这意味着可以通过 `revoke` 函数来撤销并关闭一个代理。

此后，对代理进行的任意的操作都会导致 [`TypeError`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/TypeError)。
```
const revocable = Proxy.revocable(
  {},
  {
    get(target, name) {
      return `[[${name}]]`;
    },
  },
);
const proxy = revocable.proxy;
console.log(proxy.foo); // "[[foo]]"

revocable.revoke();
// TypeError: Cannot perform 'get' on a proxy that has been revoked
console.log(proxy.foo); 
// TypeError: Cannot perform 'set' on a proxy that has been revoked
proxy.foo = 1; 
// TypeError: Cannot perform 'deleteProperty' on a proxy that has been revoked
delete proxy.foo; 
console.log(typeof proxy); // "object", `typeof` 不会触发任何陷阱
```