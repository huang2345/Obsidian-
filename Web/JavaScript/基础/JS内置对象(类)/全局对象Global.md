
| 全局属性      | 描述             |
| --------- | -------------- |
| Infinity  | 正无穷大           |
| Java      | 表示java.\*层的包   |
| NaN       | 表示非数值          |
| Packages  | 根JavaPackage对象 |
| undefined | 表示未定义的值        |

| 全局函数               | 描述                 |
| ------------------ | ------------------ |
| decodeURI          | 解码某个编码的URI         |
| decodeURIComponent | 解码一个编码的URI组件       |
| encodeURI          | 将字符串编码为URI         |
| encodeURIComponent | 将字符串编码为URI组件       |
| escape             | 对字符串进行编码           |
| eval               | 将一个JS字符串作为脚本代码来执行  |
| getClass           | 返回一个Java对象的类       |
| isFinite           | 检查某个值是否为有穷大的数值     |
| isNaN              | 检查是否是非数值           |
| Number             | 数值强制转换             |
| parseFloat         | 解析一个字符串并返回一个浮点数    |
| parseInt           | 解析一个字符串并返回一个整数     |
| String             | 字符串强制转换            |
| unescape           | 把由escape编码的字符串进行解码 |

HTTP等相关协议规定了URI中不能有中文、特殊字符等，需要使用时要先编码