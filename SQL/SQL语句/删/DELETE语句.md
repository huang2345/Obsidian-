#### DELETE FROM <表名>
删除表中全部数据
##### 指定删除对象
通过添加WHERE子句可以指定删除的记录。这种指定了删除对象的DELECT语句被称为**搜索型DELECT**
`DELECT FROM <表名> WHERE <条件>`
##### TRUNCATE
标准SQL中用来从表中删除数据的只有DELETE语句。但是，很多数据库还有`TRUNCATE`语句。

`TRUNCATE <表名>`

与DELETE不同，该语句只能删除表中的全部数据，不能通过WHERE子句指定条件。也正是因为不能控制删除对象，所以处理速度比DELETE快