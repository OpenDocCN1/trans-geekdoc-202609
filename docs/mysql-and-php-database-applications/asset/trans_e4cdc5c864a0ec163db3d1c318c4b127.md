

# 第8 章：留言板 2000，（半）防弹型留言板

```php
)
print "</p>\n";
```

在适当的情况下，在上一页条目处插入一个链接，使用户能够查看下一组条目，或者两者兼有。这完全由 `$offset` 变量和 `PAGE_LIMIT` 常量决定。

第一次执行时 `$offset` 没有值，因此不会有“上一页”的链接（因为 `$offset` 不大于 0）。但如果还有更多行需要显示，就会创建一个链接，当用户点击该链接时，会为 `$offset` 赋值。

假设这是你第一次执行此函数，$offset` 没有值，且数据库中有 10 行数据。当程序运行到最后一个 `if...` 时，脚本将发现还有更多行要显示（`$offset + PAGE_LIMIT = 2`，小于 10），因此将打印以下链接。

```html
<a href="/book/guestbook2k/view.php?offset=2">
Next Entries&gt;/</a> >
```

# 有趣的代码流

一旦你理解了目前为止介绍的函数，就应该能弄清楚 `guestbook2k` 是如何工作的。在大多数情况下，浏览器调用的页面中执行的工作很少。这些页面基本上是函数调用的集合。

我们将详细拆解一个文件，让你感受这种结构是如何运作的。其余大部分你应该能够通过文件之间的关系和函数的解释推断出来。在接下来的章节中，我们将逐步介绍 `view.php` 文件。

# 查看条目

```php
<?php

include "header.php";

$page_title = "查看我的留言板!!";
include "start_page.php";
?>
```

在每个页面中你需要做的第一件事就是包含 `header.php` 文件。这将允许你访问我们之前概述的所有函数。之后，你应该包含 `start_page.php` 中的标准页眉信息。你必须在包含 `start_page.php` 之前声明 `$page_title`，这样标题就可以在每个页面以标准方式打印。

# 第三部分 212：简单应用程序

```html
<table border=0>

<?php
if (empty($offset)) ($offset = 0; )

$result = select_entries($offset);
$preserve = "";
while ($row = mysql_fetch_array($result)) {
    print_entry($row,$preserve,"name","location","email","URL","entry date",", "comments");
    print("<td colspan=2>&nbsp;<td></td></tr>\n");
}
mysql_free_result($result);
?>

</table>
<?php
nav($offset);

include "end_page.php";
?>
```

就是这些。你确定 `$offset` 的值，运行 `select_entries()` 函数执行查询，然后在循环中运行 `print_entry()` 函数来打印结果。导航元素由 `nav()` 函数决定。

# 删除条目

该应用程序中最复杂的部分是从留言板中删除条目。这是是合情理的，因为你不希望你的留言板被匿名用户所戏弄。因此，在删除条目之前，你需要做的第一件事是验证用户身份。在讨论 `authenticate()` 函数时，我们展示了 HTTP 401 头部如何调出浏览器的用户名和密码对话框。随后输入的值需要与 `guestbook_admin` 数据库表进行校验。`authenticate.php` 文件会为你处理这些，这就是为什么该文件被包含在 `edit.php` 中。
`authenticate.php` 的核心是：

```php
if (empty($PHP_AUTH_USER)) {
    authenticate($realm,$errmsg,"header");
}
```

# 第8 章：留言板 2000，（半）防弹型留言板 213

```php
else
{
    $query = "select username from guestbook_admin where password = lower(\$PHP_AUTH_PW) and username lower(\$PHP_AUTH_USER)";
    $result = mysql_query($query);
    if ($result) { list($valid_user) = mysql_fetch_row($result); }
    if (!$result || empty(\$valid_user)) {
        authenticate(\$realm,$errmsg,\$query);
    }
}
print "<p><b>Editing as \$PHP_AUTH_USER</b></p>\n";
```

如果没有输入用户名，头部将通过你的 `authenticate()` 函数发送。如果用户名存在，它将发送到数据库以验证用户。如果返回了行，则用户通过验证并可以继续工作；否则再次发送头部。

一旦输入了用户名和密码，`edit.php` 的剩余部分将被发送。但这次，除了所有其他信息外，还将包含复选框，以便用户决定删除哪些条目。复选框的值将是留言板的主键。

此表单被发送到 `confirm_delete.php` 文件。注意你在这里传递了一个数组。表元素的名称是 `entry_id[]`，这意味着当此表单传递给 PHP 时，`entry_id` 将是一个数组。数组中的值取决于勾选框的数量。HTTP 不会发送未勾选的框。

在第一次通过 `confirm_delete.php` 文件时，我们将打印出条目。
这将让删除这些条目的人确保自己没有在做愚蠢的事。

```php
while (list($key,$value) = each($entry_id)) {
    print "Deleting these entries\n";
    print "<input type=hidden name=\"entry_id[]\" value=\"$value\">
}
```

如果对任何条目进行删除，将执行以下代码：

```php
while (list($key,$value) = each($entry_id)) {
    print "Deleting entry #$value\n";
    $q = "delete from guestbook where entry_id = $value";
    mysql_query($q);
}
```

# 脚本

有几个脚本，但不需要讨论。sign.php、start_page.php、end_page.php 和 confirm_delete.php 包含在 CD 中。

# 总结

你学到的技能可能不会让你赚大钱，但如果你理解了这里做的一切，你在未来将表现良好。

特别是，你应该看到代码的可重用性。我们编写的一切都是函数。

此外，你应该看到基础验证。当应用程序允许用户输入时，验证是一个重要的概念。

# 第9 章：调查卷

在本章中

- 创建 HTML 标签的函数
- 理解关系型数据
- 使用 MySQL 函数

如果说留言板是 Web 上最常见的应用程序，调查卷也随其后。许多网站都有某种小工具，让你选择喜欢的颜色或运动偶像，等等，以查看百分之几的人持有该观点。所以，让我们创建一个调查卷。这个应用程序将比第 8 章复杂一点。编程将变得稍微棘手，应用程序的管理将需要更多工作。与留言板不同，此应用程序需要一些数据库理论知识。存在相关的表，包含了我们在书中第一节中讨论的主键外键。这意味着你的 SQL 查询将包含连接（joins）。

# 确定应用程序的范围和目标

调查卷应用程序可以非常简单。如果你只想收集单个问题的响应，并返回响应的基本统计信息（选项 A、B、C 各有多少选票），你不需要大量的代码（或一个章节来解释）。一个存储答案的单表就能解决问题。问题可以硬编码在 HTML 中。但这不会带来非常有趣的学习体验，不是吗？
不仅仅是一个，应用程序将允许两个、十个或更多问题——随你所欲。不仅如此，调查卷还将记录人口统计信息（如年龄和国籍），并允许根据这些信息进行排序。我们还决定从填写了个人信息的人中选出一个获胜者——这会鼓励人们提供真实而非虚假的答案。

这里还有一个小折。真的没有办法创建一个记录完美数据的调查卷应用程序。即使你采取极端手段，那

