

在 SQL:1999 中，创建和删除触发器的语句具有以下语法：

```
create trigger triggername
{ before | after } { insert | delete | update [ of col-list ] } on tablename
[ referencing { old | new } { row } [ as ] correlation-name |
{ old | new } table [ as ] table-alias [ , ...] ]
[ for each { row | statement } ]
[ when ( condition ) ]
triggered-SQL-statement
drop trigger triggername
```

虽然大多数 SQL 方言都支持触发器，但它们不一定符合刚才显示的创建触发器的标准语法。例如，SQL Server 目前不支持 before 触发器。

除 before 和 after 触发器外，SQL:2003 还引入了第三种触发器：instead of 触发器。顾名思义，触发器操作是代替触发事件执行的。instead of 触发器的一个重要应用是拦截对视图的修改尝试，并将其替换为对视图所基于的表（或表）的一组适当的修改。

作为示例，我们可以回到之前定义的 FemaleCompScientist 视图。

```
create view FemaleCompScientist ( empNr, name, rank ) as
select empNr, empName, grade
from Academic
where dept = 'CS' and gender = 'F'
```

请回顾，基表 Academic 包含列 (empNr, empName, dept, gender, grade)。

尝试向视图中插入新行，例如：

```
insert into FemaleCompScientist
values ( 105, 'Bird', 'L', 'Lec' )
```

这将会失败，因为我们没有 dept 和 gender 列的值；空值条目将违反视图定义。然而，我们可以使用 instead of 触发器来拦截尝试的插入，并代替在基表中进行正确的插入，如下所示：

```
create trigger AddFCS
instead of insert on FemaleCompScientist
referencing new row as Inserted
for each row
insert into Academic ( empNr, empName, grade, dept, gender )
select empNr, empName, rank, 'CS', 'F'
from Inserted
```

我们从 *新过渡变量* 的 empNr、empName 和 rank 列中获取 empNr、empName 和 grade 的适当值。我们已经从视图定义中知道，dept 和 gender 的值必须分别为 “CS” 和 “F”。这使我们能够将新行正确插入 Academic 基表。随后在视图上执行 **查询** 命令将显示插入似乎已成功，新行现在出现在视图中。

## 练习 13.4

![](img/1344db3eba3d550e6edb009556fcd95c_689_0.png)

- 1. 从 Competence 到 Technician 的外键引用通常由 **引用** 子句实现。假设省略了该子句，请使用 SQL 触发器创建等效功能以防止参照完整性违规（仅需要 **限制**）。
- 2. certificationRef 的值如果存在必须是唯一的，但某些 SQL 实现不允许唯一列中有多个空值。与其将 certificationRef 列指定为唯一，不如编写一个触发器，以确保非空值是唯一的，但允许有多个空值。
- 3. 不定时，装配体的 complexityNr 可能会上调或下调，但每次只能调整一个级别。例如，complexityNr 为 6 时，只能更改为 5 或 7。请编写一个更新触发器，以限制单次更新中对 complexityNr 的更改最多为一个级别。
- 4. 现场会生成详细说明在装配体中发现的故障的报告。这些报告存储在架构为 *报告* ( reportId, assemblyCode, reportDoc ) 的表中，其中 reportId 和 reportDoc 的数据类型分别为 **整数** 和 **大对象**。如果后来发现报告不反映真实故障，则可以删除该报告。为提高效率，我们希望在 Assembly 表中为任何有报告的装配体设置一个标志。请为 Report 表编写一个触发器，以维护 Assembly 表中的 hasReport 标志。

## 13.5 SQL: 例程

SQL 标准使用通用术语 *例程* 来描述可以从其他代码调用的代码体——这涵盖了函数、过程以及用户定义数据类型的方法。

### 用户定义函数 (UDFs)

我们先来看看函数，简单来说，它们是返回结果的代码体。

SQL 标准定义了大量内置函数，用于计算对数、生成随机数、将字符串转换为全大写或全小写等等。

它们可以在 SQL 代码中的任何合适位置使用。

定义新函数来封装可能被重复使用的代码片段也非常方便。

在 SQL 中，函数可以返回给定数据类型的标量（单个）值。

SQL:2003 标准将该概念扩展到包括返回表的函数。

创建函数的基本 SQL:2003 语法如下。

```
create function functionname ( [ parameter-list ] )
returns { data-type | table col-name data-type [,...] }
function-body
```

parameter-list 是一个（可能为空的）由参数名、参数类型对组成的逗号分隔列表。返回值的 data-types 可以是任何合法的 SQL 类型。函数体可以由任何有效的 SQL 语句组合组成，但必须包含一个 **返回** 子句，用于返回 **返回** 子句中指定类型的参数。可以使用 **删除函数** *函数名* 删除 UDF。

商业 DBMS 可能会施加其他限制。例如，在 SQL Server 中，UDF 不能使用在用相同参数多次调用函数时会产生不同结果的 SQL 语句。此类语句的示例包括获取当前时间和生成随机数。SQL Server 还禁止 UDF 中的副作用，因此，例如，函数不能用于更新基表。

以下示例展示了一个适用于 SQL Server 的标量 UDF，它接受货币金额（定义为十进制值）和货币符号作为参数，并返回一个由货币符号与金额的字符串版本拼接而成的字符串。SQL Server 使用 “+” 进行字符串拼接，而非标准的 "||"。

```
create function moneyString ( @amount decimal( 9, 2 ), @symbol char ( 1 ) )
returns varchar ( 11 )
return @symbol + cast ( @amount as varchar(10) )
```

定义后，函数通常可以在任何可以使用返回类型值的地方使用。因此，以刚才给出的示例为例，我们可以在任何合法使用 varchar(11) 值的地方调用 moneyString()。

### 存储过程

存储过程（通常简称为 “sprocs”）是从其他代码中显式调用的代码体。

在本节中，我们假设过程体是用 SQL 编写的，但过程操作也可以用其他语言（如 “C”）编写，然后从 SQL 调用。

存储过程可以（并且通常会）产生副作用，例如在执行期间更新表。

将代码封装在存储过程中的有几种潜在的好处。

**模块化。** 存储过程中的代码可以在其他代码中轻松重用。维护良好的存储过程库在开发新应用程序时是宝贵的资源。模块化还有助于确保一致性。例如，业务规则可以在存储过程中实现一次，并根据需要调用，而不是在不同地方以略有不同的方式实现相同的规则。相同的论点也适用于可维护性。如果需要更改，只需在一个地方应用。只要保持之前的接口，调用存储过程的其他程序就不需要知道所做的任何更改。

**安全性。** 存储过程的用户只能使用过程提供的功能。以这种方式限制访问极大地减少了对数据库造成损害的可能性，无论是故意的还是意外的。授予存储过程用户的权限可以与访问任何基表的权限不同，因此任何操作只能在过程上下文中执行。例如，对 “Orders” 表的所有修改都可以通过存储过程来渠道化，该过程对可进行的更改施加业务规则和其他约束，而不是授予用户对基表的直接访问权。

**性能。** 存储过程通常被编译、优化并缓存，以便在需要时使用。细节因实现而异，通常会提供对基本语法的扩展，以解决诸如在使用情况发生变化时需要重新编译和优化等问题。存储过程还可以减少网络流量：与其在应用程序中构建查询并将生成的 SQL 通过网络传输，不如只需将参数传递给存储过程。

创建和删除存储过程的基本语法如下。

```
create procedure procedurename
( [{ | in | out | inout } parmname parmtype [...] ] )
procedure-body

drop procedure procedurename
```

存储过程接受零个或多个参数。每个参数可以指定为 in（向过程提供外部值）、out（过程将其结果提供给外部）或 inout（输入参数可能由过程修改以供外部访问）。和往常一样，商业系统可能与标准语法有所不同。例如，在 SQL Server 中，存储过程的任何参数都被视为 in 参数，除非它们明确标记为 out，并且没有 inout 选项。

