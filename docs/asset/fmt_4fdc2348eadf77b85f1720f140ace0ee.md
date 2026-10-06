
- 使用 XPath 搜索 XML 文档

XML 是数据存储和处理工具的“瑞士军刀”。它小巧、便携，并且几乎可以完成你需要的任何事情（除了打开豆头罐）。

本章将引导你了解使用 PHP 操作 XML 文档的细节，从文档对象模型（简称 DOM）开始。从那里，我们介绍了三个最著名的 XML 技术：XML Schema、XSLT 和 XPath。

### 理解文档对象模型

文档对象模型 (DOM) 定义了 XML 的基本结构。PHP 的最新版本完全按照 W3C 在 `www.w3.org/dom` 发布的 DOM/XML 标准实现。

### 读取 DOM

你可以通过两种方式从 DOM 中提取有用信息：

- 遍历文档树
- 按 ID 或名称进行搜索

要遍历整个文档树，请使用带有通配符字符 (`*`) 的 `getElementsByTagName()` 函数，如下：

```php
$xmlDoc = new DOMDocument("xmlsource.xml");
$nodes = $xmlDoc->getElementsByTagName('*');
foreach( $nodes as $item ) {
    echo $item->getAttribute('name');
}
```

要按标签名搜索，使用相同的代码，但将通配符字符 (`*`) 替换为你搜索的标签名称。变量 `$nodes` 将包含匹配你所搜索标签的节点数组。

如果你在 XML 文档结构中按 ID 划分关键元素，你可以使用 `getElementByID()` 函数进行更精确的搜索。只需将前一个示例中的 `getElementsByTagName()` 函数调用替换为 `getElementByID()` 即可。

### 写入 DOM

你可能发现搜索 DOM 中的特定信息很有用，但当你使用 PHP 写入 DOM 时，它才会真正大放异彩。手动编写 XML 最多也是枯燥的。通过 PHP，你可以指定文档的结构，并让脚本执行将原始数据转换为 XML 的实际工作。PHP 内置的 XML 支持提供了许多工具，用于创建和填充 XML 文档：

- `createElement()`：接受两个参数——名称和值
- `createProcessingInstruction()`：插入处理指令
- `createTextNode()`：创建文本节点
- `createCDATASection()`：创建 CDATA 段
- `createAttribute()`：创建属性

例如，以下代码创建一个带有“War and Peace”元素的文档：

```php
$xmlDoc = new DOMDocument();
$xmlDoc->appendChild(
    $xmlDoc->createElement('War and Peace')
);
```

注意 `appendChild()` 函数的结果被添加到了文档中。

### 使用 Schema 进行验证

`Schema` 是验证文档结构的 W3C 标准。使用 Schema 允许验证整个文档的有效性，也可以指定单个元素的类型。

**示例 3-1：一个 Schema 文档**

```xml
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">
    <xsd:annotation>
        <xsd:documentation>
            Sample schema
        </xsd:documentation>
    </xsd:annotation>
    <xsd:element name="newsletter">
        <xsd:complexType>
            <xsd:sequence>
                <xsd:element name="comment" type="xsd:string" minOccurs="0"/>
                <xsd:element name="header" type="HeaderType"/>
                <xsd:element name="section1" type="SectionType"/>
                <xsd:element name="section2" type="SectionType"/>
            </xsd:sequence>
            <xsd:attribute name="volume" type="xsd:positiveInteger"/>
            <xsd:attribute name="number" type="xsd:positiveInteger"/>
        </xsd:complexType>
    </xsd:element>
    <xsd:complexType name="HeaderType">
        <xsd:sequence>
            <xsd:element name="long_title" type="xsd:string"/>
            <xsd:element name="filename" type="xsd:string"/>
            <xsd:element name="date" type="xsd:date"/>
            <xsd:element name="meta_title" type="xsd:string"/>
            <xsd:element name="meta_description" type="xsd:string"/>
            <xsd:element name="meta_keywords" type="xsd:string"/>
        </xsd:sequence>
    </xsd:complexType>
</xsd:schema>
```

**示例 3-1（继续）**

```xml
<xsd:complexType name="SectionType">
    <xsd:sequence>
        <!-- 每个部分都必须有一个标题 -->
        <xsd:element name="title" type="xsd:string" minOccurs="1"/>
        <!-- 每个部分最多有 2 个链接和 URL -->
        <xsd:element name="linktitle1" type="xsd:string" minOccurs="0"/>
        <xsd:element name="url1" type="xsd:uriReference" minOccurs="0"/>
        <!-- 每个部分都必须有一个注释 -->
        <xsd:element name="annotation1" type="xsd:string" minOccurs="1"/>
        <xsd:element name="toc1" type="xsd:boolean" minOccurs="0"/>
        <!-- 每个部分最多有 2 个链接、URL 和 TOC 条目 -->
        <xsd:element name="linktitle2" type="xsd:string" minOccurs="0"/>
        <xsd:element name="url2" type="xsd:uriReference" minOccurs="0"/>
        <xsd:element name="annotation2" type="xsd:string" minOccurs="0"/>
        <xsd:element name="toc2" type="xsd:boolean" minOccurs="0"/>
    </xsd:sequence>
</xsd:complexType>
```

前面的代码列表包含了几个常见项。例如，标签 `<xsd:element name="linktitle2" type="xsd:string" minOccurs="0"/>` 定义了一个可以在相应的 XML 文档使用的元素。它还指定了数据类型（string）以及该数据类型必须出现的次数。在这种情况下，最小出现次数为 0（零），因此它是一个可选元素。此示例还定义了复杂类型，例如 `SectionType`，它们由较小的元素组成。

本书没有空间对 XML Schema 进行详尽介绍，因此请利用网络和书店中一些优秀的教程。由 Lucinda Dykes 和 Ed Tittel 出版的第 4 版《XML For Dummies》（Wiley Publishing, Inc.）是一个很好的起点。

创建好 schema 之后，就是时候使用它来验证传入的 XML 文档了。始终对进入你应用程序的任何 XML 进行验证，特别是来自外部源的。否则，你只是在盲目信任数据就是你预期的那样。信任可能是一种很好的美德，但在编写应用程序时并非如此！

使用 schema 验证 XML 文档最简单的方法是使用 `DOM` 对象。有关创建 `DOM` 对象的更多信息，请参考本章较早之前的“理解文档对象模型”章节。

在将 XML 读取到 `DOM` 对象后（如下例所示），只需使用此 `schemaValidate()` 方法将存储在 `DOM` 中的 XML 与 schema 定义的标准进行比较：

```php
// Read the XML into the DOM object
$dom_object = new DOMDocument("xmlsource.xml");
$dom_object->schemaValidate("./my_schema.xsd");
```

`schemaValidate()` 返回一个 `Boolean` 值：如果 XML 验证成功则返回 true，否则返回 false。

### 第 3 章：使用 XML

在验证过程中遇到的错误会以 PHP 警告（warnings）的形式抛出，因此在生产环境中使用 `schemaValidate()` 之前，请确保已禁用警告。你不希望外部用户看到 XML 验证警告，因为这些警告通常包含敏感的服务器信息，例如你的 schema 文档的路径。

## 使用 XSLT 为你的文档添加样式

你使用 `XSLT`（可扩展样式表语言转换）将一种类型的 XML 文档转换为另一种。`XSLT` 最常见的用途是将存储在 XML 文档中的数据转换为 HTML 文档。

毕竟，`HTML` 仅仅是 `XML` 的一个特殊版本。（`XML` 是 20 世纪 60 年代开发的 `SGML` [标准通用标记语言] 的直接后代。我们所熟知的 `XML` 大部分与 `SGML` 相比实际上没有变化。`HTML` 是 20 世纪 80 年代末和 90 年代初作为 `SGML` 的应用创建的。`XML` 在 1996 年正式定义。2000 年初开发了 `XHTML` 以使 HTML 重新符合 `SGML` 和 `XML`。）通常，在 XML 文档通过验证后（验证 XML 的细节请见上一节），必须通过样式表才能将数据呈现给最终用户。

PHP 内置了 `XSLT` 功能，只要在编译 PHP 时使用了 `--xsl` 关即可。要使用 PHP 的 `XSLT` 函数，请遵循以下步骤：

1. 创建一个 `XSLTProcessor` 对象和一个 `DOM` 文档对象：

```php
$xslt_processor = new XSLTProcessor();
$DOMdocument = new DOMDocument();
```

2. 将你的 `XSLT` 样式表导入到对象中：

```php
$xslt_processor->importStylesheet("./stylesheet.xsl");
```

3. 将你的 XML 文档转换为另一种格式：

```php
$xslt_processor->transformToDoc($DOMdocument);
$xslt_processor->transformToURI($DOMdocument, $uri);
$xslt_processor->transformToXML($DOMdocument);
```

要将 XML 转换为 HTML，请使用 `transformToXML()` 或 `transformToURI()` 方法。

## 使用 XPath 搜索 XML 文档

`XPath` 是一个工具，让你能够从 XML 文档中提取单个节点，而无需必遍历整个文档。例如，假设你有有如下 XML：

```xml
<?xml version="1.0" encoding="utf-8"?>
<library>
  <book>
    <title>XML For Dummies, 4th Edition</title>
    <author>Lucinda Dykes</author>
    <author>Ed Tittel</author>
    <ISBN>9780764588457</ISBN>
  </book>
  <book>
    <title>PHP &amp; MySQL For Dummies, 3rd Edition</title>
    <author>Janet Valade</author>
    <ISBN>978047009600</ISBN>
  </book>
  <book>
    <title>Database Development For Dummies</title>
    <author>Allen G. Taylor</author>
    <ISBN>9780764507526</ISBN>
  </book>
  <book>
    <title>XML for Programmers</title>
    <author>Joe P. Writer</author>
    <ISBN>1234567890123</ISBN>
  </book>
</library>
```

如果你需要提取 Janet Valade 编写的每本书的标题，你可以遍历每本书并将作者元素与字符串“Janet Valade”进行比较。这种方法相当慢，而且你作为开发者必须花费额外的精力。与其重新发明这个轮子，不如使用 `XPath` 精确地找到你需要的信息。按照以下步骤使用 `XPath` 查找图书馆中有多少书是 Janet Valade 写的：

1. 创建一个 `domXPath` 对象：

```php
$xpath = new domXPath($dom_object);
```

2. 在对象上执行 XPath 查询，返回一个结果数组：

```php
$authors = $xpath->query("/library/book/author");
```

3. 遍历数组以找到精确结果：

```php
$found_books = 0;
foreach ($authors as $author) {
  if ($author == "Janet Valade") {
    $found_books++;
  }
}
print("Found " . $found_books . " books by Janet Valade.");
```

此脚本将打印一条消息，表明它在 XML 数据文件中恰好找到一本 Janet Valade 编写的书。这是一个简单的示例，但它展示了你可以如何轻松地从大数据文件中提取特定数据。

## 第 4 章：使用 GD 处理图像

### 本章

- 配置 GD
- 使用 GD 调整图像的大小和颜色
- 使用 GD 在图像上添加文本

但是，如果你需要根据页面内容包含更改的图像该怎么办？你可以创建几十个独立的图像文件，然后根据页面内容包含它们。但这种解决方案依赖于你能够预判所有需要的每张图像。这也是一种让你的文件系统充满几乎完全相同的文件的好方法。

幸运的是，有一种更好的方法。`GD` 扩展允许你从 `PHP` 内部动态创建并修改图像。动态创建图像有什么好处呢？假设你需要显示一个饼图，向用户展示你的图书馆数据库中虚构类和非虚构类书籍的精确百分比。如果没有 `GD`，你必须为每种可能性手动创建一个不同的饼图图像——创建这些图像将耗费你一整天的时间，占用大量的存储空间，可能还会让你头疼。或者，你可以将百分比（以及其他一些信息）发送给 `GD`，让它动态创建饼图。

图像处理是非常消耗资源的，这可能会让你的应用程序运行得像爬行一样，甚至导致整个 Web 服务器崩溃。请务必在 `php.ini` 中设置足够高的 `memory_limit` 以避免此类问题。设置到多少才够高？遗憾的是，这取决于你的硬件以及你正在进行多少图像处理。你必须通过不断尝试调整 `memory_limit`，直到在你的系统中找到完美的平衡点。

### 查找支持的图像格式

在使用 `GD` 之前，要做的第一件事是找出你的系统支持哪些图像类型。运行如下例所示的 `phpinfo()`，并查找 `gd` 部分。你会看到类似这样的：`$php -r ‘phpinfo();’`

```
phpinfo()

gd

GD Support enabled

GD Version 2.0 or higher

FreeType Support enabled

FreeType Linkage with freetype

JPG Support enabled

PNG Support enabled

WBMP Support enabled
```

`PHP` 自带了它版本的 `GD`，该版本可能与官方标准版本略有不同，因此你通常使用捆绑的版本比从源码 `www.libgd.org` 获取 `GD` 要好。`PHP` 捆带的 `GD` 版本已经过优化配置，以与 `PHP` 配合工作。

密切注意示例的最后三行。那些是系统支持的图像类型。要启用未列出的图像类型，你必须按照如下方式重新编译 `PHP` 并包含对其他图像类型的支持：
