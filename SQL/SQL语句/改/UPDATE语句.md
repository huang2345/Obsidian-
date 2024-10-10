`UPDATE <表名> SET <列名> = <表达式>`
更新记录的列的数据。在未使用WHERE子句进行条件选择时，该语句会更新所有记录的该列数据。
###### 多列更新
`UPDATE <表名> SET <列名1> = <值1>,...;`常用
`UPDATE <表名> SET (列1,2...) = (值1,2...);`有些DBMS无法使用
>使用UPDATE语句可以将值设置为NULL，但只限于未设置NOT NULL约束和主键约束
#### 搜索型UPDATE语句
UPDATE语句与DELETE语句一样，都可以通过WHERE子句进行条件选择。
`UPDATE <表名> SET <列名> = <表达式> WHERE <条件>;`
