
```
$fields =func_get_args();
while (list($index,$field) = each($fields))
{
    print " <tr>\n";
    print " <td valign=top
align=right><b>".ucfirst($field).":</b></td>\n";
    print " <td align=top align=left><input type=text
name=$field size=40 value=\"" . $GLOBALS["last_$field"]."\"/></td>\n";
    print " </tr>\n\n";
}
}
```

注意到这里使用了全局变量作为文本字段的默认值。这是在用户输入错误信息且信息需要重新呈现用户所输入的值时使用的。为什么信息需要打印第二次？在阅读完下一个函数 create_entry() 后，这应该就完全说得通了。

## CREATE_ENTRY

我们不会简单地将用户信息转储到数据库中。首先需要对其进行验证。

```
function create_entry($name,$location,$email,$url,$comments)
{
    // remove all HTML tags, and escape any
    //other special characters
    $name = cleanup_text($name);
    $location = cleanup_text($location);
    $email = cleanup_text($email);
    $url = cleanup_text($url);
    $comments = cleanup_text($comments);

    // start out with an empty
    //error message. as validation tests fail,
    // add errors to it.
    $errmsg = "";
    if (empty($name))
    {
        $errmsg .= "<li>you have to put in a name, at least!\n";
    }

    // do a very simple check on the format of the email address
    // supplied by the user. an email address is required.
    if (empty($email) || !eregi("^[A-Za-z0-9_\-]+@[A-Za-z0-9_\-]+.[A-Za-z0-9_\-]+.*", $email))
    {
        $errmsg .= "<li>$email doesn't look like a valid email address\n";
    }
    else
    {
        // if the format is OK, check to see if this user has already
        // signed the guestbook. multiple entries are not allowed.
        $query = "select * from guestbook where email = '$email'";
        $result = safe_query($query);
        if (mysql_num_rows($result) > 0)
        {
            $errmsg .= 
            "<li>$email has already signed this guestbook.\n";
        }
    }

    // perform a very simple check on the format of the url supplied
    // by the user (if any)
    if (!empty($url) && !eregi("^http://[A-Za-z0-9%\?\._~:\/~\.-]+$",$url))
    {
        $errmsg .= "<li>$url doesn't look like a valid URL\n";
    }

    if (empty($errmsg))
    {
        $query = "insert into guestbook "
        . "(name,location,email,url,comments,remote_addr) values "
        ."('$name', '$location', '$email', '$url', "
        "'$comments','$REMOTE_ADDR')"
        ;
        safe_query($query);

        print "<h2>Thanks, $name!</h2>\n";
    }
    else
    {
        print <<<EOQ
<p>
<font color=red>
<b>
<ul>
$errmsg
</ul>
Please try again
</p>
EOQ;
    }
    return $errmsg;
}
```

此函数将确保输入的信息具有一定的实用性。如果信息存在问题，则会将描述问题的文本字符串赋给变量 $errmsg。如果函数执行后 $errmsg 为空，则值将被插入数据库。否则错误信息将被打印，并且用户输入的值将被赋给全局变量，以便下次循环时可作为文本字段的默认值打印。按顺序，此函数检查以下内容：

-   姓名字段包含内容
-   电子邮件地址可能是一个正确的地址（包含文本、一个 @ 和一个句点（.））。请注意，这并不是对电子邮件的严格验证。要彻底验证电子邮件需要一段非常长且复杂的脚本，正如你在后续章节中会看到的那样。
-   如果电子邮件看起来没问题，则该电子邮件地址尚未在数据库中输入过
-   URL 可能有效

![](img/de0823012275cf4ceebdb822a56e6b71_239_0.png)

请参阅附录 F 了解有关正则表达式的更多详细信息。

## SELECT_ENTRIES()

此函数的唯一目的是组装你的数据库调用。

```
function select_entries ($offset=0)
{
    if (empty($offset)) { $offset = 0; }
    $query = "select *
        , date_format(created,'%e %M, %Y %h:%i %p') as entry_date
        from guestbook
        order by created desc
        limit $offset, " . PAGE_LIMIT
    ;
    $result = safe_query($query);
    return $result;
}
```

你已经知道 PAGE_LIMIT 设置每页显示的记录数。作为 limit 子句中的第二个参数，$offset 变量指示查询将返回哪些记录。如果你对 $offset 的理解有困难，请查看第 3 章中对 limit 子句的解释。$offset 的值将通过导航元素传递。我们在讨论下一个函数时会详细检查这一点。

为了以可读的方式检索日期值，此查询使用了 MySQL 的日期函数。MySQL 将日期和时间存储为 14 位数字（YYYY:MM:DD:HH:SS），但以更易于人类阅读的方式返回日期信息会更好。MySQL 的 date_format 函数以我们想要使用的方式检索信息。此函数以及许多其他 MySQL 函数在附录 I 中进行了讨论。

## NAV()

此函数的唯一目的是创建导航元素。

```
function nav ($offset=0,$this_script="")
{
    global $PHP_SELF;

    if (empty($this_script)) { $this_script = $PHP_SELF; }
    if (empty($offset)) { $offset = 0; }

    // get the total number of entries in the guest book -
    // we need this to know if we can go forward from where we are
    $result = safe_query("select count(*) from guestbook");
    list($total_rows) = mysql_fetch_array($result);

    print "<p>\n";
    if ($offset > 0)
    {
        // if we're not on the first record, we can always go backwards
        print "<a href=\"{$this_script}?offset=\".($offset-PAGE_LIMIT).\">&lt;&lt;Previous Entries</a> &nbsp; ";
    }
    if ($offset+PAGE_LIMIT < $total_rows)
    {
        // offset + limit gives us the maximum record number
        // that we could have displayed on this page. if it's
        // less than the total number of entries, that means
        // there are more entries to see, and we can go forward
        print "<a href=\"{$this_script}?offset=\".($offset+PAGE_LIMIT).\"\">Next Entries&gt;&gt;</a> &nbsp; ";
    }
    print "</p>\n";
}
```

在适当的情况下，此函数将插入链接，使用户能够查看下一组条目、上一组条目或两者兼有。这一切都由 $offset 变量和 PAGE_LIMIT 常量决定。

第一次运行时 $offset 没有值，因此不会有上一条目链接（因为 $offset 不会大于 0）。但如果还有更多行需要显示，将会创建一个链接，如果跟随该链接则会为 $offset 创建一个值。

假设这是我们第一次执行此函数，因此 $offset 没有值，数据库中有 10 行。当脚本到达最后一个 if... 时，它会看到还有更多行需要显示（$offset + PAGE_LIMIT = 2，小于 10），因此以下链接将被打印。

```
<a href="/book/guestbook2k/view.php?offset=2">
Next Entries&gt;&gt;</a>
```

## 有趣的代码流程

一旦你理解了迄今为止介绍的函数的工作原理，你应该不会有任何问题弄清楚 guestbook2k 的工作原理。在大多数情况下，浏览器调用的页面几乎没有做多少工作。这些页面基本上是函数调用的集合。

我们将详细分解一个文件，以便你了解这种结构的工作原理。其余大部分内容你应该可以通过在文件和函数说明之间切换来弄清楚。在以下各节中，我们将逐步介绍 view.php 文件。

## 查看条目

这是代码的逻辑流程。

```
<?php
include "header.php";

$page_title = "View My Guest Book!!";
include "start_page.php";
?>
```

在每个页面中需要做的第一件事是包含 header.php 文件。这将允许访问我们之前概述的所有函数。之后你应该从 start_page.php 包含标准页眉信息。你必须在包含 start_page.php 之前声明 $page_title，以便标题能够以标准方式在每个页面上打印。
