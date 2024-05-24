Map是键值对的映射，Set中的值唯一

| 全局属性        | 描述                 |
| ----------- | ------------------ |
| size        | 大小                 |
| constructor | 实例的构造函数，默认是Set,Map |


| 全局函数              | 描述                         |
| ----------------- | -------------------------- |
| add(value)        | 在对象尾部添加一个元素，返回该对象          |
| has(value)        | 判断该值在对象中是否存在，存在返回true      |
| delete(value)     | 删除值为value的元素，成功返回true      |
| clear             | 删除全部元素                     |
| entries           | 返回迭代器对象，该对象为Set对象中所有元素值的数组 |
| forEach(callback) | 遍历回调函数                     |
| keys()            | 与values()方法相同              |
| values()          | 迭代器对象                      |
