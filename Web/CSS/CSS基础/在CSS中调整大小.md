## 原始尺寸，或固有尺寸

在受 CSS 设置影响之前，HTML 元素有其原始的尺寸。一个直观的例子就是图像。一幅图像的长和宽由这个图像文件自身确定。这个尺寸就是固有尺寸。

一个空div是没有原始尺寸的，因为没有内容，没有高度。

### 设置具体的尺寸
当给元素指定尺寸（然后其内容需要适合该尺寸）时，我们将其称为**`外部尺寸`**。

使用百分比设置元素的内外边距时，值是以包含块的`内联尺寸`来计算的，也就是元素的`inline`即水平宽度。

### min-和max-尺寸
	除了固定大小的盒子外，还有一些盒子的宽高是弹性的(比如`display:flex;`)，可以使用min-height、min-width、max-height、max-width等属性设置最小高度宽度和最大是多少。
	这个技术是用来让图片可响应的，所以在更小的设备上浏览的时候，它们会合适地缩放。但是针对视口大小所加载的图片尺寸调整不应该使用该技术，这个问题更适合使用<source>、srcset等来解决。

## 视口单位
视口，即你在浏览器中看到的部分页面，也是有尺寸的。在 CSS 中，我们有与视口尺寸相关的度量单位，即意为视口宽度的 vw 单位，以及意为视口高度的 vh 单位。
使用这些单位，你可以把一些东西做得随用户的视口改变大小。
