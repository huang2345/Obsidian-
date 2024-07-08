两个主要属性：
 - `transform`：指定作用的变换
 - `transoform-origin`：指定元素的原点

`transform的值`
 - `rotate()`旋转
 - `skew(x,y)` 倾斜
	- skewx(x)
	- skewy(y)
 - `translate(x,y)` 位移
	- translatex(x)
	- translatey(y)
 - `scale` 缩放，1为默认，最多三个参数分别设置XYZ轴的缩放系数

## 适用于三维的属性
使用三维空间需要设置一个透视点 `perspective` 以配置3D空间，再去定义2D元素在空间中的行为。

###  透视
首先需要设置透视值 `perspective` 。这是三维空间立体感的来源，近大远小。
该值越小，说明观察者距离元素越近。

在设置了透视值的三维空间中，每个元素都有自己的XYZ轴，如果用了rotate()函数，例如 `rotateY(180deg)` 可使Z轴指向后面。

所以第二个设置 `perspective-origin` 属性，默认情况下观察正面。
取值：
 - x：
	指定消失点的X坐标
 - y：
	指定消失点的Y坐标
