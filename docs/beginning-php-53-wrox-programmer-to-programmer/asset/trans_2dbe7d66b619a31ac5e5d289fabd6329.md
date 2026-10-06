

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

最后，通过调用文本节点的 `replaceData()` 方法将 $1.39 的价格更改为 $0.79。`replaceData()` 接受三个参数：开始替换数据的字符位置、要替换的字符数以及用于替换数据的字符串。如果要替换的字符数大于字符串中的总字符数，则会替换整个字符串。脚本使用了值 10 来确保所有字符都被替换（因为任何蔬菜的价格都不可能超过 $999999999）。一旦替换完成，任务就完成了，因此它跳出了循环。

## 移动元素

DOM 层次结构非常棒的一点点是，你可以通过操作块顶部的节点来轻松地移动 XML 块。例如，以下代码使用 DOM 类的 `insertBefore()` 方法将 "beetroot"甜菜根）项目（及其所有其他子项）从库存列表的底部移动到：

```php
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
```

```php
$php = $itemElements->item( 0 );
$beetroot = $itemElements->item( 1 );

// 将 "beetroot" 移动到项目列表的开头
$stockList->insertBefore($beetroot, $apple);

// 输出 XML 文档，根据需要对标记字符进行编码
echo htmlspecialchars($doc->saveXML());

?>
</pre>
</body>
</html>
```

脚本将 "apple" 和 "beetroot" 项目存储在两个变量 `$apple` 和 `$beetroot` 中。它调用 `$stocklist->insertBefore()` 在列表中 `$apple` 之前插入 `$beetroot`。（通过插入一个已经存在于文档某处的 DOM 节点，该节点会自动从原位置移动到新位置。）

你可以用于移动节点的其他方法还包括在本节早些提到的 `appendChild()` 和 `removeChild()`，以及 `replaceChild()`（用于用一个节点替换另一个节点）。

## 使用 SimpleXML 轻松地处理 XML

虽然 DOM 扩展是处理 XML 文档的一种强大方法，但其大量的类、方法和属性可能会让人感到无从下手。此外，执行简单任务（如创建子元素和在文档中定位节点）可能会非常繁琐且耗时。

这就是 SimpleXML 发挥用场的地方。该扩展提供了一种更直接的方法来操作 XML 文档中的元素。在很多方面，你可以将其视为“轻版 DOM”。DOM 扩展提供了 15 多个类以及 100 多个方法和属性，而 SimpleXML 只给你一个类：`SimpleMLElement`。此外，DOM 扩展允许你直接深入节点级别，而 SimpleXML 则在元素级别工作，这使得元素操作过程变得简单得多。

以下你可以用于操作 XML 文档的常用 `SimpleMLElement` 方法列表：

| 方法 | 说明 |
| --- | --- |
| addAttribute( name, value ) | 为元素添加一个名为 *name* 的属性，其值为 *value* |
| addChild( name [, value] ) | 为元素添加一个名为 *name* 的子元素。该子元素可以是空的，也可以包含文本 *value*。它返回作为新的 SimpleXMLElement 对象的子元素 |
| asXML( [filename] ) | 从 SimpleXMLElement 对象生成 XML 文档。如果提供了 *filename*，则将 XML 写入文件；否则，以字符串形式返回 XML |
| attributes() | 返回该元素中所有属性的关联数组，格式为 name=value 对 |
| children() | 返回该元素的所有子元素的数组，每个元素都是 SimpleXMLElement 对象 |
| getName() | 以字符串形式返回元素的名称 |
| xpath( path ) | 查找匹配给定的 XPath（XML 路径语言）路径字符串的子元素 |

此外，SimpleXML 还提供了三个函数，你可以用它们将 XML 数据导入到 SimpleXMLElement 对象中：

| 函数 | 说明 |
| --- | --- |
| simplexml_import_dom( node ) | 将提供的 DOM 节点 *node* 转换为 SimpleXMLElement 对象 |
| simplexml_load_file( filename ) | 加载名为 *filename* 的 XML 文件为 SimpleXMLElement 对象 |
| simplexml_load_string( string ) | 加载提供的 XML 字符串为 SimpleXMLElement 对象 |

使用 SimpleXML，XML 文档中的所有元素都表示为 SimpleXMLElement 对象的树。任何给定元素的子元素都可以作为该 SimpleXMLElement 对象的属性可用。例如，如果 *$parent* 是一个代表具有名为 *child* 子元素的 SimpleXMLElement 对象，你可以通过以下代码直接访问该子元素的文本值：

```php
$value = $parent->child;
```

使用 DOM 类实现相同的操作需要几行代码。

