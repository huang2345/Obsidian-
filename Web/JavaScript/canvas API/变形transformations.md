#### 状态的保存和恢复
在使用变形之前保存canvas状态十分重要，在绘制复杂图形时十分有用。
- save()
	- 保存canvas的所有状态，无参函数
- restore()
	- 恢复canvas状态，无参函数
Canvas状态保存在栈中，当save()调用时，当前的状态压入栈中。调用restore后，上一个保存的状态从栈中弹出。
保存的状态包括：
- 当前应用的变形
- stokeStyle,fillStyle,globalAlpha,lineWidth,lineCap,lineJoin,miterLimit,lineDashOffset,shadowOffsetX,shadowOffsetY,shadowBlur,shadowColor,globalCompositeOperation,font,textAlign,textBaseline,direction,imageSmoothingEnabled
- 当前的裁剪路径

#### 移动translate(x,y)
移动canvas画布原点的位置
#### 旋转rotate(angle)
以原点为中心，旋转canvas画布的X轴(顺时针方向，单位弧度)
#### 缩放scale(x,y)
缩放画布的XY轴的单位，值可以为负数，默认值为1，大于1为放大，小于1为缩小
#### 变形transform(a,b,c,d,e,f)
为以上三个方法的矩阵(translate)
- a (m11)
	- 水平缩放。
- b (m12)
	- 垂直倾斜。
- c (m21)
	- 水平倾斜。
- `d (m22)`
	- 垂直缩放。
- e (dx)
	- 水平移动。
- f (dy)
	- 垂直移动。
```
a c e水平
b d f垂直
0 0 1
```

setTransform(a,b,c,d,e,f)
- 取消当前变形，设置为指定变形
resetTransform()
- 重置矩阵

