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
	2. `<input type="checkbox">` 和`<input type="radio">`会绑定`value`属性并侦听`change`事件
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
##### 复选框
`true-value`和`false-value`是`vue`特有的属性，只能和`v-model`配套使用。这两个属性可以指定`v-model`绑定的变量的值。
```html
<!-- 选中时设为yes，取消时设为no-->
<input
  type="checkbox"
  v-model="toggle"
  true-value="yes"
  false-value="no" />
```
#### 修饰符
##### .lazy
默认情况下，`v-model`会在每次`input`事件后更新数据。可以添加该修饰符来改为在每次`change`事件后更新。
##### .number
让用户输入自动转换为数字。如果该值无法被`parseFloat()`处理，那么将返回原始值。该修饰符会在输入框有`type="number"`时自动启用。
##### .trim
自动去除用户输入内容中两端的空格。