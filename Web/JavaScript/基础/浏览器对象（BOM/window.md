全局变量是Window对象的属性，全局函数是window对象的方法

属性：
window/self：Window属性等价于self，包含了对窗口自身的引用

属性只读：
document，history，navigator，screen，

方法：
alert：显示消息的警告框
prompt(提醒消息，默认值)：返回用户输入的字符串值
confirm：确认返回true

setInterval(函数地址,相隔时间ms)：设置计时器循环触发,返回ID
clearInterval：根据ID取消计时器

setTimeout：设置延时触发，参数列表与计时器相同，返回ID
clearTimeout：根据ID取消延时触发


| 属性                       | 说明               |
| ------------------------ | ---------------- |
| closed                   | 返回窗口是否已关闭        |
| defaultStatus            | 设置或返回窗口状态栏中的默认文本 |
| innerHeight/innerWidth   | 返回文档区的高度/宽度      |
| length                   | 设置或返回窗口中的框架数量    |
| name                     | 设置或返回窗口名称        |
| opener                   | 返回创建了这个窗口的窗口的引用  |
| outerHeight/outerWidth   | 窗口的外部高度/宽度       |
| parent                   | 返回父窗口            |
| status                   | 设置窗口状态的文本        |
| top                      | 返回顶层的先辈窗口        |
| screenLeft/Top,screenX/Y | 窗口左上角在屏幕上的XY坐标   |


| 方法          | 说明                     |
| ----------- | ---------------------- |
| blur        | 把键盘焦点从顶层窗口移开           |
| close       | 关闭浏览器窗口                |
| createPopup | 创建一个pop-up窗口           |
| focus       | 把键盘焦点给予下一个窗口           |
| moveBy      | 移动窗口指定像素               |
| moveTo      | 移动窗口到指定像素              |
| resizeBy    | 窗口增减指定像素               |
| resizeTo    | 窗口调整到指定像素              |
| open        | 打开一个新的浏览器窗口或查找一个已命名的窗口 |
| print       | 打印机打印当前窗口内容            |
| scrollBy    | 滚动指定像素                 |
| scrollTo    | 滚动到指定的像素               |

