

SQL 提供 GRANT 语句，用于向用户授予各种权限。SQL-92 语法如下：

```
grant all privileges |
select | insert [ ( col ) ] | update [ ( col ) ] | delete | usage | references [ ( col ) ] [...]
on object
to user-list [ with grant option ]
```

其中 object 可以是 [table] tablename、domain domainname 等。用户列表可以包含 public，即所有用户。SQL:1999 扩展了该语句，以支持“角色”（用户组）。如果包含 with grant option，则用户列表有权将相同的权限授予其他用户。例如，以下语句授予所有用户对 Stock 表的读取访问权限：grant select on Stock to public。以下语句授予授权 ID 为 "Mgr" 的用户对 Stock 表的读取权限，以及更新 price 列中值的权限：grant select, update(price) on Stock to Mgr。可以使用 REVOKE 语句删除权限：

```
revoke [ grant option for ] privilege-list
on object
from user-list [ restrict | cascade ]
```

例如，要撤销先前授予的更新权限，请使用 revoke update( price ) on Stock from Mgr。GRANT 或 REVOKE 语句中的表名可以是基本表或视图的名称。授予对视图的访问权限而不授予对基本表的访问权限，是强制安全性的一种便捷方式。RESTRICT 和 CASCADE 选项尚未得到广泛支持。

除数据库权限外，商业系统还提供对与数据库服务器及 DBMS 实例相关的操作的控制。一个服务器可能包含多个实例，一个实例可能支持多个单独的数据库。通常，角色按层级排列，层级较低的角色拥有的权限少于层级较高的角色。例如，较低级别的管理员可以执行维护和实用程序操作，但无法访问数据库中存储的数据。

现在，让我们转到元数据（关于数据的数据）。SQL 系统会自动维护一组系统表，其中包含关于数据库架构本身（例如，基本表、视图、域、约束和权限）的信息。在商业 DBMS 中，此类表通常被统称为“系统目录”等名称。SQL-92 在不同的意义上使用“目录”一词（用于指环境中的架构集合）。商业系统的系统表还包括优化器使用的物理信息（例如，关于索引的信息）。拥有系统表访问权限的用户可以使用 SQL 查询这些表（就像查询应用表一样）。

自 SQL-92 起，SQL 标准在名为 DEFINITION_SCHEMA 的特殊架构中，使用表和断言来定义元数据。这为元数据提供了参考模型，但并无意在任何商业实现中以这种方式实现——实现模拟其存在即可。

元数据的预期访问方式是通过在另一个名为 INFORMATION_SCHEMA 的架构中定义的 _视图_。INFORMATION_SCHEMA 中的视图是根据 DEFINITION_SCHEMA 中的模型定义的。大多数视图都定义了授予给 **public** 的 **select** 权限，但未授予其他权限，因此这些视图不可更新。随着标准后续版本中添加了触发器等新功能，这些架构也得到了扩展。

为符合标准，DBMS 应该支持这些视图，许多流行的 DBMS 至少正在努力这样做。商业系统可能仍然使用其自身的特定名称（例如，SysTables、SysCatalog 等）和结构来存储元数据。这些通常提供与标准架构等效的功能，但在详细语法上有一些差异。

作为一个简单示例，以下查询使用标准 Columns 视图来请求 Customer 表中的列数：

```
select count ( * ) from Columns
where table_name = 'CUSTOMER'
```

为了了解商业系统之间可能存在的差异，SQL Server 中的等效查询可能如下所示：

```
select count ( * ) from sys.Columns
where object_id = object_id ( 'CUSTOMER', 'U' )
```

而在 DB2 中我们可能会看到：

```
select count ( * ) from sysibm.Columns
where table_name = 'CUSTOMER'
```

## 13.9 总结

基本表架构可以使用 *create-table 语句* 来定义，其主要语法如下：

```
create table tablename (
  colname data-type   [ not null ]
                              [ default literal | null | user ]
                              [ primary key | unique ]
                              [ references tablename ]
                              [ check (col-condition-on-same-row) ]

      [...]
      [, primary key ( col-list ) ]
      [, unique ( col-list ) ]
      [, foreign key ( col-list ) references tablename [ ( unique-col-list ) ] [...] ]
      [, check (table-condition-on-same-row) [...] ] )
```

除了通过定义来创建表（如刚才所示）之外，表还可以使用 **like** 根据另一个表创建，或使用 **as** 作为 select 查询的结果创建。还存在用于更改和删除表等任务的其他 SQL 语句，其他类型的数据库对象也有等效的 alter 或 drop 语句。

视图可以使用 create-view 语句创建，语法如下：

```
create view viewname [ ( col-list ) ] as
      select-query
[ with check option ]
```

视图定义用于将对视图的查询转换为对基本表的等效查询。有些视图不可更新（例如，涉及连接的视图）。

触发器用于响应给定表或视图上下文中的特定事件。当检测到指定事件时，将执行触发器中的代码体。触发器可以检查导致事件的数据，以确定适当的操作方案。创建触发器的基本语法如下：

```
create trigger triggername
  { before | after } { insert | delete | update [ of col-list ] on tablename
  [ referencing { old | new } [row] [ as ] correlation-name |
        { old | new } table [ as ] table-alias [, ...] ]
  [ for each { row | statement } ]
    [ when ( condition ) ]
  triggered-SQL-statement
```

例程是显式调用的代码体，与本质上是事件驱动的触发器不同。UDF 返回标量或表结果。创建函数的基本语法如下：

```
create function functionname ( [ parameter-list ] )
      returns { data-type | table col-name data-type [...] }
      function-body
```

存储过程能够执行比函数更广泛的活动（例如更新表），并且是封装 SQL 代码的标准方式。存储过程通常用于将数据库与可能造成损害的用户操作“隔离”。创建存储过程的基本语法如下：

```
create procedure procedurename
      ( [ { in | out | inout } parmname parmtype [...] ] )
      procedure-body
```

数据库架构可以包含其他类型的对象。序列用于自动生成唯一标识符。索引可用于提高查询性能。游标可用于提供逐行处理。

实际数据库系统包括处理并发的措施，通常基于选择性锁定资源以避免事务之间的干扰。更高隔离性和更高吞吐量之间的首选位置可以在语句级别或连接级别指定。

数据库安全性围绕两个主要概念展开。用户根据指定的凭据进行身份验证，以确认其身份。权限——执行某些类型操作的权利——可以授予特定个人或组，也可以从中撤销。

元数据——关于数据库系统本身的信息——存储在各种表中，以供系统内部使用。也可以查询这些信息，尽管标准做法是不鼓励直接访问这些表，而是使用系统视图。

本章结束了对现代关系数据库系统主要特性的基础介绍。SQL 的其他一些方面在书中其他章节的相关主题背景下进行了探讨。更高级的 SQL 方面包含在在线附录 C 中，章节笔记提供了更多细节。虽然了解相关的 SQL 标准提供了良好的基础，但学习这门语言最简单的方法是通过使用它，这需要发现所选 SQL 方言与标准之间的差异。幸运的是，大多数商业 DBMS 都提供广泛的在线资源，可协助你在这方面的学习。

## 章节笔记

SQL 标准已被国际标准化组织（ISO）采纳为 ISO/IEC 9075。本书出版时，当前版本（SQL:2023）为 ISO/IEC 9075-2:2023；请参见 https://www.iso.org/standard/76584.html，并按“预览”按钮获取更多详细信息。由于标准体积庞大（总共数千页），因此被拆分为多个部分。第 2 部分（基础）与本章最相关。

大多数商业数据库系统使用的 SQL 语法往往与 SQL 标准语法有些许不同。有关使用 Oracle、MySQL、PostgreSQL 和 SQL Server 等不同 DBMS 的 SQL 的最新介绍，请参见 Taylor (2018) 和 Zhao (2021)。许多书籍都介绍了 SQL Server，例如 Syverson 和 Murach (2023)。SQL Server Pro Magazine 是有关 SQL Server 技术文章的良好来源（www.sqlmag.com）。大多数商业系统都提供可以多种方式搜索的在线帮助。

