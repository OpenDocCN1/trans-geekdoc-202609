

## 第 3 章：通过 select 获取你想要的内容

MySQL 并不实际上会为每个组创建一个临时表；然而，分组的实际内部机制相当复杂，这是理解 MySQL 运行机制的一种很好的方法。

## COUNT()

再次，你的查询目标是找出 `users` 表每个州的人数。为了实现这一点，你将使用 `group by` 配合 `count()`。

记住，当使用 `group by` 子句时，你可以想象 MySQL 正在创建一个用于组装行的临时表。`count()` 函数（正如你所想的那样）会统计每个组的行数。查看以下查询以及图 3-5 中返回的结果。

```sql
select state, count(*) from users group by state
```

![](img/245156cc770929860a3ede93c01f9981_89_0.png)

图 3-5：使用 select state, count(*) from users group state 的查询结果

在这里，星号 (`*`) 表示应该统计组内的所有行。`count(*)` 函数对于获取表的总行数也非常方便。

```sql
select count(*) from users
```

在组内，你也可以指定一个要计数的特定字段；`count()` 会查找非空值的数量。例如，3-6 中的表。

![](img/245156cc770929860a3ede93c01f9981_90_0.png)

图 3-6：users_ages 表

从这个表中统计非空值似乎并没有太大用处。然而，如果你是一个非常热衷于统计的人，你可以利用这张表来计算每个城市中对你年龄感到舒适的百分比。首先，你需要统计每个特定城市和州的条目数；随后，你需要统计该字段中所有非空值的数量。

```sql
select city, state, count(*) from user_ages group by state, city
```

从图 3-7 的结果中你可以看到芝加哥人比沿海地区坦率得多。现在是引入别名（aliases）的好时机。在某些情况下，特别是当你使用函数时，查询返回的列名不是你想要的。例如，在图 3-7 中，你可能希望表头比 `count(*)` 更具描述性。

你可以在任何函数或列名后加上 `as` 单词，然后指定一个你喜欢的名称作为别名。如果你需要一个多个单词的列名，请用单引号括起字符串。

![](img/245156cc770929860a3ede93c01f9981_91_0.png)

**图 3-7：** `count()` 函数的查询结果

谈到别名，我还会提到 MySQL 中提供了多种可用函数（参见附录 I）。它们从简单的数学函数到更复杂的操作不等。我在下面加入了一些数学计算，以澄清查询的目的。注意 `as` 子句的使用以及它是如何影响查询显示的（如图 3-8 所示）。

```sql
select city, state, count(*) as 'Total Rows',
count(age) as 'The Willing',
(count(age)/count(*)*100) as 'Percent Responding'
from user_ages
group by state, city
```

你可以在表上使用别名。这在处理多个表时将特别有用。我将在“多表连接”部分中详细讨论这一点。

## SUM()

`sum()` 函数返回给定列的和，并且始终与 `group` 子句一起使用。例如，如果你正在为一个非营利组织运行应用程序，你可能想知道每个州的总贡献额。你正在处理的表可能像图 3-9 所示。

![](img/245156cc770929860a3ede93c01f9981_92_0.png)

图 3-8：使用函数和别名的查询结果

![](img/245156cc770929860a3ede93c01f9981_92_1.png)

图 3-9：使用 sum() 时会有用的表

要获取每个州的总额，你需要运行以下查询：

```sql
select state, sum(contribution) from contributions group by state
```

## MIN()

`min()` 函数提取每个分组中的最低值。要找到任何州的最低贡献额，只需对之前的查询进行微小的修改：

```sql
select state, min(contribution) from contributions group by state
```

## MAX()

正如你可能猜的那样，`max()` 将返回组中的最高值：

```sql
select state, max(contribution) from contributions group by state
```

## AVG()

`avg()` 返回组的平均值：

```sql
select state, sum(contribution) from contributions group by state
```

你可以将所有这些组合在一起创建一个非常有用的查询：

```sql
select state, sum(contribution) as 'Total',
avg(contribution) as 'Average',
min(contribution) as 'Minimum',
max(contribution) as 'Maximum'
from contributions
group by state
```

## GROUP BY

大多数数据库要求 `select` 子句中的字段必须在 `group by` 子句中使用。但 MySQL 提供了更多选项；例如，如果你想找出每个城市的人数，可以运行：

```sql
select city, count(*) from users group by city
```

## HAVING

`having` 谓词限制了 `group by` 显示的行。这与 `where` 子句不同。`where` 子句实际上限制的是进入计算的行。如果你需要找到平均捐款金额超过 100 的所有州的平均值，你必须使用 `having`：

```sql
select avg(donations) as avg_contrib, state
from contributions
group by state
having avg(donations) > 100
```

## 连接表

如果你读过第 1 章，你就知道关系型数据库之所以运行良好是因为它们对信息进行了分段。不同的表持有不同主题的信息，字段被插入到表中以维持关系。完成规范化过程后，可能如果没有其他表，你的任何表都无法使用。这就是为什么在 `select` 语句中需要连接表。

## 两表连接（等值连接）

为了保持连续性，我们将复习第 1 章中的两个表。请看图 3–11 中的表。

| company_id | company_name | address |
|---|---|---|
| 1 | Big Co Company | 1121 43rd St |
| 2 | Little Co Company | 4444 44th St |

| contract_id | company_id | Name | Title | Phone | Email |
|---|---|---|---|---|---|
| 1 | 1 | Jay Greenspan | Vice President | 41555122 | 1121 43rd St |
| 2 | 1 | Brad Bulder | President | 415555222 | 4444 44th St |
| 3 | 2 | John Doe | Lucky | 2125556666 | 4444 44th St |

图 3–11：需要连接的表

