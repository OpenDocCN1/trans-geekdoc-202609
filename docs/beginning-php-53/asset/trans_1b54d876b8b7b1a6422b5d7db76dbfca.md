

通过使用有效的 XML 文档，互不相识的应用程序仍然可以有效通信——它们只需交换 XML 文档，并理解用于验证这些文档的 DTD 或 XSD 的含义。这是使 XML 如此强大的主要特性之一。

## XML 文档的主要部分

一般而言，格式正确的 XML 文档可能包含以下内容：

- 文档顶部的 XML 声明，可能包含字符编码声明。这个声明是个好主意，但不是强制性的。如果未提供 XML 声明，通常使用版本 1.0。如果未指定字符编码，则假定为 UTF-8。例如：
  `<?xml version="1.0" encoding="UTF-8"?>`

- 可选的 DTD 或 XSD，或者对其中一个的引用（如果它们存储在外部）。这必须出现在文档的根元素之前。例如，这是对外部 DTD 的引用：
  `<!DOCTYPE stockList SYSTEM "http://www.example.com/dtds/stockList.dtd">`

- 所有 XML 文档都必须包含一个且只有一个根元素。该元素通常包含一个或多个子元素，每个子元素可选地具有一个或多个属性。元素可以在其开始标记和结束标记之间包含其他子元素或数据，也可以为空。

- XML 文档可能包含其他组件，例如处理指令（PI，为特定应用程序提供机器指令）；CDATA 节，可包含普通 XML 数据中不允许的特殊字符；符号表示法；注释；实体引用（特殊字符等实体的别名）；文本；以及实体。本章稍后将介绍其中一些组件。

下面是之前使用过的 stockList 示例文档的增强版本，用于说明这些主要部分。首先是 XML 声明：

```
<?xml version="1.0" encoding="UTF-8"?>
```

接下来是定义文档中允许的元素和属性的 DTD 引用：

```
<!DOCTYPE stockList SYSTEM "http://www.example.com/dtds/stockList.dtd">
```

现在根元素开始。请记住，XML 文档中只能有一个根元素：

```
<stockList>
```

根元素包含两个 `item` 子元素。每个子元素本身包含四个子节点。`description` 元素包含 CDATA 节来封装其文本数据，因为数据包含 >、< 和 & 等字符，否则这些字符会被视为标记：

```
<item type="fruit">
    <name>apple</name>
    <unitPrice>0.99</unitPrice>
    <quantity>412</quantity>
    <description><![CDATA[Apples are >>>yummy<<<]]></description>
</item>
<item type="vegetable">
    <name>beetroot</name>
    <unitPrice>1.39</unitPrice>
    <quantity>67</quantity>
    <description><![CDATA[Beetroots are lovely & purple]]></description>
</item>
```

最后，根元素被关闭：

```
</stockList>
```

## XML 语法规则

您现在知道 XML 文档的主要组件是什么。此外，格式正确的 XML 文档必须遵循 XML 规范中的所有其他语法规则，最常见的规则列于此：

- XML 元素被声明为非空（在这种情况下，它们旨在包含数据）或空（在这种情况下，它们不能包含数据）。例如，在 XHTML 中，p（段落）元素是非空的，因为它可以包含文本；而 br（换行）元素是空的，因为它不能包含任何内容。

- 非空元素可以由开始标记和结束标记创建（例如 XHTML 中的 <p> ... </p> 标记）。空元素应使用特殊的空元素标记格式创建（例如 XHTML 中的 <br/> 标记）。与 HTML 不同，您不能有一个不带结束标记的开始标记。

- XML 属性写在非空元素的开始标记内，或写在空元素的空元素标记内，并且必须采用 name="value" 或 name='value' 格式。任何给定元素内的属性名称不能出现多次。例如：
  `<item type="vegetable"> ... </item>`
  `<emptyElement color='red' />`

- XML 元素必须正确嵌套，这意味着任何给定元素的开始标记和结束标记必须位于其内部元素的开始标记和结束标记之外，并位于其封闭元素的开始标记和结束标记之内。例如：
  `<!-- Incorrect nesting -->`
  `<parent><child></parent></child>`
  `<!-- Correct nesting -->`
  `<parent><child></child></parent>`

- 元素名称不能以字符 "xml"、"XML" 或这些字符的任何大小写组合（按此顺序）开头。名称必须以字母、下划线或冒号开头，但在实际中，除非您正在处理 XML 命名空间，否则永远不应该使用冒号。名称区分大小写。字母、数字、连字符、下划线和句点是首字符之后可以使用的有效字符。

- 注释的分隔方式与 HTML 注释相同（<!-- 和 -->）。

## 使用 XML 元素和属性

XML 元素及其属性构成了 XML 文档的层次结构，并包含文档的数据。虽然只能有一个根元素，但每个元素（包括根元素）都可以包含多个元素（通常称为 *子元素*）。此外，您可以拥有多个同名的子元素。

每个 XML 元素可以包含一个或多个属性；但是，任何给定元素内的属性名称只能出现一次。

关于何时使用属性、何时使用子元素来包含数据，存在一些争议。虽然没有绝对的规则，但一个很好的经验法则是：

- 当您可能需要在元素中多次包含同一字段时，请使用子元素。例如，前面描述的 *stockList* 根元素包含多个 *item* 子元素。使用属性无法实现这一点，因为任何给定元素不能有多个同名属性。

- 当您确定数据在元素中仅出现一次时，请使用属性，例如 *item* 元素的 *type* 属性（*item* 可以是水果或蔬菜，但不能同时是两者）。

另一个很好的经验法则是：对核心于元素的数据使用子元素，对外围于元素的数据或唯一标识元素的数据（例如 *id* 属性）使用属性。

## 有效的 XML 文档：DTD 和 XSD

如前所述，有效的 XML 文档是指包含对 DTD（文档类型定义）或 XSD（XML 架构定义）的引用，且其内容既遵循一般 XML 语法规则（即格式正确），也遵循 DTD 或 XSD 中指定的规则（即有效）。前面描述的“股票列表”XML 文档既格式正确又（可能）有效：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE stockList SYSTEM "http://www.example.com/dtds/stockList.dtd">
<stockList>
	<item type="fruit">
		<name>apple</name>
		<unitPrice>0.99</unitPrice>
		<quantity>412</quantity>
		<description><![CDATA[Apples are >>>yummy<<<]]></description>
	</item>
	<item type="vegetable">
		<name>beetroot</name>
		<unitPrice>1.39</unitPrice>
		<quantity>67</quantity>
		<description><![CDATA[Beetroots are lovely & purple]]></description>
	</item>
</stockList>
```

请注意第二行中对外部 DTD URL 的引用。这允许一段软件通过读取 DTD 并确保文档符合 DTD 来验证文档。当然，您可以手动阅读文档并将其与 DTD 中指定的元素、属性和其他文档组件进行比较，但有许多应用程序可以自动将 XML 文档与 DTD 或 XSD 进行验证。并且，由于 DTD 或 XSD 可直接在文档中或在线上获得，这些应用程序在解析文档时可以轻松为您自动执行验证功能。

> 也可以将 DTD 的内容嵌入 XML 文档本身，而非引用外部 DTD。但是，仅当 DTD 较小时才建议嵌入。

DTD 是使用扩展巴克斯-诺尔范式（EBNF）编写的特殊文档，它不是一种 XML 语言，也不如 XML 容易解析。DTD 对 XML 元素、属性、内容等指定约束。

XSD 与 DTD 服务于相同的目的，但使用基于 XML 的 XML Schema 语言编写，因此可以使用 XML 解析器轻松处理。XSD 在定义元素和属性的详细信息（例如数据类型、值范围等）方面也比 DTD 功能强大得多，因此许多 XML 作者更倾向于使用 XSD 而非 DTD。但是，XSD 是一个超出本书范围的复杂主题，因此本章专注于 DTD。

> 如果您对 XSD 感兴趣，可以在 http://www.w3schools.com/Schema/default.asp 上了解更多信息。

## XHTML：DTD 的实际应用示例

如前所述，任何人都可以编写 XML 文档，任何人都可以定义 DTD 或 XSD 来验证 XML 文档。DTD 的一个著名示例是 XHTML，它是重新表述为 XML 的 HTML。XHTML DTD 本质上与现有的 HTML DTD 相似，只是做了非常小的修改，并且它定义了 XHTML 文档中允许的所有元素、属性和其他组件。HTML 与 XHTML 的主要区别在于，XHTML 文档（本质上是 XML 文档）必须符合 XML 规范，而 HTML 文档不需要这样做。

要将 XHTML 文档显示为常规网页，该文档必须格式正确，并且要与 XHTML DTD 进行验证。在接下来的几个部分中，您将查看 XHTML DTD 的一部分，了解如何在 XHTML 文档中引用 DTD，探索 XML 命名空间，并学习如何创建 XHTML 网页。

## XHTML 的 DTD

XHTML 有三个 DTD。它们位于：

- www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd
- www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd
- www.w3.org/TR/xhtml1/DTD/xhtml1-frameset.dtd

