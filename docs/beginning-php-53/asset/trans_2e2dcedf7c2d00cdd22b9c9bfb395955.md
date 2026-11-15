

通过将 nodeType 属性与这些常量进行比较，你可以确定节点的类型，而 traverseDocument( ) 函数正是做这件事。如果是元素节点，它使用 DOMElement 对象的 tagName 属性显示元素的名称。如果元素包含属性（使用 hasAttributes( ) 方法测试），它会遍历存储在元素的 attributes 属性中的 DOMAttr 属性对象数组，并使用对象的 name 和 value 属性显示每个属性的名称和值：

```
case XML_ELEMENT_NODE:
    echo "Found element: \"$node->tagName\"";

    if ( $node->hasAttributes() ) {
        echo " with attributes: ";
        foreach ( $node->attributes as $attribute ) {
            echo "$attribute->name=\"$attribute->value\" ";
        }
    }

    echo "\n";
    break;
```

如果节点是文本节点，函数会测试该节点是否实际包含除空白字符之外的内容（这样可以避免显示 XML 文档中可能存在的任何格式空白字符）。如果包含，函数会显示存储在 DOMText 对象的 wholeText 属性中的节点文本内容：

```
case XML_TEXT_NODE:
    if ( trim($node->wholeText) ) {
        echo "Found text node: \"$node->wholeText\"\n";
    }
    break;
```

如果节点是字符数据节点，同样，函数会显示字符数据，前提是它不仅仅包含空白字符。数据存储在 DOMCharacterData 对象的 data 属性中。另外，因为字符数据节点可能包含“<”和“>”等标记字符，函数会调用 htmlspecialchars( ) 来按需要对任何标记字符进行编码：

```
case XML_CDATA_SECTION_NODE:
    if ( trim($node->data) ) {
        echo "Found character data node: \"" .
            htmlspecialchars($node->data) . "\"\n";
    }
    break;
```

最后，函数使用 DOMNode 对象的 hasChildNodes( ) 方法测试正在处理的节点是否包含任何子节点。如果有子节点，函数会遍历存储在 DOMNode 对象的 childNodes 属性中的每个子节点，并对每个子节点调用自身，从而继续递归过程：

```
if ( $node->hasChildNodes() ) {
    foreach ( $node->childNodes as $child ) {
        traverseDocument( $child );
    }
}
```

## 使用 DOM 创建 XML 文档

现在你知道如何使用 DOM 扩展读取 XML 文档，并且在过程中也探索了一些常见的 DOM 类、属性和方法。你现在已准备好尝试使用 DOM 从头开始创建一个 XML 文档。

你已经知道如何使用 `new DOMDocument()` 创建一个基本的 DOM 文档。创建文档后，只需创建节点，然后将每个节点添加到文档中以构建 DOM 树。

要创建节点，你需要调用 `DOMDocument` 类的各种方法。常用方法包括：

| 方法 | 描述 |
|---|---|
| `createElement( name [, value ] )` | 创建名为 `name` 的元素节点，并可选地将包含 `value` 的文本节点追加到其中 |
| `createTextNode( content )` | 创建包含 `content` 的文本节点 |
| `createCDATASection( data )` | 创建包含 `data` 的字符数据节点 |
| `createComment( data )` | 创建包含 `data` 的注释节点 |

创建节点后，你可以通过调用现有节点的 `appendChild()` 方法将其作为子节点添加到现有节点中：

```
$parentNode->appendChild( $childNode );
```

这样你就可以构建包含根元素节点、其子节点、其孙子节点等等的文档树。

你还可以向元素节点添加属性。简单的方法是使用 `DOMElement` 对象的 `setAttribute()` 方法：

```
$element->setAttribute( "name", "value" );
```

更冗长的方法是使用 DOMDocument 的 `createAttribute()` 方法创建一个 DOMAttr 属性节点，设置属性的 `value` 属性，然后使用元素的 `appendChild()` 方法将属性添加到元素中：

```
$attribute = $doc->createAttribute( "name" );
$attribute->value = "value";
$element->appendChild( $attribute );
```

虽然第二种方法更繁琐，但它确实向你展示了 DOM 文档中几乎所有东西最终都是一个节点——即使属性也是节点。

## 使用 DOM 创建 XML 文档

现在你可以将这些理论付诸实践。你将仅使用 DOM 类和方法，从头开始创建 stock_list.xml 文件的一个几乎完全相同的版本。

下面的脚本就是用来完成此任务的：

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Creating an XML File with the DOM Extension</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Creating an XML File with the DOM Extension</h1>
<pre>

<?php
// Create a DOMDocument object and set nice formatting
$doc = new DOMDocument( "1.0", "UTF-8" );
$doc->formatOutput = true;

// Create the root "stockList" element
$StockList = $doc->createElement( "stockList" );
$doc->appendChild( $StockList );

// Create the first "item" element (apple)
$item = $doc->createElement( "item" );
$item->setAttribute( "type", "fruit" );
$StockList->appendChild( $item );

// Create the item's "name" child element
$Name = $doc->createElement( "name", "apple" );
$item->appendChild( $Name );

// Create the item's "unitPrice" child element
$UnitPrice = $doc->createElement( "unitPrice", "0.99" );
$item->appendChild( $UnitPrice );

// Create the item's "quantity" child element
$Quantity = $doc->createElement( "quantity", "412" );
$item->appendChild( $Quantity );

// Create the item's "description" child element
$description = $doc->createElement( "description" );
$item->appendChild( $description );
$cdata = $doc->createCDATASection( "Apples are >>>yummy<<<" );
$description->appendChild( $cdata );

// Create the second "item" element (beetroot)
$item = $doc->createElement( "item" );
$item->setAttribute( "type", "vegetable" );
$StockList->appendChild( $item );

// Create the item's "name" child element
$name = $doc->createElement( "name", "beetroot" );
$item->appendChild( $name );

// Create the item's "unitPrice" child element
$UnitPrice = $doc->createElement( "unitPrice", "1.39" );
$item->appendChild( $UnitPrice );

// Create the item's "quantity" child element
$quantity = $doc->createElement( "quantity", "67" );
$item->appendChild( $quantity );

// Create the item's "description" child element
$description = $doc->createElement( "description" );
$item->appendChild( $description );
$cdata = $doc->createCDATASection( "Beetroots are lovely & purple" );
$description->appendChild( $cdata );

// Output the XML document, encoding markup characters as needed
echo htmlspecialchars( $doc->saveXML() );
?>
</pre>
</body>
</html>
```

将此脚本保存为文档根目录下的 dom_create_document.php，然后运行它。你应该会看到类似图 19-3 的内容。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_634_0.png)

图 19-3

## 工作原理

如果你迄今为止都跟上了，这个脚本应该相当易于自行理解。在输出 XHTML 页面标题后，它会创建一个新的 DOMDocument 对象，并传入可选参数，分别指定 XML 版本（1.0）和要使用的字符编码（UTF-8）。接着，它将对象的 `formatOutput` 属性设置为 `true`；这样可以确保输出的 XML 格式良好，而不是全部挤在一行上：

```php
$doc = new DOMDocument( "1.0", "UTF-8" );
$doc->formatOutput = true;
```

接下来，脚本创建一个新的 DOMElement 节点来表示根元素 `stockList`，并将此节点作为子节点添加到文档对象中：

```php
$stockList = $doc->createElement( "stockList" );
$doc->appendChild( $stockList );
```

现在是时候创建第一个 `item` 元素，为其赋予值为 "fruit" 的 `type` 属性，并将该元素添加到 `stockList` 元素中：

```php
$item = $doc->createElement( "item" );
$item->setAttribute( "type", "fruit" );
$stockList->appendChild( $item );
```

接下来的几行代码会创建 `item` 元素的所有子元素。每个元素对象都会被创建，然后追加到 `item` 中。`createElement()` 方法允许你传入一个可选的第二个字符串参数，然后用该参数的值构建一个 DOMText 对象，并自动将其追加到新创建的元素中。这样你就不必每次都手动使用 `createTextNode()` 来创建子 DOMText 对象：

```php
// Create the item's "name" child element
$name = $doc->createElement( "name", "apple" );
$item->appendChild( $name );
```

```php
// Create the item's "unitPrice" child element
$unitPrice = $doc->createElement( "unitPrice", "0.99" );
$item->appendChild( $unitPrice );
```

```php
// Create the item's "quantity" child element
$quantity = $doc->createElement( "quantity", "412" );
$item->appendChild( $quantity );
```

但是，要为 `description` 元素创建 CDATA 节点，你必须采用繁琐的方法：

```php
// Create the item's "description" child element
$description = $doc->createElement( "description" );
$item->appendChild( $description );
$cdata = $doc->createCDATASection( "Apples are >>>yummy<<<" );
$description->appendChild( $cdata );
```

接下来，第二个 `item` 元素以类似的方式创建：

