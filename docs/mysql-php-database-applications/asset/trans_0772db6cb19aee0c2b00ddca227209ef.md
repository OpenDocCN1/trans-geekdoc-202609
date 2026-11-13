

要以可读的方式检索日期值，此查询使用了 MySQL 的日期函数。MySQL 将日期和时间存储为 14 位数字（YYYY:MM:DD:HH:SS），但以更易于人类阅读的方式返回日期信息会更好。MySQL date_format 函数以我们想要的方式检索信息。本函数及许多其他 MySQL 函数在附录 J 中讨论。

## NAV()

此函数的唯一目的是创建导航元素。

```
function nav ($offset=0, $this_script='', $limit=DEFAULT_LIMIT)
{
    $offset = (int)$offset;
    $limit = (int)$limit;

    // don't run things from outside this directory
    if ( empty($this_script) or
        dirname(realpath(__FILE__)) !=
        dirname(realpath($this_script))
    )
    {
        $this_script = $_SERVER['PHP_SELF'];
    }

    // get the total number of entries in the guest book -
    // we need this to know if we can go forward from where we are
    $result = safe_mysql_query('select count(*) from guestbook');
    $total_rows = mysql_result($result,0,0);

    print "<p>\n";
    if ($offset > 0)
    {
        // if we're not on the first record,
        // we can always go backwards
        $poffset = $offset - $limit < 0 ? 0 : $offset - $limit;
        print <<<EOO
    <a href="$this_script?offset=$poffset">&lt;&lt;Previous
    Entries</a>
    &nbsp;
    EOO;
    }
    if ($offset+$limit < $total_rows)
    {
        // offset + limit gives us the maximum record number
        // that we could have displayed on this page. if it's
        // less than the total number of entries, that means
        // there are more entries to see, and we can go forward
        $noffset = $offset + $limit;
        print <<<EOF
<a href="$this_script?offset=$noffset">Next Entries&gt;&gt;</a>
EOF;
    }
    print "</p>\n";
}
```

在适当的时候，此函数将打印链接，使用户能够查看下一组条目、上一组条目或两者。范围由 $offset 和 $limit 参数决定。

第一次执行时，$offset 没有值，因此不会存在上一条目链接（因为 $offset 不会大于 0）。但如果还有更多行需要显示，将创建一个链接，该链接被访问后会为 $offset 创建一个值。

假设我们第一次执行此函数，因此 $offset 没有值，且数据库包含 10 行。当脚本到达最后一个 if 块时，它会发现还有更多行需要显示（$offset + $limit 等于 2，小于 10），因此将打印以下链接：

```
<a href="/book/guestbook2k/view.php?offset=2">Next
Entries&gt;&gt;</a>
```

## 有趣的代码流程

一旦你理解到目前为止所介绍的函数的工作原理，就应该不难搞清楚 Guestbook 2003 的工作方式。大部分情况下，由浏览器调用的页面中完成的工作非常、非常少。这些页面基本上只是函数调用的集合。

我们将详细分解一个文件，让你了解这种结构的工作方式。其余大部分内容，你应该能够通过在文件和函数说明之间切换来弄清楚。在接下来的部分中，我们将逐步讲解 view.php 文件。

## 查看条目

在每个页面中，你首先需要做的是包含 header.php 文件，以便访问我们之前概述的所有函数。之后，你应该通过调用 guestbook_start_page() 函数并传入页面标题来包含标准标题信息。以下是代码的逻辑流：

```
<?php
require_once('header.php');
guestbook_start_page('View My Guest Book!!');

?>

<table border="0">

<?php
// $preserve is passed into the cleanup_text() function (declared in
// /book/functions/basic.php). setting it to an empty value will
// cause any HTML tags in an entry to be stripped out before
// being displayed.
$preserve = '';

// select_entries() (declared in header.php) should return a mysql
// result set identifier
$result = select_entries($offset);

while ($row = mysql_fetch_array($result))
{
    print_entry($row,$preserve,'name','location','email','URL','entry date','comments');
    print "<tr><td colspan="2">&nbsp;</td></tr>\n";
}

// release memory associated with this mysql result set
mysql_free_result($result);

?>

</table>

<?php
nav($offset);

end_page();

?>
```

就是这样。你使用全局 $offset 变量配合 select_entries() 函数运行查询，然后在 while 循环中调用 print_entry() 函数打印结果。导航元素由 nav() 函数决定。

## 删除条目

本应用程序最复杂的部分涉及从访客簿中删除条目的功能。这很合理，因为你不希望访客簿被匿名用户随意篡改。因此，在删除条目之前，你首先要做的是对用户进行身份验证。在讨论 guestbook_authenticate() 函数时，我们展示了 HTTP 401 标头如何弹出浏览器的用户名和密码对话框。输入的值需要与 guestbook_admin 数据库表进行核对。guestbook_authenticate() 函数会为你处理此事，因此它在 edit.php 文件的顶部被调用。

```
<?php

ob_start();

require_once('header.php');
guestbook_authenticate();

ob_end_flush();

guestbook_start_page('Edit The Guest Book');

?>
```

我们使用 PHP 的输出缓冲函数 ob_start() 和 ob_end_flush()，以确保在发送 HTTP 401 标头之前不会向浏览器发送任何输出。否则，header.php 中 <?php ... ?> 标签外的空行或空格将阻止 guestbook_authenticate() 运行。如果你知道不会将 PHP 用作 Apache 模块，那么你知道 PHP 不会尝试发送这些标头，你可以删除这段代码。不过，如果保留它，也不应有任何可见差异。

输入有效的用户名和密码后，将发送 edit.php 文件的其余部分。但这一次，除了所有其他信息外，还会包含一个复选框，以便用户决定删除哪些条目。复选框的值将是 guestbook 表的主键。

```
while ($row = mysql_fetch_array($result))
{
    // call the normal function to display a guestbook entry
    print_entry($row,$preserve,'name','entry date','location','email','URL','comments');
    // now add an extra row to allow the user to mark this entry
    // for deletion
    print <<<EOO
<tr>
<td valign="top" align="right"><b>Delete?</b></td>
<td valign="top" align="left">
<input type=checkbox name="entry_id[]"
value="{$row['entry_id']}">
Yes, delete entry #{$row['entry_id']}
</td>
</tr>
<tr><td colspan="2">&nbsp;</td></tr>
EOO;
}
```

随后，此表单将被提交到 confirm_delete.php 文件。注意，这里我们传递的是一个数组。表单元素的名称为 entry_id[]，这意味着当表单传递给 PHP 时，entry_id 将变成一个数组。数组中值的数量取决于选中的复选框数量。HTTP 根本不会发送未选中的框。

第一次处理 confirm_delete.php 文件时，我们将打印出条目。这样做是为了让删除这些条目的人确保自己没有做蠢事。

```
foreach ((array)$entry_id as $value)
{
print <<<EOO
<li>Delete entry #$value?
<input type="hidden" name="entry_id[]" value="$value">
EOO;
}
```

如果要删除其中任何条目，此页面将自行提交，并通过提交按钮发送一个不同的值（confirm delete）。这将导致以下代码运行：

```
foreach ($entry_id as $value)
{
print "<li>Deleting entry #$value\n";
safe_mysql_query("delete from guestbook where entry_id = $value");
}
```

我们遍历 $entry_id 数组，为每个成员删除记录。

