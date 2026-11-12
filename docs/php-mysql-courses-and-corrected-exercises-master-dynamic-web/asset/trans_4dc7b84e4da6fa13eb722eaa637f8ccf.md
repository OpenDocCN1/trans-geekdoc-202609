

| 函数 | 描述 | 示例 |
|---|---|---|
| abs() | 返回绝对值 | abs(-10) = 10 |
| sqrt() | 返回数字的平方根 | sqrt(25) = 5 |
| pow() | 返回数字的幂 | pow(2,3) = 8 |
| round() | 将数字四舍五入到最接近的小数位 | round(3.7) = 4 |

- **abs()**: 该函数返回数字的绝对值，即不带符号的值。例如：

```
$number = -10;

$absolute_value = abs($number); // $absolute_value is 10
```

- **sqrt()**: sqrt() 函数返回数字的平方根。例如：

```
$number = 25;

$square_root = sqrt($number); // square_root is 5
```

- **pow()**: 该函数返回一个数字提升到另一个数字幂次的值。例如：

```php
$number = 2;
$power = 3;
$result = pow($number, $power); // $result is 8 (2^3)
```

- **round()**: round() 函数根据指定精度将数字四舍五入到最接近的小数位。示例如下：

```php
<?php
$number1 = 3.7;
$arrondi_number1 = round($number1); // $arrondi is 4

$number2 = 12.146345;
$arrondi_number2 = round($number2, 2); // round $number2 to 2 decimal places, result is 12.15

echo $arrondi_number1;
echo "<br>";
echo $arrondi_number2;
?>
```

这些基本函数在许多需要对数字进行简单运算的编程场景中非常有用。它们为在 PHP 中执行基本数学计算提供了灵活性和易用性。

![](img/caba2aa22f5409ba73dea47176330677_235_0.png)

## 三角函数

在 PHP 中，集成了三角函数，以便开发者能够高效、准确地执行三角计算。下表概述了其中一些函数。

| 函数 | 描述 | 示例 |
|---|---|---|
| sin() | 返回以弧度表示的角度的正弦值 | sin(0.5) 返回 0.479（0.5 弧度的正弦） |
| cos() | 返回以弧度表示的角度的余弦值 | cos(1) 返回 0.540（1 弧度的余弦） |
| tan() | 返回以弧度表示的角度的正切值 | tan(0.8) 返回 1.029（0.8 弧度的正切） |
| asin() | 返回数字的反正弦值 | asin(0.5) 返回 0.523（0.5 的反正弦） |
| acos() | 返回数字的反余弦值 | acos(0.5) 返回 1.047（0.5 的反余弦） |
| atan() | 返回数字的反正切值 | atan(1) 返回 0.785（1 的反正切） |

## 随机函数

PHP 的随机函数可用于生成随机数并在应用程序中执行随机操作。它们广泛用于游戏、模拟、随机数据生成等领域。以下是 PHP 中一些最常用的随机函数：

### 随机数生成

- **rand($min, $max)**: 该函数在 $min 和 $max 值之间生成一个随机数。返回的值是整数。

### 示例：

```php
<?php
$random_number = rand(1, 100);
echo "Random number between 1 and 100: $random_number";
?>
```

每次运行此代码，您都会得到 1 到 100 之间的随机数。

- **mt_rand($min, $max)**: 与 rand() 类似，但使用 **Mersenne Twister** 随机数生成器，以其更好的随机数分布而闻名。

### 示例：

```php
<?php
$random_number = mt_rand(1000, 9999);
echo "Random 4-digit PIN code: $random_number";
?>
```

## 字符串函数

PHP 中的字符串函数提供了各种工具，可用于高效地操作和处理字符串。以下是此类别中一些最常用的函数：

**strlen()**: 该函数返回字符串的长度。

### 示例：

```php
<?php
$text = "Hello";
$length = strlen($text); // $length is 5
echo $length;
?>
```

### 结果

![](img/caba2aa22f5409ba73dea47176330677_239_0.png)

strpos(): 该函数返回子字符串在字符串中首次出现的位置。

### 示例：

```
$text = "Good morning";
$position = strpos($text, "mor"); // $position is 5
```

在此示例中，我们有一个包含值 "Good morning" 的字符串 "$text"。使用 "strpos()" 函数来查找子字符串 "mor" 在字符串 "$text" 中首次出现的位置。由于 "mor" 在 "Good morning" 中从第五个位置开始，因此 "strpos()" 函数返回值 5，即子字符串 "mor" 在字符串 "$text" 中的起始位置。请注意，位置索引从零开始。字母 "G" 的索引为 0，字母 "o" 的索引为 1，第二个字母 "o" 的索引为 2，字母 "d" 的索引为 3，空格的索引为 4，字母 "m" 的索引为 5。

### substr():

该函数从指定位置和长度返回给定字符串的子字符串。

### 示例：

```php
<?php
$text = "Hello everyone";
$substring = substr($text, 3, 10); // $substring is "lo everyone".
echo $substring;
?>
```

在此示例中，我们有一个包含值 "Hello everyone" 的字符串 "$text"。使用 "substr()" 函数从 "$text" 提取子字符串。函数的参数如下：第一个参数是原始字符串（"$text"），第二个参数是提取的起始位置（在我们的例子中是 3，即从字符串 $text 的第四个字符开始，因为索引从零开始），第三个参数是要提取的子字符串的长度（在我们的例子中是 10 个字符）。因此，"substr()" 函数从 "$text" 的第三个位置开始提取长度为十个字符的子字符串，得到 "lo everyone"。空格也是需要考虑的字符。

### 结果

![](img/caba2aa22f5409ba73dea47176330677_241_0.png)

strtoupper() 和 strtolower(): 这些函数分别将字符串转换为 **大写** 或 **小写**。

### 示例：

```php
<?php
$text = "Hello everyone";
$upper_text = strtoupper($text); // $upper_text is "HELLO EVERYONE".

$lower_text = strtolower($text); // $lower_text is "hello everyone".

echo $upper_text;
echo "<br>";
echo $lower_text;
?>
```

![](img/caba2aa22f5409ba73dea47176330677_242_0.png)

### str_replace():

该函数将字符串中子字符串的所有出现替换为另一个字符串。

### 示例：

```php
<?php
$text = "Hello everyone";
$new_text = str_replace("everyone", "friends", $text);
echo $new_text;
?>
```

在此代码中，str_replace() 函数将字符串 $text 中的字符串 "everyone" 替换为字符串 "friends"。如果运行此代码，您将得到以下结果：

![](img/caba2aa22f5409ba73dea47176330677_243_0.png)

简而言之，这些只是 PHP 中用于高效、灵活地操作字符串的众多函数中的几个示例。

## 数组函数

数组操作是 PHP 中的常见任务，语言提供的内置函数使其变得容易得多。以下是一些用于处理数组的最常用函数：

| 函数 | 含义 |
|---|---|
| count() | 计算数组中的元素个数 |
| sort() | 将数组按升序排序 |
| rsort() | 将数组按降序排序 |
| array_push() | 将一个或多个元素添加到数组末尾 |

| 函数 | 描述 |
|---|---|
| `array_unshift()` | 将一个或多个元素添加到数组开头 |
| `array_pop()` | 删除数组的最后一个元素 |
| `array_shift()` | 删除数组的第一个元素 |
| `array_slice()` | 提取数组的一部分 |
| `array_merge()` | 合并一个或多个数组 |
| `array_key_exists()` | 检查键是否存在于数组中 |
| `in_array()` | 检查给定值是否存在于数组中 |
| `array_search()` | 在数组中搜索给定值并返回相应的键 |
| `array_replace()` | 将数组的元素替换为一个或多个其他数组中的元素 |

- **sort()** 函数：按值对数组进行升序排序。它直接就地修改数组，并返回一个布尔值以指示操作是否成功。示例如下：

```php
<?php
$fruits = ["orange", "apple", "banana", "strawberry"];
sort($fruits);
?>
```

