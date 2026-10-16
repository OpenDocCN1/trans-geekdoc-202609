
PHP 提供了多个用于在 MySQL 数据库中存储和检索数据的函数。查询数据库时，我们会得到一个关联数组作为返回结果，其中包含整个结果集。这个结果集需要传递给一个函数（mysqli_fetch_array()），该函数以关联数组的形式返回记录集中下一行，使用字段名作为元素引用来表示该行包含的值。每次后续调用 mysqli_fetch_array() 都会返回下一行，直到记录集中不再有剩余行。当记录集中没有更多行时，会返回 NULL，这使你能够退出循环。清单 9.2 是一个 while 循环的示例。

## Listing 9.2.

```html
<html>
<head>
  <title>Fetching Multiple Rows</title>
</head>
<body>
<?php
  $dbc = mysqli_connect('localhost', 'testuser', 'testuser', 'northwind')
  or trigger_error('Error connecting to MySQL server.', E_USER_ERROR);

  $query = "SELECT ProductName, UnitPrice FROM Products";

  $result = mysqli_query($dbc, $query)
  or trigger_error('Error querying database.', E_USER_ERROR);
?>
<table border='1px solid;'>
  <tr><th>Product Name</th>
  <th>Unit Price</th></tr>
<?php
  while($row = mysqli_fetch_array($result))
  {
    echo '<tr><td>' . $row['ProductName'] . '</td><td>'
    . $row['UnitPrice'] . '</td></tr>';
  }
  mysqli_close($dbc);
?>
</table>
</body>
</html>
```

## 9. 循环

图 9.1 显示了使用 while 循环从数据库中获取的产品信息表。

> 我们将在后续章节中探讨创建和使用函数以及与数据库协作的内容。

do/while[1] 循环在你能保证至少进入一次循环时很有帮助。在 PHP 中，你很少能保证这一条件。因此它很少被使用。

### 退出和继续循环

有时，你可能希望提前退出循环，或者继续迭代循环但跳过当前迭代剩余部分的某些代码执行。PHP 为此提供了 break 和 continue 命令。

### break

如果你想退出循环，请在循环中使用 break 命令。清单 9.3 是一个示例，如果数组中的元素等于 finished，则退出 foreach 循环。

### Listing 9.3.

```php
<?php
$random_words = ['happy', 'sad', 'finished', 'anxious', 'ecstatic'];
foreach ($random_words as $word) {
    if ($word == 'finished') {
        break;
    }
    echo "$word<br/>";
}
```

以下是输出：

```
happy
sad
```

[1] do/while: http://php.net/control-structures.do.while

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_98_0.png)

### continue

如果你想跳过当前迭代的剩余部分并继续下一轮迭代，请在循环中使用 continue 命令。参见清单 9.4，其中给出了一个跳过循环中每第三次迭代的示例。

### Listing 9.4.

```php
<?php
$random_words = ['one', 'two', 'three', 'anxious', 'ecstatic'];

for ($i = 1; $i <= 9; $i++)
{
    if ($i % 3)
    {
        continue;
    }

    echo "$i<br/>";
}
```

此循环产生以下输出：

```
1
2
4
5
7
8
```

### 练习

为以下内容创建脚本 loops.php：

- 1. 编写一个循环，从一数到十并在一列中输出每个值。在第二列中，输出该数字的平方。
- 2. 使用 foreach 循环输出第 6 章 arrays.php 中的图书标题列表。

## 章节

## 10

## 函数

> “在水上行走和根据规范开发软件都很简单，如果两者都被冻结的话。”
> 
> – Edward V. Berard

## 10. 函数

编写代码并持续添加功能非常容易。问题是我们的程序代码变得过大且难以管理。常见的做法是将代码模块化为函数并将功能限制为特定任务。这样做使我们能够在整个程序中重用这些模块。函数还使我们能够传入参数并返回结果。

### 简单函数

最简单的函数不接受参数也不返回任何内容；它只是执行某些功能。假设你想要一个函数来输出你在网站的每个页面上显示的问候语“Welcome to my Website!” 它可能看起来像这样：

```
function outputGreetingToWebsite()
{
    echo "<h1>Welcome to my Website!</h1>";
}
```

在 PHP 中创建函数时，你总是使用 function 关键字开始。接下来，你需要为函数取一个好名字。由于函数是被调用来执行某事的，通常最好以动词开头命名函数。在本例中，我们希望向网站输出问候语。将函数命名得尽可能具体有助于代码的可读性和可维护性。因此 outputGreetingToWebsite 是一个好名字。虽然 PHP 标准中未明确规定，但我通常喜欢使用一种称为“驼峰命名法”的方式命名函数。如上例所示，我们使用小写字母开始函数的第一个单词，然后将每个后续单词与函数连接在一起时，将连接单词的首字母大写。接下来，函数在括号之间定义传递给函数的参数。在本例中，我们没有参数要传递，所以我们将只使用空括号。接下来，函数内的代码包含在两个大括号 ({}) 中。此外，每次遇到新的左大括号时，你都希望缩进代码。我通常使用四个空格作为缩进级别，并对行续行使用双倍缩进（八个空格）。

组织我们的函数也是一个好主意。稍后，当我谈到面向对象编程时，我们会将函数（称为方法）放入称为“类”的东西中。现在，让我们假设我们有多个用于向网站输出信息的函数，收集在一个名为 outputToWebsite.php 的单个 PHP 脚本中。

当我们想在代码的其他地方（例如在另一个 PHP 脚本中）调用或使用我们的函数时，我们需要做几件事。首先，我们需要确保包含定义函数所在的代码。我们使用 require_once() 语句来做到这一点，并将包含我们想要使用的函数的脚本名称放在引号内：

```
<?php
require_once('outputToWebsite.php');
```

接下来，我们调用函数。下面示例中，让我们调用它两次：

```
outputGreetingToWebsite();
outputGreetingToWebsite();
```

调用函数两次的输出如 图 10.1 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_103_0.png)

### 函数参数/参数

函数也可以接受参数。假设我们想要创建一个函数，将两个数字作为参数传递给函数。让我们将此函数命名为 addTwoNumbers。我们需要在括号之间用逗号分隔两个参数。这些变量是函数的参数，并且被视为作用域限定于函数的局部变量。同样，给这些参数命名时尽可能描述性也是一个好主意：

```
function addTwoNumbers($num1, $num2)
{
    $sum = $num1 + $num2;
    echo "$num1 + $num2 = $sum<br />";
}
```

当我们调用此函数时，我们需要在与函数中定义相同的顺序下向此函数传入两个参数：

```
addTwoNumbers(4, 5);
```

这导致输出：

```
4 + 5 = 9
```

## 10. 函数

这在传入变量时也适用：

```
$the_first_number = -2;
$the_second_number = 5;
addTwoNumbers($the_first_number, $the_second_number);
```

输出结果为：

```
-2 + 5 = 3
```

调用函数时，传入的值被视为函数的参数。然而，从函数的角度来看，这些值被视为参数。我不认为这点计算机科学知识会让你在混淆这两种观点时遇到麻烦。当你调用函数时，参数的值（无论是字面值还是变量值）都会被复制到函数的参数变量中。

### 从函数返回值

最后，我们可以编写函数使其向我们返回结果。在上述加两个数字的示例基础上，让我们修改此函数。不是回显函数的结果，我们可以返回结果并允许调用函数的代码自行决定如何处理结果。首先，让我们将此函数的名称改为 sum，因为这更准确地描述了函数的功能。我们需要对代码做的唯一修改是将 echo 语句替换为返回变量 $sum：

```
function sum($num1, $num2)
{
    $sum = $num1 + $num2;
    return $sum;
}
```

现在当我们调用此函数时，我们可以创建一个变量来保存调用结果，并将其设置为等于函数调用：

```
$first_num = 5;
$second_num = 7;

$sum_of_two_numbers = sum($first_num, $second_num);
echo "The result of adding $first_num and $second_num is $sum_of_two_numbers<br/>";
```
