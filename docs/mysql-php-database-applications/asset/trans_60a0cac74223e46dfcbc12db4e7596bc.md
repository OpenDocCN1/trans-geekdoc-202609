

6 => 6
7 => 7
8 => 8
9 => 9
10 => 10
11 => 11
12 => 12
);

```
// set the $years array to a list of plausible years
$y = date('Y');
$years = array(
	$y => $y++
, $y => $y++
, $y => $y++
, $y => $y++
, $y => $y++
, $y => $y++
, $y => $y++
, $y => $y++
);
```

```
// use January of next year as a default expiration date
if (empty($order->cc_exp_mon))
{
	$order->cc_exp_mon = 1;
}
if (empty($order->cc_exp_yr))
{
	$order->cc_exp_yr = date('Y')+1;
}
```

```
print labeled_row(
	'Expires',
	select_field(array(
		'name' => 'cc_exp_mon'
		, 'values' => $months
		, 'match' => $order->cc_exp_mon
	))
	, select_field(array(
		'name' => 'cc_exp_yr'
		, 'values' => $years
		, 'match' => $order->cc_exp_yr
	))
);

print end_table();

// display the order button
print paragraph(
    submit_field($order_button)
    , submit_field('Test Submit')
);

print end_form();

print end_page();

$_SESSION['order'] = serialize($order);
?>
```

## 摘要

本章详细讲解了许多 PHP 概念，以购物车为例（并非双关语）。

我们讨论的最重要概念之一是持久性——即存储与特定用户相关的信息（例如购物车项目）的能力，以便在多次访问中保留。PHP 依赖于其与数据库的连接（如果你够聪明，这个连接由 PEAR 类来中介）来存储信息。

另一个关键概念是状态维护。由于 HTTP 本质上是无状态协议，你需要做一些工作来将某人的一次 HTTP 请求与同一人的下一次请求关联起来，同时将这些请求与同时可能出现的数百个其他请求区分开来。PHP 提供了一些有用的状态管理功能。例如，你已经看到，注册会话标识符并稍后检查它以识别特定用户的过程并不复杂。

这些功能在我们的购物车应用程序中至关重要。一方面，我们使用持久性将每个购物车的内容存储在数据库中，并确保它们彼此独立。此外，我们使用会话管理在用户浏览我们的商品并向购物车添加或移除商品时，跟踪他们在我们网站上的一系列请求/响应事务。

## 第 15 章

## XML 解析

### 本章内容

- 学习如何处理 XML 文档
- 检查从 URL 检索到的 XML 文档

HTML 对网页是什么，eXtensible Markup Language（即 XML）对数据就是什么。

而 HTML 关乎向世界呈现你的信息——处理字体、大小、颜色、布局等等——XML 则纯粹关注结构化和标识该信息。

考虑到每周似乎都会冒出新的不同 Web 平台——台式电脑、笔记本电脑、手机、电视、手表、车载音响——这种内容与呈现的分离是 Web 程序员的崇高目标。

这两种语言都非常成功，因为它们本质上都很简单，却允许广泛的应用。

它们甚至长得很像——这也是应该的，考虑到两者都基于标准通用标记语言（SGML）。

例如，在包含气象观测数据的 XML 文档中，不同的标签可以将某些数字标识为风速值，将其他数字标识为风向值。

如何以可视化方式表示这些值——如果它们确实要被可视化显示，而不仅仅是读入数据库或其他处理环境中——是另一个问题。

XML 另一个优点是，它是传输信息的极佳格式，不仅传输数据，还传输你通常会与常规编程语言（如 PHP 本身）联系在一起的各种查询和响应。

原因在于它很轻量——毕竟它只是 ASCII（或 Unicode）——并且透明。

你第一次查看 XML 文档时，很有机会立即理解它。

然而，它也适合机器解读，而机器在理解方面臭名昭著地迟钝。

本章将探索 XML 以及 PHP 处理 XML 的能力。我们将从 URL 读取文档，并重新格式化其内容以供在我们的内容管理应用程序 Netsloth 中使用。

本章中使用 Slashdot.org 网站仅为示例目的。大多数像 Slashdot.org 这样的网站都有管理其发布内容使用的条款和条件，因此在通过你自己的 Web 应用程序公开发布从其他网站获取的任何内容之前，请务必寻求适当的授权。有关使用 Slashdot 标题的具体信息，请参阅 http://slashdot.org/code.shtml。

## 应用程序的范围和目标

不久前，我们有这样一个很棒的应用程序可以向你展示。它带有 XML 解析器、事件处理程序、函数回调以及各种花哨的功能。

其构思是从类似 Slashdot (www.slashdot.org) 的网站抓取标题，该网站以现代人类所知的几乎所有格式提供其内容。

其中一种格式是 XML，你可以在 http://slashdot.org/slashdot.xml 自行查看。

我们会读取它、解析它，然后将其作为 HTML 输出，以包含在我们小巧而独特的 Web 内容网站示例 Netsloth 中（你可能还记得第 11 章中提到的它）。

但随后开发 PHP 的人决定改变其底层 XML 支持，围绕 Gnome XML 库 libxml2 构建，并引入名为 Simplexml 的新扩展，这就是你现在构建我们第一个示例的方式。完全。

```
<?php
// keep the errors off the page
ini_set('display_errors', 0);
$url = 'http://www.slashdot.org/slashdot.xml';
$cachefile = "/tmp/slashdot.xml.cache";

if (($xml = file_get_contents($url)))
{
        file_put_contents($cachefile, $xml);
}
else
{
        error_log('Unable to contact www.slashdot.org');
        if (($xml = file_get_contents($cachefile)) == FALSE)
        {
error_log("Unable to open cache file: $cachefile");
print <<<EOT
<p>
Unable to obtain Slashdot.org content.
Please try again later.
</p>
EOT;
return;
}
$stories = simplexml_load_string($xml);
print <<<EOT
<h3>Slashdot Stories:</h3>
<ul>
EOT;
foreach ($stories->story as $story)
{
print <<<EOT
<li><a href="{$story->url}">{$story->title}</a>
EOT;
}
print <<<EOT
</ul>
EOT;
?>
```

这将使本章相当简短。你会特别注意到，代码中“处理 XML”的部分只有十行。所以我们稍微润色了一下。

我们希望能够包含每个故事的更多信息，包括网站提供的代表主题的图片。同时，如果 Slashdot 被 Slashdot 效应击中并离线，我们希望我们在 Netsloth 上的页面能保持运行，同时尽量减少对其网站流量的增加。这两个目标都涉及设置内容的本地缓存。图 15-1 向你展示了新的 Netsloth 主页。

> 图 15-1 中显示的故事仅用于示例目的。本章中的内容都不代表曾经实际出现在 Slashdot.org 上的帖子。

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_553_0.png)

图 15–1：带有模拟示例故事的 Netsloth21 主页

## 代码概览

我们应用程序的基本目的是跨越互联网，获取 XML 文档，将其拆解，并将切碎的片段重新格式化为适合在我们 Netsloth 内容管理套件中使用的形式。为了实现这些目标，此软件需要能够查看 XML 文档，区分标签和标记文本（也称为字符数据），并在必要时将它们分开。执行此操作的代码片段通常称为 _XML 解析器_。XML 解析器可以以几种不同的方式设计。

## 解析器简介

如果你要使用 XML，你需要一个解析器。解析器大体分为两种不同的类型：

- 树式解析器（也称为文档对象模型（DOM）解析器），它们一次性读取整个 XML 文档，并将导入的数据转换为表示整个文档的分层组织对象。微软的 MSXML 解析器属于此类。

