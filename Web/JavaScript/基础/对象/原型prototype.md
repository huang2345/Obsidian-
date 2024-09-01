所有对象类型都有一个原型，原型中的属性与方法在该类型中共享。原型可以扩展对象类型的功能，比如可以为JS自带的Number类型新增属性或方法
```
function a(){}

a.prototype.play = function()
{
	console.log(123);
}
a.prototype.name = "Name";

let n1 = new a();
let n2 = new a();
//n1和n2都可以调用同一个方法play，并且共享了同一个属性name,如果n1改变了name的值，那么n2的值也会改变
```

#### Function.prototype.call(thisArg\[,argN\])
会以给定的this值和参数调用该函数。
- thisArg
	- 在调用函数时要使用的this值。如果函数不在严格模式下，null 和 undefined 将被替换为全局对象，并且原始值将被转换为对象。

#### Function.prototype.ball(thisArg\[,argN\])
创建一个新函数，当调用该新函数时，它会调用原始函数并将其 `this` 关键字设置为给定的值
- thisArg
	- 调用创建的新函数时，作为`this`参数传递给目标函数。如果函数不在严格模式下，null 和 undefined 会被替换为全局对象，并且原始值会被转换为对象。如果使用 new 运算符构造绑定函数，则忽略该值。


