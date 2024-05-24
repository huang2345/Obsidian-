**`align-items`** 属性设置了所有直接子元素的 [`align-self`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-self) 值作为一个组。在 Flexbox 中，它控制子元素在[交叉轴](https://developer.mozilla.org/zh-CN/docs/Glossary/Cross_Axis)上的对齐。在 Grid 布局中，它控制了子元素在其[网格区域](https://developer.mozilla.org/zh-CN/docs/Glossary/Grid_Areas)内的块向轴上的对齐。

[`normal`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-items#normal)
这个关键字的效果取决于我们处在什么布局模式中：

- 在绝对定位的布局中，对于_被替代_的绝对定位盒子，行为与 `start` 类似；对于_其他所有_绝对定位的盒子，行为与 `stretch` 类似。
- 在绝对定位布局的静态位置上，行为与 `stretch` 类似。
- 对于那些 flex 元素而言，行为与 `stretch` 类似。
- 对于那些 grid 元素而言，行为与 `stretch` 类似，但对于具有长宽比或固有尺寸的盒子，其行为与 `start` 类似。
- 这个属性不适用于块级盒子和表格。

[`flex-start`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-items#flex-start)
只在 flex 布局中使用，将元素与 flex 容器的主轴起点或交叉轴起点对齐。

[`flex-end`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-items#flex-end)
只在 flex 布局中使用，将元素与 flex 容器的主轴末端或交叉轴末端对齐。

[`center`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-items#center)
flex 元素的外边距框在交叉轴上居中对齐。如果元素的交叉轴尺寸大于 flex 容器，它将在两个方向上等距溢出。

[`start`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-items#start)
将元素与容器的主轴起点或交叉轴起点对齐。

[`end`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-items#end)
将元素与容器的主轴末端或交叉轴末端对齐。

[`self-start`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-items#self-start)
将元素与容器的主轴起点或交叉轴起点对齐，轴起点的方向对应于元素的起始方向。

[`self-end`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-items#self-end)
将元素与容器的主轴末端或交叉轴末端对齐，轴末端的方向对应于元素的结尾方向。

[`baseline`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-items#baseline)、`first baseline`、`last baseline`
所有 flex 元素都对齐，以使它们的 [flex 容器基线](https://drafts.csswg.org/css-flexbox-1/#flex-baselines) 对齐。距离其交叉轴起点和基线之间最远的元素与行的交叉轴起点对齐。

[`stretch`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-items#stretch)
如果（多个）元素的组合大小小于容器的大小，其中自动调整大小的元素将等量增大，以填满容器，同时这些元素仍然保持其宽高比例的约束。

[`safe`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-items#safe)
与其它对齐值一起使用。如果所选对齐值导致元素溢出容器，则将元素按 `start` 方式对齐。

[`unsafe`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-items#unsafe)
与其它对齐值一起使用。不管元素和容器的相对尺寸以及是否会发生溢出，都会采用给定的对齐值。