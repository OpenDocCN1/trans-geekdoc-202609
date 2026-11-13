
与我们为作者开发的代码几乎完全相同，
只有一个重要例外。

当我们删除一个类别时，不能同时删除属于该类别的任何笑话，因为这些笑话也可能属于其他类别。我们可以检查每个笑话，看它是否属于其他任何类别，并仅删除那些不属于的笑话，但与其进行如此耗时的过程，不如允许在数据库中包含根本不属于任何类别的笑话。这些笑话对网站访问者不可见，但会保留在数据库中，以防我们以后想将它们分配给某个类别。

因此，要删除一个类别，我们还需要删除引用该类别的JokeLookup表中的任何条目：

```
<!-- deletecat.php -->
...
// Delete all joke lookup entries for the
// category along with the entry for the category.
$ok1 = @mysql_query("DELETE FROM JokeLookup WHERE
CID=$id");
$ok2 = @mysql_query("DELETE FROM Categories WHERE
ID=$id");
...
```

除此之外，类别管理在功能上与作者管理相同。如果需要，cats.php、newcat.php、
deletecat.php 和 editcat.php 的代码可在代码存档中找到
（位于 http://www.sitepoint.com/books/）如果需要。

## 管理笑话

除了在数据库中添加、删除和修改笑话外，我们还需要能够为笑话分配类别和作者。

此外，我们可能拥有的笑话比作者或类别多得多。因此，尝试显示完整的笑话列表（就像我们为作者和类别所做的那样）可能会导致一个难以管理的长列表，并且无法轻松找到我们想要的那个笑话。因此，我们需要创建一种更智能的方法来浏览我们的笑话库。

在不同时间，我们可能知道要处理的笑话的类别、作者或其中的一些文本，因此让我们支持所有这些方法来定位数据库中的笑话。提示管理员提供所需笑话信息的表格必须展示类别和作者列表。该代码如下：

```
<!-- jokes.php -->
<html>
<head>
<title> Manage Jokes </title>
</head>
<body>
<h1>Manage Jokes</h1>
<p><a href="newjoke.php">Create New Joke</a></p>
<?php
$dbcnx = mysql_connect("localhost", "root", "mypasswd");
mysql_select_db("jokes");
$authors = mysql_query("SELECT ID, Name FROM Authors");
$cats   = mysql_query("SELECT ID, Name FROM
Categories");
?>
<form action="jokelist.php" method="post">
<p>View jokes satisfying the following criteria:<br />
By Author:
<select name="aid" size="1">
<option selected value=" ">Any Author</option>
<?php
while ($author = mysql_fetch_array($authors)) {
  $aid = $author['ID'];
  $aname = htmlspecialchars($author['Name']);
  echo("<option value='$aid'>$aname</option>\n");
}
?>
</select><br />
By Category:
<select name="cid" size="1">
<option selected value=" ">Any Category</option>
<?php
while ($cat = mysql_fetch_array($cats)) {
  $cid = $cat['ID'];
  $cname = htmlspecialchars($cat['Name']);
  echo("<option value='$cid'>$cname</option>\n");
}
?>
</select><br />
Containing Text: <input type="text" name="searchtext" />
<br />
<input type="submit" name="submit" value="Search" />
</form>
<p align="center"><a href="admin.html">Return to Front
Page</a></p>
</body>
</html>
```

请注意，echo 函数输出的字符串末尾的 \n 是换行符的特殊代码，用于使该脚本输出的 HTML 代码更易读。另外，请注意使用 htmlspecialchars 以确保显示时作者和类别名称不包含任何麻烦的字符。

由 jokelist.php 负责使用上述表单中提交的值来构建满足指定条件的笑话列表。显然，这将通过 SELECT 查询完成，但该查询的确切性质将取决于通过我们上面定义的表单输入的内容。由于构建这个 SELECT 语句是一个相当复杂的过程，让我们逐步分析 jokelist.php。

首先，我们先处理一些准备工作：

```
<!-- jokeslist.php -->
<html>
<head>
<title>Manage Jokes</title>
</head>
<body>
<h1>Manage Jokes</h1>
<p><a href="jokes.php">New Search</a></p>
<?php
$dbcnx = mysql_connect("localhost", "root", "mypasswd");
mysql_select_db("jokes");
?>
```

首先，我们定义几个字符串，将它们串联在一起，即可形成如果在表单中未选择任何约束时所需的 SELECT 查询：

```
// The basic SELECT statement
$select = "SELECT DISTINCT ID, JokeText";
$from = " FROM Jokes";
$where = " WHERE ID > 0";
```

上述代码中的 WHERE 子句可能有点令人困惑。其思路是，我们可以根据表单中选择的约束，在此基本 SELECT 语句的基础上进行扩展。这些约束将要求我们向 SELECT 语句的 FROM 和 WHERE 子句（部分）添加内容。但如果未指定任何约束（即管理员想要数据库中所有笑话的列表），则根本不需要 WHERE 子句！因为很难向不存在的 WHERE 子句添加内容，所以我们需要想出一个“什么都不做”的 WHERE 子句。因此，我们引入了 Jokes.ID 必须大于零的要求。这非常合适，因为 MySQL 的 AUTO_INCREMENT 功能（负责为此列分配值）将始终选择大于零的整数。

我们的下一项任务是检查表单中可能设置的每个可能的约束（作者、类别和搜索文本），并相应地调整 SQL。首先，我们处理指定了作者的情况。

表单中的“任何作者”选项被赋予了 ""（空字符串）的值，因此如果该表单字段的值（存储在 $aid 中）不等于 ""，则表示已指定作者，我们必须调整我们的查询：

```
if ($aid != "") { // An author is selected
    $where .= " AND AID=$aid";
}
```

 .= 运算符用于将新字符串附加到现有字符串的末尾。在此情况下，我们向 WHERE 子句添加条件，即 Jokes 表中的 AID 必须与表单中选择的作者 ID（$aid）匹配。

接下来，我们处理笑话类别的指定：

```
if ($cid != "") { // A category is selected
    $from .= ", JokeLookup";
    $where .= " AND ID=JID AND CID=$cid";
}
```

由于特定笑话关联的类别存储在 JokeLookup 表中，我们需要将此表添加到查询中以创建连接。为此，我们只需将表名附加到 $from 变量的末尾。为了完成连接，我们还必须指定 Jokes 表中的 ID 列必须与 JokeLookup 中的 JID 列匹配，因此我们将此条件添加到 $where 变量中。最后，我们要求 JokeLookup 中的 CID 列必须与表单中选择的类别 ID（$cid）匹配。

处理搜索文本非常简单，使用了我们在第二部分中学到的 LIKE SQL 运算符：

```
if ($searchtext != "") { // Search text was specified
    $where .= " AND JokeText LIKE '%$searchtext%'";
}
```

现在我们已经构建了 SQL 查询，可以使用它来检索和显示笑话，以及允许我们编辑和删除它们的链接（就像我们为作者和笑话类别所做的那样）。为了可读性，我们在 HTML 表中显示笑话：

```
?>
<table border="1">
<tr><th>Joke Text</th><th>Options</th></tr>
<?php
$jokes = mysql_query($select . $from . $where);
if (!$jokes) {
    echo("</table>");
    echo("<p>Error retrieving jokes from database!<br />".
        "Error: " . mysql_error() . "</p>");
    exit();
}
```

```
while ($joke = mysql_fetch_array($jokes)) {
    echo("<tr valign='top'>\n");
    $id = $joke["ID"];
    $joketext = htmlspecialchars($joke["JokeText"]);
    echo("<td>$joketext</td>\n");
    echo("<td><a href='editjoke.php?id=$id'>Edit</a>|".
        "<a href='deletejoke.php?id=$id'>Delete</a></td>".
        "</td>\n");
    echo("</tr>\n");
}
?>
</table>
</body>
</html>
```

处理完 jokelist.php 后，让我们来处理 newjoke.php，它在 jokes.php 顶部链接。此页面将与 newauthor.php 和 newcat.php 非常相似。但是，除了指定笑话文本外，此页面还必须允许管理员为笑话分配作者和类别。这些功能使得这个文件的代码值得仔细审查。

从查看 newauthor.php 的代码可知，处理表单提交的 PHP 代码位于表单代码本身之前（不一定非要如此，但这是我们迄今为止使用的布局）。但让我们先看看表单代码，以便处理表单提交的代码更容易理解。

首先，我们获取数据库中所有作者和类别的列表：

```
<?php
else:
    $dbcnx = mysql_connect("localhost", "root",
        "mypasswd");
    mysql_select_db("jokes");
    $authors = mysql_query("SELECT ID, Name FROM Authors");
    $cats    = mysql_query("SELECT ID, Name FROM Categories");
?>
```

接下来，我们创建表单。我们从一个标准的文本区域开始，用于输入笑话文本：

```
<form action="<?=$PHP_SELF?>" method="post">
<p>Enter the new joke:<br />
<textarea name="joketext" rows="15" cols="45" wrap></textarea>
```
