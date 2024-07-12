使用JS操控的canvas可以实现一些动画，实现动画需要对所有东西进行重绘。
###### 基本步骤
1. 清空canvas画布
2. 保存canvas状态
3. 重绘动画帧
4. 恢复canvas状态

### 操控动画
想要使用canvas来绘制动画，使用for或者while是不太行的(效率低、占用主线程、动画效果差)。因此，需要定时重绘(异步)
##### 更新画布
- window.setInterval
- window.setTimeout
- ==requestAnimationFrame(callback)
	- 浏览器在下次重绘之前调用指定的回调函数更新动画。回调函数会在浏览器下一次重绘之前执行。
	- 如果想要形成连续的动画，回调函数需要用requestAnimationFrame形成递归
	- 回调函数执行次数通常是每秒 60 次，但在大多数遵循 W3C 建议的浏览器中，回调函数执行次数通常与浏览器屏幕刷新次数相匹配
	- [`DOMHighResTimeStamp`](https://developer.mozilla.org/zh-CN/docs/Web/API/DOMHighResTimeStamp) 参数会传入回调方法中，它指示当前被 `requestAnimationFrame()` 排序的回调函数被触发的时间。在同一个帧中的多个回调函数，它们每一个都会接受到一个相同的时间戳，即使在计算上一个回调函数的工作负载期间已经消耗了一些时间。该时间戳是一个十进制数，单位为毫秒，最小精度为 1ms
	- 返回一个long值ID
- cancelAnimationFrame(ID)
	- 取消回调函数请求

#### 太阳系动画
```
function init() {
    redR = 100;
    blueR = 50;
    redX = 300;
    redY = 300;
    blueX = redR;
    blueY = 0;
    ctx.translate(150, 150);
    requestAnimationFrame(draw);
}
function draw() {
    let date = new Date();
    //清除画布
    ctx.clearRect(-150, -150, width, height);
    ctx.save();
    //绘制红色圆
    ctx.save();
    ctx.beginPath();
    ctx.arc(redX,redY, redR, 0, Math.PI * 2);
    ctx.closePath();
    ctx.fillStyle = 'red';
    ctx.fill();
    ctx.restore();
    //绘制地球轨道
    ctx.beginPath();
    ctx.beginPath();
    ctx.moveTo(redX * 2,redY);
    ctx.arc(redX,redY,redR * 3,0,Math.PI * 2);
    ctx.closePath();
    ctx.stroke();
    ctx.restore();
    //绘制蓝色圆
    ctx.save();
    ctx.beginPath();
    //将原点移动到太阳中心点
    ctx.translate(redX,redY);
    //旋转调整角度
    ctx.rotate(date.getSeconds() * (Math.PI * 2 /60) 
			    + date.getMilliseconds() * (Math.PI * 2 / (60 * 1000)));
    ctx.translate(redR * 3,0);
    ctx.arc(0,0,blueR,0,Math.PI * 2);
    ctx.closePath();
    ctx.fillStyle = 'blue';
    ctx.fill();
    //绘制月亮
    ctx.beginPath();
    ctx.rotate(date.getSeconds() * (Math.PI * 2 /60) 
			    + date.getMilliseconds() * (Math.PI * 2 / (60 * 1000)));
    ctx.arc(redR / 1.5,redR / 1.5,blueR / 2,0,Math.PI * 2);
    ctx.closePath();
    ctx.fillStyle = 'rgb(230,230,230)';
    ctx.fill();
    ctx.restore();

    requestAnimationFrame(draw);
}
init();
```
#### 时钟动画
```
let borderR = 200;
//校准角度
let startAngle = Math.PI / 180 * 1.75; 
let hourZ = borderR / 4;
let minuteZ = borderR / 2;
let secondZ = borderR / 1.3;

function init() {
    
    ctx.translate(width / 2, height / 2);
    requestAnimationFrame(draw);
}
function draw() {
    let date = new Date();

    ctx.clearRect(- width / 2, - height / 2, width, height);
    
    //绘制外部蓝色边框
    ctx.save();
    ctx.strokeStyle = 'blue';
    ctx.lineWidth = 10;
    ctx.beginPath();
    ctx.arc(0,0,borderR,0,Math.PI * 2);
    ctx.closePath();
    ctx.stroke();
    ctx.restore();
    //绘制内部虚线
    ctx.save();
    ctx.strokeStyle = 'gray';
    ctx.lineWidth = 15;
    let lineDash = (Math.PI * (borderR - 20) * 2) / 120;
    ctx.setLineDash([lineDash, lineDash]);
    ctx.beginPath();
    ctx.arc(0,0,borderR - 20,-startAngle,Math.PI * 2 - startAngle);
    ctx.closePath();
    ctx.stroke();
    ctx.restore();
    ctx.save();
    ctx.strokeStyle = 'black';
    ctx.lineWidth = 30;
    ctx.setLineDash([lineDash, lineDash * 9]);
    ctx.beginPath();
    ctx.arc(0,0,borderR - 20,-startAngle,Math.PI * 2 - startAngle);
    ctx.closePath();
    ctx.stroke();
    ctx.restore();

    //绘制三种针
    //三种针的旋转角度均-(Math.PI /2)是由于初始角度为0度，而canvas的初始角度为3点钟方向，所以需要旋转-90度
    //startAngle是为了弥补绘制虚线时的角度问题
    let hour = date.getHours();
    let minute = date.getMinutes();
    let second = date.getSeconds();

    //绘制时针
    ctx.save();
    console.log(hour % 12);
    ctx.rotate(-(Math.PI / 2) + (Math.PI * 2 / 12) * (hour % 12) - startAngle  + (Math.PI * 2 / 12 / 60) * minute);
    
    ctx.lineCap = 'round';
    ctx.lineWidth = 5;
    
    ctx.beginPath();
    ctx.moveTo(0, 0);
    ctx.lineTo(hourZ,0);
    ctx.closePath();
    ctx.stroke();

    ctx.restore();
    //绘制分针
    ctx.save();
    ctx.rotate(-(Math.PI / 2) + (Math.PI * 2 / 60) * minute - startAngle + (Math.PI * 2 / 60 / 60) * second);
    ctx.lineCap = 'round';
    ctx.lineWidth = 2;
    ctx.beginPath();
    ctx.moveTo(0, 0);
    ctx.lineTo(minuteZ,0);
    ctx.closePath();
    ctx.stroke();
    ctx.restore();
    //绘制秒针
    ctx.save();
    ctx.rotate(-(Math.PI / 2) + (Math.PI * 2 / 60) * second - startAngle);
    ctx.lineWidth = 1;
    ctx.fillStyle = 'red';
    ctx.beginPath();
    ctx.moveTo(0, 0);
    ctx.lineTo(0,5);
    ctx.lineTo(secondZ,0);
    ctx.lineTo(0,-5);
    ctx.closePath();
    ctx.fill();
    ctx.restore();

    requestAnimationFrame(draw);
}
```
#### 循环全景照片
```
let img = new Image();
let i = 0;
let speed = 3;
function init() {
    img.src = './tu1.png';
    requestAnimationFrame(draw);
}
function draw(s) {
    ctx.clearRect(0, 0, width, height);

    ctx.drawImage(img,i,0,width,height,0,0,width,height);
    i += speed;
    if(i >= 2559 - width) speed = -speed;
    if(i <= 0) speed = -speed;
    requestAnimationFrame(draw);
}
init();
```

#### 鼠标追踪动画
```
let x,y;
let a = 100;
let zc = Math.sqrt(a*a - (a/2)*(a/2));
let r = 400;

function init() {
    //获取鼠标位置
    canvas.addEventListener('mousemove', function (e) {
        x = e.clientX;
        y = e.clientY;
    });
    requestAnimationFrame(draw);
}
function draw(s) {
    ctx.clearRect(0, 0, width, height);


    ctx.save();
    ctx.translate(x,y);
    ctx.rotate(s/1000);
    ctx.fillStyle = 'red';
    //绘制一个旋转的三角形，该三角形由三个三角形加一个空白未绘制的三角形组成
    ctx.beginPath();
    ctx.moveTo(- a / 2,- zc / 2);
    ctx.lineTo(a / 2,- zc / 2);
    ctx.lineTo(0,- zc / 2 - zc);
    ctx.lineTo(- a / 2,- zc / 2);

    ctx.lineTo(- a / 2 - a / 2, zc / 2);
    ctx.lineTo(0,zc / 2);
    ctx.lineTo(- a / 2,- zc / 2);

    ctx.moveTo(a / 2,- zc / 2);
    ctx.lineTo(0, zc / 2);
    ctx.lineTo(a / 2 + a / 2, zc / 2);
    ctx.lineTo(a / 2,- zc / 2);
    ctx.fill();
    ctx.closePath();
    ctx.restore();

    ctx.save();
    ctx.translate(x,y);
    ctx.rotate(s/1000);
    ctx.strokeStyle = 'blue';
    ctx.lineWidth = 5;

    ctx.beginPath();
    ctx.arc(0,0,r,s / 1000, s / 1000 + Math.PI/2);
    // ctx.closePath();
    ctx.stroke();
    ctx.beginPath();
    ctx.rotate(s / 1000 + Math.PI/2);
    ctx.arc(r,0,r / 10, 0, Math.PI * 2);
    ctx.closePath();
    ctx.fill();


    ctx.restore();




    requestAnimationFrame(draw);
}
init();
```