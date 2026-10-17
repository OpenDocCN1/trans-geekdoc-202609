
```php
$n1 = 1;
$n2 = 2;
$sum = $n1 + $n2;
```

你可以将两个不同数据类型的数字相加，如下：

```php
$n1 = 1.5;
$n2 = 2;
$sum = $n1 + $n2;
```

PHP 将 `$n2` 转换为浮点数并将两个值相加。

### 算术运算符

PHP 提供了五种算术运算符：

| 运算符 | 说明 |
| :--- | :--- |
| `+` | 两个数字相加。 |
| `-` | 从第一个数字减去第二个数字。 |
| `*` | 两个数字相乘。 |
| `/` | 将第一个数字除以第二个数字。 |
| `%` | 求第一个数字除以第二个数字的余数。这被称为取模。 |

你可以一次执行多个算术运算。例如，运算的顺序很重要。PHP 先执行乘法和除法，然后执行加法和减法。因此，PHP 从左到右执行：

```php
$result = 1 + 2 * 4;
```

你可以通过括号改变算术运算的顺序。括号内的算术先执行。例如，你可以用括号写之前的语句：

```php
$result = (1 + 2) * 4;
```

### 将数字格式化为金额

通常你处理的数字是金额，例如产品价格。你希望客户在网页上以正确的格式看到价格。换句话说，金额应该始终保留两位。然而，PHP 以最高效率存储和显示数字。如果数字是 `10.00`，它会被显示为 `10`。为了将数字格式化，你可以使用 `sprintf`。以下语句将数字格式化为金额格式：

```php
$newvariablename = sprintf("%01.2f", $oldvariablename);
```

例如，以下语句以正确的格式显示金额：

```php
$price = 25;
$f_price = sprintf("%01.2f", $price);
echo "$f_price";
```

你在网页上看到：

```text
25.00
```

如果你用 `var_dump($f_price)` 显示变量，输出为 `string(5) "25.00"`。

如果你想在数字中使用逗号来分隔千分位，可以使用 `number_format`。以下语句创建了一个带有逗号的美元格式数字：

```php
$price = 25000;
$f_price = number_format($price, 2);
echo "$f_price";
```

你会在网页上看到以下内容：

```text
25,000.00
```

`number_format` 语句中的 `2` 将格式设置为保留两位小数。你可以使用任何数字来获取任意位数的小数。

## 处理字符串

## 第二部分：第一章

`character string`（字符字符串）是一系列字符。字符包括字母、数字和标点符号。当数字被用作字符时，它只是一个存储的字符，与字母相同。它不能用于算术运算。例如，`PHP Basics` 中的电话号码被存储为字符字符串，因为它只需要被存储——而不是进行加法或乘法。

### 将字符串赋值给变量

将字符字符串存储在变量中时，通过使用双引号或单引号告诉 PHP 字符串的开始和结束。例如，以下两个语句产生相同的结果：

```php
$string = "Hello World!";
$string = 'Hello World!';
```

假设你想要存储如下所示的字符串：

```php
$string = 'It is Sally\'s house';
echo $string;
```

这些语句无法工作，因为当 PHP 看到 Sally 后面的 `'`（单引号）时，它认为这是字符串的结束，从而显示以下内容：

```text
It is Sally
```

你需要告诉 PHP 将单引号（`'`）解释为撇号，而不是字符串的结束。你可以在单引号前面使用反斜杠（`\`）来实现这一点。反斜杠告诉 PHP 该单引号没有特殊含义；它只是一个撇号。这被称为字符*转义*（escaping）。使用以下语句显示整个字符串：

```php
$string = 'It is Sally\'s house';
echo $string;
```

同样，当你用双引号包裹字符串时，也必须在字符串中的任何双引号前面使用反斜杠。

### 在字符串中使用单引号和双引号

单引号字符串和双引号字符串的处理方式不同。单引号字符串是按字面意思存储的，`\'` 除外，后者会被存储为撇号。在双引号字符串中，变量和某些特殊字符在字符串存储之前会被求值。以下是代码中使用双引号或单引号时最重要的区别：

* **处理变量：** 如果你将变量包含在双引号中，PHP 将使用变量的值。然而，如果你将变量包含在单引号中，PHP 将使用字面变量名。例如，如果你使用以下语句：

```php
$month = 12;
$result1 = "$month";
$result2 = '$month';
echo $result1;
echo "<br />";
echo $result2;
```

输出为：

```text
12
$month
```

更多示例请参考本章前面的表 1-3。

* **换行：** 特殊字符 `\n` 告诉 PHP 开始换行。当你使用双引号时，PHP 在 `\n` 处换行；使用单引号时，`\n` 是字面字符串。例如，使用以下语句时：

```php
$string1 = "String\ndouble quotes";
$string2 = 'String\nsingle quotes';
```

`string1` 的输出是：

```text
String
double quotes
```

而 `string2` 的输出是：

```text
String\nsingle quotes
```

* **插入制表符：** 特殊字符 `\t` 告诉 PHP 插入一个制表符。当你使用双引号时，PHP 在 `\t` 处插入制表符，但使用单引号时，`\t` 是字面字符串。例如，使用以下语句时：

```php
$string1 = "String\tdouble quotes";
$string2 = 'String\tsingle quotes';
```

`string1` 的输出是：

```text
String	double quotes
```

而 `string2` 的输出是：

```text
String\tsingle quotes
```

包裹整个字符串的引号决定了变量和特殊字符的处理，即使字符串内部还有其他的引号。例如，看以下语句：

```php
$number = 10;
$string1 = "There are $number people in line.";
$string2 = 'There are $number people waiting.';
echo $string1, "<br />";
echo $string2;
```

输出如下：

```text
There are 10 people in line.
There are $number waiting.
```

### 连接字符串

你可以使用点（`.`）来连接字符串，这个过程被称为*拼接*（concatenation）。例如，你可以通过以下语句连接字符串：

```php
$string1 = 'Hello';
$string2 = 'World!';
$stringall = $string1 . $string2;
echo $stringall;
```

`echo` 语句的输出是 `HelloWorld!`。

注意 Hello 和 World 之间没有空格。这是因为在连接的两个字符串中没有包含空格。你可以通过连接语句而不是之前的语句在单词之间添加空格：

```php
$stringall = "Hello";
$stringall .= " World!";
echo $stringall;
```

echo 语句的输出是：

```text
Hello World!
```

你也可以拆分字符串。你可以在指定的字符处分离它们，或者在字符串中查找子字符串。你可以使用函数对字符串进行这些操作。我们将在第二章中介绍函数。

### 存储长字符串

PHP 提供了一种名为 `heredoc` 的功能，用于赋值跨多行的长字符串。`heredoc` 允许你指定从哪里开始和结束字符串。`heredoc` 语句的格式如下：

```php
$varname = <<<ENDSTRING
text
ENDSTRING;
```

`ENDSTRING` 是你想要的任何字符串。通过在开头和结尾输入 `ENDSTRING` 来将文本存储在变量 `$varname` 中。当 PHP 处理 `heredoc` 时，它读取第一个 `ENDSTRING` 并知道开始读取文本。它继续读取文本，直到遇到同一个 `ENDSTRING`。

此时，它结束字符串。由 `heredoc` 语句创建的字符串以类似于双引号的方式评估变量和特殊字符。

以下语句使用 `heredoc` 方法创建字符串：

```php
$distance = 10;
$herevariable = <<<ENDOFTEXT
The distance between
Los Angeles and Pasadena
Is $distance miles.
ENDOFTEXT;
echo $herevariable;
```

echo 语句的输出如下：

```text
The distance between Los Angeles and Pasadena is 10 miles.
```

但要注意，PHP 对 `ENDSTRING` 非常挑剔。当它第一次出现时，`ENDSTRING`（在本例中为 ENDOFTEXT）必须出现在行末尾，后面不能有任何内容，甚至是空格。而最后一行的 `ENDSTRING` 必须出现在行的开头，前面不能有任何内容，甚至是空格，除了分号外不能有任何内容。如果违反了这些规则，PHP 将无法识别结束字符串，并在整个脚本中继续寻找。它最终会显示一个解析错误，行号为脚本的最后一行。

## 处理布尔类型

布尔数据类型只有 `true` 或 `false` 两个值。你可以如下所示给变量赋值布尔值：

```php
$var1 = true;
```

PHP 将变量设置为布尔数据类型。布尔值用于在条件语句（如 `if` 语句）比较值和表达式。比较值将在本手册第二章中详细讨论。

### PHP Basics

以下值被 PHP 评估为假：

* 单词 `false`
* 整数 `0`
* 浮点数 `0.0`
* 一个空字符串
* 值为 `0` 的字符串
* 一个空数组
* 一个空对象
* `NULL` 值

如果变量包含的值不被求值为假（false），则它被赋值为值 `true`。

## 使用 NULL 数据类型

唯一属于 `NULL` 数据类型的值是 `NULL`。你可以按照如下方式将该值赋值给变量：

```php
$var1 = NULL;
```

带有 `NULL` 值的变量不包含任何值。

## 使用数组

数组是复杂的变量。一个 `array` 在单个变量名下存储一组值。数组适用于存储相关的值。例如，你可以在一个名为 `$flowerinfo` 的单个数组中存储有关花卉的信息（如品种、颜色和成本）。数组中的信息可以很方便地处理、访问和修改。例如，PHP 有多种方法可以对数组进行排序。接下来的章节将为你介绍数组的详细信息。

### 创建数组

创建数组简单的方法是在变量名末尾加上方括号 `[]` 并为其赋值一个值。例如，假设你在脚本之前的任何地方都没有引用过 `$cities`，以下语句将创建一个名为 `$cities` 的数组：

```php
$cities[1] = "Phoenix";
```

此时，名为 `$cities` 的数组已经创建，并且它只有一个值：Phoenix。接下来，你使用以下语句：

```php
$cities[2] = "Tucson";
$cities[3] = "Flagstaff";
```

现在，数组 `$cities` 包含了三个值：Phoenix、Tucson 和 Flagstaff。

数组可以被视为 `key/value pairs`（键值对）列表。每个键值对被称为 `element`（元素）。要获取特定的值，你需要在括号中指定 `key`（键）。在前面的数组中，键是数字——1、2 和 3。然而，你也可以使用单词作为键。例如，以下语句创建了一个州首的数组：

```php
$capitals['CA'] = "Sacramento";
$capitals['TX'] = "Austin";
$capitals['OR'] = "Salem";
```

你可以使用快捷方法，而不是为每个数字编写单独的赋值语句。其中一种快捷方法使用以下语句：

```php
$cities[] = "Phoenix";
$cities[] = "Tucson";
$cities[] = "Flagstaff";
```

当你使用这种快捷方法创建数组时，值会自动分配从数字 0 开始的序列号作为键。例如，以下语句

```php
echo "$cities[0]";
```

会输出 Phoenix。

在带有数字索引的数组中，第一个值的索引是 0，除非你刻意将其设置为不同的数字。在处理数组时，一个常见的错误是将第一个数字认为是 1 而不是 0。

一个更快捷方法是使用以下语句：

```php
$cities = array("Phoenix", "Tucson", "Flagstaff");
```

该语句创建了与前面的快捷方法相同的数组，并且带有数字索引的键。你可以使用类似的语句来创建以单词作为键的数组。例如，以下语句创建了州首的数组：

```php
$capitals = array("CA" => "Sacramento", "TX" => "Austin", "OR" => "Salem");
```

### 查看数组

你可以像这样输出数组值：

```php
echo $capitals['TX'];
```

如果你在一个由双引号括的较长的 echo 语句中包含数组值，你可能需要将数组值的名称括在大括号中：`echo "The capital of Texas is {$capitals['TX']}<br />"`。你可以通过 `print_r` 或 `var_dump` 语句查看任何数组的结构和值。要显示 `$capitals` 数组，可以使用以下语句之一：

```php
print_r($capitals);
var_dump($capitals);
```

此 `print_r` 语句提供了如下输出：

```text
Array
(
    [CA] => Sacramento
    [TX] => Austin
    [OR] => Salem
)
```

`var_dump` 语句提供了如下输出：

```text
array(3) {
  ["CA"]=>string(10) "Sacramento"
  ["TX"]=>string(6) "Austin"
  ["OR"]=>string(5) "Salem"
}
```

`print_r` 输出显示数组中每个元素的键和值。`var_dump` 输出显示数据类型以及键和值。

当你在 Web 页面上显示 `print_r` 或 `var_dump` 的输出时，它是以 HTML 格式显示的，这意味着它显示为一长行。为了在 Web 上以我们在这里描述的有用格式查看输出，可以使用以下语句发送 HTML 标签，告诉浏览器按接收到的内容显示文本而不进行更改：

```php
echo "<pre>";
print_r($capitals);
echo "</pre>";
```

### 从数组中删除值

有时你需要完全从数组中删除一个元素。例如，假设你有如下一个包含五个元素的数组：

```php
$cities[0] = "Phoenix";
$cities[1] = "Tucson";
$cities[2] = "Flagstaff";
$cities[3] = "Tempe";
$cities[4] = "Prescott";
```

现在你决定不再想包含 Tempe，因此你使用以下语句尝试从数组中移除 Tempe：`$cities[3] = "";`。

尽管此语句将 `$cities[3]` 设置为空字符串，但它并没有从数组中删除该元素。你仍然拥有一个包含五个元素的数组，但五个值中的一个是空的。要从数组中完全删除该元素，你需要使用以下语句用 `unset` 取消它：

```php
unset($cities[3]);
```

现在你的数组只有四个元素了，如下：

```php
$cities[0] = "Phoenix";
$cities[1] = "Tucson";
$cities[2] = "Flagstaff";
$cities[4] = "Prescott";
```

## 排序数组

数组最常用的特性之一是 PHP 可以为它们进行排序。

PHP 最初按照你创建元素的顺序存储数组元素。

如果你在不改变顺序的情况下显示整个数组，元素将按照你创建它们的顺序进行显示。通常，你想要更改这种顺序。例如，你可能想按值或按键按字母顺序显示数组。

PHP 可以通过多种方式对数组进行排序。要对数字为键的数组进行排序，使用如下 `sort` 语句：

```php
sort($cities);
```

该语句对值进行排序并分配新的数字键。数字在前，大写字母在后，小写字母最后。例如，考虑前面提到的 `$cities` 数组：

```php
$cities[0] = "Phoenix";
$cities[1] = "Tucson";
$cities[2] = "Flagstaff";
```

在执行以下 `sort` 语句后：

数组变为

```php
$cities[0] = "Flagstaff";
$cities[1] = "Phoenix";
$cities[2] = "Tucson";
```

如果你使用 `sort()` 对以单词作为键的数组进行排序，键将变为数字，单词键将被丢弃。

要对以单词作为键的数组进行排序，使用 `asort` 语句。该语句按值对数组进行排序并为每个值保留原始键。例如，考虑前面提到的州首数组：

```php
$capitals['CA'] = "Sacramento";
$capitals['TX'] = "Austin";
$capitals['OR'] = "Salem";
```

在执行以下 `asort` 语句后：

数组变为：
