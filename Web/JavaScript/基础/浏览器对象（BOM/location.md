属性：
hash：设置或返回锚点链接，设置时无需添加#号
href：设置或返回地址，可以改变当前窗口的地址

| 属性       | 说明                 |
| -------- | ------------------ |
| host     | 设置或返回主机名和当前URL端口号  |
| hostname | 设置或返回当前URL的主机名     |
| pathname | 设置或返回路径部分          |
| port     | 设置或返回当前URL的端口号     |
| protocol | 设置或返回当前URL的协议      |
| search   | 设置或返回当前地址的参数(包含？号) |

| 方法              | 描述                        |
| --------------- | ------------------------- |
| assign(url)     | 加载新地址                     |
| reload(force)   | 刷新，若参数为true则从服务器刷新        |
| replace(newUrl) | 在history对象中使用newUrl替换当前文档 |
使用location的hash属性使用锚点跳转时，可以用<a name="xxx">的形式设置锚点，不想用a标签可以用其他标签，但属性要使用id