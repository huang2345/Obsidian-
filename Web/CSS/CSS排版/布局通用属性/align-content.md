设置了浏览器如何沿着[弹性盒子布局](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_flexible_box_layout)的纵轴和[网格布局](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_grid_layout)的主轴在内容项之间和周围分配空间。

[`start`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-content#start)
所有行从容器的起始边缘开始填充。

[`end`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-content#end)
所有行从容器的结束边缘开始填充。

[`flex-start`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-content#flex-start)
所有行从垂直轴起点开始填充。第一行的垂直轴起点边和容器的垂直轴起点边对齐。接下来的每一行紧跟前一行。

[`flex-end`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-content#flex-end)
所有行从垂直轴末尾开始填充。最后一行的垂直轴终点和容器的垂直轴终点对齐。同时所有后续行与前一个对齐。

[`center`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-content#center)
所有行朝向容器的中心填充。每行互相紧挨，相对于容器居中对齐。容器的垂直轴起点边和第一行的距离相等于容器的垂直轴终点边和最后一行的距离。

[`normal`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-content#normal)
这些项按默认位置填充，就像没有设置对齐内容值一样。

[`space-between`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-content#space-between)
所有行在容器中平均分布。相邻两行间距相等。容器的垂直轴起点边和终点边分别与第一行和最后一行的边对齐。

[`space-around`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-content#space-around)
所有行在容器中平均分布，相邻两行间距相等。容器的垂直轴起点边和终点边分别与第一行和最后一行的距离是相邻两行间距的一半。

[`space-evenly`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-content#space-evenly)
所有行沿垂直轴均匀分布在对齐容器内。每对相邻的项之间的间距，主开始边和第一项，以及主结束边和最后一项，都是完全相同的。

[`stretch`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-content#stretch)
拉伸所有行来填满剩余空间。剩余空间平均地分配给每一行。

[`safe`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-content#safe)
与对齐关键字一起使用。如果所选的关键字意味着项溢出对齐容器（data loss），则将采用备用策略对项进行对齐，就像启动了 `start` 对齐模式一样。

[`unsafe`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-content#unsafe)
与对齐关键字一起使用。无论元素和对齐容器的相对大小如何、是否会导致一些元素溢出可见范围（data loss），都使用给定的对齐值。