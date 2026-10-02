
你希望对 (username, state, age) 建立一个覆盖索引，而不是对每个列单独建立索引。现在，如果你的查询是：

```
SELECT * FROM geeks WHERE state = 'CA';
```

该查询将无法利用多列索引，因为你在 WHERE 中指定的列是第二个指定的列（这称为键部分）。在这种情况下，如果这两个查询是最常用的查询，你希望覆盖索引先指定 state（state, username, age）。规则是：要使用覆盖索引，覆盖索引中指定的第一个列是你可以在 WHERE 子句中单独指定的唯一列，并且必须包含在 WHERE 子句中指定另外两个索引，以便这些索引能被多列索引覆盖。下面的 EXPLAIN 列表强调了这一概念。在第一个示例中，所有列都列在 WHERE 子句中，并且使用了覆盖索引 age_state_name：

```
explain select *
from users
where name = 'Chaintanya Mahaprabhu'
and age = 28
and state = 'HI'\G
*************************** 1. row ***************************
        id: 1
    select_type: SIMPLE
        table: users
           type: ref
possible_keys: age_state_name
          key: age_state_name
        key_len: 50
           ref: const,const,const
          rows: 1
        Extra: Using where
```

接下来，仅使用了 name_state_age 索引的第一个列，导致索引被使用：

```
explain select * from users where name = 'Chaintanya Mahaprabhu'\G
*************************** 1. row ***************************
        id: 1
    select_type: SIMPLE
        table: users
           type: ref
possible_keys: age_state_name
          key: age_state_name
        key_len: 42
           ref: const
          rows: 1
        Extra: Using where
1 row in set (0.00 sec)
```

仅在 WHERE 子句中指定了 age 和 state 列，但索引未被使用：

```
mysql> explain select * from users where age = 28 and state = 'HI'\G
*************************** 1. row ***************************
        id: 1
    select_type: SIMPLE
table: users
type: ALL
possible_keys: NULL
key: NULL
key_len: NULL
ref: NULL
rows: 8
Extra: Using where
```

在这种情况下，你希望再创建一个覆盖索引，但仅针对 (age, state)。因此， whenever in doubt, use EXPLAIN。

## 其他命令

本章不会详细介绍 SHOW PROFILE 命令；然而它也可以成为查询分析的有价值且精细的工具。它可以按 MySQL 内核中的各个组件显示 SQL 语句的微秒级分解，并可以提供一些有关在哪里调整查询的提示。要使用分析，只需使用以下语句将 profiling 设置为 true 即可：

```
mysql> set profiling=1;
```

以下代码显示了执行查询的内部操作的分解：

```
SELECT user,host,password FROM mysql.user;
SHOW PROFILE;
```

| 状态 | 持续时间 |
|---|---|
| 启动 | 0.000078 |
| 打开表 | 0.000015 |
| 系统锁 | 0.000007 |
| 表锁 | 0.000008 |
| 初始化 | 0.000031 |
| 优化 | 0.000016 |
| 统计 | 0.000062 |
| 准备 | 0.000018 |
| 执行 | 0.000005 |
| 发送数据 | 0.000075 |
| 结束 | 0.000006 |
| 查询结束 | 0.000004 |
| 释放项目 | 0.000031 |
| 记录慢查询 | 0.000004 |
| 清理 | 0.000005 |

对于熟悉源代码的开发者，SOURCE 选项甚至提供源文件和行号，以便你可以深入 MySQL 源代码（如果可用）来审查代码。如果你将 SOURCE 添加到之前的查询，可以看到特定操作源自哪个源文件和行：

```
SELECT user,host,password FROM mysql.user;
SHOW PROFILE SOURCE\G
```

```
**************************** 1. row *******************************
        Status: starting
        Duration: 0.000078
Source_function: NULL
        Source_file: NULL
        Source_line: NULL
**************************** 2. row *******************************
        Status: Opening tables
        Duration: 0.000015
Source_function: open_tables
        Source_file: sql_base.cc
        Source_line: 4501
**************************** 3. row *******************************
        Status: System lock
        Duration: 0.000007
Source_function: mysql_lock_tables
        Source_file: lock.cc
        Source_line: 258
...
```

在此示例中，使用 \G 结尾是因为输出中有太多列，这样查看更方便，并且在查询上添加了 LIMIT 3 以节省几棵树！你可以通过简单地使用包含与 SHOW 命令完全相同数据的 INFORMATION_SCHEMA.PROFILING 表来更具选择性地显示想要的列：

```
select state, source_file, source_line, duration
from information_schema.profiling
limit 1;
```

| 状态 | 源文件 | 源行号 | 持续时间 |
|---|---|---|---|
| 启动 | NULL | NULL | 0.000078 |
| 打开表 | sql_base.cc | 4501 | 0.000015 |
| 系统锁 | lock.cc | 258 | 0.000007 |
| 表锁 | lock.cc | 269 | 0.000008 |
| 初始化 | sql_select.cc | 2386 | 0.000031 |
| 优化 | sql_select.cc | 781 | 0.000016 |
| 统计 | sql_select.cc | 963 | 0.000062 |
| 准备 | sql_select.cc | 973 | 0.000018 |
| 执行 | sql_select.cc | 1657 | 0.000005 |
| 发送数据 | sql_select.cc | 2226 | 0.000075 |
| 结束 | sql_select.cc | 2431 | 0.000006 |
| 查询结束 | sql_parse.cc | 4915 | 0.000004 |
| 释放项目 | sql_parse.cc | 5942 | 0.000031 |
| 记录慢查询 | sql_parse.cc | 1648 | 0.000004 |
| 清理 | sql_parse.cc | 1615 | 0.000005 |

通过使用 INFORMATION_SCHEMA 的查询，你可以以任何排列显示信息，而使用 SHOW 命令则限制为固定格式。

## 优化 UPDATE

要优化 UPDATE，请查看 WHERE 子句。如果使用的是 PRIMARY KEY，则无需进一步分析。如果不是，将 UPDATE 语句重写为 SELECT 语句并获取 QEP 如前所述，以确保使用最佳索引是有益的。例如：

```
UPDATE t
SET    c1 = 'x',
       c2 = 'y',
       c3 = 100
WHERE  c1 = 'x'
AND    d = CURDATE()
```

你可以将此 UPDATE 语句重写为 SELECT 语句以使用 EXPLAIN：

```
EXPLAIN
SELECT c1, c2, c3
FROM   t
WHERE  c1 = 'x'
AND    d = CURDATE()
```

现在你应应用在优化 SELECT 语句中详细说明的相同原则。

## 优化 DELETE

你应参考“优化 UPDATE”部分并应用相同的原则来优化 DELETE 语句。下一个示例显示了一个常见的删除查询，该查询运行在与父表有关的子表上，其中存在“孤立”记录——这意味着子表中存在一些没有对应父记录的记录。

例如，如果你有一个包含四个父记录的父表：

```
mysql> select * from parent;
```

| ID | 名称 |
|---|---|
| 1 | parentA |
| 2 | parentB |
| 3 | parentC |
| 4 | parentD |

并且子表中有一些孤立记录（那些 parent_id 值在父表中不存在的记录）：

```
mysql> select * from child;
```

| 父 ID | 子 ID |
|---|---|
| 1 | 1 |
| 2 | 2 |
| 3 | 3 |
| 1 | 4 |
| 1 | 5 |
| 2 | 6 |
| 0 | 7 |
| 0 | 8 |
| 10 | 9 |
| 5 | 10 |

删除这些孤立记录的一种常见方法是使用子查询在 DELETE 语句中使用：

```
delete from child where parent_id not in (select id from parent);
Query OK, 4 rows affected (0.00 sec)
```

但更有效的方法是使用 join，因为它避免了子查询，而子查询是删除必须内部执行的一个额外查询，以获取 parent_id 值的列表，从而找到哪些子记录没有匹配项。你可以在实际运行删除语句之前通过使用 join 查询来测试这个想法。此查询获取孤立记录的列表以验证你想要删除的内容。以下代码显示了如何使用 profiling，它利用了 join 并导致更快的执行和更少的内部操作：

```
set profiling = 1;
select *
from child
where parent_id not in (select id from parent);
```

| 父 ID | 子 ID |
|---|---|
| 0 | 7 |
| 0 | 8 |
| 10 | 9 |
| 5 | 10 |

```
select parent_id, child_id
from child
left join parent on (parent.id = child.parent_id)
where parent.id is NULL;
```

| 父 ID | 子 ID |
|---|---|
| 0 | 7 |
| 0 | 8 |
| 10 | 9 |
| 5 | 10 |

```
select query_id,count(*) as '# ops', sum(duration)
from information_schema.profiling
group by query_id;
```

| 查询 ID | 操作数 | 持续时间总和 |
|---|---|---|
| 1 | 18 | 0.000725 |
| 2 | 15 | 0.000535 |
