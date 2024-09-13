**`Expires`** 响应标头包含响应被视为过期的日期/时间。
>如果响应中有指令为`max-age`或`s-maxage`的`Cache-Control` 标头，则 `Expires` 标头会被忽略。

#### 语法
```
Expires: <http-date>
```
#### 指令
\<http-date>
- HTTP时间戳
