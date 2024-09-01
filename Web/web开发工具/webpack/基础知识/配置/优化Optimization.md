从webpack 4开始，会根据mode配置来执行不同的优化。但依旧可以手动设置
## splitChunks : object
###### 历史
最初，chunks（以及内部导入的模块）是通过内部 webpack 图谱中的父子关系关联的。`CommonsChunkPlugin` 曾被用来避免他们之间的重复依赖，但是不可能再做进一步的优化。
从 webpack v4 开始，移除了 `CommonsChunkPlugin`，取而代之的是 `optimization.splitChunks`。
###### 默认值
默认情况下，它只会影响到按需加载的 chunks，因为修改 initial chunks 会影响到项目的 HTML 文件中的脚本标签。
webpack 将根据以下条件自动拆分 chunks：
- 新的 chunk 可以被共享，或者模块来自于 `node_modules` 文件夹
- 新的 chunk 体积大于 20kb（在进行 min+gz 之前的体积）
- 当按需加载 chunks 时，并行请求的最大数量小于或等于 30
- 当加载初始化页面时，并发请求的最大数量小于或等于 30
当尝试满足最后两个条件时，最好使用较大的 chunks。
#### automaticNameDelimiter : string
默认情况下，webpack 将使用 chunk 的来源和名称生成名称。该选项使开发者可以指定生成名称之间分隔符
>	webpack自动生成的chunks文件名与output中设置的bundle名字不同。在 Webpack 打包过程中，`output.filename` 定义了主文件的名称，而 chunks 文件名则负责管理分割后的代码块

#### chunks : 'all' | 'async' | 'initial'
表示选择哪些chunk进行优化。`all`意味着 chunk 可以在异步和非异步 chunk 之间共享。
>	可以使用函数去做更精细的控制
```js
module.exports = {
  //...
  optimization: {
    splitChunks: {
      chunks(chunk) {
        // exclude `my-excluded-chunk`
        return chunk.name !== 'my-excluded-chunk';
      },
    },
  },
};
```
#### maxAsyncRequests : number
按需加载时的最大并行请求数。
#### maxInitialRequests : number
入口的最大并行请求数。
#### defaultSizeTypes : string\[\]
该选项用于定义在自动代码分割时，哪些类型的文件的大小在chunk中会被考虑，进而影响webpack决定模块被分割在不同的chunk中。
	例子：`defaultSizeTypes: ['javascript','unknown']`
#### minChunks : number
拆分前必须共享模块的最小chunk数量

#### hidePathInfo : boolean
为由 maxSize 分割的部分创建名称时，阻止公开路径信息。
#### minSize : number
生成chunk的最小大小(字节单位)
#### minSizeReduction : number
生成一个chunk需要减少主chunk(bundle)文件多少的大小。
例如：该属性值为`10000 bytes`，bundle文件原本为30000bytes，生成chunk后大小至少减少1w字节，那么该chunk可以生成。
>	生成chunk需要`minSizeReduction`和`minSize`都满足
#### enforceSizeThreshold : number
当chunk大小超过该属性值时，强制执行代码分割。即使其他分割条件没有满足，例如：minSize
#### minRemainingSize : number
确保拆分后最小的chunk超过该属性值，以此避免chunk大小为0。`development模式`中默认为0，其他情况默认该值为`minSize`的值。
>	该属性仅在剩余单个chunk时生效
#### layer : RegExp | string | Function
按模块层将模块分配给缓存组。
#### maxSize : number
设置分割chunk的最大大小。如果大小超过该属性值，webpack会尝试将其分割为较小的chunk。但该属性和`minSize`不代表chunk的大小一定不能超过。
>`maxSize` 比 `maxInitialRequest/maxAsyncRequests` 具有更高的优先级。
>实际优先级是 `maxInitialRequest/maxAsyncRequests < maxSize < minSize`。
>设置 `maxSize` 的值会同时设置 `maxAsyncSize` 和 `maxInitialSize` 的值。
#### maxAsyncSize : number
该属性与`maxSize`的区别在于该属性只影响动态加载的chunk
#### maxInitialSize : number
该属性与`maxSize`的区别在于该属性只影响最初加载的chunk
#### name : boolean | (module,chunks,cacheGroupKey)=>string | sting
拆分 chunk 的名称。设为 `false` 将保持 chunk 的相同名称。这是生产环境下构建的建议值。

提供字符串或函数使你可以使用自定义名称。指定字符串或始终返回相同字符串的函数会将所有常见模块和 vendor 合并为一个 chunk。这可能会导致更大的初始下载量并减慢页面加载速度。
`chunk.name` 和 `chunk.hash` 属性（其中 `chunk` 是 `chunks` 数组的一个元素）在选择 chunk 名时特别有用。