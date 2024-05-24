	DOM HTML是DOM核心接口的扩展，专门针对HTML和XHTML文档定义了接口

HTMLDocument接口：
document对象实现了HTMLDocument接口

属性childNodes：获取所有子节点，包括文本
属性children：children 属性返回元素的子元素的集合，是一个 HTMLCollection 对象

| 属性        | 描述                                       |
| --------- | ---------------------------------------- |
| title     | \<title>中的内容                             |
| referrer  | 通过链接跳转到本页后，该属性记录了跳转前的页面URI               |
| domain    | 文档所在服务器域名                                |
| URI       | 文档地址                                     |
| body      | \<body>                                  |
| images[]  | 文档中所有\<img>元素列表，HTMLCollection           |
| applets[] | 文档中所有\<applet>元素列表，HTMLCollection        |
| links[]   | 文档中所有\<a href=...>元素列表，HTMLCollection    |
| forms[]   | 文档中所有\<form>元素列表，HTMLCollection          |
| anchors[] | 文档中所有\<a name=...>元素列表，HTMLCollection,锚点 |
| cookie    | 文档的cookie信息                              |

| 方法                     | 描述               |
| ---------------------- | ---------------- |
| open                   | 打开文档流            |
| close                  | 关闭文档流，显示文档内容     |
| write                  | 在文档流中写入          |
| writeIn                | 在文档流中写入，在末尾添加换行符 |
| getElementsByName      | 根据name获取属性       |
| getElementsByClassName | 根据class获取属性      |

HTMLElement接口：

	HTMLElement接口继承了Element接口，HTML文档中的所有元素都属于HTMLElement接口类型，该接口没有方法


| 属性        | 描述                     |
| --------- | ---------------------- |
| id        | id属性                   |
| title     | title属性，表示鼠标悬停在元素上时的提示 |
| lang      | lang属性，表示元素的字符编码       |
| dir       | dir属性，表示元素的文本方向        |
| className | className属性，表示元素采用的样式  |
| innerHTML | 标签中的内容                 |
| outerHTML | 包含标签的内容，可以改变元素自身使用的标签  |
DOM HTML为几乎所有的HTML元素都定义了特定的接口，这些接口都继承了HTMLElement。