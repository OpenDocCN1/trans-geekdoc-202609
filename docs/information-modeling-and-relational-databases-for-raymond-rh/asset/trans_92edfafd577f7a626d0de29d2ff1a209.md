
# SQL 中的包函数

`sum` 和 `avg` 函数要求参数为数值表达式，而 `max` 和 `min` 接受数值或字符串表达式。`Count` (`*`) 将空值视同实际值处理。所有其他函数调用在计算结果前都会先移除空值。如果参数包为空（无论是最初就为空，还是因移除空值而变空），`count` 返回 0，其他函数返回 null。

`count` 函数有两种用法。`Count` (`*`) 返回指定表中的行数，而 `count` (`colname`) 返回指定列中的值的个数。如果在包函数中指定了 `distinct`，则会排除任何重复值。如果需要保留重复值，可使用关键字 `all`；但由于这是默认行为，因此通常会省略。显而易见，给 `max` 或 `min` 添加 `distinct` 没有任何效果。

以下查询展示了一些基于 [图 12.55](#Ch012_539-646_B9780443237904000268_2.xhtml#f0280) 中 Pupil 表的示例。在第三个示例中，使用 `where` 子句在调用函数前过滤掉不需要的行。

```
select count(*) from Pupil → 6
```

```
select count(distinct gender) from Pupil → 2
```

```
select count(*) from Pupil
where iq > 100 → 3
```

`sum` 函数返回列中值的总和，`avg` 返回这些值的平均值。例如：

```
select sum(iq) from Pupil → 550
```

```
select sum(distinct iq) from Pupil → 430
```

```
select avg(iq) from Pupil → 110
```

请注意此处空值的排除。因为 Don Collins 的 IQ 未知，所以只有五个 IQ 值参与计算。因为这些值总和为 550，所以它们的平均值是 110。

如果 `avg` 函数的参数是精确数值类型，SQL 标准将结果的小数位数留给具体实现定义。例如，以下查询根据所用 SQL 方言的不同会返回不同的结果。

```
select avg(distinct iq) from Pupil → 107.50 -- 在某些 SQL 中
```

```
→ 107 -- 在 SQL Server 中
```

在 SQL Server 中，此处的小数位数为 0，因此平均结果中的任何小数部分都会丢失。要保留小数部分，可以将参数乘以 1.0 以将其强制转换为实数。例如：

```
select avg(distinct 1.0 * iq) from Pupil → 107.500000
```

函数 `max` 和 `min` 分别返回最大值和最小值。如果数据类型是字符串而非数值，这些值将根据字符排序规则中的顺序位置计算。例如：

```
select max(iq) from Pupil → 120
```

```
select min(iq) from Pupil → 95
```

```
select max(surname) from Pupil → Evans
```

在 SQL-89 中，包函数只能在 `select` 列表中调用（或在 `having` 子句中——见后文）。例如，考虑请求“谁的 IQ 高于学生平均 IQ？”以下写法是非法的：

```
select firstname, surname from Pupil
where iq > avg(iq) → Error!
```

相反，我们需要将函数调用嵌入子查询中，如下所示。该查询在其结果中正确列出了 Ann Adams、Tom Brown 和 Ann Evans。

```
select firstname, surname from Pupil
where iq >
    (select avg(iq) from Pupil)
```

以下 SQL 查询给出了更多示例。第一个查询计算最高 IQ 与最低 IQ 的差值。第二个查询确定最高 IQ 与最低 IQ 的比率（注意乘以 1.0 以确保包含小数部分）。类似地，在第三个示例中，为计算最高和最低 IQ 的平均值，除数为 2.0 而非 2。第四个示例列出了那些 IQ 的 80% 大于最小 IQ 的 90% 的学生。作为练习，解释为什么在 SQL-89 中将搜索条件表示为 `0.8 * IQ > 0.9 * (select min(IQ) from Pupil)` 是错误的。

```
select max(iq) - min(iq) from Pupil → 25
```

```
select 1.0 * max(iq) / min(iq)
from Pupil → 1.263157
```

```
select (max(iq) + min(iq)) / 2.0
from Pupil → 107.500000
```

```
select firstname, surname from Pupil
where 0.8 * iq >
    (select 0.9 * min(iq) from Pupil)
→ Ann Adams
  Tom Brown
  Ann Evans
```

此例说明了这样一个事实：在 SQL-89 中，与函数调用不同，算术表达式可作为搜索条件中待比较的项使用。

下一个例子额外说明了内置函数可以接受算术表达式作为参数。考虑以下关系模式：`Window` (`windowNr`, `height`, `width`)。以下查询可用于列出那些高度超过宽度且差值最大的窗户的详细信息。

```
select * from Window
where height - width =
    (select max(height - width) from Window)
```

SQL-92 和 SQL:1999 扩展了可作为包函数参数的表达式范围。例如，`sum` 和 `avg` 可应用于间隔类型，`max` 和 `min` 可应用于用户定义类型。虽然 SQL-92 和 SQL:1999 没有增加新的包函数，但它们增加了许多标量函数。例如，SQL-92 引入了以下标量函数，每个函数接受零个或多个参数并返回一个标量：`bit_length`、`char_length`、`octet_length`、`case`、`cast`、`collate`、`convert`、`translate`、`current_date`、`current_time`、`current_timestamp`、`current_user`、`session_user`、`system_user`、`user`、`extract`、`lower`、`upper`、`position`、`substring` 和 `trim`。大多数方言支持其中一些，以及它们自己其他的标量函数。

`lower` 和 `upper` 函数分别返回参数的小写和大写版本，而 `cast` 函数将参数转换为另一种数据类型。这些函数的示例前面已给出。`substring` 函数使用语法 `substring` (`string-expn` `from` `start-posn` [`for` `length`]) 返回字符串的一部分。例如：

```
select substring(surname from 2 for 3)
from Pupil
where surname = 'Adams' → dam
```

某些方言对该函数使用非标准语法。例如，SQL Server 使用逗号代替 `from` 和 `for` 关键字，如 `substring` (`surname`, 2, 3)。
