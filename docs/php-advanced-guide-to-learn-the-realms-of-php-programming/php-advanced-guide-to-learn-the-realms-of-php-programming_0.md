
# PHP 高级指南：学习 PHP 编程领域

![](img/image_rsrcCGT.jpg)

## 第一章：学习 PHP 的第一步

有很多理由可以使用 PHP 创建你的程序。你可能对学习 PHP 感兴趣，因为你想构建一个包含一些交互元素的网站。

### Web 世界中的 PHP

PHP 用于构建网站。PHP 程序与运行在桌面电脑上供单个人使用的程序不同，它通常运行在 Web 服务器上，并由许多使用电脑上网络浏览器的用户访问。本节将解释 PHP 如何调整到 Web 服务器和网络浏览器之间的交互中。

当你坐在电脑前，并借助 `Firefox` 或 `Safari` 等浏览器打开一个页面时，你可能会导致你的电脑和其他任何电脑之间通过互联网发生一个小小的对话。Web 服务器读取你用 PHP 编写的程序。这些程序就像是你通过 PHP 传给 Web 服务器的简单指令。Web 服务器会决定做什么。

PHP 既指解释器，也指编程语言。PHP 被称为服务端语言，因为它倾向于运行在特定的 Web 服务器上。像 `Flash` 和 `JavaScript` 等技术和语言被称为客户端，因为它们运行在桌面 PC 或网络客户端上。PHP 程序中提供的指令会导致解释器输出一个网页。指令触发网络浏览器执行诸如弹出新窗口等的操作。一旦网络浏览器将生成的网页发送给客户端，PHP 似乎就离场了。如果页面内容包含 `JavaScript`，`JavaScript` 会运行，但与生成该页面的 PHP 程序保持断开状态。

由 PHP 生成的动态页面就像写给世界另一端朋友的一封信。你可以将脑海中的任何内容添加到页面中，并发送给世界另一边的朋友。信的内容是为发送给的特定人员定制的。一旦信件放入邮箱，你就无法更改它了。它会立即飞向目的地。你无法在朋友阅读时对其修改。

### 为什么选择 PHP？

PHP 是免费的。无论你是在旧 PC 还是价值百万美元的超级计算机上运行解释器，你都不需要支付任何许可费、维护费、升级费和支持费。大多数 `Linux` 发行版都预装了 PHP。如果你的系统没有安装，你可能正在使用其他操作系统，如 `Windows`。作为开源项目之一，PHP 允许任何人检查它。即使你缺乏 PHP 的技术知识，你也可以派人为你进行调查。

### 安装 PHP

在接下来的章节中，我将解释在你的电脑操作系统上安装 PHP 的不同步骤。

#### 安装 Web 服务器

你不能像运行 `HTML` 那样直接在浏览器中运行 PHP。如果你想运行 PHP，你需要在电脑系统上安装一个服务器，以便浏览器可以解析 PHP 脚本，然后对数据库运行若干条 `MySQL` 查询以返回结果。你也可以使用支持 `MySQL` 和 `PHP` 的主机，让他们将将其上传到服务器并允许你测试你的网站。你可以在你的电脑系统上安装不同的服务器，如 `WAMP`、`XAMP` 和 `MAMP`。

我将解释适用于 `Windows` 操作系统的 `XAMP` 安装过程。它是一个适用于 `Windows`、`Linux` 和 `Mac` 的完全免费开源平台 Web 服务器包。该过程的第一步是下载最新版本的 `XAMP`。一旦下载完成，你需要在电脑上找到该文件。

#### 文本编辑器

在接下来的章节中，我将解释在你的操作系统上安装 PHP 的不同步骤。你不能像运行 `HTML` 那样直接在浏览器中运行 PHP。如果你想运行 PHP，你需要在电脑系统上安装一个服务器，以便浏览器可以解析 PHP 脚本，然后对数据库运行若干条 `MySQL` 查询以返回结果。你也可以使用支持 `MySQL` 和 `PHP` 的主机，让他们将其上传到服务器并允许你测试你的网站。你可以在你的电脑系统上安装不同的服务器，如 `WAMP`、`XAMP` 和 `MAMP`。

我将解释适用于 `Windows` 操作系统的 `XAMP` 安装过程。它是一个适用于 `Windows`、`Linux` 和 `Mac` 的完全免费开源平台 Web 服务器包。该过程的第一步是下载最新版本的 `XAMP`。一旦下载完成，你需要在电脑上找到该文件。

#### 控制面板

在接下来的章节中，我将解释在你的电脑操作系统上安装 PHP 的不同步骤。你不能像运行 `HTML` 那样直接在浏览器中运行 PHP。如果你想运行 PHP，你需要在电脑系统上安装一个服务器，以便浏览器可以解析 PHP 脚本，然后对数据库运行若干条 `MySQL` 查询以返回结果。你也可以使用支持 `MySQL` 和 `PHP` 的主机，让他们将其上传到服务器并允许你测试你的网站。你可以在你的电脑系统上安装不同的服务器，如 `WAMP`、`XAMP` 和 `MAMP`。

#### 变量

在接下来的章节中，我将解释在你的电脑操作系统上安装 PHP 的不同步骤。你不能像运行 `HTML` 那样直接在浏览器中运行 PHP。如果你想运行 PHP，你需要在电脑系统上安装一个服务器，以便浏览器可以解析 PHP 脚本，然后对数据库运行若干条 `MySQL` 查询以返回结果。你也可以使用支持 `MySQL` 和 `PHP` 的主机，让他们将其上传到服务器并允许你测试你的网站。你可以在你的电脑系统上安装不同的服务器，如 `WAMP`、`XAMP` 和 `MAMP`。

#### 常量

在接下来的章节中，我将解释在你的电脑操作系统上安装 PHP 的不同步骤。你不能像运行 `HTML` 那样直接在浏览器中运行 PHP。如果你想运行 PHP，你需要在电脑系统上安装一个服务器，以便浏览器可以解析 PHP 脚本，然后对数据库运行若干条 `MySQL` 查询以返回结果。你也可以使用支持 `MySQL` 和 `PHP` 的主机，让他们将其上传到服务器并允许你测试你的网站。你可以在你的电脑系统上安装不同的服务器，如 `WAMP`、`XAMP` 和 `MAMP`。

#### 字符串拼接

在接下来的章节中，我将解释在你的电脑操作系统上安装 PHP 的不同步骤。你不能像运行 `HTML` 那样直接在浏览器中运行 PHP。如果你想运行 PHP，你需要在电脑系统上安装一个服务器，以便浏览器可以解析 PHP 脚本，然后对数据库运行若干条 `MySQL` 查询以返回结果。你也可以使用支持 `MySQL` 和 `PHP` 的主机，让他们将其上传到服务器并允许你测试你的网站。你可以在你的电脑系统上安装不同的服务器，如 `WAMP`、`XAMP` 和 `MAMP`。

#### 常量

在接下来的章节中，我将解释在你的电脑操作系统上安装 PHP 的不同步骤。你不能像运行 `HTML` 那样直接在浏览器中运行 PHP。如果你想运行 PHP，你需要在电脑系统上安装一个服务器，以便浏览器可以解析 PHP 脚本，然后对数据库运行若干条 `MySQL` 查询以返回结果。你也可以使用支持 `MySQL` 和 `PHP` 的主机，让他们将其上传到服务器并允许你测试你的网站。你可以在你的电脑系统上安装不同的服务器，如 `WAMP`、`XAMP` 和 `MAMP`。

#### 运算符

PHP 使用不同的运算符来对值和变量执行各种操作。我们现在将以分组的形式查看 PHP 使用的不同运算符。某些运算符会对值执行特定的数学运算并返回计算结果。

- `$a + $b` 用于计算两个变量之和。
- `$a - $b` 用于计算两个变量之差。
- `$a * $b` 用于计算两个变量之积。
- `$a / $b` 用于计算两个变量之商。
- `$a / $b` 用于计算两个变量的余数。
- `$a ** $b` 用于计算两个变量的幂。
- `$a = $b` 用于获取 `$b` 的值并将其赋值给 `$a`。

## 第二章：表达式与控制

上一章节向你介绍了 PHP 的基础知识，如安装框架和 PHP 变量。本章将带你了解 PHP 编程是如何工作的，以及你如何控制程序的执行流。

### 表达式

现在我将从 PHP 的基础部分开始。表达式是值、运算符、变量和函数的组合，并产生一个值。你可以通过组合如 `OR`、`AND` 和 `XOR` 等布尔运算符来编写表达式。在接下来的示例中，我将在以下代码块中解释简单的表达式。

```html
<html>
<head>
<title>This is a PHP web page</title>
</head>
<body>
<?php
echo "e: \[" . (80 > 9) . "\]\\n";
echo "f: \[" . (10 == 6) . "\]\\n";
echo "g: \[" . (5 == 0) . "\]\\n";
echo "i: \[" . (2 == 2) . "\]\\n";
?>
</body>
</html>
```

```bash
php main.php
```

```html
<html>
<head>
<title>This is a PHP web page</title>
</head>
<body>
e: [1]
f: []
g: []
i: [1]
</body>
</html>
```

你也可以通过以下代码获取 `true` 和 `false` 的输出。

```html
<html>
<head>
<title>This is a PHP web page</title>
</head>
<body>
<?php
echo "e: \[" . TRUE . "\]\\n";
echo "f: \[" . FALSE . "\]\\n";
?>
</body>
</html>
```

```bash
php main.php
```

```html
<html>
<head>
<title>This is a PHP web page</title>
</head>
<body>
e: [1]
f: []
</body>
</html>
```

在某些语言中，`FALSE` 可能被定义为 `-1` 或零，因此在其他语言中，你应该验证此布尔表达式的定义。

### 关系运算符

关系运算符接收两个操作数。它测试这些操作数并返回 `FALSE` 或 `TRUE` 的布尔结果。三类关系运算符 `逻辑`、`相等` 和 `比较` 如下：

#### 等于

相等运算符是 `==`。至关重要的是不要将其与单等号赋值运算符混淆。第一个语句分配一个特定值，第二个语句在表达式中对其测试以检查相等性。

```html
<html>
<head>
<title>This is a PHP web page</title>
</head>
<body>
<?php
$month = "June";
if ($month == "June") echo "The summer season has arrived. It is time to go to the beach.";
?>
</body>
</html>
```

```bash
php main.php
```

```html
<html>
<head>
<title>This is a PHP web page</title>
</head>
<body>
The summer season has arrived. It is time to go to the beach.
</body>
</html>
```

通过返回 `TRUE` 或 `FALSE`，相等运算符允许你在 `if` 语句的帮助下测试条件。然而，PHP 被视为弱类型语言。如果相等表达式的两个操作数属于不同类型，PHP 将它们转换为合理的形式。任何由数字组成的字符串在与数字比较时都会转换为数字。

#### 比较运算符

通过使用比较运算符，你可以测试不仅是相等还有不等。PHP 在你构建网站时提供了大于、小于等选项供使用。

```html
<html>
<head>
<title>This is a PHP web page</title>
</head>
<body>
<?php
$x = 20;
$y = 35;
if ($x > $y) echo "$x is greater than $y\\n";
if ($x < $y) echo "$x is less than $y\\n";
if ($x >= $y) echo "$x is greater than or equal to $y\\n";
if ($x <= $y) echo "$x is less than or equal to $y\\n";
?>
</body>
</html>
```

```bash
php main.php
```

```html
<html>
<head>
<title>This is a PHP web page</title>
</head>
<body>
20 is less than 35
20 is less than or equal to 35
</body>
</html>
```

#### 逻辑运算符

逻辑运算符产生假或真的的结果，因此它们也被称为布尔运算符。共有四种这样的运算符。

- `AND`
- `OR`
- `XOR`
- `NOT`

```html
<html>
<head>
<title>这是一个 PHP 网页页面</title>
</head>
<body>
<?php
$x = 1;
$y = 0 ;
echo ($x AND $y) . "\n";
echo ($x or $y) . "<\n";
echo ($x XOR $y) . "\n";
echo !$x . "\n";
?>
</body>
</html>
```

```bash
php main.php
```

```html
<html>
<head>
<title>这是一个 PHP 脚本</title>
</head>
<body> 1< 1 </body>
</html>
```

## PHP 条件语句

PHP 条件语句会改变程序的执行流。它们允许你对不同的事物提出某些问题，然后以多种方式对答案做出响应。条件语句在动态网站页面中占据着核心位置，因为它们让观众每次访问你的网页时都能轻松获得不同的输出。条件语句有三种类型：`if` 语句、`?` 运算符和 `switch` 语句。

### if 语句

控制程序流的一种方法是使用 `if` 语句。`if` 语句的内容可以是一个有效的 PHP 表达式，包括比较、等值以及函数的返回值。当你希望让 PHP 在 `if` 条件为真（TRUE）时执行的操作，需要放在大括号 `{}` 中。如果你只需要执行一条语句，可以忽略大括号。然而，如果你始终使用大括号，你就可以避免寻找那些难以排查的 bug。

```html
<html>
<head>
<title>这是一个 PHP 脚本</title>
</head>
<body>
<?php
if ($my_account_balance < 1000) {
    $my_money = 10000;
    $my_account_balance += $my_money;
}
?>
</body>
</html>
```

### else 语句

当条件语句不为真（TRUE）时，你可能需要继续执行主代码，但你可能也想做其他事情。这就是 `else` 语句大显身场的地方。在 `if-else` 语句的帮助，如果条件为真，则执行第一个条件语句；如果为假（FALSE），则执行第二个。两个选择中必须有一个被执行。在当前情况下，两个都会执行。下面的示例展示了 `if-else` 结构。

```html
<html>
<head>
<title>这是一个 PHP 脚本</title>
</head>
<body>
<?php
$greetings_time = date("H");
if ($greetings_time < "12") {
    echo "祝你有美好的一天!";
} else {
    echo "祝你有一个完美的夜晚!";
}
?>
</body>
</html>
```

```bash
php main.php
```

```html
<html>
<head>
<title>这是一个 PHP 脚本</title>
</head>
<body> 祝你有美好的一天! </body>
</html>
```

### if….elseif….else 语句

这种结构比前两个要长，并且为两个以上的条件执行多段代码。它非常适合测试多种可能性。查看下面的示例中代码是如何工作的。

```html
<html>
<head>
<title>这是一个 PHP 脚本</title>
</head>
<body>
<?php
$greetings_time = date("H");
if ($greetings_time < "12") {
    echo "祝你有一个美好的早晨!";
} elseif($greetings_time < "20") {
    echo "祝你有一个良好的午后!";
} else {
    echo "祝你有一个完美的夜晚!";
}
?>
</body>
</html>
```

```bash
php main.php
```

```html
<html>
<head>
<title>这是一个 PHP 脚本</title>
</head>
<body> 祝你有一个美好的早晨! </body>
</html>
```

我将修改时间来测试其他条件。我会用 `10` 填充代码。

```html
<html>
<head>
<title>这是一个 PHP 脚本</title>
</head>
<body>
<?php
$greetings_time = date("H");
if ($greetings_time < "12") {
    echo "祝你有美好的一天!";
} elseif($greetings_time < "20") {
    echo "祝你有一个良好的午后!";
} else {
    echo "祝你有一个完美的夜晚!";
}
?>
</body>
</html>
```

```bash
php main.php
```

```html
<html>
<head>
<title>这是一个 PHP 脚本</title>
</head>
<body> 祝你有美好的一天! </body>
</html>
```

我将用 `15` 填充代码。



```html
<html>
<head>
<title>这是一个 PHP 脚本</title>
</head>
<body>
<?php
$greetings_time = date("H");
if ($greetings_time < "12") {
    echo "祝你有美好的一天!";
} elseif($greetings_time < "20") {
    echo "祝你有一个良好的午后!";
} else {
    echo "祝你有一个完美的夜晚!";
}
?>
</body>
</html>
```

我将用 `23` 填充代码。

```html
<html>
<head>
<title>这是一个 PHP 脚本</title>
</head>
<body>
<?php
$greetings_time = date("H");
if ($greetings_time < "12") {
    echo "祝你有美好的一天!";
} elseif($greetings_time < "20") {
    echo "祝你有一个良好的午后!";
} else {
    echo "祝你有一个完美的夜晚!";
}
?>
</body>
</html>
```

## switch 语句

当你在处理多个情况时，`switch` 语句非常有用。通过 `switch` 语句，你可以从许多情况中选择一个执行块。查看以下示例：

```html
<html>
<head>
<title>这是一个 PHP 脚本</title>
</head>
<body>
<?php
$states = "Texas";
switch ($states) {
    case "Texas":
        echo "我访问过德克萨斯州";
        break;
    case "California":
        echo "我访问过加利福尼亚州";
        break;
    case "Los Angeles":
        echo "我访问过洛杉矶";
        break;
    case "Florida":
        echo "我访问过佛罗里达州";
        break;
    case "New York":
        echo "我访问过纽约州";
        break;
    case "Las Vegas":
        echo "我访问过拉斯维加斯";
        break;
    case "Virginia":
        echo "我访问过弗吉尼亚州";
        break;
    default:
        echo "我没有访问过任何州";
}
?>
</body>
</html>
```

### 替代语法

有一种你可以使用的替代语法来获得相同的结果。你可以将大括号替换为单冒号和 `endswitch` 命令。它的工作方式和之前一样。

```html
<html>
<head>
<title>这是一个 PHP 脚本</title>
</head>
<body>
<?php
$states = "New York";
switch ($states):
    case "Texas":
        echo "我访问过美国的德克萨斯州";
        break;
    case "California":
        echo "我访问过美国的加利福尼亚州";
        break;
    case "Los Angeles":
        echo "我访问过美国的洛杉矶";
        break;
    case "Florida":
        echo "我访问过美国的佛罗里达州";
        break;
    case "New York":
        echo "我访问过美国的纽约州";
        break;
    case "Las Vegas":
        echo "我访问过美国的拉斯维加斯";
        break;
    case "Virginia":
        echo "我访问过美国的弗吉尼亚州";
        break;
    default:
        echo "我没有访问过美国的任何州，这意味着我还没有访问过美国";
endswitch;
?>
</body>
</html>
```

# 第三章：PHP 循环

计算机最优秀的特性之一就是它们倾向于不知疲倦且快速地重复某些计算任务。你可能希望软件重复某些代码，直到你从中推导出某些结果。PHP 有不同类型的循环结构，为实现这种操作提供了完美的方法。一旦进入代码块，只有在条件正确的情况下你才能退出。

## while 循环

`while` 循环在特定条件保持为真时会多次执行代码块。以下代码执行同样的操作。只要我设置的条件保持为真，它就会一直运行。

```html
<html>
<head>
  <title>这是我的 PHP 脚本</title>
</head>
<body>
  <?php
  $a = 1;
  while ($a <= 25) {
    echo "The requisite value of the variable a should be: " . $a . "\n";
    $a++;
  }
  ?>
</body>
</html>
```

```bash
php main.php
```

```html
<html>
<head>
  <title>这是我的 PHP 脚本</title>
</head>
<body>
  The requisite value of the variable a should be: 1
  The requisite value of the variable a should be: 2
  The requisite value of the variable a should be: 3
  The requisite value of the variable a should be: 4
  The requisite value of the variable a should be: 5
  The requisite value of the variable a should be: 6
  The requisite value of the variable a should be: 7
  The requisite value of the variable a should be: 8
  The requisite value of the variable a should be: 9
  The requisite value of the variable a should be: 10
  The requisite value of the variable a should be: 11
  The requisite value of the variable a should be: 12
  The requisite value of the variable a should be: 13
  The requisite value of the variable a should be: 14
  The requisite value of the variable a should be: 15
  The requisite value of the variable a should be: 16
  The requisite value of the variable a should be: 17
  The requisite value of the variable a should be: 18
  The requisite value of the variable a should be: 19
  The requisite value of the variable a should be: 20
  The requisite value of the variable a should be: 21
  The requisite value of the variable a should be: 22
  The requisite value of the variable a should be: 23
  The requisite value of the variable a should be: 24
  The requisite value of the variable a should be: 25
</body>
</html>
```

你可以看到，循环只有在条件为假时才会停止。我们可以通过从最后一行切掉 `++$a` 并将其放在 `while` 关键字旁边的括号内来改变 `while` 循环。这样它就变成了 `while` 循环条件表达式的一部分。PHP 在所有 `while` 循环迭代开始时都会检查 `$a` 变量，在此之前观察到它首先递增了变量并与其值进行了比较。唯一的区别是循环将从二开始。要将其调整为一，你需要对变量的初始值进行调整。

```html
<html>
<head>
  <title>这是我的 PHP 脚本</title>
</head>
<body>
  <?php
  $a = 0;
  while ($a++ <= 25) {
    echo "The requisite value of the variable a should be: " . $a . "\n";
  }
  ?>
</body>
</html>
```

```bash
php main.php
```

```html
<html>
<head>
  <title>这是我的 PHP 脚本</title>
</head>
<body>
  The requisite value of the variable a should be: 1
  The requisite value of the variable a should be: 2
  The requisite value of the variable a should be: 3
  The requisite value of the variable a should be: 4
  The requisite value of the variable a should be: 5
  The requisite value of the variable a should be: 6
  The requisite value of the variable a should be: 7
  The requisite value of the variable a should be: 8
  The requisite value of the variable a should be: 9
  The requisite value of the variable a should be: 10
  The requisite value of the variable a should be: 11
  The requisite value of the variable a should be: 12
  The requisite value of the variable a should be: 13
  The requisite value of the variable a should be: 14
  The requisite value of the variable a should be: 15
  The requisite value of the variable a should be: 16
  The requisite value of the variable a should be: 17
  The requisite value of the variable a should be: 18
  The requisite value of the variable a should be: 19
  The requisite value of the variable a should be: 20
  The requisite value of the variable a should be: 21
  The requisite value of the variable a should be: 22
  The requisite value of the variable a should be: 23
  The requisite value of the variable a should be: 24
  The requisite value of the variable a should be: 25
  The requisite value of the variable a should be: 26
</body>
</html>
```

## do...while 循环

这是 `while` 循环的一种变体。当你需要一个代码块执行一次然后推入条件时，使用它。参见以下代码。

```html
<html>
<head>
  <title>这是我的 PHP 脚本</title>
</head>
<body>
  <?php
  $a = 0;
  echo "The requisite value of the variable a should be: " . $a . "\n";
  while ($a++ <= 25)
  ?>
</body>
</html>
```

```bash
php main.php
```

```html
<html>
<head>
  <title>这是我的 PHP 脚本</title>
</head>
<body>
  The requisite value of the variable a should be: 0
  The requisite value of the variable a should be: 1
  The requisite value of the variable a should be: 2
  The requisite value of the variable a should be: 3
  The requisite value of the variable a should be: 4
  The requisite value of the variable a should be: 5
  The requisite value of the variable a should be: 6
  The requisite value of the variable a should be: 7
  The requisite value of the variable a should be: 8
  The requisite value of the variable a should be: 9
  The requisite value of the variable a should be: 10
  The requisite value of the variable a should be: 11
  The requisite value of the variable a should be: 12
  The requisite value of the variable a should be: 13
  The requisite value of the variable a should be: 14
  The requisite value of the variable a should be: 15
  The requisite value of the variable a should be: 16
  The requisite value of the variable a should be: 17
  The requisite value of the variable a should be: 18
  The requisite value of the variable a should be: 19
  The requisite value of the variable a should be: 20
  The requisite value of the variable a should be: 21
  The requisite value of the variable a should be: 22
  The requisite value of the variable a should be: 23
  The requisite value of the variable a should be: 24
  The requisite value of the variable a should be: 25
  The requisite value of the variable a should be: 26
</body>
</html>
```

你唯一应该注意的是循环是从 0 开始的。这是因为 PHP 编辑器立即执行代码，没有递增变量的机会。代码看起来非常相似。如果你有多个语句要填充到代码块中，将使用大括号。

```html
<html>
<head>
  <title>这是我的 PHP 脚本</title>
</head>
<body>
  <?php
  $a = 0;
  do {
    echo "The requisite value of the variable a should be: " . $a . "\n";
    echo "The do...while loop will go on.\n";
  } while ($a++ <= 25)
  ?>
</body>
</html>
```

```bash
php main.php
```



```html
<html>
<head>
  <title>这是我的 PHP 脚本</title>
</head>
<body>
  The requisite value of the variable a should be: 0
  The do...while loop will go on.
  The requisite value of the variable a should be: 1
  The do...while loop will go on.
  The requisite value of the variable a should be: 2
  The do...while loop will go on.
  The requisite value of the variable a should be: 3
  The do...while loop will go on.
  The requisite value of the variable a should be: 4
  The do...while loop will go on.
  The requisite value of the variable a should be: 5
  The do...while loop will go on.
  The requisite value of the variable a should be: 6
  The do...while loop will go on.
  The requisite value of the variable a should be: 7
  The do...while loop will go on.
  The requisite value of the variable a should be: 8
  The do...while loop will go on.
  The requisite value of the variable a should be: 9
  The do...while loop will go on.
  The requisite value of the variable a should be: 10
  The do...while loop will go on.
  The requisite value of the variable a should be: 11
  The do...while loop will go on.
  The requisite value of the variable a should be: 12
  The do...while loop will go on.
  The requisite value of the variable a should be: 13
  The do...while loop will go on.
  The requisite value of the variable a should be: 14
  The do...while loop will go on.
  The requisite value of the variable a should be: 15
  The do...while loop will go on.
  The requisite value of the variable a should be: 16
  The do...while loop will go on.
  The requisite value of the variable a should be: 17
  The do...while loop will go on.
  The requisite value of the variable a should be: 18
  The do...while loop will go on.
  The requisite value of the variable a should be: 19
  The do...while loop will go on.
  The requisite value of the variable a should be: 20
  The do...while loop will go on.
  The requisite value of the variable a should be: 21
  The do...while loop will go on.
  The requisite value of the variable a should be: 22
  The do...while loop will go on.
  The requisite value of the variable a should be: 23
  The do...while loop will go on.
  The requisite value of the variable a should be: 24
  The do...while loop will go on.
  The requisite value of the variable a should be: 25
  The do...while loop will go on.
  The requisite value of the variable a should be: 26
</body>
</html>
```

## for 循环

PHP 代码中还有另一种循环 `for`。它是最强大的循环，因为它允许你在循环内部设置变量、在迭代时测试条件并修改变量。`for` 循环的第一部分是初始化。在 `for` 循环第一次迭代开始时，初始化表达式被执行。计数从 0 开始。每次测试条件时，如果发现条件为真，循环就会继续。最后，当循环结束时，它开始重复。你可以对计数器进行操作。参见以下代码。

```html
<html>
<head>
  <title>这是我的 PHP 脚本</title>
</head>
<body>
  <?php
  for ($a = 1; $a <= 25; $a++) {
    echo "The requisite value of the variable a should be: " . $a . "\n";
    echo "The do...while loop will go on.\n";
  }
  ?>
</body>
</html>
```

```bash
php main.php
```

```html
<html>
<head>
  <title>这是我的 PHP 脚本</title>
</head>
<body>
  The requisite value of the variable a should be: 1
  The do...while loop will go on.
  The requisite value of the variable a should be: 2
  The do...while loop will go on.
  The requisite value of the variable a should be: 3
  The do...while loop will go on.
  The requisite value of the variable a should be: 4
  The do...while loop will go on.
  The requisite value of the variable a should be: 5
  The do...while loop will go on.
  The requisite value of the variable a should be: 6
  The do...while loop will go on.
  The requisite value of the variable a should be: 7
  The do...while loop will go on.
  The requisite value of the variable a should be: 8
  The do...while loop will go on.
  The requisite value of the variable a should be: 9
  The do...while loop will go on.
  The requisite value of the variable a should be: 10
  The do...while loop will go on.
  The requisite value of the variable a should be: 11
  The do...while loop will go on.
  The requisite value of the variable a should be: 12
  The do...while loop will go on.
  The requisite value of the variable a should be: 13
  The do...while loop will go on.
  The requisite value of the variable a should be: 14
  The do...while loop will go on.
  The requisite value of the variable a should be: 15
  The do...while loop will go on.
  The requisite value of the variable a should be: 16
  The do...while loop will go on.
  The requisite value of the variable a should be: 17
  The do...while loop will go on.
  The requisite value of the variable a should be: 18
  The do...while loop will go on.
  The requisite value of the variable a should be: 19
  The do...while loop will go on.
  The requisite value of the variable a should be: 20
  The do...while loop will go on.
  The requisite value of the variable a should be: 21
  The do...while loop will go on.
  The requisite value of the variable a should be: 22
  The do...while loop will go on.
  The requisite value of the variable a should be: 23
  The do...while loop will go on.
  The requisite value of the variable a should be: 24
  The do...while loop will go on.
  The requisite value of the variable a should be: 25
  The do...while loop will go on.
</body>
</html>
```

分号分隔了 `for` 循环中的所有的表达式。在 `for` 循环第一次迭代开始时，初始化表达式被执行。计数从 0 开始。每次测试条件时，如果发现条件为真，循环就会继续。最后，当循环结束时，它停止执行代码块。

## for each 循环

一种遍历数组中找到的每个元素的循环被称为 `foreach` 循环。

```html
<html>
<head>
  <title>这是我的 PHP 脚本</title>
</head>
<body>
  <?php
  $states = array("New York", "Los Angles", "Florida", "California", "Texas", "Virginia", "South Dakota", "North Dakota");
  foreach ($states as $states) {
    echo "I have visited " . $states . "\n";
  }
  ?>
</body>
</html>
```

## break 语句

如果你已经开始编程，你可能听说过 `break` 语句。我在之前的 `switch` 语句中用过它。`break` 语句是跳出循环的最佳方法。

```html
<html>
<head>
  <title>这是我的 PHP 脚本</title>
</head>
<body>
  <?php
  for ($a = 1; $a <= 25; $a++) {
    if ($a == 20) {
      break;
    }
    echo "The requisite value of the variable a should be: " . $a . "\n";
    echo "The do...while loop will go on.\n";
  }
  ?>
</body>
</html>
```

### continue 语句

`continue` 语句的作用与 `break` 语句类似，它们都会中断迭代。如果条件为真，它会中断当前循环，但继续执行剩余的代码，而不是直接跳出循环。这就像是在旅途中途暂停片刻，然后继续出发。

```html
<html>
<head>
    <title>This is my PHP Script</title>
</head>
<body>
<?php 
for ($a = 1; $a <= 15; $a++) { 
    if ($a == 10) { 
        continue; 
    } 
    echo "The requisite value of the variable a should be: " . $a . "\n";
    echo "The do...while loop will go on.\n"; 
} 
?>
</body>
</html>
```

`php main.php`

```html
<html>
<head>
    <title>This is my PHP Script</title>
</head>
<body>
The requisite value of the variable a should be: 1
The do...while loop will go on.
The requisite value of the variable a should be: 2
The do...while loop will go on.
The requisite value of the variable a should be: 3
The do...while loop will go on.
The requisite value of the variable a should be: 4
The do...while loop will go on.
The requisite value of the variable a should be: 5
The do...while loop will go on.
The requisite value of the variable a should be: 6
The do...while loop will go on.
The requisite value of the variable a should be: 7
The do...while loop will go on.
The requisite value of the variable a should be: 8
The do...while loop will go on.
The requisite value of the variable a should be: 9
The do...while loop will go on.
The requisite value of the variable a should be: 11
The do...while loop will go on.
The requisite value of the variable a should be: 12
The do...while loop will go on.
The requisite value of the variable a should be: 13
The do...while loop will go on.
The requisite value of the variable a should be: 14
The do...while loop will go on.
The requisite value of the variable a should be: 15
The do...while loop will go on.
</body>
</html>
```

你可以看到，`continue` 语句在数字 10 处中断了代码，并继续执行块的其他部分。

## while 循环中的 break 和 continue 语句

在上面的代码中，你看到了 `for` 循环中 `break` 和 `continue` 语句的使用。现在我将解释如何在 `while` 循环中整合这两个语句。



```html
<html>
<head>
    <title>This is my PHP Script</title>
</head>
<body>
<?php 
$a = 0; 
while($a < 20) { 
    if ($a == 10) { 
        break; 
    } 
    echo "The requisite value of the variable a should be: " . $a . "\n";
    echo "The do...while loop will go on.\n"; 
    $a++; 
} 
?>
</body>
</html>
```

`php main.php`

```html
<html>
<head>
    <title>This is my PHP Script</title>
</head>
<body>
The requisite value of the variable a should be: 0
The do...while loop will go on.
The requisite value of the variable a should be: 1
The do...while loop will go on.
The requisite value of the variable a should be: 2
The do...while loop will go on.
The requisite value of the variable a should be: 3
The do...while loop will go on.
The requisite value of the variable a should be: 4
The do...while loop will go on.
The requisite value of the variable a should be: 5
The do...while loop will go on.
The requisite value of the variable a should be: 6
The do...while loop will go on.
The requisite value of the variable a should be: 7
The do...while loop will go on.
The requisite value of the variable a should be: 8
The do...while loop will go on.
The requisite value of the variable a should be: 9
The do...while loop will go on.
</body>
</html>
```

现在我将在上述代码块中添加 `continue` 语句。它将跳过 10 并跳转到 11 继续执行代码。

```html
<html>
<head>
    <title>This is my PHP Script</title>
</head>
<body>
<?php 
$a = 0; 
while($a < 20) { 
    if ($a == 10) { 
        $a++; 
        continue; 
    } 
    echo "The requisite value of the variable a should be: " . $a . "\n";
    echo "The do...while loop will go on.\n"; 
    $a++; 
} 
?>
</body>
</html>
```

`php main.php`

```html
<html>
<head>
    <title>This is my PHP Script</title>
</head>
<body>
The requisite value of the variable a should be: 0
The do...while loop will go on.
The requisite value of the variable a should be: 1
The do...while loop will go on.
The requisite value of the variable a should be: 2
The do...while loop will go on.
The requisite value of the variable a should be: 3
The do...while loop will go on.
The requisite value of the variable a should be: 4
The do...while loop will go on.
The requisite value of the variable a should be: 5
The do...while loop will go on.
The requisite value of the variable a should be: 6
The do...while loop will go on.
The requisite value of the variable a should be: 7
The do...while loop will go on.
The requisite value of the variable a should be: 8
The do...while loop will go on.
The requisite value of the variable a should be: 9
</body>
</html>
```

# 定义函数

函数定义以关键字 `function` 开始。在名称之后，你必须输入一个字母或下划线。之后，你可以输入不同的字母、下划线或数字。你还必须为函数加上括号。函数名是区分大小写灵敏的，这意味着 `print` 和 `PRINT` 是两个不同的函数。函数语句可能包含多个 `return` 语句，这会强制你的函数停止执行并将其返回给调用代码。如果你向 `return` 语句附加一个值，调用代码可能会获取到它。

```html
<html>
<head>
<title>This is my PHP Script</title>
</head>
<body>
<?php 
function greetings() { 
    echo "I wish you a good morning on this beautiful shiny day!"; 
}
greetings(); 
// I am calling the function 
?>
</body>
</html>
```

```php
main.php
```

```html
<html>
<head>
<title>This is my PHP Script</title>
</head>
<body> I wish you a good morning on this beautiful shiny day!</body>
</html>
```

## PHP 函数参数

你可以通过参数向函数传递信息。函数中的参数就像变量。你可以在括号内指定参数，并根据需要添加尽可能多的参数。你应该用逗号将它们分开。我将创建一个带有一个参数的函数。我将从那里开始，通过同一个参数向函数传递信息。

```html
<html>
<head>
<title>This is my PHP Script</title>
</head>
<body>
<?php 
function greetings($name) { 
    echo "$name, I wish you a good morning on this beautiful shiny day!\\n"; 
}
greetings('James'); 
// I am calling the function 
greetings('Jasmine'); 
greetings('Martha'); 
greetings('Tim'); 
greetings('David'); 
greetings('Chelsea'); 
?>
</body>
</html>
```

```php
main.php
```

```html
<html>
<head>
<title>This is my PHP Script</title>
</head>
<body> James, I wish you a good morning on this beautiful shiny day! Jasmine, I wish you a good morning on this beautiful shiny day! Martha, I wish you a good morning on this beautiful shiny day! Tim, I wish you a good morning on this beautiful shiny day! David, I wish you a good morning on this beautiful shiny day! Chelsea, I wish you a good morning on this beautiful shiny day!</body>
</html>
```

## 多参数

在下面的示例中，我将提供一个多个参数的示例。

```html
<html>
<head>
<title>This is my PHP Script</title>
</head>
<body>
<?php 
function greetings($name, $day) { 
    echo "$name, I wish you a good morning on this beautiful shiny day!\\n"; 
    echo "Anyway, we shall start working on $day.\\n"; 
}
greetings('James', 'Monday'); 
// I am calling the function 
greetings('Jasmine', 'Tuesday'); 
greetings('Martha', 'Wednesday'); 
greetings('Tim', 'Thursday'); 
greetings('David', 'Friday'); 
greetings('Chelsea', 'Saturday'); 
?>
</body>
</html>
```

```php
main.php
```

```html
<html>
<head>
<title>This is my PHP Script</title>
</head>
<body> James, I wish you a good morning on this beautiful shiny day! Anyway, we shall start working on Monday. Jasmine, I wish you a good morning on this beautiful shiny day! Anyway, we shall start working on Tuesday. Martha, I wish you a good morning on this beautiful shiny day! Anyway, we shall start working on Wednesday. Tim, I wish you a good morning on this beautiful shiny day! Anyway, we shall start working on Thursday. David, I wish you a good morning on this beautiful shiny day! Anyway, we shall start working on Friday. Chelsea, I wish you a good morning on this beautiful shiny day! Anyway, we shall start working on Saturday.</body>
</html>
```

PHP 是弱类型的，你不需要告诉 PHP 类型。你可以向字符串传递整数，PHP 以这种方式处理它们。

```html
<html>
<head>
<title>This is my PHP Script</title>
</head>
<body>
<?php 
function addingNumbers($x, $y) { 
    return $x + $y; 
}
echo "5 + 10 = " . addingNumbers(5, 10); 
?>
</body>
</html>
```

## 默认值

就像其他语言一样，你可以为参数设置默认值。如果不提供参数，PHP 将提取默认值。

```html
<html>
<head>
<title>This is my PHP Script</title>
</head>
<body>
<?php 
function greetings($name, $day = "Monday") { 
    echo "$name, I wish you a good morning on this beautiful shiny day!\\n"; 
    echo "Anyway, we shall start working on $day.\\n"; 
}
greetings('James'); 
// I am calling the function 
greetings('Jasmine'); 
greetings('Martha'); 
greetings('Tim'); 
greetings('David'); 
greetings('Chelsea'); 
?>
</body>
</html>
```

## 返回值

你可以通过 `return` 语句让 PHP 返回值。

```html
<html>
<head>
<title>This is my PHP Script</title>
</head>
<body>
<?php 
declare(strict_types=1);
function summing(int $a, int $b) { 
    $c = $a + $b; 
    return $c; 
}
echo "5 + 10 = " . summing(5, 10); 
echo "7 + 33 = " . summing(7, 13); 
echo "2 + 9 = " . summing(2, 4); 
echo "2 + 10 = " . summing(2, 4); 
echo "29 + 14 = " . summing(2, 4); 
echo "82 + 94 = " . summing(2, 4); 
?>
</body>
</html>
```

PHP 支持返回语句的类型声明。与不同函数参数的类型声明一样，当数据类型不匹配时它将显示致命错误。当你想要函数的返回声明类型时，必须在大括号之前添加冒号（`:`）和数据类型。

```php
<?php 
declare(strict_types=1);
function summing(float $a, float $b) : float { 
    return $a + $b; 
}
echo "152 + 105 = " . summing(152, 105); 
echo "77 + 331 = " . summing(77, 331); 
echo "22 + 95 = " . summing(22, 95); 
echo "25 + 49 = " . summing(25, 49); 
echo "2 + 4 = " . summing(2, 4); 
echo "26 + 42 = " . summing(26, 42); 
?>
```

# 第五章：PHP 数组

数组被定义为一组相关的值的集合。它们可以是特定形式提交的数据，例如班级学生的姓名或城市人口列表。本章将引导你如何使用数组。你将学习如何使用 `for` 和 `foreach` 循环来遍历数组。修改数组可能会引入 `explode()` 和 `implode()` 函数，它们可以将不同的数组转换为字符串，并将将字符串转换为数组。你还可以对数组进行排序。

数组包含键和值形式的元素。一个包含蔬菜和水果信息的数组将水果和蔬菜的名称作为键，将类型作为值。如果你有特定的键，可以封装一个包含单个元素的数组。

```php
$vegetables = array("pumpkin", "tomato", "potato", "cabbage", "cauliflower", "ginger", "turmeric", "peas");
echo "Today I plan to cook " . $vegetables[0] . "\n";
echo "Today I plan to cook " . $vegetables[1] . "\n";
echo "Today I plan to cook " . $vegetables[2] . "\n";
echo "Today I plan to cook " . $vegetables[3] . "\n";
echo "Today I plan to cook " . $vegetables[4] . "\n";
echo "Today I plan to cook " . $vegetables[5] . "\n";
echo "Today I plan to cook " . $vegetables[6] . "\n";
echo "Today I plan to cook " . $vegetables[7] . "\n";
```

数组是一种特殊的变量，可以在特定时期内保存多个值。

## 数组的长度

PHP 允许你通过 `count()` 函数计算数组的长度。



```php
$vegetables = array("pumpkin", "tomato", "potato", "cabbage", "cauliflower", "ginger", "turmeric", "peas");
echo count($vegetables);
```

## PHP 索引数组

你可以通过两种方式创建索引数组。你可以通过从 0 开始自动分配索引。你已经在上面的示例中看到了一种方法。我将在接下来的示例中解释另一种方法。

```php
$vegetables[0] = "pumpkin";
$vegetables[1] = "tomato";
$vegetables[2] = "potato";
$vegetables[3] = "cabbage";
$vegetables[4] = "cauliflower";
$vegetables[5] = "ginger";
$vegetables[6] = "turmeric";
$vegetables[7] = "peas";
echo "Today I plan to cook " . $vegetables[0] . "\n";
echo "Today I plan to cook " . $vegetables[1] . "\n";
echo "Today I plan to cook " . $vegetables[2] . "\n";
echo "Today I plan to cook " . $vegetables[3] . "\n";
echo "Today I plan to cook " . $vegetables[4] . "\n";
echo "Today I plan to cook " . $vegetables[5] . "\n";
echo "Today I plan to cook " . $vegetables[6] . "\n";
echo "Today I plan to cook " . $vegetables[7] . "\n";
```

### 遍历索引数组

你可以遍历索引数组并逐个打印值。我将索引数组与`for`循环配合使用以产生我需要的结果。

```php
$vegetables = array("pumpkin", "tomato", "potato", "cabbage", "cauliflower", "ginger", "turmeric", "peas");
$arrlength = count($vegetables);
for($a = 0; $a < $arrlength; $a++) { 
    echo $vegetables[$a];
    echo "\nToday I plan to cook " . $vegetables[0] . "\n";
    echo "Today I plan to cook " . $vegetables[1] . "\n";
    echo "Today I plan to cook " . $vegetables[2] . "\n";
    echo "Today I plan to cook " . $vegetables[3] . "\n";
    echo "Today I plan to cook " . $vegetables[4] . "\n";
    echo "Today I plan to cook " . $vegetables[5] . "\n";
    echo "Today I plan to cook " . $vegetables[6] . "\n";
    echo "Today I plan to cook " . $vegetables[7] . "\n";
}
```

## PHP 关联数组

关联数组使用命名的键。你可以为它们分配任何名称。你可能通过两种方式创建关联数组。

```php
$vegetables = array(
    "pumpkin" => "vegetable", 
    "tomato" => "fruit", 
    "potato" => "vegetable", 
    "cabbage" => "vegetable", 
    "cauliflower" => "vegetable", 
    "orange" => "fruit", 
    "ginger" => "vegetable", 
    "turmeric" => "spice", 
    "peas" => "vegetable"
);
echo "\nToday I plan to cook " . $vegetables['pumpkin'] . "\n";
echo "Today I plan to cook " . $vegetables['tomato'] . "\n";
echo "Today I plan to cook " . $vegetables['potato'] . "\n";
echo "Today I plan to cook " . $vegetables['cabbage'] . "\n";
echo "Today I plan to cook " . $vegetables['cauliflower'] . "\n";
echo "Today I plan to cook " . $vegetables['orange'] . "\n";
echo "Today I plan to cook " . $vegetables['ginger'] . "\n";
echo "Today I plan to cook " . $vegetables['turmeric'] . "\n";
echo "Today I plan to cook " . $vegetables['peas'] . "\n";
```

### 遍历关联数组

在下面的示例中，我将遍历上面创建的关联数组。我将使用`foreach`循环来实现。

```php
$vegetablesfruits = array(
    "pumpkin" => "vegetable", 
    "tomato" => "fruit", 
    "potato" => "vegetable", 
    "cabbage" => "vegetable", 
    "cauliflower" => "vegetable", 
    "orange" => "fruit", 
    "ginger" => "vegetable", 
    "turmeric" => "spice", 
    "peas" => "vegetable"
);
foreach($vegetablesfruits as $x => $x_value) { 
    echo "\nToday I plan to cook " . $x . ", which technically is a $x_value . "\n";
}
```

## 多维数组

多维数组是包含多个数组的数组。PHP 支持深度为四或六层的数组。当你处理二维数组时，你可能需要两个索引来选择特定元素。当你处理三维数组时，你可能需要三个索引。我将创建一个三列的数组；第一列表示汽车名称，第二列表示库存，第三列表示售出的数量。

```php
$middleclasscars = array(
    array("Swift",40,22), 
    array("Vitz",15,15), 
    array("Passo",50,25), 
    array("Cultus",25,15), 
    array("City EXI",30,45), 
    array("Civic",45,15)
);
echo $middleclasscars[0][0].": The cars that are in stock: ".$middleclasscars[0][1].", The cars that have been sold: ".$middleclasscars[0][2].\n";
echo $middleclasscars[1][0].": The cars that are in stock: ".$middleclasscars[1][1].", The cars that have been sold: ".$middleclasscars[1][2].\n";
echo $middleclasscars[2][0].": The cars that are in stock: ".$middleclasscars[2][1].", The cars that have been sold: ".$middleclasscars[2][2].\n";
echo $middleclasscars[3][0].": The cars that are in stock: ".$middleclasscars[3][1].", The cars that have been sold: ".$middleclasscars[3][2].\n";
echo $middleclasscars[4][0].": The cars that are in stock: ".$middleclasscars[4][1].", The cars that have been sold: ".$middleclasscars[4][2].\n";
echo $middleclasscars[5][0].": The cars that are in stock: ".$middleclasscars[5][1].", The cars that have been sold: ".$middleclasscars[5][2].\n";
```

现在我将在另一个`for`循环内部添加一个`for`循环。

```php
$middleclasscars = array (
    array("Swift",40,22),
    array("Vitz",15,15), 
    array("Passo",50,25), 
    array("Cultus",25,15), 
    array("City EXI",30,45), 
    array("Civic",45,15) 
);
for ($rows = 0; $rows < 6; $rows++) { 
    echo "<p><b>This is Row number $rows</b></p>\n";
    echo "<ul>\n"; 
    for ($cols = 0; $cols < 3; $cols++) { 
        echo "<li>".$middleclasscars[$rows][$cols]."</li>\n" 
    } 
    echo "</ul>\n"; 
} 
```

## 数组排序

```php
$vegetables = array("pumpkin", "tomato", "potato", "cabbage", "cauliflower", "ginger", "turmeric", "peas");
sort($vegetables);
$length = count($vegetables);
for($x = 0; $x < $length; $x++) { 
    echo "I am buying " . $vegetables[$x] . " from the vegetable market.";
    echo "\n"; 
}
```

### 下面的示例将数组降序排序。

```php
$vegetables = array("pumpkin", "tomato", "potato", "cabbage", "cauliflower", "ginger", "turmeric", "peas");
rsort($vegetables);
$length = count($vegetables);
for($x = 0; $x < $length; $x++) { 
    echo "I am buying " . $vegetables[$x] . " from the vegetable market.";
}
```

### 下面使用`asort`关键字将数组升序排序。

```php
$vegetables = array("pumpkin", "tomato", "potato", "cabbage", "cauliflower", "ginger", "turmeric", "peas");
asort($vegetables);
$length = count($vegetables);
for($x = 0; $x < $length; $x++) { 
    echo "I am buying " . $vegetables[$x] . " from the vegetable market.";
    echo "\n"; 
}
```

### 下面的示例将根据键对数组进行排序。

```php
$vegetablesfruits = array(
    "pumpkin" => "vegetable", 
    "tomato" => "fruit", 
    "potato" => "vegetable", 
    "cabbage" => "vegetable", 
    "cauliflower" => "vegetable", 
    "orange" => "fruit", 
    "ginger" => "vegetable", 
    "turmeric" => "spice", 
    "peas" => "vegetable"
);
ksort($vegetablesfruits);
foreach($vegetablesfruits as $x => $x_value) { 
    echo "\nToday I plan to cook " . $x . ", which technically is a $x_value . "\n";
}
```

### 现在我将按值降序排序。其关键字是`arsort()`。

```php
$vegetablesfruits = array(
    "pumpkin" => "vegetable", 
    "tomato" => "fruit", 
    "potato" => "vegetable", 
    "cabbage" => "vegetable", 
    "cauliflower" => "vegetable", 
    "orange" => "fruit", 
    "ginger" => "vegetable", 
    "turmeric" => "spice", 
    "peas" => "vegetable"
);
arsort($vegetablesfruits);
foreach($vegetablesfruits as $x => $x_value) { 
    echo "\nToday I plan to cook " . $x . ", which technically is a $x_value . "\n";
}
```

### 这将按键降序排序。我将使用`krsort`关键字作为目的。

```php
$vegetablesfruits = array(
    "pumpkin" => "vegetable", 
    "tomato" => "fruit", 
    "potato" => "vegetable", 
    "cabbage" => "vegetable", 
    "cauliflower" => "vegetable", 
    "orange" => "fruit", 
    "ginger" => "vegetable", 
    "turmeric" => "spice", 
    "peas" => "vegetable"
);
krsort($vegetablesfruits);
foreach($vegetablesfruits as $x => $x_value) { 
    echo "\nToday I plan to cook " . $x . ", which technically is a $x_value . "\n";
}
```

# 第六章：PHP 超全局变量

超全局变量基本上是内置变量，它们在不同的作用范围内都是可用的。我将在后面的代码示例中讨论每一个变量，并看看它们能做什么。

## PHP `$GLOBALS`

`$GLOBALS` 是 PHP 中的一个超变量，你可以用它从 PHP 脚本的任何位置（如方法和函数）访问不同的全局变量。PHP 倾向将变量存储在名为`$GLOBALS[$index]`的数组中。索引即变量的名称。

```php
<!DOCTYPE html>
<html>
<body>
<?php
$a = 55;
$b = 15;
function additionofnumbers() {
    $GLOBALS['c'] = $GLOBALS['a'] + $GLOBALS['b'];
}
additionofnumbers();
echo $c;
?>
</body>
</html>
```

```php
main.php
```

```html
<!DOCTYPE html>
<html>
<body>
70
</body>
</html>
```

## PHP 超全局变量 = `$_SERVER`

超全局变量是某种内置变量，它们在不同的作用范围内都是可用的。`$_SERVER` 包含了关于路径、标头和脚本位置的信息。



进入`/path/to/xxx`目录，找到`xxx.json`。

在表达式`cvar = avar + bvar`中，加法运算符（`+`）将`avar`与`bvar`相加，得到它们的和`cvar`

在`List.of(arg0, arg1, arg2)`中，`List`接口的工厂方法`of()`接受一系列的元素，返回包含它们的只读列表。

之后我们这样调用`cmd`命令：`cmd arg0 arg1 arg2`。

```
if (condVar > someVal) {console.log("xxx")}
```



```
Connection has fully failed: php_network_getaddresses: getaddrinfo failed: Name or service not known
PHP Warning: mysqli::__construct(): php_network_getaddresses: getaddrinfo failed: Name or service not known in /home/cg/root/4530372/main.php on line 11 
PHP Warning: mysqli::__construct(): (HY000/2002): php_network_getaddresses: getaddrinfo failed: Name or service not known in /home/cg/root/4530372/main.php on line 11
```

如果连接失败，你将得到上述结果。

## MySQLi 过程化

这是 PHP 连接到 MySQLi 数据库的另一个示例。

```php
<!DOCTYPE html>
<html>
<body>
<?php
$theservername = "this is a localhost";
$theusername = "this is the username box";
$thepassword = "this is the password box";
// 创建连接
$myconnection = new mysqli_connect($theservername, $theusername, $thepassword);
// 检查连接
if (!$myconnection) {
    die("Connection has fully failed: " . $myconnection->connect_error);
}
echo "You have been connected successfully to the database";
?>
</body>
</html>
```

## 数据库创建

在这个示例中，我将编写代码帮助你创建一个加载到你网站上的数据库。

```php
<!DOCTYPE html>
<html>
<body>
<?php
$theservername = "this is a localhost";
$theusername = "this is the username box";
$thepassword = "this is the password box";
// 创建连接
$myconnection = new mysqli_connect($theservername, $theusername, $thepassword);
// 检查连接
if (!$myconnection) {
    die("Connection has fully failed: " . $myconnection->connect_error);
}
echo "You have been connected successfully to the database";
// 这将帮助你创建一个数据库
$sql = "I am trying to create a database";
if ($myconnection->query($sql) === TRUE) {
    echo "Thank you, you have got your database. You are now free to use it.";
} else {
    echo "There is an error in the creation of database: " . $myconnection->error;
}
$myconnection->close();
?>
</body>
</html>
```

## 过程化 MySQLi 中的数据库创建

```php
<!DOCTYPE html>
<html>
<body>
<?php
$theservername = "this is a localhost";
$theusername = "this is the username box";
$thepassword = "this is the password box";
// 创建连接
$myconnection = new mysqli_connect($theservername, $theusername, $thepassword);
// 检查连接
if (!$myconnection) {
    die("Connection has fully failed: " . $myconnection->connect_error);
}
echo "You have been connected successfully to the database";
// 这将帮助你创建一个数据库
$sql = "I am trying to create a database";
if (mysqli_query($myconnection, $sql)) {
    echo "Thank you, you have got your database. You are now free to use it.";
} else {
    echo "There is an error in the creation of database: " . mysqli_error($myconnection);
}
mysqli_close($myconnection);
?>
</body>
</html>
```

## 表格创建

这里是用于 PHP 的表格创建代码。

```php
<!DOCTYPE html>
<html>
<body>
<?php
$theservername = "this is a localhost";
$theusername = "this is the username box";
$thepassword = "this is the password box";
// 创建连接
$myconnection = new mysqli_connect($theservername, $theusername, $thepassword);
// 检查连接
if (!$myconnection) {
    die("Connection has fully failed: " . $myconnection->connect_error);
}
echo "You have been connected successfully to the database";
$sql = "CREATING TABLE BuyingDetails (
    id INT(6) UNSIGNED AUTO_INCREMENT PRIMARY KEY,
    Serial VARCHAR(30) NOT NULL,
    BuyerName VARCHAR(30) NOT NULL,
    PostalAddress VARCHAR(30) NOT NULL,
    Age VARCHAR(30) NOT NULL,
    Namecountry VARCHAR(30) NOT NULL,
    MoneySpent VARCHAR(30),
    reg_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
)";
if (mysqli_query($myconnection, $sql)) {
    echo "Thank you, you have got your table. You can use it as per need.";
} else {
    echo "There is an error in the creation of database: " . $myconnection->error;
}
$myconnection->close();
?>
</body>
</html>
```

# 第九章：PHP 和 SQL 命令

当你借助 PHP 的帮助构建网站时，你必须学习如何使用 SQL，因为没有数据库的网站就像只有骨骼但缺乏血肉和肌肉的人体。SQL 中的数据库由表格组成。你必须通过名称识别表格，以便轻松定位存储在其中的信息。我将使用以下数据库来实验 SQL 命令。

| Serial | BuyerName | PostalAddress | Age | Namecountry | MoneySpent |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

在开始创建之前，数据库的设计应该是正确的。否则，你将需要通过调整表格、合并表格或向上或向下移动列来建立 MySQL 可能使用的关系。在本章中，我将解释不同 SQL 命令的使用以及它们的行为。

## SQL 列选择

以下语句将从表格中选择列。我将使用`select`命令来解释它的工作原理。`BuyingDetails`数据库所示：

| Serial | BuyerName | PostalAddress | Age | Namecountry | MoneySpent |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

命令如下：`SELECT BuyerName, Nameofcountry FROM BuyingDetails`

| BuyerName | Nameofcountry |
| --- | --- |
| Temeria Fellar | United States |
| Pastor Kemari | Canada |
| Tim Miller | United States |
| Jasmine Tim Kesan | Sweden |
| Kevin Nevada | Spain |
| Mark Flagrar | United States |
| Stanley Cooper | Italy |
| Justin Goldminer | Canada |
| Sylvinia Marko | United Kingdom |
| Adam Toffin | United Kingdom |

如果你不确定需要处理哪一列，可以使用`*`命令来选择表格中的所有列。原始表格如下：

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| --- | --- | --- | --- | --- | --- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

这里是 SELECT 语句：`SELECT * FROM BuyingDetails;`

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| --- | --- | --- | --- | --- | --- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

该命令已经选择了表格中的所有列。这是查看所有列详情最简单的方法。你可以从这里记录下列名，并使用相同的`SELECT`命令选择所需的列。另一种名为`DISTINCT`的语法用于消除数据库中的重复条目，这样你就可以避免在重复读取相同条目上浪费时间。

在下面的示例中，我将选取来自的买家。以下是命令：



```sql
SELECT * FROM BuyingDetails WHERE Nameofcountry = 'United Kingdom' ;
```

这是原始形式的表格。

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

以下是结果：

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

文本：你可以根据`serial`列的编号来选择行。这是其原始形式的表格。

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

以下是命令：

```sql
SELECT * FROM BuyingDetails WHERE Serial#=1; WHERE Serial#=2; WHERE Serial#=3; WHERE Serial#=4; WHERE Serial#=5; WHERE Serial#=6; WHERE Serial#=7; WHERE Serial#=8; WHERE Serial#=9; WHERE Serial#=10;
```

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

SQL `AND`、`OR` 操作符与 `AND`、`OR` 子句配合使用。你可以使用这些子句过滤表格。这是表格当前的状态。

```sql
SELECT * FROM BuyingDetails WHERE Nameofcountry=United States' AND Moneyspent=1000;
```

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |

`OR` 的示例如下。这是表格的原始形式。

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

```sql
SELECT * FROM Buyingdetails WHERE Nameofcountry='United States' OR Moneyspent= 55000;
```

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

### NOT 子句

在下面的示例中，我将展示如何使用 `NOT` 子句来消除一行或一列并显示其余部分。我假设表格的原始状态如下：

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

`NOT` 子句如下：

```
SELECT * FROM Buyingdetails WHERE NOT Nameofcountry = 'Spain';
```

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| --- | --- | --- | --- | --- | --- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

### 双重 NOT 子句 (Double Not Clause)

你已经看到我们如何使用 `NOT` 子句来移除元素。然而，如果你必须排除两个条件，可以使用双重 `NOT` 子句。表格恢复到原始状态，如下：

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| --- | --- | --- | --- | --- | --- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

以下语句将选择表中所有国家为 `NOT` 西班牙且不是 `NOT` 意大利的字段。



| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| --- | --- | --- | --- | --- | --- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

## 解密 SQL ORDER BY 关键字

`ORDER BY` 关键字通常用于按升序或降序对结果进行排序。`ORDER BY` 关键字将作为默认函数对细节进行排序。你需要使用 `DESC` 关键字将其变为降序。以下是未排序的表格。

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| --- | --- | --- | --- | --- | --- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

我将写下命令：

```sql
SELECT * FROM BuyingDetails ORDER BY Country
```

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| --- | --- | --- | --- | --- | --- |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |

我们可以通过根据买家名称对表格进行排序来对 `ORDER BY` 子句进行进一步实验。首先，我将表格恢复到原始形式。

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| --- | --- | --- | --- | --- | --- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

这里是完成此任务代码：

```sql
SELECT * FROM BuyingDetails ORDER BY BuyerName;
```

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| --- | --- | --- | --- | --- | --- |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |

### ORDER BY DESC

下一个示例将按降序排列表格。表格目前的状态如下：

| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

现在我将编写代码来按国家降序重新排列表格。

```sql
SELECT * FROM BuyingDetails ORDER BY Nameofcountry DESC;
```

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |

## SQL 插入语句

你可以使用 `INSERT INTO` 语句向现有表格添加新的行和列。我将用我们在所有示例中一直使用的表格真实示例进行演示。

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

`insert into` 语句如下：

```sql
INSERT INTO BuyingDetails (BuyerName, PostalAddress, Age, Nameofcountry, MoneySpent) VALUES ('Eliseh Bentley', 'Street 45 Aliano Cameo', '33', 'Mexico', '5000')
```

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |



### UPDATE 语句

在这个示例中，我将解释你如何使用 `UPDATE` 语句以及它在构建网站时起什么作用。当你创建一个表格后，可以使用 `UPDATE` 语句刷新特定行和列的详细信息。需要记住的一点是，你不应该省略 `WHERE` 子句，否则你将得到不可预测的结果。你想要的更新将会发生。现在让我们来一些代码。以下是表格的当前状态。

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

更新表格的代码如下：

```sql
UPDATE BuyingDetails SET BuyerName = 'Alfred', Nameofcountry = 'Germany' WHERE Serial# = 1;
```

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Alfred | Street 7 Orington | 45 | Germany | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

在同一行中，你可以更新表格中的多个条目。`WHERE` 子句帮助你选择更新的精确位置。请下例。为了方便阅读和理解，我将表格恢复到之前的状态。

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

以下示例将将国家名从 `United Kingdom` 更新为 `Germany`。

```sql
UPDATE BuyingDetails SET Nameofcountry= 'Germany' WHERE Nameofcountry= 'United States';
```

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| --- | --- | --- | --- | --- | --- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | Germany | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | Germany | 55000 |

当你组织的员工在表中填写了错误的条目时，这个子句特别有用。

### 如果你没有使用 WHERE 子句会？

在这个代码示例中，我将解释省略 `WHERE` 子句会带来什么危险。当然，在学习阶段并没有什么危险。然而，当你成为企业所有者并为业务运行大型数据库时，简单的错误造成的危险程度会更高。我将以原始形式展示表格供参考。

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| --- | --- | --- | --- | --- | --- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

现在我将编写代码但省略 `WHERE` 子句，看看结果如何。

```sql
UPDATE BuyingDetails SET Nameofcountry= 'United States'
```

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| --- | --- | --- | --- | --- | --- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | United States | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | United States | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | United States | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | United States | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | United States | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United States | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United States | 55000 |

当你创建表格并更新它时，可能会遇到这种情况。使用 `WHERE` 子句来删除某些条目。你想要删除的条目。使用 `WHERE` 子句来删除 `DELETE` 状态。

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| --- | --- | --- | --- | --- | --- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

以下语句将删除表中的条目。

```sql
DELETE FROM BuyingDetails;
```

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| --- | --- | --- | --- | --- | --- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

在某些情况下，你可能想删除所有属性。这包括结构和所有索引。这是目前表的状态。

最重要的重要的是表格将保持完整。只有条目会被删除。



# TOP、ROWNUM、LIMIT 子句

这里有一些有趣的子句可以使用。你可以使用`SELECT TOP`来指定返回的条目总数。在处理具有数千条记录的大表时，`SELECT TOP`子句非常有用。如果你选择返回整个表格，将会降低数据库性能。但是，如果你只返回你想要处理的条目，除非这些数据过大，否则几乎不会影响性能。以下是我将使用`TOP`子句的表格。

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| --- | --- | --- | --- | --- | --- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

以下是从表格中选择前 7 条条目的代码。

```sql
SELECT TOP 7 * FROM BuyingDetails;
```

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| --- | --- | --- | --- | --- | --- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |

SQL 中还有另一个语句可以完成相同的工作，但更容易使用。我将表格恢复到原始状态，然后使用该子句。

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| --- | --- | --- | --- | --- | --- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

```sql
SELECT * FROM BuyingDetails LIMIT 7;
```

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| --- | --- | --- | --- | --- | --- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |

这是另一种完成相同工作的技术。当你有多种方法可以完成某项技术任务时，如果一种方法不起作用，你会感到更有信心。以下是表格的当前状态。

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| --- | --- | --- | --- | --- | --- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |

以下是与上述两种方法等效的代码。

```sql
SELECT * FROM BuyingDetails WHERE ROWNUM <=7
```

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| --- | --- | --- | --- | --- | --- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| ... | ... | ... | ... | ... | ... |

## TOP 50 Percent

`Percent`子句在处理大型数据库时非常有用。它会选择表格的前 50% 并显示条目。以下是表格。

| Serial# | BuyerName | PostalAddress | Age | Nameofcountry | MoneySpent |
| --- | --- | --- | --- | --- | --- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | United States | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | Canada | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | United States | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | Sweden | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | Spain | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | United States | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | Italy | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | Canada | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | United Kingdom | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | United Kingdom | 55000 |

`TOP`子句如下：

```sql
SELECT TOP 50 PERCENT * FROM BuyingDetails;
```

你可以为`TOP 50 percent`子句添加`WHERE`子句以获得自定义结果。请参阅以下示例。

| 序号 | 买家姓名 | 邮寄 | 年龄 | 国家 | 消费金额 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | 美国 | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | 加拿大 | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | 美国 | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | 瑞典 | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | 西班牙 | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | 美国 | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | 意大利 | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | 加拿大 | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | 英国 | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | 英国 | 55000 |

以下是代码：

```sql
SELECT TOP 2 * FROM BuyingDetails WHERE Nameofcountry= ‘United States’;
```

| 序号 | 买家姓名 | 邮寄 | 年龄 | 国家 | 消费金额 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | 美国 | 1000 |
| 3 | Tim Miller | Street 55 Irina | 45 | 美国 | 1500 |

通配符 SQL 的奇妙之处在于它为实验提供了极大的空间。我将使用一个语句来选择国家以‘Uni.’开头的买家。我将使用下表。

| 序号 | 买家姓名 | 邮寄 | 年龄 | 国家 | 消费金额 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | 美国 | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | 加拿大 | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | 美国 | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | 瑞典 | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | 西班牙 | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | 美国 | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | 意大利 | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | 加拿大 | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | 英国 | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | 英国 | 55000 |

以下是选择以‘Uni.’开头的特定国家的语句：

```sql
SELECT * FROM BuyingDetails WHERE Country LIKE ‘Uni%';
```

| 序号 | 买家姓名 | 邮寄 | 年龄 | 国家 | 消费金额 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | 美国 | 1000 |
| 3 | Tim Miller | Street 55 Irina | 45 | 美国 | 1500 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | 美国 | 18000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | 英国 | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | 英国 | 55000 |

以下通配符将选择以‘dom’结尾的所有国家：

| 序号 | 买家姓名 | 邮寄 | 年龄 | 国家 | 消费金额 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | 美国 | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | 加拿大 | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | 美国 | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | 瑞典 | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | 西班牙 | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | 美国 | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | 意大利 | 15000 |



以下是语句：

```sql
SELECT * FROM BuyingDetails WHERE Nameofcountry LIKE '%dom%';
```

| 序号 | 买家姓名 | 邮寄 | 年龄 | 国家 | 消费金额 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | 英国 | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | 英国 | 55000 |

如果你使用`_`通配符，你可以更有选择性地查看表格条目。这里是原始格式的表格：

| 序号 | 买家姓名 | 邮寄 | 年龄 | 国家 | 消费金额 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Temeria Fellar | Street 7 Orington | 45 | 美国 | 1000 |
| 2 | Pastor Kemari | Street 10 Ontario | 55 | 加拿大 | 500 |
| 3 | Tim Miller | Street 55 Irina | 45 | 美国 | 1500 |
| 4 | Jasmine Tim Kesan | Street 87 | 20 | 瑞典 | 2000 |
| 5 | Kevin Nevada | Street 76 Kevada Olumpur | 15 | 西班牙 | 5000 |
| 6 | Mark Flagrar | Street 90 Time Square | 25 | 美国 | 18000 |
| 7 | Stanley Cooper | Street 45 Insta Debian | 33 | 意大利 | 15000 |
| 8 | Justin Goldminer | Street 10 Trafalgar Square | 30 | 加拿大 | 10000 |
| 9 | Sylvinia Marko | Street 34 Nion Valley | 33 | 英国 | 15000 |
| 10 | Adam Toffin | Street 55 Nion Valley | 21 | 英国 | 55000 |

这里是通配符语句：

```sql
SELECT * FROM BuyingDetails WHERE Nameofcountry LIKE ‘_United Kingdom’;
```

### 结论

现在你已经读到了这本书的最后，下一步是更多的练习。当你将 PHP 与 MySQL 结合时，它并不是一种容易的语言。你需要考虑细节、代码中的细微差别以及禁忌区域。希望这本书已经让你熟练了 PHP 高级编程。我为面向对象编程和数据库留了大量的空间，以便你更进一步，进入函数式编程的世界。

### 参考文献

- Nixon, R. (2014, June). *Learning PHP, MySQL, JavaScript, CSS & HTML5 X-Files*.
- PHP `$_REQUEST`. (n.d.). Www.W3schools.com. Retrieved from https://www.w3schools.com/php/php_superglobals_request.asp
