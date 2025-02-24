#### 基础使用
通过该指令来遍历数组来渲染一个列表。`v-for`指令的值需要使用`item in items`形式的特殊语法。
>也可以是更贴近JS语法的：`item of items`

在`v-for`块中可以完整地访问父作用域内的属性和变量。`v-for`也支持使用可选的第二个参数表示当前项的位置索引。
```html
<li v-for="(item, index) in items">
  {{ parentMessage }} - {{ index }} - {{ item.message }}
</li>
...
<li v-for="item in items">
  <span v-for="childItem in item.children">
    {{ item.message }} {{ childItem }}
  </span>
</li>
```
>同样可以在`<template>`中使用
#### 遍历对象
可以使用`v-for`来遍历一个对象的所有属性，遍历的顺序取决于对该对象调用`Object.values()`的返回值。
第二个参数表示属性名，第三个参数表示下标。
```html
<ul>
  <li v-for="value in myObject">
    {{ value }}
  </li>
</ul>
...
<li v-for="(value, key) in myObject">
  {{ key }}: {{ value }}
</li>
```
#### 使用范围值
`v-for`可以直接接收一个整数值。在这种用例中，会将该模板基于 `1...n` 的取值范围重复多次。
```html
<span v-for="n in 10">{{ n }}</span>
```
#### 通过key管理状态
`vue`默认按照**就地更新**的策略来更新`v-for`指令渲染的列表。当数据项的顺序改变时，`vue`不会移动DOM元素的顺序，而是就地更新。
为了给Vue一个提示，以便它可以跟踪每个节点的标识，从而重用和重新排序现有的元素，你需要为每个元素对应的块提供一个唯一的特殊的属性：==key==。
```html
<div v-for="item in items" :key="item.id">
  <!-- 内容 -->
</div>
```
#### 在组件上使用v-for
可以直接在组件上使用`v-for`，和在一般的元素上使用没有区别。但是不会自动将任何数据传递给组件，因为组件有独立的作用域。为了将迭代后的数据传递给组件，可以传递prop
```html
<MyComponent
  v-for="(item, index) in items"
  :item="item"
  :index="index"
  :key="item.id"
/>
```
不自动将`item`注入组件的原因是，这会使组件与`v-for`的工作方式紧密耦合。明确其数据的来源可以使组件在其他情况下重用。