Web存储只能存储简单的键值对，因此提供了该API来存储较为复杂的数据。
IndexedDB是一个事务型数据库系统，类似基于SQL的RDBMS。但是IndexedDB是一个基于JS的面向对象数据库。

为了获取数据库的访问权限，需要调用`window.indexedDB`属性的`open(name:string,version:number)`，该方法返回一个`IDBRequest`对象