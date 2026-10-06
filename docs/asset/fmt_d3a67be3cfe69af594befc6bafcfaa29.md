
```html
<html>
<head>
<title>这个月有多少天？</title>
</head>
<body>
<?php
$month=date("n");
if ($month==1) echo '31';
if ($month==2) echo '28 (unless it's a leap year);
if ($month==3) echo '31';
if ($month==4) echo '30';
if ($month==5) echo '31';
if ($month==6) echo '30';
if ($month==7) echo '31';
if ($month==8) echo '31';
if ($month==9) echo '30';
if ($month==10) echo '31';
if ($month==11) echo '30';
if ($month==12) echo '31';
?>
</body>
</html>
```

- 2. 将此文件保存为 `date.php` 并在浏览器中打开。

结果应该显示当前月份的天数。

## 工作原理

我们通过调用 PHP 的许多内置日期函数之一来获取 `$month` 的值；`date("n")` 返回一个等于服务器设置的月份数值的值，例如 1 月为1，2 月为2，以此类推。（我们将在附录 C 中详细讨论 `date()`。）

然后我们对 `$month` 的每个可能值测试 `if` 语句，直到得到正确答案。如果第一个语句为假，程序会立即跳转到下一行并执行它。当遇到正确的月份时，它会执行该行剩余的语句，然后跳转到下一行继续执行。它在遇到真语句后不会停止，而是像什么都没发生一样继续运行。

# 创建 PHP 页面

## 结合使用 if 和 else

在某些情况下，单独使用 `if` 是没问题的，但在其他时候，`if/else` 组合更为合适。例如，假设你想在网站上显示某条消息，但希望在十二月显示特定的假期信息？或者假设你的影评网站想为那些没看过电影的人显示影评的简短版本？正是在这些“要……要么……”的情况下，你需要祭出强大的 `if/else` 组合。

## 使用 if 和 else 进行尝试

让我们继续沿日期主题，告诉用户当前年份是否为闰年。

按照以下步骤完成此操作：

- 1. 打开你的文本编辑器并输入以下代码：

```html
<head>
<title>是闰年吗？</title>
</head>
<body>
<?php
$leapyear=date('L');
if ($leapyear==1) echo "Hooray! It's a leap year";
else echo "Aww, sorry, mate. No leap year this year.";
?>
</body>
</html>
```

- 2. 将此文件保存为 `leapyear.php` 并在浏览器中打开。

你现在应该能根据当前年份是否为闰年看到语句。

## 工作原理

当程序评估 `if` 语句时，如果假，像上一个例子一样跳转到下一行代码。当程序读取该语句的 `else` 部分时，它会执行并移动到下一行。这部分基本上与单独使用 `if` 时相同。然而，如果语句为真，则执行该行的剩余部分，程序跳转到下一行。看到 `else` 语句时，它会跳过并继续执行程序。

如果你删掉 `else` 单词并保留语句的其他部分，那么“Aww, sorry, mate” 消息每次都会出现，这是我们不希望发生的。

## 使用 Includes 编写高效代码

你是否厌倦了反复输入相同的内容？PHP 的创建者们为沮丧的开发者们赐予了一个名为“includes”包含的小型省时设备，它让你免于反复不断地输入经常使用的文本。

# 第2章

## Includes

`include` 可以将 PHP 文件嵌入到其他 PHP 文件中。想象你想在网站的每个页面都输入相同的信息。也许是你公司的名称和地址，或者可能是今天的日期。如果你从零开始编写网站的每个页面，由于以下原因，效率并不高：

- 你在一遍又一遍地输入相同的信息，这永远不是好事。
- 如果发生更新或更改，你必须对网站的每一个页面进行修改。这同样是冗余且耗时的，并增加了人为错误的可能性。

解决这个问题的办法是使用 `include`。可以使用任何扩展名，但有时被称为 `.inc` 文件。如果你正在添加敏感信息，例如作为密码的服务器变量，建议将这些保存在 `.php` 文件中，这样它们永远不会被任何人访问，因为信息在发送到浏览器之前就会被解析。一个“include”在解析时被包含在另一个文件中，最终输出会被发送到浏览器。你可以在任何其他文件中添加 `include`，而且不需要每次都插入。

## 尝试添加欢迎消息

让我们看看影评网站的每个页面都显示欢迎消息以及可能的今天的日期。我们想创建一个包含这些信息的文件，请按照以下步骤操作：

- 1. 打开你的文本编辑器并输入内容：

```
<div align="center"><FONT SIZE="4">Welcome to my movie review site!</font>
<br>
<?php
echo "Today is ";necho date("F d");
echo ", ";necho date("Y");
?>
</div>
```

- 2. 将此文件保存为 `header.php`。

- 3. 为了在现有的三个网站文件中包含此文件，在 `login.php`、`moviel.php` 和 `moviesite.php` 的 HTML `<body>` 部分开头添加以下行：

<?php include "header.php" ?>

- 4. 保存你的文件。

让我们再次查看这些文件。如果你打开 `login.php`，你应该看到图 2-12 所示的内容。

## 创建 PHP 页面

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_89_0.png)

图 2-12

## 工作原理

当 PHP 遇到脚本中的 `include` 行时，它会停止当前程序的运行，并立即跳转到它被要求包含的文件。服务器解析该第二个文件，并将结果带回原始文件，然后从之前停止的地方继续解析。

假设我们决定并不希望在日期中显示末尾的零。幸运的是，PHP 在格式化日期函数方面提供了一个解决方案。对你的 `header.php` 文件进行以下修改并观察发生的变化：

```php
<div align="center"><FONT SIZE="4">Welcome to my movie review site!</font>
<br>
<?php

echo "Today is ";
echo date("F j");
echo " ";
echo date("Y"); 
</div>
?>
```

你的问题解决了，而且是一性解决了你网站中所有页面的问题。

## 使用函数编写高效代码

通过 `include`，使用函数可以让你的代码以及你的打字工作更高效且更于调试。

函数是代码块，可以从程序的任何地方调用。它们让你能够执行代码行，而不需要在每次使用它们时都重新思考。函数可以帮助设置或更新变量，并且可以嵌套。你还可以设置一个函数，仅在满足特定标准时才执行。

函数本身就是微型程序。除非你通过一个名为“global”的门让其他变量访问函数，否则它们对周围的任何变量一无不知。我们使用 `global $varname` 命令使变量的值对函数可见。这不适用于通过任何变量传递的任何默认为全局的变量，例如 `$_POST`、`$_GET` 等。

你的函数可以位于程序的任何位置，并可以从程序的任何地方调用。这是相对于 PHP3 的变化。因此，你可以将所有常用的函数列在程序的顶部，以便于后续调试。更好的是，你可以将所有函数放在一个文件中并在程序中包含它们。我们开始行动起来了！

PHP 提供了一套全面的内置函数，可以在附录 C 中找到，但有时你需要创建自己的自定义函数。

## 尝试使用函数

让我们通过以下步骤查看函数的实际运行：

- 1. 打开你的 `movie.php` 页面并按加粗文本所示进行修改：

```php
<TITLE>Find my Favorite Movie!</TITLE>
<BODY>
<?php include "header.php"; ?>
<?php
$myfavmovie=urlencode("Life of Brian");
echo "<a href=\"http://localhost/movies.php?favmovie=$myfavmovie\">";
echo "Click here to see information about my favorite movie! ";
echo "</a>";
echo "<br>";
echo "<a href=\"http://localhost/movies.php?movienum=5\">";
echo "click here to see my top 5 movies.";
echo "</a>";
echo "<br>";
?>
</BODY>
</HTML
```

- 2. 现在按照所示修改 `moviesite.php`：

```php
<?php
session_start();
// 检查用户是否已有效密码登录
if ($_SESSION['user']!=1) {
    echo "Sorry, you don't have permission to view this
    page, you loser!";
    exit();
}
?>
<HTML>
<HEAD>
<TITLE>My Movie Site - <?php echo $_REQUEST['favmovie'] ?></TITLE>
</HEAD>
<BODY>
<?php include "header.php"; ?>
<?php
function listmovies_1()
{
echo "1. Life of Brian<br>";
echo "2. Stripes Space<br>";
echo "3. Office Space<br>";
echo "4. The Holy Grail<br>";
echo "5. Matrix<br>";
}

function listmovies_2()
{
echo "6. Terminator<br>";
echo "7. Star Wars<br>";
echo "8. Encounters of the Third Kind<br>";
echo "9. Sixteen Candles<br>";
}

if (isset($_REQUEST['favmovie'])) {
    echo "Welcome, " . $_REQUEST['favmovie'] . "!<br>";
    echo "Your favorite movie is: " . $_REQUEST['favmovie'] . "<br>";
} else {
    echo "Please select a movie.<br>";
}
?>
</BODY>
</HTML>
```

## 第 2 章

| 功能 | 说明 |
| :--- | :--- |
| asort (array) | 按值降序对数组排序，并保持键/值关系 |
| asort (array) | 按值升序对数组排序，并保持键/值关系 |
| rsort (array) | 按值降序对数组排序 |
| sort (array) | 按值升序对数组排序 |

## 尝试排序数组

在继续之前，让我们对数组排序进行一个快速测试，这样你就可以看到数组在排序时的行为。在你的文本编辑器中输入以下程序，并将其命名为 sorting.php。

```php
<?php
$flavor[] = "blue raspberry";
$flavor[] = "root bear";
$flavor[] = "pineapple";

sort($flavor);
print_r($flavor);
?>
```

## 工作原理

你注意到前面的代码中有什么奇怪的处吗？是的，我们引入了一个新函数：`print_r`。它仅仅是打印变量的信息，以便人们阅读。它经常被用于检查数组的值，特别是。因此，输出看起来就像图 2-16 所示。

你可以看到 `sort()` 函数已经完成了它的职责，并将值按字母顺序升序排列。你还可以看到分配给每个值的不可见键，在本例中，这些键被重新分配了。

## foreach 结构

存在一个 `foreach` 命令，它可以对数组中的每个值应用一组语句。一个贴切的名字，对吧？然而，它只作用于数组，如果你尝试将它用于其他类型的变量，它会给你抛出一个巨大的错误。

`foreach` 命令的语法如下：

```php
<?php
$flavor[] = "blue raspberry";
$flavor[] = "root bear";
$flavor[] = "pineapple";
echo "My favorite flavors are:<br>";
foreach($flavor as $currentvalue) {
  // 只要 $currentvalue 中有值，这些行就会执行
  echo $currentvalue . "<br>\n";
}
?>
```

## 创建 PHP 页面

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_97_0.png)

图 2-16

这将产生每个口味在数组中出现的顺序列表。

## 尝试添加数组

让我们看看当我们将数组添加到 moviesite.php 文件时会发生什么。让我们也对它们进行排序并使用 `foreach` 结构。更改已加粗显示：

```<?php
<?php
session_start();
// 检查用户是否已有效密码登录
if ($_SESSION['authuser']!=1) {
    echo "Sorry, you don't have permission to view this
    page, you loser!";
    exit();
}

?>
<HTML>
<HEAD>
<TITLE>My Movie Site - <?php echo $_REQUEST['favmovie'] ?></TITLE>
</HEAD>
<BODY>
<?php include "header.php"; ?>
<?php
$favmovies = array("Life of Brian","Stripes","Office Space","The Holy Grail",
"Matrix","Terminator 2","Star Wars","Close Encounters of the Third Kind",
"Sixteen Candles","Caddyshack");

// /删除这些行：
function listmovies_1()
{
    echo "1. Life of Brian<br>";
    echo "2. Stripes<br>";
    echo "3. Office Space<br>";
    echo "4. The Holy Grail<br>";
    echo "5. Matrix<br>";
}

function listmovies_2()
{
    echo "6. Terminator 2<br>";
    echo "7. Star Wars<br>";
    echo "8. Close Encounters of the Third Kind<br>";
    echo "9. Sixteen Candles<br>";
    echo "10. Caddyshack<br>";
}

// /被删除行结束

if (ISSET($_REQUEST['favmovie'])) {
    echo "Welcome to our site, ";
    echo $_SESSION['username'];
    echo "<br>";
    echo "My favorite movie is: ";
    echo $_REQUEST['favmovie'];
    echo "<br>";
    $movierate=5;
    echo "My movie rating for this movie is: ";
    echo $movierate;
} else {
    echo "My top 10 movies are:<br>";

    if (ISSET($_REQUEST['sorted'])) {
        sort($favmovies);
    }

    // /删除这些行
    echo $_REQUEST['movienum'];
    echo " movies are: ";
    echo "<br>";
}

listmovies_1();
if ($_REQUEST['movienum'] == 10) listmovies_2();

// /被删除行结束
foreach ($favmovies as $currentvalue) {
    echo $currentvalue;
    echo "<br>";
}
?>
</BODY>
</html>
```

让我们按照所示修改 movie.php：
