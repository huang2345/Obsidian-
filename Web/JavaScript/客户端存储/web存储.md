Web存储API简单易用——只能存储简单的键值对。
所有的Web存储数据都包含在浏览器内两个类似对象的结构中：`sessionStorage`和`localStorage`。

对于`sessionStorage`，数据会在页面开着时一直保存，直到页面关闭(页面刷新数据依旧保存)。
对于`localStorage`，数据会一直保存，哪怕浏览器关闭后重启。

### Storage接口
作为`Web Storage API`的接口，`Storage`接口提供了访问特定域名下的会话存储或本地存储的功能。
#### 属性
只有`length`属性表示数据项的数量
#### 方法
##### setItem(key : string,value : string)
将键值对存储。如果键已存在，则更新`value`
##### getItem(key : string)
获取值
##### removeItem(key : string)
通过键名删除数据项
##### key(n : number)
返回存储中的第n个键名
##### clear()
清除存储中的所有数据项