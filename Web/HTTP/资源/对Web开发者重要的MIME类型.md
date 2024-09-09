#### application/octet-stream
二进制文件的默认值。这意味着未知的二进制文件
#### text/plain
文本文件的默认值。它其实意味着未知的文本文件，但浏览器认为是可以直接展示的。
>`text/plain`并不意味着“任何类型的文本数据”。

#### text/css
在网页中要被解析为CSS的文件必须指定MIME为`text/css`。
通常，如果服务器不识别 CSS 文件的 `.css` 后缀，则可能将它们以 MIME 为 `text/plain` 或 `application/octet-stream` 来发送给浏览器：在这种情况下，大多数浏览器不将其识别为 CSS 文件而直接忽略。
#### text/html
所有的HTML内容都应该使用这种类型。XHTML的其他 MIME 类型（如 `application/xml+html`）现在基本不再使用。
#### text/javascript
JS应该始终使用该类型。
某些 JS 内容在 MIME 类型中错误地使用了 `charset` 参数，以指定脚本内容的字符集。对于 JavaScript 内容来说，`charset` 参数无效，在大多数情况下会导致脚本加载失败。
#### 图片类型
- image/apng
- image/avif
- image/gif
- image/jpeg
- image/png
- image/svg+xml
- image/webp
#### 音频与视频类型
|MIME 类型|音频或视频类型|
|---|---|
|`audio/wave`、`audio/wav`、`audio/x-wav`、`audio/x-pn-wav`|采用 WAVE 容器的音频文件。一般支持 PCM 音频编码（WAVE codec "1"），其他解码器有限支持（如果有的话）。|
|`audio/webm`|采用 WebM 容器的音频文件。Vorbis 和 Opus 是 WebM 规范官方支持的最常用的解码器。|
|`video/webm`|采用 WebM 容器的音视频文件。VP8 和 VP9 是其最常用的视频解码器。Vorbis 和 Opus 是其最常用的音频解码器。|
|`audio/ogg`|采用 OGG 容器的音频文件。Vorbis 是这个多媒体文件格式最常用的音频解码器。现在，同样也支持 Opus。|
|`video/ogg`|采用 OGG 容器的音视频文件。常用的视频解码器是 Theora；常用的音频解码器为 Vorbis，不过 Opus 也变得越来越常用。|
|`application/ogg`|采用 OGG 容器的音视频文件。常用的视频解码器是 Theora；音频解码器为 Vorbis。|
#### multipart/form-data
可用于表单从浏览器发送信息给服务器
#### multipart/byteranges
用于把部分的响应报文发送回浏览器