# PHP 全面教程指南



# 简介

感谢您选择本书，并向您表示祝贺。本书包含了使用正确语法、关键字和标点符号创建代码的详细步骤、策略和指南。它还提供了关于如何正确使用数组、表单、条件语句、会话等的技巧。您还将学习如何在 PHP 中打开、读取、写入和关闭文件。书中包含示例程序（示例），可作为您编写代码时的指南。本书还包含有关 PHP 的有用信息，包括其功能。希望本书对您有所帮助！

# 第 1 章：PHP 简介

## 要求

在开始学习 PHP 之前，建议您对以下内容有基本了解：

- CSS
- HTML

## 什么是 PHP

- PHP 是 Hypertext Preprocessor 的缩写
- PHP 是一种嵌入 HTML 的脚本语言
- PHP 脚本在服务器上执行
- PHP 文件的扩展名为 ".php"

## PHP 能做什么

从 PHP 能为您做什么的角度来思考也是有帮助的。

- 减少创建大型网站所需的时间。
- 根据您从访问者那里收集的信息，为访问者创建定制的用户体验。
- 可以生成动态页面内容
- 可以收集表单数据
- 可以发送和接收 Cookie
- 可以在数据库中添加、删除、修改数据
- 可以在服务器上创建、打开、读取、写入和关闭文件
- 可以加密数据

## 为什么选择 PHP

- PHP 可在各种操作系统平台上运行（Windows、Unix 等）
- PHP 易于学习，并在服务器端高效运行
- PHP 与当今使用的几乎所有服务器兼容（Apache 等）
- PHP 支持多种数据库
- PHP 可免费获得

## PHP 语法

PHP 脚本以 `<?php` 开始，以 `?>` 结束：

```php
<?php 

// PHP code here 

?>
```

PHP 文件通常包含 HTML 标签和一些 PHP 脚本代码。

如您在下面的示例中所见，PHP 代码行后面有一个分号。分号表示 PHP 语句的结束，绝不能遗忘。分号终止该语句。

下面是一个简单的 PHP 文件示例，其中包含一个使用 PHP 函数（内置函数）`echo` 输出文本 "Hello World!" 的 PHP 脚本：

```html
<html> 
<head> 
<title>My First PHP Page</title> 
</head> 
<body> 
<?php 
echo "Hello World!"; 
?> 
</body> 
</html>
```

显示：

Hello World!

## PHP 中的注释

PHP 代码中的注释是一行不会作为程序的一部分执行的代码。其目的是供编辑代码的人阅读。

PHP 支持三种表达注释的形式或方式。

注释有以下用途：

- 提醒自己做了什么 - 大多数程序员都有过回头查看自己注释的经历，这能让你想起写代码时的想法
- 让他人了解你在做什么 - 注释能让其他程序员理解你的每一个步骤

`// This is a single line comment`

`\# This is also a single line comment`

```
/*
This is a multiple lines comment block that spans over more than one line
*/
```

## PHP 中的大小写敏感性

在 PHP 中，所有变量都区分大小写。

下一章将详细讨论变量。

在下面的示例中，只有第一条语句会显示 `$pet` 变量的值（因为 `$pet`、`$PeT` 和 `$PET` 被视为三个完全不同的变量）：

示例

```html
<html> 
<body> 
<?php 
$pet="cat"; 
echo "My animal is a " . $pet . "<br>"; 
echo "My animal is a " . $PeT . "<br>"; 
echo "My animal is a " . $PET. "<br>"; 
?> 
</body> 
</html>
```

在 PHP 中，所有用户定义的函数、关键字和类都不区分大小写。

在下面的示例中，下面的两条 `echo` 语句都是合法的：

示例

```html
<html> 
<body> 
<?php 
echo "Hello World!<br>"; 
ECHO "Hello World!<br>";
?> 
</body> 
</html>
```

## 空格

在 HTML 中，PHP 语句之间的空格会被忽略。这意味着可以有一行 PHP 代码，然后在下一行 PHP 代码之前有 2 行或更多空行。因此，您可以缩进代码，PHP 解释器也会忽略这些空格。

下面是一个详细的示例：

```html
<html> 
<head> 
<title>My First PHP Page</title> 
</head> 
<body> 
<?php 
echo "Hello World!"; 
echo "Hello World!"; 
?> 
</body> 
</html>
```

显示：

Hello World!Hello World!

# 第 2 章：PHP 变量

## 变量定义

变量是存储值的一种方式，例如文本字符串 "Hello World!" 或整数值 30。变量可以在整个代码中重复使用，而不必一遍又一遍地输入实际值，换句话说，变量可以被称为存储信息的“容器”。

在 PHP 中，您可以使用以下形式定义变量：

`$variable_name = Value;`

就像在数学中一样

`r=1`
`s=2`
`t=r+s`

字母 `r`、`s` 分别保存数字 1、2。

从上面的表达式 `t=r+s` 中，我们可以计算出 `r` 的值为 3。

在 PHP 中，这些字母称为变量。

示例

```php
<?php 
$r=1; 
$s=2; 
$t=$r+$s; 
echo $t; 
?>
```

示例

```php
<?php 
$txt="Hello world"; 
?>
```

## 变量赋值约定

- 多个单词的变量应使用下划线分隔。`$my_variable`
- 变量以 `$` 符号开头，后跟变量名
- 变量名区分大小写（`$r` 和 `$R` 是两个不同的变量）
- 变量名不能以数字开头
- 变量名必须以字母或下划线字符开头
- 变量名只能包含字母数字字符和下划线（`A-z`、`0-9` 和 `_`）

## 第 3 章：PHP 数据类型

## PHP 数据类型

字符串、整数、浮点数、布尔值、数组。

## 字符串

字符串是字符序列，例如 "Hello world!"。

字符串可以是引号内的任何文本。您可以使用单引号或双引号，两者都能高效工作。

示例

```php
<?php 
$x = "Hello world!"; 
echo $x;  
?>
```

## 整数

整数是没有小数的数字。

整数规则：





# 整数

- 整数必须至少有一个数字 (`0-9`)
- 整数不能包含逗号或空格
- 整数不能有小数点
- 整数可以是正数或负数
- 整数可以用三种格式指定：十进制 (`10`-based)、十六进制 (`16`-based - 前缀为 `0x`) 或八进制 (`8`-based - 前缀为 `0`)

在以下示例中，我们将测试不同的数字。PHP `var_dump()` 函数返回变量的数据类型和值：

Example

```php
<?php 

$x = 5985; 

var_dump($x); 

echo "<br>"; 

$x = -345; // negative number 

var_dump($x); 

echo "<br>"; 

$x = 0x8C; // hexadecimal number 

var_dump($x); 

echo "<br>"; 

$x = 047; // octal number 

var_dump($x); 

?> 
```

### 浮点数

浮点数是带有小数点的数字或指数形式的数字。

在以下示例中，我们将测试不同的数字。PHP `var_dump()` 函数返回变量的数据类型和值：

Example

```php
<?php 

$x = 10.365; 

var_dump($x); 

echo "<br>"; 

$x = 2.4e3; 

var_dump($x); 

echo "<br>"; 

$x = 8E-5; 

var_dump($x); 

?> 
```

### 布尔值

布尔值可以是 `TRUE` 或 `FALSE`。

`var x=true;` 

`var y=false;`

布尔值常用于条件测试。您将在本教程的后续章节中了解更多关于条件测试的内容。

### 数组

数组在一个单一变量中存储多个值。

在以下示例中，我们创建一个数组，然后使用 PHP `var_dump()` 函数返回数组的数据类型和值：

Example

```php
<?php 

$fruits=array("mango","apple","ovacado",’’banana’’); 

var_dump($fruits); 

?> 
```

您将在本教程的后续章节中了解更多关于数组的内容。

# Chapter 4: PHP OPERATORS

## PHP Operators

本章展示了可以在 PHP 脚本中使用的不同运算符。

## PHP 算术运算符

1. 加法或求和 (`+`)

`$x + $y`

`$x` 和 `$y` 的和

2. 减法 (`-`)

`$x - $y`

`$x` 和 `$y` 的差

3. 乘法 (`*`)

`$x * $y`

`$x` 和 `$y` 的积

4. 除法 (`/`)

`$x / $y`

`$x` 和 `$y` 的商

5. 取模 (`%`)

`$x % $y`

`$x` 除以 `$y` 的余数

下面的示例展示了使用不同算术运算符的不同结果：

Example

```php
<?php 

$x=5; 

$y=3; 

echo ($x + $y); // outputs 8

echo ($x - $y); // outputs 2 

echo ($x * $y); // outputs 15 

echo ($x / $y); // outputs 1.6666666666667 

echo ($x % $y); // outputs 2 

?> 
```

## PHP 赋值运算符

PHP 赋值运算符用于将值写入变量。

PHP 中的基本赋值运算符是 `"="`。它表示左操作数被设置为右侧赋值表达式的值。

`x = y` 和是与 `x = y` 相同

左操作数被设置为右侧表达式的值

1. 加法

`x += y`

`x = x + y`

2. 减法

`x -= y`

`x = x - y`

3. 乘法

`x *= y`

`x = x * y`

4. 除法

`x /= y`

`x = x / y`

5. 取模

`x %= y`

`x = x % y`

下面的示例展示了使用不同赋值运算符的不同结果：

Example

```php
<?php 

$x=10; 

echo $x; // outputs 10 

$y=10; 

$y += 10; 

echo $y; // outputs 20 

$z=40; 

$z -= 25; 

echo $z; // outputs 15 

$i=5; 

$i *= 9; 

echo $i; // outputs 45

$j=12; 

$j /= 6; 

echo $j; // outputs 2 

$k=15; 

$k %= 4; 

echo $k; // outputs 3 

?> 
```

## PHP 字符串运算符

1. 连接 (`.`)

`$txt1 = "Hello"`

`$txt2 = $txt1 . " world!"`

输出是 hello world

2. 连接赋值 (`.=`)

`$txt1 = "Hello"`

现在 `$txt1` 包含 `"Hello world!"`

`$txt1 .= " world!"`

下面的示例展示了使用字符串运算符的结果：

Example

```php
<?php 

$x = "Hello"; 

$y = $a . " world!"; 

echo $y; // outputs Hello world! 

$x="Hello"; 

$x .= " world!"; 

echo $x; // outputs Hello world! 

?> 
```

## PHP 自增/自减运算符

1. 前自增 (`++$x`)

将 `$x` 增加一，然后返回 `$x`

2. 后自增 (`$x++`)

返回 `$x`，然后将 `$x` 增加一

3. 前自减 (`--$x`)

将 `$x` 减少一，然后返回 `$x`

4. 后自减 (`$x--`)

后自减

返回 `$x`，然后将 `$x` 减少一

下面的示例展示了使用不同自增/自减运算符的不同结果：Example

```php
<?php 

$x=9; 

echo ++$x; // outputs 10 

$y=10; 

echo $y++; // outputs 10 

$z=6; 

echo --$z; // outputs 5 

$i=5; 

echo $i--; // outputs 5 

?> 
```

## PHP 比较运算符

PHP 比较运算符用于比较两个值（数字或字符串）：

1. 等于 (`==`)

`$x == $y`

如果 `$x` 等于 `$y`，则为真

2. 全等 (`===`)

`$x === $y`

如果 `$x` 等于 `$y`，并且它们的类型相同，则为真

3. 不等于 (`!=`)

`$x != $y`

如果 `$x` 不等于 `$y`，则为真

4. 不等于 (`<>`)

`$x <> $y`

如果 `$x` 不等于 `$y`，则为真

5. 不全等 (`!==`)

`$x !== $y`

如果 `$x` 不等于 `$y`，或者它们的类型不同，则为真

6. 大于 (`>`)

`$x > $y`

如果 `$x` 大于 `$y`，则为真

7. 小于 (`<`)

`$x < $y`

如果 `$x` 小于 `$y`，则为真

8. 大于或等于 (`>=`)

`$x >= $y`

如果 `$x` 大于或等于 `$y`，则为真

9. 小于或等于 (`<=`)

`$x <= $y`

如果 `$x` 小于或等于 `$y`，则为真

下面的示例展示了使用一些比较运算符的不同结果：

Example

```php
<?php 

$x=100; 

$y="100"; 

var_dump($x == $y); 

echo "<br>"; 

var_dump($x === $y); 

echo "<br>"; 

var_dump($x != $y); 

echo "<br>"; 

var_dump($x !== $y); 

echo "<br>"; 

$a=50; 

$b=90; 

var_dump($a > $b); 

echo "<br>"; 

var_dump($a < $b); 

?> 
```

## PHP 逻辑运算符

1. `and`

`$x and $y`

如果 `$x` 和 `$y` 都为真，则为真

2. `or`

`$x or $y`

如果 `$x` 或 `$y` 为真，则为真

3. `xor`

`$x xor $y`

如果 `$x` 或 `$y` 为真，但不是两者都为真，则为真

4. 两者 (`&&`)

`$x && $y`

如果 `$x` 和 `$y` 都为真，则为真

5. `||` (Or)

`$x || $y`

如果 `$x` 或 `$y` 为真，则为真

6. `!` (Not)

`!$x`

如果 `$x` 不为真，则为真

## PHP 数组运算符

PHP 数组运算符用于比较数组：

1. 并集 (`+`)

`$x + $y`

`$x` 和 `$y` 的并集（但重复的键不会被覆盖）

2. 相等 (`==`)

`$x == $y`

如果 `$x` 和 `$y` 具有相同的键/值对，则为真

3. 全等 (`===`)

`$x === $y`

如果 `$x` 和 `$y` 具有相同的键/值对，顺序相同且类型相同，则为真

4. 不相等 (`!=`)

`$x != $y`

如果 `$x` 不等于 `$y`，则为真

5. 不相等 (`<>`)

`$x <> $y`

如果 `$x` 不等于 `$y`，则为真

6. 不全等 (`!==`)

`$x !== $y`

如果 `$x` 不全等于 `$y`，则为真

下面的示例展示了使用不同数组运算符的不同结果：

Example

```php
<?php 

$x = array("a" => "red", "b" => "green"); 

$y = array("c" => "blue", "d" => "yellow"); 

$z = $x + $y; // union of $x and $y 

var_dump($z); 

var_dump($x == $y); 

var_dump($x === $y); 

var_dump($x != $y); 

var_dump($x <> $y); 

var_dump($x !== $y); 

?> 
```

# Chapter 5: CONTROL STRUCTURES

## If 语句

PHP if 语句与其他编程语言中 if 语句的用法非常相似，请查看以下内容：

这种简单的 if/then 语句在日常生活中非常常见，在编程中也经常出现。每当你想要在某件事情为真时做出决定，并确保采取适当的行动时，你都在使用 if/then 关系。

example

`$my_name = "william";`

`if ( $my_name == "william" ) {`

`echo "Your name is william!<br />";`

`}`

Display:

Your name is william!

explanation

你是否明白我们是在将变量 `$my_name` 与 `"william"` 进行比较，看它们是否相等？在 PHP 中，你使用双等号 (`==`) 来比较值。此外，请注意，因为 if 语句结果为真，所以执行了代码段，打印出 "Your name is william!"。让我们深入了解一下细节

• 我们首先将变量 `$my_name` 设置为 `"william"`。





## PHP 条件语句

• 我们接下来使用了 PHP `if` 语句，检查变量 `$my_name` 中包含的值是否等于 `"william"`。

• `$my_name` 与 `"william"` 之间的比较是使用双等号 `"=="` 完成的，而不是单个等号 `"="`！单个等号用于给变量赋值，而双等号用于检查事物是否相等。

• `$my_name` 确实等于 `"william"`，因此执行了 `echo` 语句。

假设 `$my_name` 不等于 `"william"`，会发生什么情况？

PHP 代码：

```php
$my_name = "james";

if ( $my_name == "william" ) { 

echo "Your name is william!<br />"; 

} 

echo "Welcome to mysite!"; 
```

显示：

Welcome to mysite!

## If /else 语句

有人曾经告诉过你，“如果你努力学习，你就会通过考试”？如果你没有努力学习，会发生什么？嗯，你会失败！这是一个 if/else 条件语句的示例。

PHP 代码：

```php
$number_four == 4; 

if ( $number_four == 4 ) { 

echo " true"; 

} else { 

echo " false"; 

} 
```

显示：

 true 

说明：

• 我们首先创建了一个名为 `$number_four` 的 PHP 变量，并将其设置为 4。

• 在本示例中，我们将变量与整数值进行比较。要进行此类比较，我们使用 `"=="`。

• `$number_four` 确实等于 4，因此该语句将计算为 true。

• 位于 `if` 语句后面的左花括号 `"{"` 和右花括号 `"}"` 之间的所有代码，将在 `if` 语句为 true 时执行。

• `else` 段中包含的代码不会被使用。

## 将 else if 与 if..else 一起使用

示例

PHP 代码：

```php
$teacher = "george"; 

if($teacher == "anne"){ 

echo "Hello madam"; 

} elseif ($teacher == "george"){ 

echo "hello Sir!"; 

}else { 

echo 

"Morning"; 

} 
```

显示：

hello Sir! 

PHP 首先检查 `$teacher` 是否等于 `"anne"`，结果为 false。接下来，PHP 检查第一个 `elseif` 语句，`$teacher` 确实等于 `"george"`，因此打印出了短语 `george Sir!"`。如果我们想检查更多教师姓名，可以插入更多 `elseif` 语句！请注意，除非 `elseif` 语句前面有 `if` 语句，否则不能使用 `elseif` 语句。

## Switch 语句

有时，`if` 语句不是检查某些条件的最有效方法。使用 `switch` 语句，您可以一次性检查所有这些条件。

其工作原理如下：首先，我们有一个单个表达式（通常是一个变量），该表达式只计算一次。然后，将表达式的值与代码结构中每个 `case` 的值进行比较。如果匹配，则执行与该 `case` 关联的代码块。使用 `break` 是为了防止代码自动运行到下一个 `case`。如果没有找到匹配项，则使用 `default` 语句。

示例

```php
<?php 

$color="pink"; 

switch ($color) 

{ 

case "yellow": 

echo "Your favorite color is yellow!"; 

break; 

case "red": 

echo "Your favorite color is red!"; 

break; 

case "pink": 

echo "Your favorite color is pink!"; 

break; 

default: 

echo "Your favorite color is not known!"; 

} 

?>
```

`if` 语句有 `else` 子句，而 `switch` 语句有 `default` case。通常，在所有 `switch` 语句中始终包含 `default` case 是个好主意。

## while 循环

PHP `while` 循环在指定条件为 true 时执行一段代码。通常，当您编写代码时，希望同一段代码反复运行多次。与其在脚本中添加几个（这很乏味）几乎相同的代码行，不如使用循环来执行此类任务。

在 PHP 中，使用以下循环语句：

• `while` - 循环执行一段代码，只要指定条件为 true 即可。

语法

```php
while ( condition is true) 

{ 

 code to be executed; 

} 
```

以下示例首先将变量 `$x` 设置为 1 (`$x=1;`)。然后，`while` 循环将继续运行，只要 `$x` 小于或等于 10。每次循环运行时，`$x` 都会增加 1 (`$x++;`)：

示例

```php
<?php 

$x=1; 

while($x<=10) 

{ 

echo "The number is: $x <br>"; 

$x++; 

} 

?> 
```

• `do...while` - 循环执行一次代码块，然后只要指定条件为 true 就重复循环。`do...while` 循环总是会先执行一次代码块，然后检查条件，并在指定条件为 true 时重复循环。

语法

```php
do 

{ 

 code to be executed; 

 } 

while ( condition is true); 
```

以下示例首先将变量 `$x` 设置为 1 (`$x=1;`)。然后，`do while` 循环将输出一些内容，然后将变量 `$x` 增加 1。然后检查条件，只要 `$x` 小于或等于 10，循环就会继续运行：

示例

```php
<?php 

$x=1; 

do 

{ 

echo "The number is: $x <br>"; 

$x++; 

} 

while ($x<=10) 

?> 
```

请注意，在 `do while` 循环中，条件是在执行循环内的语句后进行测试的。这意味着，即使条件第一次失败，`do while` 循环也会至少执行一次其语句。

## For 循环

PHP `for` 循环执行一段代码指定的次数。当您事先知道脚本应该运行多少次时，使用 `for` 循环。

语法

```php
for ( init counter; test counter; increment counter) 

{ 

code to be executed;  

} 
```

说明：

• `init counter`：初始化循环计数器值。

• `test counter`：在每次循环迭代中进行计算。如果计算结果为 true，则循环继续。如果计算结果为 false，则循环结束。

• `increment counter`：增加循环计数器值。

以下示例显示 0 到 100 的数字：

示例

```php
<?php 

for ($x=0; $x<=100; $x++) 

{ 

echo "The number is: $x <br>"; 

} 

?> 
```

## Foreach 循环

`foreach` 循环仅适用于数组，用于遍历数组中的每个键值对。在每次循环迭代中，当前数组元素的值被赋给 `$value`，数组指针移动一位，直到到达最后一个数组元素。以下示例演示了一个循环，它将输出给定数组 (`$fruits`) 的值：

语法

```php
foreach ($ array  as  $ value) 

{ 

code to be executed;  

} 
```

示例

```php
<?php 

$fruits = array("mango","orange","pawpaw","ovacado"); 

foreach ($fruits as $value) 

{ 

echo "$value <br>"; 

} 

?> 

# Chapter 6:PHP ARRAYS

### Array definition

数组将多个值存储在一个单个变量中，因此数组是一种特殊的变量，一次可以容纳多个值。

如果您有一个项目列表（例如书籍名称列表），将书籍存储在单个变量中可能如下所示：

```php
$books1="computing"; 

$books2="religion"; 

$books3="history"; 

$books4="philosophy"; 
```

如果您想遍历书籍并查找特定书籍，该怎么办？如果您不是 4 本书，而是 4000 本书，该怎么办？最好的解决方案是创建一个数组，数组可以在一个名称下容纳许多值，并且您可以通过引用索引号来访问这些值。

### Creating an array

`array()` 函数用于创建数组：

数组有三种类型：

• Indexed arrays - 带有数字索引的数组

• Associative arrays - 带有命名键的数组

• Multidimensional arrays - 包含一个或多个数组的数组

### Indexed arrays

创建索引数组有两种方法：

注意：索引始终从 0 开始

1. 索引可以自动分配 `$books=array("computing","religion","history");`

2. 索引可以手动分配：

```php
$books[0]="computing"; 

$books[1]="religion"; 

$books[2]="history"; 
```

以下示例创建一个名为 `$cars` 的索引数组，向其分配三个元素，然后打印包含数组值的文本：

示例

```php
<?php 

$books=array("computing","religion","history");

echo "I love " . $books[0] . ", " . $books[1] . " and " .$books[2] ."; 

?> 
```

### Looping in indexed array

要遍历并输出索引数组的所有值，可以使用 `for` 循环 示例

```php
<?php 
```





`$books=array("computing","religion","history");`

`$arraylength=count($books);`

```
for($x=0;$x<$arraylength;$x++) 

{ 

echo $books[$x]; 

echo "<br>"; 

} 

?>
```

### 关联数组

关联数组是使用你分配给它们的命名键的数组。

然后可以在脚本中使用命名键：

创建关联数组有两种方式：1.`$year=array("benson"=>"1975","anne"=>"1937","Joel"=>"2000");` 或 2.`$year['benson']="1975";`

`$year['anne']="1937";`

`$year['Joel']="2000";`

示例

```
<?php 

$year=array("benson"=>"1975","anne"=>"1937","Joel"=>"2000");

 echo "benson was born in " . $year['benson'] . ; 

?> 
```

### 遍历关联数组

要遍历并输出关联数组的所有值，可以使用 foreach 循环

示例

```
<?php 

$year=array("benson"=>"1975","anne"=>"1937","Joel"=>"2000"); 

foreach($year as $x=>$x_value) 

{ 

echo "Key=" . $x . ", Value=" . $x_value; 

echo "<br>"; 

} 

?> 
```

### 获取数组长度

`count()` 函数用于返回数组的长度（元素个数）：

示例

```
<?php

$books=array("computing","religion","history");

echo count($books); 

?> 
```

# 第 7 章：PHP 函数

PHP 的真正威力来自于其函数；它拥有超过 1000 个内置函数。

注意：

- 除了内置的 PHP 函数，我们还可以创建自己的函数。
- 函数是一段可以在程序中重复使用的语句块。
- 页面加载时函数不会立即执行。
- 函数会通过函数调用来执行。

## 创建用户定义函数

- 用户定义函数声明始终以单词 `"function"` 开头
- 函数名不区分大小写。
- 函数名可以以字母或下划线开头（但不能以数字开头）。
- 为函数命名，使其反映函数的功能

请记住，开始花括号 (`{`) 表示函数代码的开始，结束花括号 (`}`) 表示函数的结束。

语法

```
function functionName() 

{ 

code to be executed; 

} 
```

示例

在下面的示例中，我们创建一个名为 `"displayname"` 的函数。该函数输出 `"Hello world!"`。要调用函数，只需写出其名称：

示例

```
<?php 

function displayname() 

{ 

echo "Hello world!"; 

} 

displayname(); // call the function 

?>
```

## 函数参数

参数就像一个变量，用于向函数传递信息；参数在函数名之后、括号内指定。

你可以添加任意数量的参数；但是，用逗号将它们分隔开。

下面的示例有一个带有两个参数的函数。当调用 `detail()` 函数时，我们也会传递 `detail`（例如 `james`、`1937`），并且 `detail` 在函数内部使用，该函数输出多个不同的详细信息。

示例

```
<?php 

function detail($name,$year) 

{ 

echo "$name Refsnes. born in $year <br>"; 

} 

detail("james","1937"); 

detail("kate","1971"); 

detail("anne","1963"); 

?> 
```

## 默认参数值

下面的示例说明如何使用默认参数。如果不带参数调用函数 `width()`，它将使用默认值作为参数。

示例

```
<?php 

function width($w=60) 

{ 

echo "The width is : $w <br>"; 

} 

width(65); 

width(); // will use the default value of 60 

width(15); 

width(90); 

?> 
```

## 返回值

要让函数返回一个值，请使用 `return` 语句。

示例

```
<?php 

function div($x,$y) 

{ 

$z=$x/$y; 

return $z; 

} 

echo "15 / 2 = " . div(15,5) . "<br>"; 

echo "14/2= " . div(14,2) . "<br>"; 

echo "12 / 4 = " . div(12,4); 

?> 
```

## 第 8 章：PHP 表单处理

## 简单 HTML 表单说明

当你想要从网站访问者那里收集一些数据时，需要 HTML 表单。例如，在用户注册期间，你可能希望收集姓名、电子邮件地址、信用卡等信息。

表单将从网站访问者那里获取输入，然后将其发布到后端应用程序，例如 CGI、ASP 脚本或 PHP 脚本等。后端应用程序将根据应用程序内定义的业务逻辑对传递的数据进行所需处理。

有多种表单元素可用，例如文本字段、文本区域字段、下拉菜单、单选按钮、复选框等。

HTML `<form>` 标签用于创建 HTML 表单，其语法如下：

```
<form action="Script URL" method="GET|POST">

   form elements like input, textarea etc.

</form>
```

| Action | 准备处理传递数据的后端脚本。 |
| --- | --- |
| Method | 用于上传数据的方法。最常用的是 GET 和 POST 方法。 |

## HTML 表单控件

你可以使用不同类型的表单控件来通过 HTML 表单收集数据：

- 复选框控件
- 单选按钮控件
- 下拉列表控件
- 文件选择框
- 隐藏控件
- 可点击按钮
- 提交和重置按钮

## 复选框控件

当需要选择多个选项时，使用复选框。它们也是使用 HTML `<input>` 标签创建的，但 `type` 属性设置为 `checkbox`。

以下是带有两个复选框的表单示例 HTML 代码：

```
<html>

<head>

<title>复选框控件</title>

</head>

<body>

<form>

<input type="checkbox" name="maths" value="on"> Maths

<input type="checkbox" name="physics" value="on"> Physics

</form>

</body>

</html>
```

表单底部

## 单选按钮控件

当有多个选项但只需要选择一个选项时，使用单选按钮。它们也是使用 HTML `<input>` 标签创建的，但 `type` 属性设置为 `radio`。

以下是带有两个单选按钮的表单示例 HTML 代码：

```
<html>

<head>

<title>单选按钮控件</title>

</head>

<body>

<form>

<input type="radio" name="subject" value="maths"> Maths

<input type="radio" name="subject" value="physics"> Physics

</form>

</body>

</html>
```

表单顶部

表单底部

## 下拉列表控件

下拉列表（也称为下拉框）提供一个选项，以列表形式列出各种选项，用户可以从中选择一个或多个选项。

以下是带有一个下拉列表的表单示例 HTML 代码：

```
<html>

<head>

<title>下拉列表控件</title>

</head>

<body>

<form>

<select name="dropdown">

<option value="Maths" selected>Maths</option>

<option value="Physics">Physics</option>

</select>

</form>

</body>

</html>
```

表单顶部

表单底部

## 文件上传框

如果你想允许用户将文件上传到你的网站，则需要使用文件上传框，也称为文件选择框。这也是使用 `<input>` 元素创建的，但 `type` 属性设置为 `file`。

以下是带有一个文件上传框的表单示例 HTML 代码：

```
<html>

<head>

<title>文件上传框</title>

</head>

<body>

<form>

<input type="file" name="fileupload" accept="image/\*" />

</form>

</body>

</html>
```

表单顶部

表单底部

## 按钮控件

在 HTML 中有多种方法可以创建可点击按钮。你也可以通过将 `<input>` 标签的 `type` 属性设置为 `button` 来创建可点击按钮。`type` 属性可以取以下值：

以下是带有三种类型按钮的表单示例 HTML 代码：

```
<html>

<head>

<title>按钮控件</title>

</head>

<body>

<form>

<input type="submit" name="submit" value="Submit" />

<input type="reset" name="reset" value="Reset" />

<input type="button" name="ok" value="OK" />

<input type="image" name="imagebutton" src="/html/images/logo.png" />

</form>

</body>

</html>
```

表单底部

### 隐藏表单控件





### 隐藏表单控件

隐藏表单控件用于隐藏页面中的数据，这些数据稍后可以推送到服务器。此控件隐藏在代码中，不会在实际页面上显示。例如，以下隐藏表单用于保存当前页码。当用户单击下一页时，隐藏控件的值将发送到 Web 服务器，服务器将根据传递的当前页码决定显示哪一页。

以下是显示隐藏控件用法的示例 HTML 代码：

```html
<html>

<head>

<title>hidden form control</title>

</head>

<body>

<form>

<p>This is number 1</p>

<input type="hidden" name="pagenumber" value="1" />

<input type="submit" name="submit" value="Submit" />

<input type="reset" name="reset" value="Reset" />

</form>

</body>

</html>
```

## Post 和 get 方法

以下示例包含一个带有两个输入字段和一个提交按钮的简单 HTML 表单，使用 post 方法：

Example 

```html
<html> 

<body> 

<form action="process.php" method="post"> 

Name: <input type="text" name="surname"><br> 

Age: <input type="text" name="age"><br> 

<input type="submit" name="submit"> 

</form> 

</body> 

</html> 
```

当用户填写上面的表单并单击提交按钮时，表单数据将发送到名为 "process.php" 的 PHP 文件进行处理。表单数据使用 `method="post"` 发送。

"process.php" 如下所示： 

```html
<html> 

<body> 

Welcome <?php echo $_POST["surname"]; ?>!!!<br> 

You are <?php echo $_POST["age"]; ?> years old. 

</body> 

</html> 
```

输出： 

Welcome oliver!!!

You are 36 years old. 

使用 `method="get"` 也可以实现相同的结果： 

Example 

```html
<html> 

<body> 

<form action="process.php" method="get"> 

Name: <input type="text" name="surname"><br> 

Age: <input type="text" name="age"><br> 

<input type="submit" name="submit"> 

</form> 

</body> 

</html> 
```

"process.php" 如下所示： 

```html
<html> 

<body> 

Welcome <?php echo $_GET["surname"]; ?>!!!<br> 

You are <?php echo $_GET["age"]; ?> years old. 

</body> 

</html> 
```

## Post 方法回顾

代码片段： 

```html
<form action="process.php" method="post"> 

Name: <input type="text" name="surname"><br> 

Age: <input type="text" name="age"><br> 
```

这段 HTML 代码指定表单数据将使用 POST 方法提交到 "process.php" 网页。PHP 的处理方式是将所有“发布”的值存储到名为 "`$_POST`" 的关联数组中。请务必注意表单数据的名称，因为它们代表 "`$_POST`" 关联数组中的键。

既然你了解了关联数组，"process.php" 中的 PHP 代码应该更容易理解一些。 

代码片段： 

```php
$y = $_POST['surname']; 

$x = $_POST['age']; 
```

表单名称用作关联数组中的键，因此请确保 HTML 表单中永远不会有两个名称相同的输入项。如果有，可能会出现一些问题。

## Get 方法回顾

如上所述，post 方法的替代方案是 get。如果我们将 HTML 表单更改为 get 方法，它将如下所示： 

代码片段： 

```html
<form action="process.php" method="get"> 

Name: <input type="text" name="surname"><br> 

Age: <input type="text" name="age"><br> 
```

get 方法的不同之处在于，它通过将变量附加到 URL 末尾的方式将变量传递到 "process.php" 网页。单击提交后，URL 末尾将添加以下内容： 

"?item=##&quantity=##" 

问号 "?" 告诉浏览器，以下项目是变量。既然我们更改了 "order.html" 上发送信息的方法，就必须更改 "process.php" 代码以使用 "`$_GET`" 关联数组。 

代码片段： 

```php
$y = $_GET['surname']; 

$x = $_GET['age']; 
```

更改数组名称后，脚本将正常工作。使用 get 方法会向访问者显示变量信息，因此请确保不要使用 get 方法发送密码信息或其他敏感项目。你不希望访问者看到他们不应该看到的内容。

## 安全预防措施

每当你获取用户输入并使用时，都需要确保输入是安全的。如果你打算将数据插入 MySQL 数据库，则应确保已考虑防止 [MySQL 注入](http://www.tizag.com/mysqlTutorial/mysql-php-sql-injection.php)；如果你打算将用户输入公开，则应考虑使用 PHP `htmlentities`。

# 第 9 章：全局变量

## 全局变量 - 超全局变量

PHP 中的几个预定义变量是“超全局变量”，这意味着它们始终可访问，无论作用域如何 - 你可以从任何函数、类或文件中访问它们，而无需做任何特殊操作。

PHP 超全局变量包括：

· `$GLOBALS`

· `$_SERVER`

· `$_REQUEST`

· `$_POST`

· `$_GET`

· `$_FILES`

· `$_ENV`

· `$_COOKIE`

· `$_SESSION`

本章将解释其中一些超全局变量。

## `$GLOBALS`

`$GLOBALS` 是一个 PHP 超全局变量，用于从 PHP 脚本中的任何位置（包括函数或方法内部）访问全局变量。

PHP 将所有全局变量存储在名为 `$GLOBALS[index]` 的数组中。索引保存变量的名称。

以下示例展示了如何使用超全局变量 `$GLOBALS`：

Example 

```php
<?php 

$x = 15; 

$y = 5; 

functionmultipyl() 

{ 

$GLOBALS['z'] = $GLOBALS['x'] * $GLOBALS['y']; 

} 

multiply(); 

echo $z; 

?> 
```

在上面的示例中，由于 z 是 `$GLOBALS` 数组中存在的变量，因此它也可以从函数外部访问！

## `$_SERVER`

`$_SERVER` 是一个 PHP 超全局变量，用于保存有关标头、路径和脚本位置的信息。

以下示例展示了如何使用 `$_SERVER` 中的一些元素：

Example 

```php
<?php 

echo $_SERVER['PHP_SELF']; 

echo "<br>"; 

echo $_SERVER['SERVER_NAME']; 

echo "<br>"; 

echo $_SERVER['HTTP_HOST']; 

echo "<br>"; 

echo $_SERVER['HTTP_REFERER']; 

echo "<br>"; 

echo $_SERVER['HTTP_USER_AGENT']; 

echo "<br>"; 

echo $_SERVER['SCRIPT_NAME']; 

?> 
```

下表列出了可以放入 `$_SERVER` 中的最重要元素：

元素/代码 

`$_SERVER['PHP_SELF']` 

返回当前正在执行的脚本的文件名 

`$_SERVER['GATEWAY_INTERFACE']` 

返回服务器使用的通用网关接口 (CGI) 的版本 

`$_SERVER['SERVER_ADDR']` 

返回主机服务器的 IP 地址 

`$_SERVER['SERVER_NAME']` 

返回主机服务器的名称（例如 www.w3schools.com） 

`$_SERVER['SERVER_SOFTWARE']` 

返回服务器标识字符串（例如 Apache/2.2.24） 

`$_SERVER['SERVER_PROTOCOL']` 

返回信息协议的名称和修订版本（例如 HTTP/1.1） 

`$_SERVER['REQUEST_METHOD']` 

返回访问页面时使用的请求方法（例如 POST） 

`$_SERVER['REQUEST_TIME']` 

返回请求开始的时间戳（例如 1377687496）

`$_SERVER['QUERY_STRING']` 

如果页面是通过查询字符串访问的，则返回查询字符串 

`$_SERVER['HTTP_ACCEPT']` 

返回当前请求的 Accept 标头 

`$_SERVER['HTTP_ACCEPT_CHARSET']` 

返回当前请求的 Accept_Charset 标头（例如 utf-8,ISO-8859-1） 

`$_SERVER['HTTP_HOST']` 

返回当前请求的 Host 标头 

`$_SERVER['HTTP_REFERER']` 

返回当前页面的完整 URL（不可靠，因为并非所有用户代理都支持它） 

`$_SERVER['HTTPS']` 

脚本是否通过安全 HTTP 协议查询 

`$_SERVER['REMOTE_ADDR']` 

返回用户查看当前页面时的 IP 地址 

`$_SERVER['REMOTE_HOST']` 

返回用户查看当前页面时的主机名 

`$_SERVER['REMOTE_PORT']` 





返回用户机器上用于与 Web 服务器通信的端口

`$_SERVER['SCRIPT_FILENAME']`

返回当前执行脚本的绝对路径名

`$_SERVER['SERVER_ADMIN']`

返回 Web 服务器配置文件中 SERVER_ADMIN 指令的值（如果您的脚本在虚拟主机上运行，则为该虚拟主机定义的值）（例如 someone@w3scholls.com）

`$_SERVER['SERVER_PORT']`

返回服务器机器上 Web 服务器用于通信的端口（例如 80）

`$_SERVER['SERVER_SIGNATURE']`

返回添加到服务器生成页面中的服务器版本和虚拟主机名

`$_SERVER['PATH_TRANSLATED']`

返回当前脚本的基于文件系统的路径

`$_SERVER['SCRIPT_NAME']`

返回当前脚本的路径

`$_SERVER['SCRIPT_URI']`

返回当前页面的 URI

## `$_REQUEST`

PHP `$_REQUEST` 用于在提交 HTML 表单后收集数据。

以下示例显示了一个带有输入字段和提交按钮的表单。当用户单击“提交”提交数据时，表单数据将发送到 `<form>` 标签的 action 属性中指定的文件。在此示例中，我们指向此文件本身以处理表单数据。如果您希望使用另一个 PHP 文件来处理表单数据，请将其替换为您选择的文件名。然后，我们可以使用超级全局变量 `$_REQUEST` 来收集输入字段的值：

示例

```html
<html>

<body>

<form method="post" action="<?php echo $_SERVER['PHP_SELF'];?>"> Name: <input type="text" name="name">

<input type="submit">

</form>

<?php

$name = $_REQUEST['fname'];

echo $name;

?>

</body>

</html>
```

# 第 10 章：SESSIONS

## Sessions 概述

随着网站变得越来越复杂，支持它的代码也必须随之提升。当您的网站需要将用户数据从一个页面传递到另一个页面时，可能就是开始考虑使用 PHP 会话的时候了。

普通 HTML 网站不会在页面之间传递数据。换句话说，当加载新页面时，所有信息都会被遗忘。这对于购物车等任务来说是个大问题，购物车需要记住用户从一个页面到下一个页面选择的产品。

PHP 会话通过允许您将用户信息存储在服务器上以供以后使用（例如用户名、购物车项目等）来解决此问题。但是，此会话信息是临时的，通常在用户离开使用会话的网站后很快就会被删除。

重要的是要思考会话的临时存储是否适用于您的网站。如果您需要更持久的存储，则需要寻找其他解决方案，例如 MySQL 数据库。

会话通过为每个访问者创建唯一的识别号（UID）并基于此 ID 存储变量来工作。这有助于防止两个用户的数据在访问同一网页时相互混淆。

注意：如果您不熟悉会话编程，不建议在需要高安全性的网站上使用会话，因为存在一些需要高级技术才能修补的安全漏洞。

## 启动会话

在开始在 PHP 会话中存储用户信息之前，必须先启动会话。启动会话时，必须放在代码的最开始处，在发送任何 HTML 或文本之前。

以下是一个简单的脚本，您应该将其放在 PHP 代码的开头以启动 PHP 会话。

PHP 代码：

```php
<?php

session_start(); // start up your PHP session!

?>
```

这段小代码会将用户的会话注册到服务器，允许您开始保存用户信息，并为该用户的会话分配一个 UID（唯一识别号）。

## 存储会话变量

当您想要在会话中存储用户数据时，请使用 `$_SESSION` 关联数组。这就是您存储和检索会话数据的地方。在 PHP 的早期版本中，有其他方法来执行此存储操作，但它已被更新，这是正确的做法。

PHP 代码：

```php
<?php

session_start();

$_SESSION['views'] = 1; // store session data

echo "Pageviews = ". $_SESSION['views']; //retrieve data

?>
```

显示：

Pageviews = 1

在此示例中，我们学习了如何将变量存储到会话关联数组 `$_SESSION` 中，以及如何从同一数组中检索数据。

## 使用 PHP 的 isset 函数

现在您知道可以轻松地从 `$_SESSION` 数组中存储和检索数据，我们可以探索会话的一些真实功能。当您创建一个变量并将其存储在会话中时，您可能希望将来使用它。但是，在使用会话变量之前，有必要检查它是否已经存在！

这时 PHP 的 `isset` 函数就派上用场了，`isset` 是一个函数，它接受您想要使用的任何变量并检查它是否已被设置。也就是说，它是否已经被赋予了一个值。

通过我们之前的示例，我们可以使用 `isset` 来检查页面浏览量变量是否已经创建，从而创建一个非常简单的页面浏览量计数器。如果已创建，我们可以增加计数器。如果不存在，我们可以创建一个页面浏览量计数器并将其设置为 1。以下是完成此任务的代码：

PHP 代码：

```php
<?php

session_start();

if(isset($_SESSION['views']))

$_SESSION['views'] = $_SESSION['views']+ 1;

else

$_SESSION['views'] = 1;

echo "views = ". $_SESSION['views'];

?>
```

第一次在新打开的浏览器上运行此脚本时，if 语句将失败，因为尚未存储会话变量 views。但是，如果您刷新页面，if 语句将为真，计数器将加 1。每次重新运行此脚本，您都会看到浏览量增加 1。

## 销毁会话

虽然会话数据是临时的，不需要您显式地清理，但您可能希望出于各种任务删除一些数据。

假设您正在经营一家在线业务，用户使用您的网站购买您的商品。用户刚刚在您的网站上完成了一笔交易，您现在想要从他们的购物车中删除所有内容。

PHP 代码：

```php
<?php

session_start();

if(isset($_SESSION['cart']))

unset($_SESSION['cart']);

?>
```

您也可以通过调用 `session_destroy` 函数来完全销毁整个会话。

PHP 代码：

```php
<?php

session_start();

session_destroy();

?>
```

销毁会话会重置您的会话，所以除非您完全愿意丢失所有存储的会话数据，否则不要调用该函数！

## 会话备注

Cookie 在互联网上已经存在相当长一段时间了。它们被发明出来是为了允许网站管理员在用户的计算机上存储有关用户及其访问的信息。

起初，公众非常担心 Cookie，因为人们认为它们是严重的隐私风险。

如今，几乎每个人的浏览器都启用了 Cookie，部分原因是有更糟糕的事情需要担心，部分原因是所有“可信”的网站现在都使用 Cookie。

本课将教您存储 Cookie 和检索 Cookie 的基础知识，以及解释您可以为 Cookie 设置的各种选项。

# 第 11 章：COOKIES

## 创建 Cookie

当您创建 Cookie 时，使用函数 `setcookie`，您必须指定三个参数。这些参数是 `setcookie(name, value, expiration)`：

1. name：您的 Cookie 的名称。您将使用此名称稍后检索您的 Cookie，所以不要忘记！

2. value：存储在您的 Cookie 中的值。常见的值是用户名（字符串）和上次访问时间（日期）。





3\. expiration: Cookie 将过期并被删除的日期。如果不设置此过期日期，则它将被视为会话 Cookie，并在浏览器重新启动时被删除。

在本示例中，我们将创建一个存储用户上次访问时间的 Cookie，以衡量人们返回访问我们网页的频率。我们希望忽略那些超过两个月才返回网站的人，因此我们将 Cookie 的过期日期设置为两个月后！

PHP Code:

```php
//Calculate 60 days in the future
//seconds * minutes * hours * days + current time
$inTwoMonths = 60 * 60 * 24 * 60 + time();
setcookie(lastVisit, date("G:i - m/d/y"), $inTwoMonths);
```

如果你无法跟上本示例中稍微复杂的日期计算，请不要担心。重要的是，你要知道如何通过指定三个重要参数（名称、值和过期日期）来设置 Cookie。

## 检索 Cookie

如果 Cookie 尚未过期，让我们使用 `$_COOKIE` 关联数组从用户的 PC 中检索它。存储 Cookie 的名称是键，它将让你检索存储的 Cookie 值！

PHP Code:

```php
if(isset($_COOKIE['lastVisit']))
$visit = $_COOKIE['lastVisit'];
else
echo "You've got some stale cookies!";
echo "Your last visit was - ". $visit;
```

这个实用脚本首先使用 `isset` 函数来确保我们的 "lastVisit" Cookie 仍然存在于用户的 PC 上，如果存在，则显示用户的上次访问时间。如果用户在 2015 年 5 月 14 日访问了我们的网站，它可能看起来像这样：

显示：

Your last visit was - 10:41- 05/14/15

# 第 12 章：使用文件

## 打开和关闭文件

在 PHP 中，通常使用 `fopen()` 函数来打开文件。它需要两个参数，分别指定文件名和操作模式。如果文件打开不成功，`fopen()` 函数将返回 false，否则它将返回一个文件指针，用于读取或写入该特定文件。

文件模式可以按如下方式指定

| 文件模式 | 用途 |
| --- | --- |
| r | 仅以读取方式打开文件。将文件指针放置在文件开头。 |
| r+ | 以读取和写入方式打开文件。将文件指针放置在文件开头。 |
| w | 仅以写入方式打开文件。将文件指针放置在文件开头，并将文件截断为零长度。如果文件不存在，则尝试创建文件。 |
| w+ | 以读取和写入方式打开文件。将文件指针放置在文件开头，并将文件截断为零长度。如果文件不存在，则尝试创建文件。 |
| a | 仅以写入方式打开文件。将文件指针放置在文件末尾。如果文件不存在，则尝试创建文件。 |
| a+ | 以读取和写入方式打开文件。将文件指针放置在文件末尾。如果文件不存在，则尝试创建文件。 |

## 读取文件

一旦使用 `fopen()` 函数打开文件，就可以使用名为 `fread()` 的函数来读取它。该函数需要两个参数。这些参数必须是文件指针和以字节表示的文件长度。

可以使用 `filesize()` 函数来查找文件的长度，该函数以文件名作为参数，并返回以字节表示的文件大小。

以下是使用 PHP 读取文件所需的步骤。

* 使用 `fopen()` 函数打开文件。
* 使用 `filesize()` 函数获取文件长度。
* 使用 `fread()` 函数读取文件内容。
* 使用 `fclose()` 函数关闭文件。

以下示例将文本文件的内容分配给一个变量，然后在网页上显示这些内容。

```php
$filename = "example.txt";
$file = fopen( $filename, "r" );
if( $file == false )
{
    echo ( "Error occurred in opening file" );
    exit();
}
$filesize = filesize( $filename );
$filetext = fread( $file, $filesize );
fclose( $file );
echo ( "File size is : $filesize bytes" );
echo ( "<pre>$filetext</pre>" );
```

## 写入文件

可以使用 PHP 的 `fwrite()` 函数创建新文件或将文本追加到现有文件中。该函数需要两个参数，分别指定文件指针和要写入的数据字符串。可选地，可以包含第三个整数参数来指定要写入的数据长度。如果包含第三个参数，写入将在达到指定长度后停止。

以下示例创建一个新文本文件，然后在其中写入一个简短的文本标题。关闭此文件后，使用 `file_exist()` 函数确认其存在，该函数以文件名作为参数

```php
$filename = "/home/user/guest/newfile.txt";
$file = fopen( $filename, "w" );
if( $file == false )
{
    echo ( "Error occurred in opening new file" );
    exit();
}
fwrite( $file, "This is a simple file\n" );
fclose( $file );
```

```php
$filename = "newfile.txt";
$file = fopen( $filename, "r" );
if( $file == false )
{
    echo ( "Error occured in opening file" );
    exit();
}
$filesize = filesize( $filename );
$filetext = fread( $file, $filesize );
fclose( $file );
echo ( "File size is: $filesize bytes" );
echo ( "$filetext" );
echo("file name: $filename");
```

# 第 13 章：面向对象 PHP

我们的宇宙由不同的对象组成，如月球、地球、火星等。同样，我们可以想象我们的汽车由不同的对象组成，如车轮、方向盘、齿轮等。同样，面向对象编程概念将一切视为对象，并使用不同的对象实现软件。

## 面向对象概念

Class − 这是一种程序员定义的数据类型，包括局部函数和局部数据。你可以将类视为制作同一类（或类）对象的多个实例的模板。

Object − 由类定义的数据结构的一个单独实例。你定义一次类，然后创建许多属于它的对象。对象也称为实例。

Inheritance − 当一个类通过继承父类的现有函数来定义时，这称为继承。在这里，子类将继承父类的全部或部分成员函数和变量。

Parent class − 被另一个类继承的类。这也称为基类或超类。

Child Class − 从另一个类继承的类。这也称为子类或派生类。

Polymorphism − 这是一种面向对象的概念，其中同一个函数可以用于不同的目的。例如，函数名称将保持不变，但它可以接受不同数量的参数并执行不同的任务。

Overloading − 一种多态类型，其中一些或所有运算符根据其参数的类型具有不同的实现。同样，函数也可以用不同的实现进行重载。

Data Abstraction − 隐藏实现细节的任何数据表示。

Encapsulation − 指将所有数据和成员函数封装在一起以形成对象的概念。

Constructor − 指一种特殊的函数，每当从类中创建对象时，它都会自动被调用。

## 定义 PHP 类

在 PHP 中定义新类的一般形式如下 −

```php
class phpClass{
    var $var1;
    var $var2 = "constant string";
    function myfunc ($arg1, $arg2) {
        [...]
    }
    [...]
}
```





这里是每一行的简单描述 −

* 特殊形式 `class`，后跟你要定义的类的名称。
* 一组花括号，括住任意数量的变量声明和函数定义。
* 变量声明以特殊形式 `var` 开头，后跟 `$ 变量名称`；它们也可以有一个初始赋值到常量值。
* 函数定义看起来很像独立的 PHP 函数，但局限于类，并将用于设置和访问对象数据。

example

```php
class Books{
   /* Member variables */
   var $price;
   var $title;
   /* Member functions */
   function setPrice($par){
      $this->price = $par;
   }
   function getPrice(){
      echo $this->price ."<br/>";
   }
   function setTitle($par){
      $this->title = $par;
   }
   function getTitle(){
      echo $this->title ." <br/>";
   }
}
```

变量 `$this` 是一个特殊变量，它指向同一个对象，即自身。

## 创建对象

一旦你定义了类，就可以创建任意数量的该类类型的对象。以下是使用 `new` 运算符创建对象的示例。

```php
$biology = new Books;
$maths = new Books;
$chemistry = new Books;
```

这里我们创建了三个对象，这些对象彼此独立，并且它们将分别存在。接下来我们将看到如何访问成员函数和处理成员变量。

## 构造函数

构造函数是一种特殊的函数，每当创建对象时会自动调用。因此，我们充分利用这种行为，通过构造函数初始化许多内容。

PHP 提供一个名为 `__construct()` 的特殊函数来定义构造函数。你可以向构造函数传递任意数量的参数。

以下示例将为 `Books` 类创建一个构造函数，它将在对象创建时初始化书籍的价格和标题。

```php
function __construct( $par1, $par2 ){
   $this->price = $par1;
   $this->title = $par2;
}
```

现在我们不需要单独调用 set 函数来设置价格和标题。我们只能在对象创建时初始化这两个成员变量。查看下面的示例 −

```php
$physics = new Books( "biology", 10 );
$maths = new Books ( "maths", 14 );
$chemistry = new Books ("chemistry", 17 );

/* Get those set values */
$physics->getTitle();
$chemistry->getTitle();
$maths->getTitle();
$physics->getPrice();
$chemistry->getPrice();
$maths->getPrice();
```

这将产生以下结果 −

```text
 biology
 maths
 chemistry
 10
 14
 17
```

## 继承 

PHP 类定义可以选择使用 `extends` 子句从父类定义继承。语法如下 −

```php
class Child extends Parent {
   <definition body>
}
```

继承的效果是子类（或子类或派生类）具有以下特征 −

* 自动拥有父类的所有成员变量声明。
* 自动拥有与父类相同的所有成员函数，默认情况下，这些函数的工作方式与父类中的函数相同。

示例：

```php
class Novel extends Books{
   var publisher;
   function setPublisher($par){
      $this->publisher = $par;
   }
   function getPublisher(){
      echo $this->publisher. "<br />";
   }
}
```

现在，除了继承的函数之外，类 `Novel` 还保留了两个额外的成员函数。

## 覆盖 

子类中的函数定义会覆盖父类中同名的定义。在子类中，我们可以修改从父类继承的函数的定义。

示例：

`getPrice` 和 `getTitle` 函数被覆盖以返回某些值。

```php
function getPrice(){
   echo $this->price . "<br/>";
   return $this->price;
}

function getTitle(){
   echo $this->title . "<br/>";
   return $this->title;
}
```

## 公共成员

除非你另有说明，否则类的属性和方法都是公共的。也就是说，它们可以在三种可能的情况下被访问 −

* 从声明它的类之外
* 从声明它的类之内
* 从实现声明它的类的另一个类之内

到目前为止，我们看到的所有成员都是公共成员。如果你希望限制类成员的可访问性，则可以将类成员定义为 `private` 或 `protected`。

## 私有成员

通过将成员指定为私有，你将其可访问性限制在声明它的类中。私有成员不能从继承声明它的类的类中引用，也不能从类之外访问。

类成员可以通过在成员前使用 `private` 关键字来设为私有。

```php
class MyClass {
   private $car = "audi";
   $driver = "willy";
   function __construct($par) {
      // Statements here run every time
      // an instance of the class
      // is created.
   }
   function myPublicFunction() {
      return("I'm visible!");
   }
   private function myPrivateFunction() {
      return("I'm  not visible outside!");
   }
}
```

当 `MyClass` 类被另一个类使用 `extends` 继承时，`myPublicFunction()` 将可见，`$driver` 也将可见。扩展类将不会意识到或访问 `myPrivateFunction` 和 `$car`，因为它们被声明为私有。

## 受保护成员

受保护的属性或方法在声明它的类中以及扩展该类的类中都可访问。受保护的成员在这两种类之外不可用。类成员可以通过在成员前使用 `protected` 关键字来设为受保护。

以下是 `MyClass` 的不同版本 −

```php
class MyClass {
   protected $car = "audi";
   $driver = "willy";
   function __construct($par) {
      // Statements here run every time
      // an instance of the class
      // is created.
   }
   function myPublicFunction() {
      return("I'm visible!");
   }
   protected function myPrivateFunction() {
      return("I'm  visible in child class!");
   }
}
```

## 接口

接口被定义以向实现者提供通用的函数名称。不同的实现者可以根据其要求实现这些接口。你可以说，接口是由开发者实现的骨架。

从 PHP5 开始，可以像这样定义接口 −

```php
interface email {
   public function sendemail();
}
```

然后，如果另一个类实现了该接口，像这样 −

```php
class Report implements email {
   // sendemail() Definition goes here
}
```

# 结论

 再次感谢你选择阅读本书。我希望本书能帮助你学习和了解更多关于 PHP 以及如何编写 PHP 代码的内容。接下来，将由你来应用在本书中所学到的知识。

最后，如果你喜欢这本书，请恳请抽出时间分享你的想法并在 Amazon 上发表评论。这将不胜感激。

