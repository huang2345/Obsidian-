#### LIKE模糊查询
使用 LIKE 关键字实现模糊查询。
	在 LIKE 模糊查询中，我们使用通配符来代表零个或多个字符，从而能够快速地找到匹配的数据。
有如下 2 种通配符：
- 百分号（%）：匹配任意长度的任意字符序列。
- 下划线（\\\_）：匹配任意单个字符。
```
... where xxx like '%张%'
//查询xxx列中值包含'张'的
```
可以使用 `not like` 来查询不包含某关键字的信息。

#### ORDER BY排序
- ASC(升序，从小到大)
- DESC(降序，从大到小)

对查询结果排序，可以对多个字段进行排序
`SELECT ... from ... ORDER BY 字段 ASC`
#### LIMIT截断
截断查询结果，只获取`a~b?`条数据，`index为a，获取b条数据`
`SELECT ... from ... LIMIT a,b`
#### CASE WHEN条件分支
```
SELECT ..., 
CASE WHEN(条件1) THEN 结果1
	WHEN(条件2) THEN 结果2
	...
	ELSE 其他结果 END
```
```
SELECT name,
	CASE WHEN(name = 'xxx')
	THEN 'true'
	ELSE 'false'
	END AS 会不会C语言
```
#### 时间函数
- DATE：获取当前日期
- TIME：获取当前时间
- DATETIME：获取当前日期和时间
`SELECT DATE() as '日期'`
#### 字符串处理
- UPPER：大写
- LOWER：小写
- LENGTH：长度
`SELECT ... , UPPER(name) as upper_name from  表名`
#### HAVING子句
用于在分组聚合后对分组进行筛选。

**WHERE** 子句用于在 分组之前 进行过滤，而 **HAVING** 子句用于在 分组之后 进行过滤。
`SELECT ...,from 表名 GROUP BY ... HAVING 条件1,...`
