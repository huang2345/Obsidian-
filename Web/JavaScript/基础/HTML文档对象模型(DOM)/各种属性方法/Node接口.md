	Node接口定义了节点的基本操作，其他接口都继承了Node接口

属性：
attributes：返回当前节点的属性节点列表，NamedNodeMap类型
childNodes：返回所有子节点的节点列表，NodeList类型
textContent：返回节点与子节点的文本内容，子节点文本内容不包含块级标签

方法：
appendChild()：在尾部添加节点
hasAttributes：判断是否有属性，有true
hasChildNodes：判断是否有子节点，有true
insertBefore(要添加的节点，子节点node)：在子节点node的前面插入要添加的节点
removeChild(node)：删除子节点node
replaceChild(newNode,oldNode)：节点替换
normalize()：遍历当前节点下的所有子节点，合并相邻的Text节点

| 属性                 | 描述                               |
| ------------------ | -------------------------------- |
| firstChild         | 返回第一个子节点                         |
| lastChild          | 返回最后一个子节点                        |
| localName          | 返回当前节点的本地名称                      |
| nextSibling        | 返回下一个兄弟节点                        |
| nextElementSibling | 属性只返回元素节点之后的兄弟元素节点（不包括文本节点、注释节点） |
| previousSibling    | 上一个兄弟节点                          |
| parentNode         | 返回父节点                            |
| nodeName           | 根据类型返回指定的节点名称                    |
| nodeType           | 返回节点类型，使用数字代指                    |
| nodeValue          | 根据类型设置或返回节点值                     |
| ownerDocument      | 返回当前节点的文档对象                      |
| prefix             | 设置或返回一个节点的命名空间前缀                 |

| 方法                      | 描述                  |
| ----------------------- | ------------------- |
| cloneNode               | 复制节点                |
| compareDocumentPosition | 比较两个节点的文档位置         |
| getFeature              | 返回一个带有指定特性和版本的DOM对象 |
| getUserData             | 返回此节点上与键相关联的对象      |
| isEqualNode             | 比较两个节点值是否相等         |
| isSameNode              | 比较两个节点是否相同          |
| isSupported             | 返回节点是否支持某个DOM特性     |
| setUserData             | 把某个对象关联到节点上的一个键上    |

Node.nodeType的值是一个整数，用数字代表了不同的节点类型