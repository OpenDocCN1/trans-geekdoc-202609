
如果你在写完代码几个月后再次回到它，你会想知道当时你在想什么。

在 PHP 中，你可以用两个斜杠（//）、井号（#）来表示注释，或用 /* 和 */ 包围被注释的代码。后一种方法对于多行注释特别有帮助。

对所有函数进行注释，说明它们的作用、期望接收什么以及返回什么。务必记录任何难以追踪的变量。

当你浏览 CD 上的 /functions 目录时，你会看到每个函数都有一个初始注释，其风格模仿了 PHP 手册中使用的风格。例如，

```
int fetch_record (string table name [, mixed key [, mixed value]])
```

然后我们提供一些描述，说明这些参数的含义以及返回值的重要性。在编写函数体时，你应该对任何对后来接触该脚本的人来说不直观的内容进行注释。如果你有一系列执行复杂字符串处理或使用冗长正则表达式的函数，务必明确说明这些函数 intended to accomplish 的内容。例如，我们将重现这一行代码：

```
$file_ext = strtolower(substr($file, strrpos($file,".")));
```

这并不特别难弄明白，但你可以用一个简单的注释来帮助下一个看到这一行的人。

//get characters following the final dot
//and make lowercase
$file_ext = strtolower(substr($file, strrpos($file,".")));

另一个需要注释的重要内容是页面的整体逻辑，尤其是长页面。通常脚本在不同情况下的行为会有所不同。从表单传递的变量、错误和其他因素都会影响脚本的哪些部分会被运行。在页面顶部，你可以说明哪些因素会影响页面的逻辑，然后在到达不同的 if 块时，解释条件来自何处以及它们的含义。

举一个简短的例子，取自第 8 章 Guestbook2k 中的 confirm_delete.php 页面：

/*
This script will only run if the user is logged in.
It will be accessed in two circumstances:
  -- The "Delete Entries" button was pressed on
     the edit.php page. (Normally this will be the
     first time to this script). The ids of the
     records to be deleted are passed in the entry_id
array.
-- The "Confirm Delete" button was pressed on this page. This will confirm the deletion and run the delete queries.
*/
include("header.php");
include("authenticate.php");

$page_title = "Confirm Changes";
include("start_page.php");

//if coming from edit_page.php. The first time to
//this script. Print a form with checkboxes that
//the user must check in order to confirm deletion.
if ($submit == "Delete Entries")
{
    //the form contains no action, so it will submit
    //to the same page, and the value of submit will be
    //"Confirm Delete"
    print "<form method=post>\n";
    if (is_array($entry_id))
    {
        while (list($key,$value) = each($entry_id))
        {
            print "<li>Delete entry #$value?\n";
            print "<input type=hidden name=\"entry_id[]\" value=\"$value\">\n";
        }
        print "<br><input type=submit name=submit value=\"Confirm Delete\">\n";
        print "<input type=hidden name=offset value=\"$offset\">\n";
        print "</form>\n";
    }
}

//if the page has been submitted to itself,
//to confirm that the deletion should happen.
elseif ($submit == "Confirm Delete")
{
    //loop through each element in the entry_id array
    //and run a delete query for each item.
    while (list($key,$value) = each($entry_id))
    {
        print "<li>Deleting entry #$value\n";
        $q = "delete from guestbook where entry_id = $value";
```
mysql_query($q) or die("Invalid query:$q");
}
}
else
{
    print "No action to confirm\n";
}
```

我们将这一节以一个警告结束：不要过度注释。逐行注释，或让显而易见的事情变得更加显而易见是很烦人的。例如，以下注释完全没有必要，只会让你的脚本难以阅读。

//make string lowercase
$str = strtolower($str);
//increase $i by 1
$i++

注释需要良好的判断。你不想注释太多，也不想注释太少。我最好的建议是看看有多少程序员注释他们的代码并选择你喜欢的风格。我们在本书的应用程序中使用一种方法；其他人有不同的风格。

你的 PHP 安装中的 PEAR 目录是寻找良好编码风格技巧的好地方。PEAR 代表 PHP Extension and Application Repository。它是一组不断增长的脚本，包含了一系列 PHP 编程的最佳实践。参与 PEAR 工作的人都是真正的专业人士，写出了极好的代码。我们建议浏览该目录中的脚本，以汲取编写高质量代码的技巧。

## 摘要

在本章中，我们介绍了编写干净、有组织的代码的一些方法。当你查看脚本时，你应该问自己几个问题。是否有常见于每个页面的代码块？也许那些块应该移到一个 include 中。是否有我一遍又一遍编写的代码块？也许编写一个函数可以节省时间。下一个人来到这个脚本时是否能够弄明白我做了什么？如果不能，请确保添加足够的注释来使事情清晰。

你需要决定面向对象的方法是否适合你和你正在编写的应用程序。事实是，如果你不立即确定，答案很可能是否定的。在你进入类之前，请确保你能舒适地编写干净的过程式代码。

现在你已经完成了所有必要的阅读，是时候进入第三部分，在那里我们将 PHP 和 MySQL 付诸实践。

## 第 8 章

## Guestbook 2000，（半）防弹留言簿

## 本章内容

- 学习 guestbook 2000 的强大功能
- 以合理的方式组织你的代码
- 编写良好、可重用的函数

在本章中我们将开发我们的第一个应用程序——一个留言簿。留言簿并不复杂，也不是很令人兴奋。然而，这个应用程序确实给了我们介绍诸如验证等概念的机会，并将本书前面讨论的许多实践付诸实践。

在本书记载的引言中，我们介绍了可用于最基本的留言簿的一些代码。然而，使用该代码作为你的留言簿并不是一个好主意。它有各种各样的漏洞，会让外面的恶意人员篡改你的页面。超基本留言簿的另一个问题是：鉴于代码只是被倾倒到一个页面中，没有一行是可重用的。开发任何应用程序的顶级目标之一是创建可重用代码块。

## 确定应用程序的范围和目标

当面对一个应用程序时，最容易让你陷入麻烦的方式就是不知道自己试图实现什么。开发人员的工作中一个重要部分是弄清楚应用程序中需要什么。通常这将涉及与应用程序开发对象进行广泛的讨论。在这些讨论期间，提前思考一步并提出可能尚未考虑过的问题是很重要的。如果范围以某种方式增加会怎样？

如果需要跟踪额外但相关的信息会怎样？所有这些事情都会影响你设计数据库和脚本的方式，这就是为什么最好知道应用程序的确切范围和目标。取决于你与谁合作，你可能希望获得需要开发的页面的一些草图。

该应用程序的范围很小，目标也很有限。留言簿存储姓名、地址等信息。（但，说实话，本章的目标与其说是教你如何编写留言簿，不如说是教你如何为你的应用程序编写良好、可重用、有组织的代码。）无论如何，在继续之前你应该知道 guestbook2k 的样子。

> 在本章中，我们不会将创建良好函数的概念发挥到极致。在下一章我们将介绍一套更广泛的函数，我们将在本书的其余部分中使用它们。

## 必要的页面

有三个基本页面：一个用于签名留言簿，一个用于查看留言簿，一个用于管理留言簿。

图 8-1 显示了让用户有机会签名留言簿的页面。它很简单，一个表单包含四个文本字段和一个 textarea 字段。此外，还有一个提交按钮和一个重置按钮。

![](img/de0823012275cf4ceebdb822a56e6b71_224_0.png)

图 8-1：用于签名留言簿的页面
