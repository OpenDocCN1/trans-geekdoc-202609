
# SQL:2003 标准映射规则

SQL:2003 标准引入了一套广泛的映射规则，以定义 SQL 实体如何从 SQL 映射到 XML（以及反向映射）。规则规范相当广泛，且某些方面取决于实现，因此我们不在此涵盖所有细节。广义上讲，SQL 数据类型映射到 XML Schema 中定义的最接近的等价类型。可使用 XML Schema 侧面和注释来指示某些区别。例如，基本 XML Schema 不区分 `character varying` 和 `character large object`，它们在 SQL 中是不同的类型。SQL 中的分隔标识符按定义映射，保留字符的大小写。常规标识符的大小写不保证会被保留。

对于会导致 XML 中非法名称的字符，会给予特殊处理。通用技术是将该字符替换为 `_xNNNN_` 或 `_xNNNNNN_`，其中 N 为十六进制数字，NNNN 或 NNNNNN 为该字符的 Unicode 表示。标识符映射有两种变体：`部分转义` 和 `完全转义`。两者的关键区别在于对非初始冒号以及以字母“xml”开头（任何大小写组合）的标识符的处理。这些差异总结在表 16.5 的示例中。

## 表 16.5

将 SQL 标识符映射到 XML。

| ![t16-05-9780443237904](img/t16-05-9780443237904.jpg) |

---

# 使用 XQuery

SQL/XML:2006 引入的最重要方面之一，是将 XQuery 集成到成熟的关系数据库框架中——这是将 SQL/XML 迁移到 XQuery 数据模型的关键动因。需注意一点：如果您有 SQL 背景，请记住与 SQL 不同，XQuery **区分大小写**，因此在指定表达式时需格外小心。同样重要的是要记住，在 SQL/XML 中，我们操作的是 XML 值而非其序列化表示。因此，例如，我们并非试图文本处理“尖括号”，尽管这些对于表示人类可读的结构可能很有用。

最后，我们将介绍 SQL/XML 中提供的一些机制，它们有助于将 XQuery 集成到关系框架中。其中最重要的是 `xmlquery` 函数，它允许在 SQL 上下文中评估 XQuery 表达式。单独的 SQL 无法操作 XML 文档的各个部分：整个文档被视为单个值。借助 `xmlquery` 函数，可以查询 XML 文档内部，使 XML 数据能参与 SQL 查询，并将 SQL 处理应用于返回的 XML 值（例如，使用 `order by` 对结果排序）。`xmlquery` 的基本语法如下。参数的使用方式与我们在其他函数中已见到的等价物类似。

```
xmlquery ( XQuery-expression [ passing [ { by ref | by value } ] XML-query-argument [,...] ] [ returning { content | sequence } ] [ { by ref | by value } ] [ { null on empty | empty on empty } ] )
```

## 另一个函数，`xmltable`

另一个函数 `xmltable` 提供了一种将 XQuery 结果集成回 SQL 的有用方法。通常，XQuery 表达式会返回一个序列，但通过使用 `xmltable`，我们可以执行一个 XQuery 表达式并将值作为表返回。返回的表可以包含任何 SQL 数据类型的列，包括 XML，尽管插入到 `xmltable` 中 `xml` 列的值必须是格式良好且具有单一根节点的。基本语法如下：

```
xmltable ( [ xmlnamespaces ( namespace-declaration-item [,…] ), ] row-pattern [ passing [ { by ref | by value } ] XMLquery-argument [,…] ]columns { { colname for ordinality | colname datatype [ by ref | by value ] path column-pattern} [,…] } )
```

`row-pattern` 定义一个生成元素序列的表达式。该序列中的每个元素将成为结果表中的一行。`columns` 子句列出列定义以及用于在 `row-pattern` 的每个元素中查找列值的路径表达式。`for ordinality` 选项创建一个带有自动序号引用的列，因此第一行是 1，第二行是 2，依此类推。此处显示了一个示例。假设我们有一个名为 `movieXML` 的 `xml` 值，其内容与我们在讨论 XQuery 时使用的示例类似。如果此 `xmltable` 函数调用包含在 `select` 语句中，则传递的值可以从表中合适的 xml 列中选择。

```
xmltable (‘//movies'passing movieXMLcolumns “Seqno” for ordinality, “MovieNr” int path ‘@movieNr', “Movie Name” varchar (50) path ‘title', “Release Year” char(4) path ‘released' “Director” varchar(50) path ‘director' )
```

生成的表将具有以下形式，并且可以像通过其他方式生成的表一样进行别名设置等操作。

| ![u16-05-9780443237904](img/u16-05-9780443237904.jpg) |

---

在这种情况下，自动生成的 `SeqNo` 列中的值和检索到的 `MovieNr` 列中的值巧合地相同。如果 XML 数据顺序不同，`SeqNo` 列将保持不变，但 `MovieNr` 列（和其他检索到的列）将反映 XML 元素的顺序。

# 练习 16.2

以下模式显示了一个数据库的一部分，该数据库存储有关维修技术人员及其擅长维修的组件类型的信息。不同的技术人员可能擅长维修不同的组件。

![](img/u16-01-9780443237904.jpg)

1. 利用现代数据库系统提供的功能，将维修数据库的内容转换为三个 XML 文档，即每个表对应一个 XML 文档。

2. 使用 XPath 和 XQuery 表达式生成以下结果，使用 Technician、Competence 和 Assembly XML 文档中的一个或多个。将结果生成为 XML 文档或 XML 片段。

   1. (a) 列出所有主管，并在每个主管下列出所有向其汇报的技术人员。Supervisor 和 Technician 元素应将 `empNr` 作为属性，将 `firstName` || ` ` || `lastName` 的连接作为元素内容。

   2. (b) 以层次结构形式列出组件（即顶级组件将包含子组件，子组件将包含其自己的子组件，以此类推）。将 `assemblyCode` 作为每个元素的内容显示。

   3. (c) 列出所有复杂度代码为 5 或更高且有报告的组件。按 `complexityNr`（降序）和 `assemblyCode`（升序）对列表进行排序。

   4. (d) 对于每个技术人员，列出他们擅长维修的组件类型。将每个组件的 `complexityNr` 作为属性包含在内。

   5. (e) 列出所有技术人员，并在每个技术人员下包含一个 `certificationRefs` 元素。在技术人员没有 `certificationRef` 的情况下使用 `xsi:nil = “true”`。对于存在的每个 `certificationRef`，显示相关的 `assemblyCode`。

   5. (f) 列出没有技术人员擅长维修的所有组件。

3. 利用现代数据库系统提供的功能，将问题 2 中查询的每个 XML 结果转换为关系表。

# 16.3 JSON

JSON 代表 JavaScript Object Notation，这非常清楚地描述了它的起源和功能。与 XML 一样，JSON 是一种基于文本的格式，使得在不同系统之间交换数据变得非常容易。每个系统可以将数据以其自己的内部形式存储以实现高效处理，但这些内部表示不需要相同。JSON 最初由 Douglas Crockford 于 2000 年代初定义为一种数据交换格式，但随后被广泛采用为一种表达数据结构的便捷方式，并受到大多数编程语言的支持。早期的“信息性”标准（Crockford, 2006）之后，于 2013 年发布了第一个国际标准 (ECMA-404)。

JSON 的语法非常简单，是 JavaScript 语法的略微修改版本。有两个主要的结构元素。

1. 键值对集合。冒号字符分隔键和值，如：

   ```
   “givenName” : “Alan”, “familyName” : “Turing”
   ```

   键用双引号括起来。连续的项用逗号字符分隔，整个集合用大括号括起来。集合中项的顺序无关紧要。由于其 JavaScript 起源，此类集合被称为“对象”。

2. 包含有序值集合的数组。值用逗号字符分隔。数组用方括号括起来。

引用值之外的空白字符（空格、制表符、换行符等）会被忽略。值可以是字符串、数字、布尔值、特殊值 null，或两种结构化类型（对象和数组）之一。大体准则是数组用于相似项的集合，对象用于单个项的属性集合。

JSON 语法与 JavaScript 略有不同，后者不要求键加引号，并允许其他可能的值，如函数，但总体风格相似。这使得在 JavaScript 中处理 JSON 非常简单，该语言内置了处理 JSON 文本的函数。`JSON.parse()` 将文本表示转换为 JavaScript 对象结构，`JSON.stringify()` 将 JavaScript 对象结构转换为文本。其他面向对象语言也提供类似功能。JSON 的一个明显缺失是表达注释的任何能力。这是其设计者的有意选择，但一直是许多用户沮丧的来源。

与 XML 相比，这种简单直接的处理是一个显著优势，XML 需要更复杂的解析器将文本处理为内部表示，并且只能间接访问数据值。

实体的嵌套（例如对象包含对象）产生层次结构，这与 XML 非常相似，但 JSON 还提供了数组，这在 XML 中没有直接等价物。与 XML 一样，JSON 文件可以用简单的文本编辑器打开和编辑。通过合理使用空白字符可以提高人类可读性，但也有专门的、对 JSON 结构敏感的编辑器可用。JSON 文件通常比相同数据的等效 XML 表示更紧凑。

XML 和 JSON 之间的另一个区别是数据类型的方法。XML 像 SQL 一样，拥有可在模式中指定的广泛数据类型。JavaScript 是一种动态类型语言，这延续到了 JSON 中，JSON 只有三种标量数据类型：字符串、数字和布尔值（加上 null，像 SQL 一样，表示值的缺失）。数字可以是整数或浮点数，布尔值为 true 或 false。

## JSON 支持与 SQL/JSON

JSON 支持在许多语言中均可用，不仅限于 JavaScript。一旦 JSON 文件被加载到所选语言中，即可使用该语言的标准功能以常规方式对数据执行操作，例如遍历集合的成员。从加载 JSON 文件创建的对象结构中提取数据需要使用 JavaScript、Python、C# 或正在使用的任何宿主语言编写代码。严格来说，JSON 指的是文本格式，因此一旦被加载，它就不再是 JSON，而是变成了适合该语言的某种结构。语法可能因语言而异，单引号与双引号的约定可能不同，等等。数据操作通常是在该内部结构上进行，而非在 JSON 文本上。每种语言也都会提供某种函数来执行反向过程，以输出内部结构的文本表示。不同语言可能会通过在输出中引入额外的空白字符而略微改变格式。这不会改变数据，但意味着如果从一种编程语言迁移到另一种，结果可能不完全相同。

### JSON Schema

与 XML 类似，JSON 文件可以使用 Schema 进行精确描述。JSON Schema 规范描述了 JSON 文档的结构、约束和验证规则。JSON Schema 本身采用 JSON 格式编写。它使用 JSON 对象来描述其验证的数据结构。这意味着 JSON Schema 文档本身也可以被验证。可以定义对象的预期属性，每个属性拥有自己的验证规则和数据类型。这包括数值属性的最大值和最小值、字符串的最大长度和最小长度、正则表达式模式，以及电子邮件或 URL 等特殊格式。数组属性可以指定数据类型以及最大和最小项目数。JSON Schema 还包含许多此处不再赘述的其他特性。该规范会持续审查和更新，且免费开放获取。有许多工具可用于针对特定 Schema 验证 JSON、生成 JSON Schema、从 Schema 生成代码等。与 XML Schema 一样，我们在此不深入探讨完整细节。

### JSON 数据处理示例

为了说明 JSON 的通用特性，我们可以使用之前在 Listing 16.1 中作为 XML 示例介绍的电影信息。Listing 16.3 以 JSON 格式展示了相同信息。`movies` 对象包含一个数组（列表），其中存放单个电影。数组项通过索引访问，因此第一部电影是 `movies[0]`（数组索引从零开始）。数组中的每个电影项都是一个对象，包含 `title`、`director` 等属性。属性本身也可以是对象或数组，例如 `stars` 属性包含一个 `star` 对象列表。对象属性可通过键名访问。

![Listing 16.3 Movie information in JSON.](img/f16-08p1-9780443237904.jpg)

Listing 16.3 JSON 格式的电影信息。

与 XML 和 XQuery 不同，JSON 没有专门的查询语言。取而代之的是，使用宿主编程语言的通用特性来处理数据。我们需要记住，一旦 JSON 文件被加载，它就不再是 JSON，而是变成了在宿主语言上下文中有意义的结构。为了提供提取所需数据值的具体示例，我们可以使用与之前 XML 示例中相同的查询，如 Table 16.2 所示。此处我们将使用 Python 来表达查询，但其他语言遵循类似的方法。第一步是在预置的 `json` 库帮助下，将 JSON 文件加载到 Python 字典中。

```
import json
# Open JSON file
theFile = open('movies.json')
# load JSON object into Python dictionary
data = json.load(theFile)
```

```
# Iterate over the json object
for item in data['movies']:
    # code fragment goes here
```

现在我们可以遍历字典内容以提取（并在本例中打印）所需数据。Table 16.6 中的代码片段假定直接位于上述 Python 代码之后。

## Table 16.6

Python 代码片段示例。

| ![t16-06-9780443237904](img/t16-06-9780443237904.jpg) |

---

在某些方面，JSON 文件（及其加载和处理该文件的相应程序）可被视为一个小型数据库，尽管可能缺乏完整数据库系统所期望的许多特性，如事务、并发控制等。然而，JSON 格式已被证明极其有用，以至于它被用作完整数据库系统的基础，通常称为`文档数据库`。这些通常被归类为一种“NoSQL”数据库，将在 Chapter 17 中更详细地讨论。

## SQL/JSON

鉴于 JSON 的广泛使用，SQL 标准需要扩展以适应它，就像之前适应 XML 一样。SQL:2016 支持将 JSON 作为文本存储在基于字符的列中（通常为 `varchar`）。由于时间限制，未能完全定义 JSON 作为一种数据类型，但这在 SQL:2023 中已完成，因此数据可以存储在数据类型为 `json` 的列中。多家供应商早已预见到这一点，但他们的解决方案不一定彼此兼容，也不一定兼容 SQL:2023 标准。然而，所有供应商始终坚持遵循 JSON 的标准定义。`json` 数据类型有两个直接优势。

1. 值可以自动验证为格式正确的 JSON。像 `varchar` 这样的数据类型本身不理解 JSON 结构，因此需要额外的函数来确认文本代表有效的 JSON 值。

2. 值可以通过将 JSON 文本转换为二进制形式以供内部操作，从而得到更高效的处理，避免了相对昂贵的字符串处理。二进制版本也需要更少的存储空间。

SQL/JSON 数据模型涵盖 SQL/JSON 项和 SQL/JSON 序列。序列是项的有序列表。项可以是以下任意一种：

* SQL/JSON 对象：成员的无序集合，每个成员是一个键值对，其值组件为 SQL/JSON 项。
* SQL/JSON 数组：元素的有序列表，每个元素为 SQL/JSON 项。
* SQL/JSON 标量：具有标准 JSON 类型（字符串、数值或布尔值）或日期时间类型的非空值。
* SQL/JSON null（不同于 SQL null）。

由于结构项（对象和数组）可以嵌套，JSON 文本可以表示任意复杂度的数据。

值可以按常规方式插入 `json` 列。假设我们有以下表定义：

```
create table movies (
    movienr int primary key,
    moviedata json
)
```

此处的主键列仅为方便而包含。我们可以像其他 SQL 数据类型一样，为每部电影使用一行来输入 JSON 数据。

```
insert into movies values (3,
    '{ "title": "The Secret Garden",
         "released": "1987",
         "director": "Alan Grint",
         "stars": [
             { "name": "Gennie James", "gender": "F" },
             { "name": "Barret Oliver", "gender": "M" }
         ]
    }')
```

然而，我们不一定非要以这种方式拆分数据。例如，Listing 16.2 中的所有电影数据都可以作为单个值输入到 `json` 列中。
