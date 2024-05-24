	DOM是W3C的标准，定义了操作HTML和XML文档的标准接口。DOM允许程序或脚本动态地访问文档的内容、结构和样式。DOM被分为三个不同的部分：DOM核心API、XML DOM、HTML DOM

	不同浏览器对DOM标准的支持程度不同，可以使用hasFeature()方法来检测当前浏览器支持哪些DOM特性
	document.implementation.hasFeateure(feature,version)
	feature是字符串，要检测的DOM特性，version也是字符串，要检测的特性的版本

DOM将HTML文档的层次结构以树形结构表示，称为DOM树。将文档中的标签、属性和标签内容等数据都作为节点。
	例如：\<p align="center">Hello</p>
	align属性是标签p的子节点，Hello也是p的子节点