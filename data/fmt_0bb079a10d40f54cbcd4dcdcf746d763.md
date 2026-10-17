
# 主机类型概述

- 经销商主机（Reseller hosting）。
- VPS 和独立主机（Dedicated hosting）。

## 共享主机
在此方案下，你可以托管许多网站。有些共享主机方案还允许你托管不限数量的网站。在共享主机方案中，你只能获得一个 `CPanel`（控制面板）来管理所有网站。

## 经销商主机
经销商主机允许你将托管服务转售给其他客户。但你也可以用它来托管自己的网站。在经销商主机账户中，你可以为每个网站创建单独的账户。因此，当你购买经销商主机套餐时，你会获得一个 `Cpanel`（控制面板）和 `WHM`（网站托管管理器），用于创建和管理不同的网站账户。

Hirdesh Bhardwaj

## VPS 和独立主机
`VPS` 主机更适合访问量非常高的网站和需要大量功能的网站。通常，如果你使用共享或经销商主机方案，虚拟主机服务商不会允许你消耗那么多资源。他们会停用你的网站，并要求你升级到 `VPS` 或独立主机方案。

## 存储空间和带宽
如上所述，虚拟主机公司为你提供存储文件的空间和带宽，使你的文件可供公众访问。因此，基本上，存储空间就是用来存储你的博客文章、图片、媒体文件（视频、播客等）、`WordPress` 安装文件、主题、插件等的空间，它们都存储在服务器上。

**带宽：** 每次访问者访问你的网站时，他/她都会使用服务器资源。这是因为服务器需要将所有文件/图片/媒体发送到他的计算机。
因此，以这种方式提供文件所消耗的资源被计算为带宽。
你的访问者越多，所需的服务器资源就越多，因此你需要更多的带宽。
带宽以字节为单位进行测量，其值通常以 `GB`（千兆字节）或 `TB`（太字节）表示。

## 支持的语言
首先，我们来说说支持的语言。显然，因为你购买了这本书，我们假设你正在考虑使用 `PHP`，但你可能还需要使用其他语言。有些时候，其他语言（如 `JavaScript`）可能比 `PHP` 更适合某项工作。例如，
如果你想在网站上直播音频或视频，你可能会使用某种 `Java` 小程序（applet），因为 `PHP` 需要来自服务器的请求来处理信息。`PHP` 可以通过对服务器的不同调用来实现，但由于这更像是来自浏览器的客户端请求，因此客户端语言更适合此任务。
有时，你可能需要使用另一种编程语言来完成客户在其他主机或服务器上已经设置好的功能。如果是这样，至少可以有选择地使用例如 `Perl` 脚本，而不是花费时间和金钱用 `PHP` 重新开发应用程序。
类似 `WordPress` 的 `CMS` 使用 `MySQL` 数据库来存储和检索数据以动态生成网页。
如果计划运行一个不使用任何 `CMS` 或 `PHP` 语言的静态网站，则不需要数据库。

## 服务器控制和访问
许多主机提供商不会给 Web 开发人员对其托管域的完全访问和/或控制权限。
我们倾向于避开这些主机，因为当你想对服务器进行一些自定义配置时，更有可能遇到问题。
查看你的主机提供的访问类型。显然，你的主机会提供 `FTP` 访问，以便你将文件上传到 Web 服务器。然而，有些主机只提供 `FTP` 访问，其他什么都没有。
问题在于你很可能会遇到想要配置服务器的情况。为此你需要 `telnet` 或 `SSH` 访问来使用命令行。
事实上，配置能力在执行主机默认通常不允许的任务时往往是必要的。例如，考虑 `htaccess`。使用 `htaccess`，你可以根据 `htpasswd` 文件中允许的用户来拒绝和允许对某些文件和目录的访问

![](img/9ab4a56a650535285811bb802190e58f_183_0.png)

## 管理 GUI
某些主机在其套餐中提供管理 `GUI`（图形用户界面）或用户控制面板作为功能。很多人并不特别喜欢 `GUI`，但当你别无选择时——要么是因为你没有足够的服务器访问权限，要么是因为你不完全了解如何通过 `telnet` 完成操作——点按式解决方案就是一个很棒的工具。
界面可以简单到只允许你查看有关服务器的信息，也可以复杂到允许你一键安装应用程序和编程语言。另外，请记住，如果你的客户希望能够管理其电子邮件用户，许多控制面板都有实用程序允许客户自行操作。有了这样的功能，客户无需打电话给你或托管公司来设置电子邮件帐户，客户只需登录控制面板并根据需要设置和删除用户即可。

## 备注

## PHP 分页
当我们在同一页面上显示大量内容时，我们开始考虑添加分页，因为在同一页面上加载所有数据在优化方面不是正确选择。因此我们将所有内容拆分为多个页面。在这种情况下——每个页面包含我们信息的一部分。我们可以使用服务器端以及客户端分页，使用 `javascript` 和 `PHP` 来管理我们的页面。
你的 `SQL` `SELECT` 语句查询可能产生数千条记录的情况总是存在的。但在一页上显示所有结果并不是一个好主意。因此我们可以根据需要将此结果分成多个页面。
分页意味着将查询结果显示在多个页面中，而不是全部放在一个页面上。

### 使用 LIMIT 获取记录以生成分页的简单示例
```
<?php

include 'dbconnectivity.php';

// to check if page url already contain page number like
test.php?pageNum=2

if (isset($_GET['pageNum']))

{

$pageNum = $_GET['pageNum'];

} else
{
    // if no pageNum variable exist in url then set pageNum variable to page 1
    $pageNum = 1;
}

// place your query here
$query=mysql_query("select * from imageslave");

$resultRows = mysql_num_rows($query);

// Set number of Records per page
$rowsPerPage = 4;

/* Calculate how many pages to be generate example if you have 20 record and you want to display 4 pages each page then last page will be 5. ( 20/4 =5 )*/
$lastPage = ceil($resultRows/$rowsPerPage);

// set page position to beginning or at the end of the page
if ($pageNum > $lastPage)
{
    $pageNum = $lastPage;
}
    else if ($pageNum < 1)
{
$pageNum = 1;
}
while($row =mysql_fetch_assoc($query))
{

// display data fields here
echo $row['fname'];
echo " " .$row['lname']."<br>";
}
echo "<br><br>";

// Display links of Next / Prev Page
if ($pageNum > 1)
{
    $prevPage = $pageNum-1;
    echo " <a href='{$_SERVER['PHP_SELF']}?pageNum=1'>FIRST</a> ";
    echo " <a href='{$_SERVER['PHP_SELF']}?pageNum=$prevPage'>PREVIOUS</a> ";
}
echo "Page $pageNum of $lastPage ";
if ($pageNum < $lastPage)
{

$nextPage = $pageNum+1;

echo " <a href='{$_SERVER['PHP_SELF']}?pageNum=$nextPage'>NEXT</a> ";

echo " <a href='{$_SERVER['PHP_SELF']}?pageNum=$lastPage'>LAST</a>" ;

}

?>
```

## 备注

## Bootstrap – 框架
`Bootstrap` 是一个免费的开源 `CSS` 框架，面向响应式、移动优先的前端 Web 开发。它包含用于排版、表单、按钮、导航和其他界面组件的基于 `CSS-` 和（可选）`JavaScript` 的设计模板。*(来源：维基百科)*
最初名为 `Twitter Blueprint`，由 **Mark Otto 和 Jacob Thornton** 在 **Twitter** 开发，作为一个框架以鼓励内部工具的一致性。

**安装指南：** 你可以访问 `getbootstrap.com` 下载 `bootstrap` 的最新版本。下载设置后你需要解压或提取它。你将获得以下三个目录
- **CSS** – 包含所需的 `css` 文件，例如 – `bootstrap.min.css`, `bootstrap-theme.css` 等
- **Fonts** - 包含用于额外字体的 `ttf` 和 `otf` 文件
- **JS** - 包含所需的 `JS` 文件 – 例如 – `bootstrap.min.js`, `npm.js` 等。

### 示例代码：安装 Bootstrap
```
<!DOCTYPE html>

<html lang="en">

  <head>

    <meta charset="utf-8">

    <meta http-equiv="X-UA-Compatible" content="IE=edge">

    <meta name="viewport" content="width=device-width, initial-scale=1">

<title>Bootstrap 101 Template</title>
<link href="css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
// Your HTML code goes
</body>
</html>
```

## Bootstrap 3 中可用的一些主要类

### .container
- 为元素设置固定宽度（根据屏幕尺寸会更改为其他固定值，因此仍然具有响应性）在除 `xs` 之外的所有屏幕尺寸上 - 在 `xs` 上，宽度会自动计算（此行为可以更改）
- 固定宽度的响应式网站应包装在 `.container` 中（或仅内容而不带菜单，随便你——由你决定）
- `.container` 不能嵌套！

### .container-fluid
- 设置 100% 宽度，`margin-left` 和 `margin-right: auto`，`padding-left` 和 `padding-right: 15px`
- 全屏网站应包装在 `.container - fluid` 中
- `.container-fluid` 不能嵌套！

### .row
- 创建列的水平组（通常具有宽度类，见下文）
- 必须在 `.container` 内以确保正确的填充和对齐
- 只有列（具有宽度类的块元素）可以是行的直接子元素
- 设置 `margin-left` 和 `margin-right: -15px`

### .pull-right

### .pull-left
- 将 `float` 设置为 `left` 或 `right`

### .center-block
- 将 `margin-left` 和 `margin-right` 设置为 `auto`

## Bootstrap 网格类
- 可以嵌套，嵌套的列也必须包装在 `.row` 中
- 所有列都有 `float: left` 和 `position: relative` 样式

### .col-xs-1 .col-xs-2 .col-xs-3 .col-xs-4 .col-xs-5 .col-xs-6 .col-xs-7 .col-xs-8 .col-xs-9 .col-xs-10 .col-xs-11 .col-xs-12
- 在超小屏幕（<768px）上设置列的宽度（以 % 指定）

### .col-sm-1 .col-sm-2 .col-sm-3 .col-sm-4 .col-sm-5 .col-sm-6 .col-sm-7 .col-sm-8 .col-sm-9 .col-sm-10 .col-sm-11 .col-sm-12
- 在小屏幕（≥768px）上设置列的宽度（以 % 指定）

### .col-md-1.col-md-2.col-md-3.col-md-4.col-md-5.col-md-6.col-md-7.col-md-8.col-md-9.col-md-10.col-md-11.col-md-12
- 在中等尺寸屏幕（≥992px）上设置列的宽度（以 % 指定）

### .col-lg-1.col-lg-2.col-lg-3.col-lg-4.col-lg-5.col-lg-6.col-lg-7.col-lg-8.col-lg-9.col-lg-10.col-lg-11.col-lg-12
- 在大屏幕（≥1200px）上设置列的宽度（以 % 指定）
- 通过指定列数设置偏移（`margin-left`）（例如，在小屏幕上将列移动三列，将 `.col-sm-offset-3` 类设置为列）

### .col-xs-pull-* (.col-xs-pull-1, .col-xs-pull-2 ... up to -12)
.col-sm-pull-* (.col-sm-pull-1, .col-sm-pull-2 ... up to -12)
.col-md-pull-* (.col-md-pull-1, .col-md-pull-2 ... up to -12)
.col-lg-pull-* (.col-lg-pull-1, .col-lg-pull-2 ... up to -12)
- 以与列相同的方式按 % 设置 `left` 位置（例如，使用 `-pull-9` 时 `left: 75%`）

## Bootstrap 可见性类
- 你可以在单个元素上应用任意多个这些类，这种混合为你的布局提供了更多可能性

### .clearfix
- 显而易见，`clear: both`
- 通常与下面的类组合使用

### .visible-xs-block and .visible-xs .visible-sm-block and .visible-sm .visible-md-block and .visible-md .visible-lg-block and .visible-lg
- 仅在指定尺寸的屏幕上显示元素（设置 `display: block` 属性），并在其他尺寸的屏幕上自动隐藏它（设置 `display: none`）
- 通常与 `.clearfix` 结合使用，使 `clearfix` 仅在选定的屏幕尺寸上生效

### .hidden-print
- 在打印（预览）时隐藏元素（设置 `display: none`）

## Bootstrap Typography Classes
- `<body>` a `<p>` 元素的默认字体大小为 14px，行高为 1.428；`<p>` 还有 `margin-bottom` 为其行高的一半（14px 字体时为 20px），因此默认为 10px
- `b`、`big`、`code`、`em`、`i`、`mark`、`small`、`strong`、`sub`、`sup`、`ins`、`del`、`s`、`u`、`abbr`、`address` 和 `blockquote`（以及内部的 `small` 和 `cite`）等元素都被正确样式化
- 这些类的绝大多数最常设置在段落、`strong` 或 `em` 元素上

### .page-header
- 用于标题的包装 `div` 的类
- 添加一些 `margin`、`padding` 和 `border-bottom`

### .lead
- 用于突出显示元素
- 将元素的 `font-size` 设置为 21px，`font-weight` 为 300，`line-height` 为 1.4，`margin-bottom` 为 20px

### .text-left .text-center .text-right .text-justify
- 使用 `text-align CSS` 属性对齐文本，通常是段落

### .text-nowrap
- 保持带有此类的整个文本在一行上，不换行，因为该类的 `white-space: nowrap CSS` 属性

### .text-lowercase .text-uppercase .text-capitalize
- 设置 `text-transform CSS` 属性，使带有此类的元素内的所有字符变为小写、大写或首字母大写

### .text-muted
- 使文本变灰

### .text-primary
- 使文本变蓝

### .text-success
- 使文本变绿

### .text-info
- 使文本变深蓝

### .text-warning
- 使文本变深黄

### .text-danger
- 使文本变红

## Bootstrap Lists' Classes

### .list-unstyled
- 在列表项上移除 `list-style` 和 `margin-left`
- 对嵌套列表不适用（如果需要，嵌套列表也必须具有 `.list-unstyled` 类）

### .list-inline
- 将列表项放置在一行上（使用 `display: inline-block` 和 `padding`）

### .dl-horizontal
- 用于定义列表（`<dl>`）的类
- 为定义列表内的 `<dt>` 和 `<dd>` 设置漂亮的样式（文本对齐、字体粗细）

### .list-group
- 列表项的父元素的类（通常是 `<ul>`，也可以是 `<div>`）
- 列表项必须具有 `.list-group-item` 类

### .list-group-item
- 用于 `.list-group` 子元素的类
- 使列表项看起来更美观
- 通常用于 `<li>`，也可以是 `<a>`

### .table-condensed
- 应与 `.table` 类结合使用
