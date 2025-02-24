### 基本用法
`v-model`可以在组件上使用以实现双向绑定(同步父子组件的某个变量)。
从Vue3.4开始，推荐使用`defineModel()`宏
```vue
<!-- 子组件 -->
<script setup>
	const model = defineModel();
</script>
<template>
	<input v-model="model" type="text"/>
</template>
<!-- 父组件 -->
<script setup>
let text = ref("hello");
</script>
<Child v-model="text"/>
```
`defineModel()`宏返回的值是一个`ref`，它能起到双向绑定的作用：
	1. 它的`.value`与父组件的`v-model`的值同步
	2. 更改时，会触发父组件绑定的值一起更新
#### defineModel的底层机制
`defineModel`实际上使用`props`和事件来双向绑定，编译器将其展开为：
- 一个名为`modelValue`的 prop，ref的值与其同步；
- 一个名为`update:modelValue`的事件，当本地ref的值发生变更时触发。

因为`defineModel`声明了一个`prop`，可以通过给`defineModel`传递选项，来声明`modelValue`的选项：
```js
// 使 v-model 必填
const model = defineModel({ required: true })

// 提供一个默认值
const model = defineModel({ default: 0 })
```
### 多个v-model绑定
#### v-model的参数
组件上的`v-model`可以接受一个参数：
```vue
<!-- title是参数-->
<MyComponent v-model:title="bookTitle" />
```
子组件通过传入一个相同的字符串来支持相应的参数：
```js
const model = defineModel('title');
```
单独使用参数似乎没什么用，但是可以通过参数来绑定多个`v-model`
#### 利用参数绑定多个v-model
```vue
<UserName
  v-model:first-name="first"
  v-model:last-name="last"
/>
<!-- 子组件 -->
<script setup>
const firstName = defineModel('firstName')
const lastName = defineModel('lastName')
</script>

<template>
  <input type="text" v-model="firstName" />
  <input type="text" v-model="lastName" />
</template>
```