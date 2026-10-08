

...类到后续 if 分支案例中，指示迭代器指向的节点位于目标表格内部。

当遇到表格行元素时，进入下一个 if 分支。通过检查节点名称和先前设置的 `$inTable` 标志来促进这一过程。当进入该分支时，`$tableData` 数组中的新元素被初始化为空数组。该数组稍后将存储该行中单元格的数据。与 `$tableData` 中该行关联的键存储在 `$row` 变量中。

最后，当遇到表格单元格元素时执行最后一个 if 分支。与行分支类似，此分支检查节点名称和 `$inTable` 标志。如果检查通过，则会将当前节点的值存储在关联于当前表格行的数组中。

这就是 XMLREADER::END_ELEMENT 节点类型发挥作用的地方。一旦到达表格末尾，就不应将更多数据读入数组。因此，如果结束元素名为 'table'，且 `$inTable` 标志当前指示迭代器指向目标表格内的节点，则将该标志设置为 false。由于理论上没有其他表格应拥有相同的 id 属性，因此在后续 while 循环迭代中不会执行任何 if 分支。

如果该表格是文档中唯一感兴趣的表格，将 `$inTable = false;` 语句替换为 `break 2;` 语句是明智的。这将在遇到表格末尾时终止用于从文档读取节点的 while 循环，防止任何进一步的无谓读取操作。

## readString() 可用性

正如 PHP 手册条目中所述，上述示例中使用的 `readString()` 方法仅在 XMLReader 扩展针对特定版本的底层 libxml 库编译时才存在。

如果你的环境中此方法不可用，示例中的替代方案是使用开/关表格单元格检查来切换它们自己的标志（例如 `$inCell`），并为 TEXT 和 CDATA 节点类型添加情况，这些情况会检查该标志，并且当标志设置为 true 时，将 XMLReader 实例的 `value` 属性的内容添加到 `$tableData` 数组中。

### DOM 互操作

XMLReader 扩展的一个良好特性是 `expand()` 方法，它返回迭代器当前指向的节点对应的 DOM 扩展类对象。例如，元素节点导致此方法返回 DOMElement 实例。

下面的示例说明了前一个示例的修改，并利用这种 DOM 互操作性提供了获取表格单元格内容的 `readString()` 方法的另一种替代方案。

```php
<?php
if ($doc->localName == 'td' && $inTable) {
    $node = $doc->expand();
    $tableData[$row][] = $node->nodeValue;
}
?>
```

### 关闭文档

在对文档执行所有必要的读取操作后，应调用 XMLReader 实例的 `close()` 方法，以干净地终止文件访问，或者以其他方式表明不再需要访问原始数据源。

### 总结

希望本章能让你了解拉式解析器（pull parsers）通常是如何工作的，以及在何时使用 XMLReader 这样的解析器比使用树解析器更好。要获取更多关于 XMLReader 的信息，请查看 PHP 手册中位于 <http://www.php.net/manual/en/book.xmlreader.php> 的相应章节。

## 第 13 章

### CSS 选择器库

本章将回顾几个建立在前面章节描述的 XML 扩展之上的库。这些库提供了使用 CSS 选择器表达式来查询标记文档的接口，而不是使用编程 API 或 XPath 表达式。如果你对 CSS 选择器不熟悉，请不要担心，因为本章的一部分将展示基本表达式及其 XPath 等价物。

![](img/1e839861f06c77df9ecabc0aed9127b5_148_0.png)

**CSS 版本**

CSS 标准有多个版本，支持的随版本变化的选择器各不相同。本章将涵盖 CSS3 中可用选择器的一个子集。特定库支持的 CSS 标准版本会在可用的情况下注明。可以在 <http://www.w3.org/TR/css3-selectors/#changesFromCSS2> 找到两个常见版本 CSS2 和 CSS3 之间差异的列表。

### 使用它们的理由

在深入探讨使用 CSS 选择器库的“如何”之前，最好先弄清“为什么”（以及“为什么不”）。不用说，这些库为使用它们的应用程序增加了一层复杂性，引入了另一个潜在的故障点。为了实现将 CSS 选择器表达式作为输入并将其转换为等效的 userland 操作，它们实现了表达式解析器，这可能会影响性能。

除上述观点外，它们确实提供了一些被认为更直观的语法。如今大多数开发人员至少了解一些 CSS，并且很可能对使用 CSS 选择器在客户端进行节点选择的 JavaScript 库（例如 jQuery）有一点经验。因此，当使用基于此的库时，该特定领域的知识可以转移到服务器端。

总而言之，如果你特别关注性能或应用程序的简洁性（相对于其依赖组件的数量），最好坚持使用像 XPath 这样的工具。否则，CSS 选择器库值得考虑，以便利用现有的通用技能集。

即使你的决定是坚持使用 XPath，请继续阅读。本章还将展示每组已解释 CSS 选择器的 XPath 等价物，这可能有助于进一步加深你对 XPath 的理解。请注意，这些比较并不一定是全面的，并且在任何给定情况下，可能有多种方式来表达相同的内容。

![](img/1e839861f06c77df9ecabc0aed9127b5_149_0.png)

### jQuery 示例

jQuery 库本身的文档实际上拥有出色的选择器可视化客户端示例。如果你不确定是否理解下面任何 CSS 选择器的描述，jQuery 演示和源代码很可能会证明是有益的补充。你可以在 <http://api.jquery.com/category/selectors/> 找到它们。

### 基础

让我们查看一些基本选择器及其应用于标记示例时的结果。

```html
<html>
<body>
  <div id="nav">
    <ul class="horizontal">
      <li><a href="/home">Home</a></li>
      <li><a href="/about-us">About Us</a></li>
      <li><a href="/contact-us">Contact Us</a></li>
    </ul>
    <img src="/img/ad1.jpg" alt="Advertisement #1">
    <img src="/img/ad2.jpg" alt="Advertisement #2">
  </div>
</body>
</html>
```

- `#nav` 将选择 div 元素，因为它的 id 属性值为 nav。
- `li` 将根据节点名称选择所有 li 元素。
- `.horizontal` 将选择 ul 元素，因为它具有 horizontal 类。（注意元素可以具有多个类。）
- `*` 将选择文档中的所有元素。
- `li, a` 通过将两个选择器 li 和 a 组合成逗号分隔列表来选择文档中所有的 li 和 a 元素。

以下是各自的 CSS 对应项旁边的 XPath 等价项。除了 .class 选择器外，XPath 表达式并没有显著变长或变得复杂。

| 选择器 | CSS | XPath |
| :--- | :--- | :--- |
| id | `#nav` | `//*[@id="nav"]` |
| 元素 | `li` | `//li` |
| 类 | `.horizontal` | `//*[@class="horizontal"] or starts-with(@class, "horizontal ") or contains(@class, " horizontal ") or ends-with(@class, " horizontal ")` |
| 通配符 | `*` | `//*` |
| 多重 | `li, a` | `//li | //a` |

### 层级选择器

现在让我们继续讨论层级选择器，它们使用文档结构作为选择元素的方式，使用之前的标记示例。

- `body ul` 将选择所有 body 元素的 descendants（后代）中的 ul 元素。
- `ul > li` 将选择所有 ul 元素的 children（子级）中的 li 元素。
- `ul + img` 将选择所有紧随 ul 兄弟元素之后的 img 元素（即它们的下一个兄弟）。
- `ul ~ img` 将选择所有跟随 ul 兄弟元素的 img 元素（即它们之后且拥有相同父节点）。

此列表中的第三项和第四项可能看起来非常相似。区别在于“immediately”（紧接）这个词。在此示例中，列表中的第三项只会选择 Advertisement#1 图像，因为它紧接在文档中其 ul 兄弟元素之后。另一方面，列表中的第四项将选择两个图像，因为两个都跟随其 ul 兄弟元素。

| **选择器** | **CSS** | **XPath** |
| --- | --- | --- |
| 祖先 后代 | `body ul` | `body//ul` |
| 父级 > 子级 | `ul > li` | `//ul/li` |
| 前 + 后 | `ul + img` | `//ul/following-sibling::img[1]` |
| 前 ~ 兄弟 | `ul ~ img` | `//ul/following-sibling::img` |

### 基本过滤器

本章到目前为止回顾的选择器始终改变所选择节点的 *类型*。相反，当在表达式后附加过滤器时，它仅仅是将返回的节点集限制为匹配原始表达式的子集。

请注意，可用的过滤器因库而异。jQuery 对过滤器的支持相当全面，因此在本章中，它被用作与过滤器相关部分的主要参考。

