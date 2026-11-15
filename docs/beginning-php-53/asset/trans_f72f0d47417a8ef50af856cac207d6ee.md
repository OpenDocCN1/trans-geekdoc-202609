
要动态创建函数 — 你可以在创建匿名函数时自定义其中的代码。虽然你很少需要这样做，但在某些特定情况下，这可以使你的代码非常灵活。

要创建短期、一次性的函数 — 通常，当你使用需要创建回调函数或事件处理程序函数的内置函数时会这样做。示例包括 xml_set_element_handler()（你将在第 19 章中遇到）以及 array_walk() 等数组函数，它允许你将函数应用于数组中的每个值，还有 usort()，它根据你自己创建的比较函数对数组元素进行排序。

要创建匿名函数，你使用 create_function()。它需要两个参数：用逗号分隔的参数列表（如果有的话），以及函数体的代码（不包括花括号，但每行代码末尾包含分号）。它返回一个唯一的、随机生成的字符串值，你可以用它来稍后引用该函数：

```
$myFunction = create_function( '$param1, $param2', 'function code here,' );
```

下面是一个简单示例，它根据变量的值动态创建匿名函数：

```
$mode = "+";
$processNumbers = create_function( '$a, $b', "return \$a $mode \$b;" );
echo $processNumbers( 2, 3 ); // Displays "5"
```

这段代码使用 $mode 变量的值作为处理其两个参数 $a 和 $b 的运算符。例如，如果将 $mode 改为 "*"，代码将显示 "6"（2 乘以 3）。代码本身看起来没有什么意义，但如果你能想象一个更复杂的函数，其内容由外部因素（如用户输入）决定，你就能看到这是 PHP 的一项潜在强大功能。

更常见的是，你会使用匿名函数来创建某些内置函数所需的回调函数，如下例所示。

## 试一试 按长度排序单词

此示例脚本获取一段文本，并按每个单词的字母数量对文本中的所有单词进行排序，最短单词优先。为此，它使用匿名函数，以及 PHP 内置的 usort()、preg_replace()、array_unique() 和 preg_split() 函数。

将脚本保存为 sort_words_by_length.php 到你的文档根目录文件夹中，然后在浏览器中运行它。你应该会看到类似于图 7-5 的页面。

```
<!DOCTYPE html PUBLIC "--//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
	<title>Sorting words in a block of text by length</title>
	<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
	<h1>Sorting words in a block of text by length</h1>

<?php

$myText = <<<END_TEXT
But think not that this famous town has
only harpooneers, cannibals, and
bumpkins to show her visitors. Not at
all. Still New Bedford is a queer place.
Had it not been for us whalemen, that
tract of land would this day perhaps
have been in as howling condition as the
coast of Labrador.
END_TEXT;

echo "<h2>The text:</h2>";
echo "<div style=\"width: 30em;\">$myText</div>";

$myText = preg_replace( "/[.,]/", "", $myText );
$words = array_unique( preg_split( "/[ \\n\\r\\t]+/", $myText ) );
usort( $words, create_function( '$a, $b', 'return strlen($a) - strlen($b);' ) );

echo "<h2>The sorted words:</h2>";
echo "<div style=\"width: 30em;\">";

foreach ( $words as $word ) {
    echo "$word ";
}

echo "</div>";

?>
</body>
</html>
```

![](img/1ddec54918a4802eb9b4febec3d4e7f6_193_0.png)

## 图 7-5

## 工作原理

显示 XHTML 页面页眉后，脚本设置一个 $myText 变量，用于保存要排序其单词的文本。（随意将示例文本替换为你自己的文本。）然后，它在固定宽度的 HTML div 元素中显示该文本。

接下来，脚本开始处理文本。首先，它使用 PHP 的 preg_replace() 函数从文本中删除所有逗号和句点：

```
$myText = preg_replace( "/[\\.,]/", "", $myText );
```

（此行代码使用简单的正则表达式来完成其工作；你将在第 18 章了解更多关于 preg_replace() 和正则表达式的内容。）

下一行代码调用 PHP 的 preg_split() 函数，将字符串分割为单词数组，使用 \n、\r、\t 和空格等任何空白字符来确定单词边界。然后，它通过 PHP 实用的 array_unique() 函数处理该数组，从数组中删除任何重复的单词：

```
$words = array_unique( preg_split( "/[ \\n\\r\\t]+" , $myText ) );
```

preg_split() 通过使用正则表达式来定位分割点，从而分割字符串。有关 preg_split() 的更多信息，请参见第 18 章。

接下来是排序逻辑，这就是匿名函数发挥作用的地方。脚本使用 PHP 的 usort() 函数对单词数组进行排序。usort() 需要一个要排序的数组，随后是一个回调比较函数。所有比较函数都需要接受两个值——$a 和 $b——并返回三个值之一：

- 如果 $a 被认为“小于” $b，则返回负数
- 如果 $a 被认为“等于” $b，则返回零
- 如果 $a 被认为“大于” $b，则返回正数

在这种情况下，比较函数需要确定字符串 $a 的长度是小于、等于还是大于字符串 $b 的长度。它可以通过用 $b 的长度减去 $a 的长度并返回结果来简单地完成此操作。（请记住第 5 章中，PHP 的 strlen() 函数返回字符串的长度。）

那么，对数组进行排序的完整代码行如下：

```
usort( $words, create_function( '$a, $b', 'return strlen($a) - strlen($b);' ) );
```

请注意，此行代码使用 create_function() 函数创建一个匿名比较函数，随后由 usort() 用于对数组进行排序。

最后，脚本在另一个固定宽度的 div 元素中显示排序后的单词列表。

顺便说一句，在这种情况下，你不必使用匿名函数。前面的代码行可以写成：

```
function sortByLength( $a, $b ) {
  return strlen( $a ) - strlen( $b );
}

usort( $words, "sortByLength" );
```

不过，如你所见，匿名函数版本更加简洁。

## 使用引用

你已经学到，你可以以参数形式将信息传递给函数，也可以使用 return 语句从函数向其调用代码返回信息。当你做其中任何一件事时，PHP 实际上是将信息的副本传递到函数中和从函数中返回；这被称为按值传递和返回。

大多数时候这不是问题，但有时你希望函数处理原始信息，而不是副本。考虑以下示例：

```
function resetCounter( $c ) {
  $c = 0;
}

$counter = 0;
$counter++;
$counter++;
$counter++;
echo "$counter<br />"; // Displays "3"
resetCounter( $counter );
echo "$counter<br />"; // Displays "3"
```

这段代码定义了一个名为 resetCounter() 的函数，用于将其参数重置为零。然后，将 $counter 变量初始化为零并递增三次。正如你所期望的，此时 $counter 的值为 3。随后调用 resetCounter()，传入 $counter 变量（即要重置的变量）。然而，正如第二条 echo 语句所示，$counter 并未被函数重置。这是因为 resetCounter() 内部的参数 $c 仅持有 $counter 中存储信息的副本。因此，当函数将 $c 设置为零时，它根本不影响 $counter 的值。

幸运的是，PHP 提供了一种称为引用的机制，你可以使用它来绕过此类问题。引用有点类似于硬盘上文件的快捷方式或别名。当你创建对 PHP 变量的引用时，你现在有两种读取或更改变量内容的方法——可以使用变量名，也可以使用引用。下面是一个创建对变量引用的简单示例：

```
$myVar = 123;
$myRef = & $myVar;
$myRef++;
echo $myRef . "<br />"; // Displays "124"
echo $myVar . "<br />"; // Displays "124"
```
