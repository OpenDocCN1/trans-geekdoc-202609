
- 当你需要在元素中多次包含相同的字段时，请使用元素。例如，之前描述的 `stockList` 元素包含多个子元素。使用属性无法实现这一点，因为在任何给定的元素中，相同名的属性不能超过一个。

- 当你确定数据在元素中只出现一次时，请使用属性，例如 `item` 元素的 `type` 属性（元素可以是水果或蔬菜，但不能两者兼有）。

另一个经验法是：对于元素的核心数据使用子元素，对于元素的次要数据或唯一标识元素的属性（例如 `id` 属性）。

# 有效 XML 文档：DTD 和 XSD

如前所述，一个有效的 XML 文档是一个包含对 DTD（文档类型定义）或 XSD（XML 架构定义）引用的文档，其内容遵循通用 XML 语法规则（意味着它是良好的），并且符合 DTD 或 XSD 中指定的规则（意味着它是有效的）。之前描述的 "list" XML 文档良好且（可能的）有效的：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE stockList SYSTEM "http://www.example.com/dtd/stockList.dtd">
<stockList>
  <item type="fruit">
    <name>apple</name>
    <unitPrice>0.99</unitPrice>
    <quantity>412</quantity>
    <description><![CDATA[Apples are >>> yummy<<<]]></description>
  </item>
  <item type="vegetable">
    <name>beetroot</name>
    <unitPrice>1.39</unitPrice>
```

```xml
<quantity>67</quantity>
<description><![CDATA[Beetroots are lovely & purple]]></description>
</item>
</stockList>
```

# XHTML：DTD 的实际应用

如之前提到的，任何人都可以编写 XML 文档，并且都可以定义一个 DTD 或 XSD 来验证它。一个广为人知的 DTD 示例是 XHTML，它是重构为 XML 的 HTML。XHTML DTD 与现有 HTML DTD 基本相似，只有细微修改，它定义了 XHTML 文档中允许的所有元素、属性和其他组件。为了将 XHTML 文档作为普通的网页显示，该文档必须是良好的，并且通过 XHTML DTD 的验证。在接下来的几秒钟，你将检查 XHTML DTD 的一部分，学习如何在 XHTML 文档中引用它，探索 XML 命名空间并学习创建 XHTML 网页。

## XHTML 的 DTD

XHTML 有三个 DTD。它们位于：

- `www.w3.org/TR/xhtml/DTD/xhtmlml-strict.dtd`
- `www.w3.org/TR/xhtml/DTD/xhtmlml-transitional.dtd`
- `www.w3.org/TR/xhtml/DTD/xhtmlml-frameset.dtd`

这三个 DTD 与你的 HTML 对应部分相补充，事实上，它们非常相似。如果你在浏览器中输入这些 URL，你实际上会看到纯文本格式的 DTD。（你可能需要下载 DTD 文件并在你的编辑器中打开它）

以下是 XHTML Strict DTD 的部分内容，展示了 `img`（图像）元素是如何声明的：

```
<--
为了避免无法查看图像的人出现可访问性问题，
你应该使用 alt 和 longdesc 属性提供
文本描述。此外，还可以使用服务器端图像映射。
注意，在此 DTD 中没有 name 属性。
该属性仅在 transitional 和 frameset DTD 中可用。
-->

<!ELEMENT img EMPTY>
<!ATTLIST img
%attrs;
  src           #REQUIRED
  %Text          #REQUIRED
  alt           #IMPLIED
  longdesc      #IMPLIED
  height        #IMPLIED
  width         #IMPLIED
  usemap        %URI#IMPLIED
  ismap         (ismap)#IMPLIED
>
<!-- usepoints 用于映射 map 元素，该元素可能存在于本文档或
外部文档中，尽管后者并不被广泛支持 -->
```

在注释后的第一行，`img` 元素被声明为 `EMPTY`（这意味着它不包含任何内容，只有属性）。紧随 `ELEMENT` 行之后的是 XHTML 文档中可能在 `img` 标签内部包含的属性列表。熟悉 HTML 和 XHTML 的同学可能不认识 XML 文档中的 `src` 属性，它用于指定图像文件的位置；该属性是 `REQUIRED`（必须的）。

在 XML 文档的这部分 DTD，可以在文档中包含 `img` 元素。如果 XML 文档中引用了该 DTD，且文档包含一个带有可选 `src` 属性的 `img` 元素，可以说该文档是有效的（至少对于 `img` 而言）。然而，如果你尝试使用 `imge` 或 `image` 或 `images` 元素名称，验证 XML 解析器将产生错误，因为根据 DTD，这些元素未被声明，因此文档是无效。

## 引用 DTD

要引用外部 DTD，你需要使用 `DOCTYPE` 声明。该声明指示了 DTD 的名称和位置。例如，此行展示了如何引用 XHTML Strict DTD：

```
<!DOCTYPE html PUBLIC "//W3C//DTD HTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml/xhtml-strict.dtd">
```

# 第 19 章：处理 XML

第一行中 `<!DOCTYPE>` 之后的 `html` 表明根元素名为 `html`。该声明还包含了位于 `www.w3.org` 网站的 DTD URI。如果 DTD 是外部文档，它可以位于任何地方，并通过任何读取它的应用程序理解并可以访问的 URI 来标识，而不仅仅是互联网上的 URL。

## 指定命名空间

XML 命名空间指示元素和属性名称的来源。能够指定元素或属性名称的来源意味着你可以在单个文档中使用相同的名称来表示不同的事物。如果需要，XML 文档可以引用多个命名空间。

可以通过引用特殊的 XML 关键字在 XML 文档中识别命名空间：`xmlns`（XML 命名空间）属性。当应用于元素时，该命名空间对该元素及其子元素有效。

例如，XHTML 文档中的所有元素必须位于 XHTML 命名空间中。最简单的方法是在 XHTML 文档的根元素（`html`）上使用 `xmlns` 属性。定义根元素同时也定义了其所有子元素的命名空间——即文档中其余元素和属性。

```
<html xmlns="http://www.w3.org/1999/xhtml">
```

## 创建 XHTML 文档

现在你已经理解了如何创建一个有效的 XML 文档，就可以应用这些知识来创建一个 XHTML 文档。

要做到这一点，首先识别你正在使用的 XML 版本，并提供一个引用 DTD 的 `DOCTYPE` 声明。创建根元素——`html` 并包含 `xmlns` 属性以声明该元素（及其所有子元素）的 XHTML 命名空间。最后，你可以在根元素下包含所有子元素——换句话，就是你的 XHTML 页的内容。

这是一个示例：

```
<xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 1.0 Strict//EN"
"http://www.w3.org/TR/DTD/xhtml-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en">
<head>
<title>An XML example</title>
</head>
<body>
<p>This is an example of an XHTML document. It can contain images
<img src="http://www.example.com/image.gif" alt="image" /> as
links as <a href="http://example.com/">example</a> and any other
HTML elements, provided they conform to the XML syntax rules.</p>
</body>
</html>
```

当然，这个文档看起来非常像普通的 HTML 文档，并且像在 HTML 浏览器中编写的任何页面一样显示。然而，与 HTML 文档不同，它符合 XML 规范，不仅是格式良好的（well-formed），而且有效的（valid）。

## 使用 PHP 读取 XML 文档

最近，XML 规范作为数据交换和存储的机制已受到重视。

### 解析器如何工作

解析 XML 的过程涉及几个步骤：

- 使用 `xml_parser_create()` 创建新解析器。
- 使用 `xml_set_element_handler()` 和 `xml_set_character_data_handler()` 注册事件处理器。
- 使用 `xml_parse()` 解析 XML 文档。
- 使用 `xml_parser_free()` 销毁解析器资源。

### 创建新解析器

创建新解析器的过程非常简单。只需调用 `xml_parser_create()` 生成新解析器，并将资源存储在变量中：

```php
$parser = xml_parser_create();
```

你可以选择地添加一个参数，指定字符数据传递给你的事件处理器的编码。默认情况下，解析器发送 UTF-8，但如果你喜欢，可以将其改为 ISO-8859-1 或 US-ASCII。例如：

```php
$parser = xml_parser_create("US-ASCII");
```

### 创建事件处理器

现在你已经有一个解析器可以工作了，你需要创建函数来处理元素的开始、元素的结束和字符数据。

处理元素开始的函数需要三个参数：解析器资源、元素名称以及元素中任何属性的关联数组。例如：

```php
function startElementHandler($parser, $element, $attributes) {
    // (处理元素的开始)
}
```

元素结束处理器类似，但它不需要处理属性：

```php
function endElementHandler($parser, $element) {
    // (处理元素的结束)
}
```

最后，字符数据处理器需要接受解析器资源和一个包含字符数据的字符串。

```php
function characterDataHandler($parser, $data) {
    // (处理字符数据)
}
```

显然，示例处理器没有对元素或数据进行任何处理。我们稍后会编写真实的处理器。

一旦创建了这三个事件处理器，就可以在解析器中注册它们。要注册开始和结束处理器，使用 `xml_set_element_handler()`，传入解析器资源，然后是元素处理器和结束元素函数的名称字符串。例如：

```php
xml_set_element_handler($parser, "startElementHandler", "endElementHandler");
```

要注册字符数据处理器，调用 `xml_set_character_data_handler()`，传入解析器资源，然后是处理器函数的名称字符串：

```php
xml_set_character_data_handler($parser, "characterDataHandler");
```

## 解析 XML 文档

现在你已经准备好实际解析文档了。首先，如果文档是磁盘上的文件或位于某个 URL，你需要将其内容读取到一个字符串变量中，例如使用 PHP 的 `file_get_contents()` 函数。一旦你将 XML 存储在字符串变量中，调用 `xml_parse()`，并将你创建的解析器资源和字符串变量传入参数。例如：

```php
$xml = file_get_contents("xml_document.xml");
xml_parse($parser, $xml);
```

解析器会处理字符串变量的内容，根据需要调用你的事件处理函数，直到读取完所有数据为止。如果解析器成功解析了所有数据，它将返回 `true`；否则将返回 `false`。

你可以在第 11 章中找到更多关于 `file_get_contents()` 和其他文件相关函数的知识。

如果你愿意，也可以分块解析 XML；如果你有大量的 XML 数据且不希望将其全部读取到内存中，这将非常有用。实现此点的一种方法是持续调用 `xml_parse()`。在解析最后的一块数据时，向 `xml_parse()` 传递 `true` 值，告诉它已到达 XML 的末尾：

```php
xml_parse($parser, $xml, true);
```

一旦解析完 XML，让解析器释放内存是一个好主意。要做到这一点，请如下所示使用 `xml_parser_free()`：

```php
xml_parser_free($parser);
```

## 处理解析错误

如果调用 `xml_parse()` 返回 false，则说明解析 XML 文档时出现了一个问题。你可以通过调用各种 XML 解析器函数来查找问题的具体原因：

| 函数 |  |
|---|---|
| `xml_error_code($parser)` | 返回一个指示上一次错误的错误代码 |
| `xml_error_string($code)` | 返回与提供的错误代码相关的错误字符串 |
| `xml_get_current_line_number($parser)` | 返回 XML 文档中当前解析行的行号（这将是错误发生行） |
| `xml_get_current_column_number($parser)` | 返回 XML 文档中当前解析的列数（错误发生点） |

# 第 19 章：与 XML 交互

例如，你可以通过以下代码显示最后的错误消息：

```php
echo xml_error_string( xml_get_error_code($ parser ) );
```

如果你愿意，可以在解析过程的任何点调用 `xml_get_current_line_number()` 和 `xml_get_current_column_number()`，而不仅仅是在发生错误时。这对于查找解析器已到达文档的什么位置很有用。

## 尝试解析 XML 文件

这是一个 XML 解析的简单示例。你将打开硬盘上的 XML 文档并对其进行解析，在此显示它的元素和属性。你可以对任何 XML 文档进行尝试，但此示例使用了章节早期创建的 `stockList` 文档：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE stockList SYSTEM "http://www.example.com/dtd/stockList.dtd">
<stockList>
  <item type="fruit">
    <name>apple</name>
    <unitPrice>0.99</unitPrice>
    <quantity>412</quantity>
    <description><![CDATA[Apples are yummyummy]]></description>
  </item>
  <item type="vegetable">
    <name>beetroot</name>
    <unitPrice>1.39</unitPrice>
    <quantity>67</quantity>
    <description><![CDATA[Beetroots are lovely & purple]]]></description>
  </item>
</stockList>
```

将此文件保存为 `stock_list.xml` 并于你的文档根目录中，以便你的解析器脚本读取。

现在让解析器解析自身。将其保存为 `xml_parser.php` 于你的文档根目录：
