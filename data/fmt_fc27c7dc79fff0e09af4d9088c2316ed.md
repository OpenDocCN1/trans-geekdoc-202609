
`print("$key : $value<br>\n");`

}

?>

```
# list(...)

`list` 函数将变量列表视为数组。它只能用于赋值运算符的左侧。它非常用于将返回的数组直接转换为一组变量。

```php
<?php

$colors = array("red", "green", "blue");

// 将返回数组的前两个元素
// 分别放入键和值

list($key, $value) = each($colors);

print("$key: $value<br>\n");

?>
```

# value型 max(array) 或 value型 max(...)

`max` 函数返回所有数组元素中的最大值。如果所有值都是字符串，则将作为字符串进行比较。如果任何值是数字，则对整数和浮点数进行数值比较。`max` 函数的备用版本接受任意数量的参数并返回其中最大的。使用此用法时，你必须提供至少两个值。

要找到最小值，请使用 `min`。

```php
<?php

$colors = array("red"=>"FF0000",
    "green"=>"00FF00",
    "blue"=>"0000FF");

// 输出 FF0000
print(max($colors)) . "<br>\n";

// 输出 13
print(max("hello", "55", 13) . "<br>\n";

// 输出 17
print(max(1, 17, 3, 5.5) . "<br>\n");

?>
```

`min` 函数返回所有数组元素中的最小值。如果所有值都是字符串，则将作为字符串进行比较。如果任何值是数字，则只对整数和浮点数进行数值比较。`min` 函数的备用版本接受任意数量的参数并返回其中最小的。你必须提供至少两个值。

```php
<?php

$colors = array("red"=>"FF0000","green"=>"00FF00","blue"=>"0000FF");

// 输出 0000FF
print(min($colors)) . "<br>\n";

// 输出 13
print(min("hello", "55", 13)) . "<br>\n";

// 输出 1
print(min(1, 17, 3, 5.5) . "<br>\n";

?>
```

# value型 next(array arrayname)

`next` 函数将 PHP 数组指针向前移动一个元素。它返回新元素的值。如果指针已经到达数组末尾，则返回 FALSE。

```php
<?php

$colors = array("red","green","blue");

$my_color = current($colors);

do {
    print("$my_color <br>\n");
}while($my_color = next($colors));

?>
```

### 核心 PHP 编程

# pos

你可以将 `pos` 作为 `current` 函数的别名。

# value型 prev(array arrayname)

`prev` 函数的操作与 `next` 函数类似，不同在于它是向后移动数组。内部指针向后移动一个元素，并返回该位置的值。如果指针在开头，则返回 FALSE。

```php
<?php

$colors = array("red", "green", "blue");

end($colors);

$my_color = current($colors);

do(
    print("$my_color <br>\n");
) while ($my_color = next($colors));
?>
```

# array range(integer start, integer stop)

使用 `range` 创建包含从 `start` 到 `stop` 之间每个整数的数组（包含 `stop`）。

```php
<?php
$numbers = range(13, 19);
// 输出所有值
foreach($numbers as $value)
{
    print("$value <br>\n");
}
?>
```

# value型 reset(array arrayname)

`reset` 函数将数组的指针设置为第一个元素。返回该元素。使用 `end` 将指针设置为最后一个元素。

```php
<?php
$colors = array("red", "green", "blue");
// 设置第一个元素
reset($colors);
// 设置最后一个元素
end($colors);
// 获取当前元素
current($colors);
// 移动到下一个元素
next($colors);
// 移动到上一个元素
prev($colors);
// 获取当前键
key($colors);
// 获取键值对
each($colors);
// 重置到第一个元素
reset($colors);
?>
```

```php
<?php

$colors = array("red", "green", "blue");

// 将指针设置为第一个元素
reset($colors);

// 获取当前元素
$my_color = current($colors);

// 移动到下一个元素
$my_color = next($colors);

// 移动到上一个元素
$my_color = prev($colors);

// 获取当前键
$key = key($colors);

// 获取键值对
$pair = each($colors);

// 重置到第一个元素
reset($colors);

// 输出第一个元素
print($my_color);

?>
```

# rsort(array unsorted)

`rsort` 函数按反向顺序对数组进行排序。在排序函数中，字符串值的出现会导致所有元素被视为字符串并按字母顺序排序。如果所有元素都是数字，它们将进行数值比较。类似于 `asort`，`rsort` 会丢弃键值并从零开始重新赋值。第 15 章深入讨论了排序。

```php
<?php
// 测试用数据
$colors = array("one"->"orange", "two"->"cyan", "three"->"purple");

// 按键对数组进行排序
rsort($colors);

// 输出数组
foreach($colors as $key=>$value)
{
    print("$key = $value<br>\n");
}
?>
```

# shuffle(array data)

`shuffle` 函数随机重排数组中的元素。`srand` 函数可用于随机数生成器的种子，但与 `rand` 函数一样，如果你不提供种子，将使用当前时间的种子。

```php
<?php
// 测试用数据
$numbers = range(1, 10);

// 重排
shuffle($numbers);

// 输出所有值
foreach($numbers as $value)
{
    print("$value<br>\n");
}
?>
```

# sizeof

这是 `count` 函数的别名。

# sort(array unsorted_array)

`sort` 函数按元素值从低到高对数组进行排序。如果任何元素是字符串，为了比较，所有元素都将转换为字符串并按字母顺序排序。如果所有元素都是数字，它们将进行数值比较。类似于 `rsort`，`sort` 会丢弃键值并从零开始重新赋值。第 15 章深入讨论了排序。

```php
<?php
// 测试用数据
$colors = array("one"->"orange","two"->"cyan", "three"->"purple");

// 按键对数组进行排序
sort($colors);

// 输出数组
foreach($colors as $key=>$value)
{
    print("$key = $value<br>\n");
}
?>
```

# uasort(array unsorted_array, string comparison_function)

`uasort` 函数使用自定义比较函数对数组进行排序。索引值或键会随元素值移动，类似于 `as` 函数的行为。

比较函数必须返回一个带符号的整数。如果它返回零，则两个元素被视为相等。如果返回负数，则认为两个元素是有序的。如果返回正数，则认为两个元素是无序的。

```php
<?php

/*
 ** 重普通排序
 */
function compare($left, $right) 
{
    return($left - $right);
}

//创建测试数据
$sum_numbers = array(
    "red"=>0,
    "green"=>4,
    "blue"=>8,
    "yellow"=>2,
    "orange"=>7,
    "cyan"=>1,
    "purple"=>9,
    "magenta"=>3,
    "black"=>5
);

//使用自定义比较排序
uasort($sum_numbers, "compare");

//显示排序后的数组
foreach($sum_numbers as $key=>$value) 
{
    print($key . " =" . $value . "<BR\n");
}
?>
```

# uksort(array unsorted_array, string comparison_function)

`uksort` 函数使用自定义比较函数对数组进行排序。与 `usort` 不同，数组根据索引值（key values）进行排序，而不是元素。比较函数必须返回一个符号整数。如果返回零，则认为两个索引相等。如果返回负数，则认为两个索引是有序的。如果返回正数，则认为两个索引是无序的。

```php
<?php

/*
 ** 重普通排序
 */
function compare($left, $right) 
{
    return($left - $right);
}

//创建测试数据
srand(time());
for($i=0; $i<10; $i++)
{
  $data[rand(1,100)] = rand(1,100);
}

//使用自定义比较排序
uksort($data, "compare");

//显示排序后的数组
foreach($data as $key=>$value) {
  print($key . "=" . $value . "<BR>\n");
}
?>
```

# usort(array_unsorted_array, string_compare_function)

`usort` 函数使用自定义比较函数根据元素值对数组进行排序。该函数必须返回一个符号整数。如果返回负数，则认为两个元素是有序的。如果返回正数，则认为两个元素是无序的。

```php
<?php
/*
 ** 重普通排序
 */
function compare($left, $right) {
  return($left - $right);
}

//创建测试数据
srand(time());
for($i=0; $i<10; $i++) {
  $data[rand(1,100)] = rand(1,100);
}

//使用自定义比较排序
uksort($data, "compare");

//显示排序后的数组
foreach($data as $key=>$value) {
  print($key . "=" . $value . "<BR>\n");
}
?>
```

# 哈希 (Hashing)

# PHP 核心编程

哈希是使用值本身为该值创建一个索引的过程。该索引被称为哈希（hash）。有时哈希对于值来说是唯一的，但并非总是如此。哈希可以用于快速查找，这是 PHP 用来跟踪变量的方法。在其他情况下，如果两个字符串的哈希相同，你可以假设这两个字符串匹配，只要哈希值是唯一的。通过这种方式，你可以在不解密原始密码的情况下检查密码。

本节中的某些函数是 PHP 内置的。其他的是 Sascha Shumann 的 Mhash 库的一部分。该库为许多哈希算法提供了通用接口。访问主页了解更多信息 <http://schmann.cx/mhash/>。

# string md5(string text)

`md5` 函数产生如 RFC 1321 描述的哈希值。该函数接受任意长度的字符串并返回一个 32 字符的标识符。理论上，`md5` 函数的算法将为所有字符串生成唯一的标识符。

图 9-5. `md5`。

![](img/58e6a0f5d6a8a41d4645d8c07b3bf1e3_244_0.png)

```php
<?php
print(md5("Who is John Galt?"));
?>
```

# string metaphone(string word)

使用 `metaphone` 生成一个描述单词口读发音的字符串。此函数类似于 `soundex`；然而，它知道英语中字母组合的发音方式。因此，它更准确。将此函数与 `soundex` 和 `similar_text` 进行比较。

# PHP 核心编程

`metaphone` 算法由 Lawrence Philips 发明，首次在《Computer Language》杂志上描述。你可能可以在 Scott Gasch 的存档 <http://perl.guru.org/archive> 中找到关于 `metaphone` 的讨论。

```php
<?php
print("Atkinson encodes as " . metaphone("Atkinson"));
?>
```

# string mhash(integer hash, string data)

使用 `mhash` 获取字符串的哈希值。编写时可哈希算法见表 9.2。

参考 Mhash 文档获取有关每个算法的更多信息。

```php
<?php
print(mhash(MHASH_GOST
```

表 9.2. Mhash 算法

| MHASH_CRC32 |
| :--- |
| MHASH_CRC32B |
| MHASH_GOST |
| MHASH_HAVAL |
| MHASH_MD5 |
| MHASH_RIPEMD128 |
| MHASH_RIPEMD160 |
| MHASH_SHA1 |
| MHASH_TIGER |

# integer hash_count()

`hash_count` 函数返回哈希标识符。所有算法从零开始编号，因此你可以使用此函数和 `mhash_get_hash_name` 获取完整列表。

```php
<?php
print("<TABLE ORDER=\"1
```

# PHP 核心编程

```php
<?php
for($i=0; $i <= hash_count(); $i++) {
    print("<TR>\n");
    print("<TD>MHASH_" . mhash_get_hash_name($i) . "</TD>\n");
    print("<TD>" . mhash_get_block_size($i) . "</TD>\n");
    print("<TR>\n");
}
print("</TABLE>\n");
?>
```

# integer mhash_get_block_size(integer hash)

`get_block_size` 函数返回哈希算法的块大小。

# string mhash_get_hash_name(integer hash)

`get_hash_name` 函数返回特定哈希标识符名称。

# int similar_text(string left, string right, percentage)
