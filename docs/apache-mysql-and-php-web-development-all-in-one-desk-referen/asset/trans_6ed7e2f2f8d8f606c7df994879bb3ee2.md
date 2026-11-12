

在此示例中，我为四个元素指定了索引；这些索引是 1、2、5 和 6。之后我没有指定任何索引。在这种情况下，PHP 处理器会确定数值上最高的索引，加 1，并将其用作下一个索引。因为 6 是最高的，所以下一个索引是 7，接着是 8，然后是 9。

When you open this PHP code in the browser, you see the following output:

```
1,2
2,4
3,
4,
5,10
6,12
7,14
8,16
9,18
```

你可以看到使用的索引是：1、2、5、6，这是我显式指定的，接着是 7、8 和 9，由 PHP 处理器自动指定。我跳过了索引 3 和 4，所以 PHP 处理器在这些索引中没有放入任何内容。

如果你指定一些索引，让 PHP 处理器指定其他索引，请小心。你可能会无意中覆盖一个元素。查看以下示例：

```php
<?php
$names = array(0=>"Suzy", 1=>"Carousel",
"Jennifer", 2=>"Jeff" );
print $names[0]."<br>";
print $names[1]."<br>";
print $names[2]."<br>";
print $names[3]."<br>";
print $names[4]."<br>";
?>
```

处理器在遇到值 Jennifer 时会自动分配索引 2，因为处理器只考虑目前为止遇到的元素。然后当它到达下一个元素时，会发现该元素也是 2，于是处理器会覆盖前一个元素。因此，名称 Jennifer 被名称 Jeff 覆盖，最终你只有三个元素，而不是四个！所以请小心！

如果你需要将数组的值嵌入字符串，且索引本身也是字符串，最好使用尖括号以确保清晰。但这样做可能会变得混乱，因为字符串内部的字符串该如何表示呢？一种方法是为主字符串使用双引号，为索引使用单引号，如下所示：

```php
print "{$movies['The Matrix']} was in The Matrix.<br>";
```

在这行代码中，数组名为 $movies，索引是 The Matrix。对于主字符串，我使用了双引号；对于索引，我使用了单引号。

虽然这看起来可能很奇怪且难以置信（我承认我当时也很惊讶），但全程使用双引号也可行：

```php
print "{$movies["The Matrix"]} was in The Matrix.<br>";
```

之所以可行，是因为解析器（PHP 处理器中将代码行拆分并弄清各个部分的机制）足够智能，知道花括号内的内容是特殊的，且可能包含双引号。

那么你应该使用哪一个呢？就像编程中很多次一样，选择权在你。就我个人而言，我更喜欢在双引号内使用单引号，因为这样对我们人类来说读起来更容易一些。

你不能为外层字符串使用单引号，因为无法在单引号内嵌入变量。PHP 处理器会将整个内容视为实际字符串。因此，如果你这样做：

```php
print '{$movies["The Matrix"]} was in The Matrix.<br>';
```

你会在浏览器窗口中看到以下输出：

```
{$movies["The Matrix"]} was in The Matrix.
```

这可能不是你期望的结果。

## 混合使用索引类型

有时，你可能希望某些索引是整数，而某些是字符串。PHP 允许你这样做；你只需混合使用索引即可，如以下示例所示：

```php
<?php
$nums = array(
    "a" => "b",
    1 => 2,
    "x" => "y"
);
print "a,{$nums['a']}<br>\n";
print "1,{$nums['1']}<br>\n";
print "x,{$nums['x']}<br>\n";
?>
```

在这段代码中，我创建了索引 a 并将值 b 存储在其中。然后我创建了索引 1 并将值 2 存储在其中。最后，我创建了索引 x 并将值 y 存储在其中。程序运行得很好。

PHP 处理器允许你混合使用索引类型，并在同一段代码中让处理器为你选择一些索引。这可能会令人困惑。以下是一段可能令人困惑的代码示例：

```php
<?php
$funs = array(
    1=>2,
    "a"=>"b",
    3,
    "x"=>"y"
);
print "1,{$funs[1]}<br>\n";
print "2,{$funs[2]}<br>\n";
print "a,{$funs['a']}<br>\n";
print "x,{$funs['x']}<br>\n";
?>
```

在此示例中，数组中的第三项没有索引。为分配索引，PHP 处理器遵循常规规则，查看现有的编号索引，找到最大的一个并加 1。此示例中只有一个编号索引，即 1，因此该项得到索引 2。于是，$funs[2] 得到值 3。当 print 语句运行时，你可以看到这是正确的。

在 C++ 等传统语言中，数组的索引始终是整数，并且始终从 0 或 1 开始，具体取决于语言。然而，Python 和 Perl 等其他语言允许你使用字符串作为索引。

## 在数组中存储值

如果你已经声明了特定的数组，可以向数组添加值或修改其中已有的值。

如果你熟悉 C++ 等其他语言，会很高兴地知道，在 PHP 中，你可以在创建数组后随时向数组末尾添加新元素，从而使数组变长。在 C++ 中，你无法做到这一点。

创建数组后，可以通过向元素分配新值来更改其值。假设你有一个名为 $nums 的数组，并将元素 2 初始化为值 4。你现在希望该元素的值为 10。更改值的方法如下：

```php
$nums[2] = 10;
```

此语句将元素 2 原有的任何值替换为值 10。

在 PHP 中，变量没有固定类型。因此，你可以编写如下代码：

```php
$nums[2] = 10;
```

稍后，你可以将其更改为：

```php
$nums[2] = 'hello';
```

你也可以通过分配索引来向数组添加新值。以下是一个示例：

```php
<?php
$needmore = array(
    "icecream" => "chocolate",
    "pizza" => "pepperoni",
    "sandwich" => "turkey" );
$needmore["snacks"] = "potato chips";
print $needmore["pizza"]."<br>\n";
print $needmore["snacks"];
?>
```

在此，我创建了 $needmore 数组并放入三个项目。然后我又向数组添加了一个项目，即索引 snacks 对应的值 potato chips。

## 从数组中移除值

要从数组中移除项目，请使用 unset 关键字。（是的，名称有点奇怪，但这是计算机的世界。）以下是一个示例：

```php
<?php
$movies = array(
  "The Matrix" => "Keanu Reeves",
  "Raiders of the Lost Ark" => "Harrison Ford",
  "Forrest Gump" => "Tom Hanks",
  "Men in Black" => "Will Smith" );
unset ( $movies["The Matrix"] );
print $movies["The Matrix"];
?>
```

此代码从数组中移除键为 The Matrix 的条目。运行此代码时，输出中没有任何内容，因为 $movies["The Matrix"] 不再具有值。

因为 PHP 中的数组按键分组存储一组值，所以数组没有顺序。这意味着你可以从数组中移除项目而不会在数组中留下空位，这与其他语言的情况不同。

你可能好奇为什么要从数组中移除项目。毕竟，如果不需要该项目，难道不能直接忽略它吗？是的，可以，但有时你可能希望遍历数组的所有元素。如果有多余的元素，就很难简单地跳过它们。要了解如何遍历数组，请查看下一节。

## 遍历数组

如果你需要对数组的每个成员执行某个操作（例如打印每个成员姓名；而不是切除胆囊），PHP 提供了几种方法。以下是一个示例：

```php
<?php
$missingbodyparts = array( "Jim" => "spleen", "Sally" =>
  "gall bladder",
  "Hank" => "appendix", "Jill" => "tonsils" );
foreach ( $missingbodyparts as $part ) {
  print $part."<br>";
}
?>
```

Here's the HTML output from this program:

```
spleen<br>gall bladder<br>appendix<br>tonsils<br>
```

此代码用各种身体部位填充数组 $missingbodyparts，以人名作为键。（幸运的是，没有人缺头。）

