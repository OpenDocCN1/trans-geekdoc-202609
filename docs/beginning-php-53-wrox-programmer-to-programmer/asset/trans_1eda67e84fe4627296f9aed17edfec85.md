

# 第二部分：学习语言

```php
print_r( $authors );
echo $nextCell;
print_r( array_splice( $authors, 2, 0, $arrayToAdd ));
echo $nextCell;
print_r( $arrayToArray );
echo $nextCell;
print_r( $authors );
echo $rowEnd;
echo "${($headingStart)2. 用一个新元素替换两个元素${($headingEnd)}"

$authors = array( "Steinbeck", "Kafka", "Tolkien" );
$arrayToAdd = array( "Bronte" );
echo $rowStart;
print_r( $authors );
echo $nextCell;
print_r( array_splice( $authors, 0, 2, $arrayToAdd ) );
echo $nextCell;
print_r( $arrayToAdd );
echo $nextCell;
print_r( $authors );
echo $rowEnd;

echo "${($headingStart)3. 移除最后两个元素${($headingEnd)}"

$authors = array( "Steinbeck", "Kafka", "Tolkien" );
echo $rowStart;
print_r( $authors );
echo $nextCell;
print_r( array_splice( $authors, 1 ) );
echo $nextCell;
echo "Nothing";
echo $nextCell;
print_r( $authors );
echo $rowEnd;

echo "${($headingStart)4. 插入字符串而不是数组${($headingEnd)}"

$authors = array( "Steinbeck", "Kafka", "Tolkien" );
echo $rowStart;
print_r( $authors );
echo $nextCell;
print_r( array_splice( $authors, 1, 0, "Orwell" ) );
echo $nextCell;
echo "Orwell";
echo $nextCell;
print_r( $authors );
echo $rowEnd;

echo '</table>';

?>

<body>
</body>
</html>
```

## 第 6 章：数组

![](img/ede05b7b77968b82cbd9a513122fb183_170_0.png)

| 原始数组 | 已移除的 | 新数组 |
| --- | --- | --- |
| [0] => Steinbeck | [0] => Melville | [0] => Steinbeck |
| [1] => Kafka | [1] => Hardy | [1] => Kafka |
| [2] => Tolkien | | [2] => Tolkien |

## 2. 用一个新元素替换两个元素

| 原始数组 | 已移除的 | 新数组 |
| --- | --- | --- |
| [0] => Steinbeck | [0] => Steinbeck | [0] => Bronte |
| [1] => Kafka | | [1] => Kafka |
| [2] => Tolkien | | [2] => Tolkien |

## 3. 移除最后两个元素

| 原始数组 | 已移除的 | 新数组 |
| --- | --- | --- |
| [0] => Steinbeck | [0] => Kafka | [0] => Steinbeck |
| [1] => Kafka | [1] => Tolkien |

## 4. 插入字符串而不是数组

| 原始数组 | 已移除的 | 新数组 |
| --- | --- | --- |
| [0] => Steinbeck | | [0] => Steinbeck |
| [1] => Kafka | | [1] => Orwell |
| [2] => Tolkien | | [2] => Kafka |
| | | [3] => Tolkien |

完成：

## 工作原理

此脚本演示了 `array_splice()` 的四种不同用法，并在 HTML 表格中显示结果。第一个示例在数组的第三位置插入了两个元素，显示了被移除的元素，在这种情况下它是一个空数组，因为没有元素被移除：

```php
array_splice( $authors, 2, 0, $arrayToAdd );
```

你可以这样理解它：“在第三个位置 (2)，移除 (0) 个元素，然后插入 `$arrayToArray`。”

第二个示例演示了如何同时移除和插入元素：

```php
array_splice($authors, 0, 2, $arrayToAdd );
```

这段代码从数组的开头（位置 0）移除两个元素，并在位置 0 处插入 `$arrayToArray` 的内容。

第三个示例展示了如果省略第三个参数会发生什么：

```php
array_splice($authors, 1 );
```

```这段代码移除了从第二个位置（位置 1）到数组末的所有元素。

最后，第四个示例演示了你不需要传递数组作为第四个参数。如果你只有一个元素要添加——一个字符串值——你只需要传递该值即可。这是因为 `array_splice()` 在使用第四个参数之前会自动将其转换为数组。因此，字符串 "Orwell" 在被添加到数组之前，会被转换成一个包含单个元素（"Orwell"）的数组。

```php
array_splice($authors, 1, 0, "Orwell");
```

顺便说一下，你会注意到脚本通过创建变量来存储标记片段，从而输出了大量重复的内容。这不仅让 PHP 代码更加紧凑且易于遵循，而且在以后需要时更容易更改标记。请注意，当插入数组时，所插入元素的键（keys）不会被保留；它们将使用数字键进行重新索引。`array_splice()` 对于关联数组并不好用。例如：

```php
$authors = array("Steinbeck", "Kafka", "Tolkien");
array_splice($authors, 1, 0, array("authorName" => "Milton"));
echo "<pre>";
print_r($authors);
echo "</pre>";
```

这段代码产生了以下结果：

```
Array
{
[0] => Steinbeck
[1] => Milton
[2] => Kafka
[3] => Tolkien
}
```

注意看 "Milton" 元素的原始键 ("authorName") 是如何被替换为数字键 (1)。

## 合并数组

如果你想合并两个或多个数组以生成一个大数组，你需要 `array_merge()` 函数。该函数接受一个或多个数组作为参数，并返回合并后的数组（原始数组不受影响）。这是一个示例：

```php
$authors = array("Steinbeck", "Kafka");
$moreAuthors = array("Tolkien", "Milton");
print_r(array_merge($authors, $moreAuthors));
```

注意 `array_merge()` 通过合并数组的元素来生成最终数组。它与 `array_push()`、`array_shift()` 以及方括号语法不同，后者是通过插入来生成多个数组。

```php
$authors = array("Steinbeck", "Kafka");
$moreAuthors = array("Tolkien", "Milton");
```

`array_merge()` 将数组元素合并以生成最终数组。对比 `array_push()`、`array_shift()` 和方括号语法：

```php
$authors = array("Steinbeck", "Kafka");
$moreAuthors = array("Tolkien", "Milton");
```

`array_push()` 是通过插入来生成多个数组的。通过数组，你可以使用它来重新索引索引数组：

```php
$authors = array("Steinbeck", "Kafka");
$moreAuthors = array("Tolkien", "Milton");
```

`array_merge()` 的一个特性是保留关联数组的键，因此你可以使用它来添加新的键值对：

```php
$authors = array("Steinbeck", "Kafka");
$moreAuthors = array("Tolkien", "Milton");
```

`array_merge()` 产生：

如果数组中已经存在相同的键，该元素会被覆盖：

```php
$authors = array("Steinbeck", "Kafka");
$moreAuthors = array("Tolkien", "Milton");
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：

```Array [0] => Steinbeck, [1] => Kafka, [2] => Tolkien, [3] => Milton
```

`array_merge()` 产生：（此处省略重复内容）

## 转换数组与字符串

PHP 提供了几个函数，可以将字符串转换为数组，或者将数组转换为字符串。

要将字符串转换为数组，可以使用 PHP 的 `explode()` 字符串函数。该函数接收一个字符串，根据指定的分隔符将其拆分为不同的块，并返回包含这些块的数组。示例：

```php
$fruitString = "apple,pear,banana,strawberry,peach";
$fruitArray = explode(",", $fruitString);
```

执行此代码后，$fruitArray 包含一个有五个元素的数组："apple","pear","banana","strawberry" 和 "peach"。

你可以通过第三参数限制返回数组中的元素数量，在这种情况下，数组元素将包含字符串剩余部分：

```php
$fruitString = "apple,pear,banana,strawberry,peach";
$fruitArray = explode(",", $fruitString, 3);
```

在这个示例中，$fruitArray 包含元素 "apple","pear" 以及 "banana,strawberry,peach"。

或者，指定一个负参数来从字符串末尾排除相应数量的组件。例如，在示例中使用 -3 仅创建一个包含 "apple" 和 "pear" 的数组。（三个组件 "banana","strawberry" 和 "peach" 被忽略了）。

```php
$fruitString = "apple,pear,banana,strawberry,peach";
$fruitArray = explode(",", $fruitString, -3);
```

```Array [0] => apple, [1] => pear
```

