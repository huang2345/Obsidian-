**`Content-Encoding`** 列出了对当前实体消息（消息荷载）应用的任何编码类型，以及编码的顺序。
Content-Encoding 主要用于在不丢失原媒体类型内容的情况下压缩消息数据。

一般建议服务器应对数据尽可能地进行压缩，并在适当情况下对内容进行编码。对一种压缩过的媒体类型如 zip 或 jpeg 进行额外的压缩并不合适，因为这反而有可能会使荷载增大。
#### 语法
```HTTP
Content-Encoding: deflate, gzip   // 多个，按应用的编码顺序列出
```
#### 指令
###### gzip
表示采用 [Lempel-Ziv coding](https://zh.wikipedia.org/wiki/LZ77%E4%B8%8ELZ78#LZ77)（LZ77）压缩算法，以及 32 位 CRC 校验的编码方式。这个编码方式最初由 UNIX 平台上的 _gzip_ 程序采用。出于兼容性的考虑，HTTP/1.1 标准提议支持这种编码方式的服务器应该识别作为别名的 `x-gzip` 指令。
###### compress
采用 [Lempel-Ziv-Welch](https://zh.wikipedia.org/wiki/LZW)（LZW）压缩算法。这个名称来自 UNIX 系统的 _compress_ 程序，该程序实现了前述算法。
与其同名程序已经在大部分 UNIX 发行版中消失一样，这种内容编码方式已经被大部分浏览器弃用，部分因为专利问题（这项专利在 2003 年到期）。
######  deflate
采用 [zlib](https://zh.wikipedia.org/wiki/zlib) 结构（在 [RFC 1950](https://datatracker.ietf.org/doc/html/rfc1950) 中规定），和 [deflate](https://zh.wikipedia.org/wiki/DEFLATE) 压缩算法（在 [RFC 1951](https://datatracker.ietf.org/doc/html/rfc1951) 中规定)。
###### br
表示采用 [Brotli](https://zh.wikipedia.org/wiki/Brotli) 算法的编码方式。