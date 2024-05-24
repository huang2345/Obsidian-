	Element接口表示HTML和XML中的元素(标签)，Element接口只定义了tagName属性，该属性是字符串，存储了大写形式的HTML和XML元素标签名

getAttribute(name)：获取指定属性的属性值
setAttribute(name,value)：设置指定属性的属性值
removeAttribute(name)：删除指定属性

| 方法                  | 描述                     |
| ------------------- | ---------------------- |
| getAttributeNode    | 获取属性节点                 |
| getElementByTagName | 通过标签名获取节点数组            |
| hasAttribute(name)  | 判断节点某个属性是否存在，存在返回true  |
| hasAttributes()     | 判断节点中有没有属性，有返回true     |
| removeAttributeNode | 删除属性节点                 |
| setIdAttribute      | 为当前Element节点设置一个ID属性值  |
| setIdAttributeNode  | 为当前Element节点设置一个ID属性节点 |
