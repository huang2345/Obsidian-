	HTML5增加了一项新功能是：自定义数据属性，也就是data-\*自定义属性。在HTML5中我们可以使用data-为前缀来设置我们需要的自定义属性，来进行一些数据的存放。

## dataset属性存取data-自定义属性的值

这种方式通过访问一个元素的dataset属性来存取data\-自定义属性的值。这个dataset属性是HTML5 Javascript API的一部分，用来返回一个所有选择元素的data-属性的DOMStringMap对象。

使用这种方法时，不是使用完整的属性名，如data-id来存取数据，应该去掉data-前缀。

还有一点特别注意的是：data-属性名如果包含了连字符，例如 data-id-and-class，连字符将被去掉，并转换为驼峰式的命名，前面的属性应该写成idAndClass。

如果你想删掉一个`data-`属性，可以这么做：

```
delete div.dataset.id;
```