
输出：
704

#### 双精度浮点

可以包含带有分数或小数部分的数字，包括正数和负数。默认情况下，变量会添加最小的小位数。

示例：

```php
<?php
$val1 = 50.85;
$val2 = 654.26;
$sum = $val1 + $val2;
echo $sum;
?>
```

#### 字符串

包含字母或任何字母字符，甚至包括数字。这些在声明时写在双引号内。字符串也可以写在单引号内，但在打印变量时处理方式不同。为了澄清这一点，请看下例。
示例：

```php
<?php
$name = "Jone";
echo "The name of the Geek is $name \n";
echo 'The name of the geek is $name';
?>
```

输出：
The name of the Geek is Jone
The name of the geek is $name

#### NULL

这些是特殊的变量类型，只能存储一个值，即 NULL。我们遵循大写形式的习惯，但它是区分大小大小的。
示例：

```php
<?php
$nm = NULL;
echo $nm;   // 这不会产生输出
?>
```

#### 布尔值

只包含两个值：TRUE 或 FALSE。成功的事件返回 true，失败的事件返回 false。NULL 类型的值在布尔值中也被视为 false。除了 NULL 之外，0 也被视为 false。如果字符串为空，那么它在布尔数据类型中也被视为 false。

示例：

```php
if(TRUE)
  echo "This condition is TRUE";
if(FALSE)
  echo "This condition is not TRUE";
?>
```

> 布尔数据类型是一种具有一个可能值（通常表示为 true 和 false）的数据类型，旨在表示逻辑和布尔代数的真值。

输出：
This condition is TRUE
This condition is not TRUE

#### 数组

数组是一种复合数据类型，可以存储相同数据类型的多个值。下面是一个整数数组的示例。

```php
<?php
$intArray = array(10, 20 , 30);
echo "First Element: $intArray[0]\n";
echo "Second Element: $intArray[1]\n";
echo "Third Element: $intArray[2]\n";
?>
```

![](img/f8aa82c4ef45031ca4eadc2bb946c87a_51_0.png)

输出：
First Element: 10
Second Element: 20
Third Element: 30

对象：对象被定义为用户定义类的实例，它们可以同时包含值和函数。

资源：PHP 中的资源不是精确的数据类型。它们基本上用于存储对某些函数调用或外部资源的引用。例如，考虑一个数据库调用。这是一个外部资源。

HipHop 由 Facebook 开发并开源，它将 PHP 脚本转换为 C++ 然后编译生成的代码，从而将服务器负载降低高达 50%。在 2013 年初，由于多个原因，Facebook 弃用了它转而使用 HHVM，原因包括对整个 PHP 语言的困难和缺乏支持，包括 `create_function()` 结构。

### 2.2 PHP 运算符

运算符接收一个或多个值（称为操作数），并对它们执行操作，例如将它们相加。以下是 PHP 中最常用的运算符：

- 算术运算符
- 赋值运算符
- 位运算符运算符
- 比较运算符
- 递增/递减运算符
- 逻辑运算符
- 字符串连接运算符

#### 2.2.1 算术运算符

算术运算符需要数值值。非数值值会自动转换为数值值。以下是算术运算符的列表：

- 加法 (`+`) 返回两个操作数的和
- 减法 (`-`) 返回两个操作数的差
- 乘法 (`*`) 返回两个操作数的积
- 除法 (`/`) 返回两个操作数的商。两个整数相除的结果可能会产生一个整数（4/2 = 2）或浮点数（3/2 = 1.5）
- 取模 (`%`) 返回第一个操作数除以第二个操作数的余数。

以下是示用例：

```php
<?php
$x = 20;
$y = 10;
// 加法
echo $x + $y; // 30
// 减法
echo $x - $y; // 10
// 乘法
echo $x * $y; // 200
// 除法
echo $x / $y; // 2
// 取模
echo $x % $y; // 0
?>
```

#### 2.2.2 赋值运算符

赋值运算符的主要功能是将值分配给变量。简单的赋值运算符是等号 (`=`)，它只赋值值。而其他赋值运算符是在赋值之前执行其他操作的快捷赋值。

以下是示例：

```php
<?php
$num=10;
$new_num=$num;
echo "Simple Assignment Operator $new_num";
$num+=5;
echo "Addition Assignment $num";
$num*=2;
echo "Multiplication Assignment $num";
$num/=3;
echo "Division Assignment $num";
$num.=5;
echo "Concatenation Assignment $num";
?>
```

#### 2.2.3 字符串运算符

PHP 中的字符串运算符提供了两个连接字符串的运算符。由于第一个运算符 (`.`) 是连接运算符，可以将两个字符串连接在一起。而第二个运算符 (`.=`) 是赋值运算符，在连接后赋值。

这里是一个展示如何在 PHP 中使用连接运算符连接两个字符串的示例。

```php
<?php
$lang1="JavaScript";
$lang2="PHP";
$lang=$lang1." & .$lang2;
echo $lang;
$out="are programming languages";
echo $out;
?>
```

#### 2.2.4 位运算符

与其他运算符不同，位运算符在组成整数值的单个位上上检查并操作整数值。由于这些类型的运算符将整数转换为二进制数并执行逻辑操作，最后以整数形式显示，因此得名位运算符。AND(`&`)、OR(`|`)、XOR(`^`)、NOT(`~`)、左移(`<<`) 和右移(`>>`) 是最常用的位运算符。

这里有一个示例展示了 PHP 位与 AND(`&`) 运算符的用法，它显示了

两个变量 `$a` 和 `$b` 的位与（AND）运算输出。

```php
<?php
$a=66;
$b=88;
$c=$a&&$b;
echo "Bitwise AND on a and b is $c";
?>
```

输出:
Bitwise AND on a and b is 64

#### 2.2.5 比较运算符

由于逻辑运算符提供了决策的方法，比较运算符则提供了一种直接控制程序流的方法。比较运算符比较变量的两个或多个值。最常用的比较运算符包括小于 (`<`)、大于 (`>`) )、小于或等于 (`<=`)、大于或等于 (`>=`) 以及三元运算符 (`? :`)。

以下是一个展示如何在 PHP 中使用比较运算符的示例。

- 等于 (`==`) ：如果两个操作数相等，则返回 true，否则返回 false。
- 恒等 (`===`) ：如果两个操作数具有相同的数据类型且相等，则返回 true，否则返回 false。
- 不等于 (`!=` 或 `<>`) ：如果两个操作数不相等，则返回 true，否则返回 false。
- 不相同 (`!==`) ：如果两个操作数不相等或没有相同的数据类型，则返回 true，否则返回 false。
- 大于 (`>`) ：如果左侧的操作数大于右侧的操作数，则返回 true，否则返回 false。
- 大于或等于 (`>=`) ：如果左侧的操作数大于或等于右侧的操作数数，则返回 true，否则返回 false。
- 小于 (`<`) ：如果左侧的操作数小于右侧的操作数，则返回 true，否则返回 false。
- 小于或等于 (`<=`) ：如果左侧的操作数小于或等于右侧的操作数，则返回 true，否则返回 false。

### 记住

在 PHP 中，可以将这些递增递减运算符放在变量的任意侧。在使用递增或递减运算符赋值时，会产生略有不同的效果。

#### 2.2.6 递增和递减运算符

另一组运算符可以增加或减少变量的值，称为递增 (`++`) 和递减 (`--`)运算符。递增运算符 (`++`) 将值加 1，而递减运算符 (`--`) 将值减 1。

在下面的示例中，将一个数字赋值给一个整数变量，在赋值给第一个变量后增加该值，在减少整数值后增加赋值给第二个变量变量的值。

```php
$int=45; // 将整数 45 赋值给 \int
```

```php
$int1++; $int;
```

```php
$int2=$int;
```

```php
echo "The value of first integer is $int1<br/>";
echo "The value of second integer is $int2<br/>";
?>
Value of first integer is 46
The value of second integer is 46
```

#### 2.2.7 逻辑运算符

逻辑运算符提供了根据多个变量的值进行决策。这些运算符在创建 PHP 时最为有用。因此，可以使用逻辑运算符控制程序的流。逻辑运算符通常用于 if 条件和 for 循环等控制结构。以下是 PHP 中的逻辑运算符列表及其用途。

- AND, `&&` 并 与运算符 → 如果两个变量都为 True，则为 True。
- OR, `||` → 或运算符 → 如果至少有一个变量为 True，则为 True。
- NOT, `!` → 非运算符 → 如果变量不为 True，则为 True。
- XOR → 异或运算符 → 如果只有一个变量为 True，则为 True。

以下是一个展示在 PHP 编程中使用的不同逻辑运算符的示例。

```php
<?php
$a=5;
$b=6;
$c=7;
if (($a<$b) && ($b<$c)) {
    echo "$c is the greatest number<br/>";
}
if ($a==5 || $b==5) {
    echo "Either a or b is equal to 5<br/>";
}
if ($a!=5) {
    echo "a and b are not equal";
}
?>
```

### 输出

7 is the greatest number

Either a or b is equal to 5

a and b are not equal

#### 2.2.8 连接运算符

连接运算符 (`.`)允许将两个字符串合并。它允许连接两个字符串。让我们看看以下示例：

```php
<?php
$str = 'This is ' . 1;
echo $str;
?>
```

### 2.3 控制语句

由于逻辑运算符提供了根据多个变量的值进行决策的方法。这些运算符在创建 PHP 应用时最有用。所以，可以使用逻辑运算符控制程序的流。逻辑运算符主要用于 if 条件和 for 循环等控制结构。以下是 PHP 中的逻辑运算符列表及其用途。

#### 2.3.1 if 语句

if 语句用于检查条件。如果条件为真，则执行大括号内的代码。其形式如下：

```php
<?php
$x = 10;
if ($x > 5) {
    echo "x is greater than 5";
}
?>
```

if 语句用于检查条件。如果条件为真，则执行大括号内的代码。如果条件为假，则执行 else 部分。

```php
<?php
$x = 4;
if ($x > 5) {
    echo "x is greater than 5";
} else {
    echo "x is not greater than 5";
}
?>
```

if 语句用于检查条件。如果条件为真，则执行大括号内的代码。如果条件为假，则执行 else 部分。

```php
<?php
$x = 10;
if ($x > 5) {
    echo "x is greater than 5";
} elseif ($x > 8) {
    echo "x is greater than 8";
} else {
    echo "x is not greater than 8";
}
?>
```

if 语句用于检查条件。如果条件为真，则执行大括号内的代码。如果条件为假，则执行 else 部分。

```php
<?php
$x = 10;
if ($x > 5) {
    echo "x is greater than 5";
} elseif ($x > 8) {
    echo "x is greater than 8";
} else {
    echo "x is not greater than 8";
}
?>
```

if 语句用于检查条件。如果条件为真，则执行大括号内的代码。如果条件为假，则执行 else 部分。

```php
<?php
$x = 10;
if ($x > 5) {
    echo "x is greater than 5";
} elseif ($x > 8) {
    echo "x is greater than 8";
} else {
    echo "x is not greater than 8";
}
?>
```

#### 2.3.2 switch 语句

switch 语句是一种选择控制流语句。它允许通过变量或表达式的值来控制程序流的多路分支。与使用 if、elseif 语句相比，创建多个分支更加简单。

```php
<?php
$color = "red";
switch ($color) {
    case "red":
        echo "color is red";
        break;
    case "blue":
        echo "color is blue";
        break;
    default:
        echo "color is unknown";
}
?>
}
?>
```

#### 2.3.3 PHP while 循环

while 是一种控制语句，允许根据给定的布尔条件重复执行代码。
这是 while 循环的通用形式：

while (expression):
    statement

当表达式（expression）求值为真时，while 循环会执行该语句（statement）。该语句可以是以分号结尾的简单语句，也可以是包含在大括号中的复合复合语句。

```
whilst.php
<?php
$i = 0;
while ($i < 5) {
    echo "PHP language\n";
    $i++;
}
?>
```

在代码示例中，我们反复向控制台打印字符串 "PHP language"。
while 循环包含三个部分：初始化、测试和更新。语句的每次执行被称为一个周期（cycle）。

$i = 0;

我们初始化变量 $i。它在我们的脚本中被用作计数器。

```
while ($i < 5) {
...
}
```

方括号内的表达式是第二阶段，即测试。while 循环会执行体内的语句，直到表达式求值为假。

$i++;

while 循环的最后一个阶段是更新；计数器递增。注意，处理 while 循环不当会导致死循环。

$ php whilst.php
PHP language
PHP language
PHP language
PHP language
PHP language

程序向控制台打印了五次消息。do while 循环是 while 循环的一个版本。区别在于，该版本保证至少运行一次。

```
dowhile.php
<?php
$count = 0;
do {
    echo "$count\n";
} while ($count != 0) {
}
?>
```

首先执行迭代，然后评估真值表达式。
while 循环通常与 list() 和 each() 函数配合使用。

```
seasons.php
<?php
$seasons = ["Spring", "Summer", "Autumn", "Winter"];
while (list($idx , $val) = each($seasons)) {
    echo "$val\n";
}
?>
```

我们在 $seasons 数组中有四个季节。我们遍历了所有的值并将它们打印到控制台。`each()` 函数从数组中返回当前的键值对，并移动数组指针。当函数到达数组末尾时，它返回 false 循环终止。`each()` 函数返回一个数组。赋值左侧也必须是一个数组。我们使用 `list()` 函数从两个变量创建一个数组。

```
php seasons.php
Spring
Summer
Autumn
Winter
```

这是 seasons.php 脚本的输出。

#### 2.3.4 PHP for 关键字

for 循环的作用与 while 循环相同。不同的是它将初始化、测试和更新这三个阶段放在了同一个位置，即圆括号之间。它主要用于进入循环前已知迭代次数的情况。

让我们来看一个 for 循环的示例。

```
forloop.php
<?php
$days = [ "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday" ];
$len = count($days);
for ($i = 0; $i < $len; $i++) {
    echo $days[$i], "\n";
}
?>
```
