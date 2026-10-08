

# 相关子查询

有一种特殊的子查询类型被称为相关子查询。在这些查询中，你可以将外部查询的条目使用到内部查询中。例如：

```sql
SELECT ISBN, Title
FROM Books
WHERE EXISTS
(SELECT * FROM Order_Items WHERE Order_Items.ISBN = Books.ISBN);
```

此查询演示了相关子查询的使用以及最后一个特殊子查询运算符 `EXISTS` 的用法。它检索所有未被订过的书籍。注意，内部查询的 `FROM` 列表中仅包含 `Order_Items` 表，但引用了 `Books.ISBN`。换句话说，内部查询引用了外部查询中的数据。这就是相关子查询的定义：你正在寻找与外部行匹配（在本例中是不匹配）的内部行。

`EXISTS` 运算符在子查询中存在任何匹配的行时返回 `true`。相反，`NOT EXISTS` 在子查询中没有匹配的行时返回 `true`。

# 行子查询

到目前为止所有的子查询返回的都是单个值，尽管在很多情况下这个值是 `true` 或 `false`（如前一个使用 `EXISTS` 的示例所示）。行子查询返回整行，并可以与外部查询中的行进行比较。这种方法通常用于查找在一个表中同时也存在另一个表中的行。在本书的数据库中没有很好的示例，但语法的通用示例可能如下：

```sql
SELECT c1, c2, c3
FROM t1
WHERE (c1, c2, c3) IN (SELECT c1, c2, c3 FROM t2);
```

# 使用子查询作为临时表

你可以在外部查询的 `FROM` 子句中使用子查询。这种方法实际上允许你查询子查询的输出，将其视为临时表。

在最形式的形式，它类似于：

```sql
SELECT *
FROM (SELECT CustomerID, Name FROM Customers WHERE City = 'Box Hill')
AS box_hill_customers;
```

注意，我们在这里将子查询放在了 `FROM` 子句中。在子查询的右括号之后，你必须为子查询的结果指定一个别名。然后你就可以将其视为外部查询中的任何其他表。

# 更新数据库中的记录

除了从数据库检索数据外，你通常还更改数据。例如，你可能想要增加数据库中书籍的价格。你可以使用 `UPDATE` 语句来实现。

`UPDATE` 语句的通常形式为：

```sql
UPDATE [LOW_PRIORITY] [IGNORE] table
SET column1=expression1,column2=expression2,...
WHERE condition
ORDER BY order_criteria
[LIMIT number]
```

基本思想是更新名为 `tableName` 的表，将每个命名列设置为相应的表达式。你可以使用 `WHERE` 子句限制 `UPDATE` 到特定的行，并使用 `LIMIT` 子句限制影响的总行数。`ORDER BY` 仅与 `LIMIT` 子句配合使用；例如，如果你只想更新前 10 行，可以先对它们进行排序。`LOW_PRIORITY` 和 `IGNORE` 如果指定，其工作方式与它们在 `INSERT` 语句中相同。

让我们来看一些示例。如果你想将书籍的价格提高 10%，可以使用不带 `WHERE` 子句的 `UPDATE` 语句：

```sql
UPDATE Books
SET Price = Price * 1.1;
```

另一方面，如果你想更改单行——例如更新客户的地址——你可以这样做：

```sql
UPDATE Customers
SET Address = '25 Olsens Road'
WHERE CustomerID = 4;
```

# 创建后修改表

除了更新行之外，你可能还会更改数据库中表的结构。实现此目的的基本形式是使用 `ALTER TABLE` 语句。

```sql
ALTER TABLE [IGNORE] tableName alteration [, alteration ...],
```

注意，在 ANSI SQL 中每个 `ALTER TABLE` 语句只能进行一种更改，但 MySQL 允许你进行尽可能多的更改。使用的每个更改都可以修改表的不同方面。

如果指定了 `IGNORE` 子句且你正尝试进行会导致主键冲突的更改，则第一条将进入修改后的表，其余的将被删除。如果没有指定（默认情况），更改将失败并回滚。

# ALTER TABLE 的可能更改

使用此语句可以进行的常见更改如表 10.5 所示。

| 语法 | 说明 |
| :--- | :--- |
| ADD [column] [AFTER location] | 在表中添加一个新列。 |
| MODIFY [column] [type] | 更改列的数据类型。 |
| CHANGE [old_name] [new_name] [type] | 重命名列并更改其类型。 |
| DROP [column] | 删除一个列。 |
| ADD [index] | 添加索引。 |
| DROP [index] | 删除索引。 |
| ADD [constraint] | 添加约束。 |
| DROP [constraint] | 删除约束。 |
| RENAME TABLE [old_name] TO [new_name] | 重命名表。 |
| ALTER TABLE [table_name] ... | 更改 修改表。 |

