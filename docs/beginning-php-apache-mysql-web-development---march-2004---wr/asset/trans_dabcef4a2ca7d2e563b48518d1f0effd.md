

# 第 6 章

| | | |
|---|---|---|
| 上天作戏 | [编辑] [删除] |
| 办公室空间 | [编辑] [删除] |
| 大峡谷 | [编辑] [删除] |
| Jim Carver | 人 [添加] [编辑] [删除] |
| Tom Shadrac | [编辑] [删除] |
| Lawrence Kaidan | [编辑] [删除] |
| Kevin Kline | [编辑] [删除] |
| Ron Livingston | [编辑] [删除] |
| Mike Judge | [编辑] [删除] |

图 6-1

## 使用 phpMyAdmin 插入简单记录

注意，在接下来的脚本中，我们将遵循一个关于 SQL 的简单规则：在将查询插入代码之前，始终先在 MySQL 中尝试运行。简单的原因是，一次只调试一种语言可能让你更明智。

## 尝试插入简单数据

现在请按照以下步骤插入一些数据：

- 1. 在 phpMyAdmin 中打开你的数据库，并输入图 6-2 所示的 SQL 代码（是的，这里有一个错误）：

```
INSERT INTO
`movie`
(`movie_name`, `movie_type`, `movie_year` )
VALUES
(`Bruce Almighty','1','2003` )
```

## 允许用户编辑数据库

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_189_0.png)

图 6-2

- 2. 出现以下消息（详情见图 6-3）：

您的 SQL 语法中存在错误。请检查与您的 MySQL 服务器版本对应的手册，以获取第 5 行附近 '2003' 的正确语法。

- 3. 按照建议修复错误（通过行号操作非常简单）并运行。phpMyAdmin 会显示执行的 SQL 并带你回到表格内容显示界面，如图 6-4 所示。

在 PHP 中执行任何 SQL 查询之前，你始终应该先在 phpMyAdmin 中测试你的 SQL 语句。这允许你将在其插入代码之前对其进行调试，并防止同时调试两种不同的语言。

# 第 6 章

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_190_0.png)

图 6-3

## 工作原理

当向表中表中插入记录时，如果你将主键字段设置为自动递增（auto increment），你就不需要插入 id。引擎会乐意为你处理这一点。这让你能够确保表中没有重复的键。

要获取刚刚插入的记录的自动递增 id，只需在调用 `mysql_query()` 函数后使用 PHP 的 `mysql_insert_id()` 函数即可。该函数在插入新记录时返回主键字段。

> `mysql_insert_id` 函数的语法可以在 PHP 网站 www.php.net/mysql_insert_id 找到。

由于我们在多行中创建了 SQL 查询，因此我们可以使用以下错误消息中返回的行号来定位问题。

> 您的 SQL 语法中存在错误。请检查与您的 MySQL 服务器版本对应的手册，以获取第 5 行附近 '2003' 的正确语法。

## 允许用户编辑数据库

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_191_0.png)

这一行对应于我们 SQL 语句的值部分，如下：

> ( 'Bruce Almighty','1', '2003' )

如果我们的 SQL 查询在同一行内，我们只会得到一条没用的“第 1 行错误”消息。在这里你可以看到，在该行中我们忘记在 movie_year 值中闭合引号。

现在你可以说我们省略了 'movie'.'movie_id' 字段。我们是故意这么做的（是的，我们确实如此）。不指定主键值将迫使 MySQL 引擎自动确定递增值。得益于此，我们不需要知道键将会是什么。

## 在关系型数据库中插入记录

数据库通常包含多个表格。所有这些表都可以是完全独立的，就像使用你的汽车后备箱来存放东西，而不是开车它一样。

在不存在关系型数据库的旧系统中，每一行都包含所有信息。你的系统仅靠一个包含所有信息的表运行。你的电影表将存储关于演员、导演和电影类型的所有数据。假设某天你决定将某个电影类别从动作改为冒险（事物总在变化）。你必须遍历所有记录来更改电影类型标签。

在现代 RDBMS（关系型数据库管理系统）中，情况不再是这样；你会创建一个 'movetype' 表来存储所有可能的电影类型的引用，并将电影链接到相关的电影类型。

要链接表，你将使用主键/外键。'movetype' 表的主键是每种电影类型的数字标识。例如，在我们的数据库中，id 1 喜剧。外键是 movie 表中对 'movetype' 主键的引用。

在下面的练习中，你将使用 PHP 和 SQL 在你的数据库中插入一部电影。这部电影属于

## 尝试插入已知类型的电影

这次，让我们来做一些复杂一点。你需要向系统添加一部电影，并指定现有的电影类型和导演。

- 1. 创建一个名为 movie.php 的新空文件并输入以下代码：

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

2. 保存文件并将其上传到服务器上新的 chapter6 目录。

3. 创建一个名为 commit.php 的新空文件并输入以下代码：

```
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

