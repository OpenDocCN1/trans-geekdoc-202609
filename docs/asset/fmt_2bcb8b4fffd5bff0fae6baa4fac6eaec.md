
我们有一个包含一周期的数组。我们想要打印该数组中的所有日期。

`$len = count($days);`

或者我们可以通过程序计算数组中的项数。

```php
for ($i = 0; $i < $len; $i++) {
    echo $days[$i], "\n";
}
```

## 基础计算机编程：PHP

这里我们有了 `for` 循环结构。三个阶段由分号隔开。首先初始化计数器 `$i`。初始化部分只发生一次。接下来进行测试。如果测试结果为真，则执行语句。最后，计数器递增。这是一个周期。`for` 循环一直迭代直到测试表达式为假。

```
$ forloop.php
Monday
Tuesday
Wednesday
Thursday
Friday
Saturday
Sunday
```
这是 `forloop.php` 的输出。

### 2.3.5 PHP foreach

`foreach` 简化了数组的遍历。它没有显式的计数器。它遍历数组元素。

```php
foreach.php
<?php
$seasons = ["Spring", "Summer", "Autumn", "Winter"];
foreach ($seasons as $val) {
    echo "$val\n";
}
?>
```

`foreach` 循环允许遍历数组元素。在处理数组时，它比 `while` 循环更方便。

```php
<?php
$fruits = ["apple", "banana", "cherry"];
foreach ($fruits as $fruit) {
    echo $fruit\n";
}
?>
```

`foreach` 循环也可以用于获取数组元素的键和值。

```php
<?php
$seasons = ["Spring", "Summer", "Autumn", "Winter"];
foreach ($seasons as $key => $val) {
    echo "$key => $val\n";
}
?>
```

### 2.3.6 PHP Break, Continue 语句

`break` 语句用于跳出循环。`continue` 语句用于跳过周期的剩余部分。

```php
testbreak.php
<?php
while (true) {
    $val = rand(1, 30);
    echo $val, " ";
    if ($val == 22) {
        break;
    }
}
echo "\n";
?>
```

```
$ php testbreak.php
6 13 5 21 9 22
```
这是脚本的输出。

在下面的示例中，我们打印不能被 2 除除的数字。

```php
testcontinue.php
<?php
$num = 0;
while ($num < 1000) {
    $num++;
    if ($num % 2 == 0) {
        continue;
    }
    echo "$num ";
}
echo "\n";
?>
```

```
$ php testcontinue.php
1 3 5 7 9 ...
```

## 知识检查

- 1. PHP 是 ............ 脚本语言的一个示例。
  - a. 服务端
  - b. 客户端
  - c. 浏览器端
  - d. 内部
- 2. 下列逻辑运算符中哪个的优先级更高？
  - a. `&&`
  - b. `!`
  - c. `||`
  - d. `xor`
- 3. 哪些运算符的优先级更高？
  - a. 算术运算符
  - b. 比较运算符
  - c. 逻辑运算符
  - d. 布尔运算符
- 4. 递减运算符表示为
  - a. `++`
  - b. `--`
  - c. `%%`
  - d. `//`
- 5. 比较运算符的优先级高于
  - a. 算术运算符
  - b. 赋值运算符
  - c. 布尔运算符
  - d. 以上所有

## 复习题

1. 什么是数据类型？
2. 如何在 php 中使用算术运算符？
3. 讨论字符串运算符。
4. 解释逻辑运算符。
5. 讨论流程控制语句。

## 检查你的结果

- 1. (a) 2. (b) 3. (a) 4. (b) 5. (b)

## 参考

- 1. http://php.net/manual/en/intro-whatis.php
- 2. http://www.siteforinfotech.com/different-types-php-operators/
- 3. http://www.zentout.com/php-tutorial/php-operators/
- 4. https://docstore.mik.ua/orelly/webprog/php/ch02_05.htm
- 5. https://www.guru99.com/data-types-variables-and-operators.html
- 6. https://www.guru99.com/what-is-first-php-program.html
- 7. https://www.tutorialspoint.com/php/php-operator_types.php
- 8. https://www.tutorialspoint.com/php/php_operator_types.htm
- 9. https://www3.ntu.edu.sg/home/ehchua/programming/java/datarerepresentation.html
- 10. Lendorf, Rasmus (1995-06-08). “Announce: Personal Home Page Tools (PHP Tools)”. Newsgroup: comp.infosystems. www.authoring.cgi. Retrieved 2006-09-17.
- 11. php.net 2007 cgi archive. The PHP Group. 2007-07-13. Retrieved 2008-02-22.
- 12. Variable functions (PHP manual). php.net. 2014-07-04. Retrieved 2014-07-07.

```php
$string1 = "This is Sublime Text Editor.";
$string2= preg_replace("/Sublime/", '<h2>Sublime</h2>', $string);
echo $string1;
echo "<br>";
echo $bcompiler_read
echo $sevent_buffer_read
maxdb_bind_result
mysqli_bind_result
enchant_broker_request_dict
enchant_broker_request_pwl_d...
aggregate_methods_by_regexp
```

# 第3 章

### PHP 函数

> “社交媒体网站已不再履行预想的在朋友、家人和专业人士之间建立积极交流链接的功能。它是一个真正的战场，侮辱从人类箭袋中飞出，伤害了生活，摧毁了自尊心和个人的价值感”

> —Anthony Carmona

### 学习目标

学习完本章后，你将能够：

- 讨论 PHP 中的函数
- 解释 CPU 使用信息
- 理解序列化

### 引言

函数是一块代码，在声明后，可以从脚本的任何位置被调用。它本质上是一个模块化的 PHP 脚本，旨在完成单一任务。此外，函数内部包含的代码在脚本的其他部分调用该函数之前会被忽略。函数是极有益益的，因为它们有助于实现快速、可靠且减少错误的编码，并通过整理复杂的代码序列来增加代码的可读性。

### 3.1 PHP 中的函数

函数是更大型程序中的一段代码。该函数执行特定任务。使用函数的优势是：

- 减少代码重复
- 将复杂问题分解为更简单的部分
- 提高代码的清晰度
- 代码复用
- 信息隐藏

函数有两种基本类型：内置函数和用户定义函数。内置函数是 PHP 语言的一部分。例如：`phpinfo()`、`round()` 或 `abs()`。用户定义函数由程序员创建以满足他们的需求。它们使用 `function` 关键字创建。

#### 3.1.1 PHP 定义函数

函数使用 `function` 关键字创建。
`simple.php`

```php
<?php
function displayVersion() {
    echo "this is PHP " . phpversion();
    echo "\n";
}
displayVersion();
?>
```

`function` 关键字后面跟着带有圆括号的函数名。函数体位于大括号之间。我们称这为“调用”一个函数。如果我们调用一个函数，函数体内部的语句就会执行。

这行代码调用了该函数。
```
$php simple.php
is PHP 5.9.14
```
在这里我们看到了脚本的输出。

#### 3.1.2 PHP Return 关键字

`return` 关键字用于从函数返回一个值。函数可以返回一个值，也可以不返回。

```php
<?php
function maximum($x, $y) {
    if ($x > $y) {
        return $x;
    } else {
        return $y;
    }
}
$a = 3;
$b = 2;
$val = maximum($a, $b);
echo "The max of $a and $b is $val\n";
?>
```

#### 3.1.3 PHP 参数

大多数函数都接受参数。参数是发送给函数的值。函数处理这些值并可能返回某些结果。

```php
<?php
function power($c) {
    return $c * $c;
}
echo power(5);
echo "\n";
echo power(10);
echo "\n";
echo power(0);
echo "\n";
echo power(30);
echo "\n";
?>
```
`php`，`power()` 函数接受一个参数 `$c`，代表摄氏温度。
在我们的示例中，我们将华氏度转换为摄氏度。

#### 3.1.4 PHP 隐式值

PHP 函数的参数具有隐式值。如果没有提供值，则使用隐式值。

```php
<?php
function power($a, $b=2) {
    $value = 1;
    for ($si = 0; $si < $b; $si++) {
        $value *= $a;
    }
    return $value;
}
$v1 = power(5);
$v2 = power(5, 4);
echo "5^2 is $v1\n";
echo "5^4 is $v2\n";
?>
```
在这里我们创建了一个函数。该函数有一个隐式值参数。

#### 3.1.5 PHP 可变参数

函数可以接受任意数量的参数。也就是说，有时我们不知道会有多少参数传递给函数。`func_get_args()` 函数返回函数的参数列表。从 PHP 5.6 开始，可以使用 `...` 运算符来创建变变函数。

`variable_arguments.php`
```php
<?php
function sum(...$nums) {
  $sum = 0;
  foreach ($nums as $n) {
    $sum += $n;
  }
  return $sum;
}
echo sum(1, 2, 3) . "\n";
echo sum(1, 2, 3, 4) . "\n";
echo sum(1, 2, 3, 4, 5) . "\n";
?>
```
我们创建了一个 `sum()` 方法，它可以接受任意数量的参数。该方法计算传递给方法的值的和。

```
$sum = 0;
foreach ($args as $n) {
  $sum += $n;
}
return $sum;
```
我们计算并返回这些值的和。
```
echo sum(1, 2, 3) . "\n";
echo sum(1, 2, 3, 4) . "\n";
echo sum(1, 2, 3, 4, 5) . "\n";
```
我们向 `sum()` 函数传递了三个、四个和五个值。

```
6
10
15
```
这是输出。

`variable_arguments2.php`
```php
<?php
function sum() {
    $args = func_get_args();
    $sum = 0;
    foreach ($args as $n) {
        $sum += $n;
    }
    return $sum;
}
echo sum(1, 2, 3) . "\n";
echo sum(1, 2, 3, 4) . "\n";
echo sum(1, 2, 3, 4, 5) . "\n";
?>
```
现在我们使用 `func_get_args()` 函数创建了相同的示例。

#### 3.1.6 PHP 静态变量

静态变量是静态分配的变量，其生命周期贯穿整个程序的运行。默认的局部变量在连续的函数调用中不会保留其值。

#### non_static.php

静态变量（Static Variable）是被“静态”分配的变量，这意味着它的生命周期（或“范围”）是整个程序运行期间。

```php
<?php
function nonstatic() {
  $value = 0;
  $value += 1;
  return $value;
}
nonstatic();
nonstatic();
nonstatic();
nonstatic();
echo nonstatic(), "\n";
?>
```

在上面的示例中，我们有一个普通的非静态变量。每次调用函数时，我们都会增加该变量的值。我们调用了 5 次函数。然而，非静态变量在每次调用函数时都会初始化。在调用 5 次函数后，`$value` 的值等于 2。
静态变量只在函数第一次被调用时初始化一次。此后它们会保留自己的值。

#### static.php

```php
<?php
function staticfun() {
static $value = 0;
$value += 1;
return $value;
}
staticfun();
staticfun();
staticfun();
staticfun();
echo staticfun(), "\n";
?>
```

在连续调用 5 次后，`$value` 的值等于 5。

```
$ php nonstatic.php
2
$ php static.php
6
```

#### 3.1.7 PHP 匿名函数

匿名函数没有名字。
`anonymous.php`

```php
<?php
$var = function() {
echo "This is anonymous function\n";
};
$var();
```

### PHP 函数

我们将一个函数体赋值给一个变量。只能通过这个变量来调用函数。

```php
$var = function () {
echo "This is anonymous function\n";
};
```

注意闭合括号后面的分号。这是必须的，因为该结构是一个赋值语句。

```bash
$ php anonymous.php
This is anonymous function
```

这是示例的输出结果。

### 记忆

函数名必须以字母或下划线开头，不能以数字开头，后面可以跟跟更多的字母、数字或下划线。函数名不区分大小写。

#### 3.1.8 值传递和引用传递

PHP 支持两种向函数传递参数的方式。默认方式是按值传递。当我们按值传递参数时，函数仅与值的副本进行操作。在处理大量数据时，这可能会导致性能开销。

当我们按引用传递值时，函数接收的是实际值的引用。修改时，原始值会受到影响。这种传递值的方式在时间和空间上效率更高。另一方面，它更容易出错。

我们应该使用哪种参数传递？这取决于情况。假设我们有一组数据，员工的工资。如果我们想计算某些数据的统计信息，不需要修改它们，那么就按值传递。如果我们处理大量数据且计算速度至关重要，就按引用传递。如果我们想修改数据，例如对工资进行某些削减或增加，我们可能会使用引用传递。
以下两个示例涵盖了这两个概念。

![](img/f8aa82c4ef45031ca4eadc2bb946c87a_89_0.png)

1993年，伊利诺伊大学厄巴纳夏槟分校的国家超级计算机应用中心（NCSA）发布了 NCSA Mosaic，这是第一个流行的图形化 浏览器，它在推动新生世界 Web 的增长方面发挥了重要作用。

```php
swap1.php
<?php
function swap($a, $b) {
    $temp = $a;
    $a = $b;
    $b = $temp;
    echo "inside swap function:\n";
    echo "\$a is $a \n";
    echo "\$b is $b \n";
    $a = 4;
    $b = 7;
    echo "outside swap function:\n";
    echo "\$a is $a \n";
    echo "\$b is $b \n";
    swap($a, $b);
    echo "outside swap function:\n";
    echo "\$a is $a \n";
    echo "\$b is $b \n";
}
?>
```
