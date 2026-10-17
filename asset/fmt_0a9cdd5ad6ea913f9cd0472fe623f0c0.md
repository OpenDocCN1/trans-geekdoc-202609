
```html
<!DOCTYPE html PUBLIC "//W3C//DTD HTML 1.0 Strict//EN"
"http://www.w3.org/TR/html/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml-lang="en" lang="en">
<head>
<title>Sorting words in a block of length</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body
<h1>Sorting words in a block of length by</h1>
<?php
$myText = <<<END_TEXT
But think not that famous town has only harpooneers, cannibals, and bumpkins to show their visitors. Not at all, Still New Bedford is a queer place. Had it not been for us whalemen, that tract of land this day perhaps have been in howling condition as the coast of Labrador.
END_TEXT

echo "<h2>Text:</h2>";
echo "<div style=\"width:30em;\">$myText</div>";

$myText = preg_replace('/[\/]/', "", $myText);
$words = array_unique(preg_split('/[\n\r]+/', $myText));
sort($words, create_function($a, $b) {
    return strlen($a) - strlen($b);
}));

foreach ($words as $word) {
    echo "$word<br/>";
}
?>
</body>
</html>
```

# 第二部分：学习语言

最后，脚本会在另一个固定宽 `div` 元素中显示排序后的单词列表。

顺便说一下，在这种情况下，你不必使用匿名函数。之前的代码可以写成：

```php
function sortByLength( $a, $b ) {
  return strlen($a) - strlen($b);
}

usort( $words, "sortByLength" );
```

但正如你所看到的，匿名函数要简洁得多。

## 使用引用

你已经学习了如何以参数的形式向函数传递信息，以及使用 `return` 语句从函数向其调用代码返回信息。当你执行这些操作之一时，PHP 实际上是在函数和外部之间传递信息的拷贝；这被称为按值传递和返回。

在大多数情况下，这不是问题，但有时你希望函数作用于原始信息而不是拷贝。考虑以下示例：

```php
function resetCounter( &$c ) {
  $c = 0;
}

$counter = 0;
$counter++;
$counter++;
echo "$counter"; // 显示 "3"
resetCounter($counter);
echo "$counter"; // 显示 "3"
```

这段代码定义了一个函数 `resetCounter()`，它将它的参数重置为零。初始化了一个 `$counter` 变量并将其自增三次。如你预期的那样，此时 `$counter` 的值为 3。然而，正如第二个 `echo` 所示，`$counter` 并没有被函数重置，因为 `resetCounter` 内部的参数 `$c` 只持有信息的拷贝。

幸运的是，PHP 提供了一种名为“引用”的机制，你可以利用它来解决问题。引用就像是你变量的快捷方式或别名。当你对变量创建引用时，你现在有两种方法来读取或更改内容：你可以使用变量名，也可以使用引用。这里有一个创建引用的简单示例：

```php
$myVar = 23;
$myRef = &$myVar;
$myRef++;
echo "$myRef"; // 显示 "24"
echo "$myVar"; // 显示 "24"
```

# 第7章：函数

首先，初始化新变量 `$myVar` 值为 23。接下来，创建 `$myVar` 的引用，并将该引用存储在变量 `$myRef` 中。注意等号符号被 `&` 符号修饰了；这创建了引用。下一行代码将 `$myRef` 的值加1。因为 `$myRef` 指向与 `$myVar` 相同的数据，正如两个 `echo` 语句所示，`$myRef` 和 `$myVar` 都包含值 24。

现在你已经什么是引用以及如何创建引用，是时候看看如何将引用传递进出函数中了。

# 向你自己的函数传递引用

通过将变量的引用作为参数传递参数而不是变量本身，你是按引用传递参数而不是按值传递。这意味着函数可以修改原始值而不是拷贝。要让函数接受引用而不是按值的参数，请在函数内部的参数名称前加上取地址符号 `&`：

```php
function myFunction(&$aReference) {
    // (对 $aReference 进行操作)
}
```

现在，当一个变量传递给 `myFunction()` 时，PHP 实际上传递的是该变量的引用，以便 `myFunction()` 能够直接处理变量的内容，而不是拷贝。既然你已经知道了，你可以通过使用引用来修复之前的计数器示例：

```php
function resetCounter(&$c) {
    $c = 0;
}

$counter = 0;
$counter++;
$counter++;
echo "$counter"; // 显示 "3"
resetCounter($counter);
echo "$counter"; // 显示 "0"
```

脚本中唯一的变化在第一行：

```php
function resetCounter(&$c) {
```

在 `$c` 之前加上 `&` 使 `$c` 参数成为所传递的参数（在本例中为 `$counter`）的引用。现在，当函数将 `$c` 设置为零时，它会改变 `$counter` 的值为零，正如 `echo` 语句所示。

许多 PHP 内置函数都以这种方式接受引用。例如，你在上一章中遇到的 PHP 的 `sort()` 函数，它会改变传递给它的数组，对其元素进行顺序排序。数组是按引用传递而不是按值传递的，这样函数就可以更改数组本身，而不是它的拷贝。

# 第二部分：学习语言

## 从你自己的函数返回引用

除了通过函数传递变量外，你还可以让函数返回引用而不是值。要做到这一点，在函数定义中，在函数名前前加上 `&` 来返回一个变量。然后，当你将该变量的引用传回调用代码时，而不是变量的值：

```php
function &Func() {
    // (进行操作)
    return $var; // 返回 $var 的引用
}
```

这里有一个展示按引用返回的示例：

```php
$number = 5;

function &getMyNumber() {
    global $number;
    return $number;
}

$numberRef = &getMyNumber();
echo "$number = $numberRef"; // 显示 "6"
echo "$numberRef = $numberRef"; // 显示 "6"
```

这是它的工作原理。首先，创建一个全局变量 `$number` 并赋值为 5。接下来，定义一个函数 `getMyNumber()`。该函数返回全局 `$number`。因为 `getMyNumber()` 的名字名前有一个 `&`，它返回的是 `$number` 的引用，而不是 `$number` 所持的值。

接下来，脚本调用 `getMyNumber()`。`getMyNumber()` 的值——即对 `$number` 的引用——被赋值给新变量 `$numberRef`。注意 `$numberRef` 指向与 `$number` 相同的数据。

## 编写递归函数

在第4章中，你学习了如何使用循环来管理大量数据。循环通常被称为迭代。如果你需要处理一组值，递归是另一种你可以使用的技术。通常来说，迭代通常比递归更容易；然而，在某些情况下，递归是有意义的。实际上，几乎任何循环都可以转换为递归，反之亦然。

以下是递归如何运行的简要概述：

- 递归函数由调用代码调用

- 如果满足基础情况（或条件），函数执行任何所需的处理，然后退出

- 否则，函数执行任何所需的处理，然后调用自己继续递归

当然，你必须确保最终能到达基础情况，否则函数将无限调用自己（导致死循环）。

# 尝试用递归创建斐波那契数列

第4章展示了如何使用循环创建斐波那契数列。以下脚本与第4章显示的类似，但它使用递归函数来生成每个值，而不是计算它。

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 1.0 Strict//EN">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Fibonacci sequence using recursion</title>
<link rel="stylesheet" type="text/css" href="common.css" />
<style>
th { text-align: left; background-color: #999; }
th, td { padding: 0.4em; }
tr.alt td { background: #ddd; }
</style>
</head>
<body>
<h2>Fibonacci sequence using recursion</h2>
<table cellspacing="0" border="0" style="width:20em; border: 1px solid #666;">
<tr>
<th>Sequence</th>
<th>Value</th>
</tr>
</table>
```

```php
$iterations = 10;
```

# 第二部分：学习语言

```php
function fibonacci($n) {
  if ( $n == 0 ) || ( $n == 1 ) return $n;
  return fibonacci($n-2) + fibonacci($n-1);
}

for ($i=0; $i <= $iterations; $i++) {
  <tr<?php if ($i % 2 != 0 ) echo ' class="alt"' ?>>
    <td><?php echo $i; ?></td>
    <td><?php echo fibonacci( $i );?></td>
  </tr>
}
<?php
?>
</table>
</body>
</html>
```

将脚本保存为 `fibonacci_recursion.php` 你的文档根目录，并通过 Web 浏览器运行它。你应该看到一个与图 7-6 相似的页面。注意，该序列与第 4 章脚本生成的序列完全相同。

![](img/ede05b7b77968b82cbd9a513122fb183_199_0.png)

图 7-6

162

## 第 7 章：函数

## 工作原理

大部分代码与第 4 章中的脚本相似。该脚本显示了一个 XHTML 头部，然后创建一个表格来显示结果。它也使用 `for` 循环来显示斐波那契数，与第 4 章的脚本非常相似。

区别在于斐波那契数的计算方式。第 4 章中的迭代版本使用了两个变量 `$num1` 和 `$num2` 来存储当前的斐波那契数，并在循环迭代时计算新数字。而在该脚本中，另一个使用了递归函数 `fibonacci()` 来计算任何给定序列数字的斐波那契数。然后从 `for` 循环中调用该函数来显示对应的斐波那契数。

`fibonacci` 函数是如何工作的？你可以看到它接受当前序列 `$n` 作为参数。函数的第一行返回基础情况：

```php
if ( $n == 0 ) || ( $n == 1 ) return $n;
```

这段代码检查序列号是否为 0 或 1；如果是，它将立即退出函数并返回该序列（因为 F 是 0 且 F 是 1）。在满足条件下，函数结束并将控制权交还给调用代码。

如果还没有达到基础情况，第二行代码是：

```php
return fibonacci($n-2) + fibonacci($n-1);
```
