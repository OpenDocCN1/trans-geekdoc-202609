
```
{
echo "Between 50 and 99.";
}
}
```

![](img/de0823012275cf4ceebdb822a56e6b71_199_0.png)

你是否遇到无法识别的解析错误？请确保大括号和圆括号的开启和关闭数量相同。如果页面中有五个闭合大括号而只有三个开启，那么你一定没有关闭其中一个代码块。

## 函数调用

缩进代码不应止于代码块。经常你需要使用嵌套的函数调用或占用多行的复杂变量。在这些情况下使用缩进，你的编程生活会更愉快。以下示例取自 Catalog 应用，请看一下。

```
$file_ext = strtolower(
    substr($file
    , strrpos($file,".")
    )
);
```

这段代码的目的很简单：它取一个文件名并将其扩展名（最后一个点“.”之后的字符）赋给 $file_ext。完成此操作需要三个独立的内置 PHP 函数。PHP 会先执行最内层。此时，strrpos() 找到最后一个点的数字位置。例如，在字符串 myfile.jpg 中，它会返回 6。然后 substr() 函数只返回点之后的字符。最后，该字符串会被转换为小写字符。

这可以写在一行上，但正如你所见，这样读起来相当困难。

```
$file_ext = strtolower(substr($file, strrpos($file,".")));
```

![](img/de0823012275cf4ceebdb822a56e6b71_199_1.png)

或者你觉得这样读起来更容易。本章中我们要讨论的很多事情都是个人偏好的问题。重要的是，你要花大量时间考虑如何使代码尽可能易读。

在该代码的第一个示例中，更容易看出每个闭合圆括号对应什么，并且可以更快地了解这段代码实现了什么以及如何实现。

![](img/de0823012275cf4ceebdb822a56e6b71_200_0.png)

你可能会想用临时变量赋值的方式来写上面的代码。类似这样：

```
$file_ext = strrpos($file, ".");
$ext_letters = substr($file, $file_ext);
$lower_ext_letters = strtolower($file_ext);
```

但这样会慢很多。变量赋值确实需要时间，在不需要的地方使用临时变量赋值要避免，尤其是在短小的代码中。话虽如此，你绝不应牺牲可读性。在某些地方，临时变量可以帮助使代码更易读。

## SQL 语句

在 Web 数据库应用中，SQL 语句会散布在 PHP 代码各处。通常 PHP 变量会包含在 SQL 语句中，以便根据变量数据获取特定结果。缩进 SQL 语句有助于保持代码的可读性和可维护性。下面我们展示几种类型的 SQL 语句示例。你将在本书第三部分和第四部分的应用中看到很多这些示例。

```
//2 table select
$query ="select n.fname, n.lname, c.co_name, c.co_address,
        c.co_zip
        from names n, companies c
        where n.name_id = $name_id
          and n.co_id = $co_id
";
```

```
//update query
$query="update products
    set product = '$product'
    , description = '$cleandsc'
    , price = $nullprice
    , image_src = $nullimage_src
    where product_id = $product_id
";
```

```
//insert query
$query="insert into products
(category_id, product)
values ($category_id, '$product')
";
```

![](img/de0823012275cf4ceebdb822a56e6b71_201_0.png)

我们听说过数据库引擎拒绝处理像上面那样包含换行符的查询的说法。这对 MySQL 来说不是问题，对大多数数据库也不会是问题。然而，编写查询还有其他完全可接受的方式。以下是几个示例：

```
$query = "select col_1, col2 ";
$query .= "from table_1, table_2 ";
$query .= "where col_1 = $var";
or:
$query = "select col_1, col_2 "
    ."from table_1, table_2 "
    ."where col_1 = $var";
```

选择你最喜欢的一种。

## 包含文件

每种语言都有包含外部文件的功能。PHP 有四个命令可以实现这一点。在介绍这些命令之前，我们将简要讨论为什么包含文件对于编写结构化和可读的代码如此关键。我们从一个非常常见的示例开始。

在大多数网站中，页眉信息从页面到页面变化很小。有开始标签（<HTML>、<HEAD> 等），也许还有一些导航信息。以下是 HTML 页面典型的页眉。

```
<HTML>
<HEAD>
    <TITLE>My Page Name</TITLE>
</HEAD>
<body bgcolor="#FFFFFF" link="#8e0402" vlink="#20297c">
```

在网站的每个文件中都输入这段文本绝对是浪费。而且可能很麻烦。假设你想在整个站点中更改 <body> 标签的 bgcolor 属性。如果此信息在每个文件中都硬编码，你就别无选择，只能逐个文件进入并进行更改，或编写脚本为你完成。

你最好将所有这些信息保存在单个文件中（也许称为 header.php），然后使用一个命令将该文件的内容输出到被访问的文件中。为此，你可以使用下一节讨论的 PHP 函数之一。在本示例中我们将使用 include()。

![](img/de0823012275cf4ceebdb822a56e6b71_202_0.png)

> 如果你能访问 Apache httpd.conf 文件，你可能希望为包含文件指定一个不同的扩展名；.inc 是典型选择。此外，如果可能，你希望将包含文件放在 htdocs 目录之外，以便它们不能通过 URL 访问。我们在本书中没有使用这两种技术，因为大多数使用 ISP 托管其 PHP/MySQL 应用的人将无法以这种方式更改其设置。

假设我们有两个文件，header.php 和 index.php。请注意，我们在 header.php 中做了一个重要更改：<title> 标签现在包含一个 PHP 变量

```
<HTML>
<HEAD>
    <TITLE> <?php echo $page_title; ?> </TITLE>
</HEAD>
<body bgcolor="#FFFFFF" link="#8e0402" vlink="#20297c">
```

现在来看 index.php 文件。

```
<?php

$page_title = "Welcome to My Site";
include('header.php');

echo "Here are the contents of my PHP pages. Anything could be here.";

?>
```

请注意，变量 $page_title 将在包含中被拾取。因此，当 index.php 被提供时，PHP 页面的源代码将如下所示：

```
<HTML>
<HEAD>
    <TITLE> Welcome to My Site </TITLE>
</HEAD>
<body bgcolor="#FFFFFF" link="#8e0402" vlink="#20297c">
```

无论是 HTML 还是 PHP，只要在多个页面中需要使用的代码，都应保存在包含文件中。页眉和页脚信息、数据库连接代码，以及包含函数或类的页面都是包含文件的良好候选。

![](img/de0823012275cf4ceebdb822a56e6b71_203_0.png)

> 在包含文件开始时，PHP 会恢复到 HTML 模式。如果包含文件中的代码需要作为 PHP 解析，你必须先用 <?php 标记标明。

再次说明，PHP 4 包含多种对包含文件做略有不同处理的命令。我们将在以下章节中查看这些命令。

## include() 和 require()

这两个命令非常相似，通常可以互换使用。然而，你应该知道它们的区别，因为有时使用错误的一个会导致问题。

require() 命令会导入指定文件的内容，即使该文件未被使用。这意味着，首先，即使 require() 位于测试结果为 false 的 if 块中，外部文件仍会被包含。你大概可以推断这不是什么大问题，因为测试结果为 false 的块中的代码不会被执行。然而，PHP 执行导入确实需要时间，而且没有必要通过在可能测试为 false 的 if 块中放置 require 来增加脚本的执行时间。

![](img/de0823012275cf4ceebdb822a56e6b71_203_1.png)

> PHP 手册中列出了 include 和 require 之间的其他差异，但这些差异与 PHP 3 更相关。PHP 4 在处理包含文件方面非常智能，并在解释脚本时决定哪种最适合你。用 include 和 require 编写行为不同的脚本非常困难。

在像上面这样的情况下，include() 命令会更合适。include() 命令在脚本中每次遇到时都会被执行。

## include_once() 和 require_once()

除了 include() 和 require() 之外，PHP 还提供 include_once() 和 require_once()。这些是为了防止开发者自己踩到自己的脚而提供的。正如你所料，它们会阻止你重复包含同一个文件，这在调用用户自定义函数时可能会引起一些问题。

