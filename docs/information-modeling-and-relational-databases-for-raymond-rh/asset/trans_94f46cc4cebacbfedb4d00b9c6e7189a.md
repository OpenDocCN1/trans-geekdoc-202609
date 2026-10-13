
然而，我们不一定非要以这种方式拆分数据。例如，[Listing 16.2](#Ch016_831-873_B9780443237904000207.xhtml#f0040) 中的所有电影数据都可以作为单个值输入到 **`json`** 列中。

SQL:2023 提供了多个函数来处理 JSON 值。这些函数分为两类。SQL/JSON *检索* 函数作用于 SQL/JSON 数据，并将值作为 SQL 数据或 SQL/JSON 数据返回。SQL/JSON *构造* 函数从 SQL 数据或 SQL/JSON 数据返回 SQL/JSON 值。

虽然 JSON 支持是在 SQL:2016 中添加的，但直到 SQL:2023 才包含 **`json`** 数据类型。在此期间，多个供应商引入了该数据类型及其对应处理函数的各自实现。结果导致不同系统之间存在一些差异，包括以下几点：

1.  某些 SQL/JSON 函数完全缺失，尽管可能通过更迂回的方式获得类似结果。
2.  提供的函数与 SQL/JSON 函数同名，但语法不同。
3.  函数具有与 SQL/JSON 定义相同的主要语法，但不支持 SQL:2023 中定义的某些可选子句。

希望未来这种情况能得到规范化。SQL:2023 中的主要 SQL/JSON 查询函数总结在 [Table 16.7](#Ch016_831-873_B9780443237904000207.xhtml#t0040) 中。

[Table 16.7](#Ch016_831-873_B9780443237904000207.xhtml#B-t0040)

SQL/JSON 查询函数。

| ![t16-07-9780443237904](images/B9780443237904000207/t16-07-9780443237904.jpg) |

| --- |

某些系统可能提供替代方案，例如 **`json_extract()`**，其提供的功能类似于 **`json_query()`**；以及 **`json_contains()`**，可作为 **`json_exists()`** 的替代品。

这些查询操作符使用路径语言定位 JSON 数据的相关部分。这在原理上类似于将 XPath 与 XML 数据配合使用，但 JSON 路径语言的语法更接近 JavaScript。

路径从相关 JSON 文本的根开始。这将是一个对象或数组，表示为“美元”符号 (`$`)。路径使用 *访问器* 显示从根到 JSON 文本中所需元素（或元素）的步骤：方括号 (`[ ]`) 用于数组中的元素，句点或“点” (`.`) 用于对象的成员。JSONPath 的 ECMAScript 语言规范也允许对象成员使用括号表示法，但 SQL/JSON 不支持此语法。星号 (`*`) 用作通配符，表示数组中的所有元素或对象的所有成员。为了说明这些概念，假设我们在名为 `videos` 的表的 `movie` 列中存储了 [Listing 16.3](#Ch016_831-873_B9780443237904000207.xhtml#f0045) 的 JSON 文本。

该文本包含一个名为 `movies` 的单个对象。该对象的值是一个包含六个元素的列表。列表中的每个元素都是一个包含“title”、“director”等成员的对象。我们可以使用以下查询获取所有电影名称的列表。

```
select json_query(movie, '$.movies[*].title') from videos
```

要从根构建路径，我们首先添加 `movies` 成员（此层级的唯一成员）。接下来，为 `movies` 数组的所有元素添加通配符规范。最后，从每个数组元素添加 `title` 成员。所有路径表达式都以此方式工作，尽管它们可能复杂得多。

JSON 路径表达式可在两种模式下使用：*lax*（宽松）和 *strict*（严格）。Lax 模式是默认模式，它提供对某些结构问题的自动处理。如果路径表达式中的对象访问器发现数组而非对象，则将该数组转换为序列，然后将对象访问器应用于序列的每个元素。如果数组访问器发现的值不是数组，则将该值转换为单元素数组。如果错误无法通过这些机制处理，则返回空的 SQL/JSON 序列。

在 strict 模式下，结构错误将直接报告，不会尝试任何修正。这对于识别路径表达式返回意外结果的原因非常有用。

**`json_query`** 的目的是返回 JSON 文本的提取内容。这将是一个包含其他项目的结构项（数组或对象）。要返回标量值，则使用 **`json_value`**。其语法与 **`json_query`** 相似，但路径必须标识单个项目。请看以下两个查询：

```
select json_query(movie, '$.movies[*].movieNr') from videos
select json_value(movie, '$.movies[*].movieNr') from videos
```

第一个查询将返回电影编号列表，但第二个将返回 **`null`**，因为结果不是标量值。可以将 **`json_value`** 返回的标量转换为适当的 SQL 数据类型。例如：

```
select json_value(movie, '$.movies[0].movieNr returning decimal(5,2)') from videos
```

返回一个标量值（因为此查询仅指定了第一个数组项），并转换为指定的 SQL 类型。如果未指定转换，返回值的类型为系统默认值（通常为 **`varchar`**）。

如果返回 null，我们可能想知道原因。有三种可能性：null 可能是从被查询的 JSON 文本中检索到的，指定的值不存在，或发生了某些错误。所有这些情况的默认行为都是返回 null，但我们可以通过可选子句来区分“on empty”和“on error”情况。例如，以下查询将返回文本 "Not found"，因为我们指定了一个数据中不存在的数组索引。并非所有系统都支持此类可选子句。

```
select json_value(movie, '$.movies[8].movieNr' default 'Not found' on empty) from videos
```

我们可以使用 **`json_exists`** 检查特定项目是否存在。在这种情况下，如果项目存在则返回 1，不存在则返回 0。例如：

```
select json_exists(movie, '$.movies[*].director') from videos
```

将返回 1，表示至少找到一个指定项目的实例；但：

```
select json_exists(movie, '$.movies[*].producer') from videos
```

返回 0，因为我们的电影对象不包含 `producer` 成员。

**`json_exists`** 的一个有用应用是创建检查约束，以确保 JSON 数据包含某些强制元素。还可以使用进一步的谓词来检查项目是（或不是）JSON 值、数组、对象或标量，但我们在此不详述。

虽然 **`json_query`** 可以从 JSON 文档返回结果，但结果仍保持 JSON 格式。为了与其他操作保持一致，我们可能更倾向于以标准 SQL 表的形式获取结果。这正是 **`json_table`** 提供的功能，它从 JSON 文档中提取数据并将其作为关系表返回。这是一个基于我们常用电影数据的简单示例。

```
select jt.Title, jt.Director from videos as v, json_table (v.movies, '$.movies[*]' columns(   Title varchar(20) path '$.title',   Director varchar(20) path '$.director'  )) as jt
```

SELECT 语句标识由 **`json_table`** 函数创建的别名 JSON 表（“jt”）中的列。函数的第一个参数指定 JSON 源，在本例中为 `videos` 表的 `movies` 列。第二个参数定义 JSON 文本中的起始点，在本例中为 `movies` 数组。列列表定义列名、SQL 数据类型以及当前上下文中的路径（在本例中为前面定义的起始点）。结果是一个直观的 SQL 表。

| ![u16-06-9780443237904](images/B9780443237904000207/u16-06-9780443237904.jpg) |

| --- |
