
## 使用 LIKE

当然在搜索字符串时，会有你并不完全确定字符串长什么样子的情况。在这种情况下，你需要使用通配符。要使用通配符，需要 like 谓词。

有两种通配符可用，下划线（_）和百分号（%）。下划线代表单个字符。百分号代表任意数量的字符，包括零个。

所以，例如，如果你要查找名字为 Daniel 或 Danny 或 Dan 的人，你就会使用百分号。

```
select * from users where fname like 'Dan%'
```

请注意，因为百分号可以匹配零个字符，前面的查询也会匹配名字“Dan”。

但是，如果出于某种奇怪的原因，你需要查找数据库中名字以字母 J 开头且为四个字母的所有人，你会这样构造查询：（注意字母 J 后面跟着三个下划线。）

```
select * from users where fname like 'J___'
```

这三个下划线将匹配任意字符并返回像 Jean、John 和 Jack 这样的名字。Jay 和 Johnny 不会被返回。

![](img/de0823012275cf4ceebdb822a56e6b71_87_0.png)

> 在 MySQL 中，like 比较不区分大小写。这与大多数实现大不相同。

## ORDER BY

在处理关系数据库时，你应该始终牢记一件事：任何表中行的存储是完全随意的。通常，你不会知道数据库决定以何种顺序放置你插入的行。当顺序很重要时，你可以在查询末尾加上 order by 来指定返回行的顺序。

此命令可以根据任何列类型进行排序：字母、时间或数字。此外，order by 允许你通过分别在 order by 后放置 asc 或 desc 来按升序或降序排序。如果两者均未包含，则默认使用 asc。

要对表中的条目进行字母排序，你可能希望确保此列表按名字和姓氏同时排序：

```
select * from users order by lname, fname
```

你可以按任意多个列排序，并且可以根据需要混合使用 asc 和 desc。以下查询不是特别有用，但它是可行的：

```
select * from users order by lname asc, fname desc
```

## LIMIT

limit 谓词将限制从查询中返回的行数。它允许你指定起始行和想要返回的行数。要获取表中的前五行，运行以下查询：

```
select * from users limit 0,5
```

要按字母顺序查找前五行，你可以使用 limit 与 order by：

```
select * from users order by lname, fname limit 0,5
```

你可能会注意到编号类似于数组——第一行为第 0 行。要获取表的第二五行，你可以运行以下语句：

```
select * from users limit 5,5
```

limit 在你希望限制单页显示的情况下特别有用。你将在整本书中看到 limit 的使用。即使是本书的第一個应用第 8 章，也使用了 limit。

## GROUP BY 和聚合函数

还记得我们谈论使用 select 与 distinct 时，它是如何删除不需要的行吗？这可能看起来很酷，但与使用 group by 及其关联的聚合函数所能获得的效果相比，简直不值一提。

考虑这个任务：你希望知道数据库中每个州的条目数（例如，加州六个，纽约七个，佛蒙特州两个）。如果你执行 select distinct state from users order by state，你会得到数据库中每个州的列表，但无法得到数量。当 MySQL 处理查询时遍历表，它只是跳过会返回相同值的行。

然而，使用 group by 时，MySQL 会创建一个临时表，其中保留符合你条件的行和列的所有信息。这使得引擎能够在临时表上执行一些非常关键的任务。展示 group by 能做什么的最简单方法可能是展示其中一个聚合函数。我们从 count() 开始。

MySQL 可能不会为每个 group by 实际创建一个临时表；然而，group by 的实际内部工作原理相当复杂，而这是一种思考 MySQL 在做什么的好方法。

### COUNT()

再次，查询的目标是找出 users 表中每个州的人数。为此你将使用 group by 与 count()。请记住，当使用 group by 子句时，可以想象 MySQL 创建一个临时表，在其中汇集相似的行。然后 count() 函数（你猜对了）统计每个组中的行数。请查看以下查询以及图 3-5 中返回的结果。

```
select state, count(*) from users group by state
```

![](img/de0823012275cf4ceebdb822a56e6b71_89_0.png)

图 3-5：使用 select state, count(*) from users group by state 查询的结果

这里的星号 (*) 表示应统计组内的所有行。count(*) 函数对于获取表中的总行数也很方便。

```
select count(*) from users
```

在 group by 中，你也可以指定要计数的特定字段。count 会查找非空值的数量。例如，图 3-6 中的表。

![](img/de0823012275cf4ceebdb822a56e6b71_90_0.png)

图 3-6：users_ages 表

从这个表计数非空值可能看起来没什么用。然而，如果你真的很热衷于统计，你可以使用这个表来计算每个城市有多少比例的人愿意透露年龄。首先你需要每个特定城市和州的所有条目的计数；随后，你需要 age 字段中所有非空值的计数。

```
Select city, state, count(*), count(age) from users_ages
group by state, city
```

从图 3-7 的结果可以看出，芝加哥人比沿海地区的人坦率得多。

现在是介绍别名的好时机。在某些时候，特别是当你使用函数时，查询返回的列名可能不是你想要的。例如，在图 3-7 中，你可能希望表头比 count(*) 更具描述性。

你可以在任何函数或列名后加上 as，然后指定你喜欢的名称。as 只是指定别名。如果需要多于一个单词的列名，请用单引号将文本字符串括起来。

![](img/de0823012275cf4ceebdb822a56e6b71_91_0.png)

图 3-7：使用 count() 函数查询的结果

谈到别名时，我还要提到 MySQL 中有各种函数（参见附录 I）。它们从简单的数学函数到更复杂的操作不等。下面我加入了一些数学运算以阐明查询的目的。请注意 as 子句的使用以及它对查询显示的影响（见图 3-8）。

```
Select city, state, count(*) as 'Total Rows',
    count(age) as 'The Willing',
    (count(age)/count(*)*100) as 'Percent Responding'
from users_ages
group by state, city
```

你也可以对表使用别名。在处理多个表时这会特别有帮助。我将在“多表连接”部分更详细地讨论这一点。

### SUM()

sum() 函数返回给定列的总和，并且几乎总是与 group by 子句一起使用。例如，如果你为非营利组织运行一个应用程序，你可能想知道每个州的总捐款。你的工作表可能看起来像图 3-9 中的那样。

![](img/de0823012275cf4ceebdb822a56e6b71_92_0.png)

图 3-8：使用函数和别名查询的结果

![](img/de0823012275cf4ceebdb822a56e6b71_92_1.png)

图 3-9：使用 sum() 会很有帮助的表
