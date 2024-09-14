`Last-Modified`是一个响应标头。其中包含源头服务器认定的资源做出修改的日期及时间。它通常被用来判断接收到的或者存储的资源是否与服务器最新的资源一致。
#### 语法
```
Last-Modified: <day-name>, <day> <month> <year> <hour>:<minute>:<second> GMT
```
#### 指令
##### \<day-name>
"Mon", "Tue", "Wed", "Thu", "Fri", "Sat" 或 "Sun" 之一(区分大小写)
##### \<day>
两位数表示天数
##### \<month>
"Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec" 之一(区分大小写)。
##### \<year>
四位数表示年份
##### \<hour>
两位数表示小时
##### \<minute>
两位数表示分钟
##### \<seconds>
两位数表示秒数
##### GMT
国际标准时间。HTTP 中的时间均用国际标准时间表示，从来不使用当地时间。