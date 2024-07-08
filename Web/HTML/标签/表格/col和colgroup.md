	colgroup和col可以控制一整列的样式。

之前通常使用td的colgroup和rowspan来控制单元格的大小，但现在用col元素控制一整列的单元格可能会更方便。

以下是一个简单的例子：
```
```
<table>
  <colgroup>
    <col style="background-color:red" span="1"/>
    <col style="background-color: yellow" span=""/>
  </colgroup>
  <tr>
    <th>Data 1</th>
    <th>Data 2</th>
  </tr>
  <tr>
    <td>Calcutta</td>
    <td>Orange</td>
  </tr>
  <tr>
    <td>Robots</td>
    <td>Jazz</td>
  </tr>
</table>
```
```

col元素有一个span属性，用来指定让这个样式应用到表格中多少列。
