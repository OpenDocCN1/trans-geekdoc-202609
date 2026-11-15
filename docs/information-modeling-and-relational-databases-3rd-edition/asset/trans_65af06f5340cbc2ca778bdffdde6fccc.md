

一行中的更多值。在 SQL 中，修改操作称为“更新”，因此该术语有时被用于此限制义。

让我们先考虑如何向表中**插入行**。为此，SQL 提供了两种基本形式的**插入**语句。第一种向表中添加一*单行数据*。其 SQL-89 语法为：

```
insert into tablename [ ( col-list ) ]
values (constant-list)
```

如果未列出列，则必须为所有列提供值。字符串必须用单引号分隔。空值可以输入为**空值**。SQL-92 引入了以下形式的**插入**语句：**插入到** *表名* **默认值**。这会添加一行，其中每个列都被赋予其默认值（可能为**空值**）。如果任何列没有默认值，则会出错。SQL:1999 增加了用于构造函数和覆盖的选项。

作为简单示例，请考虑表方案 *员工*（empNr, surname, firstname, gender, [phone], [email]）。假设一名名为“Eve Jones”的新女性员工被分配了员工编号 715。要将这些新员工详细信息添加到表中，可以使用以下任何一条命令。

```
insert into Employee
values ( 715, 'Jones', 'Eve', 'F', null, null )
```

或

```
insert into Employee ( empNr, surname, firstname, gender )
values ( 715, 'Jones', 'Eve', 'F' )
```

商业系统还提供用于从文件快速批量加载数据的命令（例如，以分隔 ASCII 格式）。用户的数据输入通常通过屏幕表单而不是直接向表格进行。由于表单或表格之间的约束，单行插入可能要求在同一事务中插入其他数据。事务是一系列 SQL 语句，由**提交**语句终止：

```
commit [work]
```

如果未提交，事务可能会被取消，即：

```
rollback [work]
```

SQL:1999 允许在事务中包含一个或多个*保存点*。然后，工作可以回滚到特定的保存点，而不是回滚整个事务。释放保存点相当于对保存点之前的事务部分进行临时提交。许多 SQL 厂商尚不支持保存点。

**插入**语句的最强大形式允许我们一次向表中插入*多行*。其基本语法为：

```
insert into tablename [ ( col-list ) ]
select-query
```

这将插入子查询返回的行集。这有许多用途，例如复制表，或临时存储连接结果以加快后续查询。例如，请考虑前面在图 12.63 中图示的软件零售商数据库。现在，假设我们想要运行许多关于数据库产品销售的查询。为此，我们可以创建一个名为“DBSales”的适当表，然后填充它，如下所示：

```
insert into DBSales
select *
from Invoice natural join LineItem natural join Item
where category = 'DB'
```

为了分析给定期间（例如，1 周）的目的，可以忽略对基础基表的更新。现在可以在 DBSales 上制定查询，而无需承受原始连接的性能开销。这种方法用于数据仓库。现在，让我们考虑如何删除行。在 SQL 中，**删除**语句用于从表中删除某些或所有行。删除后，表结构仍然存在（直到相关的 drop table 命令）。**删除**语句的基本语法为：

```
delete from tablename
[where condition]
```

基于我们的零售商数据库，这里有两个示例：

```
delete from Item -- deletes all rows from the Item table
delete from Item
where category = 'DB' -- deletes all the database item rows from Item
```

接下来，让我们考虑如何更新行（即，更改现有行中的一个或多个值）。在 SQL 中，**更新**语句用于修改行。其基本语法如下所示。在 SQL-89 中，expression 必须是标量表达式，或 null 或 default。标量表达式可以包含列名、常量和标量运算符。

```
update tablename
set colname = expression [, ...]
[where condition]
```

例如，请考虑表方案 Employee（empNr, ..., job, salary）。以下语句为所有收入低于 50,000 美元的建模人员增加 5% 的薪水：

```
update Employee
set salary = salary * 1.05
where job = 'Modeler'
and salary < 50000
```

由于 insert、delete 和 update 命令具有批量更新功能，因此拥有撤销（回滚）和安全性（例如，授予相关访问权限）的设施至关重要。

## 12.14 摘要

关系模型的数据操纵方面包括关系代数和关系赋值（:=）。除了在表达条件时使用逻辑和比较运算符外，代数还包括九个基本表操作。比较运算符优先于逻辑运算符，逻辑运算符优先于表运算符。

表 12.3 列出了运算符的六个优先级：=, <>, <, >, <=, >=; not; and; or; selection (where ...) and projection ([ ]); 最后是 union \(\cup\), intersection \(\cap\), difference \(-\)（在 SQL 中称为 except）, Cartesian product \(\times\), natural join \(\bowtie\), and division \(\div\)。可以使用括号来覆盖此顺序。左侧显示了学术期刊中常见的符号，右侧显示了我们的符号。

```
\sigma_c(T) \equiv T \text{ where } c
\pi_{a,b,...}(T) \equiv T [a,b,...]
A \bowtie_c B \equiv (A \times B) \text{ where } c
```

同一优先级别的运算符是左结合的（按它们在表达式中出现的顺序从左到右求值）。我们的优先级约定旨在最大限度地减少括号的使用，并且比一些其他通用约定更强。如果有疑问，或者纯粹为了清晰起见，请随意添加额外的括号。

关系 DBMS 以关系表作为其唯一的基本数据结构，并支持关系选择、投影和连接，而无需指定访问路径。

表运算符在图 12.64 中以可视方式总结。选择、投影和连接存在许多不同的符号。

比较和逻辑运算符的规律是众所周知的。表 12.17 列出了表运算符的大部分主要规律。其中一些尚未讨论；它们的证明留作简单练习。这里 \(A, B\), 和 \(C\) 是表，\(c\) 是条件，\(p\) 是属性投影列表。

可以陈述各种其他分配律；但是请记住，\([\) 不分配给 \(\cap\) 或 \(-\)。

SQL 是关系 DBMS 中使用的主导语言，多年来已标准化了各种版本，最新的是 SQL:2023。大多数商业 SQL 方言支持所有 SQL-89、SQL-92 和 SQL:1999 中的一些附加功能，以及他们自己的一些特殊功能。

诸如表和列之类的数据库对象可以使用标准标识符或分隔标识符（允许双引号内的任何字符）命名。数据库字段可以根据预定义的数据类型（例如，varchar(20)）定义。

### 并集

![](img/1344db3eba3d550e6edb009556fcd95c_667_0.png)

$A \cup B$

### 交集

![](img/1344db3eba3d550e6edb009556fcd95c_667_1.png)

$A \cap B$

### 差集

![](img/1344db3eba3d550e6edb009556fcd95c_667_2.png)

$A - B$

### 笛卡尔积

| 1 | 2 | 3 |
|---|---|---|
|   |   |   |

×

|   |   |
|---|---|
|   |   |

=

| 1 |   |
|---|---|
| 1 |   |
| 2 |   |
| 2 |   |
| 3 |   |
| 3 |   |

### 选择

![](img/1344db3eba3d550e6edb009556fcd95c_667_3.png)

$T \text{ where } c$

### 投影

![](img/1344db3eba3d550e6edb009556fcd95c_667_4.png)

$T [a, b]$

| a |   | A |
|---|---|---|
| 1 |   | A |
| 1 |   | B |
| 2 |   | C |
| 2 |   | A |
| 3 |   | B |

### 自然连接

|   | 1 |   |   |
|---|---|---|---|
|   | 2 |   |   |
|   | 3 |   |   |
|   | 1 |   |   |
|   | 2 |   |   |
|   |   |   |   |

### 除法

图 12.64 关系代数的八个基本表操作。

