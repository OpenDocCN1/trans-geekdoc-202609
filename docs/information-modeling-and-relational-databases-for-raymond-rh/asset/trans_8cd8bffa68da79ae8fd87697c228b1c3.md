

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

```json
{
  "Agents": [
    {
      "empNr": 101,
      "name": {"given": "Alice", "family": "Andrews"},
      "phone": [{"work": "222-1234"}, {"home": "222-9876"}],
      "office": "Boston",
      "projects": ["Mallard", "Grebe"]
    },
    {
      "empNr": 232,
      "name": {"given": "Bob", "family": "Brown"},
      "phone": [{"work": "555-6789"}, {"home": null}],
      "office": "Portland",
      "projects": ["Grebe", "Plover", "Bittern"]
    },
    {
      "empNr": 397,
      "name": {"given": "Carol", "family": "Codd"},
      "phone": [{"work": "777-4321"}, {"home": "777-6789"}],
      "office": "Durham",
      "projects": null
    },
    {
      "empNr": 468,
      "name": {"given": "Dave", "family": "Dunk"},
      "phone": [{"work": null}, {"home": null}],
      "office": "varies",
      "projects": null
    }
  ]
}
```

## 16.4 其他标记语言

顾名思义，标记语言（如 `XML`）通过向原始信息添加某种额外标记来指示其功能或用途。历史上，标记的主要应用领域是出版业，用于（至今仍用于）指示对作者文本应用的处理方式，以将其转换为适合印刷的排版布局。在数据库语境中，我们可以将标记视为元数据。

一种与 `JSON` 理念相近的语言是 `YAML`。这最初代表 "Yet Another Markup Language"（另一种标记语言），但随后出现了对该名称的其他解释。`YAML` 是 `JSON` 的超集，具有一些额外功能，并且有可用的工具在 `YAML` 和 `JSON` 之间相互转换。`YAML` 的主要动机是提供比 `JSON` 更具 "人类可读性" 的格式，特别是避免大量使用括号（圆括号、方括号或花括号）。可以通过缩进项目来表示嵌套，类似于使用空格的 `Python` 语言。这减少了常见键盘错误的可能性。

`YAML` 的一些简要特性包括以下内容：

*   通过将子节点缩进到其父节点下方来嵌套项目。
*   键值对由冒号分隔，但不需要引号。
*   列表中的新项目由连字符指示。
*   标量值（包括字符串、数字和布尔值）可以自由使用。
*   字符串不需要引号，但如果需要可以使用（例如，如果需要将数字视为字符串处理）。
*   可以用井号字符表示注释（转换为 `JSON` 时注释会被剥离）。
*   提供了额外命令来控制输出中文本的布局（例如，抑制换行）。

以下显示了我们电影数据示例的简略版本，以 `YAML` 表示。

```yaml
--- # This is a YAML document
movies:
  - movieNr: 1
    title: Cosmology
    released: '2006'
    director: Lee Lafferty
  - movieNr: 2
    title: Kung Fu Hustle
    released: '2004'
    director: Stephen Chow
    stars:
      - name: Stephen Chow
        gender: M
  - movieNr: 5
    title: The Da Vinci Code
    released: '2006'
    director: Ron Howard
    stars:
      - name: Tom Hanks
        gender: M
      - name: Ian McKellen
        gender: M
      - name: Audrey Tautou
        gender: F
...
```

`YAML` 是在需要显式表示数据结构的相对较短文档中的热门选择。两个例子是包含应用程序数据的配置文件和结构化消息的交换。它不广泛用于大型数据集合。其易用性部分归因于对数据值背后意图的自动化决策，这可能导致意外后果。例如，某些解析器可能将未加引号的值 `No` 解释为布尔值 `false`，这可能并非原始意图。

最熟悉的标记语言可能是 `HTML`，用于定义网页结构。与 `XML` 不同，`HTML` 中的标签是预定义的，并在 `HTML` 标准中定义了特定含义。在 Web 使用的早期，`HTML` 也曾被用作识别数据结构某些方面的一种相当薄弱的方法，但这显然是令人不满意的。与 `XML` 一样，`HTML` 对作者来说可能显得笨拙和别扭，因此开发出了几种替代方案。一些例子包括以下内容。

*   可爱地命名为 `Markdown` 的轻量级语言，用于向文本文档添加格式指示符。标记文档可用于各种应用程序以生成发布格式（如 `PDF`）并转换为其他格式（如完整的静态网站）。然而，它在表达数据结构方面的能力显然有限。
*   `AsciiDoc` 是基于 `XML` 的 `DocBook` 格式的纯文本等价物，用于结构化文档。文档可以简单地使用文本编辑器创建，然后渲染为所需的最终格式，如 `PDF`、`HTML` 等。
*   `MediaWiki` 是另一种为易用性而设计的轻量级语言。顾名思义，它是为创建 Wiki 页面而开发的，也是 `Wikipedia` 的基础。与这类其他语言一样，其文档可以重新处理为许多其他格式，包括 `HTML`。

这些语言的主要目的是定义文档结构，而非数据结构。尽管存在一定程度的重叠，但既然有更好的替代方案可用，就没有迫切需要使用这些语言进行数据描述。因此，我们将不在本章中进一步探讨它们。

## 16.5 XML、JSON 和 ORM

一个值得考虑的问题是，对象角色建模（`ORM`）是否可用于设计 `XML` 模式或 `JSON` 模式，就像它可用于设计关系模式一样。答案当然是 "Yes"（可以），但有一些在关系情况中不相关的额外考量因素。

如前所述，`ORM` 模型可以用 `XML` 表示，这确实是 `NORMA` 工具使用的默认文件格式。大致结构可概述如下：

```xml
<ORMModel>
  <Objects>
    <Object id="123" ...> </ObjectType>
    <Object id="456" ...> </ObjectType>
    ...
  </Objects>
  <Facts>
    <Fact id="321" ...>
      <FactRole id="789" ...> </FactRole>
      <FactRole id="987" ...> </FactRole>
    </Fact>
    ...
  </Facts>
  <Constraints> ... </Constraints>
  ...
  <ORMDiagram> ... </ORMDiagram>
</ORMModel>
```

每个项目都有一个唯一标识符（`UUID`），这些标识符用于关联项目。例如，扮演事实角色的对象可以通过其 `UUID` 从角色实体引用。

虽然此结构捕获了所有 `ORM` 模型细节，但它并未为数据模型提供良好的模板。部分内容（如图表信息）与定义数据结构无关，且 `*.orm` 文件中的项目（如对象类型和事实类型）的表示方式旨在促进建模操作，而非数据传输。相反，需要的是从 `ORM` 模型到 `XML` 模式的映射，以适应相关数据。

从 `ORM` 模型映射到关系模式在第 11 章中讨论过。在 `Rmap` 过程中只有少数可能的选项，例如如何处理子类型。该过程在很大程度上是自动的，两个不同的开发人员映射相同的 `ORM` 模型通常会产生相同的关系模式。然而，对于 `XML` 情况则不同。

