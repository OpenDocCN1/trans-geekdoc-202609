
虽然面向对象 API 没有公开声明魔术方法 `__toString`，但它也可以强制转换为字符串，也可以使用 `echo` 语句直接输出。

#### 总结

本章到此结束。此时，你应该已经将获得的文档转换为适合输入到 XML 扩展的格式。接下来的几章将专门介绍如何使用特定的扩展从修复后的文档中搜索和提取数据。

有关 tidy 扩展的 PHP 手册部分，请访问 http://php.net/tidy。

有关 tidy 库本身的文档，请访问 http://tidy.sourceforge.net/#docs。

有关 tidy 配置设置参考，请访问 http://tidy.sourceforge.net/docs/quickref.html。

### 第 10 章

### DOM 扩展

一旦检索到的标记文档被清理并通过验证，下一步就是从中提取有用的数据。为此，理想的方法是利用文档是有效标记这一事实，并应用一个 XML 扩展。PHP 有几种这样的扩展，接下来的几章将专门介绍它们。

本章的同名主题是文档对象模型（DOM）扩展。该扩展的名称来源于一种标准化的、语言无关的 API，用于导航和操作有效的、格式良好的 XML 和 HTML 文档。该标准由致力于新兴互联网相关标准的万维网联盟（W3C）维护并推荐。本章不会全面覆盖 DOM 扩展，仅涉及与网络抓取相关且必不可少的部分。

> **注意：DOM XML**
> DOM 扩展仅在 PHP 5 中可用。其 PHP 4 兼容的前身 DOM XML 扩展具有略微不同的 API，但共享许多相同的概念。本章的示例将仅限于 DOM 扩展。有关 DOM XML 扩展的等效细节，可以参考 PHP 手册的相关章节，请访问 http://php.net/manual/en/book.domxml.php。

在继续深入之前，你应该知道有两种类型的 XML 解析器：**树解析器**和**拉取解析器**。树解析器将整个文档加载到内存中，允许你在任何时候访问其任何部分并进行操作。拉取解析器逐块读取文档，并限制你只能处理当前正在读取的部分。

这两种类型的解析器共享类似 `file_get_contents` 和 `fgets` 函数之间的关系：前者允许你一次处理整个文档，并使用存储它所需的任何内存，而后者允许你一次处理文档的一部分，并在过程中使用更少的内存。

在处理相当大的文档时，较低的内存使用率通常是更可取的选择。试图一次性将巨大的文档加载到内存中，对本地系统的影响与限制客户端对 Web 服务器的影响相同：在这两种情况下，资源都被消耗，系统性能都会因压力而减弱，直到系统最终锁死或崩溃。

DOM 扩展是一个树解析器。一般来说，网络抓取并不要求能够同时访问文档的所有部分。然而，使用拉取解析器实现网络抓取所涉及的数据提取类型可能相当复杂。选择哪种扩展取决于文档的大小和复杂度。

### 加载文档

`DOMDocument` 类是开始使用 DOM 扩展的地方。首先要做的是实例化它，然后输入已验证的标记数据。请注意，如果加载的文档无效或格式良好，DOM 扩展在加载文档时会产生警告。为了避免这种情况，请参见上一章中关于使用 tidy 扩展的内容。如果 tidy 未能消除问题，错误可以按照下面的示例进行控制。请注意，错误会被缓冲直到手动清除，因此如果不再需要它们，请在每次加载操作后清除它们，以避免浪费内存。

```php
<?php
// 缓冲 DOM 错误，而不是将其作为警告发出
$oldSetting = libxml_use_internal_errors(true);
// 实例化一个文档容器
$doc = new DOMDocument;
// 加载已包含在字符串中的标记
$doc->loadHTML($htmlString);
// 加载保存到外部文件的标记
$doc->loadHTMLFile($htmlFilePath);
// 获取所有错误（如果需要）
$errors = libxml_get_errors();
// 只获取最后一个错误
$error = libxml_get_last_error();
// 清除来自先前操作的任何现有错误
libxml_clear_errors();
// 将错误缓冲恢复到其先前的设置
libxml_use_internal_errors($oldSetting);
?>
```

### 树术语

一旦文档被加载，下一个自然的步骤就是从中提取所需的数据。然而，这样做需要对 DOM 的结构有更深入的了解。回想之前提到的树解析器。如果你有任何计算机科学背景，你会很高兴地知道，在树解析器的语境中，“树”一词确实指的是同名数据结构。如果没有，以下是相关概念的简要说明。

**树**是一种分层结构（想想家谱），由**节点**组成，这些节点在 DOM 扩展中作为 `DOMNode` 类存在。节点之于树，就像元素之于数组：只是存在于数据结构中的项目。

每个单独的节点可以有零个或多个**子节点**，这些子节点在 `DOMNode` 类中由 `childNodes` 属性集体表示。`childNodes` 是类 `DOMNodeList` 的一个实例，这听起来正是它的样子。其他相关的属性包括 `firstChild` 和 `lastChild`。**叶子节点**是指没有子节点的节点，可以使用 `DOMNode` 的 `hasChildNodes` 方法进行检查。

树中的所有节点都有一个单一的**父节点**，唯一的例外是**根节点**，树中的所有其他节点都源于该根节点。如果两个节点共享同一个父节点，它们就被恰当地称为**兄弟节点**。这种关系体现在 `DOMNode` 的 `previousSibling` 和 `nextSibling` 属性中。

最后，某节点的子节点、这些子节点的子节点，依此类推，统称为**后代节点**。同样地，某节点的父节点、该父节点的父节点，依此类推，统称为**祖先节点**。

一个示例可能有助于展示这些术语。

```html
<html>
<body>
<ul id="thelist">
<li>Foo</li>
<li>Bar</li>
</ul>
</body>
</html>
```

- `html` 是根节点。
- `body` 是 `html` 的第一个（也是唯一的）子节点。
- `ul` 是 `body` 的第一个（也是唯一的）子节点。
- 包含**Foo**和**Bar**的 `li` 节点分别是 `ul` 的第一个和最后一个子节点。
- 包含**Bar**的 `li` 节点是包含**Foo**的 `li` 节点的下一个兄弟节点。
- 同样，包含**Foo**的 `li` 节点是包含**Bar**的 `li` 节点的上一个兄弟节点。
- `ul` 和 `li` 节点是 `body` 节点的后代。

### 元素和属性

至此，DOM 超越了树的类比。存在多种类型的节点，或者用 DOM 扩展的语境来表达，即 `DOMNode` 拥有多个子类。您主要将要处理的是用于**元素**的 `DOMElement` 和用于**属性**的 `DOMAttr`。以下是这些概念在上节示例中的具体应用。

- `ul` 是一个元素的名称。
- `id` 是 `ul` 元素的一个属性的名称。
- `thelist` 是 `id` 属性的值。
- `Foo` 和 `Bar` 是 `li` 元素的值。

#### 定位节点

`DOMDocument` 类的两种方法允许您相对快速地减少需要遍历的节点数量，以找到您想要的数据。

`getElementById` 试图定位满足两个条件的单个元素：1) 它是文档根元素的后代；2) 它具有给定的 `id` 属性值。如果找到这样的元素，则作为 `DOMElement` 实例返回；否则，返回 `null`。

`getElementsByTagName` 试图定位满足两个条件的所有元素：1) 它是文档根元素的后代；2) 它具有给定的元素名称（例如 `ul`）。此方法始终返回找到的任意元素的 `DOMNodeList`。`DOMNodeList` 类有一个 `length` 属性，如果未找到任何元素，该属性将等于 0。它也是可迭代的，因此可以作为 `foreach` 循环的主题使用。

`DOMElement` 类也有一个 `getElementsByTagName` 方法，其功能相同，只是定位到的元素将是该元素的后代，而不是文档根元素的后代。

```php
<?php
// 获取上一示例中列表项的一种方法
$listItems = $doc->getElementsByTagName('li');
// 一种更具体的方法（如果有多个列表时更好）
if ($list = $doc->getElementById('thelist')) {
    $listItems = $list->getElementsByTagname('li');
}
// 另一种方法，如果列表没有 id
$lists = $doc->getElementsByTagname('ul');
if ($lists->length) {
    $list = $lists->item(0);
    $listItems = $list->getElementsByTagname('li');
}
// 输出 "thelist"（不带引号）
echo $list->getAttribute('id');
// 第一行输出 "Foo"，第二行输出 "Bar"
foreach ($listItems as $listItem) {
    echo $listItem->nodeValue, PHP_EOL;
}
// 输出 <ul id="thelist"> 和 </ul> 内的文本内容
echo $list->nodeValue;
?>
```

### XPath 和 DOMXPath

类似于正则表达式允许在字符串中找到字符模式的实例，XPath 允许在 XML 兼容的文档中找到节点模式的实例。这两种技术都是通过提供由**元字符**组成的语法来实现其目的的，从而以简洁明了的方式表达这些模式。在 DOM 扩展中，XPath 标准的 1.0 版本支持是作为**DOMXPath** 类实现的。

**DOMXPath** 构造函数有一个必需的参数：现有的**DOMDocument** 实例，查询将在该实例上执行。**DOMXPath** 还有两个相关的方法：`evaluate` 和 `query`。这两个方法的第一参数都是包含 XPath 表达式的字符串，用于查询文档。

可选地，可以与文档相关联的 **DOMNode** 实例可以作为第二个参数（`$contextNode`）传递给任一方法。当指定时，该节点将成为**上下文节点**，查询结果将被限制在该节点及其后代中。否则，假设文档的根元素为上下文节点。

*evaluate* 和 *query* 之间的区别在于，后者始终返回 *DOMNodeList* 的实例，而前者在仅找到一个结果时会尝试返回适当类型的结果。

#### 绝对寻址

使用 XPath 表达式获取该表达式应用的一组节点的过程被称为**寻址**。本章的其余部分将介绍寻址的各个方面以及相关表达式语法。

XPath 表达式与 UNIX 文件系统路径有几个相似之处，两者都用于遍历概念上的树结构。请参阅下面的具体实例。此处重新使用了上文中用于说明标记语言各种概念的 HTML 示例，以展示 XPath 寻址。

```php
<?php
// 加载一个标记文档
$doc = new DOMDocument;
$doc->loadHTML('
<html>
<body>
<ul id="thelist">
<li>Foo</li>
<li>Bar</li>
</ul>
</body>
</html>
');
// 配置用于查询文档的对象
$xpath = new DOMXPath($doc);
// 返回仅包含 html 节点的 DOMNodeList
$list = $xpath->query('/html');
// 返回仅包含 body 节点的 DOMNodeList
$list = $xpath->query('/html/body');
// 同样返回仅包含 body 节点的 DOMNodeList
$list = $xpath->query('//body');
?>
```

- 在前两个示例中请注意，即使在查询调用中未指定其他节点作为第二个参数（这意味着假设根节点（html）为上下文节点），根元素（html）也在表达式中被引用。
- 一个**单斜杠** `/` 表示父子关系。`/html/body` 寻址文档根 html 元素的所有作为子节点的 body 节点（在此情况下仅产生单个结果）。
- 一个**双斜杠** `//` 表示祖先后代关系。`//body` 寻址上下文节点的所有后代 body 节点（同样仅产生单个结果）。

单斜杠和双斜杠运算符可以多次使用，并如以下所示相互组合。

```php
<?php
// 返回所有作为 body 节点后代的 ul 节点
$list = $xpath->query('//body/ul');
// 返回所有作为 ul 节点子节点的 li 节点
$list = $xpath->query('//body/ul/li');
?>
```

### 命名空间

如果您尝试通过元素名称寻址节点，但本应得到结果时却未收到，有可能文档正在对节点进行命名空间处理。解决此问题的最简单方法是用条件替换元素名称。
例如，如果您使用的表达式是 `ul`，则忽略命名空间的等效表达式将是 `*[name()="ul"]`，其中 `*` 是所有节点的通配符，`name` 函数将节点名称与给定值进行比较。

#### 相对寻址

上述示例使用所谓的**绝对寻址**，其概念类似于绝对文件系统路径。下一个示例涵盖使用*相对寻址*。

```php
<?php
// 返回所有具有 li 子节点的 ul 节点
$list = $xpath->query('/body//ul/li/..');
?>
```

其中 `/body//ul/li` 选择 `li` 节点，而 `/body//ul/li/..` 通过使用相对寻址（具体来说是 `..`）选择 `ul` 节点，这表明应返回寻址节点（`li`）的父节点，而不是寻址节点本身。请将其与在 UNIX 文件系统中使用相同序列引用当前目录的父目录进行比较。

#### 寻址属性

迄今为止的示例主要处理的是元素节点。XPath 也支持属性节点的选择。

```php
<?php
// 返回所有 ul 节点的 id 属性节点
$list = $xpath->query('//ul/@id');
// 返回所有具有 id 属性节点的 ul 节点
$list = $xpath->query('//ul/@id/..');
// 返回所有 id 属性节点
$list = $xpath->query('//@id');
?>
```

- `/ul/@id` 寻址与作为上下文节点后代的 `ul` 元素节点相关联的所有 `id` 属性节点。
- 请注意第二个示例中相对寻址的使用如何同样适用于属性节点，就像它适用于子元素节点一样。
- `/@id` 寻址上下文节点的所有 `id` 属性节点，无论它们关联于哪个元素。

#### 并集

在寻址节点时，可以使用多个表达式执行单个查询。这被称为寻址这些表达式的**并集**。

```php
<?php
// 返回所有 ul 和 ol 节点的 li 子节点
$list = $xpath->query('//ol/li|//ul/li');
// 返回所有 tr 节点的 th 和 td 节点
$list = $xpath->query('//tr/th|//tr/td');
?>
```

- 第一个示例返回无序（**ul**）列表和有序（**ol**）列表中所有的列表项（**li**）。
- 第二个示例返回表格行（**tr**）中所有的表头（**th**）和数据（**td**）单元格。

#### 条件

除了其周围的层级结构外，还可以基于**条件**来寻址节点。

```php
<?php
// 返回具有 id 属性节点的所有 ul 节点
$list = $xpath->query('//ul[@id]');
// 返回 id 为 "thelist" 的 ul 节点的所有 li 子节点
$list = $xpath->query('//ul[@id = "thelist"]/li');
// 返回上下文节点的第一个 ul 后代节点
$list = $xpath->query('//ul[1]');
// 返回每个 ul 节点的第一个 li 子节点
$list = $xpath->query('//ul/li[1]');
// 返回包含值为 "foo"bar" 的 li 节点的所有 ul 节点
$list = $xpath->query('//ul[li = "foo"bar]');
?>
```
