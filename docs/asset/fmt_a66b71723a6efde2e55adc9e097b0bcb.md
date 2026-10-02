
```
    print("Five golden rings<BR>");
    break;
  case 4:
    print("Four calling birds<BR>");
    break;
  case 3:
    print("Three French hens<BR>");
    break;
  case 2:
    print("Two turtledoves<BR>");
    break;
  case 1:
    print("Aridge in a pear tree<BR>");
    break;
  default:
    print("A partite in pear tree<BR>");
}
```

这对于`days` 2-5 会打印相应的行；对于那些之外的日子，它将打印`Aridge in pear tree`。虽然`switch`只接受单个参数，但没有理由参数不能是代码之前评估的表达式的值。

## 循环

恭喜！你刚刚跨越了脚本到真实编程的边界。我们到为止看到的分支结构很有用，但仅靠它们进行计算是有极限的。另一方面，在理论计算机科学中证实，任何带有测试加无限循环的语言都可以做到其他语言能做的几乎任何事情。例如，你可能并不真的想用 PHP 写一个编译器，但知道没有语言本身的限制会阻止你是非常好的。

## 固定循环与无限循环

固定循环执行次数的次数——你可以通过查看代码知道循环将执行多少次，语言保证其循环次数不会超过该次数。无限循环重复直到某个条件变为真（或假），而该条件依赖于循环内代码的操作。固定循环是可预测的，而无限循环可以随你的意愿变得复杂。

与某些语言不同，PHP 实际上并没有专门用于固定循环的构造——`while`、`do-while`和`for`都是无限构造——但我们将在本节看到，无限循环可以做到固定循环能做的任何事情。

![](img/70f9bfaf3d714f908e4cb0592b8eb9a6_134_0.png)

除了本中的循环构造外，PHP 还提供了遍历数组内容的函数，在第 9 章中涵盖。

## `while`

简单的 PHP 循环构造是`while`，它具有以下语法：

```
while (condition)
statement
```

`while`将条件表达式评估为布尔值——如果它为真，则执行`statement`并重新开始评估`condition`。如果条件为假，`while`循环终止。或者当然，只是`statement`是单个语句或它可能是一个大括号括起来的块。`while`循环的体可能一次都不执行，如下：

```
while (FALSE)
print("This will never print.<BR>");
```

或者可能会永远执行，如这段代码段所示：

```
while (TRUE)
print("All work and no play makes
Jack a dull boy.<BR>");
```

或者可能会以可预测的次数执行，如下：

```
$count = 1;
while ($count <= 10)
{
print("count is $count<BR>");
$count = $count + 1;
}
```

这将恰好打印 10 次。（更多有趣的示例，请参阅本章后部分的“循环示例”章节。）

## `do-while`

`do-while`结构与`while`相似，不同在于测试发生在循环的末尾。其语法如下：

```
do statement
while (expression);
```

语句会执行一次，然后评估表达式。如果表达式为真，则重复执行该语句，直到表达式变为假为止。`while`和`do-while`之间唯一的实际区别在于，后者至少会执行一次其语句。例如：

```php
do {
  $count = 45;
  print("count is $count<BR>");
  $count = $count + 1;
} while ($count <= 10);
```

打印单行内容：

```
count is 45
```

## `for`

最复杂的结构是`for`，它的语法如下：

```
for (initial-expression;
  termination-check;
  loop-end-expression)
statement
```

在执行`for`语句时，`initial-expression`只求值一次，通常用于初始化变量。然后求值`termination-check`——如果结果为假，则`for`语句将跳过执行。最后，执行`loop-end-expression`，循环重新开始进行`termination-check`。一如既往，我们说的语句指的是单个（分号分隔的）语句、大括号括的块或条件结构。

如果我们将前面的`for`循环重写为`while`循环，它看起来像这样：

```
initial-expression;
while (termination-check)
{
  statement
  loop-end-expression;
}
```

实际上，虽然`for`类型恰好包含一个初始化表达式、一个终止检查和一个循环结束表达式，但省略其中任何一个都是合法的。如果省略终止检查，则被视为始终为真，因此：

```php
for(;;)
statement
```

等同于：

```
while (TRUE)
statement
```

在每种子句中包含多个并用逗号分隔也是合法的。如果终止检查中的任何一个子句为真，则该终止检查被视为真；它是一个“或”测试。例如，以下语句：

```php
for ($x = 1, $y = 1, $z = 1; // 初始化表达式
$y < 10, $z < 10; // 终止检查
$x = $x + 1, $y = $y + 2, // 循环结束表达式
$z = $z + 3
print($x, $y, $z<BR>);
```

将会在浏览器中输出：

- 1. 1. 1
- 2. 3, 4
- 3. 5, 7

尽管`for`语法是所有循环结构中最复杂的，但它经常被用于边界循环，使用以下惯用写法：

```php
for ($count = 0; $count < $limit; $count = $count + 1
statement
```

## 循环示例

现在我们来看一些示例。

### 一个有界`for`循环

列表 6-1 显示了有界`for`循环的典型用法。列表 6-1 生成的页面见图 6-1。

列表 6-1：除法表

```php
<?php
$start_num = 1;
$end_num = 10;
?>
<HTML>
<HEAD>
<TITLE>A division table</TITLE>
</HEAD>
<BODY>
<H2>A division table</H2>
<TABLE ORDER="1">
<?php
print("<TR>");
print("<TH></TH>");
for ($count_1 = $start_num;
$count_1 <= $end_num;
$count_1++;
print("<TH>$count_1</TH>");
print("</TR>");
for ($count_1 = $start_num;
$count_1 <= $end_num;
$count_1++) {
    print("<TH>$count_1</TH>");
    for ($count_2 = $start_num;
$count_2 <= $end_num;
$count_2++) {
        $result = $count_1 / $count_2;
        printf("<TD>%.3f</TD>",
            $result); // 查看第 8 章
    }
}
print("</TR>");
</TABLE>
<body>
</html>
```

![](img/70f9af3d714f908e4cb0592b89a6_137.png)

### 除法表

|  | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 1.000 | 0.500 | 0.333 | 0.250 | 0.200 | 0.167 | 0.143 | 0.125 | 0.111 | 0.100 |
| 2 | 2.000 | 1.000 | 0.667 | 0.500 | 0.400 | 0.333 | 0.286 | 0.250 | 0.222 | 0.200 |
| 3 | 3.000 | 1.500 | 1.000 | 0.750 | 0.600 | 0.500 | 0.429 | 0.375 | 0.333 | 0.300 |
| 4 | 4.000 | 2.000 | 1.333 | 1.000 | 0.800 | 0.667 | 0.571 | 0.500 | 0.444 | 0.400 |
| 5 | 5.000 | 2.500 | 1.667 | 1.250 | 1.000 | 0.833 | 0.714 | 0.625 | 0.556 | 0.500 |
| 6 | 6.000 | 3.000 | 2.000 | 1.500 | 1.200 | 1.000 | 0.857 | 0.750 | 0.667 | 0.600 |
| 7 | 7.000 | 3.500 | 2.333 | 1.750 | 1.400 | 1.167 | 1.000 | 0.875 | 0.778 | 0.700 |
| 8 | 8.000 | 4.000 | 2.667 | 2.000 | 1.600 | 1.333 | 1.143 | 1.000 | 0.889 | 0.800 |
| 9 | 9.000 | 4.500 | 3.000 | 2.250 | 1.800 | 1.500 | 1.286 | 1.125 | 1.000 | 0.900 |
| 10 | 10.000 | 5.000 | 3.333 | 2.500 | 2.000 | 1.667 | 1.429 | 1.250 | 1.111 | 1.000 |

图-1：除法表

此代码的主体在一个`for`循环内部嵌套另一个，每个循环执行十次，生成了一个 10×10 的表格。外层循环的每次迭代打印一行，而内层迭代打印一个单元格。唯一新颖的在于我们打印数字的方式——我们使用了`printf()`（第 8 章介绍），它允许我们控制小数位数。

上面使用的`$variable_name++`特性是自增。它是`$variable_name + 1`的一种非常标准的简写。

### 无界`while`循环

现在让我们来看一个不明显的边界循环。列表 6-2 代码的唯一目的是近似 81 的平方根（使用牛顿迭代法）。近似从猜测值 1 开始，然后通过改进猜测值来“接近”9 的真实平方根。该近似的轨迹见图 6-2。

列表 6-2：近似平方根

```html
<HEAD>
<TITLE>Approximating a square root</TITLE>
</HEAD>
<BODY>
<H3>Approximating a square root</H3>
<?php
$target = 81;
$guess = 1.0;
$precision = 0.000001;
$guess_squared = $guess * $guess;
while (($guess_squared - $target) > $precision) or (
  ($guess_squared - $target < -$precision)) {
  print("Current guess: $guess is the square root of $target<BR>");
  $guess = ($guess + ($target / $guess)) / 2;
  $guess_squared = $guess * $guess;
}
print("$guess_squared = $guess_squared<BR>");
?>
</body>
```

现在，虽然它很好展示了一个可能的无界循环，但这个近似示例非常人工——首先是因为 PHP 已经有一个很好的平方根函数`sqrt()`，其次是因为数字 81 是硬编码在页面中的。我们无法使用此页面计算任何其他数字的平方根。

![](img/70f9af3d714f908e4cb0592b89a6_139.png)

### 近似平方根

```
Current guess: 1 is the square root of 81
Current guess: 4 is the square root of 81
Current guess: 21.487480780 is the square root of 81
Current guess: 5.213920667 is the square root of 81
Current guess: 7.714285714 is the square root of 81
Current guess: 9.000000000 is the square root of 81
Current guess: 9.000000000 is the square root of 81
```

图 6-2：近似平方根

退出循环结构标准方法是使用`break`和`continue`。例如，以下代码：

```php
for ($x = 1; $x < 10; $x++) {
    if ($x == 5) {
        break;
    }
    if ($x == 2) {
        continue;
    }
    print($x);
}
```

`break`语句立即终止最内循环。`continue`语句跳过当前迭代的剩余部分，进入循环的下一次迭代。

## 关于无限循环的说明

如果你用其他语言编写过程序，你可能有过无意中创建无限循环的经历（一种退出测试永远不会为真、因此永远不会返回循环结构）。当你意识到这种情况正在发生时，要的第一件事就是中断程序，否则它将“永远”运行下去并消耗大量的 CPU 时间。但如果这是一个 PHP 脚本呢？仅仅点击浏览器上的“停止”按钮就足够了吗？

事实证明，你的独立性取决于某些 PHP 设置——你可以设置 PHP 引擎以忽略来自浏览器的中断（例如点击“停止”的结果），并对脚本执行进行时间限制（这样“永远”将只会持续很短的时间）。PHP 的默认配置是忽略中断，但脚本时间限制为 30 秒——这个时间限制意味着你可以忽略自己已经启动的无限循环。

关于 PHP 的配置，请参阅第 5 章。

![](img/70f9bfaf3d714f908e4cb0592b8eb9a6_141_0.png)

## 替代性控制语法

PHP 提供了另一种方式来开始和结束`if`、`switch`、`for`和`while`结构的体。这相当于将包含块的起始大括号替换为冒号，并将结束括号替换为该结构的特殊结束语句（`endif`、`endswitch`、`endfor`和`endif`）。例如，`if`语法变为：

```
if (expression):
    statement1
    statement2
endif;
```

或者：

```
if (expression):
    statement1
    statement2
elif (expression2):
    statement3
else:
    statement4
endif;
```

注意，`else`和`elseif`的体也以冒号开始。相应的`while`语法为：

```
while (expression):
    statement
endwhile;
```

使用哪种语法取决于个人喜好。非标准语法在很大程度上是因为历史原因，以及为了让熟悉 PHP 早期版本的人感到方便。在本书的其余部分，我们将始终使用标准语法。

## 终止执行

有时你不得不放弃，PHP 提供了一个可以帮助你实现这一点的结构。`exit()`结构接受字符串或数字作为参数，打印该参数，然后终止脚本的执行。PHP 在调用`exit()`之前产生的所有内容都会像往一样发送到客户端浏览器，之后脚本中的任何内容都不会被解析——脚本执行立即停止。如果给定的参数是数字而不是字符串，该数字将作为脚本执行的返回值。由于`exit`是一个结构而不是函数，因此不带参数并省略参数也是合法的。

`die()`是`exit()`的别名，行为完全相同。（我们将使用`die()`，因为我们觉得这个名字更具启发性。）那么，`exit()`和`die()`的意义是什么？一种可能的用途是在当你的脚本确定没有有趣信息要发送时，截断页面输出，而无需将整个分支封装在结构中。然而，这种用法可能会使长脚本变得难以阅读和调试。

`die()`的更好用法是针对意外情况进行测试（如果这些条件为真会导致你的脚本崩溃），并在`die()`中带上说明性消息。如果你的预期是正确的，`die()`将永远不会被调用；如果你错了，你将获得你的错误信息，而不是可能晦涩的 PHP 错误。例如，考虑以下伪代码，它假设我们有函数来建立数据库连接，然后我们使用该数据库连接：

```
$connection = make_database_connection();
if (!$connection)
    die("No database connection!");
use_database_connection($connection);
```
