
| Australia | 12 |

MySQL 提供了预期的 ANSI SQL 语法，要求使用 `sql_mode` 使 `GROUP BY` 语句包含所有非标量函数列。列表 1-32 显示了此示例。

### LISTING 1-32: count-group.sql

```sql
SET SESSION sql_mode=ONLY_FULL_GROUP_BY;

SELECT country, COUNT(*)
FROM   flags;
```

ERROR 1140 (42000): Mixing of GROUP columns (MIN(),MAX(),COUNT(),...) with no GROUP columns is illegal if there is no GROUP BY clause

```sql
SELECT country, COUNT(*) AS color_count
FROM   flags
GROUP BY country;
```

| country | color_count |
|---|---|
| Australia | 3 |
| Canada | 2 |
| Japan | 2 |
| Sweden | 2 |
| USA | 3 |

存在一个不返回数值值的标量函数；这就是列表 1-33 中显示的 `GROUP_CONCAT()` 函数。

### LISTING 1-33: count-group-concat.sql

```sql
SELECT country, GROUP_CONCAT(color) AS colors
FROM   flags
GROUP BY country;
```

| country | colors |
|---|---|
| Australia | Blue,Red,White |
| Canada | Red,White |
| Japan | Red,White |
| Sweden | Blue,Yellow |
| USA | Blue,Red,White |

```sql
SELECT country, GROUP_CONCAT(color) AS colors, COUNT(*) AS color_count
FROM flags
GROUP BY country;
```

| country | colors | color_count |
|---|---|---|
| Australia | Blue,Red,White | 3 |
| Canada | Red,White | 2 |
| Japan | Red,White | 2 |
| Sweden | Blue,Yellow | 2 |
| USA | Blue,Red,White | 3 |

5 rows in set (0.00 sec)

### WITH ROLLUP

`GROUP BY` 语法的特性是额外的关键字 `WITH ROLLUP`。使用此语法，返回的行包括每个 `GROUP BY` 列的聚合行。这由 `NULL` 表示。列表 1-34 中的输出显示了单列和双列示例：

### LISTING 1-34: count-with-rollup.sql

```sql
SELECT country, COUNT(*) AS color_count
FROM flags
GROUP BY country WITH ROLLUP;
```

| country | color_count |
|---|---|
| Australia | 3 |
| Canada | 2 |
| Japan | 2 |
| Sweden | 2 |
| USA | 3 |
| NULL | 12 |

```sql
SELECT c.color, c.is_dark, COUNT(*)
FROM colors c, flags f
WHERE c.color = f.color
GROUP BY c.color, c.is_dark WITH ROLLUP;
```

| color | is_dark | COUNT(*) |
|---|---|---|
| Blue | yes | 3 |
| Blue | NULL | 3 |
| Red | no | 4 |
| Red | NULL | 4 |
| White | no | 4 |
| White | NULL | 4 |
| NULL | NULL | 11 |

### HAVING

为了限制使用 `GROUP BY` 对任何标量函数返回的聚合行列表，您使用 `HAVING` 子句来定义条件，而不是 `WHERE` 子句。列表 1-35 显示了一个示例。

### LISTING 1-35: having.sql

```sql
SELECT country, GROUP_CONCAT(color) AS colors
FROM flags
GROUP BY country
HAVING COUNT(*) = 2;
```

| country | colors |
|---|---|
| Canada | Red,White |
| Japan | Red,White |
| Sweden | Blue,Yellow |

您可以像前面的示例所示使用在 `SELECT` 子句中未定义的标量函数。与 `ORDER BY` 不同，您必须指定列的名称；数字列顺序不是允许的语法。

## MySQL 中的逻辑运算和流程控制

MySQL 对任何逻辑都有三种状态：`TRUE`、`FALSE` 或 `NULL`：

```sql
mysql> SELECT TRUE,FALSE,NULL;
```

| TRUE | FALSE | NULL |
|---|---|---|
| 1 | 0 | NULL |

诸如 `=`、`<=>`、`IS`、`IS NOT`、`IN`、`ISNULL` 等比较操作将导致这三种状态之一：

```sql
mysql> SELECT 'A' IS NOT NULL, 'A' IS NULL, NULL = NULL, NULL IS NULL;
```

| 'A' IS NOT NULL | 'A' IS NULL | NULL = NULL | NULL IS NULL |
|---|---|---|---|
| 1 | 0 | NULL | 1 |

MySQL 对 `TRUE` 状态始终返回 1，任何非零值都计算为 `TRUE`。

```sql
mysql> SELECT 5 IS TRUE, 0 IS FALSE, 10 IS NOT NULL;
```

| 5 IS TRUE | 0 IS FALSE | 10 IS NOT NULL |
|---|---|---|
| 1 | 1 | 1 |

### 逻辑运算符

MySQL 有四个逻辑控制运算符：`AND`、`OR`、`NOT` 和 `XOR`。其中三个运算符也有简写表示：`&&`（`AND`）、`||`（`OR`）、`!`（`NOT`）。这些简写表示不应与位运算符混淆，后者是单个字符 `&` 和 `|`。

```sql
mysql> SELECT TRUE AND TRUE, TRUE AND FALSE, TRUE AND NULL, NULL AND NULL;
```

| TRUE AND TRUE | TRUE AND FALSE | TRUE AND NULL | NULL AND NULL |
|---|---|---|---|
| 1 | 0 | NULL | NULL |

```sql
mysql> SELECT TRUE OR TRUE, TRUE OR FALSE, TRUE OR NULL, NULL OR NULL;
```

| TRUE OR TRUE | TRUE OR FALSE | TRUE OR NULL | NULL OR NULL |
|---|---|---|---|
| 1 | 1 | 1 | NULL |

```sql
mysql> SELECT TRUE XOR TRUE, TRUE XOR FALSE, TRUE XOR NULL, NULL XOR NULL;
```

| TRUE XOR TRUE | TRUE XOR FALSE | TRUE XOR NULL | NULL XOR NULL |
|---|---|---|---|
| 0 | 1 | NULL | NULL |

与 `AND`、`OR` 和 `XOR` 不同，`NOT` 运算符不计算两个值；它只是返回提供值的逆值：

```sql
mysql> SELECT NOT TRUE, NOT FALSE, NOT NULL;
```

| NOT TRUE | NOT FALSE | NOT NULL |
|---|---|---|
| 0 | 1 | NULL |

您可以使用 `sql_mode=PIPES_AS_CONCAT` 更改 MySQL 的 `||` 简写运算符，这将导致如列表 1-36 所示的意外结果。

### 清单 1-36: logic-operators.sql

可在 Wrox.com 上下载

```sql
mysql> SELECT TRUE OR FALSE, TRUE || FALSE;
+-----------------+-----------------+
| TRUE OR FALSE   | TRUE || FALSE   |
+-----------------+-----------------+
| 1               | 1               |
+-----------------+-----------------+

mysql> SET SESSION sql_mode=PIPES_AS_CONCAT;
mysql> SELECT TRUE OR FALSE, TRUE || FALSE;
+-----------------+-----------------+
| TRUE OR FALSE   | TRUE || FALSE   |
+-----------------+-----------------+
| 1               | 10              |
+-----------------+-----------------+
```

## 流程控制

MySQL 提供了四个用于流程控制的函数：`IF()`、`CASE`、`IFNULL()` 和 `NULLIF()`。`IF()` 函数提供了三元运算符的语法，根据给定条件有两种可能的结果：

```sql
mysql> SELECT IF (2 > 1,'2 is greater than 1','2 is not greater than 1') AS answer;
+-------------------+
| answer            |
+-------------------+
| 2 is greater than 1 |
+-------------------+
```

MySQL `CASE` 语句的操作方式与 PHP `switch` 语法类似，其中多个选项中的单个给定条件会导致一个 true 赋值。`CASE` 语句还包括一个特殊默认情况，当没有任何条件等于 `TRUE` 值时使用。

```sql
mysql> SET @value=CONVERT(RAND() * 10, UNSIGNED INTEGER);

mysql> SELECT @value,
    -> CASE
    ->     WHEN @value < 3 THEN 'Value is < 3'
    ->     WHEN @value > 6 THEN 'Value is > 6'
    ->     WHEN @value = 3 OR @value = 6 THEN 'Value is 3 or 6'
    ->     ELSE 'Value is 4 or 5'
    -> END;

+-----+---------------+
| 3   | Value is 3 or 6 |
+-----+---------------+
```

> 虽然可以通过 SQL 执行复杂的流程控制功能，但 MySQL 数据库的设计目的是存储和检索数据。在可能的情况下，复杂的规则应编写在应用层以实现更高的性能。

剩下的两个函数 `IFNULL()` 和 `NULLIF()` 支持用于处理 `NULL` 的条件表达式。`IFNULL()` 如果提供的表达式等于 `NULL` 则返回 `NULL`，否则返回表达式的值。`NULLIF()` 如果两个表达式的结果为 `TRUE` 条件，则返回 `NULL` 结果。清单 1-37 显示了此示例。

### 清单 1-37: flow-control.sql

```sql
mysql> SELECT IFNULL(NULL, 'Value is NULL') AS result1,
        IFNULL(1 > 2, 'NULL result') AS result2;
+----------------+----------+
| result1        | result2  |
+----------------+----------+
| Value is NULL  | 0        |
+--------------------------+

mysql> SELECT NULLIF(TRUE,TRUE) AS istrue,
        NULLIF(TRUE,FALSE) AS isfalse,
        NULLIF(TRUE,NULL) AS isnull;
+--------+---------+--------+
| istrue | isfalse | isnull |
+--------+---------+--------+
| NULL   | 1       | 1      |
+--------+---------+--------+
```

## 维护关系完整性

虽然许多开发者将关系完整性视为使用外键来维护数据的引用完整性，即 ACID 属性中的一致性部分，但在 MySQL 中，关系完整性可通过多种方式和不同级别来实现。这些可以在 `CREATE TABLE`、`ALTER TABLE` 的表结构级别语法中指定，或在 MySQL `SESSION` 或 `GLOBAL VARIABLES` 级别指定。MySQL 还可以提供特定于存储引擎的完整性级别。

### 约束

约束限制存储在给定表列中的值的类型。单列值的选项包括 `NOT NULL`、`UNSIGNED`、`ENUM` 和 `SET` 等。`UNIQUE KEY` 约束适用于单个表的一或多个列。`FOREIGN KEY` 约束涉及两个表之间的强制关系。

### NOT NULL

为确保列必须包含值，可以指定 `NOT NULL` 约束。重要的是，不要使用 `DEFAULT` 来强制执行 `NOT NULL` 约束。`DEFAULT` 属性顾名思义，在未指定值时提供默认值。以列定义 `col1 CHAR(5) NOT NULL DEFAULT ''` 为例，当在 `INSERT` 语句中未指定 `col1` 时，不会返回未指定强制列的错误。相反，一个空白值 `''` ——不要与 `NULL` 值混淆——会被插入到列中。当列被定义为可空时，这会更加令人困惑。在这种情况下，您有 `NULL` 和 `''` 作为可能的值。它们不相等，这会导致应用程序中出现混淆。它们应该相等吗？在搜索 `col1 LIKE NULL` 时，您还需要包含 `OR col1 = ''`。

### UNSIGNED

当整数列只需要非负数时，指定 `UNSIGNED` 约束将确保列只能包含 0 或正值。例如：

### 清单 1-38: unsigned.sql

```sql
mysql> DROP TABLE IF EXISTS example;
mysql> CREATE TABLE example (
  ->   int_signed    INT NOT NULL,
  ->   int_unsigned  INT UNSIGNED NOT NULL
  -> ) ENGINE=InnoDB DEFAULT CHARSET latin1;

mysql> INSERT INTO example (int_signed, int_unsigned) VALUES ( 1, 1);
mysql> INSERT INTO example (int_signed, int_unsigned) VALUES ( 0, 0);
mysql> INSERT INTO example (int_signed, int_unsigned) VALUES ( -1, 1);
mysql> INSERT INTO example (int_signed, int_unsigned) VALUES ( 1, -1);

ERROR 1264 (22003): Out of range value for column 'int_unsigned' at row 1

mysql> SELECT * FROM example;

+-------------+---------------+
| int_signed  | int_unsigned  |
+-------------+---------------+
|           1 |             1 |
|           0 |             0 |
|          -1 |             1 |
+-------------+---------------+
```

### ENUM 和 SET

`ENUM` 数据列和支持的 `SET` 列数据类型通过仅允许特定集合的可能值来帮助您强制执行完整性。当列的可能值范围有限时，这可能有益。清单 1-39 显示了示例。

### 清单 1-39: enum.sql
