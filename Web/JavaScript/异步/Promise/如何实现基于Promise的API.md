基于回调、计时器延时触发等来包裹一个异步操作，使用 `Promise` 对象来处理操作的成功或失败。

### 实现alarm() API
##### 用setTimeout包裹
用一个函数设置全局计时器，并将这个函数添加到按钮的事件处理函数上。
```
const output = document.querySelector("#output");
const button = document.querySelector("#set-alarm");

function setAlarm() {
  window.setTimeout(() => {
    output.textContent = "Wake up!";
  }, 1000);
}

button.addEventListener("click", setAlarm);
```

#### Promise()构造器
该构造器使用一个函数作为参数，我们称这个函数为 `执行器(executor)`，当使用该执行器的Promise被创建时，该函数将被调用。

执行器本身有两个参数，两个参数都是函数，通常被称为 `resolve`和`reject`。在执行器内中，如果异步函数成功就调用 `resolve` ，如果失败就调用 `reject` 。如果执行器抛出了错误， `reject` 会被自动调用。
> 可以将任何类型的单个参数传递到 `resolve` 和 `reject` 中。

```
function alarm(person, delay) {
  return new Promise((resolve, reject) => {
    if (delay < 0) {
      throw new Error("Alarm delay must not be negative");
    }
    window.setTimeout(() => {
      resolve(`Wake up, ${person}!`);
    }, delay);
  });
}
```

##### 使用API
```
const name = document.querySelector("#name");
const delay = document.querySelector("#delay");
const button = document.querySelector("#set-alarm");
const output = document.querySelector("#output");

function alarm(person, delay) {
  return new Promise((resolve, reject) => {
    if (delay < 0) {
      throw new Error("Alarm delay must not be negative");
    }
    window.setTimeout(() => {
      resolve(`Wake up, ${person}!`);
    }, delay);
  });
}

button.addEventListener("click", () => {
  alarm(name.value, delay.value)
    .then((message) => (output.textContent = message))
    .catch((error) => (output.textContent = `Couldn't set alarm: ${error}`));
});
```