
# 第 1 章：引言

你好：感谢你拿起这本书。我很高兴你选择这这本书，我诚地希望它能帮助你掌握 PHP，并带你进入动态编程的世界。在本书中，我们将涵盖 PHP 的大部分主要主题。这些主题经过精心挑选，旨在让你广泛接触相关知识，同时又不会被不必要的细节所淹没。在书的最后，我们还将构建一个动态网站。期待吗？

在正式开始 PHP 之前，请注意，本书要求你对 HTML 和 `MySQL` 有基础了解。

## 1.1 什么是 PHP？

PHP 是一种主要用于 Web 开发的通用编程语言。它由 Rasmus Lerdorf 于 1994 年创建，允许开发者轻松地创建动态网页。例如，开发者可以在 HTML 中创建一个表单，并使用 PHP 对其进行处理。根据表单中输入的内容，开发者可以使用 PHP 显示不同的输出结果。大多数情况下，PHP 被用作服务器端语言。这意味着 PHP 代码不会在用户的计算机（也称为客户端）上处理。换句话说，当你通过浏览器中访问一个 PHP 页面时，代码不会在你的电脑上运行。相反，你的浏览器会向 Web 服务器发送请求，然后由服务器处理代码并将结果以网页的形式返回给浏览器。

通常情况下，这个 Web 服务器是存储 PHP 文件的远程计算机。为了让 Web 服务器处理 PHP 代码，需要安装一种名为 PHP 解释器的特殊软件。在下一章中，我们将学习使用一个名为 `XAMPP` 的免费软件来搭建 Web 服务器并安装 PHP 解释器。

## 1.2 为什么要学习 PHP？

学习 PHP 有很多理由。首先，PHP 是最流行的 Web 编程语言之一，用于 WordPress、Drupal 和 Joomla 等许多内容管理系统。因此，对 PHP 程序员的需求很大。如果你计划作为自由开发者工作，PHP 是一项必不可少的技能。其次，PHP 设计对初学者友好且易于学习。此外，由于这种语言的流行，如果你在 PHP 代码中遇到任何问题，都可以轻松找到帮助。在互联网上简单搜索可能就能帮你解决面对大部分问题。最后但同样重要的是，PHP 的语法与 Java 或 C 等其他编程语言非常相似。一旦熟悉了 PHP，你会发现掌握其他语言变得容易得多。准备好开始了吗？让我们开始吧！

# 第 2 章：安装 XAMPP

正如上一章提到的，我们将在章中学习设置 Web 服务器并安装 PHP 解释器。此外，由于我们在本书的后续部分将使用 PHP 与数据库交互，我们还需要设置数据库服务器。为了设置我们的 Web 和数据库服务器，我们需要安装三个软件：Apache Web 服务器、PHP 解释器和 MarieDB 数据库服务器。如果逐个安装这三个软件可能会非常麻烦。幸运的是，Apache Friends 的热心人士创建了一个包含了我们所需软件的免费软件包。这个软件包被称为 `XAMPP`，代表跨平台（X）、Apache Web 服务器（A）、MarieDB 数据库服务器（M）、PHP（P）和 Perl（P）。

MarieDB 数据库服务器是 MySQL 服务器的社区开发分支。虽然 `XAMPP` 中的 `M` 正式代表 `MarieDB`，但你会发现 `XAMPP` 中将数据库服务器标记为 `MySQL`。我们将遵循这一标签，并在书中将数据库服务器称为 `MySQL`。关于安装 `XAMPP` 以及使用它设置服务器的详细说明，请查看 https://learncodingfast.com/how-to-install-xamppand-brackets。本书的配套网站提供了相关说明，每当 `XAMPP` 发生变化时，你都可以在网站上找到更新后的说明。这将确保你始终获得最新的安装说明。

除了安装 `XAMPP` 之外，强烈建议你安装一个高级文本编辑器来编写代码。虽然你完全可以使用基础文本编辑器（如 `Notepad`）进行编码，但高级文本编辑器提供了语法高亮等功能，使你的代码更易读和调试。推荐的免费编辑器是 `Brackets`。关于安装 `Brackets` 的说明，请前往 https://learncodingfast.com/how-to-installxampp-and-brackets。

## 2.1 配置 php.ini

在电脑上安装好 `XAMPP` 和 `Brackets` 后，你就可以开始创建你的动态网站了。然而，在我们开始之前，我们需要对 PHP 服务器上的错误设置进行一些更改。这确保了当我们的代码中出现任何错误时，浏览器都会显示错误信息。配置这些设置最直接的方法是修改名为 `php.ini` 的文件。以下说明在编写时有效。如果说明有任何更改，你可以在 https://learncodingfast.com/php 找到更新后的说明。

要修改 `php.ini`，我们需要先找到该文件。在 Windows 上，启动 `XAMPP` 并点击 `Apache` 的 `Config` 按钮。接下来，选择 `php.ini`。文件将在 `Notepad` 中打开![](img/image_rsrc1HZ.jpg)

在 Mac 上，启动 `XAMPP` 并点击 `General` 标签页中的 `Start` 按钮。等待状态变为绿色。接下来，选择 `Volumes` 标签页并点击 `Mount` 按钮。最后，点击 `Explore` 并寻找 `etc` 文件夹。你会在该文件夹内找到 `php.ini`。使用 `Brackets` 打开它![](img/image_rsrc1J0.jpg)

打开 `php.ini` 后，滚动到页面底部并向其中添加以下行：

```
error_reporting=E_ALL
display_errors=On
```

这些行被添加到页面底部，是为了如果之前设置过这些设置（在 `php.ini` 文件的早期部分），新行将覆盖之前的设置。我们将在将在第 12 章详细讨论这两个设置。接下来，保存文件并重启 `Apache`。在 Windows 上，只需停止 `Apache` 服务器（如果它正在运行）并重新启动。在 Mac 上，选择 `Services` 标签页并点击 `Apache`。如果 `Apache` 正在运行，点击 `Restart` 按钮。否则，点击 `Start` 按钮。等待 `Apache` 重启，你的设置就会更新。现在，每当代码出现错误时你都会获得错误信息。根据你使用的 PHP 版本，你在测试书中代码时遇到的一些错误可能与描述的有所不同。不要担心，我们将在第 12 章深入讨论错误。

## 2.2 重要链接

在开始编写第一个网页之前，我想请你两个两个链接。第一个是 https://learncodingfast.com/php 。本书使用了大量的示例来说明不同的概念。虽然我们鼓励你自己在 `Brackets` 中手动输入这些示例，但如果你不愿意这样做，可以在上述链接下载源代码。项目文件以及本书的任何额外注释或更新也可以在那里找到。接下来，我们还有一个错表页面。虽然我们已尽力确保书中没有错误，且所有源代码已在多台机器上经过广泛测试，但如果我们遗漏了任何错误，你可以在 https://learncodingfast.com/errata 找到错表。

## 2.3 编写我们的第一个网页

太棒了！我们现在准备好编码了。首先，确保你已经在 `XAMPP` 中启动了 `Apache`。注意：如果在启动 `Apache` 时遇到任何问题，可能是由于端口冲突。请遵循 https://learncodingfast.com/how-to-install-xampp-and-brackets 的说明解决冲突。接下来，创建一个新文件并在 `Brackets` 中添加以下代码：

```html
<!DOCTYPE html>
<html>
<head>
  <title>My first page</title>
</head>
<body>
  <h1>My first page</h1>
  <?php echo "Hello World!"; ?>
</body>
</html>
```

保存文件为 `index.php` 并将其放在 `htdocs` 文件夹中。现在在浏览器中访问 `http://localhost/index.php`。你应该能看到“Hello World!”。现在，让我们尝试添加一些动态。将 `index.php` 中的 `<?php echo "Hello World!"; ?>` 替换为以下代码，然后再次访问 `http://localhost/index.php` 来看到当前的日期：

```php
<?php
$date = date("Y-m-d");
echo "Today's date is: " . $date;
?>
```

恭喜！你已经创建了第一个动态网页。在接下来的章节中，我们将学习如何使用 PHP 的更多功能。

使用 `echo "Hello World!";` 在浏览器上显示“Hello World!”字样。这被称为回显语句（echo statement）；我们将在下一章学习更多相关内容。注意我们 echo 语句是以分号（`;`）结尾的吗？PHP 中的所有语句都必须以分号结束。这与我们在英语中使用句号（`.`）结束句子相似。如果你现在加载 `hello.php`，你将得到 ![](img/image_rsrc1J1.jpg)作为输出。就是这样。我们刚刚编写了自己的第一个 PHP 网页。简单吗？太棒了！让我们继续。

# 第 3 章：基础 PHP 任务

在上一章中，我们安装了 XAMPP 和 Brackets，并编写了第一个 PHP 脚本。在本章中，我们将学习在 PHP 中执行三个非常基础的任务——向用户显示输出、在多个页面之间复制代码以及重定向用户。

## 3.1 显示输出

在学习显示输出之前，让我们先创建一个 PHP 文件作为模板，用于测试本节中的 PHP 语句。在 Brackets 中创建一个文件并将其保存为 `output.php` 到你的 `htdocs` 文件夹中。在 `output.php` 中添加以下代码：

```php
<?php 

// 在此处添加代码。每你想测试本节中的任何 PHP 语句时，都可以将该语句添加到 output.php（在 <?php 开启标签之后），并在浏览器中加载它以检查输出。注意我们没有在 `output.php` 中添加结束标签 (?> ) 吗？这是因为 `output.php` 只包含 PHP 代码。根据 PHP 框架互操作组（PHP Framework Interop Group）推荐的标准，任何仅包含 PHP 代码的 PHP 脚本都不应该以结束标签结尾。这是为了防止末尾出现意外的空格，这在修改响应头时可能会导致“标头已发送”（Headers already sent）等警告。如果上面的语句看起来没有意义，不要担心；我们稍后会学习“标头已发送”警告。现在，让我们继续学习如何在 PHP 中显示输出。 
```

### 3.1.1 echo

在 PHP 中显示输出最简单的方法是使用 `echo` 语句。要这样做，我们在 `echo` 关键字之后将想要显示的文本包括在一对匹配的引号中。`echo` 关键字对大小不敏感。因此，`echo`、`Echo` 或 `ECHO` 均有效。使用 `echo` 语句非常直观。我们在第 2 章就用过它来显示“Hello World!”字样。除了使用 `echo` 语句显示简单的文本消息外，我们还可以使用它们显示带有 HTML 标记的文本。例如，我们可以写 `echo 'PHP is fun<BR>and easy!';`

这带给我们的：

PHP is fun

and easy!

作为输出；由于 `<BR>` 标签，文本“and easy!”显示在第二行。

我们还可以在单个 `echo` 语句中组合多个消息。要这样做，我们用逗号分隔消息。例如，`echo "ABCD", "EFGH";`

带给我们的是：

ABCDEFGH

作为输出。当我们的消息更复杂时（例如消息包含变量和函数时），组合消息是非常用的。我们将在书的后续部分学习变量和函数。最后但同样重要的是，我们可以使用带括号或不带括号的 `echo` 语句。你可能看到过执行以下操作的代码：`echo ("ABCD");`

这在大多数情况下都是没的。然而，如果你使用括号，则不允许在单个 `echo` 语句中组合多个消息。例如，`echo ("ABCD", "EFGH");`

将导致错误。在大多数情况下，你最好使用不带括号的 `echo` 语句。

### 3.1.2 print

除了使用 `echo` 语句显示输出外，我们还可以使用 `print` 语句。

`print` 语句与 `echo` 语句非常相似。让我们来看例子：`print "My name is Brody.";`

带给我们的是：

My name is Brody.

作为输出。如你所示，`print` 语句的作用就像 `echo` 语句一样。虽然它们之间有一些区别，但在大多数情况下，没有必要使用 `print` 语句。在 PHP 中，有多种方法执行某项任务是相当常见的。这是开发者对 PHP 的主要抱怨之一，因为它不必要地使事情复杂化。在大多数情况下，这些方式彼此非常相似。为了不让你被过多的选项困扰，我将在书中坚持使用一种方案，并在必要时简要提到其他选项。在本书，我将使用 `echo` 语句来显示输出。

### 3.1.3 转义字符

接下来，让我们学习在 PHP 中转义字符。在之前的章节中，我们学习了在使用 `echo`（或 `print`）语句时用引号包围文本。如果我们想显示单引号会发生什么？例如，假设我们有以下语句：

`echo '<BR>Today is Friday, we're going to the zoo.';` 当我们尝试运行上面的语句时会得到错误，因为 PHP 默认不区分单引号和双引号。因此，它将“we’re”单词中的单引号视为闭合引号。换句话说，它将语句视为 `echo '<BR>Today is Friday, we'` 并期望在单引号后有一个分号或逗号。当这种情况没有发生时，PHP 就会感到困惑并给我们一个错误。处理上述错误有两种方法。第一种是使用双引号包围文本，将语句重写为 `echo "<BR>Today is Friday, we're going to the zoo.";` 由于 PHP 使用双引号来关闭双引号，因此“we're”中的单引号就不会被误认为引号。另一种方法是通过反斜杠字符（`\`）来转义原始语句中的单引号。转义改变了字符的含义。如果没有反斜杠，单引号会被解释为要显示的单引号。为了在浏览器上显示单引号，我们可以使用下面的语句：`echo '<BR>Today is Friday, we\'re going to the zoo.';` 这带给我们的输出：

Today is Friday, we're going to the zoo.

反义字符的其他常见用法包括：显示双引号 `echo ""` 输出错误，而 `echo "\""` 输出 `"`；显示反斜杠本身 `echo "\"` 输出错误，而 `echo "\\"` 输出 `\`

## 3.2 复制代码

接下来，让我们学习如何在 PHP 脚本中复制代码。在 PHP 中，通常情况下，脚本是相互独立的。因此，在一个脚本（例如 `index.php`）中编写的代码在导航到另一个页面时是不可用的。如果我们希望网站上的多个页面具有相同的 HTML 或 PHP 代码，我们需要使用 `include` 语句。

### 3.2.1 include

假设你希望网站上的多个页面具有相同的 <h1> 标题，你不需要手动将代码复制到所有页面。相反，你可以使用 `include` 语句。让我们尝试一下。在 `htdocs` 中创建一个名为 `heading.html` 的文件，并向其添加以下代码：

```html
<h1>Welcome to PHP</h1>
```

接下来，创建另一个名为 `includedemo.php` 的文件并同样保存到 `htdocs`。在 `includedemo.php` 中添加以下代码：

```php
<!DOCTYPE html>
<html>
<body> <?php include 'heading.html'; ?></body>
</html>
```

注意 `includedemo.php` 中的语句 `include 'heading.html';` 吗？当 PHP 看到此语句时，它会访问 `heading.html`，“复制”内部的代码并自动“粘贴”到 `includedemo.php` 中。这节省了我们自己复制代码的麻烦。如果你现在启动 `includedemo.php`，你将看到“Welcome to PHP”字样作为 <h1> 标题显示。明白了？要使用 include 语句，我们需要给 PHP 我们想要包含的文件路径。这与我们在 HTML 中链接 CSS 或其他外部文件到网页的方式相似。在上面的示例中，由于 `heading.html` 存储在与相同的文件夹内，

对于 `includedemo.php`，我们只需要提供文件名即可。如果 `heading.html` 存储在另一个文件夹（例如在 `htdocs` 下的一个名为“includes”的文件夹中），我们需要使用下面的语句：`include 'includes/heading.html';`

### 3.2.2 require

除了 `include` 语句，PHP 还有 `require` 语句。两者的区别在于，如果 PHP 无法找到所需的文件，`require` 会产生致命错误（fatal error）并停止脚本。相反，`include` 只产生警告而不会停止脚本。如果你想要让 PHP “复制并粘贴”到文件的内容对于页面的正确执行至关重要，你应该使用 `require` 语句。否则，你可以使用 `include` 语句。

### 3.2.3 include_once, require_once

`include` 和 `require` 语句都有对应的 `_once` 版本。正如名称所示，`include_once` 和 `require_once` 语句只会向文件中“复制并粘贴”一次代码。当同一个文件可能被意外包含多次时，这些语句非常有用（例如，当脚本很长，你忘记了之前是否已经包含过该文件）。如果你在 `includedemo.php` 中（在 `?>` 标签之前）添加另一个

```php
include 'heading.html';
```
