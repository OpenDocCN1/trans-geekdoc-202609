
# 要使用 PHP 创建动态网站

要使用 PHP 创建动态网站，你必须知道如何向 Web 浏览器发送数据。PHP 有许多内置函数可实现此目的，最常用的是 `echo` 和 `print`。我个人倾向于使用 `echo`：

```php
echo 'Hello, world!';

echo "What's new?";
```

如果你愿意，也可以使用 `print`（这个名称更明显地表明了它的作用）：

```php
print 'Hello, world!';

print "What's new?";
```

正如这些示例所示，你可以使用单引号或双引号（但这两种引号有区别，到本章结束时会清楚地说明）。函数名后的第一个引号表示要打印的消息的开始。下一个匹配的引号（即与开始引号同类型的下一个引号）表示要打印的消息的结束。

除了学习如何向 Web 浏览器发送数据，你还应该注意到，在 PHP 中，所有语句——用外行话来说就是一行执行的代码——都必须以分号结尾。此外，PHP 在函数名方面是*不区分大小写*的，所以 `ECHO`、`echo`、`eCHo` 等都能工作。当然，全小写版本最容易输入。

## 需要转义

正如你可能发现的，向 Web 发送数据时的一个麻烦在于打印单引号和双引号。以下任一情况都会导致错误：

```php
echo "She said, "How are you?"";

echo 'I'm just ducky.';
```

解决此问题有两种方法。首先，打印双引号时使用单引号，反之亦然：

```php
echo 'She said, "How are you?"';

echo "I'm just ducky.";
```

或者，你可以通过在有问题的字符前加上反斜杠来*转义*它：

```php
echo "She said, \"How are you?\"";

echo 'I\'m just ducky.';
```

被转义的引号将像其他字符一样仅被打印出来。理解如何使用反斜杠转义字符是一个重要概念，本章末尾将更深入地介绍。

## 脚本 1.3. 使用 `print` 或 `echo`，PHP 可以向 Web 浏览器发送数据

```html
1   <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML
        1.0 Transitional//EN" "http://www.w3.org/
        TR/xhtml1/DTD/xhtml1-transitional.dtd">
2   <html xmlns="http://www.w3.org/1999/
        xhtml" xml:lang="en" lang="en">
3   <head>
4       <meta http-equiv="Content-Type"
            content="text/html; charset=utf-8" />
5       <title>Using Echo</title>
6   </head>
7   <body>
8       <!-- Script 1.3 - second.php -->
9       <p>This is standard HTML.</p>
10  <?php
11  echo 'This was generated using PHP!';
12  ?>
13  </body>
14  </html>
```

## 向 Web 浏览器发送数据

**1.** 在文本编辑器或 IDE 中打开 `first.php`（参考脚本 1.2）。

**2.** 在 PHP 标签之间（第 10 行和第 11 行），添加一条简单的消息（脚本 1.3）：

```php
echo 'This was generated using PHP!';
```

你输入什么消息、使用哪个函数（`echo` 或 `print`），甚至使用哪种引号，其实都无关紧要——只是如果你的消息中包含单引号或双引号，请务必小心（请参阅侧边栏“需要转义”）。

**3.** 如果愿意，更改页面标题以更好地描述此脚本（第 5 行）：

```html
<title>Using Echo</title>
```

此更改仅影响浏览器窗口的标题栏。

**4.** 将文件保存为 `second.php`，将其放入你的 Web 目录，并在 Web 浏览器中测试它。

![Image](img/01_figure_03_a.jpg)

结果仍然不算漂亮，但此页面是由 PHP 部分动态生成的。

请记住，所有 PHP 脚本都必须通过 URL（`http://` `某物`）运行！

**5.** 如有必要，调试脚本。

如果你看到解析错误而不是你的消息，请检查是否已同时打开和关闭引号，并转义了任何有问题的字符（请参阅侧边栏）。此外，确保每个语句都以分号结尾。

![Image](img/01_figure_04_b.jpg)

这可能是你作为 PHP 程序员将看到的许多解析错误中的第一个（这个是由省略结束引号引起的）。

如果你看到一个完全空白的页面，这可能有两个原因之一：

*   HTML 有问题。通过查看页面源代码并寻找那里的 HTML 问题来测试这一点。

    ![Image](img/01_figure_05_c.jpg)

    导致 PHP 空白页面的一个可能原因是简单的 HTML 错误，比如这里的结束 `title` 标签（它缺少了斜杠）。

*   发生了错误，但你的 PHP 配置中关闭了 `display_errors`，因此什么也没显示。在这种情况下，请参阅附录 A 中关于如何配置 PHP 以便重新开启 `display_errors` 的部分。

### 提示

从技术上讲，`echo` 和 `print` 是*语言结构*，而非函数。话虽如此，不要因此感到困惑，为了方便我继续称它们为“函数”。此外，正如你稍后在本书中将看到的，我提及函数时会包含括号——例如 `number_format()`，而不仅仅是 `number_format`——以帮助将它们与变量和 PHP 的其他部分区分开来。这只是我自己的一个小习惯。

### 提示

你可以而且经常会使用 `echo` 和 `print` 向 Web 浏览器发送 HTML 代码，如下所示：

```php
echo '<p>Hello, <b>world</b>!</p>';
```

![Image](img/01_figure_06_d.jpg)

PHP 可以向 Web 浏览器发送 HTML 代码（如此处的格式）以及简单文本。

### 提示

`echo` 和 `print` 都可以跨多行使用：

```php
echo 'This sentence is
printed over two lines.';
```

### 提示

### 理解空白字符

使用 PHP 时，你会将数据（如 HTML 标签和文本）发送给 Web 浏览器，浏览器随即会将这些数据渲染为最终用户所看到的 Web 页面。因此，你用 PHP 所做的工作通常是在创建 Web 页面的 *HTML 源代码*。牢记这一点，有三个值得注意的 *空白字符*（额外的空格、制表符和空行）区域：你的 PHP 脚本中、你的 HTML 源代码中，以及渲染后的 Web 页面中。

PHP 通常对空白字符不敏感，这意味着你可以随意安排代码的间距，以使脚本更具可读性。HTML 通常也不敏感。具体来说，HTML 中唯一影响渲染页面的空白字符是单个空格（多个空格仍会被渲染为一个）。如果你的 HTML 源代码中的文本分布在多行上，并不意味着它在渲染后的页面中会显示为多行（![Image](img/graycircle-e.jpg) 和 ![Image](img/graycircle-f.jpg)）。

要改变渲染后 Web 页面中的间距，请使用 HTML 标签 `<br />`（换行，旧版 HTML 标准中为 `<br>`）和 `<p></p>`（段落）。要改变用 PHP 创建的 HTML *源代码*的间距，你可以：

*   在多行中使用 `echo` 或 `print`。
*   在双引号内打印换行符（`\n`），这等同于按下 Enter 或 Return 键。

## 编写注释

创建可执行的 PHP 代码只是编程过程的一部分（诚然，这是最重要的部分）。任何编程工作中另一个次要但仍至关重要的方面是为代码编写文档。事实上，当有人问我什么特质能区分初级程序员和经验丰富的程序员时，我坚定的回答是：对注释的良善且彻底的使用。

在 HTML 中，你可以使用特殊标签添加注释：

```html
<!-- Comment goes here. -->
```

HTML 注释可在源代码中查看，但不会出现在渲染后的页面中（请参阅上一节中的 ![Image](img/graycircle-e.jpg) 和 ![Image](img/graycircle-f.jpg)）。

PHP 注释的不同之处在于它们根本不会被发送给 Web 浏览器，这意味着最终用户甚至无法在查看 HTML 源代码时看到它们。

PHP 支持三种注释语法。第一种使用井号或数字符号（`#`）：

```php
# This is a comment.
```

第二种使用双斜杠：

```php
// This is also a comment.
```

这两种方式都会导致 PHP 忽略从该符号开始直到行尾（当你按下 Return 或 Enter 键时）的所有内容。因此，这两种注释仅用于单行。它们也常用于在包含 PHP 代码的同一行末尾添加注释：

```php
print 'Hello!'; // Say hello.
```

第三种风格允许注释跨越多行：

```php
/* This is a longer comment
that spans two lines. */
```

**脚本 1.4.** 这些基本注释演示了可在 PHP 中使用的三种注释语法。

```php
1   <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML
        1.0 Transitional//EN" "http://www.w3.org/
        TR/xhtml1/DTD/xhtml1-transitional.dtd">
2   <html xmlns="http://www.w3.org/1999/
        xhtml" xml:lang="en" lang="en">
3   <head>
4       <meta http-equiv="Content-Type"
            content="text/html; charset=utf-8" />
5       <title>Comments</title>
6   </head>
7   <body>
8   <?php

9   # Script 1.4 - comments.php
10  # Created March 16, 2011
11  # Created by Larry E. Ullman
12  # This script does nothing much.

13  echo '<p>This is a line of text.<br />
            This is another line of text.</p>';

14  /*
15  echo 'This line will not be
            executed.';
16  */

17  echo "<p>Now I'm done.</p>";
        // End of PHP code.

18  ?>
19  </body>
20  </html>
```

## 为脚本添加注释

**1.** 在文本编辑器或 IDE 中新建一个 PHP 文档，命名为 `comments.php`，从初始 HTML 开始（**脚本 1.4**）：

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>Comments</title>
</head>
<body>
```

**2.** 添加初始 PHP 标签并编写第一批注释：

```php
<?php
# Script 1.4 - comments.php
# Created March 16, 2011
# Created by Larry E. Ullman
# This script does nothing much.
```

每个脚本应包含的首批注释之一是一个介绍性块，列出创建日期、修改日期、创建者、创建者联系方式、脚本用途等。有人建议 Shell 风格的注释（`#`）在脚本中更醒目，因此最适合此类标注。

**3.** 向 Web 浏览器发送一些 HTML：

```php
echo '<p>This is a line of text.<br />This is another line of text.</p>';
```

此处具体做什么并不重要，只要生成一些供 Web 浏览器显示的内容即可。为了多样化，`echo` 语句将打印一些 HTML 标签，包括一个换行符（`<br />`）以增加生成的 HTML 页面的间距。

**4.** 使用多行注释将第二条 `echo` 语句注释掉：

```php
/*
echo 'This line will not be executed.';
*/
```

通过用 `/*` 和 `*/` 包裹任意 PHP 代码块，你可以使该代码失效，而无需将其从脚本中删除。稍后移除注释标签，即可重新激活该部分 PHP 代码。

**5.** 在第三条 `echo` 语句后添加最后一条注释：

```php
echo "<p>Now I'm done.</p>"; // End of PHP code.
```

这最后一条（多余的）注释展示了如何在行尾放置注释，这是一种常见做法。注意此处消息由双引号括起，因为单引号会与撇号冲突（请参阅本章前面的“需要转义”侧边栏）。

**6.** 关闭 PHP 部分并完成 HTML 页面：

```php
?>
</body>
</html>
```

**7.** 将文件保存为 `comments.php`，将其放入 Web 目录，并在 Web 浏览器中测试 ![Image](img/circle-a.jpg)。

![Image](img/01_figure_09_a.jpg)

![Image](img/circle-a.jpg) 脚本 1.4 中的 PHP 注释不会出现在 Web 页面或 HTML 源代码中 ![Image](img/graycircle-b.jpg)。

**8.** 如果你想一探究竟，请在 Web 浏览器中查看源代码，以确认 PHP 注释确实不在那里 ![Image](img/circle-b.jpg)。

![Image](img/01_figure_10_b.jpg)

![Image](img/circle-b.jpg) 脚本 1.4 中的 PHP 注释在客户端浏览器中无处可寻。

> **提示**
>
> 你不应该嵌套多行注释（`/* */`）（将一个放在另一个里面）。这样做会导致问题。

> **提示**
> 任何 PHP 注释都可以用在行尾（例如，在函数调用之后）：
>
> ```php
> echo 'Howdy'; /* Say 'Howdy' */
> ```
>
> 虽然这是允许的，但这种用法远不如前者常见。

> **提示**
> 你的脚本几乎不可能注释过多。编码时，始终宁可多写注释也不要少写。话虽这么说，为了节省篇幅，本书中的脚本不会像我建议的那样有详尽的文档注释。

> **提示**
> 同样重要的是，当你修改脚本时，要保持注释的更新和准确。没有什么比注释说一套而代码实际做另一套更令人困惑的了。

## 什么是变量？

变量是用于临时存储值的容器。这些值可以是数字、文本，或更复杂的数据。PHP 支持八种类型的变量。其中包括四种标量（单值）类型——`Boolean`（`TRUE` 或 `FALSE`）、`integer`（整数）、`floating point`（浮点数/小数）和 `strings`（字符串/字符）；两种非标量（多值）类型——`arrays`（数组）和 `objects`（对象）；加上 `resources`（资源，你会在与数据库交互时见到）和 `NULL`（这是一种没有值的特殊类型）。

无论你创建哪种类型，PHP 中所有变量名都遵循特定的语法规则：

*   变量名必须以美元符号（`$`）开头，例如 `$name`。
*   变量名可以包含字母、数字和下划线的组合，例如 `$my_report1`。
*   美元符号后的第一个字符必须是字母或下划线（不能是数字）。
*   **PHP 中的变量名区分大小写！** 这是一条非常重要的规则。这意味着 `$name` 和 `$Name` 是完全不同的两个变量。

要开始使用变量，接下来的脚本将输出三个*预定义变量*的值。标准变量是在脚本执行期间赋值的，而预定义变量在脚本开始执行时就已经有值了。这些预定义变量大多反映了服务器整体的属性，例如正在使用的操作系统。

在进入脚本之前，还有两件事你应该知道。首先，变量可以使用等号（`=`）赋值，这也称为*赋值运算符*。其次，要显示变量的值，可以不加引号直接打印变量：

```php
print $some_var;
```

或者变量可以在*双*引号内打印：

```php
print "Hello, $name";
```

你不能在单引号内打印变量：

```php
print 'Hello, $name'; // 不会生效！
```

**脚本 1.5.** 该脚本打印 PHP 众多预定义变量中的三个。
