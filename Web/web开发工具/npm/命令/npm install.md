将`package.json`中已添加的依赖安装
#### 选项
- --save：将其添加到dependency
- --save-dev：将其添加到devDependencies
- --no-save：仅安装，不将其添加到`package.json`中
- --save-optional：将其添加到optionalDependencies
- --no-optional：将阻止可选依赖的安装
>devDependencies是仅在开发环境中的依赖，dependency是生产环境
#### 安装特定版本
`npm install <package-name>@<version>`