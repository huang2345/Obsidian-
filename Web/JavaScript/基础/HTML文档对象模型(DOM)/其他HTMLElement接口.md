HTMLTableElement    HTMLTableRowElement    HTMLTableCellElement：
以上三个接口分别表示表格、单元行、单元格

表格.rows\[]属性，表示表格中的所有行,是HTMLCollection
表格.insertRow(index)：插入一个空的新行，并返回新行的对象
单元行.insertCell(index)：插入一个空的单元格，并返回单元格的对象
HTMLCollection.item()

	根据给定的索引（从 0 开始），返回具体的节点。如果索引超出了范围，则返回 `null`。


HTMLLinkElement：
对象.href：获取a标签的href属性

HTMLInputElement：
value：表单元素的值
type：表单控件属性
defalutValue：默认值
defaultChecked：默认选中
checked：选中属性
form：表单控件属性
disabled：false时表示禁用控件
readonly：只读属性
maxLength：最大输入字符数
size：元素大小


HTMLSelectElement：
对象.selectedIndex属性：表示当前选中的选项的索引
对象.options\[]属性：表示所有的选项，属于HTMLOptionsCollection
对象.add(element,before)：
对象.selectedOptions属性：所有选中的元素
element是要添加的选项的对象，放在before元素之前的位置，如果是数值>=1从顶部添加，<1从底部添加

对象.remove(index)：删除选项 