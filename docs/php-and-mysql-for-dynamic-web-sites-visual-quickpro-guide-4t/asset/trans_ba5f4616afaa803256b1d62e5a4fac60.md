
在本书配套网站（`www.LarryUllman.com`）的下载页面，你可以下载书中所有的 SQL 命令。使用其中一些命令，你可以像我一样填充你的 `users` 表。

> **提示**
>
> 在 MySQL 中，`INSERT` 语句里的 `INTO` 项是可选的。

> **提示**
>
> phpMyAdmin 的 `INSERT` 选项卡允许你使用 HTML 表单插入记录 ![Image](graphics/circle-f.jpg)。
>
> ![Image](graphics/05_figure_12_f.jpg)
>
> ![Image](graphics/circle-f.jpg) phpMyAdmin 的 `INSERT` 表单显示表的列，并提供用于输入值的文本框。下拉菜单列出了可用的函数，如用于密码的 `SHA1()` 或用于注册日期的 `NOW()`。

> **提示**
>
> 根据所用的 MySQL 版本，未为不能为 `NULL` 的列提供值可能会发出警告但 `INSERT` 仍然生效 ![Image](graphics/graycircle-a.jpg)，或者报错导致 `INSERT` 失败。

> **提示**
>
> 你偶尔会在 SQL 命令中看到反引号（`` ` ``）的用法。该字符位于与波浪号（`~`）相同的键上，不同于单引号。反引号用于安全地引用可能与现有关键字同名的表或列名。

> **提示**
>
> 如果 MySQL 对前一个查询发出警告，`SHOW WARNINGS` 命令将显示问题所在 ![Image](graphics/graycircle-a.jpg)。

> **提示**
>
> `INSERT` 的一个有趣变体是 `REPLACE`。如果用于表主键或 `UNIQUE` 索引的值已存在，则 `REPLACE` 更新该行。如果不存在，则 `REPLACE` 插入新行。

## 选择数据

现在数据库中已有一些记录，你可以使用所有 SQL 术语中最常用的 `SELECT` 来检索存储的信息。`SELECT` 查询使用以下语法返回记录行：

```
SELECT which_columns FROM which_table
```

最简单的 `SELECT` 查询是：

```
SELECT * FROM tablename
```

星号表示你想要检索每一列。另一种方法是指定要返回的列，每列之间用逗号分隔：

```
SELECT column1, column3 FROM tablename
```

明确指定要选择的列有几个好处。第一是性能：没有理由去获取你不会使用的列。第二是顺序：你可以按不同于表中布局的顺序返回列。第三——你稍后在本章中会看到——指定列名允许你使用函数操作这些列中的值。

### 从表中选择数据

**1.** 检索 `users` 表中的所有数据 ![Image](graphics/circle-a.jpg)：

```
SELECT * FROM users;
```

![Image](graphics/05_figure_13_a.jpg)

![Image](graphics/circle-a.jpg) `SELECT * FROM` `tablename` 查询返回表中存储的每条记录的每一列。

这个非常基础的 SQL 命令将检索该表中存储的每一行的每一列。

**2.** 仅从 `users` 中检索名和姓 ![Image](graphics/circle-b.jpg)：

```
SELECT first_name, last_name
FROM users;
```

![Image](graphics/05_figure_14_b.jpg)

![Image](graphics/circle-b.jpg) 该查询仅返回表中每条记录的两列。

你可以使用 `SELECT` 语句将结果限制为仅你需要的字段，而不是显示 `users` 表中每一列的数据。

> **提示**
>
> 在 phpMyAdmin 中，浏览选项卡运行一个简单的 `SELECT` 查询。

> **提示**
>
> 你实际上可以在不指定表或列的情况下使用 `SELECT`。例如，`SELECT NOW()` ![Image](graphics/circle-c.jpg)。
>
> ![Image](graphics/05_figure_15_c.jpg)
>
> ![Image](graphics/circle-c.jpg) 许多查询可以在不指定数据库或表的情况下运行。此查询选择调用 `NOW()` 函数的结果，该函数返回当前日期和时间（根据 MySQL）。

> **提示**
>
> `SELECT` 语句中列出列的顺序决定了值呈现的顺序（对比 ![Image](graphics/graycircle-b.jpg) 与 ![Image](graphics/circle-d.jpg)）。
>
> ![Image](graphics/05_figure_16_d.jpg)
>
> ![Image](graphics/circle-d.jpg) 如果 `SELECT` 查询指定了要返回的列，它们将按该顺序返回。

> **提示**
>
> 使用 `SELECT` 查询，你甚至可以多次检索同一列，此功能使你能以多种不同方式操作该列的数据。

## 使用条件

迄今为止使用的 `SELECT` 查询将始终检索表中的每一条记录。但通常你会想根据特定标准限制返回的行。这可以通过向 `SELECT` 查询添加条件来实现。条件使用 SQL 术语 `WHERE`，其编写方式很像你在 PHP 中编写条件：

```
SELECT which_columns FROM which_table WHERE condition(s)
```

**[表 5.1](#ch05.html#ch05table01)** 列出了在条件中最常用的运算符。例如，一个简单的相等检查：

```
SELECT name FROM people
WHERE birth_date = '2011-01-26'
```

**表 5.1. MySQL 运算符**

![Image](graphics/05tab01.jpg)

运算符可以结合使用，并配合括号，创建更复杂的表达式：

```
SELECT * FROM items WHERE
(price BETWEEN 10.00 AND 20.00) AND
(quantity > 0)

SELECT * FROM cities WHERE
(zip_code = 90210) OR (zip_code = 90211)
```

最后一个示例也可以写为：

```
SELECT * FROM cities WHERE
zip_code IN (90210, 90211)
```

为了演示条件的使用，让我们在 `sitename` 数据库上运行更多 `SELECT` 查询。以下示例只是近乎无限可能性中的一小部分。在本章和全书的学习过程中，你将看到条件如何用于各类查询。

### 使用条件

**1.** 选择姓氏为 `Simpson` 的所有用户 ![Image](graphics/circle-a.jpg)：

```
SELECT * FROM users
WHERE last_name = 'Simpson';
```

![Image](graphics/05_figure_17_a.jpg)

![Image](graphics/circle-a.jpg) 所有注册的 Simpson 家族成员。

这个简单的查询返回 `last_name` 值为 `Simpson` 的每一行的每一列。（同样，如果你表中的数据不同，可以相应地更改这些查询。）

**2.** 仅选择姓氏为 `Simpson` 的用户的名 ![Image](graphics/circle-b.jpg)：

```
SELECT first_name FROM users
WHERE last_name = 'Simpson';
```

![Image](graphics/05_figure_18_b.jpg)

![Image](graphics/circle-b.jpg) 所有注册的 Simpson 家族成员的名。

这里每行仅返回一列（`first_name`）。虽然这看起来可能有点奇怪，但你不必选择正在对其执行 `WHERE` 操作的列。原因在于 `SELECT` 后列出的列仅决定返回*哪些列*，而 `WHERE` 中列出的列决定返回*哪些行*。

**3.** 选择 `users` 表中没有电子邮件地址的每条记录的每一列 ![Image](graphics/circle-c.jpg)：

```
SELECT * FROM users
WHERE email IS NULL;
```

![Image](graphics/05_figure_19_c.jpg)

![Image](graphics/circle-c.jpg) 此查询未返回任何记录，因为 email 列不能有 `NULL` 值。所以这个查询*确实*生效了；只是没有匹配的记录。

`IS NULL` 条件等同于*没有值*。请记住，空字符串不同于 `NULL`，因此不会匹配此条件。然而，空字符串将匹配：

```
SELECT * FROM users WHERE email='';
```

**4.** 选择密码为 `mypass` 的所有记录的用户 ID、名和姓 ![Image](graphics/circle-d.jpg)：

```
SELECT user_id, first_name, last_name
FROM users
```
