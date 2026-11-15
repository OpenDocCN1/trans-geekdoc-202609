

## 表 12.6 关系代数与 SQL 的等价表述

| 关系代数 | SQL |
|---|---|
| T where c | select * from T where c |
| T where c [a, b, ...] | select distinct a, b, ... from T where c |

![](img/1344db3eba3d550e6edb009556fcd95c_601_0.png)

## 图 12.34 WHERE 子句用于仅选择水瓶座。

请注意，字符串“Aquarius”包含大写和小写字符的混合。假设这是表中存储的方式，但查询中 starsign 被输入为大写，即，

```
select * from Person
where starsign = 'AQUARIUS'
```

除非系统已配置为在比较之前将字符串转换为相同大小写，否则不会匹配，因为字符串“AQUARIUS”不同于“Aquarius”。要在 SQL-92 及以后版本中使字符串比较不区分大小写，要么声明按此方式操作的排序规则，要么使用字符串函数转换大小写。例如，给定字符串表达式 s，折叠函数 upper(s) 和 lower(s) 分别返回 s 的大写和小写版本。因此，以下查询将检索水瓶座，而不管列条目中“Aquarius”字母使用何种大小写：

```
select * from Person
where upper(starsign) = 'AQUARIUS'
```

尽管许多商业 SQL 方言（如 SQL Server）支持标准的 upper 和 lower 字符串函数，但某些方言提供了其他控制字符串常量大小写敏感性的方法。

图 12.35 中的示例说明了三个新功能。表方案 Actor (surname, firstname, gender) 的示例数据包括姓氏“D’Abot”，其中包含单引号作为字符之一。如前所述，字符串常量由单引号分隔。要在这种字符串中嵌入单引号，我们需要告知 SQL 该引号是字符串的一部分而非结束符。为此，我们使用两个相邻的单引号来表示嵌入的单引号。

| surname | firstName | gender |
|---|---|---|
| Bardot | Brigitte | F |
| D'Abot | Maryam | F |
| D'Abot | Tony | M |

```
select *, 'This isn''t hard' as comment
from Actor
where surname = 'D''Abot'
```

| surname | firstName | gender | comment |
|---|---|---|---|
| D'Abot | Maryam | F | This isn't hard |
| D'Abot | Tony | M | This isn't hard |

## 图 12.35 两个单引号嵌入一个单引号，而“as”引入别名。

以下 **插入** 语句可用于向表中添加第二行数据：**insert into Actor values ('D''Abot', 'Maryam', 'F')**。请注意，这在“D’Abot”中使用了两个单引号。虽然查询时可能仅显示为“D’Abot”，但在 SQL 语句中使用该值时必须使用两个单引号。例如，请注意搜索条件：surname = 'D''Abot'。

关于该查询需要注意的第二点是，*我们可以将常量作为 select 项包含在内*。此处 **select** 列表包含字符串常量“This isn’t hard”。请再次注意使用两个单引号来嵌入单引号。作为 **select** 列表中项包含的任何常量都将包含在查询返回的每一行中。在我们的示例中，返回了两行。

该示例说明的第三个方面是，关键字“as”*可用于为 **select** 项引入别名*。此别名将在结果表中作为该项的列名出现。该示例为添加到 **select** 列表中的字符串常量引入了别名“comment”。在实践中，**select** 项的别名主要用于为更复杂的表达式提供简单名称，如前所述。

搜索条件可包括项、比较运算符（=、<>、<、>、<=、>=）和逻辑运算符（**not**、**and**、**or**）。某些 SQL 方言允许使用除“<>”以外的符号表示“不等于”（例如，“~=”、“!=”）。SQL Server 还包含“!<”表示“不小于”和“!>”表示“不大于”，它们分别等价于“>=”和“<=”。出于可移植性考虑，应避免此类非标准符号。采用与关系代数相同的优先级约定。因此，除非括号另有规定，*比较运算符在逻辑运算符之前求值*，逻辑运算符按 **not**、然后 **and**、最后 **or** 的顺序求值。

请考虑图 12.36 中的查询。它列出了 1950 年以后出生且为水瓶座或双子座的人的姓名和星座。如果省略了括号，条件将被解释为 starsign = 'Aquarius' **or** (starsign = 'Gemini' **and** birthyr > 1950)。这有所不同，因为这也会列出年长的水瓶座（在此例中为 Terry）。

如果存在空值，选择操作会变得稍微复杂一些。请考虑关系方案 **Employee** (<u>empNr</u>, empName, dept, [carType])。在此，carType 列是可选的。有些员工可能不开车，即使开车，也许也没有记录。图 12.37 为此表提供了示例数据以及两个查询及其结果。假设我们想知道谁开福特汽车，谁不开。我们可以将这些问题表述为图 12.37 中的查询。尽管在现实中，每个员工要么开福特汽车，要么不开，但员工 1002 和 1005 却不出现在任何查询结果中。你能明白这是为什么吗？

```
select firstname, starsign
from Person
where (starsign = 'Aquarius' or starsign = 'Gemini')
and birthyr > 1950
```

| firstname | starsign |
|---|---|
| Bob | Gemini |
| Eve | Aquarius |
| Fred | Gemini |

## 图 12.36 需要括号才能在 and 之前求 or。

员工表：

| empNr | empName | dept | carType |
|---|---|---|---|
| 1001 | Thompson, E. | Sales | Ford |
| 1002 | Jones, E. | Sales | ? |
| 1003 | Smith, F. | R&D | Toyota |
| 1004 | Adams, A. | Sales | Ford |
| 1005 | Dennis, A. | Admin | ? |

(a)

```
select empNr, empName
from Employee
where carType = 'Ford'
```

| empNr | empName |
|---|---|
| 1001 | Thompson, E. |
| 1004 | Adams, A. |

(b)

```
select empNr, empName
from Employee
where carType <> 'Ford'
```

| empNr | empName |
|---|---|
| 1003 | Smith, F. |

## 图 12.37 当条件为真时选择行（而非假或未知）。

就空值而言，SQL 基于三值逻辑运算。条件的求值结果可能为 true、false 或 unknown。更准确地说，条件是已知为真、已知为假或未知。当比较项中包含空值时，任何比较运算符（=、<>、< 等）的求值结果均为 unknown。请考虑员工 1002 的行，其中 carType 记录了一个空值（此处显示为“？”）。对于图 12.37(a) 中的查询，条件为“null = Ford”；对于图 12.37(b) 中的查询，条件为“null <> Ford”。在这两种情况下，条件的求值结果均为 unknown。

WHERE 子句执行的选择操作仅返回求值为 true（即已知为真）的行。求值为 false 或 unknown 的行会被过滤掉。因此，在两个查询中都会过滤掉员工 1002 和 1005（Jones 和 Dennis）的行。过滤掉未知值有助于避免不必要的假设。如前所述，SQL 提供了一个用于检测空值的特殊函数。

现在，让我们讨论如何控制结果表中列和行的顺序。列按其在 select 列表中出现的顺序显示。因此，如果需要不同的列顺序，只需重新排列 select 列表即可。但是，行的显示顺序可以通过 **order by** 子句来控制。如果使用，**order by** 子句必须位于 **select** 语句的末尾。**select** 列表中的一个或多个列（按名称或在 **select** 列表中的位置标识）可用作排序条件。

对某一条件的排序默认为升序。您也可以通过向列标识符追加 **asc** 来显式指定升序。要指定降序，必须追加 **desc**。对于数值，“升序”意味着较小的数字排在前面。例如，1 < 3 < 7，因此 1、3、7 为升序。对于字符串值，“升序”意味着排序序列中较早的字符串排在前面。粗略地说，通常按字母顺序较早的单词排在前面。

```
select empNr, empName
from Employee
order by empName
```

| empNr | empName |
|---|---|
| 1004 | Adams, A. |
| 1005 | Dennis, A. |
| 1002 | Jones, E. |
| 1003 | Smith, F. |
| 1001 | Thompson, E. |

```
select empNr, empName
from Employee
order by empName asc
```

## 图 12.38 按员工姓名升序列出员工。

作为一个简单示例，图 12.38 中的每个查询都可用于按字母顺序列出员工。虽然极其不推荐，但在 **order by** 子句中可使用“2”来代替“empName”，因为 empName 是 **select** 列表中的第二个项（它不必是基表的第二列）。使用位置编号会带来问题：如果稍后修改 **select** 列表，会使查询更难理解，并且这是 SQL 标准中不推荐的特性（即以后版本可能会将其删除）。因为需要时可以使用 **asc** 来引入结果列名称，因此绝对不必为了排序而使用位置编号。所以，请勿使用它们。

字符串按字符排序序列进行排序。例如，如果使用 ASCII，则空格（“ ”）在数字（0..9）之前，数字在大写字母（A..Z）之前，大写字母在小写字母（a..z）之前。例如，在 ASCII 中，“M2” < “MY” < “Ma” < “Ma Kettle” < “MacTavish” < “Zen” < “apple”。然而，其他排序序列可能与此不同。例如，在 EBCDIC 中，小写字母在大写字母之前，大写字母在数字之前。

**order by** 子句可以被视为将行集转换为行序列的一种方式。出于排序目的，空值被视为相等，并且取决于实现，它们要么小于所有非空值（如 SQL Server 中），要么大于所有非空值。请考虑以下查询：

```
select carType from Employee
order by carType
```

这将返回序列“Ford”、“Ford”、“Toyota”，两个空值可能位于前面或后面，具体取决于实现。

如果用于排序的列没有唯一性约束，则可以通过指定更多列在其重复值内获得进一步的排序，如 in the

