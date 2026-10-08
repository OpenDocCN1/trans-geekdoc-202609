

-   `/@id` 寻址上下文节点的所有 `id` 属性节点，无论它们关联于哪个元素。

## 并集

在寻址节点时，可以使用多个表达式执行单个查询。这被称为寻址这些表达式的**并集**。

```php
<?php
// 返回所有 ul 和 ol 节点的 li 子节点
$list = $xpath->query('//ol/li|//ul/li');
// 返回所有 tr 节点的 th 和 td 节点
$list = $xpath->query('//tr/th|//tr/td');
?>
```

-   第一个示例返回无序（**ul**）列表和有序（**ol**）列表中所有的列表项（**li**）。
-   第二个示例返回表格行（**tr**）中所有的表头（**th**）和数据（**td**）单元格。

## 条件

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

-   方括号用于界定条件表达式。
-   在条件内部，元素和属性节点的表示方式与在条件外部相同。也就是说，元素仅通过元素名称引用，而属性名称前缀为 @。
-   = 运算符用于相等性比较。反之，!= 运算符用于检查不等性。还支持其他一些标准的比较运算符，包括 <、<=、> 和 >=。
-   仅由单个数字组成的条件实际上是 position() = # 的简写形式，其中 # 是使用的数字。position 是一个函数，返回当前上下文中每个单独节点的位置。

# 资源

这里只涵盖了 XPath 提供功能的一小部分，主要是基本概念以及在使用 XPath 从检索到的标记文档中提取数据时最可能适用的领域。其他函数、运算符以及更高级的概念在本章末尾引用的资源中有更详细的说明。为了进行更广泛和更复杂的数据提取应用程序，强烈建议查阅这些资源。

-   PHP 手册中的 DOM 文档：http://php.net/dom
-   XML 和 XPath 的优秀概述：http://schlitt.info/opensource/blog/0704_xpath.html
-   XML 的更多信息：http://en.wikibooks.org/wiki/XML:_Managing_Data_Exchange
-   DOM 第三级核心标准：`http://www.w3.org/TR/DOM-Level-3-Core`
-   DOM 第三级 XPath 标准：`http://www.w3.org/TR/DOM-Level-3-XPath`

# 第 11 章

# SimpleXML 扩展

与 DOM 扩展一样，SimpleXML 扩展也提供了一个树解析器。然而，DOM 扩展保持其 API 与其基于的标准非常一致。与 DOM 扩展的 API 相比，SimpleXML 提供的 API 对大多数 PHP 开发者来说更少、更直观且更易于使用。

SimpleXML 通过使用 PHP 数组来访问具有相同元素名的集合中的单个元素以及元素属性，利用了 PHP 数组的灵活性和多功能性。它还使标记文档具有可迭代性，使其遍历变得简单。

然而，这些优势并非没有代价。与其他树解析器一样，SimpleXML 必须解析整个文档后才能使用。因此，在解析比 XMLReader（稍后将介绍）这样的拉取解析器更大的文档时，它往往速度较慢。但对于处理较小文档的脚本而言，SimpleXML 在紧急情况下工作得很好。

# 加载文档

在 DOM 扩展中，DOMDocument 是核心类，而 SimpleXMLElement 是 SimpleXML 扩展中的对应类。加载标记文档只需通过类构造函数指定即可。

```php
<?php
// 加载已包含在字符串中的标记
$exe = new SimpleXMLElement($markupString);

// 加载包含在外部文件中的标记
$exe = new SimpleXMLElement($filePath, null, true);
?>
```

构造函数的第二个参数（在上述第二个示例中指定为 null）允许对该实例进行进一步配置。对于标记不太有效的文档，将此参数的值设置为 LIBXML_NOERROR | LIBXML_NOWARNING 可能很有用，因为它会抑制错误和警告报告。

最后，第二个构造函数调用中使用的第三个参数设置为 true，以指示 $filePath 实际上是包含标记的文件路径，而不是标记本身。

## 访问元素

使用 SimpleXML 看起来有点像是 XPath 表达式，除了通过 API 以编程方式实现相同的效果，而不是通过存储在字符串中的格式化表达式。与 XPath 表达式不同，SimpleXML 自动假设元素访问是相对于根节点的。

```php
<?php
$markupString = '
<html>
<body>
<ul id="thelist">
<li>Foo</li>
<li>Bar</li>
</ul>
</body>
</html>
',

// 输出 "Foo" -- 注意未引用 "html" 元素
$exe = new SimpleXMLElement($markupString);
echo $exe->body->ul->li[0];

// 也有效，如果存在多个 "li" 元素，则假设第一个 "li" 元素
echo $sxe->body->ul->li;

// 也输出 "Foo" -- 注意这次引用了 "html"
$doc = new DOMDocument();
$doc->loadHTML($markupString);
$xpath = new DOMXPath($doc);
echo $xpath->evaluate('/html/body/ul/li[0]');

// 输出 "ul"
echo $sxe->body->ul->getName(), PHP_EOL;

// 输出 "Foo" 然后 "Bar"
foreach ($sxe->body->ul->li as $li) {
    echo $li, PHP_EOL;
}

// 做同样的事
foreach ($sxe->body->ul->children() as $li) {
    echo $li, PHP_EOL;
}
?>
```

当引用当前元素的子元素时（例如通过上述 $sxe 的 body 属性），请注意正在访问的子元素也是 SimpleXMLElement 的一个实例。这意味着不仅可以链接元素访问，还可以使用变量引用此类链接中的最后一个元素。参见上述第一个 foreach 循环作为这两点的示例。

## 访问属性

在访问元素时，对于访问同一层级上具有相同名称的多个元素使用枚举数组，而在访问属性时使用关联数组。以下示例使用与上一个示例相同的 $markupString 样本数据。

```php
<?php
// 输出 "thelist"
echo $sxe->body->ul['id'];

// 输出 "id=thelist"
foreach ($sxse->body->ul->attributes() as $name => $value) {
    echo $name, '=', $value, PHP_EOL;
}

// 另一种输出 "thelist" 的方法
$attrs = $sxse->body->ul->attributes();
echo $attrs->id;
?>
```

attributes() 方法实际返回的是一个 SimpleXMLElement 实例，该实例以 SimpleXMLElement 通常使子元素及其值可用的方式提供对属性名称和值的访问。因此，返回的实例可以作为 foreach 循环的主题，以迭代它公开的属性。

```
<!-- 实际标记 -->
<ul id="thelist"></ul>

<!-- attributes() 如何将其作为 SimpleXMLElement 实例公开 -->
<ul>
    <id>thelist</id>
</ul>
```

![](img/1e839861f06c77df9ecabc0aed9127b5_135_0.png)

# 一个调试缺陷

影响 SimpleXML 扩展的缺陷 #44973 报告称存在于 PHP 5.2.6 中，并且可能存在于其他版本中。当尝试使用 echo、print_r()、var_dump() 和其他类似函数通过 SimpleXMLElement 实例访问并输出节点时，会暴露此缺陷。如果节点同时具有属性和文本值，这些函数的输出中不会显示属性。这并不意味着在这种情况下属性值无法访问；只是它们无法以这种方式输出，除非直接引用。有关此问题的更多信息，请访问 http://bugs.php.net/bug.php?id=44973。

