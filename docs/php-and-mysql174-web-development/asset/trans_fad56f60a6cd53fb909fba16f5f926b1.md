

# 从数据库中检索数据 255

通过在查询中添加此连接条件，你实际上将连接转换为了另一种类型，称为等值连接（equi-join）。

还要注意使用的点符号法，它可以明确表示哪个列来自哪个表；即 `Customers.CustomerID` 指 `Customers` 表中的 `CustomerID`，而 `Orders.CustomerID` 指 `Orders` 表中的 `CustomerID`。

如果列名具有歧义——即它出现在多个表中——则需要使用这种点符号法。作为一种扩展，它也可以用于区分不同数据库中的列名。本示例使用了 `table.column` 符号，通过这种符号你可以使用 `database.table.column` 符号来指定数据库，例如测试诸如 `books.Orders.CustomerID = other_db.Orders.CustomerID` 这样的条件。

然而，你在查询的所有引用中都可以使用点符号。使用这种符号是一个好主意，特别是当你的查询开始变得复杂时。MySQL 并不要求这样做，但它让你的查询更具人类可读性且易于维护。注意我们在之前的查询中也遵循了这一约定，例如在使用条件时：

```
Customers.Name = 'Julie Smith'
```

`Name` 列只出现在 `Customers` 表中，所以我们不需要指定它来自哪个表。MySQL 不会混淆。但对于人类来说，单独的 `Name` 列是模糊的，因此当你将其指定为 `Customers.Name` 时，查询的含义就清晰了。

# 连接两个表

连接两个两个表并不比连接两个表更困难。作为一个一般规则，你需要通过连接条件成对地连接表。将其构想为从数据表追踪到该表的关系。

例如，如果你想知道哪些客户订购过 Java 书籍（也许你可以向他们发送有关新 Java 书籍的信息），你需要通过多个表来追踪这些关系。

让我们看看这些代码到底执行了什么：

```
SELECT Customers.Name
FROM Customers, Orders, Order_Items, Books
WHERE Customers.CustomerID = Orders.CustomerID
AND Orders.OrderID = Order_Items.OrderID
AND Order_Items.ISBN = Books.ISBN
AND Books.Title LIKE '%Java%';
```

# 第 10 章操作你的 MySQL 数据库

此查询返回以下输出：

| Name |
|------|
| Michelle Arthur |
| 1 row in set (0.01 sec) |

注意，这个示例通过四个不同的表追踪了数据。要通过等值连接实现这一点，通常情况下，你每一对想要连接的表都需要一个连接条件，因此，连接条件的总数少于你想要连接的表总数。这个经验法则对于调试不起作用的查询很有用。检查你的连接条件，确保你遵循了从“已知”到“想要知道的信息”的路径。

# 查找不匹配的行

你在 MySQL 中将使用的主要连接类型是左连接（left join）。

在之前的示例中，注意只有在表之间找到匹配项的行才被包含在内。有时你可能特别想要那些没有匹配项的行——例如从未下过订单的客户或从未被订购的书籍。

在 MySQL 中回答此类问题的一种方法是使用左连接。这种连接根据两个表之间的特定连接条件来匹配行。如果右表中不存在匹配的行，则结果中将添加一行，其右侧列包含 `NULL` 值。

让我们看一个例子：

```
SELECT Customers.CustomerID, Customers.Name, Orders.OrderID
FROM Customers LEFT JOIN Orders
ON Customers.CustomerID = Orders.CustomerID;
```

此 SQL 查询使用左连接来连接 `Customers` 和 `Orders`。注意左连接对连接条件使用了略有不同的语法：在这种情况下，连接条件位于语句的特殊子句中。

此查询的结果是：

| CustomerID | Name | OrderID |
|------------|------|---------|
| 1 | Julie Smith | 2 |
| 2 | Alan Wong | 3 |
| 3 | Michelle Arthur | 1 |
| 3 | Michelle Arthur | 4 |

4 rows in set (0.00 sec)

# 从数据库中检索数据

此输出仅显示那些 `OrderID` 非 `NULL` 的客户。

如果你只想查看没有订购任何东西的客户，可以检查右表主键字段（在此例中为 `OrderID`）中的 `NULL`，因为在任何行中它都应该是 `NULL`：

```
SELECT Customers.CustomerID, Customers.Name
FROM Customers LEFT JOIN Orders
USING (CustomerID)
WHERE Orders.OrderID IS NULL;
```

在这种情况下，结果是没有返回任何行，因为我们所有的客户都下过订单。

让我们添加一个新客户：

```
INSERT INTO Customers VALUES
(NULL, 'George Napolitano', '177 Melbourne Road', 'Coburg');
```

如果重复左连接查询，结果是：

| CustomerID | Name |
|---|---|
| 4 | George Napolitano |

1 row in set (0.00 sec)

正如你所预期的，因为 George 是新客户，他是唯一尚未下过订单的人。

另外注意此示例对连接条件使用了不同的语法。左连接支持第一个示例中使用的 `ON` 语法或第二个示例中使用的 `USING` 语法。注意 `USING` 语法没有指定连接属性来自哪个表；

# 使用表的其他名称：别名

能够通过名称引用表通常非常方便且必不可少的。表的名称称为别名（Aliases）。你可以在查询开始时创建它们。考虑你之前看到的查询，使用别名重写：

```
SELECT C.Name
FROM Customers AS C, Orders AS O, Order_Items AS OI, Books AS B
WHERE C.CustomerID = O.CustomerID
AND O.OrderID = OI.OrderID
AND OI.ISBN = B.ISBN
AND B.Title LIKE '%Java%';
```

当你想要将表与其连接时，需要使用别名。这项任务听起来比实际上更复杂、深奥。它是用的，例如如果你想找到住在同一城市的客户。使用不同的别名：

```
SELECT C1.Name, C2.City
FROM Customers AS C1, Customers AS C2
WHERE C1.City = C2.City
AND C1.Name != C2.Name;
```

你基本上是在假设 `Customers` 表是两个表 `C1` 和 `C2`，并对 `City` 列进行连接。注意你还需要第二个条件 `C1.Name != C2.Name`；这是为了避免每个客户与自己匹配。

# 连接总结

我们描述的不同连接类型总结在表 10.2 中。还有其他类型，但这些是你将使用的主要的。

| 表 10.2 MySQL 连接类型 |
| Name | Description |
|---|---|
| 笛卡尔积 | 连接所有表中所有行的组合。通过在表名之间指定逗号且不指定 `WHERE` 子句来实现。 |
| 全连接 | 同上。 |
| 交叉连接 | 同上。也可以通过在连接的表之间指定 `CROSS JOIN` 关键字来实现。 |
| 内连接 | 语义等同于逗号。也可以指定 `INNER JOIN` 关键字。没有 `WHERE` 子句时等同于全连接。通常你还会指定一个 `WHERE` 条件以这是一个真正的内连接。 |
| 等值连接 | 使用带有 `=` 的条件表达式来匹配连接不同表中的行。在 SQL 中，这是带有 `WHERE` 子句的连接。 |
| 左连接 | 尝试跨表匹配行，并用 `NULL` 填充不匹配的行。在 SQL 中配合 `LEFT JOIN` 关键字使用。用于查找缺失值。你可以等效地使用 `RIGHT JOIN`。 |

