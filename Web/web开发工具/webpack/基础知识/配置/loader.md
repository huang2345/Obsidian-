#### 概述
- loader 用于对模块的源代码进行转换。通过 **loader** 可以使 webpack 支持多种语言和预处理器语法编写的模块。**loader** 向 webpack 描述了如何处理非原生 **模块**，并将相关**依赖**引入到你的 **bundles**中。
- loader 可以使你在 `import` 或 "load(加载)" 模块时预处理文件。
- loader 可以将文件从不同的语言（如 TypeScript）**转换为** JavaScript 或将内联图像转换为 data URL。loader 甚至允许直接在JS模块中`import`css文件
- 除了模块之外，loader还可以支持在JS中直接导入资源文件(例如：图片、CSS、JSON、XML等数据文件)
#### 使用
想要使用loader，需要先用包管理器安装对应的loader(例如：css-loader、ts-loader)
##### 使用loader
有两种使用loader的方法：
- 配置文件
- 内联：在`import`语句中显示指定loader
###### 配置文件
==module.rules==允许你在webpack配置中指定多个loader。
loader按照从下到上(或从右到左)的顺序取值==(evaluate)/执行(execute)==
```js
module.exports = {
  module: {
    rules: [
      {
        test: /\.css$/,
        use: [
          { loader: 'style-loader' },
          {
            loader: 'css-loader',
            options: {
              modules: true,
            },
          },
          { loader: 'sass-loader' },
        ],
      },
    ],
  },
};
```
###### 内联
使用 `!` 将资源中的 loader 分开。每个部分都会相对于当前目录解析。
```js
import Styles from 'style-loader!css-loader?modules!./styles.css';
```
通过为内联 `import` 语句添加前缀，可以**覆盖配置**中的所有 loader, preLoader 和 postLoader：
- 使用 `!` 前缀，将禁用所有已配置的 normal loader(普通 loader)
    ```js
    import Styles from '!style-loader!css-loader?modules!./styles.css';
    ```
- 使用 `!!` 前缀，将禁用所有已配置的 loader（preLoader, loader, postLoader）
    ```js
    import Styles from '!!style-loader!css-loader?modules!./styles.css';
    ```
- 使用 `-!` 前缀，将禁用所有已配置的 preLoader 和 loader，但是不禁用 postLoaders
    ```js
    import Styles from '-!style-loader!css-loader?modules!./styles.css';
    ```
>选项可以传递查询参数，例如 `?key=value&foo=bar`，或者一个 JSON 对象，例如 `?{"key":"value","foo":"bar"}`。
#### 特性
- 支持链式调用
- 可以同步，也可以异步
- 运行在Node.js中，能执行任何操作
- 可以通过`options`对象配置
- - 除了常见的通过 `package.json` 的 `main` 来将一个 npm 模块导出为 loader，还可以在 module.rules 中使用 `loader` 字段直接引用一个模块。
- 插件(plugin)可以为 loader 带来更多特性。
- 能够产生额外的任意文件。
#### 解析loader
loader遵循**标准模块解析**规则。多数情况下，loader 将从**模块路径**加载（通常是从 `npm install`, `node_modules` 进行加载）。
