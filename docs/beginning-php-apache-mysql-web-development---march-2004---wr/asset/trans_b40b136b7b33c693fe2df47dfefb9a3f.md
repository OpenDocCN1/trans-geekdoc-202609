

# 使用表格显示数据

然后我们只需简单地 `echo` $table 的内容。最后，我们使用 `?>` 关闭 PHP 脚本。

通过使用这两个标签，我们可以使用原始的 HTML 代码（即不需要进行任何修改的 HTML 代码）。

正如你可能在第 2 章关于 heredoc（此处文档字符串）的讨论中记得的那样，我们可以将文本 'EOD' 更改为我们喜欢的任何内容，但开始和结束标签必须匹配。例如，这段代码运行运行良好：

```php
$table <<<HAHAHA
code here
HAHAHA;
```

但这段代码如下：

```php
$table <<<HAHAHA
code here
BOOHOO;
```

它将无法正常工作。你将收到一个类似于图 4-2 所示的错误。

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_135_0.png)

图 4-2

# 第 4 章

注意，`<<EOD` 和 `EOD;` 之后不能有任何空格。此外，结束标签上不能有前导空格、缩进或任何其他字符（允许分号）。即使只有一个空格，你也会收到错误。（由于在这些标签后多了一个空格，你可能需要花费几个小时来修复错误！）请始终记住删除这些标签之后所有的空格。

现在你已经可以创建一个表格，让我们用你的电影评论数据库中的一些数据来填充它吧。毕竟，这正是你来此的目的！

# 填充表格

查看我们的空白表格骨架，可以为你提供数据一旦从数据库检索后将如何布局的蓝图。

| 尝试一下 | 用数据填充表格 |
| :--- | :--- |

由于这是一段大量的代码，我们将在处理它的过程中解释其原理。所有的更改都已**加粗**显示。从原始脚本中去掉了几点（我们很快就会知道谁在关注了）。

- 使用你最喜欢的文本/HTML 编辑器打开 `table.php`，对现有代码进行以下更改。在本文示例中，我们使用了第 3 章中的数据库。
- 记得将 `servername`、`username`、`password` 和 `databasename` 替换为你自己的值。

```php
$link = mysqli_connect("servername","username","password") or die(mysqli_error());
mysql_select_db("wiley") or die (mysqli_error());
```

- 首先建立数据库建立连接。（你记得更改设置以反映你自己的配置了吧？很好。）

```php
$query = "SELECT
movie_name,
movie_director,
movie_leadactor
FROM
movie";
$result = mysqli_query($query,$link) or die(mysqli_error());
$num_movies = mysqli_num_rows($result);
```

- 对数据库运行 SQL 查询并获取结果。顺便，统计一下查询返回了多少条记录。

正如我们在第 3 章中讨论的那样，我们将 SQL 单词写成了大写。这是一种良好的习惯，因为它能让你轻松地识别出哪些单词是字段名，哪些单词是 SQL 关键字。让你的 SQL 查询尽可能易于阅读也是一个良好的习惯。这就是为什么我们把 SQL 查询分成了几行来写。

# 使用表格显示数据

```php
$movie_header <<=EOD
h2<center>Movie Review Database</center>/h2
<table width='70%' border='1' cellpadding='2' cellspacing='2' align='center'>
<tr>
  <th align='left'>Movie Title</th>
  <th align='left'>Movie Director</th>
  <th align='left'>Movie Lead Actor</th>
</tr>
</table>
EOD;
```

- 4. 然后输入原本在那里的代码块（减去 `echo` 语句）。

```php
// 注意它被名为 `$movie_header`，而不是 `$movie`（正如第一个例子那样）。
while($row = mysql_fetch_array($result)) {
  $movie_name = $row['movie_name'];
  $movie_director = $row['movie_director'];
  $movie_leadactor = $row['movie_leadactor'];

  $movie_details <<=EOD
<tr>
    <td>$movie_name</td>
    <td>$movie_director</td>
    <td>$movie_leadactor</td>
</tr>
EOD;
}
$movie_details .= <<=EOD
<tr>
  <td>&nbsp;</td>
</tr>
<tr>
  <td>Total: $num_movies Movies</td>
</tr>
EOD;
```

# 工作原理

前面的代码为我们完成了大量工作，所以让我们详细查看它。如你所知，`while` 语句会遍历返回的记录。对于每条记录，它都会执行括号之间的代码块。不用担心；PHP 足够聪明，知道这种情况有多少条记录以及当前是哪一条记录。不存在将错误值分配给错误记录的危险。`while` 循环内的第一行告诉脚本从当前记录中提取 `movie_name` 的值并将其放入名为 `$movie_name` 的变量中。接下来的四行做了相同的事情（嗯，几乎相同——它们只是将字段值赋值给不同命名的变量）。

# 第 4 章

接着遇到了你在在本章开头看到的熟悉的标签。它与之前的那个不同，因为它带有 `<<=EOD`。因此，不仅仅是记录的值，`$movie_details` 包含了所有返回的记录值。然后我们还包含了数据库中的电影总数。通过在 `<<=EOD` 前添加 `.=`，你正在将当前值加到现有值上。如果你忘记添加 `.=`，那么你将只得到最后一条记录的值。这是因为 `$var = "1"` 会让 `$var` 等于值 "1"。在前面的示例中，注意我们将其赋值了变量：

```php
while($row = mysql_fetch_array($result))
{
  // ...
}
```

