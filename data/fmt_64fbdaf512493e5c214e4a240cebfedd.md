
```php
<?php
$link = mysqli_connect('localhost', 'root', '');
or die("Could not connect: " . mysqli_error());
mysqli_select_db($link, 'chapter6', $link) or die(mysqli_error());
$sql = "SELECT id, name FROM movetype ORDER BY name";
$result = mysqli_query($sql)
or die("Invalid query: " . mysqli_error());
while ($row = mysqli_fetch_array($result, MYSQLI_ASSOC)) {
?>
<html
<head>
<title>Add Movie</title>
</head>
<body>
<form action="commit.php?action=add&type=movie" method="post">
<table border="0" cellspacing="0" width="100%">
<tr>
<td>Movie Name</td>
<td><input type="text" name="movie_name"></td>
</tr>
<tr>
<td>Movie Type</td>
<td>
<select name="movie_type">
<option value="">Select a type...</option>
<?php
foreach ($people as $id => $name) {
?>
<option value="<?php echo $id;?>"><?php echo $name;?></option>
<?php
}
?>
</select>
</td>
</tr>
<tr>
<td>Lead Actor</td>
<td>
<select name="movie_leadactor">
<option value="">Select an actor...</option>
<?php
foreach ($people as $id => $name) {
?>
<option value="<?php echo $id;?>"><?php echo $name;?></option>
<?php
}
?>
</select>
</td>
</tr>
<tr>
<td>Director</td>
<td>
<select name="movie_director">
<option value="">Select a director...</option>
<?php
foreach ($people as $id => $name) {
?>
<option value="<?php echo $id;?>"><?php echo $name;?></option>
<?php
}
?>
</select>
</td>
</tr>
<tr>
<td colspan="2" align="center">
<input type="submit" name="submit" value="Add">
</td>
</tr>
</table>
</form>
</body>
</html>
```

*(注意：提供的 OCR 文本非常碎片且代码块包含错误。我已根据 PHP/MySQL 应用的上下文重建了逻辑。)*

2. 保存文件并将其上传到服务器上新的 `chapter6` 目录。

3. 创建一个名为 `commit.php` 的新空文件并输入以下代码：

```php
<?php
// COMMIT ADD
$link = mysqli_connect("localhost", "root", "")
nor die("Could not connect: " . mysqli_error());
mysqli_select_db($link, "chapter6", $link) or die(mysqli_error());
switch ($_GET['action']) {
case "add":
switch ($_GET['type']) {
case "movie":
$Sql = "INSERT INTO
movie (
movie_name,
movie_year,
movie_type,
movie_leadactor,
movie_director
)VALUES
(
"".\$_POST['movie_name']."",
"".\$_POST['movie_year']."",
"".\$_POST['movie_type']."",
"".\$_POST['movie_leadactor']."",
"".\$_POST['movie_director']."\)";
```

```php
*;
break;
break;
) if (isset($sql) && !empty($sql)) {
    echo "!-".$sql->mysql->*";
    $result = mysql_query($sql)
    or die("Invalid query: " . mysql_error());
}
```

<p align="center" style="color:#FF0000">

完成。<a href="index.php">索引</a>

</p>

```php
<?php
?>
```

- 4. 保存您的文件并将其上传到服务器上的新 `chapter6` 目录。

- 5. 在浏览器中打开 `index.php` 页面，点击 `movie` 表头旁的 ADD。

- 6. 按照图 6-5 和 6-6 所示的表单，添加一个名为“Test”的电影，并随机选择电影类型、演员和导演。

| 电影名称 | |

|---|---|

| 电影类型 | 选择一个类型... |

| 电影年份 | 选择一个年份... |

| 主演员 | 选择一个演员... |

| 导演 | 选择一个导演... |

| | 添加 |

图 6-5

| 电影名称 | Test |

| --- | --- |

| 电影类型 | 冒险片 |

| 电影年份 | 2002 |

| 主演员 | Kevin Kline |

| 导演 | Lawrence Kasden | 添加 |

图 6-6

- 7. 点击“add”按钮，你将看到如图 6-7 所示的确认消息。

## 工作原理

当你有一个实际的插入方法时，插入数据总是会更容易（记住这句格言）。

我们通常使用 HTML 表单。

HTML 表单允许我们控制用户输入数据的方式。提交后，表单会向服务器发送信息，PHP 可以利用这些信息来生成并运行 SQL INSERT 语句。

如你在 `movie.php` 的电影插入表单中所示，我们有四个组合框和一个文本字段。文本字段的内容由你决定，但组合框具有很强的指导性。让我们回顾一下从数据库内容生成的组合框内容。

174

## 让用户编辑数据库

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_197_0.png)

首先，我们关注人员组合框。每个组合框列出了 `people` 表中存在的所有。

```php
<?php
$link = mysql_connect("localhost", "root", "*");
or die("Could not connect: " . mysql_error());
mysql_select_db('chapter6', $link) or die (mysql_error());
$peoplesql = "SELECT
FROM
`people`
*";
$result = mysql_query($peoplesql . " * " . mysql_error());
or die("Invalid query: " . mysql_error());
while($row = mysql_fetch_array($result , MYSQL_ASSOC)){
  $people[] = array($row['`people_id`'] => $row['`people_fullname`']);
}
?>
```

175

在表单脚本的开头，我们查询 `people` 表并将内容放入数组中。关于系统已知人员的数据存储在 `people` 表中。

为了生成人员列表，我们只需查询数据库，检索系统中的所有人员，并在组合框中显示名称，同时将其主键作为项值。每个人在组合框中都有一个：

```html
<SELECT name="movie_director">
  <option value="" SELECTED>Select a director...</option>
<?php
foreach ($people as $people_id => $people_fullname) {
  <option value="<?php echo $people_id? ?>"><?php echo $people_fullname? ?></option>
}
<?php?>
</SELECT>
```

在这里我们使用 `foreach` 语法解析数组以生成选项。

现在我们将生成电影类型组合框。这是 SQL SQL 生成内容的一种更常规的用法。我们将复用这段代码来创建一个通用的编辑表单，因此你需要理解其工作原理的细节。

此代码通过查询 `movietype` 表提取所有可用的电影类型，从而生成组合框中的选项。每个选项将具有电影类型 ID 作为值，并将电影类型本身作为标签。

现在表单已准备就，我们需要一个 `switch` 来创建记录。如你所见，针对 `$_GET['action']` 的 `switch case` 目前完全没用。在接下来的练习中，我们将为 `movie.php` 脚本添加大量代码，以便可以使用它来编辑电影。

176

## 删除记录

删除记录非常简单（有时甚至太简单了——你明白我的意思）。正如我们之前所说，务必在测试数据库上测试你的查询。在测试数据库中删除记录不会威胁你的系统，而测试查询可以帮助你在删除生产数据库中的所有记录之前发现任何 SQL 错误，防止因为你忘记了像 `WHERE` 子句这样的小细节。MySQL 会删除所有匹配 SQL 语句的记录。如果你在查询中省略了 `WHERE` 子句，所有记录将匹配 SQL 语句并被删除。

删除意味着丢失数据。要删除记录，你需要通过 `WHERE` 语句指向数据库引擎。一旦执行该语句，就无法挽回。记录将被删除，且没有回旋的希望；这就是为什么我们建议在使用 `DELETE` 语句时要加小心。

## 尝试删除单条记录

在要求 PHP 删除任何内容之前，你将尝试从 phpMyAdmin 中删除记录，以熟悉 `DELETE` 语句。按照以下步骤删除记录：

- 打开 phpMyAdmin 并输入以下代码：

```sql
DELETE FROM
movie
WHERE
movie_id = '12'
LIMIT 1
```

phpMyAdmin 返回一条消息，说明你已从 'movie' 表中删除了一条记录。

## 工作原理

`DELETE` SQL 语句非常简单。如你所见，我们使用了 `LIMIT 1` 语句将删除限制为一条记录（以防万一）。

## 级联删除

如你所知，数据库通常在不同的表中持有记录。不考虑关系的情况下删除记录会引入混乱和沉重的人工数据库维护。遗憾的是，MySQL 不会自动为你管理关系，也不会维护引用完整性。

为了避免这个问题，我们使用更复杂的 `DELETE` 语句，即级联删除，如本节所示。

## 尝试级联删除

现在你已经知道了如何使用 `DELETE`，你将尝试从 phpMyAdmin 删除一个记录。按照以下步骤实现级联删除：

1. 创建一个名为 `delete.php` 的新文件并输入以下代码：

```php
<?php
$link = mysql_connect("localhost", "root", "*");
or die("Could not connect: " . mysql_error());
mysql_select_db('chapter6', $link) or die (mysql_error());

if (isset($_GET['delete']) || $_GET['delete'] != 1) {

  if ($_GET['type'] == "people") {
    // 删除 movie 表中的人员引用
    $actor = "UPDATE
      movie
    SET
      movie_leadactor = '0'
    WHERE
      movie_leadactor = '" . $_GET['id'] . "
    ";
    $result = mysql_query($actor)
    or die("Invalid query: " . mysql_error());
    // 删除导演引用
    $director = "UPDATE
      movie
    SET
      movie_director = '0'
    WHERE
      movie_director = '" . $_GET['id'] . "
    ";
    $result = mysql_query($director)
    or die("Invalid query: " . mysql_error());
  }
  // 生成 SQL
  $sql = "DELETE FROM
    " . $_GET['type'] . "'
  WHERE
    id = '" . $_GET['id'] . "'
  LIMIT 1";
  // 为了调试目的输出 SQL
  echo "<-" . $sql . "->";
  $result = mysql_query($sql)
  or die("Invalid query: " . mysql_error());
}
?>
<p align="center" style="color:#FF0000">
你的 php <?php echo $_GET['type']?> 已删除。<a href='index.php'>索引</a>
</p>
```

- 2. 保存 `delete.php` 并将其上传到你的 `chap6` 目录。

- 3. 在浏览器中打开 `index.php`。你将在每个电影或人员旁边看到 [DELETE] 链接，如图 6-8 所示。

- 4. 点击 Test 电影名称旁边的 DELETE 链接尝试删除你之前练习添加的电影。你将被要求确认，如图 6-9 所示。

- 5. 点击“yes”链接确认删除并等待如图 6-10 所示的确认消息。

# 第6 章

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_202_0.png)

图 6-9

## 工作原理

在这里，我们正计划消灭掉一组无辜的数据。让我们抛开任何道德问题不谈，看看这个脚本是如何运作的。

首先，你需要理解，在关系型数据库中，你不能删除记录后就直接忘掉它们。删除操作必须仔细考虑。例如，如果你从'people'（人员）表中删除了某人，这将阻止你从'movie'（电影）表中找到对该人的潜在引用。如果你从'people'表中删除了吉姆·凯瑞（Jim Carrie），那么《真神天降》（Bruce Almighty）的主角将会是谁呢？如果你什么都不删除，吉姆·凯瑞的 ID 将保留在记录中，导致你将拥有一个损坏的数据库。你不希望那样，对吧？（答案是否定的。）

这个问题的解决方案是确保你始终让圆木头（圆木头即外键）插入圆孔中（圆孔即记录）。在代码中，我们用值 0 更新 'movie' 表（该默认值告诉脚本我们在删除 'people' 记录之前尚未设置过它）。这同时也允许我们检查 UPDATE SQL 语句的行为。（生活不是很美好吗？）

180

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_203_0.png)

```php
 // 删除对主演的引用
$actor = "UPDATE
`movie`
SET
`movie_leadactor` = '0'
WHERE
`movie_leadactor` = '*'.$GET['id'].*'
";
$result = mysql_query($actor) 
or die("Invalid query: " . mysql_error());
n // 删除对导演的引用
$director = "UPDATE
`movie`
SET
`movie_director` = '0'
WHERE
`movie_director` = '*'.$GET['id'].*'
";
$result = mysql_query($director) 
or die("Invalid query: " . mysql_error());
```

# 第6 章

在前面的代码中，我们设置了 'movie' 表中任何可能持有对不幸的、即将被删除的人引用的字段。UPDATE 语句的工作方式非常简单：它将所有符合 WHERE 语句要求的记录中的指定字段设置为新值。

你可能会好奇，如果有人忘记了 WHERE 部分会发生什么。嗯，好奇心是一种良好的品质：这将更新表中的所有记录，这可能不是你在现实生活中想要做的事情。

一旦我们完成了打字，我们将删除以下内容：

```php
// 生成 SQL
$sql = "DELETE FROM
    *.$GET('type').*"
WHERE
    *.$GET('type')._id = '.$GET('id').*
LIMIT 1";
// 为了调试目的输出 SQL
echo "!-".$sql->"-";
$result = mysql_query($sql)
or die("Invalid query: " . $mysql_error());
```
