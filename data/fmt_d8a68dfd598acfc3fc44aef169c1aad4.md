
```mysql
mysql> SELECT firstName, lastName FROM members WHERE firstName LIKE 'Mar_y';
+-----------+-----------+
| firstName | lastName |
+-----------+------------+
| Marty | Pareene |
+-----------+-----------+
1 row in set (0.03 sec)
```

注意，此查询没有返回 Mary Newton 的记录，因为下划线恰好匹配一个字符，而“Mary”的“r”和“y”之间之间字符了。

# 第三部分：在实战中使用 PHP

你可以使用 `NOT LIKE` 代替 `LIKE` 来反转比较含义。下面的示例显示了爱好不包含旅行的成员列表：

```mysql
mysql SELECT username, firstName, lastName, otherInterests FROM members
WHERE otherInterests NOT LIKE '%travel%';
+-----------+-------------+------------+--------------------------------+
| username | firstName | lastName | otherInterests |
| sparky  | John      | Sparks     | Football, fishing and gardening |
| jojo    | Jo        | Parareen   | Genealogy, writing, painting |
| marty   | Marty     | Scrivener  | Guitar playing, rock music, clubbing |
| nickb   | Nick      | Blakeley  | Watching movies, cooking, socializing |
| bigbill | Bill      | Swan       | Tennis, judo, music |
+-----------+-------------+------------+--------------------------------+
5 rows in set (0.05 sec)
```

# 数据汇总

正如 PHP 有许多内置函数一样，MySQL 也提供了许多函数来协助你的查询。在本节中，我们将查看聚合函数。这些函数不是返回表中的实际数据，而是让你以不同的方式汇总数据：

- `count()` —— 返回选定的行数
- `sum()` —— 返回字段的总和
- `min()` —— 返回字段的最小值
- `max()` —— 返回字段的最大值
- `avg()` —— 返回字段的平均值

你可以以两种方式使用 `count()`：

- `count( fieldname )` —— 返回 `fieldname` 不为 NULL 的行数
- `count(*)` —— 返回选定的行数，无论是否包含 NULL 值

这里有两个 `count()` 示例。第一个示例统计表中的所有行：

```mysql
mysql> SELECT COUNT(*) FROM members;
+-----------+
| COUNT(*) |
| 7        |
+-----------+
1 row in set (0.02 sec)
```

# 第13 章：使用 PHP 从 MySQL 获取数据

另一个示例只统计女性的数量：

```mysql
mysql> SELECT COUNT(*) FROM members WHERE gender = 'f';
+-----------+
| COUNT(*) |
|      3    |
+-----------+
1 row in set (0.00 sec)
```

注意，两种情况下 MySQL 工具都报告结果集中只有一行。虽然第一个示例从 `members` 表中选取了七行，但聚合函数 `count()` 获取这些行并返回单个值 (7)。最终结果集只有一行。同样，第二个 `count()` 查询将三行结果简化为 3。

剩余的聚合函数工作方式正如你所期待。例如，此查询返回所有成员访问网站的总访问次数：

```mysql
mysql> SELECT SUM( numVisits) FROM accessLog;
+-----------------------+
| SUM(numVisits) |
+-----------------------+
|          9      |
+-----------------------+
1 row in set (0.00 sec)
```

你可以对日期使用 `min()` 和 `max()` 等函数。此查询返回第一个成员加入俱乐部的日期：

```mysql
mysql> SELECT MIN( joinDate ) FROM members;
+----------------------+
| MIN(joinDate)|
+----------------------+
| 2006-03-03 |
+----------------------+
1 row in set (0.02 sec)
```

# 消除重复结果

有时使用了 WHERE 子句，查询返回的数据仍然比你需要的多。假设你的 `accessLog` 表包含以下数据：

```mysql
mysql> SELECT * FROM accessLog;
+--------------------------------------+
| memberId | pageUrl    | numVisits | lastAccess |
+----------|-------------|------------|------------+
| 1 | diary.php   | 2 | 2008-11-03 14:12:38 |
| 3 | books.php   | 2 | 2008-11-08 19:47:34 |
| 3 | contact.php | 1 | 2008-11-08 14:52:12 |
| 6 | books.php   | 4 | 2008-11-09 11:32:44 |
+--------------------------------------+
```

## 第三部分：实战中使用 PHP

现在，假设你想获取自 11 月 7 日以来访问过网站的用户 ID 列表。你可以创建一个如下所示的查询：

```mysql
mysql> SELECT memberId FROM accessLog WHERE lastAccess > '2008-11-07';
```

| memberId |
| :--- |
| 3 |
| 6 |

```mysql
----------------------++
| memberId             |
----------------------++
|            3             |
|            6             |
----------------------++
3 rows in set (0.00 sec)
```

现在出现了一个小问题：值 `3` 在结果集中出现了两次。这是因为 `accessLog` 表中有两条 `memberId` 为 3 且 `lastAccess` 日期晚于 11 月 7 日的记录，这代表用户 3 访问了两个不同的页面。例如，用户 3 会出现两次。想象一下，如果该用户访问了 100 个不同的页面，会发生什么！

为了消除重复项，你可以在查询的 `SELECT` 之后放置 `DISTINCT` 关键字：

```mysql
mysql> SELECT DISTINCT memberId FROM accessLog WHERE lastAccess > '2008-11-07';
```

| memberId |
| :--- |
| 3 |
| 6 |

```mysql
----------------------++
| memberId             |
----------------------++
|            3             |
|            6             |
----------------------++
2 rows in set (0.00 sec)
```

`DISTINCT` 会从结果集中移除与其他行完全重复的行。例如，以下查询在 `memberId` 列中包含两个 `3` 的实例，因为每个实例的 `pageUrl` 列是不同的：

```mysql
mysql> SELECT DISTINCT memberId, pageUrl FROM accessLog WHERE lastAccess > '2008-11-07';
```

| memberId | pageUrl |
| :--- | :--- |
| 3 | books.php |
| 3 | contact.php |
| 6 | books.php |

```mysql
--------------------------------------------+
| memberId | pageUrl               |
--------------------------------------------+
|            3  | books.php             |
|            3  | contact.php          |
|            6  | books.php             |
--------------------------------------------+
3 rows in set (0.00 sec)
```

## 结果分组

你已经看到过如何使用 `count()` 和 `sum()` 等函数从表中检索整体的聚合数据，例如书俱乐部中有多少位女性成员。如果你想获取更细致的信息呢？例如，你想找出每个成员过的不同页面 URL 的数量。你可以尝试这个查询：

## 第 13 章：使用 PHP 从 MySQL 获取数据

```mysql
mysql> SELECT count( pageURL ) FROM accessLog;
```

| count ( pageURL ) |
| :--- |
| 4 |

```mysql
+----------------------+
| count ( pageURL ) |
+----------------------+
|          4         |
+----------------------+
1 row in set (0.00 sec)
```

这不对。这个查询给你的只是表中的总行数！相反，你需要根据 `member ID` 对 `pageURL` 计数进行分组。为了做到，你需要添加一个 `GROUP BY` 子句。例如：

```mysql
mysql> SELECT memberID, count( pageURL ) FROM accessLog GROUP BY memberID;
```

| memberID | count ( pageURL ) |
| :--- | :--- |
| 1 | 1 |
| 3 | 2 |
| 6 | 1 |

```mysql
+----------+----------------+
| memberID | count ( pageURL ) |
+----------+----------------+
|      1 |              1 |
|      3 |              2 |
|      6 |              1 |
+----------+----------------+
3 rows in set (0.00 sec)
```

这样好多了。通过将聚合函数 `count()` 与用于分组的列（`memberID`）结合，你可以按成员查看统计数据。在这种情况下，你可以看到成员 1 和 6 分别都只访问了一个不同的页面，而成员 3 访问了两个不同的页面。

你可以在同一个查询中结合 `GROUP BY` 和 `ORDER BY`。以下是如何对之前的数据进行排序，使得访问不同页面数量数量的成员位于表格顶部：

```mysql
mysql> SELECT memberID, count( pageURL ) FROM accessLog GROUP BY memberID
ORDER BY count( pageURL ) DESC;
```

| memberID | count ( pageURL ) |
| :--- | :--- |
| 3 | 2 |
| 1 | 1 |
| 6 | 1 |

```mysql
+----------+----------------+
| memberID | count ( pageURL ) |
+----------+----------------+
|      3 |              2 |
|      1 |              1 |
|      6 |              1 |
+----------+----------------+
3 rows in set (0.00 sec)
```

## 从多个表中提取数据

到为止，你所有的查询都是一次只操作一个表。然而，关系型数据库的真正威力在于，你可以同时查询多个表，使用选定的列将表相互关联起来。这种查询被称为“连接”（join），连接允许你创建复杂的查询，以从你的表中检索各种实用的信息。

## 第三部分：实战中使用 PHP

在之前从 `accessLog` 表中检索统计数据的示例中，你的结果集包含 `memberId` 列中的整数成员 ID 列表。例如，假设你想获取访问过 Web 的成员列表：

```mysql
mysql> SELECT DISTINCT memberId FROM accessLog;
```

| memberId |
| :--- |
| 1 |
| 3 |
| 6 |

```mysql
+----------------+
| memberId |
+----------------+
|      1 |
|      3 |
|      6 |
+----------------+
3 rows in set (0.00 sec)
```

现在，成员 ID 本身并没有什么帮助。如果你想知道涉及的成员姓名，你需要对 `members` 表中的数据运行另一个查询：

```mysql
mysql> SELECT id, firstName, lastName FROM members;
```

| id | firstName | lastName |
| :--- | :--- | :--- |
| 1 | John | Sparks |
| 2 | Mary | Newton |
| 3 | Jo | Scrivener |

```mysql
+----+-------------+----------+
| id | firstName | lastName |
+----+-------------+----------+
|  1 | John       | Sparks   |
|  2 | Mary       | Newton   |
|  3 | Jo        | Scrivener |
+----+-------------+----------+
```

## 第三部分：PHP 实践

在这个查询中，`accessLog` 成员名称多次出现。幸运的是，SQL 允许你通过在 `FROM` 子句中为每个表指定别名来创建短表别名。你可以使用这些别名来引用表，而不是每次都使用完整的表名：

```mysql
mysql> SELECT DISTINCT al.memberId, m.firstName, m.lastName FROM accessLog
al, members m WHERE al.memberId = m.id;
```

| memberId | firstName | lastName |
|----------|-----------|----------|
| 1 | John | Sparks |
| 3 | Jo | Scrivener |
| 6 | Bill | Swan |

3 rows in set (0.00 sec)

你还可以使用 `AS` 关键字为查询返回的列创建别名。考虑你看过的这个查询：

```mysql
mysql> SELECT memberId, count( pageUrl ) FROM accessLog GROUP BY memberId;
```

| memberId | count( pageUrl ) |
|----------|--------------------|
| 1 | 1 |
| 3 | 2 |
| 6 | 1 |

3 rows in set (0.00 sec)

注意结果集中的第二列是 `count( pageUrl )`。这不仅很有描述性，而且发现在 PHP 脚本中引用它会很别扭。因此，将其重命名为更有意义的名字是一个好主意：

```mysql
mysql> SELECT memberId, count( pageUrl ) AS urlsView FROM accessLog GROUP BY memberId;
```

| memberId | urlsView |
|----------|----------|
| 1 | 1 |
| 3 | 2 |
| 6 | 1 |

3 rows in set (0.00 sec)
