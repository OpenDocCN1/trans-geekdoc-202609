

下面是一个示例：

```
$authors = array( "Steinbeck", "Kafka" );
$moreAuthors = array( "Tolkien", "Milton" );

// Displays "Array ( [0] => Steinbeck [1] => Kafka [2] => Tolkien [3] => 
Milton )"
print_r( array_merge( $authors, $moreAuthors ) );
```

请注意，array_merge() 将数组的元素连接在一起以生成最终数组。这与 array_push()、array_unshift() 和方括号语法形成对比，后者都会原样插入数组参数以生成多维数组：

```
$authors = array( "Steinbeck", "Kafka" );
$moreAuthors = array( "Tolkien", "Milton" );
array_push( $authors, $moreAuthors );

// Displays "Array ( [0] => Steinbeck [1] => Kafka [2] => Array ( [0] => 
Tolkien [1] => Milton ) )"
print_r( $authors );
```

array_merge() 的一个不错的特性是它保留关联数组的键，因此你可以使用它向关联数组添加新的键/值对：

```
$myBook = array( "title" => "The Grapes of Wrath",
                 "author" => "John Steinbeck",
                 "pubYear" => 1939 );

$myBook = array_merge( $myBook, array( "numPages" => 464 ) );

// Displays "Array ( [title] => The Grapes of Wrath [author] => John 
Steinbeck [pubYear] => 1939 [numPages] => 464 )"
print_r ( $myBook );
```

如果使用已经存在于数组中的字符串键添加键/值对，则原始元素会被覆盖。这使得 array_merge() 非常适合更新关联数组：

```
$myBook = array( "title" => "The Grapes of Wrath",
                 "author" => "John Steinbeck",
                 "pubYear" => 1939 );

$myBook = array_merge( $myBook, array( "title" => "East of Eden", "pubYear" 
=> 1952 ) );

// Displays "Array ( [title] => East of Eden [author] => John Steinbeck 
[pubYear] => 1952 )"
print_r ( $myBook );
```

但是，具有相同数字键的元素不会被覆盖；相反，新元素会被添加到数组末尾并赋予一个新索引：

```
$authors = array( "Steinbeck", "Kafka", "Tolkien", "Dickens" );
$authors = array_merge( $authors, array( 0 => "Milton" ) );
```

```
// Displays "Array ( [0] => Steinbeck [1] => Kafka [2] => Tolkien [3] => Dickens [4] => Milton )"
print_r ( $authors );
```

如果要在保留数字键的同时合并数组，请尝试 array_replace() 函数（PHP 5.3 新增）。有关详细信息，请参见 http://www.php.net/manual/en/function.array-replace.php。

你还可以通过仅传递数组来使用 array_merge() 重新索引单个数字索引数组。如果要确保索引数组的所有元素都是连续索引的，这很有用：

```
$authors = array( 34 => "Steinbeck", 12 => "Kafka", 65 => "Tolkien", 47 => "Dickens" );
```

```
// Displays "Array ( [0] => Steinbeck [1] => Kafka [2] => Tolkien [3] => Dickens )"
print_r( array_merge( $authors ) );
```

## 在数组和字符串之间转换

PHP 提供了一些函数，可让你将字符串转换为数组，或将数组转换为字符串。

要将字符串转换为数组，可以使用 PHP 方便的 explode() 字符串函数。该函数获取一个字符串，根据指定的分隔符字符串将其分割成单独的块，并返回包含这些块的数组。下面是一个示例：

```
$fruitString = "apple,pear,banana,strawberry,peach";
$fruitArray = explode( ",", $fruitString );
```

运行此代码后，$fruitArray 包含一个带有五个字符串元素的数组："apple"、"pear"、"banana"、"strawberry" 和 "peach"。

可以使用第三个参数限制返回数组中的元素数量，在这种情况下，最后一个数组元素包含字符串的其余部分：

```
$fruitString = "apple,pear,banana,strawberry,peach";
$fruitArray = explode( ",", $fruitString, 3 );
```

在此示例中，$fruitArray 包含元素 "apple"、"pear" 和 "banana,strawberry,peach"。

或者，指定一个负的第三个参数，以从数组中排除字符串末尾的那么多组件。例如，在刚才显示的示例中使用 -3 会创建一个仅包含 "apple" 和 "pear" 的数组。（会忽略三个组件 "banana"、"strawberry" 和 "peach"。）

explode() 通常很有用，当你需要从文件中读取一行逗号分隔或制表符分隔的数据并将数据转换为值数组时。

其他有用的字符串转数组函数包括 preg_split()（用于基于正则表达式分割，参见第 18 章）和 str_split()（用于将字符串分割为字符或固定长度字符块 — 有关详细信息，请参见 http://www.php.net/manual/en/function.str-split.php）。

如果要执行 explode() 的相反操作，将数组元素粘合成一个长字符串，请使用 — 你猜对了 — implode()。它需要两个参数：要在字符串中每个元素之间放置的字符，以及包含要放入字符串中的元素的数组。例如，以下代码将 $fruitArray 中的元素连接起来形成一个长字符串 $fruitString，每个元素之间用逗号分隔：

```
$fruitArray = array( "apple", "pear", "banana", "strawberry", "peach" );
$fruitString = implode( ",", $fruitArray );

// Displays "apple,pear,banana,strawberry,peach"
echo $fruitString;
```

## 将数组转换为变量列表

你在本章中学到的最后一个数组操作工具是 list()。这个结构提供了一种简单的方法，将数组的值提取到单独的变量中。请考虑以下代码：

```
$myBook = array( "The Grapes of Wrath", "John Steinbeck", 1939 );

$title = $myBook[0];
$author = $myBook[1];
$pubYear = $myBook[2];
```

```
echo $title . "<br />"; // Displays "The Grapes of Wrath"
echo $author . "<br />"; // Displays "John Steinbeck"
echo $pubYear . "<br />"; // Displays "1939"
```

它可行，但相当冗长。这时 list() 就派上用场了。你可以这样使用它：

```
$myBook = array( "The Grapes of Wrath", "John Steinbeck", 1939 );
list( $title, $author, $pubYear ) = $myBook;
```

```
echo $title . "<br />"; // Displays "The Grapes of Wrath"
echo $author . "<br />"; // Displays "John Steinbeck"
echo $pubYear . "<br />"; // Displays "1939"
```

请注意，list() 仅适用于索引数组，并且假设元素从零开始连续索引（即第一个元素的索引为 0，第二个元素的索引为 1，依此类推）。

`list()` 的经典用法是与 `each()` 等函数一起使用，这些函数返回一个值的索引数组。例如，你可以将本章前面“遍历数组”中的 `each()` 示例改写为使用 `list()`：

```
$myBook = array( "title" => "The Grapes of Wrath",
        "author" => "John Steinbeck",
        "pubYear" => 1939 );

while ( list( $key, $value ) = each( $myBook ) ) {
    echo "<dt>$key</dt>";
    echo "<dd>$value</dd>";
}
```

## 摘要

本章向你介绍了另一个重要概念：数组。这些是可以存储多个值的特殊变量，你会发现自己在 PHP 脚本中不断使用它们。

首先，你深入了解了数组的结构，并学习了索引数组和关联数组的概念。然后，你学习了如何在 PHP 中创建数组，以及如何使用方括号和 `array_slice()` 访问数组元素。在此过程中，你了解了一种非常有用的 PHP 函数 `print_r()`，你可以使用它输出整个数组以用于调试目的。

接着，你发现每个 PHP 数组都有一个引用其元素的内部指针，你学习了如何使用此指针通过 `current()`、`key()`、`next()`、`prev()`、`end()` 和 `reset()` 在数组中移动元素。你还使用了方便的 `foreach` 循环结构来遍历数组中的元素。

当你开始将数组嵌套以生成多维数组时，数组会变得非常强大。你学习了如何创建此类数组，以及如何访问其元素并遍历它们。

最后，你探索了一些强大的 PHP 数组操作函数，包括：

- 排序函数 — 你查看了 `sort()`、`asort()`、`ksort()` 和 `array_multisort()` 等函数
- 添加和删除元素的函数 — 这些包括 `array_unshift()`、`array_shift()`、`array_push()`、`array_pop()` 和 `array_splice()`
- `array_merge()` — 此函数可用于合并两个或多个数组
- `explode()` 和 `implode()` — 这些可让你在数组和字符串之间转换
- `list()` — 你可以使用它将数组元素存储在单个变量列表中

PHP 提供的数组相关函数远比本章介绍的多。访问在线 PHP 手册 http://www.php.net/types.array 了解 PHP 提供的其他数组函数的概览会很有帮助。另外，尝试以下两个练习来测试你的数组操作技能。你可以在附录 A 中找到这些练习的解答。

下一章将探讨 PHP 中的函数概念，并向你展示如何创建自己的函数以及构建可重用的代码块。

