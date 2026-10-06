

## 第三部分：PHP 实践

SimpleMLElement 对象包含了它的每个元素值属性，还以关联数组的形式存储了元素的属性。这一特性使得 SimpleXML 成为从 XML 文件中读取和提取数据的非常方便的方法。例如，如果你想显示甜菜根（beetroot）的单价，你只需要写：

```php
echo $stockList->item[1]->unitPrice;
```

你还可以使用 `xpath()` 方法在 XML 文档中搜索元素。这对于在大型 XML 文件中查找特定元素非常有用，特别是当你事先不知道元素的位置时。例如，以下代码可以获取甜菜根的单价，而无需知道 "beetroot" 是 stockList 的第二个子节点：

```php
$unitPriceElement =
$stockList->xpath("child:item[name=beetroot]/child::unitPrice");
echo $unitPriceElement[0];
```

传递给 `xpath()` 的字符串被称为 XPath 字符串。翻译成英文，这个字符串的意思是：“获取一个本身包含名为 beetroot 的 name 子元素的 item 子元素，然后检索该 item 元素的顺序（此处指节点）。这会返回一个代表 'beetroot' 项目内部单价的 SimpleMLElement 对象，并存储在 $unitPriceElement 中。接着只需显示 $unitPriceElement 中的第一个数组值即可，即文本节点值（1.39）。”

XPath 是将 XML 中的任何节点表示为字符串的一种非常强大的方法，但需要一些时间来。你可以访问 http://www.w3.org/TR/xpath 查看完整的规范。

## 创建 XML 文档

SimpleXML 非常适合读取 XML 文档，但如果你需要创建或修改 XML 文档，DOM 方法是你的最佳选择。这是因为 DOM 类允许你调整 XML 文档的每一个方面；而使用 SimpleXML 则会受到限制。

尽管如此，使用 SimpleXML 创建 XML 文档也是完全可能的，如下接示例所示。该脚本创建了之前示例中使用的 stock_list.xml 文件的 XML，并在浏览器中显示结果：

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

脚本首先从创建 stockList 根元素开始：

它是通过创建一个新的 SimpleXMLElement 对象并传递代表元素的 XML 字符串来实现的。如果你愿意，可以使用这种方法将 XML 文档加载到 SimpleXMLElement 对象中；例如：

```php
$xmlString = file_get_contents("./stock_list.xml");
$stockList = new SimpleXMLElement($xmlString);
```

这与以下代码的作用基本上是相同的：

```php
$stockList = simplexml_load_file("./stock_list.xml");
```

## 第三部分：PHP 实践

接下来的调用使用 `addChild()` 和 `addAttribute()` 方法向树中添加各种元素。如你所见，与本章早前的 DOM 等效代码相比，代码实际上非常紧凑。SimpleXML 使得向元素添加子元素和属性变得如此简单。然而，你会注意到脚本是将 description 元素的内容创建为节点，而不是 CDATA 区。这是因为 SimpleXML 无法创建 CDATA 区。事实上，文本元素是你可以用 SimpleXML 添加的元素类型。

SimpleXML 的另一个局限性是 `xml()` 不会对生成的 XML 字符串进行良好的格式化，因此你的整个 XML 文档最终将挤在一行。为了获得更好的格式，你需要使用 DOM 方法。

## 在 SimpleXML 和 DOM 对象之间转换

到此时你可能已经意识到 SimpleXML 非常适用于读取 XML 文档等简单任务，但 DOM 更适合创建和操作文档等高级任务。幸运的是，SimpleXMLElement 和 DOMElement 对象之间的转换很方便，这意味着如果你偏好，可以使用 SimpleXML 工作，并在需要执行 SimpleXML 无法完成的操作时切换到 DOM。两个关键函数是：

| 函数 | 说明 |
| :--- | :--- |
| simplexml_import_dom( node ) | 将提供的 DOM 节点 node 转换为 SimpleXMLElement 对象 |
| dom_import_simplexml( element ) | 将提供的元素转换为 DOM 节点 |

