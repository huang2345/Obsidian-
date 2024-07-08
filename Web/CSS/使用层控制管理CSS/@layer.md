[CSS](https://developer.mozilla.org/zh-CN/docs/Web/CSS) [@规则](https://developer.mozilla.org/zh-CN/docs/Web/CSS/At-rule) 中的`@layer`声明了一个 _级联层_，同一层内的规则将级联在一起，这给予了开发者对层叠机制的更多控制。

`@layer` @规则可以通过三种方式其一来创建级联层。
1. `@layer [name] {}`
2. `@layer [name]...` 提前按顺序声明多个层
3. 通过 `@import` 来导入样式表

其他不属于任意级联层的样式会被集合到一个匿名层中，这个级联层位于所有层的后面，优先级最高
使用了 `!important` 样式在级联层中越前面的层的优先级更高

### 嵌套层
级联层允许嵌套
如果想要对嵌套的层添加新的规则样式，可以使用如下形式：
```
// 父级层.子级层
@layer framework.layout{
// 要加的样式
}
```