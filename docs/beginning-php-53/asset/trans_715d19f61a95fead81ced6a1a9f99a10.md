

如果您的 XML 文档包含一个元素名称，由于其中包含 PHP 变量中不允许的字符而无法表示为 PHP 属性（例如 unit-price），您可以使用花括号表示法来访问它，如下所示：

```
$value = $element->{'unit-price'};

```

您可以使用数组表示法访问元素的属性。假设一个名为 $element 的 SimpleXMLElement 对象包含一个名为 type 的属性。您可以使用以下方式访问该属性的值：

```
$value = $element['type'];

```

如果 SimpleXMLElement 对象表示带有 CDATA 节的元素，该怎么办？在这种情况下，您可以通过将对象强制转换为字符串来提取 CDATA 文本：

```
$value = (string)$element;

```

## 读取 XML 文档

以下示例展示了使用 SimpleXML 读取和显示 XML 文档内容是多么简单：

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Reading an XML File with the SimpleXML Extension</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Reading an XML File with the SimpleXML Extension</h1>
<pre>
<?php
// Read the XML document into a SimpleXMLElement object
$stockList = simplexml_load_file( "./stock_list.xml", "SimpleXMLElement",
LIBXML_NOCDATA );
// Display the object
echo htmlspecialchars( print_r( $stockList, true ) );
?>
</pre>
</body>
</html>

```

将脚本保存为文档根目录下的 simplexml_read_document.php（与本章前面示例中的 stock_list.xml 文件一起），然后运行它。您应该会看到类似图 19-4 的内容。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_646_0.png)

## 图 19-4

脚本首先调用 SimpleXML 函数 `simplexml_load_file()`，将 `stock_list.xml` 文件中的根元素 `stockList` 加载为 `SimpleXMLElement` 对象 `$stockList`。

您会注意到，脚本向 `simplexml_load_file()` 传递了两个额外参数。第一个参数 "SimpleXMLElement" 是要用于生成对象的类名。这允许您继承基类 `SimpleXMLElement` 来创建自定义元素类。但是，在这种情况下，脚本只是传入默认类名 "SimpleXMLElement"，以创建一个普通的 `SimpleXMLElement` 对象。这样做纯粹是为了让脚本能够传递第三个参数：`LIBXML_NOCDATA` 常量。该常量确保 SimpleXML 库读取 XML 文档的 CDATA 节，并将其转换为文本节点，以便使用后续的 `print_r()` 函数调用轻松显示。

一旦 XML 文件被读入 `SimpleXMLElement` 对象，只需使用 `print_r()` 将对象的内容输出到浏览器即可。为此，脚本还向 `print_r()` 传递了第二个参数 `true`；这样可以确保 `print_r()` 返回一个字符串，而不是直接输出到浏览器。然后脚本使用 `htmlspecialchars()` 确保字符串正确编码为 XHTML，并将生成的字符串发送到浏览器。

从输出中可以看出，`$stockList` 对象包含一个名为 `item` 的数组，其中包含 XML 文档中的两个 `item` 子元素。每个 `item` 元素本身都存储为一个 SimpleXMLElement 对象，该对象将其每个子元素的值作为属性，并将元素的属性作为关联数组存储。正是这项功能使 SimpleXML 成为读取和提取 XML 文件中数据的非常简单的方法。例如，如果您想显示甜菜根的单价，只需编写：

```
echo $StockList->item[1]->unitPrice;
```

您还可以使用强大的 xpath() 方法在 XML 文档中搜索元素。这对于在大型 XML 文件中查找特定元素非常有用，尤其是当您事先不知道元素的位置时。例如，以下代码检索甜菜根的单价，而不需要知道“beetroot”项目是 stockList 的第二个子元素：

```
$UnitPriceElement =
$StockList->xpath( "child::item[name='beetroot']/child::unitPrice" );
echo $UnitPriceElement[0];
```

传递给 xpath() 的字符串称为 XPath 字符串。将其翻译成英语，该字符串的意思是：“获取名为 item 的子元素，该元素本身包含一个值为 beetroot 的 name 子元素，然后检索 item 元素的另一个名为 unitPrice 的子元素。”这将返回一个 SimpleXMLElement 对象，表示“beetroot”项目元素内部的 unitPrice 元素，并存储在 $UnitPriceElement 中。然后只需显示 $UnitPriceElement 中的第一个数组值，即包含所需值（1.39）的文本节点。

XPath 是一种非常强大的方式，可以将任何 XML 文档中的任何节点表示为字符串，但需要一些时间来适应。您可以在 http://www.w3.org/TR/xpath 阅读完整规范。

## 创建 XML 文档

尽管 SimpleXML 非常适合读取 XML 文档，但如果您需要创建或修改 XML 文档，DOM 方法是您的最佳选择。这是因为 DOM 类允许您调整 XML 文档的每个方面；使用 SimpleXML 时，您能做的事情更有限。

尽管如此，使用 SimpleXML 创建 XML 文档完全是可行的，如下一个示例所示。此脚本创建前面示例中使用的 stock_list.xml 文件的 XML，并在浏览器窗口中显示生成的 XML：

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Creating an XML File with the SimpleXML Extension</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Creating an XML File with the SimpleXML Extension</h1>
<pre>
<?php
// Create the root "stockList" element
$StockList = new SimpleXMLElement( "<stockList/>" );

// Create the first "item" element (apple)
$item = $stockList->addChild( "item" );
$item->addAttribute( "type", "fruit" );

// Create the item's "name" child element
$item->addChild( "name", "apple" );

// Create the item's "unitPrice" child element
$item->addChild( "unitPrice", "0.99" );

// Create the item's "quantity" child element
$item->addChild( "quantity", "412" );

// Create the item's "description" child element
$item->addChild( "description", "Apples are &gt;&gt;&gt;&gt;yummy&lt;&lt;&lt;&lt;" );

// Create the second "item" element (beetroot)
$item = $stockList->addChild( "item" );
$item->addAttribute( "type", "vegetable" );

// Create the item's "name" child element
$item->addChild( "name", "beetroot" );

// Create the item's "unitPrice" child element
$item->addChild( "unitPrice", "1.39" );

// Create the item's "quantity" child element
$item->addChild( "quantity", "67" );

// Create the item's "description" child element
$item->addChild( "description", "Beetroots are lovely &amp; purple" );

// Output the XML document, encoding markup characters as needed
echo htmlspecialchars( $stockList->asXML() );

?>
</pre>
</body>
</html>
```

脚本首先创建 stockList 根元素：

```
$stockList = new SimpleXMLElement( "<stockList/>" );
```

它通过创建一个新的 SimpleXMLElement 对象，并传入表示元素的 XML 字符串来实现这一点。如果您愿意，可以使用此方法将整个 XML 文档加载到 SimpleXMLElement 对象中；例如：

```
$xmlString = file_get_contents( "./stock_list.xml" );
$stockList = new SimpleXMLElement( $xmlString );
```

这本质上与以下操作相同：

```
$stockList = simplexml_load_file( "./stock_list.xml" );
```

接下来，脚本调用 addChild() 和 addAttribute() 方法将各种元素添加到树中。如您所见，与本章前面展示的 DOM 等效代码相比，代码实际上非常简洁。这是因为 SimpleXML 使向元素添加子元素和属性变得非常容易。但是，您会注意到，脚本将 description 元素的内容作为文本节点创建，而不是 CDATA 节；这是因为 SimpleXML 无法创建 CDATA 节。事实上，文本元素是您可以使用 SimpleXML 添加的唯一类型的元素。

SimpleXML 的另一项限制是 asXML() 不允许您以良好的方式格式化生成的 XML 字符串，因此整个 XML 文档最终会位于一行上。为了获得更美观的格式，您需要使用 DOM 方法。

## 在 SimpleXML 和 DOM 对象之间转换

到现在您可能已经意识到，SimpleXML 非常适合（嗯）读取 XML 文档之类的简单任务，但 DOM 更适合创建和操作文档等更高级的任务。幸运的是，在 SimpleXMLElement 对象和 DOMElement 对象之间转换很容易，这意味着您可以（如果您愿意）使用 SimpleXML，然后在需要做 SimpleXML 无法完成的事情时切换到 DOM。这里的两个关键函数是：

| Function | Description |
|---|---|
| `simplexml_import_dom( node )` | 将提供的 DOM 节点 `node` 转换为 SimpleXMLElement 对象 |
| `dom_import_simplexml( element )` | 将提供的 SimpleXMLElement 对象 `element` 转换为 DOM 节点 |

例如，之前您了解到 SimpleXML 无法创建 CDATA 节；然而，DOM 类可以。因此，对于前面描述的 stockList 示例，您可以按以下方式将“apple”项目的 description 元素以及相关的“Apples are >>>yummy<<<”CDATA 节添加到 SimpleXML 文档中：

```
php
// Create the item's "description" child element
$itemDOM = dom_import_simplexml( $item );
$description = $itemDOM->ownerDocument->createElement( "description" );
$itemDOM->appendChild( $description );
$cdata = $itemDOM->ownerDocument->createCDATASection( "Apples are >>>yummy<<<" );
$description->appendChild( $cdata );
```

第一行从 $item SimpleXMLElement 对象创建一个 DOM 节点 $itemDOM（此过程会隐式创建一个 DOMDocument 对象来保存该节点）。然后，接下来的两行创建一个 $description DOMElement 节点——通过 ownerDocument 属性访问 $itemDOM 节点的 DOMDocument 对象——并将其作为子节点添加到 $itemDOM 节点。最后两行创建 CDATA 节点 $cdata，并将其追加到 $description 节点。通过在 DOM 中添加这些节点，新元素会自动添加到 $item SimpleXMLElement 对象中。

