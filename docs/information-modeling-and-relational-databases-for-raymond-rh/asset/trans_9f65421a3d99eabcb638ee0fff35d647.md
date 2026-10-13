
由于 `cte-query-definition` 返回不同的列，因此不需要 `col-list`。紧随 `with` 子句之后的 `query-statement` 使用 `cte-query-definition` 的结果，引用 `cte-name`。任何其他查询试图引用此 CTE 都会失败，这与视图定义不同。这种结构在 SQL 中还有其他用途，但我们这里关注的是它在形成递归查询中所起的作用。递归查询的锚定部分可以涉及多个子查询，其结果使用标准 SQL 集合操作（`union`、`intersect` 和 `except`）进行组合，但为简单起见，我们这里假设只有一个查询。

锚定结果形成后，递归的结果将使用 SQL 的 `union all` 操作添加。在每个阶段，查询的递归部分将累积结果作为输入，运行查询，并将结果添加到结果集中。这将持续到不再产生新结果为止。通常，当层次结构中不再有未探索的节点时，就会发生这种情况。

递归 CTE 的框架如下所示：

```
with cte-name [ (col-list) ] as anchor-query-definition
```

```
union all
```

```
   recursive-query-definition
```

```
   query-statement
```

为了使其更具体，我们将看一个简单的示例。[图 12.63](#Ch012_539-646_B9780443237904000268_2.xhtml#f0320) 显示了一个表的模式，该表保存组织中部门的层次结构信息，以及示例数据填充。

![图 12.63 (a) 表模式和数据 (b) 部门层次结构。](images/B9780443237904000268/f12-63-9780443237904.jpg)

[图 12.63](#Ch012_539-646_B9780443237904000268_2.xhtml#B-f0320) (a) 表模式和数据 (b) 部门层次结构。

如 [图 12.63](#Ch012_539-646_B9780443237904000268_2.xhtml#f0320)(b) 所示，该组织有三个部门层级。我们可能想要编写各种查询来利用层次结构中固有的父子关系，而递归查询是实现这一目标的自然方式。鉴于 [图 12.63](#Ch012_539-646_B9780443237904000268_2.xhtml#f0320) 中场景的简单性，使用递归查询可能显得大材小用，但我们可以轻松演示其基本特性。

我们将从一个简单的逐层部门列表开始，以说明结果是如何产生的。查询如下：

```
with myCTE (deptId, deptName, parentDept, “level”) as ( select anchor.deptId, anchor.deptName, anchor.parentDept, 1 as “level”from Dept as anchorwhere parentDept is nullunion allselect child.deptId, child.deptName, child.parentDept, “level” + 1from Dept as child join myCTE as parenton child.parentDept = parent.deptId )select deptId, deptName, “level” from myCTE
```

执行后，查询产生以下结果：

| ![u12-33-9780443237904](images/B9780443237904000268/u12-33-9780443237904.jpg) |

| --- |

此处，“level”列表示层次结构中的相对深度，以 1 为顶层（“level”此处是分隔标识符，因为它是 SQL 中的保留关键字）。

我们通过指定 `where` parentDept `is null` 将顶层作为锚定，因此锚定元组为 \<101, ‘Management’, null, 1\>。在下一层，我们现在查找 `deptId` 为 101 的部门。`union all` 操作添加元组 \<201, ‘Sales’, 101, 2\> 和 \<202, ‘Production’, 101, 2\>。

CTE 递归部分中的 `join` 现在可以添加 Sales 下的部门。Production 没有子部门，因此 `join` 不产生结果。添加完 Sales 的三个子部门后，`join` 没有其他可能性（因为没有部门的父级 `deptId` 为 301、302 或 303），因此递归结束。

执行 CTE 后的 `select` 语句时，它会为 `myCTE` 创建结果集，然后应用其自身的查询，在本例中仅提取递归 CTE 产生的三列。

当然，最终结果取决于作用于 CTE 结果的查询，并且不必列出 CTE 的所有行。

例如，以下递归查询查找层次结构中特定节点下的员工总数——同样，我们采用了顶层节点，但只需对定义锚定的查询进行简单更改，就可以采用层次结构中的任意节点。

```
with myCTE (deptId, totalStaff, parentDept) as
```

```
   (     select anchor.deptId, anchor.totalStaff, anchor.parentDept
```

```
from Dept as anchor
```

```
where parentDept is null
```

```
union all
```

```
select child.deptId, child.totalStaff, child.parentDept
```

```
from Dept as child join myCTE as parent
```

```
on child.parentDept = parent.deptId
```

```
   )
```

```
select sum(totalStaff) as totalStaff from myCTE
```

这将产生预期结果：

![](images/B9780443237904000268/u12-25-9780443237904.jpg)

显然，我们本可以使用简单得多的查询来产生这个特定结果，但总体而言，递归允许我们构建针对层次结构的查询，而用其他方式很难（或笨拙地）实现。大多数商业 SQL 方言都支持 CTE 和递归，但细节可能与我们在此概述的不同。

## 12.13 SQL：更新表填充

一般来说，数据库表填充的“更新”可能涉及三种关系操作中的任意一种：向表中插入一行、从表中删除一行，或修改一行上的一个或多个值。在 SQL 中，修改操作称为“update”，因此该术语有时用于这种受限含义。

让我们首先考虑如何向表中 `insert rows`。为此，SQL 提供了两种基本形式的 `insert` 语句。第一种向表添加*单行数据*。其 SQL-89 语法为：

```
insert into tablename [ (col-list ) ]
```

```
values (constant-list )
```

如果未列出列，则必须提供所有列的值。字符串必须用单引号分隔。空值可作为 `null` 输入。SQL-92 引入了 `insert` 语句的以下形式：`insert into` *tablename* `default values`。这将添加一行，其中每列均赋予其默认值（可能为 `null`）。如果任何列没有默认值，则会导致错误。SQL:1999 增加了使用构造函数和覆盖的选项。

作为一个简单示例，考虑表模式 `Employee` ( empNr, surname, firstname, gender, \[phone\], \[email\])。假设一名名为“Eve Jones”的新女员工被分配了员工编号 715。要将这位新员工的详细信息添加到表中，可以使用以下任一命令。

```
insert into Employee
```

```
values ( 715, ‘Jones’, ‘Eve’, ‘F’, null, null )
```

或

```
insert into Employee ( empNr, surname, firstname, gender )
```

```
values ( 715, ‘Jones’, ‘Eve’, ‘F’ )
```

商业系统还提供从文件快速批量加载数据的命令（例如，采用分隔符分隔的 ASCII 格式）。用户的数据录入通常通过屏幕表单进行，而不是直接录入表中。由于表单上的约束或表间约束，单行插入可能要求在同一事务中插入其他数据。事务是一系列 SQL 语句，由 `commit` 语句终止：

```
commit [work]
```

如果未提交，事务可被取消，如下所示：

```
rollback [work]
```

SQL:1999 允许在事务中包含一个或多个*保存点*。然后可以将工作回滚到特定保存点，而不是回滚整个事务。释放保存点的作用类似于对保存点之前的事务部分进行暂时提交。许多 SQL 供应商尚不支持保存点。
