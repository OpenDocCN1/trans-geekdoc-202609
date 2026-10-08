
# 第 20 章.与 HTML 集成

## 在 HTML 文档中穿插 PHP

- 使用 PHP 输出所有 HTML
- 将 HTML 与 PHP 分离
- 创建 <SELECT> 字段
- 在表单中传递数组

到此时，你已经学习了 PHP 的基础知识。你有了一份函数参考，并且已经接触了一些编程中的基础问题。但我在这里看到的所有示例都是为了说明问题而提供的片段或代码块。本章将讨论如何将 PHP 集成到网站中。它将展示如何将 PHP 穿插于整个网站，或者简单地创建几个由 PHP 驱动的页面。我还将讨论使用 PHP 生成 HTML 时涉及的问题。

## 在 HTML 文档中穿插 PHP

使用 PHP 的第一个也是最明显的方法是像你一直以来那样构建 HTML 文件，并将 PHP 标签当成 HTML 标签一样插入其中。这可以表现为重复 HTML 标签，并将其替换为 PHP 函数的调用。它也可以表现为一个生成数据库输出的大型 PHP 代码块。或者是一个处理表单提交的脚本。在这些情况下，PHP 对网站的影响是微乎其微。对于编程初学者来说，这是一个很好的第一步。你能够插入最少的 PHP 代码进行测试。随着经验和信心的增长，你对 PHP 的依赖程度也会之增加。

让我们查看创建一个函数来替换重复的 HTML。层叠样式表（CSS）的一个大优势是它们允许你重新定义标签的行为。遗憾的是，这项技术在 Navigator 和 Internet Explorer 的最新版本中可用。你可以通过 PHP 在服务器端提供一些功能。假设我们所有的标题都是大写字母、7 号字体且蓝色。解决方案是编写一个函数，接收一个字符串并以正确的格式打印它。

在列表 20.1 中，我创建了一个名为 `PrintTitle` 的函数。该函数将给字符串封装在标签中。在某些情况下，这段代码比我直接写成静态 HTML 更具可读性，因为每次有标题时，我们调用 `PrintTitle` 函数。这可能比它代表的标签集合具有更多意义。这是函数的通用优点之一：它们将功能封装在一个单一名称中。

## PHP 核心编程

另一个优点是，我可以确保每个标题都以完全相同的方式渲染。每个标题需要输入的文本越少，意味着漏掉公式部分的概率越小。这对程序员来说是非常棒的，他们无疑渴望找到输入长段相同 HTML 的捷径。这确保了更高程度的质量。如果漏掉了函数调用，PHP 将显示错误。如果没有显示任何错误，则标题很可能显示且格式正确。如果标题结果没有变化，则只需在一个地方修改代码。这是应对那句痛苦的短语“我改变主意了……”的良好解药。

PHP 的另一个类似用途是为本质上是 CGI 输出的内容进行装饰：一个被 HTML 包围的大型 PHP 代码块，使得代码的输出直接出现在一个更大的页面中。这是 SSI（服务器端包含）提供的类似方法。SSI 标签可以调用 CGI 并将其输出插入到页面中。

当你的网站大部分是静态的，但关键区域必须是动态的时，这种方法是合适的。它的优点是对 Web 服务器的开销非常低。只有在绝对必要时才使用 PHP。在列表 20.2 中，代码生成了不会更改的信息，但很容易想象代码是从数据库中提取引言。它消除了每次信息变化时都编辑 HTML 页面的需求，但不会改变的部分（如页面布局）仍留为静态 HTML。

虽然列表 20.2 是动态输出的示例，但你经常面临相反的情况。你的网站可能是完全静态的，但你需要接收目录请求。PHP 是接收表单的良好解决方案。第一步是创建一个询问姓名和地址的 HTML 页面。列表 20.3 演示了这一点。

# 列表 20.1 格式化函数

```php
<?php
function PrintTitle($title)
{
    print("<CENTER>");
```

这是一个使用函数重复常用 HTML 代码的示例。<BR><BR><?php PrintTitle("how it works"); ?>\n任何需要创建标题时，都会调用带有标题文本的 <CODE>PrintTitle</CODE> 函数。<BR>

<?php PrintTitle("advantages"); ?>
代码更具可读性<BR>
每个标题输入的文本更少<BR>
易于更改每个标题<BR>
</</body>
</html>

列表 20.3 中的页面是一个非常简单的提交表单。当点击按钮时，每个输入标签都将转换为 PHP 变量。这会调用列表 20.4 中列出的脚本。将打开一个名为 `req.txt` 的文件进行追加，并将每个表单字段写入电子表格中。每个字段之间用制表符分隔，这允许你轻松地向电子表格输入数据。

# 列表 20.2 装饰 CGI 输出

```php
<HTML>
<HEAD>
<TITLE>Listing 20.2</TITLE>
</HEAD>
<body>
<h1>颜色图</h1>
<P>下图表显示了在所有浏览器中显示安全的颜色。这些颜色在调色板至少有 256 种颜色的计算机上不应出现抖真。</P>
<P>此图表仅会在支持表格单元格背景色的浏览器上显示。</P>
<?php
$color = array("00", "33", "66", "99", "CC", "FF");

for($Red = 0; $Red < count($color); $Red++) {
    print("<table>\n");
    for($Green = 0; $Green < count($color); $Green++) {
        print("<tr>\n");
```

```php
for($Blue = 0; $Blue < count($color); $Blue++)
{
$CellColor = $color[$Red] .
$color[$Green] .
$color[$Blue];
    print("<TD BGCOLOR=$CellColor>");
    print("<TT>$CellColor</TT>");
    print("</TD\n");
}
print("</TR>\n");
print("</TABLE>\n");
?>
```

# 列表 20.3 目录请求表单

```html
<HTML>
<HEAD>
<TITLE>Listing 20.3</TITLE>
</HEAD>
<BODY>
请输入姓名和地址以接收免费目录。
<FORM ACTION="20-4.php">
<TABLE>
<TR>
<TD>Name</TD>
<TD><INPUT TYPE="text" NAME="InputName"></TD>
</TR>
<TR>
<TD>Address</TD>
<TD><INPUT TYPE="text" NAME="InputAddress"></TD>
</TR>
</TABLE>
</FORM>
</BODY>
```

# 列表 20.4 表单提交

```php
<HTML>
<HEAD>
<TITLE>Listing 20.4</TITLE>
</HEAD>
<body><?php
/** 处理输入 **/
$CatalogRequests = fopen("req.txt", "a");
if ($CatalogRequests) {
    fputs($CatalogRequests, $_POST['InputName'] . "\t");
    fputs($CatalogRequests, $_POST['InputAddress'] . "\t");
    fputs($CatalogRequests, $_POST['InputCity'] . "\t");
    fputs($CatalogRequests, $_POST['InputState'] . "\t");
    fputs($CatalogRequests, $_POST['InputZIP'] . "\n");
    fclose($CatalogRequests);
}
?>
感谢您的请求！<BR>
<A HREF="20-3.html">返回网站</A>
</body>
</HTML>
```

## 使用 PHP 输出所有 HTML

## PHP 核心编程

前一节中的任何示例都是向网站引入 PHP 的极佳第一步。我喜欢认为启用 PHP 的网站，因为它们只有一对 PHP 标签。输出来自 PHP 脚本。一旦信息被放入 PHP 变量中，就可以对其添加动态内容。它还具有更可读性的优势。作为一个简单的例子，比较列表 20.5 和 20.6。我发现，虽然这需要额外的时间，但代码更具维护性。我的经验是将所有 HTML 放在 PHP 脚本中允许快速更改。我不需要在列表 20.5 的 HTML 中搜索打开和闭合标签。它还允许我在源代码中拆分成几行，但在输出中显示为单行。输出是标题文本。它可以增强可读性而不会牺牲精确性。这在处理表格时变得非常有用。在 TD 和图像之间留任何空白都会导致额外的像素出现。这些技术的实用性与其他技术一样，随着项目规模的扩大而增加。我用两种方法创建过 50 页的 Web 应用程序，并证明将所有内容放在 PHP 代码中的价值。

# 列表 20.5 混合 PHP 和 HTML

```php
<HTML>
<HEAD>
<TITLE>Listing 20.5</TITLE>
</HEAD>
<body><?php
$Hour = date("H");
$Intensity = round($Hour/24.0) * (0xFF);
$PageColor = dechex($Intensity) . 
dechex($Intensity) . 
dechex($Intensity);
?>
<BODY BGCOLOR="<?php print($PageColor); ? ?>">
<h1>Listing 20.5</h1>
</BODY>
</HTML>
```

