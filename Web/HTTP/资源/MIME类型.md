>	浏览器通常使用MIME类型而不是文件扩展名来决定如何处理URL，因此服务器在`Content-Type`响应标头的设置非常重要。

#### 构造
MIME类型通常仅包含两个部分：**type/sub\type**(子类型)
子类型标识了更具体的类型，例如`text`类型，其子类型包括`plain`(纯文本)、`html`、`calender(.ics文件)`

MIME类型有一个可选的**参数**，例如`text`有`charset`参数
#### 类型
类型可分为两类，独立的(discrete)和多部分的(multipart)。

独立类型代表单一文件；而多部分类型可以代表由多个部分组合成的文件，其中每个部分都可能有自己的MIME类型；
此外，也可以代表多个文件被封装
##### 独立类型
IANA(互联网号码分配局)目前注册的独立类型如下：
###### application
不明确属于其他类型之一的任何二进制数据。
通用二进制数据（或真实类型未知的二进制数据）是 `application/octet-stream`。其他常用的示例包含 `application/pdf`、`application/pkcs8` 和 `application/zip`。（
###### audio
音频或音乐数据
###### example
在MIME类型中用作**占位符**的保留类型，例如：某audio类型的具体子类型未知，可以先用该类型确保不会直接报错，`audio/example`
###### font
字体/字型。常见的如font/ttf、font/woff
###### image
图像或图形数据，常见的有：`image/jpeg`、`image/png` 和 `image/svg+xml`
###### model
三维物体或场景的模型数据。
###### text
纯文本
###### video
视频
##### 多部分类型
代表一个复合文档。
HTTP不会特殊处理这个复合文档，如果浏览器不知道如何处理，很可能会作为下载文件被下载器打开。除了表单的POST方法中使用的`multipart/form-data`，以及用来发送部分文档，与 `206``Partial Content` 一同使用的 `multipart/byteranges`。
###### message
封装其他信息。
例如，`message/rfc822`（用于转发或回复信息的引用）和 `message/partial`（允许将大段信息自动拆分成小段，由收件人重新组装）是两个常见的例子。
###### multipart
由多个组件组成的数据。
例如，`multipart/from-data`(用于FormData API生成的数据)