
```
<table border=0>

<?php

if (empty($offset)) { $offset = 0; }

$result = select_entries($offset);
$preserve = "";
while ($row = mysql_fetch_array($result))
{
    print_entry($row,$preserve,"name","location","email","URL","entry date","comments");
    print "<tr><td colspan=2>&nbsp;</td></tr>\n";
}
mysql_free_result($result);
?>

</table>
<?php
nav($offset);

include "end_page.php";
?>
```

就是这样。你为 $offset 确定一个值，使用 select_entries() 函数运行查询，然后在 while 循环中运行 print_entry() 函数来打印结果。导航元素由 nav() 函数决定。

## 删除条目

最复杂的部分是涉及从留言簿中删除条目。这是可以理解的，因为你不希望留言簿被匿名用户欺骗。因此，在删除条目之前，你需要做的第一件事是验证用户。在讨论 authenticate() 函数时，我们展示了 HTTP 401 头部会弹出浏览器的用户名和密码对话框。然后输入的值需要与 guestbook_admin 数据库表进行核对。authenticate.php 文件已为你处理了此事，这就是为什么该文件包含在 edit.php 文件中的原因。

authenticate.php 的核心如下：

```
if (empty($PHP_AUTH_USER))
{
    authenticate($realm,$errmsg,"header");
}
```
```
else
{
    $query = "select username from guestbook_admin where password = password(lower('$PHP_AUTH_PW')) and username = lower('$PHP_AUTH_USER')";
    $result = mysql_query($query);
    if ($result) { list($valid_user) = mysql_fetch_row($result); }
    if (!$result || empty($valid_user))
    {
        authenticate($realm,$errmsg,"query");
    }
}
print "<p><b>Editing as $PHP_AUTH_USER</b></p>\n";
```

如果没有输入用户名，头部将通过你的 authenticate() 函数发送。如果用户名确实存在，则会向数据库发送查询以验证用户。如果返回一行，则用户得到验证并可以继续操作；否则头部会再次发送。

一旦输入了有效的用户名和密码，edit.php 文件的其余部分将被发送。但这一次，除了其他所有信息外，还将包含复选框，以便用户决定应删除哪些条目。复选框的值将是 guestbook 表的主键。

```
while ($row = mysql_fetch_array($result))
{
    print_entry($row,$preserve,"name","entry
date","location","email","URL","comments");

    print " <tr>\n";
    print "  <td valign=top align=right><b>Delete?</b></td>\n";
    print "  <td valign=top align=left><input type=checkbox
name=\"entry_id[]\" value=\"" . $row["entry_id"] . "\"> Yes, delete
entry #" . $row["entry_id"] . "</td>\n";
    print " </tr>\n\n";

    print "<tr><td colspan=2>&nbsp;</td></tr>\n";
}
```

此表单随后提交到 confirm_delete.php 文件。请注意你在这里传递了一个数组。表单元素的名称是 entry_id[]，这意味着当此表单传递给 PHP 时，entry_id 将成为一个数组。数组中的值数量取决于勾选的框的数量。HTTP 根本不会发送未勾选的框。

在 confirm_delete.php 文件的第一次运行中，我们将打印出条目。这将使删除这些条目的用户确保他或她没有做蠢事。

```
while (list($key,$value) = each($entry_id))
{
    print "<li>Delete entry #$value?\n";
    print "<input type=hidden name=\"entry_id[]\" 
value=\"$value\">\n";
}
```

如果要删除其中任何条目，此页面将提交给自身，并通过提交按钮发送不同的值（Confirm Delete）。这将使以下代码运行：

```
while (list($key,$value) = each($entry_id))
{
    print "<li>Deleting entry #$value\n";
    $q = "delete from guestbook where entry_id = $value";
    safe_query($q);
}
```

我们遍历 $entry_id 数组，删除每个成员的记录。

## 脚本

还有一些脚本，但这些不值得太多讨论。sign.php、start_page.php、end_page.php 和 confirm_delete.php 已包含在光盘中。我们建议你查看它们以及注释，以了解它们如何融入应用程序。

## 总结

你在这里学到的技能可能不足以让你作为程序员赚大钱，但如果你理解这里所做的一切，随着你在 PHP 编程生涯中前进，你应该处于相当不错的状态。

特别是，你应该看到对创建可重用代码的重视。我们几乎所有内容都在函数中。这使得我们编写的代码更有可能在未来的某个应用程序中被使用。

此外，你还看到了一些基本的验证。验证是一个重要的概念，当你的应用程序允许用户输入时，你需要非常认真地对待它。如果你想知道有些人对验证有多认真，请查看 Manual Lemos 的表单验证类，它已包含在光盘中。

## 第 9 章
### 调查
### 本章内容
- 学习创建 HTML 标签的函数
- 理解使用关系结构的数据
- 让 MySQL 的日期函数发挥作用

如果留言簿是最常见的 Web 应用程序，那么调查问卷紧随其后。许多网站都有某种小部件，让你选择你最喜欢的颜色或体育英雄，或其他东西，以查看有多少比例的投票者持何种立场。所以让我们继续创建一个调查问卷。

在此应用程序中，你将看到比第 8 章中看到的更多复杂性。编程会变得有点棘手，并且应用程序的管理需要更多工作。与留言簿不同，此应用程序需要一些数据库理论知识。存在相关表，包含本书第 1 节中讨论的主键和外键。这意味着你的 SQL 查询将包含连接。

### 确定应用程序的范围和目标

调查应用程序可以非常简单。如果你只想收集来自单个问题的响应并返回响应的基本统计信息（有多少票选择 A、B 等），你不需要太多代码（或解释它的章节）。一个存储答案的表就足够了。问题甚至可以硬编码到 HTML 中。但这不会带来很有趣的学习体验，对吧？

如果可以有任意数量的问题，就会更有趣。与其只有一个，这个应用程序将允许两个、五个、十个或更多——你想要多少都可以。不仅如此，此调查还会记录人口统计信息（如年龄和原籍国），并允许基于此信息进行排序。我们还决定添加从填写个人信息的人中随机挑选获胜者的功能——这可能会鼓励人们提供真实而不是虚假的答案。

这里还有一个皱褶需要讨论。实际上没有办法创建一个记录完美数据的调查应用程序。即使你竭尽全力，狡猾且坚持不懈的人仍有机会提交多个条目。但很可能你的调查不需要通过联邦选举委员会的审查。采取一个小步骤来剔除破坏你调查的人就足够了，你稍后会看到一种实现方法。

### 所需页面

输入和查看信息需要三个页面。第一个页面将展示问题，用户将在此输入姓名、地址以及地理和人口统计信息。第二个页面将显示基本的调查结果。第三个页面将提供详细分解。图 9-1、9-2 和 9-3 分别展示了这些页面。

![](img/de0823012275cf4ceebdb822a56e6b71_246_0.png)

图 9-1：填写调查问卷的页面

请注意，对于此应用程序，你将使用 .gif 文件作为图表。脚本将更改 <img> 标签中 gif 的大小属性，以表示信息。这可行，但不一定理想。你可以安装 gd 库并使用 -with-gd 标志编译 PHP。这些功能超出了本书的范围。

像所有其他应用程序一样，此应用程序需要一些管理工具。首先，你需要能够添加、删除和编辑问题。此外，还有一个页面可从数据库中随机选择获胜者。图 9-4 和 9-5 分别展示了管理页面和选择获胜者页面。
