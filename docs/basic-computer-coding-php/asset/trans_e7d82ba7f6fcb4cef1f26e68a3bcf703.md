

# 知识检查

- 1. PHP 是 ............ 脚本语言的一个示例。
- a. 服务端
- b. 客户端
- c. 浏览器端
- d. 内部
- 2. 下列逻辑运算符中哪个的优先级更高？
- a. &&
- b. !
- c. ||
- d. xor
- 3. 哪些运算符的优先级更高？
- a. 算术运算符
- b. 比较运算符
- c. 逻辑运算符
- d. 布尔运算符
- 4. 递减运算符表示为
- a. ++
- b. --
- c. %%
- d. //
- 5. 比较运算符的优先级高于
- a. 算术运算符
- b. 赋值运算符
- c. 布尔运算符
- d. 以上所有

# 复习题

1. 什么是数据类型？
2. 如何在 php 中使用算术运算符？
3. 讨论字符串运算符。
4. 解释逻辑运算符。
5. 讨论流程控制语句。

# 检查你的结果

- 1. (a) 2. (b) 3. (a) 4. (b) 5. (b)

# 参考

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

# PHP 函数

> “社交媒体网站已不再履行预想的在朋友、家人和专业人士之间建立积极交流链接的功能。它是一个真正的战场，侮辱从人类箭袋中飞出，伤害了生活，摧毁了自尊心和个人的价值感”

> —Anthony Carmona

# 学习目标

学习完本章后，你将能够：

- 讨论 PHP 中的函数
- 解释 CPU 使用信息
- 理解序列化

# 引言

函数是一块代码，在声明后，可以从脚本的任何位置被调用。它本质上是一个模块化的 PHP 脚本，旨在完成单一任务。此外，函数内部包含的代码在脚本的其他部分调用该函数之前会被忽略。函数是极有益益的，因为它们有助于实现快速、可靠且减少错误的编码，并通过整理复杂的代码序列来增加代码的可读性。

# 3.1 PHP 中的函数

函数是更大型程序中的一段代码。该函数执行特定任务。使用函数的优势是：

- 减少代码重复
- 将复杂问题分解为更简单的部分
- 提高代码的清晰度
- 代码复用
- 信息隐藏

函数有两种基本类型：内置函数和用户定义函数。内置函数是 PHP 语言的一部分。例如：`phpinfo()`、`round()` 或 `abs()`。用户定义函数由程序员创建以满足他们的需求。它们使用 `function` 关键字创建。

# 3.1.1 PHP 定义函数

函数使用 `function` 关键字创建。
simple.php

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
$php simple.php
is PHP 5.9.14
在这里我们看到了脚本的输出。

# 3.1.2 PHP Return 关键字

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

# 3.1.3 PHP 参数

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
php，`power()` 函数接受一个参数 `$c`，代表摄氏温度。
在我们的示例中，我们将华氏度转换为摄氏度。

# 3.1.4 PHP 隐式值

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

# 3.1.5 PHP 可变参数

函数可以接受任意数量的参数。也就是说，有时我们不知道会有多少参数传递给函数。`func_get_args()` 函数返回函数的参数列表。从 PHP 5.6 开始，可以使用 `...` 运算符来创建变变函数。

variable_arguments.php
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

$sum = 0;
foreach ($args as $n) {
  $sum += $n;
}
return $sum;
我们计算并返回这些值的和。
echo sum(1, 2, 3) . "\n";
echo sum(1, 2, 3, 4) . "\n";
echo sum(1, 2, 3, 4, 5) . "\n";
我们向 `sum()` 函数传递了三个、四个和五个值。

6
10
15
这是输出。

variable_arguments2.php
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

# 3.1.6 PHP 静态变量

静态变量是静态分配的变量，其生命周期贯穿整个程序的运行。默认的局部变量在连续的函数调用中不会保留其值。

