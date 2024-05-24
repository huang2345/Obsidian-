reactive({})
ref()
mustache 语法 (即双大括号) 只能用于文本插值.
v-bind指令，如\<div v-bind:id="dynamicId">\</div>
id是指令的“参数”，dynamicId是要设置的属性值，这里引用了对象

`v-on` 指令监听 DOM 事件：
\<button v-on:click="increment">{{ count }}\</button>
简写：
\<button @click="increment">{{ count }}\</button>

`v-model` 会将被绑定的值与 `<input>` 的值自动同步
\<input v-model="xxx"/>

`v-if` 指令来有条件地渲染(显示)元素：
awesome是bool值
\<h1 v-if="awesome">Vue is awesome!\</h1>
v-else是否渲染(显示)与上一个v-if有关

使用 `v-for` 指令在\<template>标签中使用for-in循环
key是一个vue特殊的内置属性，可以用它在v-for中为数组元素设置id

在没有 key 的情况下，Vue 将使用一种最小化元素移动的算法，并尽可能地就地更新/复用相同类型的元素。如果传了 key，则将根据 key 的变化顺序来重新排列元素，并且将始终移除/销毁 key 已经不存在的元素。

同一个父元素下的子元素必须具有**唯一的 key**。重复的 key 将会导致渲染异常。

computed()，可以创建一个计算属性ref，其参数为回调函数，返回回调函数的返回值。
计算属性会自动跟踪其计算中所使用的到的其他响应式状态，并将它们收集为自己的依赖。计算结果会被缓存，并只有在其依赖发生改变时才会被自动更新。

这个ref会动态的根据回调函数使用的响应式数据来计算value

```
const fi = computed(()=>{
  return hideCompleted.value?todos.value.filter((t)=>{
    if(t.done == false)
      return t;
  }):todos.value;
})


const filteredTodos = computed(() => {
  return hideCompleted.value
    ? todos.value.filter((t) => !t.done)
    : todos.value
})
以上两种写法作用相同
```


手动操作DOM，模板引用指向模板中一个 DOM 元素的 ref。我们需要通过这个特殊的ref属性来实现模板引用。
\<p ref="xxx">\</p>
要访问该引用，我们需要声明一个同名的 ref：

```
const pElementRef = ref(null)
```

注意这个 ref 使用 `null` 值来初始化。这是因为当 `<script setup>` 执行时，DOM 元素还不存在。模板引用 ref 只能在组件**挂载**后访问。
要在挂载之后执行代码，我们可以使用 `onMounted()` 函数：

```
import { onMounted } from 'vue'

onMounted(() => {
  // 此时组件已经挂载。
  // 通过pElementRef属性手动对DOM元素进行操作
})
```

这被称为**生命周期钩子**——它允许我们注册一个在组件的特定生命周期调用的回调函数。还有一些其他的钩子如 `onUpdated` 和 `onUnmounted`。


侦听器watch
watch(count,callback)，可以侦听一个ref，只要count的值改变就会触发回调函数

通过import导入组件，可以在模板中渲染该组件
```
import ChildComp from './ChildComp.vue'
...
<template>
	<ChildComp />
</template>
```

# Props

子组件可以通过 **props** 从父组件接受动态数据。首先，需要声明它所接受的 props：
```
<!-- ChildComp.vue -->
<script setup>
const props = defineProps({
  msg: String
})
</script>
```
注意 `defineProps()` 是一个编译时宏，并不需要导入。一旦声明，`msg` 就可以在子组件的模板中使用。它也可以通过 `defineProps()` 所返回的对象在 JavaScript 中访问。

父组件可以像声明 HTML attributes 一样传递 props。若要传递动态值，也可以使用 `v-bind` 语法：
`传递的属性值最好是对象，因为defineProps()宏在参数中设置要接受的数据的类型没有基础数据类型`
```
<ChildComp :msg="greeting" />
```


# Emits

除了接收 props，子组件还可以向父组件触发事件：
```
<script setup>
// 声明触发的事件
const emit = defineEmits(['response'])

// 带参数触发
emit('response', 'hello from child')
</script>
```

`emit()` 的第一个参数是事件的名称。其他所有参数都将传递给事件响应函数。

父组件可以使用 `v-on` 监听子组件触发的事件——这里的处理函数接收了子组件触发事件时的额外参数并将它赋值给了本地状态：

`msg是调用emit时的第二个参数`
```
<ChildComp @response="(msg) => childMsg = msg" />
```


# 插槽

除了通过 props 传递数据外，父组件还可以通过**插槽** (slots) 的将模板片段传递给子组件：

```
<ChildComp>
  This is some slot content!
</ChildComp>
以上这种方法叫插槽
```

在子组件中，可以使用 `<slot>` 元素作为插槽出口 (slot outlet) 渲染父组件中的插槽内容 (slot content)：

```
<!-- 在子组件的模板中 -->
<slot/>
```

`<slot>` 插口中的内容将被当作“默认”内容：它会在父组件没有传递任何插槽内容时显示：
```
<slot>Fallback content</slot>
```

由于在`template`元素中，解析时大写自动转为小写，所以渲染其他组件时，若导入时设置的组件名有大写，则写法为在大写字母前添加`-`（除了首字母