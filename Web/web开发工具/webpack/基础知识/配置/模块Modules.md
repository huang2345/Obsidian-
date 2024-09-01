在模块化编程中，开发者将程序分解为功能离散的 chunk，并称之为 **模块**。
#### 模块解析
当打包模块时，webpack 使用`enhanced-resolve`来解析文件路径。所依赖的模块可以是来自应用程序的代码或第三方库。 resolver 帮助 webpack 从每个 `require`/`import` 语句中，找到需要引入到 bundle 中的模块代码。
>resolver 是一个帮助寻找模块绝对路径的库。
# resolver : object
#### alias : object
创建模块的别名。
```js
resolve: {
    alias: {
      Utilities: path.resolve(__dirname, 'src/utilities/'),
      Templates: path.resolve(__dirname, 'src/templates/'),
    },
  },
```
你可以这样使用别名：
```js
import Utility from 'Utilities/utility';
```
也可以给alias中的键值对的键在后面添加一个`$`，以表示精准匹配。
```js
 alias: {
      xyz$: path.resolve(__dirname, 'path/to/file.js'),
    },
...
import test from 'xyz';
```
>`resolve.alias` 优先级高于其它模块解析方式。
#### modules : \[string]
webpack 解析模块时应该搜索的目录。
#### extensions : string\[]
`extensions : ['.js','.json','wasm']`
按**顺序**解析这些后缀名。如果有多个文件有相同的名字，但后缀名不同，webpack 会解析列在数组首位的后缀的文件 并跳过其余的后缀。
能使用户在导入模块时不写后缀名：`import test`
>extensions有一个默认拓展名，可以使用`'...'`来访问默认拓展名
##### 解析规则
###### 绝对路径
`import /src/xxx`
由于已经获得文件的绝对路径，因此不需要再做进一步解析。
###### 相对路径
根据当前文件的相对路径。
###### 模块路径
```js
import 'module';
import 'module/lib/file';
```
在配置文件modules.resolve属性中指定的所有目录中检索模块，可以通过配置别名的方式替换一般的模块路径(使用resolve.alias)
