

$text = "banana";
$text = eregi_replace("(.*)(nana)", "\\2\\1", $text);
echo($text); // outputs "nanaba"

在上述内容中，\\1 在替换字符串中被替换为 ba，这对应正则表达式中的 (.*)（零个或多个非换行字符）。\\2 被替换为 nana，这对应正则表达式中的 (nana)。

我们可以利用同样的原理来创建超链接。先从一种简单的链接形式开始，其中链接文本与 URL 相同。我们希望支持以下语法：

```
visit [L]http://www.php.net/[EL].
```

我们希望输出的相应 HTML 代码如下：

```
visit <a href="http://www.php.net/">http://www.php.net/</a>.
```

首先，我们需要一个能够匹配这种形式链接的正则表达式。正则表达式如下：

```
\[L\][-_.\/a-zA-Z0-9!&%#?,':=~+]\[EL\]
```

同样，我们在 [L] 和 [EL] 的开方括号前放置了反斜杠，以表明它们应被字面理解。然后，我们使用方括号列出希望作为 URL 一部分接受的所有字符。在方括号后放置一个 + 号，以表示 URL 将由从该列表中选取的一个或多个字符组成。

为了输出我们的链接，我们需要捕获 URL，并将其同时作为 A 标签的 HREF 属性和链接文本输出。要捕获 URL，我们用括号括起正则表达式中的相应部分：

```
\[L\]\([-_.\/a-zA-Z0-9!&%#?,':=~+]\)\[EL\]
```

因此，我们使用以下代码转换链接：

```
$joketext = eregi_replace(
 "\[L\]\([-_.\/a-zA-Z0-9!&%#?,':=~+]\)\[EL\]",
 "<a href=\"\\1\">\\1</a>", $joketext);
```

请注意，我们必须在链接的 HTML 代码中双引号前放置反斜杠，以确保 PHP 不会将其与围绕替换字符串的引号混淆。与此同时，\\1 将被链接的 URL 替换，输出结果如预期！

我们还希望支持链接文本与 URL 不同的超链接。假设我们的链接形式如下：

```
Check out [L=http://www.php.net/] PHP[EL].
```

以下是我们的正则表达式：

```
\[L=([-_./a-zA-Z0-9!#%&',:=~+]+)]([-_./a-zA-Z0-9 !#%&',:=~+]+)\[EL
```

看起来相当混乱，不是吗？仔细看看，你会发现它正好实现了我们需要的功能，同时捕获链接的 URL (\1) 和文本 (\2)。执行替换的 PHP 代码如下：

```
$joketext = ereg_replace(
"\[L=([-_./a-zA-Z0-9!#%&',:=~+]+)]".
"([-_./a-zA-Z0-9 !#%&',:=~+]+)\[EL",
"<a href=\"\\1\">\\2</a>", $joketext);
```

## 将文本分页

虽然不太可能有任何笑话长到需要分成多页，但许多内容驱动型网站（如 SitePoint.com）都有冗长内容，分页呈现效果最佳。PHP 中的另一个正则表达式函数使此变得异常简单。

split 是一个函数，它接受一个正则表达式和一个文本字符串，并使用正则表达式的匹配项将文本拆分为数组。

考虑以下示例：

```
$regexp="[ \n\r\t]+"; // One or more whitespace chars
$text="This is a test.";
$textarray=split($regexp,$text);
echo("$textarray[0]<br />"); // Outputs "This<br />"
echo("$textarray[1]<br />"); // Outputs "is<br />"
echo("$textarray[2]<br />"); // Outputs "a<br />"
echo("$textarray[3]<br />"); // Outputs "test.<br />"
```

如果我们搜索 [PAGEBREAK] 标签而不是空白字符，并且只显示我们感兴趣的页面（例如由随页面请求传递的 $page 变量指示），而不是文本的所有结果部分，我们就可以成功地将内容分页。

```
// If no page specified, default to the
// first page (Page = 0)
if (!isset($page)) $page = 0;

// Split the text into an array of pages
$textarray=split("\[PAGEBREAK\]",$text);

// Select the page we want
$pagetext=$textarray[$page];
```

当然，我们希望为用户提供页面间导航的方式。让我们在当前页面顶部放置一个指向上一页的链接，在底部放置一个指向下一页的链接。

当然，如果这是第一页，我们不需要指向上一页的链接。如果 $page 等于零，则说明我们在第一页。

同样，在内容的最后一页，我们不需要指向下一页的链接。要检测最后一页，我们需要使用我在第 6 章中简要介绍过的 count 函数。count 接受一个数组，并返回该数组中的元素个数。当将 count 传递给我们的页面数组时，它会告诉我们有多少页。如果有 10 页，那么 $textarray[9] 将包含最后一页。因此，如果 $page 等于 count($textarray) 减去一，则说明我们在最后一页。

用于翻页的链接代码如下：

```
if ($page != 0) {
    $prevpage = $page - 1;
    echo("<p><a href='$PHP_SELF?id=$id&page=$prevpage'>".
        "Previous Page</a></p>");
}

// output page content here...

if ($page < count($textarray) - 1) {
    $nextpage = $page + 1;
    echo("<p><a href='$PHP_SELF?id=$id&page=$nextpage'>".
        "Next Page</a></p>");
}
```

## 综合示例

用于输出笑话文本（包含所有特殊字符、分页和自定义标签转换）的完整代码如下。该文件，连同更新后的笑话列表脚本（jokelist.php）以及允许访客选择要查看的笑话类别的首页（index.php），均可在代码存档中找到（位于 http://www.sitepoint.com/books/）。

```
<!--- joke.php -->
...
// Get the joke text from the database
$joke = mysql_query("SELECT JokeText FROM Jokes ".
    "WHERE ID=$id");
$joke = mysql_fetch_array($joke);
$joketext = $joke["JokeText"];

// Filter out HTML code
$joketext = htmlspecialchars($joketext);

// If no page specified, default to the
// first page ($page = 0)
if (!isset($page)) $page = 0;

// Split the text into an array of pages
$textarray=split("\\\\[PAGEBREAK\\\\]",$joketext);

// select the page we want
$joketext=$textarray[$page];

// Bold and italics
$joketext = eregi_replace("\\[b\]", "<b>", $joketext);
$joketext = eregi_replace("\\[eb\]", " </b>", $joketext);
$joketext = eregi_replace("\\[i\]", "<i>", $joketext);
$joketext = eregi_replace("\\[ei\]", " </i>", $joketext);

// Paragraphs and line breaks
$joketext = eregi_replace("\\r", "", $joketext);
$joketext = eregi_replace("\\n\\n", "</p><p>", $joketext);
$joketext = eregi_replace("\\n", "<br />", $joketext);

// Hyperlinks
$joketext = ereg_replace(
  "\\[L=([-_.-/a-zA-Z0-9!&%#?,'=~:+]+)\\[EL]",
  "<a href=\"\\1\">\\1</a>", $joketext);
$joketext = ereg_replace(
  "\\[L=([-_.-/a-zA-Z0-9!&%#?,'=~:+]+)".
  "([-_.-/a-zA-Z0-9 !&%#?,'=~:+]+)\\[EL]",
  "<a href=\"\\1\">\\2</a>", $joketext);

if ($page != 0) {
  $prevpage = $page - 1;
  echo("<p><a href='$PHP_SELF?id=$id&page=$prevpage'>".
    "Previous Page</a></p>");
}

echo( "<p>$joketext</p> " );

if ($page < count($textarray) - 1) {
  $nextpage = $page + 1;
  echo("<p><a href='$PHP_SELF?id=$id&page=$nextpage'>".
    "Next Page</a></p>");
}
...
```

不要忘记提供文档，以便使用你的笑话提交表单的用户知道有哪些标签可用，以及每个标签的作用。

## 自动内容提交

投入如此多时间和精力构建一个如此易于使用、任何人都能上手的内容管理系统，却只有网站管理员被允许使用，这似乎有些可惜。此外，尽管管理员无需编辑 HTML 即可更新网站内容非常方便，但他或她仍然必须将提交的文档转录到“添加新笑话”表单中，并将任何格式化文本转换为我们上面开发的自定义格式语言——这无疑是一项乏味而令人疲惫的任务。

如果我们将“添加新笑话”表单交给普通网站访客使用，会怎样？

如果你还记得，我们在第 4 章中实际上已经这样做过，当时我们为用户提供了一个提交自己笑话的表单。当时，这只是一个演示如何在 PHP 脚本中制作 INSERT 语句的示例。我们没有将其包含在本章从零开始开发的代码中，是因为其中存在固有的安全风险。毕竟，谁愿意让自己的网站内容任由任何人篡改呢？

但新提交的笑话不必立即显示在网站上。如果我们在 Jokes 表中添加一个名为 Visible 的新列，该列可以采用两个值之一：'Y' 和 'N'，会怎样？新提交的笑话可以自动设置为 Visible='N'，并且如果我们在任何面向公众访问的 Jokes 表查询中添加 WHERE Visible='Y'，就可以防止它们出现在网站上。Visible='N' 的笑话将留在数据库中，等待内容经理审核，经理可以编辑每个笑话，然后决定将其设为可见或直接删除。

要创建一个包含两个值之一（其中一个为默认值）的列，我们需要一个名为 ENUM 的新 MySQL 列类型：

```
mysql> ALTER TABLE Jokes ADD COLUMN
-> Visible ENUM('N','Y') NOT NULL;
```

括号中列出的第一个值（本例中为 'N'）是默认值，如果 INSERT 语句中未指定值，则将其分配给新条目。

在新笑话对公众隐藏后，剩下的唯一安全细节是作者身份识别。我们希望能够识别数据库中哪个作者提交了特定笑话，但依赖“添加新笑话”表单中旧的作者下拉列表是不合适的，因为任何作者都可以冒充另一位作者。显然，需要某种用户名/密码身份验证方案。

要在 Authors 表中存储密码，只需添加另一列。然后，你可以要求作者在向数据库提交笑话时正确输入其电子邮件地址和密码。在允许作者修改其详细信息（姓名、电子邮件地址等）之前，你希望实施相同的登录流程。你甚至可以为每个作者提供一个类似“控制中心”的地方，让他们可以查看提交到网站的笑话状态。

