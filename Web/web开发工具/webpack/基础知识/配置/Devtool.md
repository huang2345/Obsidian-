#### source map
webpack打包源代码后，很难追踪**错误和警告**在源代码中的位置。因为打包后都包含在`output`输出后的bundle.js文件中，堆栈跟踪会直接指向bundle.js中。
为了更容易追踪错误和警告，JS提供了==source map==功能。该功能可以将编译打包后的代码映射回源代码。
source map会直接告诉开发者错误来源于哪一个源文件。
#### devtool : string
此选项控制是否生成，以及如何生成 source map。
以下内容解释各个选项值
##### inline-source-map
使用该选项后，如果出现错误，在浏览器中的错误提示中将会指示源文件。