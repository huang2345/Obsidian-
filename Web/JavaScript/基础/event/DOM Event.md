1.DOM事件流

	DOM结构是一个树形结构，当HTML元素产生一个事件时，事件会在元素节点和根节点之间传播，路径上的元素都会收到该事件，这个过程可称为DOM事件流

冒泡型事件：
	事件从触发事件的节点开始传播，向上传递
捕获型事件：
	事件从DOM树顶层元素向下传播，向下传递

2.DOM Event接口，DOM标准为控制文档中的事件定义了一系列接口，详情见官方文档[Event - Web API 接口参考 | MDN (mozilla.org)](https://developer.mozilla.org/zh-CN/docs/Web/API/Event)

3.事件响应函数
	DOM标准中的事件响应函数也称为事件监听器，EventListener接口定义了事件响应函数的类型，事件被触发时，监听器会获得一个==event==参数，该参数为Event对象，内含事件相关信息
		
通过 `EventTarget.addEventListener(type,listener,useCapture)` 为元素添加多个事件响应函数
	type是监听事件类型，listener是事件响应函数地址，useCapture为true使用捕获事件模型，false使用冒泡事件模型
	
`removeEventListener(type,listener)`

4.事件指派
	事件指派实质上是创建并初始化一个空的、但==事件实现的接口与事件类型==和要**手动触发**的元素的事件类型相同的事件对象，然后调用元素的dispatchEvent()，将新创建的事件对象作为参数，实现手动触发事件

document.createEvent(eventType)
参数为事件接口类型的字符串，如'MouseEvent'
Event.initEvent(eventTypeArg,canBubbleArg,cancelableArg)
事件类型字符串，如'click'，是否支持冒泡，是否支持撤销

	另外，具体触发HTML元素的哪一个事件与Event.initEvent(eventTypeArg,canBubbleArg,cancelableArg)的后两个参数无关