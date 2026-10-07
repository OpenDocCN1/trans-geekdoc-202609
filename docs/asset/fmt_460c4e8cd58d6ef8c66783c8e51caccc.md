
你可以在 PEAR 网站 (`http://pear.php.net/package/HTML_Table/docs`) 上找到 `HTML_Table` 的文档，在你的 PEAR 路径下的 `doc/HTML_Table/docs` 文件夹中应该有一些示例脚本，展示如何使用 `HTML_Table`。以下是 `HTML_Table` 最重要方法的快速概述：

| 方法 | 说明 |
| --- | --- |
| `HTML_Table($attrs, $tabOffset, $useTGroups)` | `HTML_Table` 构造函数。所有三个参数都是可选的。`$attrs` 是要添加到起始 `<table>` 标签的属性数组（以键/值对形式）。`$tabOffset` 指定了表格标记缩进的制表符数量（默认为 0）。`$useTGroups` 指定了是否在表格中使用使用 `<tfoot>` 和 `<tbody>` 元素（默认为 false，即意味着不使用它们）。 |

| 方法 | 说明 |
| --- | --- |
| `addRow($contents, $attrs, $type, $inTR, $body)` | 向表格添加一行单元格。`$contents` 以索引数组的形式存储行数据，其中每个元素是单个单元格的数据。可选的 `$attrs` 参数包含应用到该行的属性，可选的 `$type` 参数可以是 `'th'`（用于表头单元格）或 `'td'`（用于数据单元格）——默认是 `'td'`。将 `$inTR` 参数设置为 true 以将属性应用到 `<tr>` 元素而不是 `<td>`/`<th>` 元素（默认）。如果你正在使用 `<tbody>` 元素，请将 `<tbody>` 组指定为 `$body` 参数。（使用 `addBody()` 添加新主体 - 详情请阅在线文档。） |
| `addCol($contents, $attrs, $type, $body)` | 添加一列单元格。参数的工作方式与 `addRow()` 相同。 |
| `altRowAttributes($start, $attrs1, $attrs2, $inTR, $body)` | 允许为每隔行的表格设置不同的属性，从而创建交替行。`$start` 是开始交替的行索引，`$attrs1` 和 `$attrs2` 是包含要应用到每个交替行的属性关联数组或字符串。可选的 `$inTR` 和 `$body` 参数的工作方式与 `addRow()` 相同。 |
| `setCell($row, $col, $contents, $type, $body)` | 允许你设置或更改任意单元格的内容。单元格通过 `$row` 和 `$col` 指定（从 0 开始计数）。 |
| `setGrow($grow, $body)` | 返回 HTML 标记。 |
| `setHeader($row, $col, $contents, $type, $body)` | 允许你设置或更改任意单元格的内容。单元格通过 `$row` 和 `$col` 指定（从 0 开始计数）。 |
| `setCell($row, $col, $contents, $type, $body)` | 允许你设置或更改任意单元格的内容。单元格通过 `$row` 和 `$col` 指定（从 0 开始计数）。 |
| `setGrow($grow, $body)` | 返回 HTML 标记。 |

等等，基于提供的 OCR 文本，表格相当混乱。让我们根据现有的碎片正确重建方法表：

| 方法 | 说明 |
| --- | --- |
| `HTML_Table($attrs, $tabOffset, $useTGroups)` | `HTML_Table` 构造函数。所有三个参数都是可选的。`$attrs` 是要添加到起始 `<table>` 标签的属性数组（以键/值对形式）。`$tabOffset` 指定了表格标记缩进的制表符数量（默认为 0）。`$useTGroups` 指定了是否在表格中使用 `<tfoot>` 和 `<tbody>` 元素（默认为 false，即意味着不使用它们）。 |
| `addRow($contents, $attrs, $type, $inTR, $body)` | 向表格添加一行单元格。`$contents` 以索引数组的形式存储行数据，其中每个元素是单个单元格的数据。可选的 `$attrs` 参数包含应用到该行的属性，可选的 `$type` 参数可以是 `'th'`（用于表头单元格）或 `'td'`（用于数据单元格）——默认是 `'td'`。将 `$inTR` 参数设置为 true 以将属性应用到 `<tr>` 元素而不是 `<td>`/`<th>` 元素（默认）。如果你正在使用 `<tbody>` 元素，请将 `<tbody>` 组指定为 `$body` 参数。（使用 `addBody()` 添加新主体 - 详情请阅在线文档。） |
| `addCol($contents, $attrs, $type, $body)` | 添加一列单元格。参数的工作方式与 `addRow()` 相同。 |
| `altRowAttributes($start, $attrs1, $attrs2, $inTR, $body)` | 允许为每隔行的表格设置不同的属性，从而创建交替行。`$start` 是开始交替的行索引，`$attrs1` 和 `$attrs2` 是包含要应用到每个交替行的属性关联数组或字符串。可选的 `$inTR` 和 `$body` 参数的工作方式与 `addRow()` 相同。 |
| `setCell($row, $col, $contents, $type, $body)` | 允许你设置或更改任意单元格的内容。单元格通过 `$row` 和 `$col` 指定（从 0 开始计数）。 |
| `setGrow($grow, $body)` | 返回 HTML 标记。 |
| `setHeader($row, $col, $contents, $type, $body)` | 允许你设置或更改任意单元格的内容。单元格通过 `$row` 和 `$col` 指定（从 0 开始计数）。 |

实际上，查看文本片段：

# 尝试显示斐波那契数

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
<title>使用 HTML_Table 的斐波那契数列</title>
<link rel="stylesheet" type="css" href="common.css" />
<style type="text/css">
th { text-align: left; background-color: #999; }
td { padding: 0.4em; }
td.alt { background: #ddd; }
</style>
</head>
<body>
<h2>使用 HTML_Table 的斐波那契数列</h2>
<?php
require_once ("HTML/Table.php");
$attrs = array("cellspacing" => 0, "border" => 0, "style" => "width: 20em; border: 1px solid #666;");
$table = new HTML_Table($attrs);
$table->addRow( array( "序列 #", "值", null, "th" );
$iterations = 10;
$num1 = 0;
$num2 = 1;
$table->addRow( array( "F0", "0" ));
$table->addRow( array( "F1", "1" ));
for ($i=2; $i <= $iterations; $i++) {
    $sum = $num1 + $num2;
    $num1 = $num2;
    $num2 = $sum;
    $table->addRow( array( "F$i", $num2 ));
}
$attrs = array("class" => "alt");
$table->addAttributes(1, null, $attrs, true);
echo $table->toHtml();
?>
</body>
</html>
```

# 第三部分：在实践中使用 PHP

## 工作原理

在创建了 XHTML 页面头部（包括用于样式化表格的额外 CSS 规则）后，脚本包含了 HTML_Table PEAR 包：

```php
require_once("HTML/Table.php");
```

接下来，脚本为 `<table>` 标签设置了一个属性关联数组，然后使用这些属性创建一个新的 HTML_Table 对象：

```php
$attrs = array("cellspacing" => 0, "border" => 0, "width" => "20em; border: 1px solid #666;");
$table = new HTML_Table($attrs);
```

通过调用 `addRow()` 方法并传递单元格数据数组来创建双单元格表头。注意 `$type` 参数被设置为 "th"，以确保创建头单元格：

```php
$table->addRow(array("Sequence #", "Value", null, "th"));
```

脚本的其余部分与第 4 章非常相似，用调用 HTML_Table 方法替换了旧的 HTML 标记。在设置好循环和两个变量后，创建了表格的前两行：

```php
$table->addRow(array("<th>0</th>", "0"));
$table->addRow(array("<th>1</th>", "1"));
```

在循环内部，通过调用 `addRow()` 向表格添加新行：

```php
$table->addRow(array("<th>$num2</th>", $num2));
```

循环结束后，调用 `altRowAttributes()` 方法来设置交替表格行。从表头行之后的行开始计算，每隔第二行被赋予一个 CSS 类 "alt"：

```php
$attrs = array("class" => "alt");
$table->altRowAttributes(1, null, $attrs, true);
```

最后，只需调用表格对象的 `toHtml()` 方法即可显示表格标记：

```php
echo $table->toHtml();
```

你可以从这个示例中看到使用 HTML_Table 创建表格是多么简单。生成的 PHP 代码也非常整洁且易于修改。此外，一旦你开始使用如 `setAutoGrow()` 和 `setCellContents()` 等 HTML_Table 方法，你只需要几行代码就可以创建（并修改）非常复杂的表格。

# 第 15 章：使用 PEAR 让你的工作变得更容易

## 使用 HTML_QuickForm 轻松构建 Web 表单

正如 HTML_Table 允许你通过编程方式创建 HTML 表格——从而使你的代码整洁且灵活——HTML_QuickForm 包提供了一个类用于创建 Web 表单，而无需在脚本中包含单行 HTML 代码。更重要的是，HTML_QuickForm 可以处理它创建的表单，减轻了你编写（以及测试）验证、过滤和错误报告代码的负担。

在接下来的章节中，你将查看 HTML_QuickForm 包的功能，然后利用 HTML_QuickForm 的功能创建一个会员表单脚本。

## 安装 HTML_QuickForm

HTML_QuickForm 的安装正如你预期的那样。例如在 Ubuntu 上，只需运行 `pear install --alldeps HTML_QuickForm` 即可：

```bash
pear install --alldeps HTML_QuickForm
downloading HTML_QuickForm-3.2.10.tgz
Starting to download HTML_QuickForm-3.2.10.tgz (101,851 bytes)
......................................done: 101,851 bytes
downloading HTML_Common-1.2.4.tgz
Starting to download HTML_Common-1.2.4.tgz (4,519 bytes)
.......................................done: 4,519 bytes
install ok: channel://pear.php.net/HTML_Common-1.2.4
install ok: channel://pear.php.net/HTML_QuickForm-3.2.10
```
