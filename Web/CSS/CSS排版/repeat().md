	函数表示轨道列表的重复片段，允许以更紧凑的形式写入大量显示重复模式的列或行。

[`<length>`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/length)
正整数长度。

[`<percentage>`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/percentage)
相对于列网格轨道中网格容器的行内大小以及行网格轨道中网格容器的块大小的非负百分比。如果网格容器的大小取决于它的轨道大小，那么 `<percentage>` 必须被视为 `auto`. 用户代理（user-agent）可以将轨道的固有大小贡献调整为网格容器的大小，将轨道的最终大小增加到可以遵守该百分比的最小数量。

[`<flex>`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/flex_value)
带有 `fr` 单位的非负尺寸指定轨道的弹性系数。任何被 `<flex>` 指定大小的轨道会根据其弹性系数按比例分配剩余空间。

[`max-content`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/repeat#max-content)
代表占据网格轨道的网格项目所分配的最大内容区域的最大值。

[`min-content`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/repeat#min-content)
代表占据网格轨道的网格项目所分配的最小内容区域的最小值。

[`auto`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/repeat#auto)
作为最大值，等同于 `max-content`。作为最小值，它代表占据网格轨道的网格项目的最小尺寸的最大值（如同[`min-width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/min-width)/[`min-height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/min-height)所指定的)）。

[`auto-fill`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/repeat#auto-fill)
如果网格容器在相关轴上具有确定的大小或最大大小，则重复次数是最大可能的正整数，不会导致网格溢出其网格容器。如果定义了，将每个轨道视为其最大轨道尺寸大小函数 ( `grid-template-rows` 或 `grid-template-columns`用于定义的每个独立值。否则，作为最小轨道尺寸函数，将网格间隙加入计算。如果重复次数过多，那么重复值是 `1` 。否则，如果网格容器在相关轴上具有确定的最小尺寸，重复次数是满足该最低要求的可能的最小正整数。否则，指定的轨道列表仅重复一次。

[`auto-fit`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/repeat#auto-fit)
行为与 `auto-fill` 相同，除了放置网格项目后，所有空的重复轨道都将折叠。空轨道是指没有流入网格或跨越网格的网格项目。（如果所有轨道都为空，则可能导致所有轨道被折叠。）

折叠的轨道被视为具有单个固定轨道大小函数为 `0px`，两侧的槽都折叠了。

为了找到自动重复的轨道数，用户代理将轨道大小限制为用户代理指定的值（例如 `1px`），以避免被零除。