with
使用with语句可以省略对象名，简化代码
```
...
with(n)
{
	console.log(weight);
	console.log(name)
}
//上面的对象都从this或局部变成了n
```

instanceof
对象 instanceof 类型
返回值为true,false

for...in
```
for(var i in 对象)
{
	对象[i]
}
//以数组的形式调用对象的每一个属性和方法
```