
# 使用 DOM 扩展向 XML 文件添加元素

```html
<title>使用 DOM 扩展向 XML 文件添加元素</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>使用 DOM 扩展向 XML 文件添加元素</h1>
```

```php
<?php
 // 加载 XML 文件
$doc = new DOMDocument();
$doc->preserveWhiteSpace = false;
$doc->load("./stock_list.xml");
$doc->formatOutput = true;

 // 获取 stockList 根元素
$stockListElements = $doc->getElementsByTagName("stockList");
$stockList = $stockListElements->item(0 );

 // 创建一个新的 "item" 元素并将其添加到 stockList
$item = $doc->createElement("item");
$item->setAttribute("type", "vegetable");
$stockList->appendChild($item);

 // 创建 item 的 "name" 子元素
$name = $doc->createElement("name", "carrot");
$item->appendChild($name);

 // 创建 item 的 "unitPrice" 子元素
$unitPrice = $doc->createElement("unitPrice", "0.79");
$item->appendChild($unitPrice);

 // 创建 item 的 "quantity" 子元素
$quantity = $doc->createElement("quantity", "31");
$item->appendChild($quantity);

 // 创建 item 的 "description" 子元素
$description = $doc->createElement("description");
$item->appendChild($description);

$data = $doc->createCDATASection("Carrots are crunchy");
$description->appendChild($data);

// 输出 XML 文档，根据需要对标记字符进行编码
echo htmlspecialchars($doc->saveXML());
?>
```

这会生成如下的 XML 文档：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE stocklist SYSTEM "http://www.example.com/dtds/stocklist.dtd">
<stocklist>
  <item type="fruit">
    <name>apple</name>
    <unitPrice>0.99</unitPrice>
    <quantity>12</quantity>
    <description><![CDATA[Apples are yummy]]></description>
  </item>
  <item type="beetroot">
    <name>beetroot</name>
    <unitPrice>1.39</unitPrice>
    <quantity>67</quantity>
    <description><![CDATA[Beets are lovely & purple]]></description>
  </item>
  <item type="vegetable">
    <name>carrot</name>
    <unitPrice>0.79</unitPrice>
    <quantity>31</quantity>
    <description><![CDATA[Carrots are crunchy]]></description>
  </item>
</stocklist>
```

## 修改节点和属性

假设你有一个 XML 文档，你想更改它的价格。你该如何操作？

正如你所看到的，文本节点以 `DOMText` 对象表示。`DOMDocument` 允许通过 `firstChild` 访问其子节点（如果没有子节点则返回 `null`）。一旦你有了第一个子节点，就可以通过 `nextSibling` 属性遍历它的兄弟节点（如果没有更多兄弟节点则返回 `null`）。

以下脚本遍历每个子节点，如果 `tagName` 匹配 `"unitPrice"`，则替换其第一个子节点：

```php
if ($child = $root->firstChild ) {
    do {
        if ($child->tagName == "unitPrice") {
            $child->firstChild->replaceData(0, 10, "0.79");
            break;
        }
    } while ($child = $child->nextSibling);
}
```

假设你有一个 XML 文档，你想更改它的价格。你该如何操作？`1.39` 到 `0.79`。

该脚本起始的方式与之前的脚本相似——它显示了 XHTML 头部并标识了 `"beetroot"` 元素。一旦完成这些操作，它使用 `item` 元素的 `setAttribute` 方法更改其属性：

```php
$beetroot->setAttribute("type", "vegetable");
```

## 第 19 章：处理 XML

```php
do {
  if ($child->tagName == "unitPrice" ) {
    $child->firstChild->replaceData(0, 10, "0.79");
    break;
  }
} while ($child->nextSibling);
```

对于每个元素，代码都会检查元素的 `tagName` 属性，直到找到该元素。一旦找到，代码就会通过元素的 `firstChild` 属性获取 `unitPrice` 元素内部的文本节点（你知道 `unitPrice` 元素包含一个子节点：包含价格的文本节点）。

最后，通过调用文本节点的 `replaceData()` 方法将 `$1.39` 的价格更改为 `$0.79`。`replaceData()` 接受三个参数：开始替换数据的字符位置、要替换的字符数以及用于替换数据的字符串。如果要替换的字符数大于字符串中的总字符数，则会替换整个字符串。脚本使用了值 `10` 来确保所有字符都被替换（因为任何蔬菜的价格都不可能超过 `$999999999`）。一旦替换完成，任务就完成了，因此它跳出了循环。

## 移动元素

DOM 层次结构非常棒的一点点是，你可以通过操作块顶部的节点来轻松地移动 XML 块。例如，以下代码使用 DOM 类的 `insertBefore()` 方法将 `"beetroot"` 甜菜根）项目（及其所有其他子项）从库存列表的底部移动到：

```html
<!DOCTYPE PUBLIC "-//W3C//DTD HTML 1.0//EN"
 "http://www.w3.org/TR/DTD/html-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>使用 DOM 扩展修改 XML 文件内容</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>使用 DOM 扩展修改 XML 文件内容</h1>
<pre>
<?php
// 加载 XML 文件
$doc = new DOMDocument();
$doc->preserveWhitespace = false;
$doc->load(".stock_list.xml");
$doc->formatOutput = true;

// 获取库存列表根元素
$stocklistElements = $doc->getElementsByTagName("stockList");
$stocklist = $stocklistElements->item(0);

// 获取 "apple" 和 "beetroot" 项目元素
$itemElements = $doc->getElementsByTagName("item");
$php = $itemElements->item(0);
$beetroot = $itemElements->item(1);
```

```php
$stockList->insertBefore($beetroot, $apple);
// 输出 XML 文档，根据需要对标记字符进行编码
echo htmlspecialchars($doc->saveXML());
?>
</pre>
</body>
</html>
```

脚本将 `"apple"` 和 `"beetroot"` 项目存储在两个变量 `$apple` 和 `$beetroot` 中。它调用 `$stocklist->insertBefore()` 在列表中 `$apple` 之前插入 `$beetroot`。（通过插入一个已经存在于文档某处的 DOM 节点，该节点会自动从原位置移动到新位置。）

你可以用于移动节点的其他方法还包括在本节早些提到的 `appendChild()` 和 `removeChild()`，以及 `replaceChild()`（用于用一个节点替换另一个节点）。

## 使用 SimpleXML 轻松地处理 XML

虽然 DOM 扩展是处理 XML 文档的一种强大方法，但其大量的类、方法和属性可能会让人感到无从下手。此外，执行简单任务（如创建子元素和在文档中定位节点）可能会非常繁琐且耗时。

这就是 SimpleXML 发挥用场的地方。该扩展提供了一种更直接的方法来操作 XML 文档中的元素。在很多方面，你可以将其视为“轻版 DOM”。DOM 扩展提供了 15 多个类以及 100 多个方法和属性，而 SimpleXML 只给你一个类：`SimpleMLElement`。此外，DOM 扩展允许你直接深入节点级别，而 SimpleXML 则在元素级别工作，这使得元素操作过程变得简单得多。

以下你可以用于操作 XML 文档的常用 `SimpleMLElement` 方法列表：

| 方法 | 说明 |
| --- | --- |
| `addAttribute(name, value)` | 为元素添加一个名为 *name* 的属性，其值为 *value* |
| `addChild(name [, value])` | 为元素添加一个名为 *name* 的子元素。该子元素可以是空的，也可以包含文本 *value*。它返回作为新的 SimpleXMLElement 对象的子元素 |
| `asXML([filename])` | 从 SimpleXMLElement 对象生成 XML 文档。如果提供了 *filename*，则将 XML 写入文件；否则，以字符串形式返回 XML |
| `attributes()` | 返回该元素中所有属性的关联数组，格式为 name=value 对 |
| `children()` | 返回该元素的所有子元素的数组，每个元素都是 SimpleXMLElement 对象 |
| `getName()` | 以字符串形式返回元素的名称 |
| `xpath(path)` | 查找匹配给定的 XPath（XML 路径语言）路径字符串的子元素 |

此外，SimpleXML 还提供了三个函数，你可以用它们将 XML 数据导入到 SimpleXMLElement 对象中：

| 函数 | 说明 |
| --- | --- |
| `simplexml_import_dom(node)` | 将提供的 DOM 节点 *node* 转换为 SimpleXMLElement 对象 |
| `simplexml_load_file(filename)` | 加载名为 *filename* 的 XML 文件为 SimpleXMLElement 对象 |
| `simplexml_load_string(string)` | 加载提供的 XML 字符串为 SimpleXMLElement 对象 |

使用 SimpleXML，XML 文档中的所有元素都表示为 SimpleXMLElement 对象的树。任何给定元素的子元素都可以作为该 SimpleXMLElement 对象的属性可用。例如，如果 `$parent` 是一个代表具有名为 `child` 子元素的 SimpleXMLElement 对象，你可以通过以下代码直接访问该子元素的文本值：

```php
$value = $parent->child;
```

使用 DOM 类实现相同的操作需要几行代码。

## 第三部分：PHP 实践

`SimpleMLElement` 对象包含了它的每个元素值属性，还以关联数组的形式存储了元素的属性。这一特性使得 SimpleXML 成为从 XML 文件中读取和提取数据的非常方便的方法。例如，如果你想显示甜菜根（beetroot）的单价，你只需要写：

```php
echo $stockList->item[1]->unitPrice;
```

你还可以使用 `xpath()` 方法在 XML 文档中搜索元素。这对于在大型 XML 文件中查找特定元素非常有用，特别是当你事先不知道元素的位置时。例如，以下代码可以获取甜菜根的单价，而无需知道 `"beetroot"` 是 `stockList` 的第二个子节点：

```php
$unitPriceElement = $stockList->xpath("child:item[name=beetroot]/child::unitPrice");
echo $unitPriceElement[0];
```

传递给 `xpath()` 的字符串被称为 XPath 字符串。翻译成英文，这个字符串的意思是：“获取一个本身包含名为 beetroot 的 name 子元素的 item 子元素，然后检索该 item 元素的顺序（此处指节点）。这会返回一个代表 'beetroot' 项目内部单价的 SimpleMLElement 对象，并存储在 `$unitPriceElement` 中。接着只需显示 `$unitPriceElement` 中的第一个数组值即可，即文本节点值（1.39）。”

XPath 是将 XML 中的任何节点表示为字符串的一种非常强大的方法，但需要一些时间来。你可以访问 `http://www.w3.org/TR/xpath` 查看完整的规范。

## 创建 XML 文档

SimpleXML 非常适合读取 XML 文档，但如果你需要创建或修改 XML 文档，DOM 方法是你的最佳选择。这是因为 DOM 类允许你调整 XML 文档的每一个方面；而使用 SimpleXML 则会受到限制。

尽管如此，使用 SimpleXML 创建 XML 文档也是完全可能的，如下接示例所示。该脚本创建了之前示例中使用的 `stock_list.xml` 文件的 XML，并在浏览器中显示结果：

```php
// 创建第一个 "item" 元素（苹果）
$item = $stockList->addChild("item");
$item->setAttribute("type", "fruit");

// 创建项目的 "name" 子元素
$item->addChild("name", "apple");

// 创建项目的 "unitPrice" 子元素
$item->addChild("unitPrice", "0.99");

// 创建项目的 "quantity" 子元素
$item->addChild("quantity", "412");

// 创建项目的 "description" 子元素
$item->addChild("description", "Apples are &gt;&gt;yummy&lt;&lt;&lt;");

// 创建第二个 "item" 元素（甜菜根）
$item = $stockList->addChild("item");
$item->setAttribute("type", "vegetable");

// 创建项目的 "name" 子元素
$item->addChild("name", "beetroot");

// 创建项目的 "unitPrice" 子元素
$item->addChild("unitPrice", "1.39");

// 创建项目的 "quantity" 子元素
$item->addChild("quantity", "67");

// 创建项目的 "description" 子元素
$item->addChild("description", "Beetroots are lovely&amp; purple");

// 输出 XML 文档，根据需要对标记字符进行编码
htmlspecialchars($stockList->asXML());
```

```html
<pre>
<body>
</body>
</pre>
```
