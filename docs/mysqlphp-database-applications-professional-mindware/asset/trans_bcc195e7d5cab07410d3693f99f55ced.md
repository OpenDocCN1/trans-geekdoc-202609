
你可以追踪一个线程到其源头。追踪帖子到其源头的非常简单的脚本看起来会像这样：

```
Select all fields from current topic
If parent_id is not equal to 0 and parent_id does not equal root_id
    Make parent ID current topic
    Go to line 1
```

这就差不多了。使用这种数据结构，你可以获得所需的所有信息。再加上几个时间戳以备安全，就万事俱备了。以下是创建表的 SQL 语句：

```
create table topics (
    topic_id integer default 0 not null auto_increment,
    parent_id integer default 0,
    root_id integer default 0,
    name varchar(255),
    description text,
    create_dt timestamp(14),
    modify_dt timestamp(14),
    author varchar(255),
    author_host varchar(255)
, primary key topics_key (topic_id)
);
```

## 代码概述

正如我们之前提到的，该应用程序涉及两个主要功能：显示帖子列表以及向数据库插入新帖子。因此，在基础层面上只有两个文件也就不足为奇了：display_topic.php 和 write_topic.php。除了这些文件之外，你还将有一个单独的文件来存储你的所有函数（functions.php）。如果你阅读了上一节，你可能不会感到惊讶地发现，开发此应用程序所涉及的大部分工作，因此我们将介绍的大部分代码都与显示特定帖子的祖先和子代有关。请记住，一个帖子可以有任意数量的祖先，也可以有任意数量的子代。因此，你的脚本必须足够灵活，能够处理只有一个回复或二十个回复的帖子。

将主题写入数据库的部分应该很容易处理。在你的表单中，你需要有标记 root_id 和 parent_id 的隐藏字段，并且你需要验证表单的内容，除此之外应该很容易。让我们分解一下。

## 代码分解

和往常一样，大多数乐趣都发生在函数中。事实上，在此应用程序中，实际上只有两个文件被 URL 引用，它们几乎是空的。

### 可复用函数

再次，这个应用程序将使用第 8 章中描述的函数。还有几个其他函数，其中一个使用了需要一些解释的技术。

### /BOOK/DISCUSSION/FUNCTIONS.PHP 中的函数

这个应用程序中新的概念称为递归。它出现在 display_kids() 函数中。

### DISPLAY_KIDS ()

通常，在本书的这一部分，一个函数会被显示然后描述。然而，这个函数必须以稍微不同的方式对待，因为递归在概念上可能有点困难。所以在显示函数之前，让我们先来看看递归。（如果你已经熟悉递归函数，请随意略过。）

需要记住的重要一点是，你不知道任何线程会有多深：可能只有一层回复，也可能有二十层。因此，要正确地排列任何一个线程的所有子代，你需要一个非常、非常灵活的脚本。它需要做类似这样的事情：

```
print current topic
while the current topic has unprocessed child topics
    set current topic to next unprocessed child
    go to line 1
end while
if current topic has a parent
    set current topic to that parent and go to line 2
else
    exit
end if
```

这必须无限重复，直到没有其他答案为止。但你如何告诉脚本在用完答案之前一直执行某些操作呢？我们迄今为止讨论过的循环机制根本不起作用。我们在第 2 章中讨论过并在前几章中使用过的 for.., while... 和 do...while 循环都没有帮助。

如果这还不清楚，请看表 12-6 和下面的代码。

## 表 12-6 示例表

| 帖子ID | 根ID | 父ID | 主题 | 姓名 | 日期 |
|---|---|---|---|---|---|
| 1 | 1 | 0 | Nachos rule | Jay | 3/12/2000 |
| 2 | 2 | 0 | Cheetos are the best | Ed | 3/12/2000 |
| 3 | 1 | 1 | Re: Nachos rule | Don | 3/12/2000 |
| 4 | 1 | 3 | Re: Nachos rule | Bill | 3/13/2000 |
| 5 | 5 | 0 | What about cookies | Evany | 3/13/2000 |
| 6 | 2 | 2 | Re: Cheetos are the best | Ed | 3/14/2000 |
| 7 | 1 | 4 | Cheetos, are you kidding | Jeff | 3/15/2000 |
| 8 | 5 | 5 | Re: What about cookies | Jay | 3/15/2000 |

假设你希望每个层级比前一个层级缩进得更深一些，使用 HTML blockquote 标签。现在假设你通过传递 topic_id 为 7 来调用下面的函数。

```
function RecurForMe($topic_id)
{
    $query = "SELECT * from topics WHERE topic_id = $topic_id;
    $result = mysql_query($query) or
        die("Query failed");
    $row = mysql_fetch_array($result);
    echo "<blockquote>";
    echo $row["name"], "\n";
    RecurForMe($row["parent_id"]);
}
```

你现在应该知道不要真正运行这样的脚本——没有错误检查，并且最终当查询没有响应时它会引发错误。我写这个函数是为了让你看最后一行。你看到它做了什么：函数调用了自身。如果你不清楚这会产生什么影响，让我们逐步走一遍。

第一次执行时，给定 $topic_id 为 7，查询将返回（不出所料）第 7 行。然后会打印出 blockquote 标签和名称（Jeff）。然后函数会调用自身，这次传递 parent_id 为 4。接下来，查询将返回第 4 行，下一次返回第 3 行，最后调用第 1 行。完成后，脚本输出（在错误之前）看起来像这样。

```
<blockquote>Jeff
<blockquote>Bill
<blockquote>Don
<blockquote>Jay
```

DisplayKids 函数的工作方式几乎完全相同。它会根据需要一直调用自身。但在最终脚本中，你需要考虑更多。例如，立即子代的 description 字段将被打印出来，但在祖先路径更深的地方，你只显示主题和姓名。在你陷入更大的脚本之前，让我们看看如何在你的简化脚本中根据祖先关系更改布局。

```
function RecurForMe($topic_id, $level = 1)
{
    $query = "SELECT * from topics  WHERE topic_id = $topic_id";
    $result = mysql_query($query);
    $row = mysql_fetch_array($result);
    echo "<blockquote>";
    echo $row["name"]. "\n";
    if($level == 1) {echo $row["subject"];;}
    RecurForMe($row["parent_id"], $level + 1);
}
```

我在这个函数中添加了另一个变量（$level）来跟踪层级。默认值是 1，并且每次执行时都会递增。第一次执行时会打印主题，但在第一次之后的迭代中，主题将不会被打印。

![](img/de0823012275cf4ceebdb822a56e6b71_351_0.png)

> 递归是一个昂贵的过程；它占用了相当多的处理器时间。为了防止系统不堪重负，你可能希望限制任何主题的深度

有了这些信息，你应该能够通过 DisplayKids 函数。里面有很多信息来确保良好的布局，但除此之外，它都相当易读。这里有一些注释来帮助你理解。

```php
function display_kids ($topic_id=0, $level=0)
{
    $child_count = 0;
    if (empty($topic_id)) { $topic_id = 0; }

    // retrieve topic records from the MySQL database having
    // this topic_id value in their parent_id column (i.e. those
    // for whom this topic is the parent_topic
    $query = "select topic_id, name, author, author_host, create_dt
        , description
        from topics where
        parent_id = $topic_id
        order by create_dt, topic_id
    ";
        $result = safe_query($query);
    while
    (list($r_topic_id,$r_name,$r_author,$r_author_host,$r_create_dt
        ,$r_description
        ) = mysql_fetch_row($result)
    )
    {
        if ($level)
        {
            // non-zero level - use unordered list format
            if (!$child_count)
            {
                // this is the first child record
                // - begin the list
                print "<ul>\n";
            }
            // begin the list item tag
            print "<li>";
        }
    else
    {
        // zero (first) level - print inside a table
        if (!$child_count)
        {
            // this is the first child record:
            // - print out a header
            print "<b>Comments:</b><br>\n";
        }
        print start_table();
        print " <tr bgcolor=skyblue>\n";
        print "  <td colspan=2 width=500>\n";
```
