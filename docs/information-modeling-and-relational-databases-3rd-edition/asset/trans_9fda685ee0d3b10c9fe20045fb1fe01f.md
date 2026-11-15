
表 12.17 关系运算的主要定律。

| Law | Expression 1 | Operator | Expression 2 |
|---|---|---|---|
| 交换律： | A ∪ B | = | B ∪ A |
| | A ∩ B | = | B ∩ A |
| 结合律： | A ∪ (B ∪ C) | = | (A ∪ B) ∪ C |
| | A ∩ (B ∩ C) | = | (A ∩ B) ∩ C |
| | A ⋈ (B ⋈ C) | = | (A ⋈ B) ⋈ C |
| | A ⋈ (B ⋈ C) | = | (A ⋈ B) ⋈ C |
| 分配律： | A ∪ (B ∩ C) | = | (A ∪ B) ∩ (A ∪ C) |
| | A ∩ (B ∪ C) | = | (A ∩ B) ∪ (A ∩ C) |
| | (A ∪ B) 其中 c | = | A 其中 c ∪ B 其中 c |
| | (A ∩ B) 其中 c | = | A 其中 c ∩ B 其中 c |
| 如果 A、B 兼容： | (A ∪ B) [p] | = | A [p] ∪ B [p] -- 对 ∩ 不成立 |
| 导出律： | A 其中 c1 其中 c2 | = | A 其中 c1 and c2 |
| 延迟投影： | A [p] 其中 c | = | (A 其中 c) [p] |

SQL:1999 添加了用户定义类型、行类型、引用类型和数组。SQL:2003 添加了对多集（bags）作为集合类型的支持，以及 bigint 和 xml 数据类型。

SQL:2016 添加了对行模式匹配、多态表函数以及存储在字符串字段中的 JSON 数据操作的支持。SQL:2019 添加了对多维数组（MDarray 类型和运算符）的支持。

SQL:2023（https://www.iso.org/standard/76584.html）修订版添加了许多可选特性（唯一约束中的空值、字符串填充函数等）、对 JSON 的更深层支持，以及对属性图查询（SQL/PGQ）的支持。

用于查询的 SQL select 语句具有以下基本语法。

```
select [all | distinct] * | expression [[as] column-alias] [,...]
from table [[as] alias]
[. | cross join table [[as] alias]
| natural [inner | left | right | full] [outer]] join table [[as] alias]
| [inner | [left | right | full] [outer]] join table [[as] alias]
{ on condition | using (col-list) }
| union join table [[as] alias]
[,...]]
[where col-condition]
[group by colname [,...]
[having group-condition]]
[union | intersect | except ...]
[order by col [asc | desc] [,...] ]
```

select 列表选择结果列，from 子句声明源表和连接，where 子句用于筛选行，group by 子句形成行组，having 子句用于筛选组，order by 子句确定行的顺序。

子查询是外部查询内部的带括号的 select 查询。如果子查询中有引用外部查询的条件，则它是关联子查询。exists 量词后的子查询是存在性子查询。如果子查询返回一行，则 exists 条件为真，否则为假。带有嵌入式子查询的三种最常见的条件形式如下所示，其中 Θ 是比较运算符。

- expression [not] in (subquery) -- 成员子查询
- expression Θ [all | some | any] (subquery) -- [量化] 比较子查询
- exists (subquery) -- 存在性子查询

可以使用 insert、update 和 delete 语句更改表数据，其基本语法如下。

```
insert into tablename [ ( col-list ) ]
{values (constant-list) | select-query}

update tablename
set colname = expression [, ...]
[where condition]

delete from tablename
[ where condition ]
```

## 章节注释

关系代数在大多数数据库教材中都有介绍，例如 Elmasri 和 Navathe (1994)、Date (2000)。已提出算术运算符、集合函数、半连接和其他运算符来扩展关系代数，例如 Date (2000)，第 6.7 节。作为关系代数的替代方案，可以使用关系演算，例如 Date (2000)，第 7 章。Codd (1990) 提出了关系模型第 2 版，包含 333 条规则，但这并未获得显著采用。

SQL 标准由国际标准化组织（www.iso.org）发布。本书出版时，当前版本（SQL:2023）为 ISO/IEC 9075-2:2023；请参见 https://www.iso.org/standard/76584.html，并按 Preview 按钮浏览公开可用的信息性章节。有关 SQL-92 标准的清晰、详尽介绍，请参见 Date 和 Darwen (1997)；有关 SQL:1999，请参见 Melton 和 Simon (2002)。

Chamberlin 和 Boyce (1974) 描述的原始 SEQUEL 语言本身基于一种名为“SQUARE”的早期关系语言。Chamberlin (1998) 对 DB2 提供了非常易读的介绍，其中第 1.3 节勾勒了 SQL 权威的早期历史，包括解释为什么 SQL 允许基表中有重复行。

有关 SQL 中多种高级查询的可读且实用的讨论，请参见 Celko (1999, 2000, 2004, 2005) 的系列图书。Date 和 Darwen (1998) 提供了对 SQL 的深入批评以及面向对象关系数据库的替代理论基础。

有关 SQL 基础知识的最新介绍以及如何将 SQL 与不同的 DBMS（例如 Oracle、MySQL、PostgreSQL 和 SQL Server）配合使用，请参见 Taylor (2018) 和 Zhao (2021)。有关 Oracle 直到 11g 版本的全面介绍，请参见 Greenwald 等人 (2013)。

许多书籍涵盖了 SQL Server，例如 Syverson 和 Murach (2023)。SQL Server Pro Magazine（以前称为“SQL Server Magazine”）是 SQL Server 技术文章的良好来源（www.sqlmag.com）。

## 其他数据库特性

- 章节大纲
- 13.1 SQL：宏观视图
- 13.2 SQL：定义表
- 13.3 SQL：视图
- 13.4 SQL：触发器
- 13.5 SQL：例程
- 13.6 更多数据库对象
- 13.7 事务和并发
- 13.8 安全和元数据
- 13.9 摘要

### 13.1 SQL：宏观视图

在上一章中，我们查看了用于检索数据（select...）和修改数据（insert...、update...、delete...）的结构化查询语言（SQL）语句。这组语句传统上被称为数据操纵语言（DML）。我们现在将注意力转向 SQL 的其他方面。我们将查看用于定义数据库架构各种元素的语句，这些语句使用 SQL 的一个子集，传统上被称为数据定义语言（DDL）。

表当然对任何架构都至关重要，但我们还将讨论几种其他类型的数据库对象及其在实现概念架构中的作用。特别是，视图和触发器等数据库对象通常用于实现最初可能在概念级别定义的约束和派生规则。

可扩展标记语言（XML）的广泛采用主要得益于其在结构化数据交换中的应用。然而，这也产生了对关系数据和 XML 数据之间更好集成的相应需求。后一章将讨论 SQL 标准如何被调整和扩展以添加与 XML 相关的功能，以及非 SQL 数据操纵（例如 XQuery 中的操作）如何在关系框架中得到容纳。

### 13.2 SQL：定义表

#### 创建表

*基表* 的数据居住在数据库中（与我们将在稍后查看的结果表和视图不同）。在填充之前，必须先创建基表。从 SQL-92 开始，基表（以及数据库的其他方面）在使用 **创建架构** 语句创建的 *数据库架构* 范围内定义。架构可以使用 **删除架构** 语句删除。商业 SQL 通常提供创建新数据库的不同语法（例如，**创建数据库**）。

在 SQL 标准中，表使用 **创建表** 语句创建。除此之外，大多数数据库管理系统（DBMS）提供图形界面，供用户通过输入文本和选择选项来创建表。表定义的主要部分是列的列表，为每个列标识列名、其数据类型以及列中是否禁止 *空值*（即，该列是强制性的）。还可以为某些列声明约束。

**创建表** 语句的 SQL-89 语法可总结如下。在此，*字面量* 表示数值或字符串常量，*列列表* 表示由逗号分隔的一个或多个列名的列表，*唯一列列表* 表示已被集体声明为主键或唯一的列列表。如果约束适用于单个列，则可以在列定义的末尾声明。多列约束必须在表定义的末尾声明。**检查** 子句限于仅涉及表中一行的条件。

```
create table tablename (
  colname data-type [ not null ]
                [ default { literal | null | user } ]
                [ primary key | unique ]
                [ references tablename ]
                [ check (col-condition-on-same-row) ]
[,...]
[, primary key (col-list) ]
[, unique (col-list) ]
[, foreign key (col-list) references tablename [ (unique-col-list) ] [,...] ]
[, check (table-condition-on-same-row) [,...] ])
```

SQL-92 扩展了此语法。约束可以通过在其定义开头插入 **约束** *约束名称* 来命名。这有助于生成有意义的错误消息和删除约束。**检查** 子句条件可以跨越多行或多个表。一般约束可以使用 **创建断言** 声明（主要用于表间约束）。

外键约束可以包含完全/部分匹配条件和引用操作。约束可以声明为立即或延迟。受约束数据类型的宏可以使用 **创建域** 语句声明。
