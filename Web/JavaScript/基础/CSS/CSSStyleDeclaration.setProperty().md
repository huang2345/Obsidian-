该方法接口为一个声明了 CSS 样式的对象设置一个新的值。

- _`propertyName`_ 是一个 [`DOMString`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String) ，代表被更改的 CSS 属性。
- _`value`_可选 是一个 [`DOMString`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String) ，含有新的属性值。如果没有指定，则当作空字符串。
    - 注意：_`value`_ 不能包含 --那个应该使用 _`priority`_ 参数。`"!important"`
- _`priority`_可选 是一个 [`DOMString`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String) 允许设置 "important" CSS 优先级。如果没有指定，则当作空字符串。