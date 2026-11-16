

## 数据定义语句

数据定义语句用于创建和修改数据库的结构。

### CREATE DATABASE

```
CREATE DATABASE database_name
```

此语句用于创建新数据库。要创建名为 Library 的新数据库，请在 mysql> 命令提示符下输入以下命令：

```
mysql> CREATE DATABASE Library;
Query OK, 1 row affected (0.01 sec)
```

分号 (;) 表示语句已结束。在 PHP 代码中发出 SQL 语句时，不需要分号。

### USE

```
USE database_name
```

数据库创建后，在对其执行任何其他操作之前，必须先将其选中。在 mysql 客户端中，USE 用于选择数据库。要选择现有数据库 Library：

```
mysql> USE Library;
Database changed
```

此语句既不是数据定义语句也不是数据操纵语句，但在 mysql 客户端的 SQL 解释器中，要完成其中任何一项都需要它，因此我们在讨论早期就介绍了它。选择现有数据库的另一种方法是在进入 mysql 客户端时，将其名称作为命令行参数提供：

```
mysql Library
```

USE 仅适用于 SQL 解释器。在 PHP 应用程序中，数据库是使用内置函数（例如 mysql_select_db() 和 mysql_db_query()，适用于 MySQL 的情况）来选择的。PHP 的数据库函数将在本章后面的 PHP 和关系数据库部分中讨论。

### CREATE TABLE

```
CREATE [TEMPORARY] TABLE [IF NOT EXISTS] tbl_name [(create_definition,...)]
[table_options] [IGNORE|REPLACE select_statement]
```

create_definition：

```
col_name data_type [NOT NULL | NULL] [DEFAULT default_value]
[AUTO_INCREMENT] [PRIMARY KEY] [reference_definition]
or  PRIMARY KEY (index_col_name,...)
or  KEY [index_name] (index_col_name,...)
or  INDEX [index_name] (index_col_name,...)
or  UNIQUE [INDEX] [index_name] (index_col_name,...)
or  FULLTEXT [INDEX] [index_name] (index_col_name,...)
or  [CONSTRAINT symbol] FOREIGN KEY index_name (index_col_name,...)
    [reference_definition]
or  CHECK (expr)
```

CREATE TABLE 用于在所选数据库中定义新表。值得注意的是，此语法特定于 MySQL。其中几个选项在其他 RDBMS 中不可用。上述选项的完整详细信息可在 MySQL 的文档网站 http://www.mysql.com/documentation/ 上查找。

让我们尝试使用 details 表的典型调用：

```
mysql> CREATE TABLE details (
    ISBN VARCHAR (13) NOT NULL,
    price FLOAT,
    num_of_books INT (11) UNSIGNED NOT NULL,
    num_booked INT (11) UNSIGNED NOT NULL,
    series_ID INT (11) NOT NULL,
    PRIMARY KEY (ISBN)
);
Query OK, 0 rows affected (0.09 sec)
```

在此示例中，我们仅使用 MySQL 中许多可用数据类型中的三种：

- VARCHAR 是用于存储字符数据的多种类型之一
- INT 是用于存储整数数据的多种类型之一
- FLOAT 列是存储浮点数的一种方式

列数据类型的具体信息将根据 RDBMS 而有所不同。因此，建议查阅各个系统的 SQL 文档。

类型后括号中出现的数字表示相应字段的最大长度：

- ISBN 最多可包含十三个字符
- NOT NULL 表示字段不能留空
- UNSIGNED 指定字段只能包含正值

PRIMARY KEY 行将 ISBN 字段声明为该表的主键。我们在本章前面讨论过主键。

让我们来看看 title 表的 CREATE 语句：

```
mysql> CREATE TABLE title (
  ISBN VARCHAR (13) NOT NULL,
  book_title VARCHAR (255) NOT NULL,
  PRIMARY KEY (ISBN)
);
Query OK, 0 rows affected (0.00 sec)
```

### DESCRIBE

MySQL 解释器中的 DESCRIBE 语句显示表的结构。这是检查工作的好方法。从现在起，在讨论表结构时，我们将只显示 DESCRIBE 输出，因为它比 CREATE TABLE 语法更易于阅读。

在下面的描述中，Null 列指示哪些字段可能包含 null 值。Key 列显示放置在字段上的键（PRI 表示主键）。Default 列显示为字段定义的默认值，Extra 列显示字段的任何其他详细信息：

| 字段 | 类型 | 允许空 | 键 | 默认值 | 额外 |
|-------|------|------|-----|---------|-------|
| ISBN | varchar(13) | | PRI | | |
| price | float | YES | | NULL | |
| num_of_books | int(10) unsigned | | | 0 | |
| num_booked | int(10) unsigned | | | 0 | |
| series_ID | int(11) | | | 0 | |

让我们创建其余表：

```
mysql> CREATE TABLE author (
  auth_ID INT (11) NOT NULL AUTO_INCREMENT,
  auth_name VARCHAR (128) NOT NULL,
  PRIMARY KEY (auth_ID)
);
Query OK, 0 rows affected (0.00 sec)
```

请注意，这里我们使用了 AUTO_INCREMENT 列。AUTO_INCREMENT 列通过递增前一行的值来自动填充自身。这保证了唯一值。AUTO_INCREMENT 修饰符仅适用于整数字段：

```
mysql> CREATE TABLE authortitle (
  ISBN VARCHAR (13) NOT NULL,
  auth_ID INT (11) NOT NULL,
  PRIMARY KEY (ISBN, auth_ID)
);
Query OK, 0 rows affected (0.00 sec)
```

在此表中，主键由两个字段组成——ISBN 和 auth_ID：

```
mysql> CREATE TABLE series (
   series_ID INT (11) NOT NULL AUTO_INCREMENT,
   book_series VARCHAR (64) NOT NULL,
   PRIMARY KEY (series_ID)
 );
Query OK, 0 rows affected (0.00 sec)
```

```
mysql> CREATE TABLE users (
   username CHAR (32) NOT NULL,
   password CHAR (32) NOT NULL,
   PRIMARY KEY (username)
 );
Query OK, 0 rows affected (0.00 sec)
```

此最后表定义使用两个 CHAR 字段，而不是 VARCHAR 字段。VARCHAR 字段是具有最大长度的可变长度字符类型。然而，数据库只需要为存储在字段中的实际字符串的字符数腾出空间，因此字符串 "ELEPHANT" 只会在数据库中使用八个字符的空间，即使 VARCHAR 字段的最大尺寸可能大于八。这可以节省大量空间，但管理可变长度字段也会带来轻微的性能损失。

另一方面，CHAR 字段始终预留其最大长度的空间。额外的字符空间通常用 NULL 值填充。虽然这可能看起来是空间浪费，但数据库访问 CHAR 字段更快，因为它是已知的固定大小。

> 某些 DBMS（如 MySQL）如果表中包含任何其他可变长度字段类型，会自动将 CHAR 字段升级为 VARCHAR 字段。在同一表定义中混合使用 CHAR 和 VARCHAR 字段会导致所有字符字段都变为 VARCHAR。

### ALTER TABLE

```
ALTER [IGNORE] TABLE tbl_name alter_spec [, alter_spec ...]
```

alter_spec：

```
ADD [COLUMN] create_definition [FIRST | AFTER column_name ]
or ADD [COLUMN] (create_definition, create_definition,...)
or ADD INDEX (index_name) (index_col_name,...)
or ADD PRIMARY KEY (index_col_name,...)
or ADD UNIQUE [index_name] (index_col_name,...)
or ADD FULLTEXT [index_name] (index_col_name,...)
or ADD [CONSTRAINT symbol] FOREIGN KEY index_name (index_col_name,...)
   [reference_definition]
or ALTER [COLUMN] col_name {SET DEFAULT literal | DROP DEFAULT}
or CHANGE [COLUMN] old_col_name create_definition
or MODIFY [COLUMN] create_definition
or DROP [COLUMN] col_name
```

