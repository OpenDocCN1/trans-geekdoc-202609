

如果触发了消息事件，则表示服务器已向客户端发送数据。处理该事件的函数接收一种数组，实际的服务器信息位于 data 键之后。以下代码以简洁且无痛的方式在模态消息窗口中显示此内容：

```
ws.onmessage = function(e) {
    alert(e.data);
}
```

清单 28.5 展示了一个稍微扩展的示例：如果你在文本输入字段中输入一些内容并点击按钮，那么你的输入将被发送到 WebSocket 服务器，并且返回结果会被显示（理想情况下应为相同的文本）。图 28.7 展示了它在浏览器中的工作方式。

```
<!DOCTYPE html>
<html>
<head>
<title>WebSockets</title>
<script>
var ws = new WebSocket("ws://127.0.0.1:12345");
ws.onmessage = (e) => {
    alert("Data from server: " + e.data);
}

window.onload = () => {
    document.getElementById("btn").addEventListener("click", (e) => {
        var input = document.getElementById("input").value;
        ws.send(input);
    })
}
</script>
</head>
<body>
<form>
<textarea id="Input"></textarea>
<input type="button" id="btn" value="Send">
</form>
</body>
</html>
```

清单 28.5 带 HTML 和 JavaScript 的 WebSocket 客户端 ("websockets.html")

![](img/ae7820c36e8f24c1623d26668b28e80e_786_0.png)

图 28.7 WebSocket 示例实战

这只是 WebSocket 的初步介绍，也是朝着具有大量 JavaScript 逻辑和高性能实时通信的现代应用迈出的第一步。

## PART VI

## 数据格式

## 第 29 章

XML

*XML 已确立自身作为数据交换的通用标准以及大多数常见描述语言的基础。*

当今是否存在一款软件产品，没有用大字醒目地印上装饰性缩写 XML？除了游戏领域，要找到一款这样的产品可能颇为困难。文字处理器生成 XML，排版程序输出 XML，CMS X 和 Y 以及数据库 Z 均支持可扩展标记语言。

### 29.1 准备工作

本章的准备工作不仅包括安装，还包括在开头对 XML 的简要介绍。如果你已经熟悉它，可以轻松跳过。这将有助于其他所有人理解本章中的示例。然而，为了更深入的介绍，推荐进一步的书籍。

#### 29.1.1 XML 基础

XML 已被 W3C 标准化为一种数据存储格式。其前身是标准通用标记语言（SGML），后者仍由国际标准化组织（ISO）标准化。XML 是 SGML 的一个子集，其特点主要在于规则更严格。

> **注意**
> 
> HTML5 在标准表示法中实际上并非有效的 XML。不过，也可以为 HTML5 选择一种 XML 兼容的表示法：XHTML (http://s-prs.co/v602241)。

#### 格式正确：XML 的规则

XML 文档由标签组成，标签是尖括号内的命令。数据被封装在标签内。标签也可以被赋予属性。到目前为止，这都与 HTML 类似。在 XML 中，标签的名称不是预定义的；相反，名称应描述数据内容。然而，对于标签和 XML 文档特别是如何结构化，是有规则的。如果 XML 文档遵循所有这些规则，则被称为格式正确。以下是 XML 文档必须遵守的最重要规则，以使其格式正确：

- XML 区分大小写；因此 `<title>` 与 `<Title>` 或 `<TITLE>` 不同。这对旧派 HTML 开发者来说需要一些时间来适应，因为 HTML 标签过去常被花哨地书写。

- 所有标签必须关闭。如果标签没有内容，也可以使用短形式关闭——即，

```
<delivery date="10.11.2026" />
```

而不是

```
<delivery date="10.11.2026"></delivery>
```

> **注意**
> 如果你想将 HTML 文档转换为 XHTML，则此规则下最常见的问题候选项是 `<br>` 和 `<hr>` 标签，它们随后变为 `<br />` 和 `<hr />`。

- 标签不得交叉嵌套。

```
<delivery><date></delivery></date>
```

因此不允许。

- 属性必须始终有一个值。这意味着

```
<delivery completed />
```

是不可能的，但

```
<delivery arrived="true" />
```

是可能的。

- 属性的值必须始终用引号括起来。

- XML 中的标签名和属性必须以字母或下划线 (_) 开头。所有后续字符可以由字母、数字、连字符和点组成。XML 关键字作为名称组件被禁止；你应该避免使用冒号，因为它用于命名空间。

- XML 文档只能有一个根元素。这必须包含所有其他标签。

- 文档需要 XML 标签，也称为 XML 声明。它包含 XML 版本和所使用的字符集。此处的标准是 UTF-8。

以下清单展示了一个格式正确文档的示例。

```
<?xml version="1.0" encoding="UTF-8" ?>
<products>
<product>
<title>Vacuum cleaner XY</title>
<price currency="Euro">4.80</price>
</product>
</products>
```

清单 29.1 一个格式正确的 XML 文档 ("wellformed.xml")

### 有效：DTD 和架构

格式正确的 XML 文档是使用 XML 实现（例如在 PHP 中）的基本要求。但是，XML 文档可以满足另一个标准：它可以是有效的。这里的有效是指 XML 文档遵循预定义的结构。该结构可以使用两种技术来定义：

- 文档类型定义 (DTD)
- XML 架构定义 (XSD)

这两项标准均由 W3C 发布。DTD 的功能范围稍小（例如，它不支持内容的不同数据类型）并且是一种不基于 XML 的独立语言。另一方面，DTD 更古老且相当简单。它至今仍在使用，例如，用于 W3C 指定的 HTML 和 XHTML 文档类型。但是，HTML5 没有明确的 DTD。

XSD 消除了 DTD 的缺点：该标准基于 XML 并提供了大量更多选项。W3C 的所有较新的基于 XML 的标准，例如 SOAP（用于 Web 服务），都在 XSD 中定义。

**注意**

如果你创建自己的文档结构，为其编写 DTD 或架构是有意义的。这样更容易确定不同文档是否具有相同的结构。即使合并不同文档，你也拥有更多控制权。然而，DTD 和架构对于在 PHP 中使用 XML 并不是决定性的。无论 XML 文档是否经过验证，都可以访问它。PHP 中验证直接出现的一个地方是一个用于 DTD 验证的 PEAR 包。库 libxml 也可以验证，并且还理解 RELAX NG，这是一种替代架构语言。然而，PHP 的基本 XML 库也支持验证。

### 命名空间

标签可以被分配到特定的命名空间。在合并多个 XML 文档时，命名空间特别有用。例如，<price> 标签在不同文档中可以具有完全不同的功能。如果它属于一个命名空间，这将确保清楚涉及哪种格式。

### XSLT

可扩展样式表语言转换（XSLT）是 XSL 的一种子语言。XSL 为 XML 文档定义样式。XSLT 用于转换 XML 文档——因此其名称中有“转换”一词。转换可以是横向的——即从一种 XML 格式转换为另一种——也可以是纵向的——即 XML 变为 HTML5 或 JSON 等用于结构化数据的输出格式。

XSLT 使用所谓的模板。为标签指定一个模板。要为标签输出的代码位于模板内部。更深层嵌套的信息通过嵌套模板实现。

清单 29.2 显示了一个简单示例，它将清单 29.1 中的 XML 文件转换为 HTML。

```
<?xml version="1.0" encoding="UTF-8" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
version="1.0">
<xsl:output indent="yes" method="html" />

<xsl:template match="/">
<xsl:apply-templates />
</xsl:template>

<xsl:template match="products">
<html>
<head>
<title>Products</title>
</head>
<body>
<table align="center" width="500" border="1">
<tr>
<th>Product</th>
<th>Price</th>
</tr>
<xsl:apply-templates select="product" />
</table>
</body>
</html>
</xsl:template>

<xsl:template match="product">

