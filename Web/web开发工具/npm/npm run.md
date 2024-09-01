执行自定义命令(node_modules/.bin中安装好的命令排列组合)，多用于将npm包复杂常用的命令缩短。

#### 串行执行
先后执行命令
`npx prettier --write && npx eslint src/*.js`
#### 并行执行
同时执行
`npm install & npm update`
