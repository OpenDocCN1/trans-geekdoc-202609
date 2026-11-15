

更有趣的是构建 JSON 结构元素、对象和数组的函数。构造函数可以嵌套，因此我们可以构建任意复杂度的 JSON 值。这些函数在表 16.8 中进行了总结。

表 16.8 SQL/JSON 结构构造函数。

| 运算符 | 功能 |
| :--- | :--- |
| json_object() | 从给定的名称-值对列表创建一个 SQL/JSON 对象 |
| json_array() | 从给定的值列表创建一个 SQL/JSON 数组 |
| json_objectagg() | 从给定的行集合创建一个 SQL/JSON 对象 |
| json_arrayagg() | 从给定的行集合创建一个 SQL/JSON 数组 |

这些函数有许多选项，我们将通过示例探讨其中一些选项。图 16.4 中的关系表显示了有关代理及其项目分配的一些数据。SQL 数据类型中，员工编号和 rate 为 int，其他列为 varchar。空格表示 SQL null。我们假设，最终我们希望创建一个单个 JSON 对象，其中包含每个代理的单独对象，包括他们可能拥有的任何项目分配。

**代理：**

| 编号 | 名 | 姓 | 工作电话 | 家庭电话 | 办公室 |
|---|---|---|---|---|---|
| 101 | Alice | Andrews | 222-1234 | 222-9876 | Boston |
| 232 | Bob | Brown | 555-6789 | | Portland |
| 397 | Carol | Codd | 777-4321 | 777-6789 | Durham |
| 468 | Dave | Dunk | | | |

**项目：**

| 员工编号 | 项目名称 | 费率 |
|---|---|---|
| 101 | Mallard | 1 |
| 101 | Grebe | 2 |
| 232 | Grebe | 3 |
| 232 | Plover | 1 |
| 232 | Bittern | 2 |

图 16.4 代理和项目数据。

创建对象非常简单。以下查询定义了一个带有员工编号和办公室成员的对象结构，然后将其应用于 Agent 表的每一行。

```
select json_object('empNr' value nr, 'office' value office) from Agent
```

结果：

```
{"empNr": 101, "office": "Boston"}
{"empNr": 232, "office": "Portland"}
{"empNr": 397, "office": "Durham"}
{"empNr": 468, "office": null}
```

一些 json_object 的实现将 value 关键字替换为逗号。结果中一个丑陋的特征是最后一个对象中的 null。更自然的 JSON 表示将完全省略此成员。SQL/JSON 定义了一个可选的 absent on null 子句来实现此目的，但并非所有实现都支持它。我们可能能够通过基于域知识提供更有意义的内容来找到变通方法。例如，如果我们知道 Dave Dunk 没有记录办公室的原因是他经常移动，因此他的办公地点是变动的，我们可以替换掉 null。

```
select json_object('empNr', nr,
'office', case when office is not null then office else 'varies' end)
from Agent
```

结果：

```
{"empNr": 101, "office": "Boston"}
{"empNr": 232, "office": "Portland"}
{"empNr": 397, "office": "Durham"}
{"empNr": 468, "office": "varies"}
```

显而易见，此查询可以扩展以包含名和姓的单独成员，但另一种方法是创建一个 name 成员，其中包含每个名称组件的对象。这可以通过在 name 成员中嵌套其他 json_object 构造函数来完成。

电话信息稍微复杂一些，因为该成员不是单值的。我们假设需要一个数字列表，每个数字由一个对象表示。可以通过以下方式将对象构造函数嵌套在数组构造函数中来生成它。

```
select json_array( json_object('type' value 'home', 'number' value homePhone),
json_object('type' value 'work', 'number' value workPhone) )
from Agent
```

结果：

```
[{"type": "home", "number": "222-9876"}, {"type": "work", "number": "222-1234"}]
[{"type": "home", "number": null}, {"type": "work", "number": "555-6789"}]
[{"type": "home", "number": "777-6789"}, {"type": "work", "number": "777-4321"}]
[{"type": "home", "number": null}, {"type": "work", "number": null}]
```

要整合此信息，我们可以在前面的对象中引入一个 phones 成员，并在其中嵌套上述数组构造。我们与之前一样存在 null 问题。如果 absent on empty 子句不可用，我们可以创建一个更复杂的 SQL 查询来从 JSON 结果中删除 null 成员，但就当前目的而言，我们将接受这些 null。

迄今未介绍的函数是对象聚合和数组聚合构造函数。我们可以使用 Project 表来说明这些函数。json_objectagg 函数需要一个键值对，如以下示例所示：

```
select empNr, json_objectagg(projName, rate)
from Project group by empNr
```

结果：

```
101 {"Grebe": 2, "Mallard": 1}
232 {"Grebe": 3, "Plover": 1, "Bittern": 2}
```

在此处，每个组生成的对象都有一个组中每个项目的成员。这与 json_object 不同，json_object 会为每个项目提供一个单独的对象。

创建聚合数组的工作方式类似，但只需要识别要列出的值。这会给出一个数组，其中包含组中每个项目的一个元素。

```
select empNr, json_arrayagg(projName)
from Project group by empNr
```

结果：

```
101 ["Mallard", "Grebe"]
232 ["Grebe", "Plover", "Bittern"]
```

为了实现全面 Agent 对象的目标，json_arrayagg 构造函数看起来最合适。这可以通过将其嵌套在主对象结构的 projects 成员中，集成到更大的查询中。

为了创建所需的最终 JSON 结构，包含上述元素的行可以聚合在一起，以在一个外围对象中形成代理列表，如以下查询所示。

```
select json_object ('Agents', json_arrayagg(
    json_object(
    'empNr' value nr,
    'name', json_object('given' value givenName, 'family' value familyName),
    'phone', json_array(
    json_object('work' value workPhone),
    json_object('home' value homePhone))),
    'office', case when office is not null then office else 'varies' end,
    'projects', (select json_arrayagg(projName)
    from Project p where p.empNr = a.nr group by p.empNr))))
from Agent a
```

以下清单显示了组合结果，稍作格式化以使结构更加明显。

```
{"Agents": [
{"empNr": 101,
"name": {"given": "Alice", "family": "Andrews"},
"phone": [{"work": "222-1234"}, {"home": "222-9876"}],
"office": "Boston",
"projects": ["Mallard", "Grebe"]
},
{"empNr": 232,
"name": {"given": "Bob", "family": "Brown"},
"phone": [{"work": "555-6789"}, {"home": null}],
"office": "Portland",
"projects": ["Grebe", "Plover", "Bittern"]
},
{"empNr": 397,
"name": {"given": "Carol", "family": "Codd"},
"phone": [{"work": "777-4321"}, {"home": "777-6789"}],
"office": "Durham",
"projects": null
},
{"empNr": 468,
"name": {"given": "Dave", "family": "Dunk"},
"phone": [{"work": null}, {"home": null}],
"office": "varies",
"projects": null
}
] }
```

## 16.4 其他标记语言

顾名思义，像 XML 这样的标记语言通过在原始信息中添加某种额外的标记来指示其功能或目的。从历史上看，标记的主要应用在出版行业，在那里它（至今仍）用于显示应对作者文本应用的处理方式，以将其转换为适合打印的正确格式布局。在数据库上下文中，我们可以将标记视为元数据。

与 JSON 精神相近的语言是 YAML。它最初代表“又一种标记语言”，但随后出现了对名称的其他解释。YAML 是 JSON 的超集，带有一些额外功能，并且有可在 YAML 和 JSON 之间双向转换的实用程序。YAML 的主要动机是提供一种比 JSON 更具“人类可读性”的格式，特别是避免大量使用括号（圆括号、方括号或花括号）。嵌套可以通过使用空格以类似于 Python 语言的方式缩进项目来指示。这减少了常见键盘错误的可能性。

YAML 的一些简要特性包括：

- 项目通过在父节点下方缩进子节点来嵌套。
- 键值对由冒号分隔，但不需要引号。
- 列表中的新项目由连字符指示。
- 可以自由使用包括字符串、数字和布尔值在内的标量值。
- 字符串不需要引号，但如果需要可以使用（例如，如果需要将数字视为字符串）。
- 注释可以用井号字符指示（转换为 JSON 时会剥离注释）。
- 提供了其他命令来控制输出中文本的布局（例如，抑制换行）。

