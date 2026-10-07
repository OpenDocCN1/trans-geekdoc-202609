

# 写入 DOM

DOMDocument 对象包含了用于操作写入 DOM 的方法。可以使用 `createElement()` 方法创建新元素，并使用 `createTextNode()` 方法插入文本内容。每个文本节点通过 `appendChild()` 方法添加到其周围的元素中，每个元素通过该方法添加到其更高层级的元素中。

此示例向 `books.xml` 中的书籍添加了一本完整的书，并使用 `save()` 方法创建一个新的、较大的 XML 文档。

![](img/7faa63a7fa0add8f53300594ebae949f_181_0.png)

```php
<?php
$dom = new DOMDocument();
$dom -> load("books.xml");

# 创建元素
$title = $dom -> createElement("title");
$topic = $dom -> createElement("topic");
$series = $dom -> createElement("series");
$pic = $dom -> createElement("pic");

# 创建文本节点
$topictext = $dom -> createTextNode("Linux");
$seriestext = $dom -> createTextNode("in easy steps");
$pictext = $dom -> createTextNode("linux.gif");

# 将文本节点添加到内部嵌套元素中
$topic -> appendChild($topictext);
$series -> appendChild($seriestext);
$pic -> appendChild($pictext);

# 将内部嵌套元素添加到 <title> 元素
$title -> appendChild($topic);
$title -> appendChild($series);
$title -> appendChild($pic);

# 现在将 <title> 元素添加到根元素
$dom -> documentElement -> appendChild($title);

# 创建一个新的较大的 XML 文档
$dom -> save("newbooks.xml");

?>
```

# ...接上

在网页浏览器中打开新的 XML 文档，可以确认每个新元素都已正确添加并嵌套在根元素内部。它们出现在最后一个原始“title”元素之后，并按照指定的适当文本内容作为摘要插入。

![](img/7faa63a7fa0add8f53300594ebae949f_182_0.png)

尽管此示例将更改保存在新文档中，但 DOM 可以进行“即时”操纵，并动态访问新元素。

```xml
http://localhost/newbooks.xml
<?xml version="1.0" encoding="iso-8859-1" ?>
<books>
  <title>
    <topic>JavaScript</topic>
    <series>in easy steps</series>
    <pic>js.gif</pic>
  </title>
  <title>
    <topic>C++ Programming</topic>
    <series>in easy steps</series>
    <pic>c+++.gif</pic>
  </title>
  <title>
    <topic>HTML</topic>
    <series>in easy steps</series>
    <pic>html.gif</pic>
  </title>
  <title>
    <topic>SQL</topic>
    <series>in easy steps</series>
    <pic>sql.gif</pic>
  </title>
  <title>
    <topic>Linux</topic>
    <series>in easy steps</series>
    <pic>linux.gif</pic>
  </title>
</books>
```

![](img/7faa63a7fa0add8f53300594ebae949f_182_1.png)

# 使用 XPath 查询

XPath 允许你对 XML 文档查询符合特定标准的特定节点。这比 `getElementsByTagName()` 方法要强大得多，后者简单地返回所有具有指定名称元素的 DomNodeList。例如，对于 XML 文档 `food.xml`（如下所示），调用 `getElementsByTagName("item")` 将返回 "fruit" 和 "veg" 元素中的所有 "item" 子元素。

![](img/7faa63a7fa0add8f53300594ebae949f_183_0.png)

```xml
<?xml version = "1.0" encoding = "iso-8859-1" ?>
<fruit>
  <item id="1">Apple</item>
  <item id="2">Banana</item>
  <item id="3">Cherry</item>
</fruit>
<veg>
  <item>Lettuce</item>
  <item>Onion</item>
</veg>
<food>
```

然而，XPath 可以返回特定的元素。

要在 PHP 5 中开始使用 XPath，必须先使用 "new" 关键字创建一个 DomXPath 对象，并将加载的 DomDocument 名称作为其参数。DomXPath 对象以与创建新 DomDocument 对象相同的方式被赋值给变量。

![](img/7faa63a7fa0add8f53300594ebae949f_183_1.png)

显著的是，DomXPath 对象有一个 `query()` 方法，可以返回符合其参数所指定标准的 DomNodeList。简单的查询指定了元素的路径，例如 "fruit/item"。

`query()` 方法用于返回 "fruit" 元素中所有 "item" 元素的 DomNodeList。下文列出的 PHP 脚本将 DomXPath 对象赋值给变量 "$xp"。它们的 textContent 然后以 HTML 列表的形式输出。

# 接上文

![](img/7faa63a7fa0add8f53300594ebae949f_184_0.png)

```html
<html><head><title>XPath Query</title></head><body>
<?php
# 将 XML 文档加载到 DOM
$dom = new DomDocument();
$dom -> load("food.xml");

# 创建 XPath 对象
$xp = new DomXPath($dom);

# 输出所有 fruit item 的列表
echo ("Fruit items are:<ul>" );
$fruits = $xp -> query("/food/fruit/item");
foreach($fruits as $node) {
echo("<li>" . $node ->textContent ."</li>"); }
echo("</ul>");
?>
</body></html>
```

# XPath DOM 查询

| 文件 编辑 查看 收藏 工具 帮助 |
|---|---|---|---|---|
| 地址: http://localhost/xpath-query.php | 转到 | | |

水果项目：

- Apple
- Banana
- Cherry

这只是一个简单的示例。进一步的查询可能包括：

- /food/fruit/item[position()=1] 返回第一个
- /food/fruit/item[@id='2'] 返回 id 为 2 的项目
- /food/veg/item 返回 veg 中的所有项目

# 使用 SimpleXML

SimpleXML 扩展提供了处理 XML 数据的一种方法。它允许你将 XML 元素视为可以通过属性访问的对象。要加载 XML 文件，请使用 `simplexml_load_file()` 函数。它返回一个 SimpleXML 对象，可以用于导航文档。

```php
<?php
$xml = simplexml_load_file("books.xml");
foreach($xml->title as $title) {
    echo "Title: " . $title . "\n";
    echo "Topic: " . $title->topic . "\n";
    echo "Series: " . $title->series . "\n";
    echo "Pic: " . $title->pic . "\n";
    echo "-----------------\n";
}
?>
```

