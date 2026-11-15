

与讨论 XQuery 时使用的示例类似。如果此 xmltable 函数调用包含在 select 语句中，则传递的值可以从表中的合适 XML 列中选择。

```
xmltable ('//movies'
passing movieXML
columns
"Seqno" for ordinality,
"MovieNr" int path '@movieNr',
"Movie Name" varchar (50) path 'title',
"Release Year" char(4) path 'released'
"Director" varchar(50) path 'director' )
```

生成的表将具有以下形式，并且可以像通过其他方式生成的表一样进行别名处理等等。

在这种情况下，自动生成的 SeqNo 列和检索的 MovieNr 列中的值巧合地相同。如果 XML 数据的顺序不同，SeqNo 列将保持不变，但 MovieNr 列（以及其他检索的列）将反映 XML 元素的顺序。

| 序号 | 电影编号 | 电影名称 | 发行年份 | 导演 |
|---|---|---|---|---|
| 1 | 1 | Cosmology | 2006 | Lee Lafferty |
| 2 | 2 | Kung Fu Hustle | 2004 | Stephen Chow |
| 3 | 3 | The Secret Garden | 1987 | Alan Grint |
| 4 | 4 | The Secret Garden | 1993 | Agnieszka Holland |
| 5 | 5 | The Da Vinci Code | 2006 | Ron Howard |

## 练习 16.2

以下架构展示了数据库的一部分，该数据库保存了关于维修技术人员及其有资格维修的装配类型的信息。不同的技术人员可能擅长维修不同的装配。

![](img/1344db3eba3d550e6edb009556fcd95c_876_0.png)

- 1. 使用现代数据库系统提供的功能，将维修数据库的内容转换为三个 XML 文档，即每个表一个 XML 文档。

- 2. 使用 XPath 和 XQuery 表达式，利用一个或多个 Technician、Competence 和 Assembly XML 文档生成以下结果。将结果生成 XML 文档或 XML 片段均可。

    - (a) 列出所有主管，并在每个主管下列出向他们汇报的所有技术人员。Supervisor 和 Technician 元素应将 empNr 作为属性，并将 'firstName' || ' ' || 'lastName' 的连接作为元素内容。

    - (b) 以层级形式列出装配（即，顶级装配将包含子装配，子装配又包含其自身的子装配，以此类推）。将 assemblyCode 作为每个元素的内容显示。

    - (c) 列出所有复杂度代码为 5 或更高且带有报告的装配。按 complexityNr（降序）和 assemblyCode（升序）对列表进行排序。

    - (d) 对于每个技术人员，列出他们有资格维修的装配类型。将每个装配的 complexityNr 作为属性包含在内。

    - (e) 列出所有技术人员，并在每个技术人员下附带 certificationRefs 元素。在技术人员没有 certificationRef 的情况下，使用 xsi:nil = "true"。对于存在的每个 certificationRef，显示相关的 assemblyCode。

    - (f) 列出没有任何技术人员有资格维修的所有装配。

- 3. 使用现代数据库系统提供的功能，将问题 2 中查询产生的每个 XML 结果转换为关系表。

## 16.3 JSON

JSON 代表 JavaScript 对象表示法，清晰地描述了其起源和功能。与 XML 类似，JSON 是一种基于文本的格式，使不同系统之间的数据交换变得非常容易。每个系统可以以其自身的内部形式存储数据以实现高效处理，但这些内部表示不需要相同。JSON 最初由 Douglas Crockford 在 2000 年代初定义为一种数据交换格式，但随后被广泛采用为表达数据结构的便捷方式，并得到大多数编程语言的支持。一个早期的“信息性”标准（Crockford, 2006）之后是 2013 年的第一个国际标准（ECMA-404）。JSON 的语法非常简单，是 JavaScript 语法的略作修改的版本。主要有两种结构元素。

- 1. 键值对集。冒号字符分隔键和值，如下所示：
- “givenName” : “Alan”,
- “familyName” : “Turing”

键由双引号括起来。连续项之间用逗号字符分隔，集合由大括号括起来。集合中项的顺序无关紧要。这种集合因其 JavaScript 起源而被称为“对象”。

- 2. 包含有序值集合的数组。值之间用逗号字符分隔。数组由方括号括起来。

引号外的空白字符（空格、制表符、换行符等）被忽略。值可以是字符串、数字、布尔值、特殊值 null，或结构化类型（对象和数组）之一。大致准则是：数组用于相似项的集合，对象用于单个项目的属性集合。

JSON 语法与 JavaScript 略有不同，JavaScript 不需要带引号的键，并允许其他可能的值，例如函数，但整体风格相似。这使得 JavaScript 中的 JSON 处理非常直接，该语言具有处理 JSON 文本的内置函数。JSON.parse() 将文本表示转换为 JavaScript 对象结构，JSON.stringify() 将 JavaScript 对象结构转换为文本。其他面向对象语言也提供类似功能。JSON 中一个明显的缺失是任何表达注释的能力。这是其设计者的刻意选择，但一直是许多用户的沮丧来源。

这种直接处理相对于 XML 是一个明显的优势，XML 需要更复杂的解析器将文本处理为内部表示，并且只能间接访问数据值。

实体的嵌套（例如，对象包含对象）以与 XML 非常相似的方式产生层级结构，但 JSON 还提供数组，这在 XML 中没有直接等价物。与 XML 类似，JSON 文件可以用简单的文本编辑器打开和编辑。合理使用空白字符有助于提高人类可读性，但也可使用对 JSON 结构敏感的专用编辑器。JSON 文件通常比同等数据的 XML 表示更紧凑。

XML 和 JSON 之间的另一个区别在于数据类型的处理方式。XML（如同 SQL）在架构中指定了广泛的数据类型范围。JavaScript 是一种动态类型语言，这一点也体现在 JSON 中，JSON 只有三种标量数据类型：字符串、数字和布尔值（加上 null，它如同 SQL 一样表示值的缺失）。数字可以是整数或浮点数，布尔值为 true 或 false。

许多语言（不仅仅是 JavaScript）都提供 JSON 支持。一旦 JSON 文件加载到所选语言中，就可以使用该语言的标准功能以通常方式对数据进行操作，例如遍历集合的成员。从加载 JSON 文件创建的对象结构中提取数据需要使用正在使用的宿主语言（如 JavaScript、Python、C# 等）编写代码。严格来说，JSON 指的是文本格式，因此一旦加载，它就不再是 JSON，而是一种适合该语言的结构。语法可能因语言而异，单引号和双引号可能有不同的约定，等等。数据操作通常在该内部结构上进行，而不是在 JSON 文本上。每种语言还会提供一些函数来执行逆过程，以输出内部结构的文本表示。不同语言可能通过在输出中引入额外的空白字符来稍微更改格式。这不会更改数据，但这意味着如果在不同编程语言之间移动，结果可能不完全相同。

与 XML 类似，JSON 文件可以使用架构精确描述。JSON Schema 规范描述了 JSON 文档的结构、约束和验证规则。JSON Schema 本身采用 JSON 格式编写。它使用 JSON 对象来描述其验证的数据结构。这意味着 JSON Schema 文档本身也可以被验证。可以定义对象的预期属性，每个属性都有其自身的验证规则和数据类型。这包括数值属性的最大值和最小值、字符串的最大长度和最小长度、正则表达式模式，以及 email 或 URL 等特殊格式。数组属性可以指定数据类型以及项目的最大数量和最小数量。JSON Schema 包含许多我们此处不予介绍的其他功能。该规范经过持续审查和更新，且可免费获取。有许多可用于根据特定架构验证 JSON、生成 JSON 架构、从架构生成代码等的工具。与 XML 架构一样，此处不深入介绍完整细节。

为了说明 JSON 的一般特性，我们可以使用之前在清单 16.1 中作为 XML 示例介绍过的电影信息。清单 16.3 以 JSON 格式显示了相同的信息。movies 对象包含一个单个电影数组（列表）。数组项通过索引访问，因此第一部电影是 movies[0]（数组索引从零开始）。数组中的每个电影项都是一个对象，包含标题、导演等属性。属性本身也可以是对象或数组，例如 stars 属性包含星对象列表。可以通过键名访问对象属性。

```
{
 "movies": [
 {
 "movieNr": 1,
 "title": "Cosmology",
 "released": "2006",
 "director": "Lee Lafferty"
 },
 {
 "movieNr": 2,
 "title": "Kung Fu Hustle",
 "released": "2004",
 "director": "Stephen Chow",
 "stars": [
 {
 "name": "Stephen Chow", "gender": "M"
 }
 ]
 },
 {
 "movieNr": 3,
 "title": "The Secret Garden",
 "released": "1987",
 "director": "Alan Grint",
 "stars": [
 {
 "name": "Genni James", "gender": "F" },
 {
 "name": "Barret Oliver", "gender": "M" }
 ]
 }
 ]
},
```

