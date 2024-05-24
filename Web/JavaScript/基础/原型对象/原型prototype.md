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