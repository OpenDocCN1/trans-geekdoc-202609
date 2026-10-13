
一个防止误删的好技巧是先使用 `SELECT *` 而不是 `DELETE` 运行查询。该查询的结果将显示哪些行将受删除影响。

**3.** 删除记录：

```sql
DELETE FROM users
WHERE user_id = 8 LIMIT 1;
```

删除表中的一条记录。

与更新一样，MySQL 将报告查询成功执行及受影响的行数。此时，除非你事先备份了数据库，否则无法恢复已删除的记录。

尽管 `SELECT` 查询（步骤 2）仅返回一行，但为了格外小心，还是在 `DELETE` 查询中添加了 `LIMIT 1` 子句。

**4.** 确认更改已生效：

```sql
SELECT user_id FROM users
WHERE first_name='Peter'
AND last_name='Tork';
```

该记录不再属于此表。

***

Tip

清空表的首选方法是使用 `TRUNCATE`：

```sql
TRUNCATE TABLE tablename
```

***

***

Tip

要删除表中的所有数据以及表本身，请使用 `DROP TABLE`：

```sql
DROP TABLE tablename
```

***

***

Tip

要删除整个数据库，包括其中的每个表及其所有数据，请使用

```sql
DROP DATABASE databasename
```

***

***

### 别名

*别名* 只是查询中使用的项目的符号重命名，通常应用于表、列或函数调用。别名使用 `AS` 创建：

```sql
SELECT registration_date AS reg
FROM users
```

别名是由数字、字母和下划线组成的区分大小写的字符串，但通常保持很短的长度。正如你在以下示例中将看到的，别名也会反映在返回结果的标题中。对于前面的示例，返回的查询结果将包含一列数据，名为 `reg`（而非 `registration_date`）。

在 MySQL 中，如果你为查询中使用的表或列定义了别名，则整个查询应始终一致地使用该别名，而不是原始名称。例如：

```sql
SELECT first_name AS name FROM
users WHERE name='Sam'
```

这与标准 SQL 不同，标准 SQL 不支持在 `WHERE` 条件中使用别名。

***

### 使用函数

为了结束本章，你将了解许多可在 MySQL 查询中使用的函数。你已经看到了两个——`NOW()` 和 `SHA1()`——但这只是冰山一角。你将在这里看到的大多数函数用于 `SELECT` 查询，以格式化和更改返回的数据，但你也可以在其他类型的查询中使用 MySQL 函数。

要将函数应用于列的值，查询如下所示：

```sql
SELECT FUNCTION(column) FROM tablename
```

要将函数应用于一列的值同时选择其他列，可以编写如下任一查询：

- `SELECT *, FUNCTION(column) FROM tablename`
- `SELECT column1, FUNCTION(column2), column3 FROM tablename`

通常首选后一种语法，因为它仅返回你需要的列（而不是所有列）。

在介绍实际函数之前，请注意以下几点。首先，函数通常应用于存储的数据（即列），但也可以应用于字面值。以下 `UPPER()` 函数（将字符串大写）的任一应用均有效：

```sql
SELECT UPPER(first_name) FROM users
SELECT UPPER('this string')
```

其次，虽然函数名称本身不区分大小写，但我将继续以全大写格式编写它们，以帮助将其与表名和列名区分开来（我也将 SQL 术语大写）。第三，函数的一个重要规则是：在 MySQL 中，*函数名和左括号之间不能有空格*，尽管括号内的空格是可以接受的。最后，当使用函数格式化返回数据时，你通常想利用*别名*，这是一个在侧边栏中讨论的概念。

***

Tip

正如存在不同的 SQL 标准且不同的数据库应用程序有其自身的语言细微差别一样，一些函数通用于所有数据库应用程序，而另一些则特定于 MySQL。本章和本书仅涉及 MySQL 函数。

***

***

Tip

[第 7 章](#ch07.html#ch07) 讨论了两类更多的 MySQL 函数：分组和加密。

***

#### 文本函数

要演示的第一组函数是用于操作文本的。此类别中最常见的函数列在 **[表 5.2](#ch05.html#ch05table02)** 中。与大多数函数一样，这些函数可以应用于列或字面值（均由 `t`、`t1`、`t2` 等表示）。

**表 5.2. 文本函数**

`CONCAT()` 可能是最有用的文本函数，值得特别关注。`CONCAT()` 函数实现连接，PHP 对此使用句点（参见[第 1 章](#ch01.html#ch01)“[PHP 简介](#ch01.html#ch01)”）。连接的语法要求你将想要组装的各个值按顺序放在括号内，并用逗号分隔：

```sql
SELECT CONCAT(t1, t2) FROM tablename
```

虽然你可以（且通常会）将 `CONCAT()` 应用于列，但也可以包含用引号括起来的字符串。例如，要将姓名格式化为 `First<SPACE>Last`，你可以使用：

```sql
SELECT CONCAT(first_name, ' ', last_name)
FROM users
```

因为连接通常以新格式返回值，所以这是使用别名（见侧边栏）的绝佳时机：

```sql
SELECT CONCAT(first_name, ' ', last_name)
AS Name FROM users
```

#### 格式化文本

**1.** 不使用别名连接名称：

```sql
SELECT CONCAT(last_name, ', ', first_name)
FROM users;
```

这种简单的连接返回每个注册用户的全名。注意列标题是 `CONCAT()` 函数的用法。

此查询将演示两件事。首先，用户的姓氏、一个逗号和一个空格，加上他们的名字被连接在一起形成一个字符串（格式为 `Last, First`）。其次，如图所示，如果不使用别名，返回数据的列标题将是函数调用。在 mysql 客户端或 phpMyAdmin 中，这只是难看；当使用 PHP 连接 MySQL 时，这可能会成为一个问题。

**2.** 使用别名连接名称：

```sql
SELECT CONCAT(last_name, ', ', first_name)
AS Name FROM users ORDER BY Name;
```

通过使用别名，返回的数据位于标题为 `Name` 的列下（与步骤 1 对比）。

要使用别名，只需在要重命名的项目后添加 `AS` `aliasname`。别名将成为返回数据的新标题。为了使查询更有趣，同一个别名也用在 `ORDER BY` 子句中。

**3.** 查找最长的姓氏：

```sql
SELECT LENGTH(last_name) AS L,
last_name FROM users
ORDER BY L DESC LIMIT 1;
```

通过使用 `LENGTH()` 函数、别名、`ORDER BY` 子句和 `LIMIT` 子句，此查询返回最长存储名称的长度和值。
