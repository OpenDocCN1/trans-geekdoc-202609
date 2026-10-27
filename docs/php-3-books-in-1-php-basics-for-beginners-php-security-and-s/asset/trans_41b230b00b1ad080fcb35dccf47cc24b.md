
statement. 这与你在 SELECT 语句中定义的方式类似，其中你将多个 SELECT 语句一起列出并用逗号分隔。

如果你想查看所有客户及其客户编号按升序排列以及他们的姓名，可以使用类似这样的语句：

在运行查询之前实际查看结果的样子，可以使用一个名为 HeidiSQL 的工具。

ORDER BY 通常是第一个语句，但你可以在查询的任何位置使用它。关键字 “ORDER” 本身可以在表名之前或之后使用。ORDER BY 子句不是使用 GROUP BY 子句所必需的。

ORDER BY 关键字用于查询中，而不是 CREATE TABLE 语句中。结果是根据你指定的列进行排序的，并且在执行查询后仍保持排序，除非你随后执行一个向该表中插入或更新数据的额外查询。

## SQL Insert Into 子句

Insert Into 是一个子句，它没有结果语句，而是执行将一个表中的指定行插入到另一个表中的操作。该子句有两个部分，第一部分指定源表，第二部分指定目标表。

字段可以与目标表中的列一起插入或追加。如果某个字段未指定且存在于源表中，则它将被忽略，并且该字段不会出现在目标表中。

例如，如果源表有一个名为 A 的列包含五行数据，另一个名为 B 的列包含两行数据，并且如果我们将其插入到另一个具有三列的表中，那么在我们的 select 语句之后将不会定义任何列。

不要新建一个表并将所有数据复制到其中，使用 select 语句扩展现有表。然后将 select 语句的结果插入到现有表中。这通常比将多行插入到一个表中更容易。

如果你想向现有表添加新列，请使用此子句的 append 子句。

如果你想从现有表中删除一列，请使用此子句的 delete 子句。

insert 子句可以与 select、update 和 delete 子句结合使用，以向现有表添加新列。

要向表中插入数据，需要指定源表和目标表。源（输入）表可以是本地或全局临时表。目标表必须是基表。

## UPDATE 语句

UPDATE 语句是一个控制语句，用于更新表中指定列的值。它与 INSERT 和 DELETE 语句类似，只是它实际上不会从表中插入或删除行。UPDATE 语句一次只更改单个行中指定列包含的内容。

UPDATE 语句不能在单个 UPDATE 语句中多次更新同一列。例如，你可以使用 WHERE 子句更改所有年薪低于 10,000 美元的员工的薪水。以下语句是不合法的：

一旦在 UPDATE 语句中计算出一个表达式，就不能在同一个 UPDATE 语句中重新定义它（通过使用 SET 或新表达式）。

UPDATE 语句可以在以下两种情况之一下执行：

单个 UPDATE 语句可以更新表中的多行。这称为多行 UPDATE 语句。此类 UPDATE 语句影响的表中的行数可多达一百万；然而，存在一些限制。

在这种 UPDATE 语句中，WHERE 子句以表选择器开头，然后由用于选择要更新的单个行的键列的选择组成。此选择称为选择列表。

选择列表中的第一列始终是正在更新的表的列标识符（也称为表名或主键）。选择列表中的第二列和任何后续列被称为引用列；这些列指定要选择的单个行。

在多行 UPDATE 语句中，SELECT 语句后面跟着一个 ORDER BY 子句，该子句指定要更新的所有行的排序顺序。然后 UPDATE 语句包含一个表达式，该表达式针对正在更新的表中的每一行进行求值。这些表达式中的每一个都分配给 SELECT 列表中指定的引用列之一。如果某行满足所有这些条件，则其值将被更新；否则，保持不变。主键列的值始终会被更新。

重要提示：SELECT 和 ORDER BY 子句各自对正在更新的整个表具有隐式的 ORDER BY，因此排序基于整个表的顺序。例如，在按名字排序更新所有列的多行 UPDATE 语句中，你必须使用括号显式地强制对每个特定要更新的行进行此排序。

## DELETE 语句

在数据库中，DELETE 语句可用于从任何表或视图中删除数据。然而，当存在引用该表的外键时，你不能使用它从表中删除数据。使用 DELETE 命令时，应指定要从特定数据库表中移除的所有列。如果未指定应删除哪些列，则数据库表的所有列都将被移除。

DELETE 语句的语法如下：

```
DELETE <table_name> [WHERE <condition>] [FROM <the_starting_point>] [WITH <options>]
```

这意味着 DELETE 语句选择列并删除满足特定条件的行。

通常，你可以使用 DELETE 命令从表或视图中删除数据。

- 1: 假设你的数据库中有一个名为 Resume 的表。Resume 表有三个列名为 Emp_ID、Name 和 Current_Salary。你可以使用以下 SQL 命令删除 Emp_ID 值为 100 的 Resume 表的所有行：

```
DELETE FROM Resume WHERE Emp_ID = 100
```

- 2: 假设你想删除名为 Department 的表中 Emp_ID 值为 100 的所有行。你可以使用以下 SQL 命令删除这些行：

```
DELETE FROM Department WHERE Emp_ID = 100
```

- 3: 假设你的数据库中有一个名为 Employees 的表。Employees 表有四个列名为 Emp_ID、First_Name、Last_Name 和 Salary。假设 Employees 表中有几行你想要删除。你可以使用以下 SQL 命令删除这些行：

```
DELETE FROM Employees WHERE Emp_ID IN (SELECT Emp_ID FROM Employees WHERE First_Name = 'Chris' OR Last_Name = 'Pederson')
```

- 4: 假设你的数据库中有一个 Employees 表，其中一个列是 Project_ID。Project_ID 列对外键引用名为 Projects 的表。Projects 表中有几行，每行都有 Emp_ID 值为 100。你可以使用以下 SQL 命令删除 Employees 表中 Emp_ID 值为 100 的所有行：

```
DELETE FROM Employees WHERE Emp_ID = 100 AND Project_ID IN (SELECT DISTINCT Project_ID FROM Projects WHERE Name = 'New Products')
```

## TOP、ROWNUM、LIMIT 子句

在本节中，我们将重点关注 TOP、ROWNUM、LIMIT 子句，并查看它们的一些用途和限制。我们将从 TOP 子句开始，最后查看 LIMIT 子句。

### TOP 子句

TOP 子句有助于确保输出限制为特定值。我们将首先解释此子句，然后在转向 ROWNUM 和 LIMIT 子句之前探索其一些用途和限制。

TOP 子句用于限制从查询返回的行数。它确定 SQL 语句输出的顺序并指定返回多少行。TOP 子句可与生成行的任何子句一起使用（where、select、order by 和 group by）。

TOP 子句仅在从表中获取所有行时或当这些行不满足条件时才进行求值（例如，如果限制小于表中的总记录数）。

TOP 子句有一种不同的语法，来自 SQL-92 和 SQL:2003。所有这些形式将在下面介绍。

现在，让我们看一些示例以便练习。第一个示例将向我们展示如何将 TOP 子句与 SELECT 语句一起使用。在此示例中，如果表中超过五行，则只返回五行。

```
select * from newstaffpartition where staffid > 10 order by staffid
TOP 5 OF NEWSTAFFPARTITION WHERE STAFFID > 10 ORDER BY STAFFID
```

如果我们想要获取许多值的组合，TOP 子句可以帮助。

```
select * from newstaffpartition order by staffid, Lastname, firstname, age where staffid > 10 order by name
TOP 5 OF NEWSTAFFPARTITION ORDER BY STAFFID, LASTNAME, FIRSTNAME, AGE WHERE STAFFID > 10 ORDER BY NAME
```

将 TOP 子句与 GROUP BY 语句一起使用与将其与 SELECT 语句一起使用类似。下面示例将生成仅显示前五名员工的输出。

```
select Lastname, firstname, age from newstaffpartition
GROUP BY LASTNAME, FIRSTNAME, AGE
TOP 5 OF NEWSTAFFPARTITION GROUP BY LASTNAME, FIRSTNAME, AGE
```

也可以将 TOP 与 ORDER BY 和 LIMIT 结合使用。接下来的三个示例将展示如何获取列表中前五名人员的结果（基于雇佣日期），但仅提供按年份雇佣的最后五名人员的信息。

```
select * from newstaffpartition group by Lastname, firstname
GROUP BY LASTNAME, FIRSTNAME LIMIT 5
```

```
TOP 5 OF NEWSTAFFPARTITION GROUP BY LASTNAME, FIRSTNAME LIMIT 5
```

与之前的示例类似，你可以将 TOP 与 SELECT 和 GROUP BY 一起使用。以下两个示例展示了如何获取按姓氏的前五名员工的结果，或按雇佣日期（按姓氏）的前五名。

