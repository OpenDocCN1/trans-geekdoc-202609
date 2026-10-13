

# 另一个函数，`xmltable`

另一个函数 `xmltable` 提供了一种将 XQuery 结果集成回 SQL 的有用方法。通常，XQuery 表达式会返回一个序列，但通过使用 `xmltable`，我们可以执行一个 XQuery 表达式并将值作为表返回。返回的表可以包含任何 SQL 数据类型的列，包括 XML，尽管插入到 `xmltable` 中 `xml` 列的值必须是格式良好且具有单一根节点的。基本语法如下：

```
xmltable ( [ xmlnamespaces ( namespace-declaration-item [,…] ), ] row-pattern [ passing [ { by ref | by value } ] XMLquery-argument [,…] ]columns { { colname for ordinality | colname datatype [ by ref | by value ] path column-pattern} [,…] } )
```

row-pattern 定义一个生成元素序列的表达式。该序列中的每个元素将成为结果表中的一行。`columns` 子句列出列定义以及用于在 row-pattern 的每个元素中查找列值的路径表达式。`for ordinality` 选项创建一个带有自动序号引用的列，因此第一行是 1，第二行是 2，依此类推。此处显示了一个示例。假设我们有一个名为 `movieXML` 的 `xml` 值，其内容与我们在讨论 XQuery 时使用的示例类似。如果此 `xmltable` 函数调用包含在 `select` 语句中，则传递的值可以从表中合适的 xml 列中选择。

```
xmltable (‘//movies'passing movieXMLcolumns “Seqno” for ordinality, “MovieNr” int path ‘@movieNr', “Movie Name” varchar (50) path ‘title', “Release Year” char(4) path ‘released' “Director” varchar(50) path ‘director' )
```

生成的表将具有以下形式，并且可以像通过其他方式生成的表一样进行别名设置等操作。

| ![u16-05-9780443237904](images/B9780443237904000207/u16-05-9780443237904.jpg) |

| --- |

在这种情况下，自动生成的 SeqNo 列中的值和检索到的 MovieNr 列中的值巧合地相同。如果 XML 数据顺序不同，SeqNo 列将保持不变，但 MovieNr 列（和其他检索到的列）将反映 XML 元素的顺序。

## 练习 16.2

以下模式显示了一个数据库的一部分，该数据库存储有关维修技术人员及其擅长维修的组件类型的信息。不同的技术人员可能擅长维修不同的组件。

![](images/B9780443237904000207/u16-01-9780443237904.jpg)

1.  利用现代数据库系统提供的功能，将维修数据库的内容转换为三个 XML 文档，即每个表对应一个 XML 文档。

2.  使用 XPath 和 XQuery 表达式生成以下结果，使用 Technician、Competence 和 Assembly XML 文档中的一个或多个。将结果生成为 XML 文档或 XML 片段。

    1.  (a) 列出所有主管，并在每个主管下列出所有向其汇报的技术人员。Supervisor 和 Technician 元素应将 empNr 作为属性，将 `firstName` || ` ` || `lastName` 的连接作为元素内容。

    2.  (b) 以层次结构形式列出组件（即顶级组件将包含子组件，子组件将包含其自己的子组件，以此类推）。将 assemblyCode 作为每个元素的内容显示。

    3.  (c) 列出所有复杂度代码为 5 或更高且有报告的组件。按 complexityNr（降序）和 assemblyCode（升序）对列表进行排序。

    4.  (d) 对于每个技术人员，列出他们擅长维修的组件类型。将每个组件的 complexityNr 作为属性包含在内。

    5.  (e) 列出所有技术人员，并在每个技术人员下包含一个 certificationRefs 元素。在技术人员没有 certificationRef 的情况下使用 `xsi:nil = “true”`。对于存在的每个 certificationRef，显示相关的 assemblyCode。

    6.  (f) 列出没有技术人员擅长维修的所有组件。

3.  利用现代数据库系统提供的功能，将问题 2 中查询的每个 XML 结果转换为关系表。

## 16.3 JSON

JSON 代表 JavaScript Object Notation，这非常清楚地描述了它的起源和功能。与 XML 一样，JSON 是一种基于文本的格式，使得在不同系统之间交换数据变得非常容易。每个系统可以将数据以其自己的内部形式存储以实现高效处理，但这些内部表示不需要相同。JSON 最初由 Douglas Crockford 于 2000 年代初定义为一种数据交换格式，但随后被广泛采用为一种表达数据结构的便捷方式，并受到大多数编程语言的支持。早期的“信息性”标准（[Crockford, 2006](#Ch016_831-873_B9780443237904000207.xhtml#bb0260)）之后，于 2013 年发布了第一个国际标准 (ECMA-404)。

JSON 的语法非常简单，是 JavaScript 语法的略微修改版本。有两个主要的结构元素。

1.  键值对集合。冒号字符分隔键和值，如：

    ```
     “givenName” : “Alan”, “familyName” : “Turing”
    ```

    键用双引号括起来。连续的项用逗号字符分隔，整个集合用大括号括起来。集合中项的顺序无关紧要。由于其 JavaScript 起源，此类集合被称为“对象”。

2.  包含有序值集合的数组。值用逗号字符分隔。数组用方括号括起来。

引用值之外的空白字符（空格、制表符、换行符等）会被忽略。值可以是字符串、数字、布尔值、特殊值 null，或两种结构化类型（对象和数组）之一。大体准则是数组用于相似项的集合，对象用于单个项的属性集合。

JSON 语法与 JavaScript 略有不同，后者不要求键加引号，并允许其他可能的值，如函数，但总体风格相似。这使得在 JavaScript 中处理 JSON 非常简单，该语言内置了处理 JSON 文本的函数。`JSON.parse()` 将文本表示转换为 JavaScript 对象结构，`JSON.stringify()` 将 JavaScript 对象结构转换为文本。其他面向对象语言也提供类似功能。JSON 的一个明显缺失是表达注释的任何能力。这是其设计者的有意选择，但一直是许多用户沮丧的来源。

与 XML 相比，这种简单直接的处理是一个显著优势，XML 需要更复杂的解析器将文本处理为内部表示，并且只能间接访问数据值。

实体的嵌套（例如对象包含对象）产生层次结构，这与 XML 非常相似，但 JSON 还提供了数组，这在 XML 中没有直接等价物。与 XML 一样，JSON 文件可以用简单的文本编辑器打开和编辑。通过合理使用空白字符可以提高人类可读性，但也有专门的、对 JSON 结构敏感的编辑器可用。JSON 文件通常比相同数据的等效 XML 表示更紧凑。

XML 和 JSON 之间的另一个区别是数据类型的方法。XML 像 SQL 一样，拥有可在模式中指定的广泛数据类型。JavaScript 是一种动态类型语言，这延续到了 JSON 中，JSON 只有三种标量数据类型：字符串、数字和布尔值（加上 null，像 SQL 一样，表示值的缺失）。数字可以是整数或浮点数，布尔值为 true 或 false。

