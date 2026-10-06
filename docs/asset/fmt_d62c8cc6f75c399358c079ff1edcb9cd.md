
```php
<?php
if ($_POST['type'] == "Movie:Movie" &&
    $_POST['MovieType'] == "*") {
    header("Location:form4.php");
}
$title = $_POST['Submit'].':'.$_POST['Name'];
$name = $_POST['Name'];
$name[0] = strtolower($name);

<html>
<head>
<TITLE><?php echo $title?></TITLE>
</head>
<body>
<form action="form4.php" method="post">
<input type="hidden" name="type" value="<?php echo $type[1]?>">
<input type="hidden" name="action" value="<?php echo $_POST['Submit']?>">
<table border="0" width="750" cellspacing="1" padding="3" bgcolor="#353535" align="center">
<tr>
<td bgcolor="#ffffff" width="30%">
电影名称
</td>
<td bgcolor="#ffffff" width="70%">
<?php echo $name?>
<input type="hidden" name="Name" value="<?php echo $name?>">
</td>
</tr>
<tr>
<td bgcolor="#ffffff">
电影类型
</td>
<td bgcolor="#ffffff">
<?php echo $_POST['MovieType']?><br />
<input type="hidden" name="type" value="<?php echo $_POST['MovieType']?>">
</td>
</tr>
<tr>
<td bgcolor="#ffffff">年份
</td>
<td bgcolor="#ffffff">
<SELECT name="MovieYear">
<option value="" SELECTED>选择年份...</option>
<?php
for ($Year=date('Y'); $Year>=1970; $Year--) {
?>
<option value="<?php echo $Year?>"><?php echo $Year?></option>
<?php
}
?>
</SELECT>
</td>
</tr>
<tr>
<td bgcolor="#ffffff">
描述
</td>
<td bgcolor="#ffffff">
<textarea name="Desc" rows="5" cols="60"><?php echo $_POST['Desc']?></textarea>
</td>
</tr>
<tr>
<td bgcolor="#ffffff" colspan="2" align="center">
<input type="SUBMIT" name="Submit" value="Add">
</td>
</tr>
</table>
</form>
</body>
</html>
```

5. 创建一个名为 `Add.php` 的文件，在其中添加此代码：

```php
<?php
if ($_POST['type'] == "Movie:Movie" &&
    $_POST['MovieType'] == "*") {
    echo "<?php echo $type[1]?> : <?php echo $_POST['Name']?>";
}
```

# 表单元素：让用户处理数据

那么，让我们回到工作正吧。这个东西到底是如何工作的呢？我们将按照下面的思路讨论你必须解译的元素。

## 骨架脚本 Skeleton Script

这里的骨架是 `form4.php` 脚本。它完全围绕着 `switch case` 结构展开。它始于一个用于调试显示的函数定义，该函数现在包含了 `$_GET` 全局数组的显示。

技巧之处在于，表单将使用 `POST` 方法，并通过 `$_POST` 数组传输其信息；实际的页面内容切换将通过传递给 `$_GET` 数组的查询字符串来实现。

数据构建的每一步都由 `$_GET['step']` 索引值引导。它包含了 URL 中 `?step=1` 部分传递的信息。

脚本的每个值都附带着一个特定的脚本。

## 默认响应

当你第一次调用且 `step` URL 参数未设置时会发生什么？从逻辑上讲，它会评估 `switch` 条件并发现它不匹配任何指定的 `case`，因此会执行默认行为：

```php
switch($_GET['step']) {
    default:
        require('startform.php');
        break;
}
```

`require()` 函数在解释时获取指定文件的内容并将其包含在脚本中。`require()` 函数与 `include()` 函数的区别在于，如果未找到文件，它会触发致命错误 fatal error 而不是警告 warning。在这种情况下，如果缺少表单将略微减少我们脚本的功能，因此我们希望在找不到文件时能有所知晓。

## 添加项目

在添加人员或电影时，你需要两个不同的表单，至少如果你认为数据库中演员和导演的类型是相同的数据的话。因此，你需要第二个分支，第一个分支通过 `switch step` 实现，来确定将显示哪个表单。

现在我们遇到了脚本的一个部分，其中有一个小技巧。列表项的值 list item value 被存储两个值而不是一个。技巧是使用一个分隔符，然后通过 `explode` 将值拆分为数组，并访问你需要的片段。`explode()` 函数取由分隔符分隔的每段文本，并将其作为新的数组元素插入。让我们仔细观察。

# 第 5 章

在这种情况下，我们有三种类型的项目，演员、导演和电影，每种都需要一个表单来创建。但我们已经决定，到目前为止，演员和导演表单持有相同的信息。我们不需要两个不同的表单，只需要一个。你通过在项目级别上方添加树形结构来处理这一点：人员 Person 或电影 Movie。在“人员”下，我们包含演员和导演级。整个重点在于能够使用新的层级名称来命名文件，这样包含就是自动的，你可以无需费太大精力添加新层级。

在 `startform.php` 中我们有

```html
<INPUT type="radio" name="type" value="Person:Actor">
Actor<br/>
```

你可以清楚地看到 `type` 元素的数值部分由两个不同的值组成，用分号分隔。

在 `form4.php` 中你有：

```php
$type = explode(":",$_POST['type']);
if ($_POST['Submit']=="Add") {
    require($_POST['Submit'].$type[0].'.php');
}
```

在这个脚本中，你使用 `$_POST['type']` 数组索引获取 `type` 元素的值，然后对其内容使用 `explode()` 函数。`explode()` 函数非常易用；它只需要一个指定分隔符的字符串和一个包含要拆分文本的字符串。

例如，我们有 "Person:Actor" 作为要拆分的值，并用冒号 `:` 作为分隔符。生成的 `$type` 变量将是一个数组，保存着在每个分号处切开的字符串片段。如果你用 `print_r` 格式表示它，你将得到：

```text
Array
(
  [0] => Person
  [1] => Actor
)
```

保存文件名包含的目标已经实现。我们有两个 `Add` 脚本，但只有一个名字模板：`AddPerson.php` 和 `AddMovie.php`。

```php
require($_POST['Submit'].$type[0].'.php');
```

这一行自动重新组合了我们的文件名。

# 表单元素：让用户处理数据

## 总结

你在这一章中学习了很多关于表单的知识。表单由字段组成。每个字段都有特定的目的并允许输入特定类型的数据。文本字段可以输入文本或数字数据。列表可以输入任何类型的数据，并有一组有限的可能值。当有多个选项可用时，列表是驱动用户输入的好方法。

PHP 脚本使用全局数组 `$_GET` 和 `$_POST` 处理表单，它们是 `$_QUERY` 的子数组。每个全局数组都有其用途，并有助于让你的脚本访问表单数据。始终记住保持表单简单。有些研究表明，超过 5 个项目的表单对用户来说往往太复杂了。可读性和布局是拥有可用系统的关键。

## 让用户编辑数据库

从数据库中检索数据在获取数据时很好。大多数数据库不会生成自己的内容，只有少数通过集成系统等方式获取数据。因此，我们必须向系统提供来自 PHP 的数据。我们选择的数据库是 MySQL，你可能已经猜到了，在书名里，对吧？你知道从表中获取数据的基本 SQL 语法；现在让我们看看等式的另一边。这一章涵盖了数据库编辑，包括：

- 添加条目，这非常简单；
- 删除条目，这并不简单，但需要考虑引用完整性；
- 修改表目，替换某些字段。

## 准备工作

在获取数据时，从数据库中检索数据一切良好。但你必须始终有一个中央管理界面，允许你对数据执行操作并轻松看到内容。这个脚本就是管理界面。它显示一切，并且你可以管理你所看到的一切。

它是如何工作的？它是如何做到的？正如在第 4 章中，我们连接到数据库并显示其内容一样，我们在这里做同样的事情。

## 尝试一下

在管理数据库时，你需要创建一个页面。按照以下步骤操作：

1. 创建一个名为 `chapter6` 的目录。

2. 创建 `index.php` 脚本并输入以下代码：

```php
<?php
$link = mysqli_connect('localhost', 'root', '');
or die("连接失败: " . mysqli_error());
?>
<html>
<head>
<TITLE>管理数据库</TITLE>
</head>
<body>
<table border="0" width="600" cellspacing="3" bgcolor="#353535" align="center">
<?php
$movies = "SELECT * FROM movie";
$result = mysqli_query($movies)
or die("查询失败: " . mysqli_error());
while ($row = mysqli_fetch_array($result, MYSQL_ASSOC)) {
<tr>
<td bgcolor="#ffffff" width="50%">
<?php echo $row['movie_name']?>
</td>
<td bgcolor="#ffffff" width="50%" align="right">
<a href="movie.php?action=edit&id=<?php echo $row['movie_id']?>">[编辑]</a>
<a href="delete.php?type=movie&id=<?php echo $row['movie_id']?>">[删除]</a>
</td>
</tr>
}
}
?>
</table>
</body>
</html>
```

3. 现在打开你的浏览器并访问 `http://localhost/chapter/6/index.php`，如图 6-1 所示。

注：由于原文未提供图 6-1，此处保留描述

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

- 1. 在 phpMyAdmin 中打开你的数据库，并输入图 6-2 所示的 SQL 代码，是的，这里有一个错误：

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

- 2. 出现以下消息，详情见图 6-3：

您的 SQL 语法中存在错误。请检查与您的 MySQL 服务器版本对应的手册，以获取第 5 行附近 '2003' 的正确语法。

- 3. 按照建议修复错误，通过行号操作非常简单并运行。phpMyAdmin 会显示执行的 SQL 并带你回到表格内容显示界面，如图 6-4 所示。

在 PHP 中执行任何 SQL 查询之前，你始终应该先在 phpMyAdmin 中测试你的 SQL 语句。这允许你将在其插入代码之前对其进行调试，并防止同时调试两种不同的语言。

# 第 6 章

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_190_0.png)

图 6-3

## 工作原理

当向表中表中插入记录时，如果你将主键字段设置为自动递增 auto increment，你就不需要插入 id。引擎会乐意为你处理这一点。这让你能够确保表中没有重复的键。

要获取刚刚插入的记录的自动递增 id，只需在调用 `mysql_query()` 函数后使用 PHP 的 `mysql_insert_id()` 函数即可。该函数在插入新记录时返回主键字段。

`mysql_insert_id` 函数的语法可以在 PHP 网站 `www.php.net/mysql_insert_id` 找到。

由于我们在多行中创建了 SQL 查询，因此我们可以使用以下错误消息中返回的行号来定位问题。

您的 SQL 语法中存在错误。请检查与您的 MySQL 服务器版本对应的手册，以获取第 5 行附近 '2003' 的正确语法。

## 允许用户编辑数据库

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_191_0.png)

这一行对应于我们 SQL 语句的值部分，如下：

' Bruce Almighty','1', '2003'

如果我们的 SQL 查询在同一行内，我们只会得到一条没用的“第 1 行错误”消息。在这里你可以看到，在该行中我们忘记在 movie_year 值中闭合引号。

现在你可以说我们省略了 'movie'.'movie_id' 字段。我们是故意这么做的，是的，我们确实如此。不指定主键值将迫使 MySQL 引擎自动确定递增值。得益于此，我们不需要知道键将会是什么。

## 在关系型数据库中插入记录

数据库通常包含多个表格。所有这些表都可以是完全独立的，就像使用你的汽车后备箱来存放东西，而不是开车它一样。

在不存在关系型数据库的旧系统中，每一行都包含所有信息。你的系统仅靠一个包含所有信息的表运行。你的电影表将存储关于演员、导演和电影类型的所有数据。假设某天你决定将某个电影类别从动作改为冒险，事物总在变化。你必须遍历所有记录来更改电影类型标签。

在现代 RDBMS 关系型数据库管理系统 中，情况不再是这样；你会创建一个 `movetype` 表来存储所有可能的电影类型的引用，并将电影链接到相关的电影类型。

要链接表，你将使用主键/外键。`movetype` 表的主键是每种电影类型的数字标识。例如，在我们的数据库中，id 1 喜剧。外键是 movie 表中对 `movetype` 主键的引用。

在下面的练习中，你将使用 PHP 和 SQL 在你的数据库中插入一部电影。这部电影属于

## 尝试插入已知类型的电影

这次，让我们来做一些复杂一点。你需要向系统添加一部电影，并指定现有的电影类型和导演。

- 1. 创建一个名为 `movie.php` 的新空文件并输入以下代码：
