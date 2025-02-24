虽然Vue的声明式渲染模型抽象了大部分对DOM的直接操作，但在某些情况下，任然需要直接访问底层DOM元素。要实现这一点，可以使用特殊的==ref属性==。
```html
<input ref="input">
```
`ref`是一个特殊的属性，使我们在一个特定的DOM元素或子组件实例被挂载后，获取到它的直接引用。
#### 访问模版引用
在组合式API中，可以使用`useTemplateRef`来获取
```vue
<script setup>
import { useTemplateRef, onMounted } from 'vue'

// 第一个参数必须与模板中的 ref 值匹配
const input = useTemplateRef('my-input')

onMounted(() => {
  input.value.focus()
})
</script>

<template>
  <input ref="my-input" />
</template>
```
>只能在组件挂载后才能访问模版引用，在挂载前引用为`null`

#### v-for中的模版引用
在有`v-for`指令的元素上使用模版引用时，`useTemplateRef`对应的`ref`中包含的值是一个数组，其包含挂载后对应整个列表的所有元素。
>`ref`数组不保证与源数组相同的顺序
#### 函数模版引用
`ref`属性的值除了是作为名字的字符串，还可以绑定一个函数，会在每次组件更新时调用。该函数接收DOM元素引用作为第一个参数：
```html
<input :ref="(el) => { /* 将 el 赋值给一个数据属性或 ref 变量 */ }">
```
>需要使用动态的`v-bind`绑定才可以传入一个函数。当绑定的元素被卸载时，函数也会被调用一次，此时的`el`参数为`null`
#### 组件上的ref
模版引用也可以被用在一个子组件上。
```vue
<script setup>
import { useTemplateRef, onMounted } from 'vue'
import Child from './Child.vue'

const childRef = useTemplateRef('child')

onMounted(() => {
  // childRef.value 将持有 <Child /> 的实例
})
</script>

<template>
  <Child ref="child" />
</template>
```
如果一个子组件使用选项式API或是没有使用`<script setup>`，那么获取的组件实例会和该子组件的`this`完全相同。这意味着父组件对子组件有完全的访问权，因此只在绝对需要时才使用组件引用。
大多数情况下，应该使用`props`和`emit`接口实现父子组件交互。
##### 使用了`<script setup>`的子组件
使用了`<script setup>`的组件是**默认私有**的，父组件无法访问除了通过`defineExpose`宏显示暴露以外的任何东西：
```html
<script setup>
import { ref } from 'vue'

const a = 1
const b = ref(2)

// 像 defineExpose 这样的编译器宏不需要导入
defineExpose({
  a,
  b
})
</script>
```
	当父组件通过模版引用获取该组件的实例时，得到`{a:number,b:number}`