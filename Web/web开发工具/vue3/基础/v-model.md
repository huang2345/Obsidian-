在前端处理表单时，常常需要将表单输入框的内容同步给JS中相应的变量。手动连接值绑定和更改事件监听器可能会很麻烦：
```html
<input
  :value="text"
  @input="event => text = event.target.value">
```
`v-model`指令简化了这一步骤：
```html
<input v-model="text">
```
`v-model`指令可以用于各种不同类型的输入，会根据所使用的元素自动使用对应的 DOM 属性和事件组合：
	1. 文本类型的`<input>`和`<textarea>`元素会绑定`value`属性并侦听`input`事件
	2. `<input type="checkbox">` 和`<input type="radio">`会绑定`checked`属性并侦听`change`事件
	3. `<select>`会绑定`value`属性并侦听`change`事件。
>`v-model`会忽略任何表单元素上初始的`value`、`checked`或`selected`属性。它将始终将当前绑定的JS变量视为数据的正确来源。

##### 多个复选框绑定到同一个数组或集合
```js
const checkedNames = ref([])
```
```html
<div>Checked names: {{ checkedNames }}</div>

<input type="checkbox" id="jack" value="Jack" v-model="checkedNames" />
<label for="jack">Jack</label>

<input type="checkbox" id="john" value="John" v-model="checkedNames" />
<label for="john">John</label>

<input type="checkbox" id="mike" value="Mike" v-model="checkedNames" />
<label for="mike">Mike</label>
```
在这个例子中，`checkedNames`数组将始终包含所有当前被选中的框的值。