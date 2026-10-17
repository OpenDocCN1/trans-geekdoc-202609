
> `DESCRIBE tablename` 与 `SHOW COLUMNS FROM tablename` 是同一条语句。

***

### 插入记录

数据库及其表创建完成后，即可开始使用 `INSERT` 命令填充数据。`INSERT` 查询有两种编写方式。第一种方法是指定要填充的列名：

```
INSERT INTO tablename (column1, column2...) VALUES (value1, value2 ...)
```

```
INSERT INTO tablename (column4, column8) VALUES (valueX, valueY)
```

使用这种结构，可以添加记录行，仅填充关键列。未赋值的列将被视为 `NULL`（或使用定义的默认值）。注意：若某列定义为 `NOT NULL` 且无默认值，不指定值将导致错误或警告。

![Image](img/05_figure_07_a.jpg)

未为 `NOT NULL` 列提供或预定义值会导致错误或警告。

第二种插入记录的格式是不指定任何列，但必须为每一列提供值：

```
INSERT INTO tablename VALUES (value1, NULL, value2, value3, ...)
```

使用此方法时，必须为每一列指定值，即使是 `NULL`。例如表有六列，则必须列出六个值。值的数量与列的数量不匹配将导致错误。

![Image](img/05_figure_08_b.jpg)

未为表中的每一列或 `INSERT` 查询中指定的列提供值，也会导致错误。

MySQL 还允许一次插入多行，各记录间用逗号分隔：

```
INSERT INTO tablename (column1, column4) VALUES (valueA, valueB),
(valueC, valueD),
(valueE, valueF)
```

虽然 MySQL 支持此语法，但不符合 SQL 标准，故并非所有数据库应用都支持。不过在 MySQL 中，该语法比单独执行多条 `INSERT` 查询更快。

注意：以上示例均使用占位符表示实际表名、列名和值，且省略了引号。实际查询中必须遵循特定规则以避免错误（参见“查询中的引号”侧边栏）。

#### 向表中插入数据

**1.** 向 *users* 表插入一行数据，指定要填充的列：

```
INSERT INTO users
(first_name, last_name, email, pass, registration_date)
VALUES ('Larry', 'Ullman', 'email@example.com', SHA1('mypass'), NOW());
```

![Image](img/05_figure_09_c.jpg)

该查询向 *users* 表插入单条记录。*1 row affected* 消息表示插入成功。

同样，这种指定具体列的语法更稳健，但并非总是最方便。`first_name`、`last_name` 和 `email` 列使用简单字符串作为值（字符串必须加引号）。

***

**查询中的引号**

在每条 SQL 命令中：

- 数值不应加引号。
- 字符串值（`CHAR`、`VARCHAR`、`TEXT` 列类型）必须始终加引号。
- 日期和时间值必须始终加引号。
- 函数不能加引号。
- `NULL` 关键字不能加引号。

给数值加不必要的引号通常不会造成问题（但仍不建议），但在其他情况下误用引号几乎总会导致错误。另外，使用单引号还是双引号无所谓，只要成对一致即可（左引号匹配右引号）。

如 PHP 一样，若值中需包含引号，可用另一种引号包裹，或用反斜杠转义：

```
INSERT INTO tablename (last_name) VALUES ('O\'Toole')
```

***

***

**两个 MySQL 函数**

虽函数详见本章后文，但此处需先介绍两个：`SHA1()` 和 `NOW()`。

`SHA1()` 函数是一种加密数据的方式。它生成的加密字符串固定为 40 字符长（这也是 *users* 表 *pass* 列定义为 `CHAR(40)` 的原因）。`SHA1()` 是单向加密（技术上属哈希函数），不可逆。适用于存储无需再以明文查看的敏感数据。因 `SHA1()` 输出不可解密，不适合存储日后需查看的敏感数据（如信用卡号）。`SHA1()` 自 MySQL 5.0.2 起可用；早期版本可用 `MD5()` 代替，功能相同但算法不同，返回 32 字符字符串（若用 `MD5()`，*pass* 列可定义为 `CHAR(32)`）。

`NOW()` 函数便于填充日期、时间、时间戳列，返回服务器当前日期和时间。

***

对于 `password` 和 `registration_date` 列，使用两个函数生成值（见“两个 MySQL 函数”侧边栏）。`SHA1()` 加密密码（示例中为 *mypass*）。`NOW()` 将 *registration_date* 设为当前时刻。

在 SQL 语句中使用函数时，切勿将其置于引号内。函数名与后续括号间也不能有空格（即 `NOW()` 而非 `NOW ()`）。

**2.** 向 *users* 表插入一行数据，不指定列名：

```
INSERT INTO users VALUES
(NULL, 'Zoe', 'Isabella', 'email2@example.com', SHA1('mojito'), NOW());
```

![Image](img/05_figure_10_d.jpg)

另一条记录被插入表中，此次为表中每一列都提供了值。

此语法示例中，每列必须赋值。`user_id` 列赋 `NULL`，MySQL 将按 `AUTO_INCREMENT` 定义自动使用下一个序号。即第一条记录 `user_id` 为 1，第二条为 2，以此类推。

**3.** 向 *users* 表插入多条数据：

```
INSERT INTO users (first_name, last_name, email, pass, registration_date) VALUES
('John', 'Lennon', 'john@beatles.com', SHA1('Happin3ss'), NOW()),
('Paul', 'McCartney', 'paul@beatles.com', SHA1('letITbe'), NOW()),
('George', 'Harrison', 'george@beatles.com', SHA1('something'), NOW()),
('Ringo', 'Starr', 'ringo@beatles.com', SHA1('thisboy'), NOW());
```

![Image](img/05_figure_11_e.jpg)

这一条查询（MySQL 允许但其他数据库应用不支持）一次性向表中插入多条记录。

利用 MySQL 支持一次插入多值的特性，可快速填充表记录。

**4.** 重复步骤 1 和 2，直到 *users* 表数据充足。

本章后续查询均基于我录入的记录。若你的数据库记录不同，请相应调整细节。因 *sitename* 数据库列和表结构固定，后续查询的核心思路仍适用。

***

> **提示**
>
> 在本书配套网站（`www.LarryUllman.com`）的下载页面，你可以下载书中所有的 SQL 命令。使用其中一些命令，你可以像我一样填充你的 `users` 表。

> **提示**
>
> 在 MySQL 中，`INSERT` 语句里的 `INTO` 项是可选的。

> **提示**
>
> phpMyAdmin 的 `INSERT` 选项卡允许你使用 HTML 表单插入记录。
>
> ![Image](img/05_figure_12_f.jpg)
>
> phpMyAdmin 的 `INSERT` 表单显示表的列，并提供用于输入值的文本框。下拉菜单列出了可用的函数，如用于密码的 `SHA1()` 或用于注册日期的 `NOW()`。

> **提示**
>
> 根据所用的 MySQL 版本，未为不能为 `NULL` 的列提供值可能会发出警告但 `INSERT` 仍然生效，或者报错导致 `INSERT` 失败。

> **提示**
>
> 你偶尔会在 SQL 命令中看到反引号（`` ` ``）的用法。该字符位于与波浪号（`~`）相同的键上，不同于单引号。反引号用于安全地引用可能与现有关键字同名的表或列名。

> **提示**
>
> 如果 MySQL 对前一个查询发出警告，`SHOW WARNINGS` 命令将显示问题所在。

> **提示**
>
> `INSERT` 的一个有趣变体是 `REPLACE`。如果用于表主键或 `UNIQUE` 索引的值已存在，则 `REPLACE` 更新该行。如果不存在，则 `REPLACE` 插入新行。

### 选择数据

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

#### 从表中选择数据

**1.** 检索 `users` 表中的所有数据：

```
SELECT * FROM users;
```

![Image](img/05_figure_13_a.jpg)

`SELECT * FROM` `tablename` 查询返回表中存储的每条记录的每一列。

这个非常基础的 SQL 命令将检索该表中存储的每一行的每一列。

**2.** 仅从 `users` 中检索名和姓：

```
SELECT first_name, last_name
FROM users;
```

![Image](img/05_figure_14_b.jpg)

该查询仅返回表中每条记录的两列。

你可以使用 `SELECT` 语句将结果限制为仅你需要的字段，而不是显示 `users` 表中每一列的数据。

> **提示**
>
> 在 phpMyAdmin 中，浏览选项卡运行一个简单的 `SELECT` 查询。

> **提示**
>
> 你实际上可以在不指定表或列的情况下使用 `SELECT`。例如，`SELECT NOW()`。
>
> ![Image](img/05_figure_15_c.jpg)
>
> 许多查询可以在不指定数据库或表的情况下运行。此查询选择调用 `NOW()` 函数的结果，该函数返回当前日期和时间（根据 MySQL）。

> **提示**
>
> `SELECT` 语句中列出列的顺序决定了值呈现的顺序。
>
> ![Image](img/05_figure_16_d.jpg)
>
> 如果 `SELECT` 查询指定了要返回的列，它们将按该顺序返回。

> **提示**
>
> 使用 `SELECT` 查询，你甚至可以多次检索同一列，此功能使你能以多种不同方式操作该列的数据。

#### 使用条件

迄今为止使用的 `SELECT` 查询将始终检索表中的每一条记录。但通常你会想根据特定标准限制返回的行。这可以通过向 `SELECT` 查询添加条件来实现。条件使用 SQL 术语 `WHERE`，其编写方式很像你在 PHP 中编写条件：

```
SELECT which_columns FROM which_table WHERE condition(s)
```

**表 5.1** 列出了在条件中最常用的运算符。例如，一个简单的相等检查：

```
SELECT name FROM people
WHERE birth_date = '2011-01-26'
```

**表 5.1. MySQL 运算符**

![Image](img/05tab01.jpg)

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

#### 使用条件

**1.** 选择姓氏为 `Simpson` 的所有用户：

```
SELECT * FROM users
WHERE last_name = 'Simpson';
```

![Image](img/05_figure_17_a.jpg)

所有注册的 Simpson 家族成员。

这个简单的查询返回 `last_name` 值为 `Simpson` 的每一行的每一列。（同样，如果你表中的数据不同，可以相应地更改这些查询。）

**2.** 仅选择姓氏为 `Simpson` 的用户的名：

```
SELECT first_name FROM users
WHERE last_name = 'Simpson';
```

![Image](img/05_figure_18_b.jpg)

所有注册的 Simpson 家族成员的名。

这里每行仅返回一列（`first_name`）。虽然这看起来可能有点奇怪，但你不必选择正在对其执行 `WHERE` 操作的列。原因在于 `SELECT` 后列出的列仅决定返回*哪些列*，而 `WHERE` 中列出的列决定返回*哪些行*。

**3.** 选择 `users` 表中没有电子邮件地址的每条记录的每一列：

```
SELECT * FROM users
WHERE email IS NULL;
```

![Image](img/05_figure_19_c.jpg)

此查询未返回任何记录，因为 `email` 列不能有 `NULL` 值。所以这个查询*确实*生效了；只是没有匹配的记录。

`IS NULL` 条件等同于*没有值*。请记住，空字符串不同于 `NULL`，因此不会匹配此条件。然而，空字符串将匹配：

```
SELECT * FROM users WHERE email='';
```

**4.** 选择密码为 `mypass` 的所有记录的用户 ID、名和姓：

```
SELECT user_id, first_name, last_name
FROM users
WHERE pass = SHA1('mypass');
```

![Image](img/05_figure_20_d.jpg)

条件判断可以使用函数，此处即为 `SHA1()`。

由于存储的密码是用 `SHA1()` 函数加密的，因此可以在条件判断中使用相同的加密函数来匹配密码。`SHA1()` 区分大小写，因此只有当密码（存储的与查询的）完全匹配时，此查询才会生效。

## 5. 选择用户 ID 小于 10 或大于 20 的用户名

![Image](img/circle-e.jpg)
