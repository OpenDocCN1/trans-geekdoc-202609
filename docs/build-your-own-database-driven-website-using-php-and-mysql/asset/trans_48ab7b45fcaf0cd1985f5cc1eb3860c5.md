

query，mysql_query 返回一个标识“结果集”的数字，该结果集包含查询返回的所有行（条目）的列表。如果查询因任何原因失败，仍会返回 False。

```php
$result = @mysql_query("SELECT JokeText FROM Jokes");
if (!$result) {
    echo("<p>Error performing query: " . mysql_error() .
    "</p>");
    exit();
}
```

前提是处理查询时未出现错误，上述代码将把一个包含 Jokes 表中所有笑话文本的结果集放入变量 $result 中。由于数据库中笑话数量没有实际限制，该结果集可能非常大。

我们之前提到过，while 循环是处理大量数据的有用控制结构。以下是逐行处理结果集中行的代码大纲：

```php
while ( $row = mysql_fetch_array($result) ) {
    // process the row...
}
```

while 循环的条件可能与你习惯的条件不太相似，让我来解释它的工作原理。请将该条件视为一个独立的语句：

```php
$row = mysql_fetch_array($result);
```

mysql_fetch_array 函数接受一个结果集作为参数（在此例中存储在 $result 变量中），并将结果集中的下一行作为数组返回。如果你不熟悉数组的概念，请不用担心：我们稍后会讨论它。当结果集中没有更多行时，mysql_fetch_array 反而返回 false。

现在，上述语句给 $row 变量赋值，同时整个语句本身也采用该值。这正是使我们能够在 while 循环中使用该语句作为条件的原因。由于 while 循环会一直循环，直到其条件求值为 false，因此循环次数将与结果集中的行数相同，每次循环执行时，$row 都会取下一行的值。剩下的就是弄清楚如何在循环每次运行时从 $row 变量中取出值。

结果集的行表示为数组。数组是一种包含多个值的特殊变量。如果你将变量视为包含值的盒子，那么数组可以看作是带有隔间的盒子，每个隔间能够存储单个值。对于我们的数据库行，这些隔间以结果集中的表列命名。如果 $row 是结果集中的一行，那么 $row["joketext"] 就是该行 JokeText 列中的值。因此，如果我们想要打印数据库中所有笑话的文本，我们的 while 循环应如下所示：

```php
while ( $row = mysql_fetch_array($result) ) {
 echo("<p>" . $row["JokeText"] . "</p>");
}
```

总结一下，下面是一个 PHP 网页的完整代码，它将连接到我们的数据库，获取数据库中所有笑话的文本，并以 HTML 段落的形式显示它们。本示例的代码可作为 jokelist.php 在代码存档中找到（位于 http://www.sitepoint.com/books/）：

```php
<html>
<head>
<title> Our List of Jokes </title>
</head>
<body>
<?php
// Connect to the database server
$dbcxn = @mysql_connect("localhost", "root",
"mypasswd");
if (!$dbcxn) {
 echo( "<p>Unable to connect to the " .
 "database server at this time.</p>" );
 exit();
}
// Select the jokes database
if ( ! @mysql_select_db("jokes") ) {
 echo( "<p>Unable to locate the joke " .
 "database at this time.</p>" );
 exit();
}
?>

<p> Here are all the jokes in our database: </p>
<blockquote>

<?php

// Request the text of all the jokes
$result = @mysql_query("SELECT JokeText FROM Jokes");
if (!$result) {
 echo( "<p>Error performing query: " . mysql_error() . "</p>" );
 exit();
}

// Display the text of each joke in a paragraph
while ( $row = mysql_fetch_array($result) ) {
 echo("<p>" . $row["JokeText"] . "</p>");
}

?>
</blockquote>
</body>
</html>
```

## 向数据库插入数据

在本节中，我们将了解如何利用现有的所有工具，允许网站访问者将自己的笑话添加到数据库中。如果你喜欢挑战，在继续阅读之前，或许可以尝试独立解决这个问题。本节几乎没有新内容，它主要是对迄今所学所有内容的示例应用。

如果你想让网站访问者输入新笑话，显然需要一个表单。以下是一个合适的表单代码：

```
<form action="?=$PHP_SELF?>" method="post">
<p>Type your joke here:<br />
<textarea name="joketext" rows="10" cols="40" wrap>
</textarea><br />
<input type="submit" name="submitjoke" value="SUBMIT" />
</p>
</form>
```

如前所述，提交此表单时，将加载同一页面（由于在表单的 ACTION 属性中使用了 $PHP_SELF 变量），但请求中会附带两个变量。第一个变量 $joketext 将包含在文本区域中输入的笑话文本。第二个变量 $submitjoke 始终包含值 "SUBMIT"，可用作已提交笑话的标志。

要将提交的笑话插入数据库，我们只需使用 mysql_query 运行 INSERT 查询，使用 $joketext 变量作为要提交的值：

```php
if ($submitjoke == "SUBMIT") {
    $sql = "INSERT INTO Jokes SET
        JokeText='$joketext',
        JokeDate=CURDATE()";
    if (@mysql_query($sql)) {
        echo("<p>Your joke has been added.</p>");
    } else {
        echo("<p>Error adding submitted joke: " .
            mysql_error() . "</p>");
    }
}
```

本示例中唯一的新技巧出现在这里的 SQL 代码中。请注意使用 MySQL 函数 CURDATE() 将当前日期作为要插入数据库的 JokeDate 列的值。MySQL 实际上有几十个这样的函数，但我们将仅在需要时介绍它们。有关完整函数参考，请参阅附录 B。

我们现在拥有允许用户输入笑话并将其添加到数据库的代码。剩下的只是以实用的方式将其插入到我们现有的笑话查看页面中。由于大多数用户只想查看我们的笑话，除非用户表达添加新笑话的意愿，否则我们不想用一个又大又丑的表单来破坏页面。出于这个原因，我们的应用非常适合作为多用途页面实现。以下是代码（可作为 jokes.php 在代码存档中找到，位于 http://www.sitepoint.com/books/）：

```php
<html>
<head>
<title> The Internet Joke Database </title>
</head>
<body>
<?php
if (isset($addjoke)): // If the user wants to add a joke ?>
<form action="<?=$PHP_SELF?>" method="post">
<p>Type your joke here:<br />
<textarea name="joketext" rows="10" cols="40" wrap>
</textarea><br />
<input type="submit" name="submitjoke" value="SUBMIT" />
</p>
</form>
<?php
else: // Default page display
// Connect to the database server
$dbcnx = @mysql_connect("localhost", "root",
"mypasswd");
if (!$dbcnx) {
echo( "<p>Unable to connect to the " .
"database server at this time.</p>" );
exit();
}
// select the jokes database
if (! @mysql_select_db("jokes") ) {
echo( "<p>Unable to locate the joke " .
"database at this time.</p>" );
exit();
}
// If a joke has been submitted,
// add it to the database.
if ($submitjoke == "SUBMIT") {
$sql = "INSERT INTO Jokes SET
    JokeText='$joketext',
    JokeDate=CURDATE()";
if (@mysql_query($sql)) {
    echo "<p>Your joke has been added.</p>";
} else {
    echo "<p>Error adding submitted joke: " .
        mysql_error() . "</p>";
}
}
echo("<p> Here are all the jokes in our database: " .
    "</p>");
// Request the text of all the jokes
$result = @mysql_query("SELECT JokeText FROM Jokes");
if (!$result) {
    echo "<p>Error performing query: " .
        mysql_error() . "</p>";
    exit();
}
// Display the text of each joke in a paragraph
while ( $row = mysql_fetch_array($result) ) {
    echo("<p>" . $row["JokeText"]. "</p>");
}
// when clicked, this link will load this page
// with the joke submission form displayed.
echo("<p><a href='$PHP_SELF?addjoke=1'>" .
    "Add a Joke!</a></p>");
endif;
?>
</body>
</html>
```

搞定了！使用一个包含少量 PHP 代码的文件，我们既可以查看现有笑话，也可以向 MySQL 数据库添加笑话。

### 挑战

作为作业，看看你能否想出如何在页面中每个笑话旁边放置一个标记为“删除此笑话”的链接，点击后将从数据库中删除该笑话并显示更新后的笑话列表。以下是几个入门提示：

- 你仍然可以在单个多用途页面中完成所有操作。
- 你需要使用 SQL DELETE 命令，我们在第 2 章中学习过。

