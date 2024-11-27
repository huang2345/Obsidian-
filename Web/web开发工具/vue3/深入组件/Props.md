#### 声明
一个组件需要显式声明它接收的`Props`，这样Vue才能知道外部传入的哪些是`Prop`，哪些是透传属性。

在使用`<script setup>`的单文件组件中，`Props`可以用`defineProps()`宏来声明：
```vue
<script setup>
const props = defineProps(['foo'])

console.log(props.foo)
</script>
```
在没有使用`<script setup>`的组件中，`Props`可以使用`props`选项来声明：
```js
export default {
  props: ['foo'],
  setup(props) {
    // setup() 接收 props 作为第一个参数
    console.log(props.foo)
  }
}
```
两种声明方式背后其实使用的都是`props`选项。

除了使用字符串数组，还可以使用对象来声明`Props`：
```js
// 使用 <script setup>
defineProps({
  title: String,
  likes: Number
})
```
>对于以对象形式声明的每个属性，`key`是`prop`的名称，而值则是该`prop`预期类型的构造函数。
#### 响应式Props解构
Vue的响应式系统基于属性访问跟踪变量的状态的使用情况。例如，在计算属性或侦听器中访问`props.foo`时，`foo`属性将被跟踪为依赖项。
因此，以下代码：
```js
const { foo } = defineProps(['foo'])

watchEffect(() => {
  // 在 3.5 之前只运行一次
  // 在 3.5+ 中在 "foo" prop 变化时重新执行
  console.log(foo)
})
```
在3.4及以下版本，`foo`是一个常量，永远不会改变。在3.5及以上版本，当在同一个`<script setup>`访问由`defineProps`解构的变量时，Vue编译器会自动在前面添加`props.`。因此，上面的打印语句实际为：`console.log(props.foo)`，实际访问的不是常量`foo`。

可以使用JS原生的默认值语法声明`prop`默认值，这在使用TS时特别有用：
```ts
const { foo = 'hello' } = defineProps<{ foo?: string }>()
```
##### 将解构的Prop传递到需要响应式的变量的函数中
当我们将解构的`Prop`传递到函数中时：
```js
const { foo } = defineProps(['foo'])
watch(foo, /* ... */)
```
这实际上是`watch(props.foo,...)`——给`watch`传递的是一个普通值而不是响应式的数据源，Vue编译器会发出警告。
可以通过将解构后的`Prop`包含在`getter`中来侦听解构的`Prop`：
```js
watch(() => foo, /* ... */)
```
#### 传递Prop的细节
##### 名字格式
一个`prop`应使用`camelCase`形式，因为这是JS的合法标识符。虽然可以在向子组件传递`prop`时使用`camelCase`形式，但是为了与HTML属性对齐，通常将其写为`kebab-case`形式。
##### 使用一个对象绑定多个prop
可以通过使用`v-bind`指令将对象的所有属性都当作`prop`传入
```vue
<script setup>
	const post = {
		id: 1,
		title: 'My Journey with Vue'
	}
</script>
<template>
	<BlogPost v-bind="post" />
</template>
```
#### 单向数据流
所有的`prop`都遵循**单向绑定原则**，`prop`因父组件的更新而更新，不会逆向传递。这避免了子组件意外修改父组件的状态的情况。
>如果试图在子组件中更改一个`prop`，Vue会在控制台发出警告
##### 更改引用类型的prop
虽然子组件无法更改`prop`绑定，但仍然可以更改对象内部的值。对Vue来说，想要阻止这种更改需要付出非常高昂的代价。
在实际操作中，应该避免这样的更改。
#### Prop校验
Vue组件可以声明对传入的Prop的校验，如果传入的值不满足类型要求，Vue会在浏览器控制台中抛出警告。
要声明这种校验，需要向`defineProps()`宏提供一个带有`props`校验选项的对象：
```js
defineProps({
  // 基础类型检查
  // （给出 `null` 和 `undefined` 值则会跳过任何类型检查）
  propA: Number,
  // 多种可能的类型
  propB: [String, Number],
  // 必传，且为 String 类型
  propC: {
    type: String,
    required: true
  },
  // 必传但可为 null 的字符串
  propD: {
    type: [String, null],
    required: true
  },
  // Number 类型的默认值
  propE: {
    type: Number,
    default: 100
  },
  // 对象类型的默认值
  propF: {
    type: Object,
    // 对象或数组的默认值
    // 必须从一个工厂函数返回。
    // 该函数接收组件所接收到的原始 prop 作为参数。
    default(rawProps) {
      return { message: 'hello' }
    }
  },
  // 自定义类型校验函数
  // 在 3.4+ 中完整的 props 作为第二个参数传入
  propG: {
    validator(value, props) {
      // The value must match one of these strings
      return ['success', 'warning', 'danger'].includes(value)
    }
  },
  // 函数类型的默认值
  propH: {
    type: Function,
    // 不像对象或数组的默认，这不是一个
    // 工厂函数。这会是一个用来作为默认值的函数
    default() {
      return 'Default function'
    }
  }
})
```
1. 所有`prop`默认都是可选的，`required:true`选项声明表示必选
2. `Boolean`以外的可选`prop`都有一个默认值`undefined`
3. `Boolean`类型的未传递`prop`将被转换为`false`。
4. 可以通过声明`default`选项来声明默认值