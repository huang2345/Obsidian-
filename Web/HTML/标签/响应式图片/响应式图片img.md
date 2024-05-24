	在不同的设备中，其屏幕的分辨率不同，(一个物理像素渲染一个CSS像素，即DPI=1)，在DPI为1显示正常的图片在DPI为2时会使得图片模糊

### 分辨率切换：不同的尺寸
	可以将img标签的srcset和sizes属性结合起来，实现根据设备屏幕判断使用什么尺寸的图片

```
srcset="elva-fairy-480w.jpg 480w, elva-fairy-800w.jpg 800w"

sizes="(max-width: 600px) 480px,
         800px"
```

### 分辨率切换：相同的尺寸，不同的分辨率

	如果你要支持多分辨率显示，但希望每个人在屏幕上看到的图片的实际尺寸是相同的，你可以使用 `srcset` 结合 x 描述符（一种更简单的语法），而不用 `sizes`，来让浏览器选择合适分辨率的图片。

```
srcset="elva-fairy-320w.jpg, elva-fairy-480w.jpg 1.5x, elva-fairy-640w.jpg 2x"
```

