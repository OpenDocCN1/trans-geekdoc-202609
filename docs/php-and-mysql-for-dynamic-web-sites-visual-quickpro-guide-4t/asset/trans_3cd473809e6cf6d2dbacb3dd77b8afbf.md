
该查询首先在第一个 *messages* 表实例 *m1* 中选择每一条根级消息——即那些 `parent_id` 值为 `0` 的消息。然后将这些记录与第二个 *messages* 表实例 *m2* 进行外连接。如果你自己运行此查询，将会看到选出了根消息的主题，以及该消息回复的主题（如果适用）。

自连接不是最流行的连接类型，但有时能比大多数其他解决方案更好地解决问题。

---

### 提示

连接可以使用涉及任意列的条件来创建，而不仅限于主键和外键，尽管那是最常用的比较基础。

---

### 提示

你可以使用 `database.table.column` 语法跨多个数据库执行连接，只要每个数据库都在同一台服务器上（你无法跨网络执行此操作），并且你以拥有访问所有相关数据库权限的用户身份连接。

---

### 提示

左外连接中的单词 `OUTER` 是可选的，且经常被省略。若要正式书写，你可以写成：

```sql
SELECT f.name, DATE_FORMAT(m.date_entered, '%M %D, Y') AS Date FROM forums AS f LEFT OUTER JOIN messages AS m USING (forum_id) ORDER BY date_entered DESC;
```

---

#### 连接三个或更多表

连接是一个有点复杂但很重要的概念，希望你目前能跟得上。还有两种连接的用法你应该熟悉：*自连接*（在侧边栏中讨论）和三个或更多表的连接。

当连接三个或更多表时，记住两个表之间的连接会创建一个结果虚拟表会有所帮助。当你添加第三个表时，连接就是在这个初始虚拟表和第三个被引用的表之间进行 ![Image](graphics/circle-j.jpg)。三表连接的语法格式为：

```sql
SELECT what_columns FROM tableA JOIN_TYPE tableB JOIN_CLAUSE JOIN_TYPE tableC JOIN_CLAUSE
```

![Image](graphics/07_figure_10_j.jpg)

![Image](graphics/circle-j.jpg)三表连接的工作原理：首先创建一个结果虚拟表，然后将第三个表连接到该虚拟表。

这两种情况下的连接类型不必相同——一种可以是内连接，另一种可以是外连接——而且连接子句几乎肯定不同。你甚至可以在末尾添加 `WHERE`、`ORDER BY` 和 `LIMIT` 子句。简单来说，要对两个以上的表执行连接，只需根据需要继续添加 `JOIN_TYPE tableX JOIN_CLAUSE` 部分即可。

跨越三个或更多表的连接可能会遇到三个常见问题。第一个是简单的语法错误，特别是当你使用括号分隔子句时。第二个是列名歧义错误，这在任何连接类型中都很常见。第三个可能的问题是返回结果为空。如果发生这种情况，请将连接简化为仅两个表以确认结果，然后尝试重新应用额外的连接子句以找出问题所在。

#### 在三个或更多表上使用连接

**1.** 连接到 MySQL 并选择 *forum* 数据库（如果尚未选择）。

**2.** 检索用户 *troutster* 发布的每条消息的消息 ID、主题和论坛名称 ![Image](graphics/circle-k.jpg)：

```sql
SELECT m.message_id, m.subject, f.name
FROM users AS u
INNER JOIN messages AS m
USING (user_id)
INNER JOIN forums AS f
USING (forum_id)
WHERE u.username = 'troutster';
```

![Image](graphics/07_figure_11_k.jpg)

![Image](graphics/circle-k.jpg)跨所有三个表的内连接。

此连接类似于本章前面的一个，但通过引入第三个表更进了一步。

**3.** 检索每个用户的用户名、消息主题和论坛名称 ![Image](graphics/circle-l.jpg)：

```sql
SELECT u.username, m.subject, f.name
FROM users AS u
LEFT JOIN messages AS m
USING (user_id)
LEFT JOIN forums AS f
USING (forum_id);
```

![Image](graphics/07_figure_12_l.jpg)

![Image](graphics/circle-l.jpg)此左连接返回每个用户、每条发布的消息主题和每个论坛名称。如果用户未发布消息（如顶部的 *finchy*），其主题和论坛名称值将为 `NULL`。

第 2 步中的查询执行两次内连接，而此查询执行两次外连接。此查询背后的过程由 ![Image](graphics/graycircle-j.jpg) 中的图表直观表示。

**4.** 找出拥有最近五条发帖的用户，同时选择消息主题和论坛名称 ![Image](graphics/circle-m.jpg)：

```sql
SELECT u.username, m.subject, f.name
FROM users AS u
INNER JOIN messages AS m
USING (user_id)
INNER JOIN forums AS f
USING (forum_id)
ORDER BY m.date_entered DESC
LIMIT 5;
```

![Image](graphics/07_figure_13_m.jpg)

![Image](graphics/circle-m.jpg)此内连接返回来自所有三个表的值，并应用了 `ORDER BY` 和 `LIMIT` 子句。

为了检索用户名、消息主题和论坛名称，需要跨所有三个表进行连接。由于查询仅查找已发帖的用户，因此内连接是合适的。两次连接的结果将是每个用户名、他们发布的每条消息、在每个论坛中。然后按消息的 *date_entered* 列对该结果排序，并仅限制为前五条记录。

### 分组选定结果

[第 5 章](#ch05.html#ch05) 讨论并演示了可在 MySQL 中使用的几类不同函数。另一类用于更复杂查询的是 *分组* 或 *聚合* 函数（**[表 7.1](#ch07.html#ch07table01)**）。

**表 7.1. 分组函数**

![Image](graphics/07tab01.jpg)

[第 5 章](#ch05.html#ch05) 中介绍的大多数函数一次操作单行中的单个值（例如，格式化日期列中的值），而分组函数返回的结果基于一组行中单个列出现的值。例如，要在 *banking* 数据库中查找平均账户余额，你可以运行此查询 ![Image](graphics/circle-a.jpg)：

```sql
SELECT AVG(balance) FROM accounts
```

![Image](graphics/07_figure_14_a.jpg)

![Image](graphics/circle-a.jpg)使用 `AVG()` 函数查找所有账户余额的平均值。

要查找最小和最大账户余额，请使用 ![Image](graphics/circle-b.jpg)：

```sql
SELECT MAX(balance), MIN(balance) FROM accounts
```

![Image](graphics/07_figure_15_b.jpg)

![Image](graphics/circle-b.jpg)`MAX()` 和 `MIN()` 函数返回表中找到的最大和最小账户值。

要仅计算表（或结果集）中的记录数，请将 `COUNT()` 应用于每一列或保证有值的每一列：

```sql
SELECT COUNT(*) FROM accounts
```

`AVG()`、`COUNT()` 和 `SUM()` 函数也可以使用 `DISTINCT` 关键字，以便聚合仅应用于不同的值。例如，`SELECT COUNT(customer_id) FROM accounts` 将返回账户数量，但 `SELECT COUNT(DISTINCT customer_ID) FROM accounts` 将返回拥有账户的客户数量 ![Image](graphics/circle-c.jpg)。

![Image](graphics/07_figure_16_c.jpg)

![Image](graphics/circle-c.jpg)`COUNT()` 函数，无论是否带 `DISTINCT` 关键字，只是计算记录集中的记录数。

聚合函数单独使用时返回单个值（如 ![Image](graphics/graycircle-a.jpg)、![Image](graphics/graycircle-b.jpg) 和 ![Image](graphics/graycircle-c.jpg) 所示）。当聚合函数与 `GROUP BY` 子句一起使用时，将为结果集中的每一行返回一个聚合值 ![Image](graphics/circle-d.jpg)：

```sql
SELECT AVG(balance), customer_id FROM accounts GROUP BY customer_id
```

![Image](graphics/07_figure_17_d.jpg)
