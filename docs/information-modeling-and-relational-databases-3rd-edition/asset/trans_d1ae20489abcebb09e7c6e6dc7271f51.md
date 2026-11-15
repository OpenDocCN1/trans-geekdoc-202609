
在 JSON 文本中使用 *访问器* 指定所需元素（或元素）：方括号（`[]`）用于数组中的元素，句点或“点”（`.`）用于对象的成员。JSONPath 的 ECMAScript 语言规范也允许对象成员的括号表示法，但 SQL/JSON 不支持。星号（`*`）用作通配符字符，表示数组中的所有元素或对象中的所有成员。为了说明这些概念，假设我们有一个名为 videos 的表中 movie 列的清单 16.3 中的 JSON 文本。

此文本包含一个名为 movies 的单个对象。该对象的值是六个元素的列表。列表中的每个元素都是带有“title”、“director”等成员的对象。我们可以使用以下查询获取所有电影名称列表。

```sql
select json_query(movie, '$.movies[*].title') from videos
```

要从根开始构建路径，我们首先添加 movies 成员（此级别中唯一的成员）。接下来，我们为 movies 数组的所有元素添加通配符规范。最后，我们从每个数组元素添加 title 成员。所有路径表达式都以这种方式工作，尽管它们可能复杂得多。

JSON 路径表达式可以在两种模式下使用：*宽松* 和 *严格*。*宽松* 模式是默认模式，它提供对某些结构问题的自动处理。如果路径表达式中的对象访问器找到的是数组而不是对象，则数组将转换为序列，然后对象访问器应用于序列的每个元素。如果数组访问器找到的不是数组的值，则该值将转换为单元素数组。如果这些机制无法处理错误，则返回一个空的 SQL/JSON 序列。

在 *严格* 模式下，会报告结构错误而不尝试纠正。这对于识别路径表达式为何返回意外结果很有用。

json_query 的目的是从 JSON 文本中返回一个提取项。这将是一个包含其他项的结构项（数组或对象）。要返回标量值，使用 **json_value**。它与 json_query 具有类似的语法，但路径必须标识单个项。请考虑以下两个查询：

```sql
select json_query(movie, '$.movies[*].movieNr') from videos
select json_value(movie, '$.movies[*].movieNr') from videos
```

第一个将返回电影编号列表，但第二个将返回 null，因为结果不是标量值。可以将 json_value 返回的标量转换为适当的 SQL 数据类型。例如：

```sql
select json_value(movie, '$.movies[0].movieNr returning decimal(5,2)') from videos
```

返回一个标量值（因为此查询仅指定第一个数组项），并强制转换为指定的 SQL 类型。如果未指定转换，则返回值的类型为系统默认值（通常是 varchar）。

如果返回 null，我们可能想知道原因。有三种可能性：null 可能是从正在查询的 JSON 文本中检索到的，指定的值不存在，或者发生了某些错误。所有这些情况的默认行为都是返回 null，但我们可以使用可选子句来区分它们，以处理“on empty”和“on error”情况。例如，以下查询将返回文本“Not found”，因为我们指定了数据中不存在的数组索引。并非所有系统都支持此类可选子句。

```sql
select json_value(movie, '$.movies[8].movieNr' default 'Not found' on empty) from videos
```

我们可以使用 json_exists 来检查特定项是否存在。在这种情况下，如果项存在则返回值为 1，如果不存在则返回 0。例如：

```sql
select json_exists(movie, '$.movies[*].director') from videos
```

将返回 1，指示至少找到一次指定的项，但是：

```sql
select json_exists(movie, '$.movies[*].producer') from videos
```

将返回 0，因为我们的电影对象不包含 producer 成员。

json_exists 的一个有用应用是在创建检查约束以确保 JSON 数据包含某些必需元素。可以使用进一步的谓词来检查项是否是（或不是）JSON 值、数组、对象或标量，但我们不会在此深入探讨这些细节。

虽然 json_query 可以从 JSON 文档返回结果，但结果仍以 JSON 格式保留。为了与其他操作保持一致，我们可能更希望以标准 SQL 表的形式获得结果。这是 json_table 提供的功能，它从 JSON 文档中提取数据并将其作为关系表返回。以下是一个基于常规电影数据的简单示例。

```sql
select jt.Title, jt.Director from videos as v,
json_table (v.movies, '$.movies[*]' columns(
Title varchar(20) path '$.title',
Director varchar(20) path '$.director'
)) as jt
```

SELECT 语句识别由 json_table 函数创建的别名 JSON 表（“jt”）中的列。函数的第一个参数指定 JSON 源，在此例中为 videos 表的 movies 列。第二个参数定义 JSON 文本中的起点，在此例中为 movies 数组。列列表定义列名、SQL 数据类型和当前上下文中的路径（在此例中为先前定义的起点）。结果是一个简单的 SQL 表。

| 标题 | 导演 |
|---|---|
| 宇宙学 | Lee Lafferty |
| 功夫足球 | Stephen Chow |
| 秘密花园 | Alan Grint |
| 秘密花园 | Agnieszka Holland |
| 达·芬奇密码 | Ron Howard |
| 失落世界 | Robert Zemeckis |

可以通过使用“嵌套”列来包含 JSON 文本不同层级中的数据。在我们的数据中，电影的任何明星名称都位于电影标题下方的层级。以下示例展示了如何合并这些层级。

```sql
select jt.* from videos as v,
json_table (v.movies, '$.movies[*]' columns(
Title varchar(20) path '$.title',
Released int path '$.released',
nested path '$[*]'
columns (
Starring varchar(20) path '$.name')
)) as jt
order by Released
```

同样，这会生成一个标准 SQL 结果表。

| 标题 | 发行年份 | 主演 |
|---|---|---|
| 秘密花园 | 1987 | Gennie James |
| 秘密花园 | 1987 | Barrett Oliver |
| 秘密花园 | 1993 | Kate Maberley |
| 秘密花园 | 1993 | Heydon Prowse |
| 失落世界 | 2000 | Tom Hanks |
| 功夫足球 | 2004 | Stephen Chow |
| 宇宙学 | 2006 | NULL |
| 达·芬奇密码 | 2006 | Tom Hanks |
| 达·芬奇密码 | 2006 | Ian McKellen |
| 达·芬奇密码 | 2006 | Audrey Tautou |

以这种方式生成的表可以参与所有常规表操作，例如与数据库中其他（非 JSON）表的连接操作。`json_table` 的一个可能用途是创建视图，以便对 SQL 开发人员隐藏数据的 JSON 源。

还有一个 SQL/JSON 检索函数，即 `json_serialize`。它以 JSON 值作为输入，并返回一种 SQL 字符数据类型（通常是 `varchar`）的 JSON 文本。如果“原始”JSON 值是以非供人类可读性的二进制形式存在，这很有用。某些实现还可能包含“pretty”选项以生成格式良好的文本。

迄今为止我们考虑的操作都假设数据库中存储了一些 JSON 值，并希望以各种方式提取其中的全部或部分。SQL/JSON 还定义了构造函数，用于从非 SQL/JSON 值构建 SQL/JSON 项。

其中最明显的是 `json_parse`，它以文本输入并将其转换为 JSON 序列。这基本上是 `json_serialize` 的逆操作。如果输入文本不是格式良好的 JSON，将返回错误。`json_scalar` 函数很简单：它从非 JSON 值创建一个 JSON 值。例如，数据类型为 `int` 的 SQL 值将被转换为 JSON 数字。
