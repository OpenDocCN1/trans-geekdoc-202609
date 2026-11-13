

FROM 子句包含一个表列表，结果集中的行应从这些表中形成。在最基本的情况下，`table_refs` 是一个或多个表的逗号分隔列表，这些表可以与 `AS` 一起或不使用 `AS` 分配别名，如上文 `select_expression` 中所述。如果指定多个表名，则正在执行一个 _连接_。这些将在下面标题为 Joins 的部分中讨论。

`WHERE` 子句中的 `where_definition` 设置了行在响应 `SELECT` 查询时被包含在结果表中的条件。这可以是一个简单的条件（例如 `id=5`），或者是一个复杂的表达式，它使用 MySQL 函数并使用布尔运算符（`AND`、`OR`、`NOT`）组合多个条件。

**GROUP BY** 子句允许你指定一个或多个列（按名称、别名或列位置指定，其中 1 是结果集中的第一个列），对于具有相等值的行应在结果集中折叠为单行。通常应将此子句与 MySQL 分组函数（如 `COUNT()`、`MAX()` 和 `AVG()`）结合使用，这些函数在附录 B 第 211 页中有描述，以生成关于所生成组的汇总信息的结果行。默认情况下，分组结果按分组列的升序排序，但是，可以在每个列引用后添加 `ASC` 或 `DESC` 参数，以分别显式按升序或降序对该列的结果进行排序。结果首先按列出的第一个列排序，然后相同的行集按第二个列排序，以此类推。

请注意，`WHERE` 子句在 **GROUP BY** 分组发生之前处理，因此 `WHERE` 子句中的条件不能引用分组操作生成的列。要对分组后的结果集施加条件，应该改用 **HAVING** 子句。此子句的语法与 `WHERE` 子句相同，只是此处指定的条件在返回结果集之前处理，并且不会以任何方式进行优化。出于此原因，应尽可能始终使用 `WHERE` 子句。有关 **GROUP BY** 和 **HAVING** 子句的更多信息，请参见第 9 章：Advanced SQL。

**ORDER BY** 子句允许你在返回结果之前根据一个或多个列中的值对结果进行排序。与 **GROUP BY** 子句类似，每个列可以通过列名、别名或位置来标识（其中 1 是结果集中的第一个列），并且每个列可以有一个 `ASC` 或 `DESC` 参数，以分别指定按升序或降序进行排序（升序为默认值）。行最初按列出的第一个列排序，然后相同的行集按第二个列排序，以此类推。

**LIMIT** 子句指示查询仅返回它通常生成的结果的一部分。在简单情况下，`LIMIT n` 仅返回完整结果集的前 n 行。你也可以使用 LIMIT x, n 的形式指定偏移量。在这种情况下，最多将返回 n 行，从完整结果集的第 x 行开始（第一行对应 x = 0，第二行对应 x = 1，以此类推）。

## 连接

如上所述，SELECT 查询的 FROM 子句允许你指定用于创建结果集的合并表。以这种方式合并多个表时，称为连接。MySQL 支持多种类型的连接，如上面 FROM 子句的 table_refs 组件所定义的受支持语法所示：

```
table_ref
table_refs, table_ref
table_refs, table_ref
table_refs [CROSS] JOIN table_ref
table_refs INNER JOIN table_ref join_condition
table_refs STRAIGHT_JOIN table_ref
table_refs LEFT [OUTER] JOIN table_ref join_condition
{ oj table_ref LEFT OUTER JOIN table_ref ON cond_expr }
table_refs NATURAL [LEFT [OUTER]] JOIN table_ref
table_refs RIGHT [OUTER] JOIN table_ref join_condition
table_refs NATURAL [RIGHT [OUTER]] JOIN table_ref
```

其中 table_ref 定义为：

```
table_name [[AS] alias] [USE INDEX (key_list)]
[IGNORE INDEX (key_list)]
```

并且 join_condition 定义为以下之一：

```
ON cond_expr
USING (column_list)
```

最基本的连接类型是内连接，它生成由第一个表与第二个表的所有可能行配对组成的行。在 MySQL 中，可以通过用逗号 (,) 分隔表名，或使用 JOIN、CROSS JOIN 或 INNER JOIN 关键字来执行内连接（这些都等效）。

通常，SELECT 查询的 WHERE 子句用于指定条件以缩小实际返回的合并行范围（例如，将第一个表中的主键与第二个表中的列匹配）；但是，当使用 INNER JOIN 语法时，join_condition 的 ON 形式也可以发挥此作用。作为最后一种替代方案，join_condition 的 USING (column_list) 形式允许你指定两个表之间必须匹配的列。例如，

```
SELECT * FROM t1 INNER JOIN t2 USING (aid)
```

等效于

```
SELECT * FROM t1 INNER JOIN t2 ON t1.aid = t2.aid
```

还等同于

```
SELECT * FROM t1, t2 WHERE t1.aid = t2.aid
```

**STRAIGHT_JOIN** 的工作方式与内连接相同，只是表按列出的顺序处理（先左后右）。通常 MySQL 会选择处理时间最短的顺序，但如果你认为自己更了解情况，可以使用 STRAIGHT_JOIN。

第二种连接类型是外连接，在 MySQL 中通过 LEFT/RIGHT [OUTER] JOIN 实现（OUTER 完全可选，且无效）。在 LEFT 外连接中，左侧表中任何在右侧表中没有匹配行的行（由 `join_condition` 定义）都将作为结果集中的单行列出。NULL 值将出现在来自右侧表的所有列中。

{ oj ... } 语法相当于标准左外连接；它是为了与其他 ODBC 数据库兼容而包含的。

RIGHT 外连接的工作方式与 LEFT 外连接相同，只是在这种情况下，右侧表的条目始终包含在内，即使它们在左侧表中没有匹配项。由于 RIGHT 外连接不是标准的，因此通常最好坚持使用 LEFT 外连接以实现跨数据库兼容性。

有关外连接的实际示例及其用途，请参见第 9 章：Advanced SQL。

**NATURAL** 连接是一种“自动”连接，因为它们会自动根据两个表之间发现的匹配列名来匹配行。因此，如果名为 Jokes 的表具有一个引用 Authors 表（其主键是另一个 AID 列）中条目的 AID 列，则可以非常简单地在这两个表上执行该列的连接（假设两个表中没有其他同名列）：

```
SELECT * FROM Jokes NATURAL JOIN Authors
```

## SET

```
SET [OPTION] SQL_VALUE_OPTION = value, ...
```

SELECT OPTION 查询允许你在客户端和服务器上设置许多选项。可以省略 OPTION 单词，因为它不影响查询的操作。

SET OPTION 查询最常见的用途是更改密码：

```
SET PASSWORD = PASSWORD('new_password')
```

以及更改另一个用户的密码（如果你有适当的访问权限）：

```
SET PASSWORD FOR user = PASSWORD('new_password')
```

有关可设置选项的完整列表，请参阅 MySQL 参考手册。

## SHOW

SHOW 查询可以以多种形式用于获取有关 MySQL 服务器、数据库及其包含的表的信息。这些形式中的许多都带有可选的 LIKE wild 组件，其中 wild 是一条可能包含通配符字符（'%' 表示多个字符，'_' 表示单个字符）的字符串，用于过滤结果列表。下面将介绍 SHOW 查询的每种形式：

```
SHOW DATABASES [LIKE wild]
```

列出 MySQL 服务器上可用的数据库。

```
SHOW [OPEN] TABLES [FROM db_name] [LIKE wild]
```

列出默认或指定数据库中的表（或当前打开的表，可选）。

```
SHOW [FULL] COLUMNS FROM tbl_name [FROM db_name] [LIKE wild]
```

当不使用 FULL 时，此查询提供与 DESCRIBE 查询相同的信息（参见第 181 页）。FULL 选项会在此信息中添加你对每个列的权限列表。SHOW FIELDS 等效于 SHOW COLUMNS。

```
SHOW INDEX FROM tbl_name [FROM db_name]
```

提供有关指定表上定义的索引的详细信息。有关此查询生成的结果的指南，请参阅 MySQL 参考手册。SHOW KEYS 等效于 SHOW INDEX。

```
SHOW TABLE STATUS [FROM db_name] [LIKE wild]
```

显示默认或指定数据库中表的详细信息。

