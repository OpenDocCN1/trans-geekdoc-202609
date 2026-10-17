
# PHP 初学者指南

## 序言

### 欢迎！

你想快速学习 `PHP` 吗？本书是正确的选择。你将学习 `PHP` 的基础知识。

从在你的电脑上搭建服务器开始。随后，你将学习如何运行第一个 `PHP` 脚本。然后你将学习如何使用数据库。

### 先决条件

不需要特殊知识。如果你想学习 `PHP`，我假设你了解一些 `HTML`。

在硬件方面，你需要一台带有显示器、键盘的电脑。由于我们要开发网站，当然需要连接互联网。

你可以使用任何操作系统。本书将向你介绍如何在 `Windows`、`Linux` 和 `MacOS` 上安装现代文本编辑器，并提供一些示例。

## 第一天

### PHP – 定义与历史

`PHP` 是一种主要用于开发动态网页的脚本语言。`PHP` 脚本在服务器上执行，而不是在访问者的浏览器中执行。

`PHP` 由 Rasmus Lerdorf 于 1995 年开发。他的目标是为一组常用的 Perl 脚本创建一个简单的替代品。这就是个人首页工具（PHP）的由来。不久后，他用 `C` 语言重新创建了这个工具集。今天，`PHP` 仍然用 `C` 开发。

1998 年，Andi Gutmans 和 Zeev Suraski 与 Lerdorf 合作，从零创建了 `PHP 3`，使其可用，特别是在蓬勃发展的电子商务领域。Gutmans 和 Suraski 创立了 Zend Technologies 公司，该公司贡献了 `PHP 4` 的大部分部分。

2004 年，`PHP5` 增强了对面向对象的支持，并大大提高了 `PHP` 解释器的速度。

十年后，2015 年发布了 `PHP 7`。它由一个全新的引擎驱动，速度极快。`PHP 6` 被跳过了，因为计划执行的项目从未完成，因此开发者们专注于一个全新的内核。大多数脚本的执行速度比 `PHP 5` 快一倍。大多数旧的 `PHP 5` 脚本只需要少量修改即可在 `PHP 7` 中运行。本书中的脚本均已更新为完全兼容的版本。

### 搭建开发环境（Windows, Linux 或 Mac OS）

#### Windows

在 Windows 上，预制的服务器包让安装服务器变得极其简单。对于开发，我倾向于使用 `Xampp` 软件包（`www.apachefriends.org`）。

下载 Windows 安装程序并运行安装。我建议将 `C:/xampp/` 保为默认文件夹路径。如果你将包安装在 `C:/Programs/XAMPP/` 目录下，服务器可能会出现问题，因为必要的文件权限没有正确设置。在安装过程中，系统会询问是否应将各个服务器组件作为操作系统的服务进行安装。你不应该这样做，否则服务器将在后台持续运行（直到你手动停止服务），消耗资源，并在网络上持续可用。

#### Linux

在 Linux 中，最好使用软件包管理器（Package Manager）安装 Apache Web 服务器和 MySQL 数据库服务器，并手动进行配置。但对于这本书来说，我建议初学者使用从 `www.apachefriends.org` 获取的预编译包，它包含了所有必要的服务器功能和 PHP 扩展。在下载链接下方，你将找到 Linux 安装说明以及一些关于如何快速启动和停止服务器的提示。

#### MacOS

针对 MacOS 甚至有 `Apachefriends.org` 的程序包。但我更倾向于让 MacOS 用户使用 `MAMP` 程序包。它的操作虽然类似，但给我带来的问题更少。该应用程序可以在 `www.mamp.info` 免费获取。它还有一个付费的 Pro 版本，但我们初次编程体验不需要它。下载安装文件后，请将 `MAMP` 安装在你的 `Application` 文件夹中。

上述所有服务器包都包含一个标记为 `htdocs` 的目录。我们将使用它来存储可以通过浏览器从服务器访问的文件。因此，打开你的浏览器并输入以下 URL：`http://127.0.0.1`

在 MacOS 下，你必须输入服务器的端口号（默认数字为 `4444`，因此整个 URL 应该为：`http://127.0.0.1:4444`）

你将看到来自服务器包网站（`XAMPP` / `MAMP`）的欢迎，并收到一些关于服务器的信息。

`127.0.0.1` 总是本地计算机。这意味着浏览器尝试寻找本地 Web 服务器。或者，你可以使用 `http://localhost`。这应该产生相同的结果。

### 文本编辑器

每个操作系统都有很多文本编辑器。然而，在这种情况下，`Microsoft Office Word` 或 `LibreOffice Writer` 不能被视为文本编辑器，因为它们除了文本之外还保存了大量关于页面和文本格式的信息。文本编辑器按照输入文本在编辑器中显示的样式保存精确的字符。现代编辑器会对文本着色以提高其可读性。这种颜色不会被保存，而是在你重新打开文件时动态显示。这种功能被称为 `语法高亮`（syntax highlighting）。语法是用于描述代码的术语，在文本编辑器中高亮它意味着编程语言的各种命令和函数被涂上了颜色。

还有集成开发环境（IDE），它们对于编写和管理程序代码以及软件项目的所有其他部分非常有帮助。IDE 会自动检测程序代码中函数的交叉引用，并在编写注释时显示最近使用的函数。

有很多大型 IDE 项目，它们以开源项目的形式提供，或者通过不同的许可证适用于所有操作系统。许多开发者使用 IDE `Eclipse`（`www.eclipse.org`）或 `NetBeans`（`www.netbeans.org`）。

如果你有一台性能较低的电脑，或者想快速测试一些短小的 PHP 脚本，我建议使用文本编辑器 `jEdit`，它是作为开源软件开发的，可以从 `www.jedit.org` 下载。在较大的 Linux 发行版中，可以通过软件通道（软件包管理器）获取版本较旧的 `jEdit`。

对于这本书来说，你正在使用 IDE 还是简单的文本编辑器并不重要。如果你打算成为一名专业的 PHP 开发者，迟早会接触到 IDE 的。

为了给出具体的建议，我个人建议你先用像 `jEdit` 这样的文本编辑器编写第一个脚本，在完成几个小型 PHP 项目后，再将更高级的脚本进入 IDE 的界面中。

### 第一个 PHP 程序（欢迎整个世界）

现在我们来编写第一个小型 PHP 脚本。

打开你喜欢的文本编辑器并输入以下代码行：

```php
<?php
echo "Hello World!";
?>
```

将此文本保存在 Web 服务器安装目录下的 `htdocs` 文件夹中，并将文件命名为 `hello.php`。

文件扩展名 `.php` 表明该文件是一个 PHP 脚本。我们的脚本以 `<?php` 行开头，这些是 PHP 代码而不是普通文本，我们的服务器会识别出 `?>` 之前的行不是输出，而是首先由我们的 PHP 解释器处理。

在编程世界中，有所谓的解释器（interpreters）和编译器（compilers）。编译器首先处理完整的程序并生成机器语言。PHP 是被解释执行的，这意味着我们的服务器会识别出 `?>` 之前的行不是输出，而是首先由我们的 PHP 解释器处理。

在我们之前的第一个 PHP 脚本中，我们写了文本 "Hello World!"。现在我们不再直接将文本紧跟在 `echo` 命令后面，而是先将其保存在变量中，然后让 `echo` 命令输出该变量的内容。

```php
<?php
  $myText = "Hello World!";
  echo $myText;
?>
```

在 PHP 中，变量以美元符号 (`$`) 开头。变量名是任意的，但不能包含空格，只能包含大小写字母、数字和下划线。

要连续打印几个变量的内容，它们必须用点（`.`）进行分隔：

```php
<?php
  $part1 = "Hello ";
  $part2 = "World!";
  echo $part1 . $part2;
?>
```

这与我们第一个示例的输出相同。我们也可以将变量和文本一起输出：

```php
<?php
  $part1 = "Hello";
  echo $part1 . " World!";
?>
```

如果你在程序中寻找错误，可以随时使用 `var_dump` 命令通过该函数来找出变量内信息的性质：

```php
<?php
  $part1 = "Hello";
  var_dump($part1);
?>
```

输出：

`string(5) "Hello"`

这意味着我们变量的内容类型是 "string"（字符串），并且包含一个有 5 个字符的字符串，即 "Hello"。

### 代码注释

如果我们的脚本只有几行长，一眼就能看出某个代码块的作用。然而，一旦脚本变得很长，就有必要在程序代码中加入注释，这样以后阅读代码的人就能立即知道接下来的几行代码对象。

PHP 中有单行注释和多行注释。单行注释以两个正斜杠 `//` 开始。当前行中两个斜杠之后编写任何内容都不再被视为代码。

多行注释以斜杠和星号 `/*` 开始，以星号和斜杠 `*/` 结束。

这是另一个示例：

```php
<?php
  // 我是一条单行注释
  echo "I am code";
  /*
  I
  am
  a
  multiline
  comment
  */
?>
```

该脚本只输出以下文本：

`I am code`

当然，一个优秀的程序员应该始终以编写能够自我揭示所有用途的代码为目标。这可以通过逻辑变量名和函数名来实现。变量 `$a`、 `$b` 和 `$c` 表示“小于”，但如果变量命名为 `$total_price`、 `$sales_tax` 和 `$gross_price` 则意义明确。

尽管如此，例如，在编写复杂算法或代码时，编写有意义的注释是有帮助的。你可以通过注释将程序代码分为几个块。

那么，一个程序块应该以注释开头：

```php
/*****************
处理用户输入
*****************/
```

接下来的块标记如下：

```php
/*****************
执行计算
*****************/
```

最后一个块（例如）如下：

```php
/*****************
输出结果
*****************/
```

那么任何想要更新计算逻辑的程序员都能立即知道他需要在代码的哪个区域进行查找。

### 算术运算（基础算术）

如果你只在变量中保存数字而不是字母，那么就可以对这些数字进行计算。

这是一个示例（在此示例中使用了 HTML 代码 `<br />`，它在浏览器中显示为换行）：

```php
<?php
  $number1 = 2;
  $number2 = 3;
  $addition = $number1 + $number2;
  $subtraction = $number1 - $number2;
  $multiplication = $number1 * $number2;
  $division = $number1 / $number2;
  echo "Number 1: " . $number1;
  echo "<br />";
  echo "Number 2: " . $number2;
  echo "<br />";
  echo "<br />";
  echo "Addition: " . $addition;
  echo "<br />";
  echo "Subtraction: " . $subtraction;
  echo "<br />";
  echo "Multiplication: " . $multiplication;
  echo "<br />";
  echo "Division: " . $division;
?>
```

该脚本在浏览器中输出：

`Number 1: 2`

`Number 2: 3`

`Addition: 5`

`Subtraction: -1`

`Multiplication: 6`

`Division: 0.666666666667`

这里是简单算术的另一种写法：

```php
<?php
  $value1 = 2;
  $value2 = 3;
  $value1 += $value2;
  $value2 *= $value2;
  echo $value1;
  echo "<br />";
  echo $value2;
?>
```

输出：

`5`

`9`

作为一个小任务，你可以写一个脚本来计算：网站每天有 30,000 个访客。有 60% 的访客看到了广告。换句话说，40% 的访客看到了我们的横幅。对于 1000 次点击，我们获得 200 欧元。我们每月赚多少（按 30 天计算）？如果网站每天有 100,000 个访客，答案应该是 240 欧元和 800 欧元。示例如下：

```php
<?php
  $dailyVisitors = 30000;
  $sees = $dailyVisitors * 0.4; // 60% 广告
  $clickratio = 0.1; // 每 1000 次点击
  $earnings = 200;
  echo ($sees / 1000) * $earnings;
?>
```

### 合并多个变量（数组）

如果你有多个变量来表示相似的值，将它们包含在数组是有意义的。这里有两个输出相同的示例：

```php
<?php
  $value1 = 2;
  $value2 = 4;
  $value3 = 8;
  $value4 = 16;
  $value5 = 32;
  echo $value1 . "<br />";
  echo $value2 . "<br />";
  echo $value3 . "<br />";
  echo $value4 . "<br />";
  echo $value5 . "<br />";
?>
```

```php
<?php
  $valueArray = array(2,4,8,16,32);
  echo $valueArray[0] . "<br />";
  echo $valueArray[1] . "<br />";
  echo $valueArray[2] . "<br />";
  echo $valueArray[3] . "<br />";
  echo $valueArray[4] . "<br />";
?>
```

两者的输出都是：

`2`

`4`

`8`

`16`

`32`

你可以通过 `$array[index]` 访问数组的值。条目从 0 到元素数量升序编号。你也可以自己设置索引：

```php
<?php
  $myArray = array("index1" => "value1");
  echo $myArray["index1"];
  echo "<br />";
  $myArray["index1"] = "value2";
  echo $myArray["index1"];
?>
```

输出：

`value1`

`value2`

以后，我们将学习如何自动连续输出数组中的所有值并处理它们。这对于包含几十个条目的数组非常有用。

#### 排序数组

如果我们动态地填充数组并希望按字母顺序对值，有一个简单的函数：`sort()`。



```php
<?php
  $myArray = array("Zita", "Anton", "Hans");
  // 未排序输出
  echo $myArray[0];
  echo "<br />";
  echo $myArray[1];
  echo "<br />";
  echo $myArray[2];
  // 排序数组
  sort($myArray);
  echo "<br /><br />";
  // 排序后的输出
  echo $myArray[0];
  echo "<br />";
  echo $myArray[1];
  echo "<br />";
  echo $myArray[2];
?>
```

输出：

`Zita`

`Anton`

`Hans`

`Anton`

`Hans`

`Zita`

#### 多维数组

数组再次可以包含另一个数组作为其值：

```php
<?php
  $myArray = array();
  $myArray["index1"] = array("value1", "value2");
  $myArray["index2"] = array("value3", "value4");
  echo $myArray["index1"][0];
  echo "<br />";
  echo $myArray["index2"][1];
?>
```

输出：

`value1`

`value4`

所以，你可以保存坐标并读取它们，例如像 X, Y 坐标系一样：

```php
<?php
  //...
  echo $chessboard[10][2];
?>
```

这取决于你的脚本如何构建。例如，你可以显示第 10 行第 2 列的棋子。

到目前为止，尽管我们已经在代码中为变量填充了值，但结果并不是一个动态网站。现在，我们想要从“外部”接收信息。

为了让用户向我们的 PHP 脚本发送数据，除此之外还有两种简单的方法：`POST` 和 `GET`。

`POST` 信息的传输方式，例如，当用户注册或发布新论坛帖子时，通过一个配置恰当的表单发送到我们的服务器。然后是 `GET` 信息，它是通过调用的 URL 接收的。你可能已经注意到网商店中那些很长的 URL，它们包含许多字母、数字和自动生成的参数。

## 识别并读取 GET 变量

`GET` 变量作为参数传递在 URL 中：

`http://www.myurl.com/script.php?variable1=value1&variable2=value2&variable3=value3`

变量和值的数量几乎不受限制，但旧版浏览器和许多服务器对 URL 的长度有 1024 个字符的限制。

当在浏览器调用此 URL 时，计算机首先尝试访问地址 `www.myurl.at`。随后从服务器请求文件 `script.php`，并接收到三个变量。第一个变量带有问号（`?`），其他变量带有和符号（`&`）。

让我们将欢迎脚本扩展为一个动态组件，以我的名义问候访问者：

```php
<?php
  $vistorsname = $_GET['name'];
  echo "Hello ".$vistorsname;
?>
```

将脚本保存，例如在你的 `htdocs` 文件夹中命名为 `hello2.php`。

在 PHP 中，始终存在一些自动生成的变量。例如，有一个名为 `$_GET` 的数组，另一个名为 `$_POST` 的数组，可以从其中读取传输的 `GET` 和 `POST` 信息。这些变量是数组，值的名称就是数组的索引。

如果你现在通过 URL 调用脚本，

`http://127.0.0.1/hello2.php?name=Klaus`

浏览器中将出现以下文本：

Hello Klaus

恭喜你！你现在编写了你的第一个动态网站，并且比其他只会写简单 HTML 的程序员领先了一步。

## 识别并读取 POST 变量

你是否会想要查询包含特殊字符的较长文本，以便在 URL 的问题中通过 `GET` 变量继续传输？为了这些目的，有 `POST` 方法，其用法如下：

my_form.html

```html
<form method="POST" action="read_form.php">
  <textarea name="myText"></textarea>
  <input type="submit" value="Send" />
</form>
```

read_form.php

```php
<?php
  $myText = $_POST["myText"];
  echo nl2br($myText);
?>
```

在第一个文件中，我们通过 HTML 定义了一个表单。我们想要从中获取信息的每个表单元素都获得一个 `name=...` 属性（标签属性）。这使得我们能够在第二个文件中通过全局变量 `$_POST` 提取所有信息。

由于我们使用了多行文本框，因此我们在 PHP 脚本中对应使用了 `nl2br` 函数，它代表将换行转换为换行符或在文本中实现换行。

## 条件、程序控制 (IF/ELSE/ELSEIF)

我们已经可以根据用户输入输出动态文本，但无法根据用户输入来运行脚本。在编程中，有很多情况可以写成如下：当用户 `A` 正好输入某些内容时，执行此操作，否则执行另一个操作。

```php
if ($input == "A") {
  do this;
}
else {
  do that;
}
```

`If` 后面跟着一个在普通括号 `()` 内编写的条件，如果条件满足，执行大括号内的代码；否则，执行 `else` 部分的代码。

输出：

myVar 存在

```php
<?php
  $myVar = "123";

  if (isset($otherVar)) {
    echo "myVar exists";
  }
  else {
    echo "myVar does not exists";
  }
?>
```

输出：

otherVar 不存在

### 用例分析 (switch / case)

假设我们有一个变量，并想要检查许多不同的内容。我们已经知道了 `if`、`elseif` 和 `else` 的功能。然而，这可能会很快变得混乱；此外，编写冗余代码来只检查单个变量更为简单。这里有一个实用的函数 `switch case`，其编写如下：

```php
<?php
  $username = $_GET["username"];
  switch ($username) {
    case "Klaus":
      echo "Hello administrator!";
      break;
    case "Dagmar":
      echo "Hello sister!";
      break;
    case "Bill Gates":
      echo "Hello richest man in the world!";
      break;
    default:
      echo "Hello visitor!";
      break;
  }
?>
```

正如我们看到的，`switch` 函数的头部与 `if` 函数非常相似；它只是没有定义参数。之后，每个多个 case 块必须以 `break` 结束；这会中断跳转到其他 case 的检查。

如果在任何一种情况下都不满足条件，将执行 `default` 块。如果你不使用 `break`，你可能会对两个或多个 case 代码块运行相同的代码：

```php
<?php
  $username = $_GET["username"];
  switch ($username) {
    case "Klaus":
    case "Dagmar":
      echo "Hello administrator!";
      break;
    case "Bill Gates":
      echo "Hello richest man in the world!";
      break;
    default:
      echo "Hello visitor!";
      break;
  }
?>
```

### 用于重复性任务的循环 (While / For / Foreach)

#### While() 循环

通常，我们的脚本需要重复执行某些任务。例如，按照特定的顺序进行某种编号：

```php
<?php
  $number = 1;
  while ($number < 100) {
    echo $number . "<br />";
    $number++;
  }
?>
```

这个短脚本返回从 1 到 99 的每个数字。它被用于所谓的 `while()` 循环。`while()` 循环的头部用于像 `if` 函数一样指定条件。只要条件为真或调用了 `break` 命令，循环就会重复。该脚本还有一个小技巧。它继承自 C 语言：`++` 将值增加 1，`--` 将其减少 1。这里是另一个相同的例子，只是这次它写在准无限循环中，因为条件永远真。循环一直运行直到遇到 `break`；命令被取消：

```php
<?php
  $number = 1;
  while (true) {
    echo $number . "<br />";
    $number++;
    if ($number > 99) {
      break;
    }
  }
?>
```

#### For() 循环

对于固定的数字，有一种更美丽的循环：`for()` 循环。`for()` 循环的功能如下：`for (起始值; 条件; 重复)`。这里有一个简短的示例：

```php
<?php
  for ($x = 1; $x < 100; $x++) {
    echo $x . "<br />";
  }
?>
```

这将产生与使用 `while()` 循环相同的输出。函数的第三个参数指定了在每次循环后执行的命令。在这种情况下，将变量 `$x` 的值增加 1。该变量只能在循环内部使用。

#### Foreach() 循环

还有另一种遍历数组的循环：`foreach()`。这里有一个关于如何使用它的的示例：

```php
<?php
  $valueArray = array(2,4,16,32);
  foreach ($valueArray as $index => $value) {
    echo $value . "<br />";
  }
?>
```

输出：

2

4

16

32

在函数内部，变量 `$index` 和 `$value` 是可用的。通过 `$index`，你可以确定你进入了数组中的哪个条目（从 0 开始计数），或者如果你定义了数组的索引，你可以在循环内部获取它。变量名可以自由定义；但在循环块内部应该清楚变量的用途。如果你在循环中不需要数组索引（例如，你只想按顺序输出值），那么更加简单了：

```php
<?php
  $valueArray = array(2,4,16,32);
  foreach ($valueArray as $value) {
    echo $value . "<br />";
  }
?>
```

## 第 3 天

### 日期和时间（谁拨了钟？）

#### DATE()

使用 `date(format, time)` 函数，你可以以格式化的形式打印特定的时间。第一个参数指定格式，而第二个可选参数指定特定的时间。如果第二个参数不存在，则显示当前的服务器时间。这里有一个示例：

```php
<?php
  echo date("Y-m-d");
?>
```

输出（假设当前日期）：

2023-10-27

`time()` 函数返回当前时间，以 `Y-m-d` 格式：

```php
<?php
  echo date("Y-m-d", time());
?>
```

`time()` 函数返回的是时间戳。

#### microtime()

`date()` 函数的 `microtime()` 参数。`microtime()` 返回当前的当前的时间戳。你可以使用 `date()` 函数来格式化它：

```php
<?php
  $time = microtime(true);
  echo date("Y-m-d H:i:s", $time);
?>
```

输出：

2023-10-27 10:30:05

#### mktime()

`mktime(秒, 分, 时, 日, 年)` 用于指定一个特定的时间：

```php
<?php
  echo date("Y-m-d", mktime(0, 0, 0, 12, 2016));
?>
```

输出：2016-12-01

#### strtotime()

`strtotime("日期文本")` 将人类可读文本转换为 `date()` 函数格式的 `time()`：

```php
<?php
  echo date("Y-m-d", strtotime("May 17th"));
?>
```

输出：2023-05-17

你甚至可以从实际时间点进行一些计算：

```php
<?php
  echo date("Y-m-d", strtotime("next Friday"));
?>
```

年份，符合 ISO8601 标准。这与 `Y` 的值相同，除非 ISO 日历周（`W`）属于上一年或下一年，在这种情况下使用该年份。

示例：1999 或 2003

`Y`

四位数的

示例：1999 或 2003

`y`

两位数年份

示例：99 或 03

### 时间

`a`

小写的上午（morning）和下午（afternoon）

`am` 或 `pm`

`A`

大写的：上午（morning）和下午（afternoon）

`AM` 或 `PM`

`B`

瑞士网络时间 (Swatch Internet Time)

每天 000 到 999

`g`

12 小时制小时，不带前导零

1 到 12

`G`

24 小时制小时，不带前导零

0 到 23

`h`

12 小时制小时，带前导零

01 到 12

`H`

24 小时制小时，带前导零

00 到 23

`i`

分钟，带前导零

00 到 59

`s`

秒，带前导零

00 到 59

`u`

微秒

示例：654321

### 时区

`e`

时区名称

示例：`UTC`, `GMT`, `Atlantic/Azores`

`I` （大写 'i'）

夏令时间（夏季）日期

如果是夏令时间为 1，否则为 0。

`O`

与格林威治时间 (GMT) 的小时差

示例：+0200

`P`

与格林威治时间 (GMT) 的小时差，小时和分钟之间有冒号

示例：+02:00

`T`

时区缩写

示例：`EST`, `MDT`

`Z`

以秒为单位的时区偏移。UTC 西侧时区的偏移始终为负，UTC 东侧时区的偏移始终为正。

-43200 到 50400

### 完整日期/时间

`c`

ISO 8601 日期

2004-02-12T15:19:21+00:00

`r`

根据 RFC 2822 格式日期

示例：Thu, 21 Dec 2000 16:01:07 +0200

`U`

自 Unix 纪元（1970 年 1 月 1 日 00:00:00 GMT）以来秒数

### 文本函数（字符串操作）

在 PHP 中，有许多函数用于处理文本，例如分割长字符串并重新组装、搜索字符等。我希望向你展示这些关键函数，这样你就能解决几乎所有的字符串处理问题。还有许多其他函数超出了本书初学者的范围。但你可以在书末找到一些链接，指向解释了所有可用 PHP 函数的网站。

#### `str_replace`

一个常用的函数是 `str_replace`。该函数查找特定字符串出现后的文本并将其替换。第一个参数是要替换的文本，第二个参数是用于替换该文本的文本，第三个是在其中搜索的文本。该函数返回替换后的完整文本。作为一个可选参数，你可以指定执行的替换次数。这里有一个应用示例：

```php
<?php
$myText = "I am learning to program Java";
echo $myText;
$myText = str_replace("Java", "PHP", $myText);
echo "<br />";
echo $myText;
?>
```

输出：

I am learning to program Java

I am learning to program PHP

#### `substr`

另一个经常使用的文本函数是 `substr()`。它是 substring（子串）的缩写。它允许你分离字符串的一部分。函数预期的第一个参数是字符串，第二个是位置——从 0 开始计数，用于返回文本部分（子字符串）的字符——作为可选参数，第三个是返回字符串的长度。这是另一个示例：

```php
<?php
$myText = "I am learning to program PHP";
echo $myText;
$myText = substr($myText, 5, 8);
echo "<br />";
echo $myText;
?>
```

输出：

I am learning to program PHP

ning to le

#### `strtolower`

此函数返回给定字符串的小写：

```php
<?php
$myText = "I am learning to program PHP";
echo $myText;
$myText = strtolower($myText);
echo "<br />";
echo $myText;
?>
```

输出：

I am learning to program PHP

i am learning to program php

#### `toupper`

此函数返回给定字符串的大写：



```php
<?php
$myText = "I am learning to program PHP";
echo $myText;
$myText = strtoupper($myText);
echo "<br />";
echo $myText;
?>
```

输出：

I am learning to program PHP

I AM LEARNING TO PHP

#### `strpos`

通过此函数，你可以在文本中搜索特定的字符或字符串。...（注：原文此部分存在逻辑混乱或重复，已按原意进行对应翻译并保留结构）

#### `strpos`

...（原文重复部分）

#### `strlen`

此函数返回字符串的长度。

示例：

```php
<?php
$myText = "I am learning to program PHP";
echo $myText;
$myText = strtolower($myText);
echo "<br />";
echo $myText;
?>
```

#### `explode`

此函数根据分隔符分割字符串。

#### `explode`

...（原文重复部分）

#### `implode`

...（原文重复部分）

## 将代码拆分到多个文件

到目前为止，我们只编写了少于 100 行的短脚本。一旦你处理由数万行代码组成大型项目时，单个文件内的代码很快就会变得混乱。例如，将函数集合外包到另一个 `.php` 文件并将其集成到我们的主项目文件中会更有意义。

因此，我们创建了两个文件：

`functions_accounting.php`

```php
<?php

  function toNetto($amount, $vat_percent = 20) {
    $amount_netto = $amount / (100 + $vat_percent) * 100;
    return $amount_netto;
  }

  function toBrutto($amount, $vat_percent = 20) {
    $amount_brutto = $amount * (100 + $vat_percent) / 100;
    return $amount_brutto;
  }
?>
```

`vat_calculator.php`

```php
<?php
  include "functions_accounting.php";
  $price_austria = 1256;
  $price_netto = toNetto($price_austria);
  $price_germany = toBrutto($price_netto, 19);
  echo $price_germany;
?>
```

例如，除了我们的 `vat_calculator.php` 之外，如果 `functions_accounting.php` 文件位于 `functions` 文件夹中，我们必须按照以下方式指定：

```php
<?php
  include "functions/functions_accounting.php";
  $price_austria = 1256;
  $price_netto = toNetto($price_austria);
  $price_germany = toBrutto($price_netto, 19);
  echo $price_germany;
?>
```

你也可以在服务器上指定绝对路径，如下：

```php
<?php 
  include "/var/www/web1/html/functions/functions_accounting.php";
?>
```

但是，如果你这样做，当你将脚本传输到不同的服务器时，路径可能会发生。

## 第 4 天

## 使用数据库存储和读取信息

现在，我们可以查询、处理和输出大量信息。然而，我们仍然缺少一项重要功能：存储和检索数据的技术。大多数 PHP 项目使用 SQL 数据库。在每个数据库中，数据存储在表中。就像 Excel 一样，每个表由列和行组成。我们将学习如何访问它们。

### 在 PHP 中连接数据库

首先，我们需要从 PHP 脚本连接数据库。如果你没有按照第一章所述修改服务器的基础安装，则可以使用 `root` 用户访问数据库服务器。否则，你可能需要在服务器管理软件中分配密码。以下是连接到数据库服务器的示例：

```php
<?php
  $mysqli=new mysqli('localhost','root','password','my_db');
  $mysqli->close();
?>
```

`mysqli` 对象期望服务器、用户名和密码。服务器通常是 `localhost`。在脚本结束时，应尽早关闭 MySQL 连接以节省资源。

### 创建新数据库

如果我们成功连接到数据库服务器，我们需要选择一个数据库进行工作。大多数 Web 开发者使用图形化数据库管理工具。通过 XAMPP、MAMP 和默认预配置的 Web 服务器，这可以在 `http://localhost/phpmyadmin/` 或 `http://localhost/phpmyadmin/` 获取。

然而，我们想在脚本中直接尝试创建一个新数据库：

```php
<?php
  $mysqli=new mysqli('localhost','root','');
  $result=$mysqli->query("CREATE DATABASE test");
  $mysqli->close();
  var_dump($result);
?>
```

你已经知道了连接和断开 MySQL 服务器的功能。示例中的新函数是 `$mysqli->query`。通过查询，你告诉 MySQL 要做什么。然而，总是返回一个请求可以执行的结果。如果你运行脚本多次，只有第一次运行会收到成功消息，然后会收到指示数据库名称已分配错误消息。

### 选择我们的数据库

如果我们知道了数据库名称，我们需要指定脚本使用它：

```php
<?php
  $mysqli=new mysqli('localhost','root','','test');
?>
```

使用的数据库定义为最后一个参数。所有后续查询现在发送到所选数据库。

### 创建表

现在我们想要创建一个表，例如存储个人记录：

```php
<?php
  $mysqli=new mysqli('localhost','root','','test');
  $result = $mysqli->query("
  CREATE TABLE IF NOT EXISTS persons (
    id int(10) unsigned AUTO_INCREMENT,
    firstname varchar(50),
    lastname varchar(50),
    PRIMARY KEY (id)
  )");
  var_dump($result);
?>
```

这个查询稍微复杂。我们告诉 MySQL 创建一个名为 `persons` 的表（如果它不存在）。在创建列时，我们必须指定它们的类型。与 PHP 不同，数据库服务器必须确切知道值是文本、数字还是其他类型。

我们创建一个类型为 `Integer(10)` 的 `id` 列。整数是不带符号的数字。`unsigned` 属性意味着不存储符号，因此将没有负号。此外，我们使用 `AUTO_INCREMENT` 表示当我们向表中插入新行时，`ID` 列与最后一个最高条目相比自动增加 1。因此，我们获得了一个连续的数字，可以在表的最后行中将其指定主键。每个表必须有一个主键。这对于每个表行必须是唯一的，以便主键允许你始终访问特定的表行。括号 `(10)` 中的数字定义了数字的长度最大为十位，因此最大数字是 `9,999,999,999`。

我们还为两种可变字符（`VARCHAR`）类型的名字和姓名各创建了一个列。这意味着我们还不知道要存储的字符串长度将是多少，但我们将其限制在最多 50 个字符。或者，我们可以使用 `TEXT` 类型，它对字符数量没有限制，但消耗的内存多得多。

### 向数据库写入数据

在我们创建表之后，现在将向其填充第一条数据：

```php
<?php
  $mysqli=new mysqli('localhost','root','','test');
  $result = $mysqli->query("INSERT INTO persons (firstname, lastname) VALUES ('Hans', 'Meier');");
  var_dump($result);
?>
```

如果你现在在 PhpMyAdmin 中查看表，将看到刚刚添加的条目。

向表中插入数据有 `INSERT INTO` SQL 语句，后面是表名和填充的字段，然后是 `VALUES` 语句以及与指定字段相同的值。如果你想向表插入多行，只需要写一次 `VALUES` 并用逗号分隔各个行值：

```php
<?php
  $mysqli=new mysqli('localhost','root','','test');
  $result = $mysqli->query("INSERT INTO persons (firstname, lastname) VALUES ('Max', 'Meier'),('Maria', 'Mauser');");
  var_dump($result);
?>
```

### 从数据库中检索数据

在我们表中写入了一些行之后，我们想在脚本中再次查询它们。这是通过 `SELECT` 语句实现的：

```php
<?php
  $mysqli=new mysqli('localhost','root','','test');
  $result = $mysqli->query("SELECT firstname, lastname FROM persons;");
?>
```

```php
while ($row = $result->fetch_array()) {
    echo $row["firstname"] . " " . $row["lastname"] . "<br />";
}
?>
```

当你编写 PHP `/SQL` 脚本时，`SELECT` 语句将仍然是你忠实的伴侣。使用 `SELECT` 进行数据查询时，后面跟着的是表列；或者，如果你想查询表的所有列，也可以使用 `*`。其之后是 `FROM` 语句以及要从中查询数据的表名。

在我们提交查询后，我们使用函数 `$result->fetch_array()` 来运行结果，直到我们无法获取更多行。从每一行中，我们访问条目：名（first name）和姓（last name）。

此时，了解如何通过可选扩展 `SELECT` 语句的条件子句 `WHERE` 来访问表中的特定条目是非常重要的：

```php
<?php
  $mysqli=new mysqli('localhost','root', '','test');
  $result = $mysqli->query('SELECT firstname, lastname FROM persons WHERE firstname = "Hans";');
  while ($row = $result->fetch_array()) {
    echo $row["firstname "]. " " . $row["lastname"]. "<br />";
  }
?>
```

现在，我们只获取返回的行，即在 `firstname` 列中值为 Hans 的行。同样，我们现在可以查询特定的 `ID`。有了这些知识，你已经具备了永久存储数据并在未来使用另一个 PHP 脚本对其进行处理的能力。

有数百本书书籍可以让你理解许多其他的 `SQL` 语句以及如何创建高效的数据库或节省资源的查询。这对于具有数十万行数据和每分钟几十次查询的项目来说非常重要。在书的最后，你将找到关于 `SQL` 免费知识来源的好建议和链接。

## 从数据库中删除数据

从数据库中删除数据的 SQL 语句与 `SELECT` 几乎相同。你可以通过 `WHERE` 子句过滤数据来选择删除哪些数据。

```php
<?php
  $mysqli=new mysqli('localhost','root', '','test');
  $result = $mysqli->query('DELETE FROM persons WHERE firstname = "Hans";');
?>
```

数据库中所有 `firstname` 字段为 Hans 的行都将被删除。因此，请务必仔细检查你的 `WHERE` 子句。

## 文件操作（读取/写入文件）

为了将文本文件导入 PHP 或向其写入，必须使用文件句柄（filehandler）将其集成到脚本中：

```php
<?php
  $myFile = "myfile.txt";
  $filehandler = fopen($myFile, "r");
?>
```

`fopen` 函数返回的文件句柄。作为第一个参数，如果文件与 PHP 脚本在同一目录下，函数期望文件名或文件的相对路径。作为第二个参数，函数期望文件的访问模式。这指定了我们是想通过文件句柄获取文件的读取权限，还是可以使用我们自己的内容对其进行描述或修改。

以下是 `fopen()` 的可用访问模式：

- `'r'` 只读，将文件指针放在文件开头
- `'r+'` 读和写，将文件指针放在文件开头
- `'w'` 只写，将文件截断为零长度或创建一个新文件
- `'w+'` 读和写，将文件截断为零长度或创建一个新文件
- `'a'` 只追加，将文件指针放在文件末尾
- `'a+'` 追加和写，将文件指针放在文件末尾
- `'x'` 只创建和写；如果文件存在则返回 false
- `'x+'` 只创建和写；如果文件存在则返回 false

### 保存到文件

要创建一个新文件或扩展现有文件，我们可以使用以下代码：

```php
<?php
  $myFile = "myfile.txt";
  $filehandler = fopen($myFile, "a");
  fwrite($filehandler, "I am a line\n");
  fclose($filehandler);
?>
```

### 读取文件

在上面的脚本中，`fwrite` 用于文件写入内容。要从文件中读取，我们使用以下代码：

```php
<?php
  $myFile = "myfile.txt";
  $filehandler = fopen($myFile, "r");
  $contents = fread($filehandler);
  fclose($filehandler);
?>
```

### 删除文件

如果你想删除文件，可以使用 `unlink` 函数：

```php
<?php
  $myFile = "myfile.txt";
  unlink($myFile);
?>
```

## 第 5 天

### 编写整洁的代码（一年后仍然易读）

在你养成不整洁的编程风格之前，我想给你一些关于如何在程序员道路上编写“整洁”代码的建议。

一方面，正如在变量章节中所描述的，使用适当且自描述的变量和函数名是极其重要的。在未知代码中读取 `$a`、`$b` 或 `$x` 等变量是非常令人失望的，因为它们没有显示其中将存储什么内容。

在编写代码时使用制表符（tab stops）。

## 原则：永远不要信任来自外部的数据

如果你遵循这一原则，你已经在对抗破解者和黑客的战斗中赢得了一半。关于对外部数据的不信任，我的意思是，你应该验证输入数据，以检查它们是否符合预期的格式。这意味着，如果要输入一个数字，最好检查该函数是否为数值（`$input`）、它是否确实是一个数字，或者电子邮件地址是否按要求设置（即恰好有一个 `@` 字符且末尾必须指定一个域名）。这引出了我们的下一个话题。

## 防止 SQL 注入

SQL 注入是一种操纵 SQL 查询的方法，使其执行其预期之外的操作。如果你没有对输入的数据进行过滤，就会发生这种情况。

假设我们有以下脚本来为网页提供登录功能：

```php
<?php

  $username = $_GET["username"];
  $password = $_GET["password"];
  $sql = "SELECT \* FROM users WHERE username = """.$username."" AND password = "" . $password ."" ";
  $mysqli=new mysqli('localhost','root','', 'test');
  $result = $mysqli->query($sql);
  echo "Found the following user(s): ";
  while ($row = $result->fetch_array()) {
    echo $row["username"]. "<br />";
  }

?>
```

如果用户只是输入用户名或密码，这个功能没有问题。但不幸的是，有一些技术高明的破解者会寻找这种简单的登录方式，有些人使用自动化机器人寻找这些登录口，并尝试输入以下内容：

用户名: admin

密码: `" OR 1=1`

如果我们将这段文本未经过滤地传递到 SQL 查询中，将得到以下 SQL 语句：

`SELECT \* FROM users WHERE username = "admin" AND password = "" OR 1=1`

由于 `1` 始终等于 `1`，因此始终会返回结果。所以，破解者以 admin 的身份登录，或者甚至添加了自己的用户：

用户名: x

密码: `x"; INSERT INTO users (username, password) VALUES ("mynewuser", "mypassword");`

SQL 将将变为：



`SELECT * FROM users WHERE username = "x" AND password = "x"; INSERT INTO users (username, password) VALUES ("mynewuser", "mypassword");`

这两个 SQL 语句都将被执行，破解者已经创建了一个新用户账户。理论上，他还可以发送 `DELETE` 命令，从而破坏我们的数据库，或者例如更改管理员的密码。

但你如何保护自己呢？

要么对指定的数据进行过滤，只允许允许字符（`a-z`、`A-Z`、`0-9`），要么对输入数据进行“转义”。这意味着所有的特殊字符以及整个字符串都被单引号封装起来，从而变得“无害”。这里有一个现成的函数 `$mysqli->real_escape_string()`，它接收一个字符串作为参数，并返回其安全的转义版本。

示例：

`$password = $mysqli->real_escape_string($password);`

## 保持你的密码加密

即使是大型全球性公司，也通过惨痛的经验学到了：必须在数据库中始终以加密方式存储密码。有些加密方法只进行单向加密，并从任意长度的字符串生成所谓的哈希（hashes）。这些是以前已知长度的字符串。PHP 从 PHP 5.5 版本起提供了了自己的经过良好测试的哈希库。你可以使用它，例如通过 `password_hash($password, ALGORITHM)` 函数。

```php
<?php

  $password = "password123";
  $hash = password_hash($password, PASSWORD_BCRYPT);
  echo $password;  
  echo "<br />";
  echo $hash;

?>
```

输出（哈希值可能因服务器而异且每次都是生成的）：

`password123`

`$2y$10$K6JP7Lfu2.wjuEGLzCact.8GZaok5oSWhH49.TzTZm5/PPfDzXYMW`

哈希值无法再明文解密。现在你可以将这些密码哈希存储在数据库中。每当用户想要登录时，使用 `password_hash()` 函数为用户输入的数据生成哈希。如果哈希相同，说明用户了正确的密码。如果黑客想要窃取你的数据库，我们需要大量时间来尝试所有的字典列表，因为 `password_hash()` 函数需要一些时间来生成哈希。你可以添加一个可选的 `$options` 参数并定义使用更复杂的哈希方法，这样哈希过程会变得更慢且更难破解。

## 为你的密码添加盐（Salt）

另一个安全方面是保护自己免受使用不安全的用户的影响。大型用户数据库的数据显示，很大比例的用户始终使用相同的密码，例如 `asdf123`、`password`、`1234567890`。如果破解者获取了带有哈希的用户名，对他来说很容易将哈希与互联网上常用的 1000 个密码进行匹配。为了防止这一点，我建议为每个项目添加一个长随机字符串，例如 `afdsoin23oidvnio3iosdvn09832jknlsd`。

如果用户再次登录并使用密码 `password`，我们存储 `passwordafdsoin23oidvnio3iosdvn09832jknlsd` 的哈希。

### 网站提示

**PHP**

`www.php.net/manual/`

**SQL**

`www.w3schools.com/php/`

**MySQL**

`dev.mysql.com/doc/`

### 书籍提示

**PHP and MySQL for Dynamic Sites, Fourth Edition: Visual Quick Guide**

作者 Larry Ullman, Peachpit Press, ISBN 0321784073

**Head First PHP & MySQL: A Brain-Friendly Guide**

作者 Lynn Beighley and Michael Morrison, O'Reilly Media, ISBN-10 0596006306, ISBN-13 978-0596006303

**PHP Objects, Patterns, and Practice**

作者 Matt Zandstra, ISBN-13 978-1430260318, ISBN-10 1430260319

**Wikibook PHP Programming**

`https://en.wikibooks.org/wiki/PHP_Programming`

## 结语

希望你喜欢这个使用 PHP 和 MySQL 进入 Web 开发世界的介绍，并且现在已经准备好实现你自己的第一个小项目了。

如果你需要关于接下来尝试什么的的想法：你可以利用本课程提供的知识，例如为网站创建一个留言板，或者编写一个根据星期和时间显示不同问候语的小脚本。

或者，建立一个用于收集签名或投票的页面如何？该页面可以将数据写入数据库，但在此之前应该检查电子邮件地址和/或特定的姓氏与名字组合是否已经存在。

你对这本书有任何反馈吗？我将不胜荣幸。

你可以通过电子邮件地址 `books@theklaus.at` 与我联系。
