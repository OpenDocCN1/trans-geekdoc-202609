
```php
<?php
session_start();
$_SESSION['username']=$_POST['user'];
$_SESSION['userpass']=$_POST['pass'];
$_SESSION['autouser']=0;

// 检查用户名和密码信息

if ($_SESSION['username']=='Joe' &&
  ($_SESSION['userpass']=='12345')) {
    $_SESSION['autouser']=1;
} else {
    echo "Sorry, but you don't have permission to view this
    page, loser!";
    exit();
}

?>
<HTML>
<HEAD>
<TITLE>Find my Movie!</TITLE>
</HEAD>
<BODY>
<?php include "header.php" ?>
<?php
$favmovie=urlencode("Life of Brian");
echo "<a href=\"http://localhost/movies.php?favmovie=$favmovie\">";
echo "Click here to see information about my movie!";
echo "<br>";

//删除这些行
echo "<a href=\"http://localhost/movies.php?movienum=5\">";
echo "Click here to see top 5 movies.";
echo "<br>";

// /被删除行结束
echo "<a href=\"http://localhost/moviesite.php\">";
echo "Click here to see my 10 movies.";
echo "<br>";

echo "<a href=\"http://localhost/moviesite.php?sorted=true\">";
echo "Click here to see my 10 movies, sorted alphabetically.";
echo "</a>";
?>
</BODY>
</html
```

现在让我们使用 `login.php` 文件进行登录（以 Joe 登录，密码为 12345）。

## 工作原理

你的屏幕应该看起来像图 2-17 和 2-18。

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_100.png)

图 2-17

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_101.png)

图 2-18

我们首先使用数组将电影列表放入变量 `$favmovies` 中。然后使用 `foreach` 结构在 `moviesite.php` 中单独列出它们。我们还添加了一个链接，通过 `$_REQUEST[sorted]` 允许用户显示排序后的列表。

## 如果你在这里

如果你有任何编程背景，你一定用过 `while-do` 函数。以防你从未听说过这个（也许你住在火星之类的），让我们对这个概念做个简要概述。`while` 仅仅告诉服务器，只要给定条件为“真”，就重复执行命令或代码块。

`while` 在代码块开始时检查条件，`do/while` 在代码块结束时检查条件，保证块至少执行一次。

以下是 `while` 和 `do/while` 命令的示例：

```php
$num = 1;
while ($num <= 5) {
  echo $num;
  echo "<br>";
}
```

这两个代码片段都打印了数字 1 到 5，每个数字占一行。

## 使用函数尝试

让我们允许用户告诉想看多少部电影，并像以前一样使用函数对列表进行编号。

对你的 `movie.php` 程序进行以下更改：

```php
<?php
session_start();
$_SESSION['username']=$_POST['user'];
$_SESSION['userpass']=$_POST['pass'];
$_SESSION['autouser']=0;

// 检查用户名和密码信息

if ($_SESSION['username']=='Joe' &&
  ($_SESSION['userpass']=='12345')) {
    $_SESSION['autouser']=1;
```

# 第2章

《终结者2》、《星球大战》、《第三类接触》，

《十六根蜡烛》、《高尔夫球场》；

```php
if (ISSET($_REQUEST['favmovie'])) {
    echo "Welcome to our site, ";
    echo $_SESSION['username'];
    echo "<br>";
    echo "My favorite movie is ";
    echo $_REQUEST['favmovie'];
    echo "<br>";
    $movierate=5;
    echo "My rating for this movie is: ";
    echo $movierate;
}
else {
    echo "My top " . $_POST['num'] . " movies are:<br>";

    if (ISSET($_REQUEST['sorted'])) {
        sort($favmovies);
    }

    // list the movies
    $numlist = 1;
    while ($numlist <= $_POST['num']) {
        echo $numlist;
        echo ". ";
        echo pos($favmovies);
        next($favmovies);
        echo "<br\n>";
        $numlist = $numlist + 1;
    }

    // delete these lines
    foreach ($favmovies as $currentvalue) {
        echo $currentvalue;
        echo "<br\n>";
    }
    // end of deleted lines
}
?>

</</body>>
</html>
```

现在，让我们玩玩新的 `movie.php` 和 `movies.php` 文件吧。

## 工作原理

你的代码应该根据你作为用户选择查看的电影数量，以及是否希望按字母顺序排列，来显示顶部电影列表。

# 创建 PHP 页面

你会在代码中注意到几点：

- 我们对普通的 `echo` 语句添加了一个小技巧：使用句点来拼接语句，如下：

`echo "My top " . $_POST["num"] . " movies are:<br>";`

这种方式可以将语句在几乎无法察觉的情况下拆分到引号之内和引号之外。

- 我们将 `numlist` 设置为 1，这将跟踪我们当前进行到第几个数字。

我们正在使用变量 `$_POST["num"]` 来限制列出的电影数量；这是来自 `movie.php` 表单的用户输入。

`pos($fmovies)` 函数对你来说也是一个新函数。该函数返回数组“指针”所在的位置（从开始处）。我们 `echo` 了它是因为我们想看到当前的值。

`next($fmovies)` 是另一个新的数组函数，它将指针移动到行中的下一个值。这为下一次 `while` 语句的迭代做好了准备。

现在看，这并不难吧？我们现在真正进入状态了！

## PHP 的替代语法

作为一名程序员，当你发现有快速、更简单的方法来实现某个功能时，总是非常棒的。我们为你已经熟悉的任务包含了一些实用的快捷方式或替代语法。

# `<?php` 和 `?>` 标签的替代方案

你可以用其他方式在 HTML 文档中标记 PHP 代码：

## `echo` 命令的替代方案

你已经领略了 `print_r()`，但你也可以使用 `print()` 在页面中显示文本或变量值。`echo()` 和 `print()` 之间的区别在于，使用 `print()` 时，在打印命令执行成功或失败后还会返回一个 1 或 0 的值。换句话说，你可以使用 `print()` 命令来判断某些内容是否没有打印，而 `echo()` 只管执行，而不会让你知道它是否正常工作。出于所有其他目的考虑，两者是等等的。

# 第2章

## 逻辑运算符的替代方案

你可能记得 `and` 和 `or` 是我们在比较两个值时使用的显而易见的逻辑运算符，但还有其他方式来表达这些运算符：

- `&&` 可以替代 `and`，唯一的区别是在数学函数执行期间运算符求值的顺序。

- `||` 可以替代 `or`，唯一的区别是在数学函数执行期间运算符求值的顺序。

## 双引号的替代方案：使用 heredoc

除了使用双引号来包围一个值外，你还可以使用 heredoc 语法：

```php
$value = <<<ABC
This is the text that will be included in the value variable.
ABC;
```

如果你内部包含双引号和单引号，这种方法特别有用：

```php
$value = <<<ABC
This is the text that will be included in the value variable.
ABC;
```

如果你内部包含双引号和单引号，这种方法特别有用：

## 递增的替代方案

你可以通过两种方式增加值：

```php
$value = $value + 1
```

或者

```php
$value++
```

## 总结

虽然我们在这一章涵盖了许多主题，但我们的目标是提供足够的知识，让你的网站真正“动态”起来，并向用户展示真实数据。

# 第3 章

MySQL 命令可以通过命令行提示符执行（正如你在第 1 章安装并授予用户权限时所的那样），也可以通过 PHP 执行。在本书我们将主要使用 PHP 来发送命令，并很快对此进行详细讨论。

## MySQL 结构

由于 MySQL 是关系型数据库管理系统，它允许你将信息分为表或“相关信息区域”。在非关系数据库中，所有信息都存储在一个大区域中，这使得存储和提取你想要的数据变得更加困难和繁琐。对于 MySQL，每张表可以包含单独的字段，每个字段代表部分信息。例如，一个字段可以包含客户的名字，另一个字段可以包含他的姓。字段可以持有不同类型的数据，如文本、日期等。

你根据想要存储在表中的信息类型创建数据库表。然后，MySQL 的各个“区域”或表通过某些共同公约数连接起来，其中公共字段的值是相同的。

为了说明这一点，请想象一张包含客户姓名、地址和 ID 号的表，以及另一个包含该客户 ID 号和其下过的订单的表。公共字段是客户的 ID 号，两个表中存储的信息将通过该数字相等的字段连接在一起。这让你能够一次性看到与该客户相关的所有信息。

让我们来看看如何定制数据库表以适应你的需求。

## 字段类型

当你创建表时，需要告诉 MySQL 每个字段将将存储什么类型的信息。下表列出了不同类型的字段及一些示例。

| MySQL 字段类型 | 描述 | 示例 |
| :--- | :--- | :--- |
| char(length) | 此字段可以包含任何字符，但字段具有固定长度。 | 客户的州份字段始终有两个字符。 |
| varchar(length) | 此字段可以包含任何字符，且数据长度可以在 1 到 255 个字符之间变化。字段的最大长度由括号中的表示。 | 客户地址字段将包含长度不一的字母和数字。 |
| int(length) | 范围从 -2147483648 到 +2147483647 的数值整数，但可以通过长度参数进行限制。长度参数限制的是可以显示的字符数，而不是值。可以对此字段中的数据执行数学函数。 | 现有产品数量。 |

## 在 PHP 中使用 MySQL

| MySQL 字段类型 | 描述 | 示例 |
| :--- | :--- | :--- |
| int(length) unsigned | 存储正整数（和零）直到 4294967295 的数值字段。长度参数限制了可以显示的字符数。可以对此字段中的数据执行数学函数。 | 客户 ID（如果完全是数字）。 |
| text | 此字段可以包含任何字符，数据最大尺寸为 65536 个字符。 | 字段允许存储更长的文本，而不将字段限制为 255 个字符。 |
| decimal(length, dec) | 可以存储小数的数值字段。长度参数限制了显示的字符数以及可以存储的 dec 小数位数。例如，一个存储高达 999.99 的价格字段将定义为 decimal(6,2)。 | 价格 |
| enum("option1","option2",...) | 仅允许在此字段中存储某些值，如“true”和“false”或列表。允许 65535 种不同的选项。 | 用户的性别字段将值为“male”或“female”。 |
| date | 以 yyyy-mm-dd 格式存储日期。 | 订单日期、生日、注册日期。 |
| time | 以 hh:mm:ss 格式存储时间。 | 新闻文章添加到网站的时间。 |
| datetime | 多用途字段，以 yyyy-mm-dd hh:mm:ss 格式存储日期和时间。 | 用户访问访问网页的日期和时间。 |

虽然前面的字段类型应该足以大多数需求，但我们在下表中列出了一些可能较少使用的类型。

| MySQL 字段类型 | 描述 |
| :--- | :--- |
| tinyint(length) | 存储从 -128 到 127 整数的数值字段。（添加 unsigned 参数允许存储 0 到 255）。 |
| smallint(length) | 存储从 -32768 到 32767 整数的数值字段。（添加 unsigned 参数允许存储 0 到 65535）。 |
| mediumint(length) | 存储从 -8388608 到 8388607 整数的数值字段。（添加 unsigned 参数允许存储 0 到 16777215）。 |
| MySQL 字段类型 | 描述 |
| :--- | :--- |
| bigint(length) | 存储从 -9223372036854775808 到 9223372036854775807 整数的数值字段。（添加 unsigned 参数允许存储 0 到 1844674407390751615。） |
| tinytext | 允许存储最多 255 个字符。 |
| mediumtext | 允许存储最多 16777215 个字符。 |
| longterm | 允许存储最多 4294967295 个字符。 |
| blob | 文本字段，但在排序和比较时区分大小。存储最多 65535 个字符。 |
| tinyblob | 等于 tinytext 字段，但在排序和比较时区分大小。 |
| mediumblob | 等于 mediumtext 字段，但在排序和比较时区分大小。 |
| longblob | 等于 longterm 字段，但在排序和比较时区分大小。 |
| year(length) | 以四位格式存储年份（默认）。可以通过指定长度参数来指定两位年份格式。 |

你可能不信，MySQL 还支持更多数据类型；这些类型的完整列表可以在附录 D 中找到。

## 选择正确字段类型的检查清单

虽然你现在还没有从头创建数据库，但了解如何确定最适合你需求的字段类型是重要的。

# 第3 章

你这辈子可能买过很多东西。现在你发现必须退掉 1984 年买的拉链降伞裤，但不幸的是你需要收据。于是你开始在堆积如山的纸张中翻找。噢，五天后，你在房间里最后一堆纸中找到了收据。在埋咒自己本可以更有条理之后，你意识到你至少可以按购买年份对它们进行分组，然后你开始真正将它们按类别分组，例如服装、8声道磁带等。下当你需要退回多年前购买的东西时，你至少可以跳到正确的堆栈，甚至知道要找什么。从某种意义上说，对吧？

现在想象一下，你的数据杂乱无章地存储在家里，每当你想搜索某些东西时，它都会从第一条记录开始，向下扫描行直到找到你要找的内容。如果你有 10,000 行，而你要找的恰好在末尾呢？搬好椅子，脱掉鞋，因为事实可能如此。

通过使用内部文件系统，MySQL 可以更快地跳转到数据的大致位置。这是通过使用索引（也称为键）实现的。在我们之前的“收据”示例中，你决定按年份对收据进行分组，所以如果你的收据存储在数据库中，索引条目就是“year”（年份）。你还决定按类别对收据进一步分组，另一个索引就是“category”（类别）。

MySQL 要求每个表至少有一个索引，这样它才有据可依。通常情况下，你会使用主键，即保持数据稳定的唯一标识符。此字段必须是“非空”（null）且“唯一”（unique）的；例如，你可以有一个客户 ID 来区分不同的客户。（你完全可能有两个“John Smith”，所以你需要轻松地辨别他们。）在你的“收据”表中，你创建了一个主键并为每张收据分配了它们自己的识别码，以便你可以区分它们。

MySQL 还提供了一个功能，允许字段中的值自动加 1。这个 `auto_increment` 参数对于确保你的主键填充的是唯一数字非常有用。

## 唯一 (Unique)

我们都喜欢认为自己是独特的，但当开启此参数时，MySQL 会确保特定字段绝对不存在任何重复项。通常，这用于表的主键，但也可以用于任何字段。

例如，如果你举办一场比赛，只有每个你访问过的州的第一个人被允许加入你的网站？你可以使用 `unique` 参数；那么任何尝试从已经有人占了位子的州向你的数据库插入数据的人都会收到错误消息。

## 自动递增 (Auto Increment)

假设你有一个字段，每当添加新记录时它都会自动加 1。在分配 ID 数字时，这是一个非常有用的函数。你不需要担心上一个 ID 号是多少；字段会自动为你跟踪。
