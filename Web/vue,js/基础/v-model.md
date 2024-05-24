`v-model` 可以用于各种不同类型的输入，`<textarea>`、`<select>` 元素。它会根据所使用的元素自动使用对应的 DOM 属性和事件组合：
- 文本类型的 `<input>` 和 `<textarea>` 元素会绑定 `value` property 并侦听 `input` 事件；
- `<input type="checkbox">` 和 `<input type="radio">` 会绑定 `checked` property 并侦听 `change` 事件；
- `<select>` 会绑定 `value` property 并侦听 `change` 事件。

	`v-model` 会忽略任何表单元素上初始的 `value`、`checked` 或 `selected` attribute。它将始终将当前绑定的 JavaScript 状态视为数据的正确来源。你应该在 JavaScript 中使用[响应式系统的 API](https://cn.vuejs.org/api/reactivity-core.html#reactivity-api-core)来声明该初始值。

##### 修饰符

- `lazy` 改为在每次 `change` 事件后更新数据
- `number`自动转换为数字，type="number"时自动启用，如果该值无法被 `parseFloat()` 处理，那么将返回原始值
-  `.trim`[​](https://cn.vuejs.org/guide/essentials/forms.html#trim)默认自动去除用户输入内容中两端的空格

