
# SQL:2023 JSON 函数

SQL:2023 提供了多个函数来处理 JSON 值。这些函数分为两类。SQL/JSON **检索** 函数作用于 SQL/JSON 数据，并将值作为 SQL 数据或 SQL/JSON 数据返回。SQL/JSON **构造** 函数从 SQL 数据或 SQL/JSON 数据返回 SQL/JSON 值。

虽然 JSON 支持是在 SQL:2016 中添加的，但直到 SQL:2023 才包含 **`json`** 数据类型。在此期间，多个供应商引入了该数据类型及其对应处理函数的各自实现。结果导致不同系统之间存在一些差异，包括以下几点：

1. 某些 SQL/JSON 函数完全缺失，尽管可能通过更迂回的方式获得类似结果。
2. 提供的函数与 SQL/JSON 函数同名，但语法不同。
3. 函数具有与 SQL/JSON 定义相同的主要语法，但不支持 SQL:2023 中定义的某些可选子句。

希望未来这种情况能得到规范化。SQL:2023 中的主要 SQL/JSON 查询函数总结在表 16.7 中。

## 表 16.7：SQL/JSON 查询函数

![t16-07-9780443237904](img/t16-07-9780443237904.jpg)

某些系统可能提供替代方案，例如 **`json_extract()`**，其提供的功能类似于 **`json_query()`**；以及 **`json_contains()`**，可作为 **`json_exists()`** 的替代品。

这些查询操作符使用路径语言定位 JSON 数据的相关部分。这在原理上类似于将 XPath 与 XML 数据配合使用，但 JSON 路径语言的语法更接近 JavaScript。

路径从相关 JSON 文本的根开始。这将是一个对象或数组，表示为“美元”符号（`$`）。路径使用 **访问器** 显示从根到 JSON 文本中所需元素（或元素）的步骤：方括号（`[ ]`）用于数组中的元素，句点或“点”（`.`）用于对象的成员。JSONPath 的 ECMAScript 语言规范也允许对象成员使用括号表示法，但 SQL/JSON 不支持此语法。星号（`*`）用作通配符，表示数组中的所有元素或对象的所有成员。为了说明这些概念，假设我们在名为 `videos` 的表的 `movie` 列中存储了 Listing 16.3 的 JSON 文本。

该文本包含一个名为 `movies` 的单个对象。该对象的值是一个包含六个元素的列表。列表中的每个元素都是一个包含“title”、“director”等成员的对象。我们可以使用以下查询获取所有电影名称的列表。

```sql
select json_query(movie, '$.movies[*].title') from videos
```

要从根构建路径，我们首先添加 `movies` 成员（此层级的唯一成员）。接下来，为 `movies` 数组的所有元素添加通配符规范。最后，从每个数组元素添加 `title` 成员。所有路径表达式都以此方式工作，尽管它们可能复杂得多。

JSON 路径表达式可在两种模式下使用：**`lax`**（宽松）和 **`strict`**（严格）。`lax` 模式是默认模式，它提供对某些结构问题的自动处理。如果路径表达式中的对象访问器发现数组而非对象，则将该数组转换为序列，然后将对象访问器应用于序列的每个元素。如果数组访问器发现的值不是数组，则将该值转换为单元素数组。如果错误无法通过这些机制处理，则返回空的 SQL/JSON 序列。

在 `strict` 模式下，结构错误将直接报告，不会尝试任何修正。这对于识别路径表达式返回意外结果的原因非常有用。

**`json_query`** 的目的是返回 JSON 文本的提取内容。这将是一个包含其他项目的结构项（数组或对象）。要返回标量值，则使用 **`json_value`**。其语法与 **`json_query`** 相似，但路径必须标识单个项目。请看以下两个查询：

```sql
select json_query(movie, '$.movies[*].movieNr') from videos
select json_value(movie, '$.movies[*].movieNr') from videos
```

第一个查询将返回电影编号列表，但第二个将返回 **`null`**，因为结果不是标量值。可以将 **`json_value`** 返回的标量转换为适当的 SQL 数据类型。例如：

```sql
select json_value(movie, '$.movies[0].movieNr returning decimal(5,2)') from videos
```

返回一个标量值（因为此查询仅指定了第一个数组项），并转换为指定的 SQL 类型。如果未指定转换，返回值的类型为系统默认值（通常为 **`varchar`**）。

如果返回 null，我们可能想知道原因。有三种可能性：null 可能是从被查询的 JSON 文本中检索到的，指定的值不存在，或发生了某些错误。所有这些情况的默认行为都是返回 null，但我们可以通过可选子句来区分“on empty”和“on error”情况。例如，以下查询将返回文本 "Not found"，因为我们指定了一个数据中不存在的数组索引。并非所有系统都支持此类可选子句。

```sql
select json_value(movie, '$.movies[8].movieNr' default 'Not found' on empty) from videos
```

我们可以使用 **`json_exists`** 检查特定项目是否存在。在这种情况下，如果项目存在则返回 1，不存在则返回 0。例如：

```sql
select json_exists(movie, '$.movies[*].director') from videos
```

将返回 1，表示至少找到一个指定项目的实例；但：

```sql
select json_exists(movie, '$.movies[*].producer') from videos
```

返回 0，因为我们的电影对象不包含 `producer` 成员。

**`json_exists`** 的一个有用应用是创建检查约束，以确保 JSON 数据包含某些强制元素。还可以使用进一步的谓词来检查项目是（或不是）JSON 值、数组、对象或标量，但我们在此不详述。

虽然 **`json_query`** 可以从 JSON 文档返回结果，但结果仍保持 JSON 格式。为了与其他操作保持一致，我们可能更倾向于以标准 SQL 表的形式获取结果。这正是 **`json_table`** 提供的功能，它从 JSON 文档中提取数据并将其作为关系表返回。这是一个基于我们常用电影数据的简单示例。

```sql
select jt.Title, jt.Director from videos as v, json_table (v.movies, '$.movies[*]' columns(   Title varchar(20) path '$.title',   Director varchar(20) path '$.director'  )) as jt
```

SELECT 语句标识由 **`json_table`** 函数创建的别名 JSON 表（“jt”）中的列。函数的第一个参数指定 JSON 源，在本例中为 `videos` 表的 `movies` 列。第二个参数定义 JSON 文本中的起始点，在本例中为 `movies` 数组。列列表定义列名、SQL 数据类型以及当前上下文中的路径（在本例中为前面定义的起始点）。结果是一个直观的 SQL 表。

![u16-06-9780443237904](img/u16-06-9780443237904.jpg)

### 使用嵌套列

可以通过使用“嵌套”列来包含 JSON 文本中不同层级的数据。在我们的数据中，电影明星的名字位于电影标题的下一层级。以下示例展示了如何组合这些层级。

```sql
select jt.* from videos as v, json_table(v.movies, '$.movies[*]' columns(
    Title varchar(20) path '$.title',
    Released int path '$.released',
    nested path '$.stars[*]' columns (
        Starring varchar(20) path '$.name'
    )
)) as jt order by Released
```

同样，这会生成一个标准的 SQL 结果表。

![u16-07-9780443237904](img/u16-07-9780443237904.jpg)

以这种方式生成的表可以参与所有常规的表操作，例如与数据库中的其他（非 JSON）表进行连接操作。`json_table` 的一个可能用途是创建视图，从而向 SQL 开发人员隐藏数据的 JSON 来源。

还有一个 SQL/JSON 检索函数，即 `json_serialize`。它以 JSON 值作为输入，并以 SQL 字符数据类型（通常为 `varchar`）之一返回 JSON 文本。如果“原始” JSON 值采用二进制形式（不便于人类阅读），这非常有用。某些实现可能还包含一个“美化”选项，以生成格式良好的文本。

## SQL/JSON 构造函数

我们迄今为止考虑的操作假设数据库中存储了一些 JSON 值，并且我们想要以各种方式提取其中的部分或全部。SQL/JSON 还定义了构造函数，用于从非 SQL/JSON 值构建 SQL/JSON 项。

其中最明显的是 `json_parse`，它接受文本输入并将其转换为 JSON 序列。这本质上是 `json_serialize` 的逆操作。如果输入文本不是格式良好的 JSON，将返回错误。`json_scalar` 函数很简单：它从非 JSON 值创建一个 JSON 值。例如，数据类型为 `int` 的 SQL 值将被转换为 JSON 数字。

更有趣的是用于构造 JSON 结构元素（对象和数组）的函数。构造函数可以嵌套，因此我们可以构建任意复杂度的 JSON 值。这些函数总结在表 16.8 中。

### 表 16.8：SQL/JSON 结构构造函数

![t16-08-9780443237904](img/t16-08-9780443237904.jpg)

这些函数有许多选项，我们将通过示例探讨其中一些。图 16.4 中的关系表显示了关于代理及其项目分配的一些数据。SQL 数据类型为：员工编号和费率为 `int`，其他列为 `varchar`。空白处代表 SQL `null`。我们假设最终目标是创建一个包含每个代理单独对象的单个 JSON 对象，包括他们可能拥有的任何项目分配。

**图 16.4** 代理和项目数据。

![图 16.4 代理和项目数据。](img/f16-04-9780443237904.jpg)

创建对象很简单。以下查询定义了一个包含员工编号和办公室成员的对象结构，然后将其应用于 Agent 表的每一行。

```sql
select json_object('empNr' value nr, 'office' value office) from Agent
```

**结果：**

```
{"empNr": 101, "office": "Boston"}
{"empNr": 232, "office": "Portland"}
{"empNr": 397, "office": "Durham"}
{"empNr": 468, "office": null}
```

某些 `json_object` 实现用逗号替换 `value` 关键字。结果中一个难看的特征是最后一个对象中的 `null`。更自然的 JSON 表示会完全省略该成员。SQL/JSON 定义了一个可选的 `absent on null` 子句来实现这一点，但并非所有实现都支持。我们可能可以根据领域知识提供更有意义的内容来找到变通方法。例如，如果我们知道 Dave Dunk 没有记录办公室的原因是他经常移动，办公室不固定，我们可以替换该 `null`。

```sql
select json_object(
    'empNr', nr,
    'office', case when office is not null then office else 'varies' end
) from Agent
```

**结果：**

```
{"empNr": 101, "office": "Boston"}
{"empNr": 232, "office": "Portland"}
{"empNr": 397, "office": "Durham"}
{"empNr": 468, "office": "varies"}
```

显然，该查询可以扩展以包含 `givenName` 和 `familyName` 的单独成员，但另一种方法是创建一个 `name` 成员，其中包含名称各组成部分的对象。这可以通过在 `name` 成员中嵌套额外的 `json_object` 构造函数来完成。

电话信息稍微复杂一些，因为该成员不是单值的。我们假设需要一个号码列表，每个号码由一个对象表示。这可以通过以下方式在数组构造函数中嵌套对象构造函数来生成。

```sql
select json_array(
    json_object('type' value 'home', 'number' value homePhone),
    json_object('type' value 'work', 'number' value workPhone)
) from Agent
```

**结果：**

```
[{"type": "home", "number": "222-9876"}, {"type": "work", "number": "222-1234"}]
[{"type": "home", "number": null}, {"type": "work", "number": "555-6789"}]
[{"type": "home", "number": "777-6789"}, {"type": "work", "number": "777-4321"}]
[{"type": "home", "number": null}, {"type": "work", "number": null}]
```

为了整合这些信息，我们可以在之前的对象中引入一个 `phones` 成员，并将上述数组构造嵌套在其中。我们面临着与之前相同的 `null` 问题。如果 `absent on empty` 子句不可用，我们可以创建一个更复杂的 SQL 查询来从 JSON 结果中移除 `null` 成员，但就我们目前的目的而言，我们将直接接受这些 `null`。

到目前为止未涉及的函数是对象聚合和数组聚合构造函数。我们可以用 Project 表来说明这些。`json_objectagg` 函数需要一个键值对，如以下示例所示：

```sql
select empNr, json_objectagg(projName, rate)
from Project group by empNr
```

**结果：**

```
101     {"Grebe": 2, "Mallard": 1}
232     {"Grebe": 3, "Plover": 1, "Bittern": 2}
```

在这里，每个组的结果对象为组中的每个项都有一个成员。这与 `json_object` 不同，后者会为每个项给出一个单独的对象。

创建聚合数组的工作方式类似，但只需要标识要列出的值。这将生成一个数组，其中每个组的每个项对应一个元素。

```sql
select empNr, json_arrayagg(projName)
from Project group by empNr
```

**结果：**

```
101     ["Mallard", "Grebe"]
232     ["Grebe", "Plover", "Bittern"]
```

为了实现我们创建全面 Agent 对象的目标，`json_arrayagg` 构造函数看起来最合适。这可以通过将其嵌套在主对象结构的 `projects` 成员中来集成到更大的查询中。

要创建所需的最终 JSON 结构，可以将包含上述元素的行聚合在一起，形成一个包含在外层对象中的代理列表，如以下查询所示。

```sql
select json_object ('Agents', json_arrayagg(json_object(
       'empNr' value nr,
       'name', json_object('given' value givenName, 'family' value familyName),
       'phone', json_array(json_object('work' value workPhone), json_object('home' value homePhone)),
       'office', case when office is not null then office else 'varies' end,
       'projects', (select json_arrayagg(projName) from Project p where p.empNr = a.nr group by p.empNr)
))) from Agent a
```

以下清单显示了组合结果，稍作格式化以使结构更加清晰。
