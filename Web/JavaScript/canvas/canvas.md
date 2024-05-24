```
<canvas></canvas>
该标签由两个属性设置画布大小，width和height,与使用CSS设置的不同

较老的浏览器不支持该功能，可以在标签中添加替代内容
```
.getContext(上下文类型，上下文属性)
	通过上下文类型返回上下文，例如`2d`

常用方法
```
moveTo(x,y)移动笔触
通常使用该函数设置起始点

lineTo(x,y)从上一个路径点绘制一条到(x,y)的直线
```
矩形绘制
```
ctx.fillRect()填充矩形
ctx.strokeRect()边框
ctx.clearRect()清除指定矩形区域
ctx.Rect()在路径中添加矩形
x,y,width,height
参数相同
```

路径绘制
```
ctx.beginPath();
新建一条路径

ctx.closePath()
闭合路径

ctx.stroke()
绘制线条

ctx.fill()
自动闭合路径，通过填充路径的内容区域生成实心的图形。
```

圆弧绘制
```
arc(x,y,r,startAngle,endAngle,anticlockwise)

anticlockwise：绘制方向，默认顺时针(false)
startAngle：起始角度
endAngle：结束角度
r：半径
弧度=(Math.PI/180)*角度。

arcTo(x1,y1,x2,y2,radius)
该函数通过两条线来绘制：
1.上个路径到(x1,y1)
2.(x1,y1)到(x2,y2)
这两条线与绘制出的圆弧相切
```
![[arcTo.png]]

贝塞尔曲线绘制
```
quadraticCurveTo(cp1x, cp1y, x, y)
绘制二次贝塞尔曲线，`cp1x,cp1y` 为一个控制点，`x,y` 为结束点。

bezierCurveTo(cp1x, cp1y, cp2x, cp2y, x, y)
三次贝塞尔曲线，有两个控制点

贝塞尔曲线通过控制点来控制曲线的弧度
```