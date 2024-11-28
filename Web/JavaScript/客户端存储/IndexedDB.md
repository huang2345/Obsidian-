Web存储只能存储简单的键值对，因此提供了该API来存储较为复杂的数据。
IndexedDB是一个事务型数据库系统，类似基于SQL的RDBMS。但是IndexedDB是一个基于JS的面向对象数据库。
#### open请求
为了获取数据库的访问权限，需要调用`window.indexedDB`属性的`open(name:string,version:number)`，该方法返回一个`IDBOpenDBRequest`对象
>第二个参数是数据库的版本号。

如果数据库不存在，`open`操作会创建该数据库，然后触发`onupgradeneeded`事件，开发者需要在该事件的处理器中创建数据库模式。
如果数据库存在，但是指定了更高的版本号，会直接触发`onupgradeneeded`事件，允许你在处理器中更新数据库模式
>版本号是一个`unsigned long long`数字，这意味着版本号可以很大，但是不能使用小数
```js
let db;
const request = indexedDB.open("MyTestDatabase");
request.onerror = (event) => {
  console.error("为什么不允许我的 web 应用使用 IndexedDB！");
};
request.onsuccess = (event) => {
  db = event.target.result;
};

```