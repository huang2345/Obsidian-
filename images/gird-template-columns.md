该属性是基于[网格列](https://developer.mozilla.org/zh-CN/docs/Glossary/Grid_Column)的维度，去定义网格线的名称和网格轨道的尺寸大小。即列的宽度

[`none`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/grid-template-columns#none)
这个关键字表示不明确的网格。所有的列和其大小都将由[`grid-auto-columns`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/grid-auto-columns) 属性隐式的指定。

[`<length>`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/length)
非负值的长度大小。

[`<percentage>`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/percentage)
非负值且相对于网格容器的 [`<percentage>`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/percentage)。如果网格容器的尺寸大小依赖网格轨道的大小（比如 inline-grid），则百分比值将被视为 `auto`。 为了遵守网格的百分比，网格轨道本身定义的大小，将自动被调整为相对网格容器大小，并且是以最小量将网格轨道调整到最终的大小。

[`<flex>`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/flex_value)
非负值，用单位 `fr` 来定义网格轨道大小的弹性系数。每个定义了 `<flex>` 的网格轨道会按比例分配剩余的可用空间。当外层用一个 `minmax()` 表示时，它将是一个自动最小值（即 `minmax(auto, <flex>)`）。

[`max-content`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/grid-template-columns#max-content)
是一个用来表示以网格项的最大的内容来占据网格轨道的关键字。

[`min-content`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/grid-template-columns#min-content)
是一个用来表示以网格项的最大的最小内容来占据网格轨道的关键字。

[`minmax(min, max)`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/minmax)
是一个来定义大小范围的属性，大于等于 min 值，并且小于等于 max 值。如果 max 值小于 min 值，则该值会被视为 min 值。最大值可以设置为网格轨道系数值`<flex>` ，但最小值则不行。
	Note : 该规范在将来可能会允许设置最小值为 `flex`，也会调整[网格轨道算法](https://www.w3.org/TR/css-grid-1/#track-sizing-algorithm)计算出正确的大小。

[`auto`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/grid-template-columns#auto)
如果该网格轨道为最大时，该属性等同于 `<max-content>`，为最小时，则等同于 `<min-content>`。
	**备注：** 网格轨道大小为 `auto`（且只有为 `auto`）时，才可以被属性 [`align-content`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-content) 和 [`justify-content`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/justify-content) 拉伸。

[`fit-content( [ <length> | <percentage> ] )`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/fit-content)
相当于公式 `min(max-content, max(auto, argument))`，类似于 `auto` 的计算（即 `minmax(auto, max-content)`），除了网格轨道大小值是确定下来的，否则该值都大于 `auto` 的最小值。

[`repeat( [ <positive-integer> | auto-fill | auto-fit ] , <track-list> )`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/repeat)
表示网格轨道的重复部分，以一种更简洁的方式去表示大量而且重复列的表达式。