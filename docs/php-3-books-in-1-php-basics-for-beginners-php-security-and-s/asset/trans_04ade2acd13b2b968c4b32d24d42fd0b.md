
```sql
select Lastname, firstname from newstaffpartition
GROUP BY LASTNAME, FIRSTNAME ORDER BY LASTNAME LIMIT 5
TOP 5 OF NEWSTAFFPARTITION GROUP BY LASTNAME, FIRSTNAME ORDER BY LASTNAME LIMIT 5
```

最后，可以将 TOP 子句与 WHERE 子句结合使用。这将影响查询返回的结果排序。以下两个示例展示了如何获取按姓氏排列的前五名员工的结果。这次，结果将按年龄排序，使前五名与基于年龄的前五名相匹配。

```sql
select Lastname, firstname from newstaffpartition where Lastname = 'Smith'
TOP 5 OF NEWSTAFFPARTITION WHERE LASTNAME = 'SMITH' ORDER BY LASTNAME
```

此时，你可能已经开始习惯 TOP 子句的工作方式以及它如何帮助你的查询。不过情况并非完全如此简单。使用此子句时需要牢记一些限制。你可以在下面的章节中阅读有关这些限制的更多信息。

TOP 子句可与各种条件一起使用（包括 IN 和 NOT IN）。它始终在 SQL 语句的末尾进行求值，即使它查询的是在处理过程中更早计算出的结果集。换句话说，如果你有多个使用 LIMIT 或 ORDER BY 子句的 SELECT 语句，则只有一个语句会在 TOP 子句下执行。这意味着即使 SQL Server 将操作视为一个整体，你也会错失可能的复杂性节省。

## ROWNUM 子句

ROWNUM 子句帮助 SQL Server 确定从查询中返回多少行。它用于限制从 SELECT 语句返回的行数。

ROWNUM 子句的语法与 TOP 子句相同，但其行为不同。在 SELECT 语句中使用时，它仅在当前行或在与 LIMIT 子句一起执行时查询结果集中的所有行进行求值。也就是说，如果恰好有 N 行并且使用了 ROWNUM 子句，则只会返回 N 行。如果未使用，则结果集中的所有行都会被返回（即，一旦获取了查询影响的所有行）。

在 SQL-2005 和 SQL-99 中（但在后续版本中不行），可以通过向 ROWNUM 子句添加可选的 "NOT NULL" 子句来更改此行为。以下示例最能说明这一点：

```sql
select * from newstaffpartition order by staffid, Lastname, firstname, age where staffid > 10
limit 5 ROWNUM(staffid)
```

这将返回仅包含五行的结果集。

## LIMIT 子句

除了 TOP 和 ROWNUM 子句之外，SQL Server 还提供 LIMIT 子句。此子句帮助 SQL Server 确定从查询中返回多少行。如前所述

1, 2, 3, 4, 5。此结果集的其余部分未定义，因为你未指定“最大值”或“最小值”。因此，它们不包含在你指定的范围内。

术语“未定义”具有误导性，可能导致你在查询中出现错误。

实际上，top 50% 子句用于过滤数据集。确保查询返回所需行要容易得多。如果你想按降序排列结果，始终可以使用 ORDER BY 子句。以下示例展示了如何操作：

```sql
SELECT TOP 50 PERCENT FROM (SELECT 1 AS min_val, 2 AS max_val, ... UNION ALL
SELECT min (min_val), max (min_val), ...) as result2 ORDER BY min_val DESC;
```

此示例过滤结果集，仅显示小于总数的 50% 的数字。注意：你想要查看的结果必须按降序排列。

你还可以向 SQL SELECT 语句添加“order by”子句。这允许你将查询结果限制为更窄的值范围。

## 通配符

通配符是用于替换字符串的一部分而不改变该字符串原始文本的字符。通配符通常有两种形式：字符数字通配符和字符字符串通配符。

字符数字通配符由百分号（%）表示，可在你知道指定字符的每个实例必须出现在字符串中，但不关心将替换的确切字符时使用。例如，给定用户名“Smith”，你可以使用 % 通配符将字符串中的第一个字符替换为你选择的任意字符。最终结果将为 smith%。

字符字符串通配符的功能与字符数字通配符相同，只是它允许你指定可在目标字符替换中出现的字符字符串。因此，你可以指定一个可匹配字符串中任意 3 个字符的通配符。例如，此字符串：“smith%”将用单词 Smith 替换 smith，并用你选择的任意单词替换 %。最终结果将为 Smith。

### 如何使用通配符

你可以通过以下方式使用通配符：

- 1. 使用“%”字符指定你想要的任意数量的字符。如果你希望替换除第一个字符外的所有字符，请使用此方法：“% %。它可以被任意数量的字符替换，但必须至少有一个数字，并且字符串中必须包含百分号。
- 2. 使用字符字符串指定替换时要使用的字符。例如，你可能会使用 %a%b%c% 作为替换字符串，其中 a、b 和 c 是任意三个字符。
- 3. 在查询中使用多个 % 通配符来指定查询中要被替换的确切字符。例如，select * from table where fieldname = %%%。

通配符的一般语法：

字符数字通配符和字符字符串通配符均可按如下方式使用：

```
|<OriginalString> | <replaceCharacter> | <replaceString1>...<replaceStringm> |
```

<replaceCharacter> 可以是下面列出的字符中的任意一个。这种方式一次只能使用一个字符。因此，如果你想替换特定字符的所有匹配项，它看起来像这样：replaceCharacter = ‘%’。在替换字符串中不能有多个‘%’字符。

<replaceString> 可以是以下组合中的任意一个：%，%%，%a%，%b%，%c%，a%，b%，c%。

示例：

在以下示例中，你将使用 replaceCharacter、替换字符串组合以及字符数字通配符和字符字符串通配符执行 SQL 通配符搜索。

- Step 1: 打开一个查询并在查询窗口中输入以下语句：select * from a table where fieldname like %a%。当你按 Enter 时，查询结果将显示字段名称中出现这些字母的所有记录。
- Step 2: 现在，通过将 % 替换为 %% 来制作通配符查询。例如，select * from table where fieldname like %%%。当你按 Enter 时，你将获得所有结果；因此，与 a% 或 b% 或 c% 对应的所有记录将被检索。
- Step 3: 通过输入以下查询执行另一个通配符搜索：select * from table where fieldname like %b%。这将获取与 b% 或 c% 或 a% 相关的所有结果。
- Step 4: 使用‘?’字符代替任何单个字符。例如，对于所有名称以 s 开头的字段，输入 select * from the table where fieldname = ?s。按 Enter，你将获得所有以 s 开头的记录。

注意：使用‘^’字符匹配字符范围。例如，要获取名称以 s 开头并以 e 结尾的所有记录，输入 select * from the table where fieldname = ?s^e。按 Enter，你将获得所有以 s 开头并以 e 结尾的记录。

- Step 5: 使用‘_’字符作为通配符允许你用任意字符序列替换任何单个字符。例如，在表的字段名称中，你可以用下划线替换任何单个字符，或用下划线替换字符序列。例如，输入 select * from the table where fieldname = _%_%_。你将获得字段名称中字符 _ 出现多次的所有记录。
