以下是一个简单的示例，在示例中我们创建一个圆和一个矩形：
```
<svg
  version="1.1"
  baseProfile="full"
  width="300"
  height="200"
  xmlns="http://www.w3.org/2000/svg">
  <rect width="100%" height="100%" fill="black" />
  <circle cx="150" cy="100" r="90" fill="blue" />
</svg>
```

从上面的例子可以看出，SVG 很容易手工编码。是的，你可以在文本编辑器中手动编写简单的 SVG，但是随着图像复杂度提升，手动编码很快就开始变得非常困难。
为了创建 SVG 图像，大多数人使用矢量图形编辑器，如 [Inkscape](https://inkscape.org/) 或 [Illustrator](https://zh.wikipedia.org/wiki/Adobe_Illustrator)。
借助这些软件包，你可以使用各种图形工具创建插图，也可以创建近似照片的矢量图（例如 Inkscape 的跟踪位图功能）。

## 将 SVG 添加到页面

1. 要通过 [`<img>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img) 元素嵌入 SVG，你只需要按照预期的方式在 src 属性中引用它。你将至少需要 `height` 或 `width` 属性中的一个（或者如果你的 SVG 没有固有的宽高比，则都需要）。
2. 内联SVG(其实就是以文本打开SVG文件然后复制粘贴)
3. 使用iframe嵌入SVG
4. 以上三种其实都差不多

## 兼容性问题

对于不支持 SVG（IE 8 及更低版本，Android 2.3 及更低版本）的浏览器，你可以用 `src` 属性引用 PNG 或 JPG，并使用 [`srcset`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img#srcset) 属性（只有较新的浏览器才能识别）来引用 SVG。
在这种情况下，仅支持 SVG 的浏览器会加载 SVG——较旧的浏览器将加载 PNG：
```
<img src="equilateral.png" alt="等边三角形" srcset="equilateral.svg" />
```
