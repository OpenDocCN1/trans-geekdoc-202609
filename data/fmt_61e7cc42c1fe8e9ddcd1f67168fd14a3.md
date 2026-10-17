
作为连接演示，将创建一个新变量——`$author`——作为两个现有字符串及中间一个空格的连接结果。

### 3. 更改 `echo` 语句以使用此新变量：

```php
echo "<p>The book <em>$book</em> was written by $author.</p>";
```

由于这两个变量已合二为一，因此应相应地修改 `echo` 语句。

### 4. 如有需要，更改 HTML 页面标题以及名、姓和书名变量的值。

### 5. 将文件保存为 `concat.php`，放入 Web 目录，并在 Web 浏览器中测试。

***

### Tip

PHP 拥有大量实用的字符串专用函数，您将在本书中逐一见到。例如，要计算字符串的长度（包含多少字符），请使用 `strlen()`：

```php
$num = strlen('some string'); // 11
```

***

### Tip

您可以使用以下函数让 PHP 转换字符串的大小写：`strtolower()` 将其全部转为小写；`strtoupper()` 将其全部转为大写；`ucfirst()` 将首字符大写；`ucwords()` 将每个单词的首字符大写。

***

### Tip

如果只是将一个值连接到另一个值后面，可以使用连接赋值运算符 (`.=`) 。以下两种写法等效：

```php
$title = $title . $subtitle;
$title .= $subtitle;
```

***

### Tip

本节开头的示例可改写为以下任意一种形式：

```php
$address = "$city, $state";
```

或

```php
$address = $city;
$address .= ', ';
$address .= $state;
```

***

### 使用 PHP 手册

PHP 手册——可在线访问 **[www.php.net/manual](http://www.php.net/manual)**——列出了该语言的每个函数和特性。手册首先讨论一般概念（安装、语法、变量），最后按主题分类列出函数（MySQL、字符串函数等）。

要在 PHP 手册中快速查找任意函数，请在 Web 浏览器中访问 **[www.php.net/`functionname`](http://www.php.net/)**（例如 **[www.php.net/print](http://www.php.net/print)**）。手册针对每个函数均指明：

*   该函数可用的 PHP 版本。
*   函数接受的参数个数及类型（可选参数用方括号括起）。
*   函数的返回值类型。

手册还包含函数的说明。

您应养成习惯：每当对某函数感到困惑、不确定如何正确使用，或需要深入了解语言的任何特性时，都去查阅 PHP 手册。了解您正在运行的 PHP 版本也至关重要，因为函数和 PHP 的其他细节会随时间变化。

***

### 数字简介

在介绍变量时，我提到 PHP 同时拥有整型和浮点型（小数）两种数字类型。但根据我的经验，这两种类型在大多数情况下均可归类为通用的“数字”，而不会丢失任何有价值的区别。PHP 中合法的数字类型变量可以是：

*   8
*   3.14
*   10980843985
*   -4.2398508
*   4.4e2

请注意，这些值从不加引号——加引号的数字是具有数值的字符串——也不包含用于表示千位的逗号。此外，除非前面有减号 (`-`)，否则数字默认为正数。

除了可以对数字使用标准算术运算符（**表 1.1**）外，PHP 还内置了数十个函数。其中两个常用函数是 `round()` 和 `number_format()`。前者将小数四舍五入为最接近的整数：

```php
$n = 3.14;
$n = round($n); // 3
```

**表 1.1. 算术运算符**

![Image](img/01tab01.jpg)

`round()` 也可四舍五入到指定的小数位数：

```php
$n = 3.142857;
$n = round($n, 3); // 3.143
```

`number_format()` 函数将数字转换为更常见的书写形式，即使用逗号分隔千位：

```php
$n = 20943;
$n = number_format($n); // 20,943
```

该函数也可设置指定的小数位数：

```php
$n = 20943;
$n = number_format($n, 2); // 20,943.00
```

为了练习数字操作，让我们编写一个模拟脚本，执行电子商务购物车中可能用到的计算。

#### 使用数字

### 1. 在文本编辑器或 IDE 中新建一个 PHP 文档，命名为 `numbers.php`（**脚本 1.8**）：

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
  <title>Numbers</title>
</head>
<body>
<?php # Script 1.8 - numbers.php
```

### 2. 建立所需变量：

```php
$quantity = 30;
$price = 119.95;
$taxrate = .05;
```

本脚本将使用三个硬编码变量进行计算。稍后您将看到如何动态确定这些值（即通过用户与 HTML 表单的交互）。

### 3. 执行计算：

```php
$total = $quantity * $price;
$total = $total + ($total * $taxrate);
```

第一行将订单总额设为购买的部件数量乘以单价。第二行再加上税额（通过税率乘以总额计算得出）。

**脚本 1.8.** `numbers.php` 脚本执行基本数学计算，如电子商务应用中所用。

***

```php
1   <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML
       1.0 Transitional//EN" "http://www.w3.org/
       TR/xhtml1/DTD/xhtml1-transitional.dtd">
2   <html xmlns="http://www.w3.org/1999/
       xhtml" xml:lang="en" lang="en">
3   <head>
4       <meta http-equiv="Content-Type"
            content="text/html; charset=utf-8" />
5       <title>Numbers</title>
6   </head>
7   <body>
8   <?php # Script 1.8 - numbers.php

9   // Set the variables:
10  $quantity = 30; // Buying 30 widgets.
11  $price = 119.95;
12  $taxrate = .05; // 5% sales tax.

13  // Calculate the total:
14  $total = $quantity * $price;
15  $total = $total + ($total * $taxrate);
       // Calculate and add the tax.

16  // Format the total:
17  $total = number_format($total, 2);

18  // Print the results:
19  echo '<p>You are purchasing <b>' .
       $quantity . '</b> widget(s) at a cost
       of <b>$' . $price . '</b> each. With
       tax, the total comes to <b>$' .
       $total . '</b>.</p>';

20  ?>
21  </body>
22  </html>
```

***

### 4. 格式化总额：

```php
$total = number_format($total, 2);
```

`number_format()` 函数将总额按千位分组并四舍五入到两位小数。应用此函数可正确格式化计算值。

### 5. 输出结果：

```php
echo '<p>You are purchasing <b>' . $quantity . '</b> widget(s) at a cost of <b>$' . $price . '</b> each. With tax, the total comes to <b>$' . $total . '</b>.</p>';
```

脚本的最后一步是输出结果。`echo` 语句结合单引号文本和连接的变量，以输出 HTML、美元符号和变量值的完整组合。本章最后一个示例将展示另一种方法。

### 6. 完成 PHP 代码和 HTML 页面：

```php
?>
</body>
</html>
```

### 7. 将文件保存为 `numbers.php`，放入 Web 目录，并在 Web 浏览器中测试。

![Image](img/01_figure_16_a.jpg)

数字 PHP 页面（脚本 1.8）根据设定的值执行计算。

**8.** 如果需要，更改最初的三个变量并重新运行脚本。

![Image](img/01_figure_17_b.jpg)

要更改生成的网页，请更改任意或所有三个变量（与 ![Image](img/graycircle-a.jpg) 对比）。

***

**提示**

在大多数平台上，PHP 支持的最大整数约为二十亿。对于大于该值的数字，PHP 将自动使用浮点类型。

***

**提示**

在处理算术运算时，*优先级* 问题会出现（复杂计算的执行顺序）。虽然 PHP 手册和其他资料倾向于列出优先级的层级，但我发现将子句放在括号中以强制执行顺序会使编程更安全、更易读（请参阅 脚本 1.8 的第 17 行）。

***

**提示**

计算机以处理小数著称不精。例如，数字 2.0 实际上可能被存储为 1.99999。大多数情况下这不会构成问题，但在数学精度至关重要的情况下，请依赖整数，而非小数。PHP 手册中有关于此主题的信息，以及用于提高计算精度的替代函数。

***

**提示**

许多数学运算符也有对应的赋值运算符，允许你创建赋值的简写。这一行代码，

```php
$total = $total + ($total * $taxrate);
```

可以重写为

```php
$total += ($total * $taxrate);
```

***

**提示**

如果你设置 `$price` 值时未使用两位小数（例如 119.9 或 34），你会想要在打印前对 `$price` 应用 `number_format()`。

***

### 介绍常量

常量与变量一样，用于临时存储值，但除此之外，常量和变量在许多方面有所不同。首先，要创建常量，你需要使用 `define()` 函数，而不是赋值运算符（`=`）：

```php
define ('NAME', value);
```

请注意，根据经验法则，常量名称通常使用全大写，尽管这不是强制要求。最重要的是，常量不像变量那样使用初始美元符号（因为常量不是变量）。

常量只能被赋予 *标量* 值，如字符串或数字：

```php
define ('USERNAME', 'troutocity');  
define ('PI', 3.14);
```

与变量不同，常量的值一旦定义就不能更改。

要访问常量的值（例如当你想打印它时），不能将常量放在引号内：

```php
echo "Hello, USERNAME"; // 不会生效！
```

使用该代码，PHP 会按字面意思打印 *Hello, USERNAME*，而不是 `USERNAME` 常量的值（因为没有迹象表明 `USERNAME` 不是字面文本）。相反，要么单独打印常量：

```php
echo 'Hello, ';  
echo USERNAME;
```

![Image](img/01_figure_18_a.jpg)

常量不能放在带引号的字符串中。

要么使用连接运算符：

```php
echo 'Hello, ' . USERNAME;
```

PHP 运行时带有几个预定义常量，这很像本章前面使用的预定义变量。这些常量包括 `PHP_VERSION`（正在运行的 PHP 版本）和 `PHP_OS`（服务器的操作系统）。下一个脚本将打印这两个值，以及用户定义常量的值。

**脚本 1.9.** 常量是你可以在 PHP 中使用的另一种临时存储工具，区别于变量。

***

```php
1   <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML  
    1.0 Transitional//EN" "http://www.w3.org/  
    TR/xhtml1/DTD/xhtml1-transitional.dtd">  
2   <html xmlns="http://www.w3.org/1999/  
    xhtml" xml:lang="en" lang="en">  
3   <head>  
4       <meta http-equiv="Content-Type"  
            content="text/html; charset=utf-8" />  
5       <title>Constants</title>  
6   </head>  
7   <body>  
8   <?php # Script 1.9 - constants.php  
9   
10  // Set today's date as a constant:  
11  define ('TODAY', 'March 16, 2011');  
12   
13  // Print a message, using predefined  
        constants and the TODAY constant:  
14  echo '<p>Today is ' . TODAY . '.<br />  
        This server is running version <b>' .  
        PHP_VERSION . '</b> of PHP on the <b>' .  
        PHP_OS . '</b> operating system.</p>';  
15   
16  ?>  
17  </body>  
18  </html>
```

***

#### 使用常量

**1.** 在文本编辑器或 IDE 中开始一个新的 PHP 文档，命名为 `constants.php`（**脚本 1.9**）。

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">  
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">  
<head>  
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />  
  <title>Constants</title>  
</head>  
<body>  
<?php # Script 1.9 - constants.php
```

**2.** 创建一个新的日期常量：

```php
define ('TODAY', 'March 16, 2011');
```

这是一个公认微不足道的常量用法，但这个例子将说明要点。在第 9 章“将 PHP 与 MySQL 结合使用”中，你将看到如何使用常量来存储数据库访问信息。

**3.** 打印出日期、PHP 版本和操作系统信息：

```php
echo '<p>Today is ' . TODAY . '.<br />This server is running version <b>' . PHP_VERSION . '</b> of PHP on the <b>' . PHP_OS . '</b> operating system.</p>';
```

由于常量不能在引号内打印，请在 `echo` 语句中使用连接运算符。

**4.** 完成 PHP 代码和 HTML 页面：

```php
?>  
</body>  
</html>
```

**5.** 将文件保存为 `constants.php`，将其放在你的 Web 目录中，并在 Web 浏览器中测试它。
