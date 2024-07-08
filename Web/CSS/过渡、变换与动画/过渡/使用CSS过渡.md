**CSS 过渡**提供了一种在更改 CSS 属性时控制动画速度的方法。其可以让属性变化成为一个持续一段时间的，而不是立即生效的过程。

通常将两个状态之间的过渡称为**隐式过渡**，因为开始与结束之间的状态由浏览器决定。

### 部分属性或属性值不支持过渡
`display` `height:auto`
## 使用过渡为鼠标悬浮时出现的菜单添加效果
过渡不能对如 `auto` 这种没有确定数值的属性值应用，所以不能通过 `height` 属性实现过渡动画。
由于 `display` 实质上是切换元素的外部显示方式，所以也不能应用过渡，因为没有中间值。
有两种方法：
1. 利用 `max-height` 设置一个较大值 ，实际的height由内容自动填充，对 `max-height` 进行控制和过渡实现。
	 - 缺点：过渡实质上是应用的 `max-height` ，而过高的属性值会导致将鼠标移开时的过渡效果出现了延迟
2. 利用网格布局来设置，网格设置 `grid-template-rows:0fr`,过渡这个属性，利用动态的 `fr` 单位实现过渡。
3. 利用弹性布局，与上一种相同的原理。
#### 属性列表长度不一致
##### 短时
会将属性值复制粘贴，并删掉多余的
例如 `transition-duration:3s 5s` 变成 `3s 5s 3s 5s`
##### 长时
删掉后面多余的

## 通过过渡让JS实现更好的效果
JS通过为事件添加事件处理，触发事件时改变CSS属性实现平滑的过渡动画。
例如mdn的指南中用JS改变元素的 `transform`属性来实现元素的位移，使用浮动移动元素是不同的技术实现相似的效果。

### 检测过渡的开始与结束
 - `transitionrun` 在延迟触发前就会触发
 - `transitionstart` 在延迟触发后触发
 -  `transitionend` 过渡动画结束后触发

你可以使用 [`transitionend`](https://developer.mozilla.org/zh-CN/docs/Web/API/Element/transitionend_event "transitionend") 事件来检测某动画是否结束运行，它是一个 [`TransitionEvent`](https://developer.mozilla.org/zh-CN/docs/Web/API/TransitionEvent) 对象，除了一般的 [`Event`](https://developer.mozilla.org/zh-CN/docs/Web/API/Event) 对象外，还有两个额外属性：

[`propertyName`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_transitions/Using_CSS_transitions#propertyname)
一个字符串，表示过渡完成的 CSS 属性的名称。

[`elapsedTime`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_transitions/Using_CSS_transitions#elapsedtime)
一个浮点数，表示在事件发生时，过渡已经运行了多少秒。这个值不受 [`transition-delay`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/transition-delay) 值的影响。



