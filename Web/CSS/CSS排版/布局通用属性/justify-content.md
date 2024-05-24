定义浏览器如何沿着弹性容器的[主轴](https://developer.mozilla.org/zh-CN/docs/Glossary/Main_Axis)和网格容器的行向轴分配内容元素之间和周围的空间。

当 length 属性和自动外边距属性生效之后，对齐已经完成了。也就是说，如果[弹性布局](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_flexible_box_layout)中存在至少一个弹性元素，而且这个元素的 [`flex-grow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/flex-grow) 属性不等于 `0`，那么对齐方式不会生效，就像没有多余空间的情况。

取值：

[`start`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/justify-content#start)
从行首开始排列。每行第一个元素与行首对齐，同时所有后续的元素与前一个对齐。

[`end`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/justify-content#end)
从行尾开始排列。每行最后一个元素与行尾对齐，同时所有前面的元素与后一个对齐。

[`flex-start`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/justify-content#flex-start)
元素紧密地排列在弹性容器的主轴起始侧。仅应用于弹性布局的项目。对于不是弹性容器里的元素，此值将被视为 `start`。

[`flex-end`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/justify-content#flex-end)
元素紧密地排列在弹性容器的主轴结束侧。仅应用于弹性布局的元素。对于不是弹性容器里的元素，此值将被视为 `end`。

[`center`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/justify-content#center)
伸缩元素向每行中点排列。每行第一个元素到行首的距离将与每行最后一个元素到行尾的距离相同。

[`left`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/justify-content#left)
伸缩元素一个挨一个在对齐容器得左边缘，如果属性的轴与内联轴不平行，则 `left` 的行为类似于 `start`。

[`right`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/justify-content#right)
元素以容器右边缘为基准，一个挨着一个对齐，如果属性轴与内联轴不平行，则 `right` 的行为类似于 `end`。

[`space-between`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/justify-content#space-between)
在每行上均匀分配弹性元素。相邻元素间距离相同。每行第一个元素与行首对齐，每行最后一个元素与行尾对齐。

[`space-around`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/justify-content#space-around)
在每行上均匀分配弹性元素。相邻元素间距离相同。每行第一个元素到行首的距离和每行最后一个元素到行尾的距离将会是相邻元素之间距离的一半。

[`space-evenly`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/justify-content#space-evenly)
flex 项都沿着主轴均匀分布在指定的对齐容器中。相邻 flex 项之间的间距，主轴起始位置到第一个 flex 项的间距，主轴结束位置到最后一个 flex 项的间距，都完全一样。

[`stretch`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/justify-content#stretch)
如果元素沿主轴的组合尺寸小于对齐容器的尺寸，任何尺寸设置为 `auto` 的元素都会等比例地增加其尺寸（而不是按比例增加），同时仍然遵守由 [`max-height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/max-height)/[`max-width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/max-width)（或相应功能）施加的约束，以便沿主轴完全填充对齐容器的组合尺寸。

**备注：** 虽然弹性盒子支持 `stretch` 属性，但将其应用于弹性盒子时，由于拉伸是由 [`flex`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/flex) 属性控制的，所以 `stretch` 的行为与 `start` 相同。

[`safe`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/justify-content#safe)
如果元素溢出对齐容器，则元素将按照对齐模式为 `start` 进行对齐。所期望的对齐将不会被实现。

[`unsafe`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/justify-content#unsafe)
即使元素溢出对齐容器，也会实现所需的对齐方式。与 `safe` 不同，`safe` 会忽略所要求的对齐方式以防止溢出。