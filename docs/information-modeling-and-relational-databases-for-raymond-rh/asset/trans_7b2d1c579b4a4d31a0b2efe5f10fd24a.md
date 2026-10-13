

# 子查询示例与连接替代方案

为了讨论一些示例，请考虑 [图 12.52](#Ch012_539-646_B9780443237904000268_1.xhtml#f0265) 中所示的表。假设存在一个从 `Mountain.countryName` 到 `Country.countryName` 的子集约束。相反的约束不适用（例如，荷兰没有山脉）。为节省空间，每个国家仅显示部分山脉。

![图 12.52 一些国家及其部分山脉（如果有）。](images/B9780443237904000268/f12-52-9780443237904.jpg)

[图 12.52](#Ch012_539-646_B9780443237904000268_1.xhtml#B-f0265) 一些国家及其部分山脉（如果有）。

考虑查询：“哪些山脉位于人口超过 1 亿的国家？”我们可以先找出具有相关人口的国家，然后找出这些国家中的山脉。这可以用 SQL 表示如下：

```
select mtName from Mountain
where countryName in
    (select countryName from Country
     where population > 100000000)
```

首先对子查询求值，得到包（“India”、“USA”）。子查询被此中间结果替换后，对外部查询求值，最终得到三座山脉的列表：Mana、McKinley 和 Rainier。当然，该查询本可以用连接来表述。作为练习，您可以尝试这样做。

子查询可以嵌套（即其搜索条件可以包含子查询）。为提高可读性，子查询应始终缩进。嵌套层级越深，缩进应越大。

通常，使用子查询的查询可以用 `join` 查询替代，反之亦然。某些连接无法用子查询重新表述。特别是，**如果 `select` 列表包含来自多个表的列，则必须使用连接**（如果选择列来自同一表的不同副本，则必须使用自连接）。

例如，以下查询无法重新表述为子查询（结果表将包含哪些列？）：

```
select * from Country natural join Mountain
```

现在考虑我们在 [练习 6.3](#Ch006_211-271_B9780443237904000025.xhtml#s0025) 中讨论并在 [图 12.53](#Ch012_539-646_B9780443237904000268_1.xhtml#f0270) 中重现的软件零售商 UoD 的关系模式。

![图 12.53 发票应用的关系模式。](images/B9780443237904000268/f12-53-9780443237904.jpg)

[图 12.53](#Ch012_539-646_B9780443237904000268_1.xhtml#B-f0270) 发票应用的关系模式。

假设我们要发出查询：“列出每张记录了产品标题为 'Quinquo' 的发货的发票的客户编号、客户名称和发票编号。”您可能想在继续阅读前自行尝试用 SQL 编写此查询。

需要选择客户名称、客户编号和发票编号，但它们并不都出现在同一张表中。因此，我们必须在查询中包含连接，以便在结果表的同一行中将它们汇总在一起。

观察模式，我们所需的最小连接是基于 `customerNr` 将 `Customer` 和 `Invoice` 表连接起来。表之间其余的导航可以用子查询完成，因为我们不需要在最终结果的 `select` 列表中包含那些表中的任何其他列。这种方法导出了一个包含一个连接和嵌套子查询的表述，如下所示：

```
select customerNr, customerName, invoiceNr
from   Customer natural join Invoice
where invoiceNr in
    (select invoiceNr from Lineitem
     where itemCode in
         (select itemCode from Item
          where title = 'Quinquo'))
```

或者，我们可以用连接替换任意子查询。例如，以下表述使用了三个连接且无子查询：

```
select customerNr, customerName, invoiceNr
from      Customer natural join Invoice
natural join Lineitem
natural join Item
```

如果您的 SQL 方言不支持 `natural join` 语法，请改用条件连接语法或旧式 SQL-89 连接语法。

作为子查询的否定示例，以下查询列出了没有山脉的国家。对于给定的数据，结果仅为一个国家：荷兰。

```
select countryName from Country
where countryName not in
    (select countryName from Mountain)
```

能否用内连接替换否定子查询？不能！但是，您可以用外连接替换它。例如，上述查询可重新表述为：

```
select countryName
from Country natural left outer join Mountain
where mtName is null
```

该查询也可以用集合差运算来表述，如下所示：

```
select countryName from Country
except
select countryName from Mountain
```

要列出拥有山脉的国家，可以使用以下查询：

```
select countryName from Country
where countryName in
    (select countryName from Mountain)
```

这执行的是集合交集，等价于：

```
select countryName from Country
intersect
select countryName from Mountain
```

因此，当仅需要单列时，**结合子查询使用 `in` 和 `not in` 即使在 SQL-89 中也能表述集合交集和集合差运算**。为进一步讨论这一点，请回顾上一节中的 `Person` (shortName, nationality) 和 `Drives` (driver, carModel) 表。为方便起见，这些表的示例数据在 [图 12.54](#Ch012_539-646_B9780443237904000268_1.xhtml#f0275) 中重复给出。

![图 12.54 两个关系表。](images/B9780443237904000268/f12-54-9780443237904.jpg)

[图 12.54](#Ch012_539-646_B9780443237904000268_1.xhtml#B-f0275) 两个关系表。

回顾一下，以下查询分别用于列出开福特车的美国人和不开福特车的美国人：

```
select shortName from Person                select shortName from Person
where nationality = 'American'                  where nationality = 'American'
intersect                                                                                        except
select driver from Drives                              select driver from Drives
where carModel = 'Ford'                               where carModel = 'Ford'
```

对于不支持 `intersect` 或 `except` 运算符的方言，这些查询可用成员资格子查询重新表述，如下所示：

```
select shortName from Person               select shortName from Person
where nationality = 'American'                where nationality = 'American'
and shortName in                                                       and shortName not in
    (select driver from Drives                                      (select driver from Drives
     where carModel = 'Ford')                        where carModel = 'Ford')
```

如果我们想获得多列表的交集或差集，此技术在 SQL-89 中将不起作用。然而，稍后将讨论的 `exists` 量词可与子查询结合使用来处理此类情况。在 SQL-92 中，由于 `in` 运算符适用于行值表达式，多列情况可用成员资格子查询处理。

