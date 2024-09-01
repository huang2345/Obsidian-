###### 安装`npm init @eslint/config`
安装的同时启动eslint的配置初始化脚本`npx eslint --init`

###### 使用的原因
1. 高可移植性
2. 相比较于IDE复杂的配置系统，只有一个配置文件，方便
3. 可针对不同项目和需求做出不同的配置效果

#### 使用可共享的配置包
可共享配置是导出配置对象的npm包。该包应该应该作为依赖项安装，然后在配置文件中引用。
```js
import config from 'eslint-config-example';
export default[
	config,
]
```
一些可共享配置导出了多个配置对象，这时需要对导入的对象使用展开运算符`...config`
#### 配置文件使用
配置文件优先级：`.js > .mjs > .cjs`，命令行可以通过`--config`选项指定备用配置文件来阻止搜素配置文件
