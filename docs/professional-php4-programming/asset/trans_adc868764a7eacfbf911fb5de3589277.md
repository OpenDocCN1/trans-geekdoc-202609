
ALTER [COLUMN] column { SET DEFAULT value | DROP DEFAULT }
ALTER TABLE table [*]
RENAME [COLUMN] column TO newcolumn
ALTER TABLE table
RENAME TO newtable
ALTER TABLE table
ADD table constraint definition
ALTER TABLE table
OWNER TO new owner

ALTER TABLE允许您更改表的结构。例如，要向details表添加列，语句如下：

```
library=# ALTER TABLE details ADD COLUMN pages INT;
ALTER
library=# \d details
Table "details"
Attribute | Type | Modifier
isbn | character varying(13) | not null
price | double precision |
num_of_books | integer | not null
num_booked | integer | not null
series_id | integer | not null
pages | integer |
Index: details_pkey
```

PostgreSQL将新列添加到表定义的末尾。此时，无法在现有列之间插入新列。

可以使用ALTER TABLE语句轻松重命名列：

```
library=# ALTER TABLE details RENAME COLUMN pages TO num_pages;
ALTER
library=# \d details
Table "details"
Attribute | Type | Modifier
isbn | character varying(13) | not null
price | double precision |
num_of_books | integer | not null
num_booked | integer | not null
series_id | integer | not null
num_pages | integer |
Index: details_pkey
```

PostgreSQL目前尚不允许从现有表中删除列。文档中记录的变通方法是将继续的数据存储在临时表中，删除旧表，使用修改后的表定义重新创建它，然后恢复旧数据。要从上面的details表中删除num_booked和num_pages列，您可以执行类似以下的操作：

```
CREATE TABLE temp AS SELECT ISBN, price, num_of_books, series_ID FROM details;
DROP TABLE details;
CREATE TABLE details (
   ISBN    VARCHAR(13) PRIMARY KEY,
   price   FLOAT,
   num_of_books INT NOT NULL,
   series_ID INT NOT NULL
);
INSERT INTO details SELECT * FROM temp;
DROP TABLE temp;
```

## DROP TABLE

```
DROP TABLE name [, ...]
```

此语句将表（包括其数据）从数据库中删除。如果我们希望删除名为"formats"和"timezones"的两个表：

```
library=# DROP TABLE formats, timezones;
DROP
```

## DROP DATABASE

```
DROP DATABASE database_name
```

此语句将删除整个数据库，包括所有表、索引和数据：

```
template1=# drop database library;
DROP DATABASE
```

> 在删除数据库之前，您应该退出数据库（不要登录其中）。

## 数据操作和检索语句

这些语句用于访问数据库中的数据，以及操作数据。

## INSERT

```
INSERT INTO table [(column [, ...])]
{DEFAULT VALUES | VALUES (expression [, ...]) | SELECT query}
```

INSERT用于向表中添加新记录。请注意，以下示例中的字符串使用单引号括起来。SQL标准规定，字符值必须始终以这种方式引用。数值类型和特殊关键字NULL不加引号：

```
library=# INSERT INTO title
library=# VALUES ('1861005156', 'Beginning Databases with PostgreSQL')
library=# ;
INSERT 101798 1
```

如果您尝试插入一个包含与现有条目相同主键值的新条目，插入尝试将失败。

## DELETE

```
DELETE FROM [ONLY] table [WHERE condition]
```

DELETE用于从表中删除记录。WHERE子句是DELETE、UPDATE和SELECT查询的重要组成部分，因为它允许您指定条件来确定查询将影响哪些记录。以下查询将仅删除ISBN字段值为"1861003730"的记录：

```
library=# DELETE FROM title WHERE ISBN = '1861003730';
DELETE 1
```

> 如果从DELETE语句中省略WHERE子句，表中的每条记录都将被删除。

## UPDATE

```
UPDATE [ONLY] table SET col = expression [, ...] [FROM fromlist]
[WHERE condition]
```

UPDATE用于更改数据库中现有记录中的数据。仔细指定WHERE条件非常重要。以下查询仅影响了一行，但如果多个记录具有相同的ISBN，它有可能更改许多行。由于ISBN是主键，在本示例中这是不可能的：

```
library=# UPDATE title SET book_title='New Title' WHERE ISBN='1861003730';
UPDATE 1
```

尽管PostgreSQL遵循参照完整性概念，但UPDATE或DELETE操作本身并没有内置自动保护。例如，如果author_ID从author表中重命名或删除，author_title表中可能仍有引用当前不存在记录的条目。因此，UPDATE或DELETE操作已破坏参照完整性。

> 如果从UPDATE语句中省略WHERE子句，表中的每条记录都将被更新。

## SELECT

```
SELECT [ALL | DISTINCT [ON (expression [, ...])]]
* | expression [AS output_name] [, ...]
[FROM from_item [, ...]]
[WHERE condition]
[GROUP BY expression [, ...]]
[HAVING condition [, ...]]
[{ UNION | INTERSECT | EXCEPT [ALL ] select}]
[ORDER BY expression [ASC | DESC | USING operator] [, ...]]
[FOR UPDATE [OF tablename [, ...]]]
[LIMIT { count | ALL } [{ OFFSET | , } start]]
```

from_item可以是：

```
[ONLY] table_name [*]
[[AS] alias [(column_alias_list)]]
|
(select)
[AS] alias [(column_alias_list)]
|
from_item [NATURAL] join_type from_item
[ON join_condition | USING (join_column_list)]
```

SELECT用于从一个或多个表中检索数据。要指定我们想要返回的字段：

```
library=# SELECT ISBN, price FROM details;
 isbn | price
------------+
1861003730 | 39.95
1861005156 | 39.95
1861005083 | 29.95
1861002092 | 49.95
1861005334 | 24.95
(5 rows)
```

要表示"所有字段"，请使用星号(*)：

```
library=# SELECT * FROM details;
 isbn | price | num_of_books | num_booked | series_id
------------+---------+--------------+------------+----------
1861003730 | 39.95 | 10 | 10 | 1
1861005156 | 39.95 | 10 | 10 | 1
1861005083 | 29.95 | 10 | 10 | 1
1861002092 | 49.95 | 10 | 10 | 1
1861005334 | 24.95 | 10 | 10 | 1
(5 rows)
```

WHERE子句在SELECT语句中的使用方式与在DELETE和UPDATE语句中相同。要仅选择价格值大于或等于39.95的记录，我们指定一个条件：

```
library=# SELECT * FROM details WHERE price >= 39.95;
         isbn | price | num_of_books | num_booked | series_id
-------------+-------+--------------+------------+-----------
 1861003730 | 39.95 | 10 | 10 | 1
 1861005156 | 39.95 | 10 | 10 | 1
 1861002092 | 49.95 | 10 | 10 | 1
(3 rows)
```

ORDER BY使得可以控制结果集的排序顺序：

```
library=# SELECT * FROM details WHERE price >= 39.95 ORDER BY ISBN;
         isbn | price | num_of_books | num_booked | series_id
-------------+-------+--------------+------------+-----------
 1861002092 | 49.95 | 10 | 10 | 1
 1861003730 | 39.95 | 10 | 10 | 1
 1861005156 | 39.95 | 10 | 10 | 1
(3 rows)
```

## PHP的PostgreSQL接口

既然我们已经讨论了PostgreSQL操作的基础知识，就可以开始介绍PHP的PostgreSQL接口了。以下是对PHP中最常用的PostgreSQL函数的描述。有关完整列表或下列函数的更多详细信息，请参阅PHP在线文档 http://www.php.net/pgsql/。

## pg_connect()

```
int pg_connect(string conn_string)
```

此函数根据连接字符串中提供的参数建立与PostgreSQL服务器的连接。如果成功，它将返回一个链接标识符（将是正整数），否则返回false：

```
<?php
/Connect.php
$conn = pg_connect("dbname=library user=postgres")
    or die("Could not connect to PostgreSQL.");
echo("Connection successful.");
pg_close($conn);
?>
```

连接字符串可以由以下一个或多个参数组成：

| 选项 | 含义 | 默认值 |
|---|---|---|
| dbname | 要连接的数据库 | $PGDATABASE |
| user | 连接时使用的用户名 | $PGUSER |
| password | 指定用户的密码 | $PGPASSWORD 或无 |
