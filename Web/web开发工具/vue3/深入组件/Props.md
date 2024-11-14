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
##### 