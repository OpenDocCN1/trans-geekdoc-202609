
```sql
SELECT first_name, last_name
FROM users WHERE
(user_id < 10) OR (user_id > 20);
```

![Image](img/05_figure_21_e.jpg)

![Image](img/circle-e.jpg)此查询使用了两个条件和 `OR` 运算符。

同一查询也可以写作：

```sql
SELECT first_name, last_name FROM
users WHERE user_id
NOT BETWEEN 10 and 20;
```

甚至可以写作：

```sql
SELECT first_name, last_name FROM
users WHERE user_id NOT IN
(10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20);
```

---

### 提示

您可以在查询中使用数学加法（`+`）、减法（`-`）、乘法（`*`）和除法（`/`）字符执行数学计算。

---

### 提示

MySQL 支持关键字 `TRUE` 和 `FALSE`，*不区分大小写*。在内部，`TRUE` 评估为 1，`FALSE` 评估为 0。因此，在 MySQL 中，`TRUE + TRUE` 等于 2。

---

### 使用 LIKE 和 NOT LIKE

在条件判断中使用数字、日期和 `NULL` 是一个直接的过程，但字符串可能比较棘手。您可以使用如下查询检查字符串相等性：

```sql
SELECT * FROM users
WHERE last_name = 'Simpson'
```

然而，以更宽松的方式比较字符串需要额外的运算符和字符。例如，如果您想匹配一个人的姓氏，可能是 *Smith*、*Smiths* 或 *Smithson*，则需要更灵活的条件判断。这就是 `LIKE` 和 `NOT LIKE` 术语的用武之地。这些主要用于字符串，并结合两个通配符：下划线（ `_` ），匹配单个字符；百分号（ `%` ），匹配零个或多个字符。在姓氏示例中，查询将是：

```sql
SELECT * FROM users
WHERE last_name LIKE 'Smith%'
```

此查询将返回所有 *last_name* 值以 *Smith* 开头的行。因为它默认是*不区分大小写*的搜索，所以也适用于以 *smith* 开头的名字。

#### 使用 LIKE

**1.** 选择姓氏以 *Bank* 开头的所有记录 ![Image](img/circle-a.jpg):

```sql
SELECT * FROM users
WHERE last_name LIKE 'Bank%';
```

![Image](img/05_figure_22_a.jpg)

![Image](img/circle-a.jpg)SQL 术语 `LIKE` 为您的条件判断增加了灵活性。此查询匹配姓氏值以 *Bank* 开头的任何记录。

**2.** 选择电子邮件地址不符合 *something@authors.com* 形式的每条记录的姓名 ![Image](img/circle-b.jpg):

```sql
SELECT first_name, last_name
FROM users WHERE
email NOT LIKE '%@authors.com';
```

![Image](img/05_figure_23_b.jpg)

![Image](img/circle-b.jpg)`NOT LIKE` 条件判断根据值不包含的内容返回记录。

要排除字符串中存在的值，请结合通配符使用 `NOT LIKE`。

---

### 提示

带有 `LIKE` 条件判断的查询通常较慢，因为它们无法利用索引。仅在绝对必要时才使用 `LIKE` 和 `NOT LIKE`。

---

### 提示

通配符可以用在查询中字符串的前部和/或后部。

```sql
SELECT * FROM users
WHERE last_name LIKE '_smith%'
```

---

### 提示

虽然 `LIKE` 和 `NOT LIKE` 通常用于字符串，但它们也可以应用于数值列。

---

### 提示

要在 `LIKE` 或 `NOT LIKE` 查询中使用字面下划线或百分号，您需要对其进行转义（在字符前加上反斜杠），以免其被误认为是通配符。

---

### 提示

下划线可以与自身组合使用；例如，`LIKE ' _ _ '` 将查找任何两个字母的组合。

---

### 提示

在第 7 章（“高级 SQL 和 MySQL”）中，您将了解 `FULLTEXT` 搜索，这可能比 `LIKE` 搜索更有用。

---

### 排序查询结果

默认情况下，`SELECT` 查询的结果将按无意义的顺序返回（对于许多数据库新手来说，这是一个奇怪的概念）。要使查询结果具有有意义的顺序，请使用 `ORDER BY` 子句：

```sql
SELECT * FROM tablename ORDER BY column
SELECT * FROM orders ORDER BY total
```

使用 `ORDER BY` 时的默认顺序是升序（缩写 `ASC`），即数字从小到大，日期从最旧到最近，文本按字母顺序排序。您可以通过指定降序（缩写 `DESC`）来反转此顺序：

```sql
SELECT * FROM tablename
ORDER BY column DESC
```

您甚至可以按多列对返回的值进行排序：

```sql
SELECT * FROM tablename
ORDER BY column1, column2
```

您可以且经常会将 `ORDER BY` 与 `WHERE` 或其他子句一起使用。这样做时，请将 `ORDER BY` 放在条件之后：

```sql
SELECT * FROM tablename WHERE conditions
ORDER BY column
```

#### 对数据进行排序

**1.** 按姓氏字母顺序选择所有用户 ![Image](img/circle-a.jpg):

```sql
SELECT first_name, last_name FROM
users ORDER BY last_name;
```

![Image](img/05_figure_24_a.jpg)

![Image](img/circle-a.jpg)按姓氏字母顺序排列的记录。

如果您将这些结果与“选择数据”部分中 ![Image](img/graycircle-b.jpg) 的结果进行比较，您将看到使用 `ORDER BY` 的好处。

**2.** 先按姓氏字母顺序显示所有用户，然后按名字字母顺序 ![Image](img/circle-b.jpg):

```sql
SELECT first_name, last_name FROM
users ORDER BY last_name ASC,
first_name ASC;
```

![Image](img/05_figure_25_b.jpg)

![Image](img/circle-b.jpg)记录按字母顺序排列，先按姓氏，然后在该姓氏内按名字。

在此查询中，效果是返回每一行，先按 *last_name* 排序，然后在 *last_name* 内按 *first_name* 排序。在 Simpson 家庭成员中，这种效果最为明显。

**3.** 按注册日期显示所有非 Simpson 姓氏的用户 ![Image](img/circle-c.jpg):

```sql
SELECT * FROM users
WHERE last_name != 'Simpson'
ORDER BY registration_date DESC;
```

![Image](img/05_figure_26_c.jpg)

![Image](img/circle-c.jpg)所有姓氏不为 *Simpson* 的用户，按注册日期显示，最近注册的列在最前面。

您可以在任何列类型上使用 `ORDER BY`，包括数字和日期。该子句也可用于带有条件判断的查询中，将 `ORDER BY` 放在 `WHERE` 之后。

---

### 提示

由于 MySQL 自然支持任意数量的语言，`ORDER BY` 将基于所使用的*排序规则*（参见第 6 章）。

---

### 提示

如果您选择用于排序的列是 `ENUM` 类型，排序将基于创建列时可能的 `ENUM` 值的顺序。例如，如果您有 *gender* 列，定义为 `ENUM('M', 'F')`，则子句 `ORDER BY gender` 将返回 *M* 记录在前的结果。

---

### 限制查询结果

另一个可以添加到大多数查询中的 SQL 子句是 `LIMIT`。在 `SELECT` 查询中，`WHERE` 决定返回哪些记录，`ORDER BY` 决定如何对这些记录排序，但 `LIMIT` 规定返回多少记录。其用法如下：

```sql
SELECT * FROM tablename LIMIT x
```

在这样的查询中，将仅返回查询结果中最初的 *x* 条记录。要仅返回三条匹配记录，请使用：

```sql
SELECT * FROM tablename LIMIT 3
```

使用此格式

```sql
SELECT * FROM tablename LIMIT x, y
```

可以返回从 *x* 开始的 *y* 条记录。要返回第 11 到第 20 条记录，您应该编写

```sql
SELECT * FROM tablename LIMIT 10, 10
```

与 PHP 中的数组一样，在涉及 `LIMIT` 时，结果集从 0 开始，因此 10 代表第 11 条记录。

因为 `SELECT` 不会按任何有意义的顺序返回结果，所以在使用 `LIMIT` 时，您几乎总是想要应用 `ORDER BY` 子句。您可以将 `LIMIT` 与 `WHERE` 和/或 `ORDER BY` 子句一起使用，始终将 `LIMIT` 放在最后：

```sql
SELECT which_columns FROM tablename WHERE
conditions ORDER BY column LIMIT x
```

#### 限制返回的数据量

**1.** 选择最后注册的五位用户 ![Image](img/circle-a.jpg)：

```sql
SELECT first_name, last_name
FROM users ORDER BY
registration_date DESC LIMIT 5;
```

![Image](img/05_figure_27_a.jpg)

![Image](img/circle-a.jpg)使用 `LIMIT` 子句，查询可以返回特定数量的记录。

要返回最新的任何内容，请按日期以降序对数据进行排序。然后，要仅查看最近的五条，请在查询中添加 `LIMIT 5`。

**2.** 选择第二个注册的人 ![Image](img/circle-b.jpg)：

```sql
SELECT first_name, last_name
FROM users ORDER BY
registration_date ASC LIMIT 1, 1;
```

![Image](img/05_figure_28_b.jpg)

![Image](img/circle-b.jpg)得益于 `LIMIT` 子句，查询甚至可以使用 `LIMIT` *`x`*, *`y`* 格式从一组记录的中间返回记录。

这看起来可能很奇怪，但这只是对迄今所学信息的一个很好的应用。首先，按 *registration_date* 升序排列所有记录，这样最先注册的人会最先返回。然后，将返回的结果限制为从 1 开始（即第二行）并仅返回一条记录。

***

### 提示

`LIMIT` *`x`*, *`y`* 子句最常用于对查询结果进行分页（跨多页分块显示）。您将在 第 10 章 “常用编程技术” 中看到这一点。

***

### 提示

`LIMIT` 子句不会提高查询的执行速度，因为 MySQL 仍然必须组装整个结果集，然后再截断列表。但 `LIMIT` 子句将在 mysql 客户端或您的 PHP 脚本处理数据时，将数据量降至最低。

***

### 提示

`LIMIT` 术语不是 SQL 标准的一部分，因此（遗憾的是）并非所有数据库都可用。

***

### 提示

`LIMIT` 子句可用于大多数类型的查询，而不仅仅是 `SELECT`。

***

### 更新数据

一旦表中包含一些数据，您就可能需要编辑那些现有记录。如果信息录入错误或数据发生变化（例如姓氏或电子邮件地址），这可能是必要的。更新记录的语法是：

```sql
UPDATE tablename SET column=value
```

您可以一次性修改多个列，用逗号将每个列与下一个分隔开。

```sql
UPDATE tablename SET column1=valueA,
column5=valueB...
```

您几乎总是想要使用 `WHERE` 子句来指定应更新哪些行：

```sql
UPDATE tablename SET column2=value
WHERE column5=value
```

如果您不使用 `WHERE` 子句，更改将应用于每一条记录。

更新连同删除，是使用主键最重要的原因之一。该值——永远不应改变——即使在需要更改其他每个字段时，也可以作为 `WHERE` 子句中的参考点。

#### 更新记录

**1.** 查找要更新记录的主键 ![Image](img/circle-a.jpg)：

```sql
SELECT user_id FROM users
WHERE first_name = 'Michael'
AND last_name='Chabon';
```

![Image](img/05_figure_29_a.jpg)

![Image](img/circle-a.jpg)在更新记录之前，确定要在 `UPDATE` 的 `WHERE` 子句中使用哪个主键。

在此示例中，我将更改该作者记录的电子邮件。为此，我必须首先找到该记录的主键，此查询即可完成。

**2.** 更新记录 ![Image](img/circle-b.jpg)：

```sql
UPDATE users
SET email='mike@authors.com'
WHERE user_id = 18;
```

![Image](img/05_figure_30_b.jpg)

![Image](img/circle-b.jpg)此查询仅更改了一行中一列的值。

要更改电子邮件地址，请使用 `UPDATE` 查询，使用主键 (*user_id*) 指定更新应应用于哪条记录。MySQL 将报告查询是否成功以及受影响的行数。

**3.** 确认更改已生效 ![Image](img/circle-c.jpg)：

```sql
SELECT * FROM users
WHERE user_id=18;
```

![Image](img/05_figure_31_c.jpg)

![Image](img/circle-c.jpg)作为最后一步，您可以通过再次选择该记录来确认更新。

尽管 MySQL 已指示更新成功 ![Image](img/graycircle-b.jpg)，但再次选择该记录以确认发生了正确的更改也无妨。

***

### 提示

除非您希望更改影响每一行，否则在使用 `UPDATE` 时请格外确定要使用 `WHERE` 条件。

***

### 提示

如果您运行的更新查询实际上没有更改任何值（如 `UPDATE users SET first_name='mike' WHERE first_name='mike'`），您不会看到任何错误，但不会有任何行受影响。较新版本的 MySQL 会显示有 *X* 行匹配查询，但 0 行被更改 ![Image](img/circle-d.jpg)。

![Image](img/05_figure_32_d.jpg)

![Image](img/circle-d.jpg)较新版本的 MySQL 将报告 `UPDATE` 查询的匹配记录和已更改记录。

***

### 提示

为了防止意外更新过多行，请将 `LIMIT` 子句应用于您的 `UPDATE`：

```sql
UPDATE users SET email='mike@authors.
com' WHERE user_id = 18 LIMIT 1
```

***

### 提示

您永远不应该对主键列执行 `UPDATE`，因为主键值永远不应改变。更改主键的值可能会产生严重后果。

***

### 提示

要在 phpMyAdmin 中更新记录，您可以使用 SQL 窗口或选项卡运行 `UPDATE` 查询。或者，运行 `SELECT` 查询以查找要更新的记录，然后单击记录旁边的铅笔图标。这将弹出一个类似于插入表单的表单，您可以在其中编辑记录的当前值。

***

### 删除数据

除了更新现有记录外，您可能需要采取的另一步是从数据库中完全删除一条记录。为此，您可以使用 `DELETE` 命令：

```sql
DELETE FROM tablename
```

按原样编写该命令将删除表中的每一条记录，使其再次变为空。一旦删除了记录，就无法检索它。

在大多数情况下，您想要删除的是单个行，而不是全部。为此，请应用 `WHERE` 子句：

```sql
DELETE FROM tablename WHERE condition
```

#### 删除记录

**1.** 查找要删除记录的主键 ![Image](img/circle-a.jpg)：

```sql
SELECT user_id FROM users
WHERE first_name='Peter'
AND last_name='Tork';
```

![Image](img/05_figure_33_a.jpg)

![Image](img/circle-a.jpg)*user_id* 值将用于在 `DELETE` 查询中引用此记录。

正如 `UPDATE` 示例中一样，我首先需要确定要用于删除的主键。
