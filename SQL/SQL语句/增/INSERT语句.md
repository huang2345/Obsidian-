#### 插入数据
```mysql
-- BEGIN TRANSACTION; 该行是postgreSQL的
START TRANSACTION;

INSERT INTO <表名> VALUES <(数据)>;
...
COMMIT;
```
>DBMS不同，开始插入行的指令语句也不同
#### INSERT语句
`INSERT INTO <表名> (列1,列2,...) VALUES (值1,值2,...);`
将标识符或值括在()内，这种形式称为**清单**。
对表进行全列INSERT时，可以省略列清单，值清单将会根据顺序赋值给每一列。

如果忽略了没有设置默认值的列，该数据的该列的值会被设置为NULL，如果该列的约束为NOT NULL，INSERT语句会报错

列清单与值清单必须保持一致
>使用默认值时，无需完全一致
>原则上，一次INSERT语句只会插入一行数据。但是，很多RDBMS都支持一次插入多行数据，这种功能被称为多行INSERT。
>`INSERT INTO <表名> VALUES 值清单1,值清单2,...;`多行INSERT写法
>Oracle不支持多行INSERT,Oracle通过`INSERT ALL INTO <表名> VALUES 值清单 INTO ...`
##### 使用默认值
创建表或添加列时通过DEFAULT约束来设置默认值
###### 显式
在值清单对应的位置中写为`DEFAULT`:
`INSERT INTO xxx (...) VALUES (...,DEFAULT,...);`
###### 隐式
可以通过在列清单和值清单中忽略设置了默认值的列将数据设置为默认值。
##### INSERT ... SELECT
通过将这两个子句结合，可以将表中的数据复制到另一个表。
```mysql
INSERT INTO <表名> <列清单> SELECT子句
```
