##### 规则严重性
规则ID：
- "off"：关闭规则
- "warn"：警告
- "error"：触发错误，退出代码为1
###### 配置注释
用注释将规则配置写在源文件内。
`/* eslint xxx:"off" */`
配置注释可以为此处的规则添加描述，使用两个或多个`-`符
`/* eslint xxx:"off" -- hello world */`
>	配置注释优先级最高，在所有配置对象设置之后应用

###### 插件规则
插件的配置规则需要在规则名字前添加插件的命名空间 + `/` 例如：`example/rule1 : "warn"`
>	如果要在配置注释中使用，需要在能应用到的配置对象中的plugins对象中指定(在配置文件中加载好的)

### 禁用规则
###### 注释块禁用
`/* eslint-disable xxx */`禁用规则
`/* eslint-enable xxx */`启用规则
###### 注释行警用
`/* eslint-disable-line xxx */` `//eslint-disable-line`禁用当前行
`/* eslint-disable-next-line xxx */` `/* eslint-disable-next-line */`禁用下一行

###### 配置文件利用files和配置值的"off"禁用
`rules:{ "xxx":"off" }`


