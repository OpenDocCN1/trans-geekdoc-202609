

# 第 13 章 高级 MySQL 编程

已永久写入数据库的事务被称为“提交”（committed）。
未写入数据库的事务——即数据库重置为事务开始前的状态——被称为“回滚”（rollback）。

# 在 InnoDB 中使用事务

默认情况下，MySQL 以“自动提交”（autocommit）模式运行。这意味着你执行的每条语句都会立即写入数据库（提交）。如果你正在使用事务安全的类型，很可能你不希望这种行为。

要在当前会话中关闭自动提交，请输入：

```
SET AUTOCOMMIT=0;
```

如果开启了自动提交，你需要使用以下语句开始事务：

```
START TRANSACTION;
```

如果已关闭，你不需要此命令，因为当你输入 SQL 语句时会自动启动事务。

当你完成构成事务的语句输入后，只需输入以下命令即可将其提交到数据库：

```
COMMIT;
```

如果你改变了主意，可以通过输入以下命令回滚到数据库之前的状态：

```
ROLLBACK;
```

在事务提交事务之前，它对其他用户或其他会话是不可见的。

让我们来看一个例子。

打开到 books 数据库的两个连接。在其中一个连接中，向数据库添加新的订单记录：

```
INSERT INTO Orders VALUES (5, 2, 69.98, '2008-06-18');
INSERT INTO Order_Items VALUES (5, '0-672-31697-8', 1);
```

现在你可以看到新订单了：

```
SELECT * FROM Orders WHERE OrderID=5;
```

你应该能看到显示的订单：

| OrderID | CustomerID | Amount | Date |
| :--- | :--- | :--- | :--- |
| 5 | 2 | 69.98 | 2008-06-18 |

```
1 row in set (0.00 sec)
```

保持此连接开启，转到另一个连接并运行相同的 SELECT 查询。
你不应该能看到该订单：

Empty set (0.00 sec)

（如果你能看到它，很可能是你忘记关闭自动提交了。检查这一点，并确认你是否使用 InnoDB 创建了相关表。）

你看不到的原因是事务尚未提交。（这是事务隔离性作用的一个良好说明。）

现在回到第一个连接并提交事务：

```
COMMIT;
```

你现在应该可以在另一个连接中检索到该行了。

# 外键

InnoDB 也支持外键。你可能还记得我们在第 8 章“设计你的 Web 数据库”中讨论过外键的概念。

例如，考虑向 order_items 表中插入一行。你需要包含一个有效的 orderid。如果没有外键，你需要在你的应用程序逻辑中确保所插入的 orderid 的有效性。使用外键，你可以让数据库为你完成检查工作。

如何设置这种设置？正如你可能记得的，我们最初使用外键创建了表：

```
CREATE TABLE Order_Items
( OrderID UNSIGNED NOT NULL,
ISBN CHAR(13) NOT NULL,
Quantity TINYINT UNSIGNED,

PRIMARY KEY (OrderID, ISBN),
FOREIGN KEY (OrderID) REFERENCES Orders(OrderID),FOREIGN KEY (ISBN) REFERENCES Books(ISBN)
);
```

我们在 OrderID 之后添加了 `REFERENCES Orders(OrderID)`。这意味着该列是一个外键，必须包含来自 Orders 表中 OrderID 列的值。

为了测试外键约束，你可以尝试插入一个在 orders 表中没有匹配行的 OrderID：

```
INSERT INTO Order_Items VALUES (77, '0-672-31697-8', 7);
```

你应该会收到类似于下面的错误：

```
ERROR 1452 (23000): Cannot add or update a row: a foreign key constraint fails
books`.`Order_Items`, CONSTRAINT `Order_Items_ibfk_1` FOREIGN KEY (`OrderID`)
REFERENCES `Orders` (`OrderID`)
```

# 存储过程

存储过程是创建并存储在 MySQL 中的程序函数。它可以由 SQL 语句和若干特殊的控制结构组成。当你想要从不同的应用程序或平台执行相同的功能，或者作为封装功能的方式时，它是非常有用的。数据库中的存储过程可以比编程中的面向对象的方法。它们允许你控制访问数据的方式。

让我们来看一个简单的示例。

# 基础示例

列表 13.1 显示了存储过程的声明。

列表13.1 basic_stored_procedure.sql——声明存储过程

```
# 基础存储过程示例
DELIMITER //
CREATE PROCEDURE Total_Orders (OUT Total FLOAT)
BEGIN
SELECT SUM(Amount) INTO Total FROM Orders;
END
//
DELIMITER;
```

让我们逐行检查这段代码。

第一条语句：

`//` 将语句结束分隔符从当前值（通常是分号，除非你之前更改过它）改为双斜杠。你这样做是为了在输入存储过程的代码时，可以在存储过程中使用分号分隔符，而不会让 MySQL 在你之前尝试转义代码。

下一行：

```
CREATE PROCEDURE Total_Orders (OUT Total FLOAT)
```

创建实际的过程。该过程的名称是 Total_Orders。它有一个参数 Total，即你将要计算的值。`OUT` 单词表示该参数正在被输出或返回。

参数也可以声明为 `IN`，意味着一个值被传递到过程中；或者为 `INOUT`，意味着一个值被传递进来但可以被过程更改。

# 存储过程

`FLOAT` 单词表示参数的类型。在这种情况下，你返回 Orders 表中所有订单的总和。Orders 列的类型是 FLOAT，因此返回的类型也是 FLOAT。可接受的数据类型映射到可用的列类型。

如果你需要更多一个参数，可以像在 PHP 中那样返回一个逗号分隔的参数列表。

过程的主体封装在 `BEGIN` 和 `END` 语句之间。它们类似于 PHP 中的大括号 (`{}`)，因为它们界定了语句块。

在主体中，你只需运行一个 `SELECT` 语句。与正常情况的区别在于你包含了 `INTO Total`。

在事务提交事务之前，它对其他用户或其他会话是不可见的。

你使用 `RETURN` 语句返回值，就像在 PHP 中一样。

等一下，调用函数与调用过程有所不同。你可以像调用内置函数一样调用存储函数。例如，

```sql
SELECT Add_Tax(100);
```

该语句应该返回以下输出：

| Add_Tax(100) |
| :--- |
| 110 |

在定义过程和函数之后，你可以使用等命令查看定义它们的代码：

```
SHOW CREATE PROCEDURE Total_Orders;
```

列表 13.2 basic_function.sql——声明函数

```
# 创建函数的基本语法
DELIMITER //

CREATE FUNCTION Add_Tax (Price FLOAT) RETURNS FLOAT NO SQL
RETURN Price*1.1;
//
DELIMITER;
```

