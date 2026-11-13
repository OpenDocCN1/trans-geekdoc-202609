

```sql
update income, folks set
    income.salary = folks.salary * 1.1
    , folks.salary = folks.salary * 1.1
    where folks.id = income.id and income.income >= 1000000
;
```

| 编号 | 名 | 姓 | 收入 | 家属薪水 | 收入薪水 |
|---|---|---|---|---|---|
| 1 | Don | Ho | 500,000 | 50,000 | 50,000 |
| 2 | Vito | Corleone | 1,500,000 | 968,000 | 968,000 |
| 3 | Don | Juan | 250 | 50,000 | 50,000 |
| 4 | Don | Johnson | 1,250,000 | 60,500 | 60,500 |

表的更新顺序与列出的顺序一致，查询的运行效果就好像实际上是按顺序执行两次更新一样：

```sql
update income, folks set
    income.salary = folks.salary * 1.1
    where folks.id = income.id and income.income >= 1000000
;
update income, folks set
    folks.salary = folks.salary * 1.1
    where folks.id = income.id and income.income >= 1000000
;
```

将其视为两个查询来看，结果就很合理了。我们建议您一次只更新一个表，哪怕只是为了清晰起见，除非您有充分的理由这样做。

请注意，此语法不是标准的 ANSI SQL 语法。这主要关系到应用程序的可移植性；这是一个隔离实际执行更新的代码的好理由。

## delete 语句

delete 语句从表中删除一行或多行。语法如下：

```sql
delete from table_name where-clause
```

若要从表 3-1 中删除 Don Ho，请运行以下语句：

```sql
delete from folks where id=1;
```

您可以一次从一个或多个表中删除记录，删除条件可以基于这些表以及其他表中的数据（此功能从 MySQL 4.0 开始提供）：

```sql
delete from table1 [, table2 [, ...]] using table1 [, table2 [, ...]]
... [, additional_table1 [, additional_table2 [, ...]]] where
where-clause
```

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_105_0.png)

> 这是多表 delete 语句支持的几种格式之一。我们采用这种格式是因为它与单表 delete 最为相似，因此不太可能写错语法。

from 子句中列出的表是要从中删除记录的表。这些相同的表会再次出现在 using 子句中，以及您希望查询的任何其他表，以确定要删除哪些记录。

举例来说，我们可以从 folks 表中删除业绩不佳的记录。表 3-7 和 3-8 再次提供示例中使用的数据。

| 编号 | 名 | 姓 | 薪水 |
|---|---|---|---|
| 1 | Don | Ho | 25,000 |
| 2 | Don | Corleone | 800,000 |
| 3 | Don | Juan | 32,000 |
| 4 | Don | Johnson | 44,500 |

| 编号 | 收入 |
|---|---|
| 1 | 500,000 |
| 2 | 1,500,000 |
| 3 | 250 |
| 4 | 1,250,000 |

现在，我们可以使用 delete 语句删除 folks 表中收入过低的人员的记录，如以下代码所示。表 3-9 显示了结果。

```sql
delete from folks using folks, income
where folks.id = income.id and income.income < 100000
;
```

| 编号 | 名 | 姓 | 薪水 |
|---|---|---|---|
| 1 | Don | Ho | 25,000 |
| 2 | Don | Corleone | 800,000 |
| 4 | Don | Johnson | 44,500 |

## replace 语句

您在其他数据库系统中找不到 MySQL 的 replace 语句，它也不属于 SQL 标准。不过，在某些场景下它很方便。replace 语句适用于您已知主键应为何值的行。运行 replace 语句时，MySQL 会查找语句中指定主键的行。如果存在具有指定主键的行，则该行会被更新；否则，会插入新行。基本语法如下：

```sql
replace into table_name (col_1, col_2, ?) values (val_1, val_2, ?)
```

举一个 replace 派上用场的场景：假设您有一个包含两个列 email 和 full_name 的表，以 email 作为主键。如果您想编写一个脚本，让用户有机会插入和编辑这些信息，则需要某种表单供用户输入数据。然后，当用户提交表单时，脚本必须进行一些决策逻辑。如果没有 replace，逻辑大致如下：

```
examine form data
delete record from database with the submitted primary key value
    (this will run with no results if no such record exists)
run insert statement
```

但由于 MySQL 提供了 replace 语句，您可以摆脱所有这些逻辑，直接运行 replace。例如：

```sql
replace into users (email, full_name) values ('jon@doe.com', 'Jon Doe')
```

请注意，您不需要使用 where 子句来标识要替换的行；MySQL 根据主键值自行处理。（如果在没有定义主键的表上使用 replace 语句，MySQL 会向表中插入新记录。）

不过，您可以使用 where 子句来标识新数据的来源，这非常有用。假设您想更改一个表中某个字段的值，以反映针对另一个表的聚合查询结果。您无法使用 update 语句来做到这一点，因为那里不允许使用 group by 子句。但 replace 可以将 select 语句作为其来源（与 insert 类似）。如果您正在更新的表具有一个唯一键（看看它们是多么方便？），那就太棒了。

举例来说，我们在示例表集中添加了第三个表。表 3-10 记录了每位捐款人带来的捐款：

| 编号 | 金额 | 日期 |
|---|---|---|
| 1 | 5000 | 3/1/2003 |
| 1 | 5000 | 3/2/2003 |
| 1 | 5000 | 3/3/2003 |
| 2 | 25000 | 3/1/2003 |
| 2 | 3000 | 3/2/2003 |
| 2 | 4000 | 3/2/2003 |
| 2 | 10000 | 3/3/2003 |
| 3 | 1000 | 3/1/2003 |
| 3 | 3.15 | 3/2/2003 |
| 3 | 25 | 3/3/2003 |
| 4 | 10000 | 3/1/2003 |
| 4 | 20000 | 3/2/2003 |

我们希望将 income 表的 income 字段更新为每个人获得的捐款总和。与之前一样，可以先删除 income 表中的当前记录，然后创建新记录。或者，也可以直接使用 replace，如以下代码所示：

```sql
replace income (id, income)
     select id, sum(amount) from donations group by id
;
```

表 3-11 显示了结果。

## 表 3-11 收入表

| 编号 | 收入 | 薪水 |
|---|---|---|
| 1 | 15000 | NULL |
| 2 | 42000 | NULL |
| 3 | 1028.15 | NULL |
| 4 | 30000 | NULL |

请注意，我们丢失了 salary 列中的数据。问题是，我们不允许在 select 语句中包含正在替换的表。要更改某些字段并保留其他字段，我们必须创建一个临时表来存储 income 中的当前值，并在 replace 语句中将其与 donations 连接。这比 delete 加 insert 好多少是个人喜好的问题。请记住，replace 遵循与 insert 相同的语法。replace 中没有 where。

## 基本 select 语句

当需要从数据库中提取信息并在网页上展示时，您需要限制从表中返回的信息，并连接表格以获取所需信息。因此，您将从数据库（即信息的全集）开始，返回一个较小的集合。在 select 语句中，您将从一个或多个表中选择列来组装结果集。此结果将包含列和行，因此可以有效地将其视为一个表（或者，如果您的思维方式如此，也可以视为二维数组）。这个表实际上并不存在于数据库中，但以这种方式思考很有帮助。

基本 select 语句要求您指定要从中选择的表或表，以及所需的列名。如果要从给定表中选择所有列，可以用星号 (*) 替代字段名。例如：

```sql
select column_1, column_2, column_3 from table_name
```

或

```sql
select * from table_name
```

请记住，使用 select 语句时，您并未实际更改查询中涉及的表，只是在检索信息。从 PHP 中，您将通过 mysql_query() 函数将查询发送到 MySQL。

您可以选择多种方式来布局信息，但有时您需要一个简单的 HTML 表，将列名放在标题行中。清单 3-1 中的简单 PHP 代码会将任何 SQL 查询布置成一个极其简单的 HTML 表。它包含一个简单表单，允许您输入查询。如果您暂时不理解这段代码，请不要担心；第 6 章将介绍所有 PHP 函数。如果您想更改所使用的数据库，请修改 mysql_connect() 和 mysql_select_db() 函数。我不建议将此脚本放在公开可用的服务器上，因为这会造成巨大的安全漏洞。

## 清单 3-1：将 SQL 查询转换为 HTML 表的 PHP 脚本

```php
<?php
mysql_connect("localhost", "username", "password") or
die("Could not connect to database.");

mysql_select_db("test") or
die("Cannot select database");
```

