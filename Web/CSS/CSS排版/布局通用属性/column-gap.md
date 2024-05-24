用来设置元素列之间的间隔（[gutter](https://developer.mozilla.org/zh-CN/docs/Glossary/Gutters)）大小。

`column-gap` 一开始是 [Multi-column 布局](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_multicol_layout)下的特有属性，后来在其他布局中也使用这个属性。
如 [CSS 盒子对齐](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_box_alignment)中的表述，该属性已经可以在 Multi-column（多列布局）、Flexible Box（弹性盒子）以及 Grid layout（网格布局）中使用。

[`normal`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/column-gap#normal)
表示列之间的间隔宽度。在 `多列布局` 时默认间隔为 `1em`，其他类型布局默认间隔为 0。

[`<length>`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/length)
用 [`<length>`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/length) 来定义列之间的间隔大小。而且 [`<length>`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/length) 值必须是非负数的。

[`<percentage>`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/percentage)
用 [`<percentage>`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/percentage)（百分比）来定义列之间的间隔大小。同样的，[`<percentage>`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/percentage) 值也必须是非负数的。

