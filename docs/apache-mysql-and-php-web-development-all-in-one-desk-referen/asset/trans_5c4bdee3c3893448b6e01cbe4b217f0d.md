
```
}
</pre>
Please review it carefully and check for errors.

Thanks!
</body>
</html>
```

当您在浏览器中打开此 HTML 时，您将看到：

您的代码是：

```
#include
int main() {
    cout << "Perseus of Andromeda" << endl;
    return 0;
}
```

请仔细检查并纠正错误。
谢谢！

## 从字符串中转义

当您使用双引号样式的字符串或 heredoc 样式的字符串（但不是单引号样式的字符串）时，可以在字符串中嵌入各种转义序列，这些序列表示原本难以放入字符串的专用信息。PHP 只包含其中几种转义序列，如下列表所述：

- \n 这是表示换行的常见方式。有关使用 \n 的一些说明，请参见本列表后的段落。
- \t 这是一个制表符字符。
- \r 这是换行的另一种方式，称为回车。有关使用 \r 的一些说明，请参见本列表后的段落。
- \\ 这只是一个老式的反斜杠。因为反斜杠表示特殊字符，这使您实际上可以指定反斜杠本身！
- \" 这是一个双引号。在 heredoc 字符串中，您不需要在其前使用反斜杠，但在双引号字符串中，您需要反斜杠，以便 PHP 处理器不会认为字符串在此处结束。
- \$ 因为变量以美元符号开头，这为您提供了一种在字符串中表示实际美元符号的方法。

现在来看那些关于换行和回车的说明。您应该使用 \r 还是 \n？大多数人使用 \n。然而，无需深入细节，只需知道 Windows 计算机使用 \r 后跟 \n 的组合来表示换行，而 Unix 和 Linux 计算机仅使用 \n。Macintosh 仅使用 \r。您自己琢磨吧。但事实是，浏览器并不在乎，因为它们将所有空白（包括换行）视为单个空格。所以我总是使用 \n。

## 嵌入变量（同时打印它们）

如果您使用 heredoc 样式字符串或双引号样式字符串，可以使用一种很酷的技术将变量直接嵌入字符串。为什么要这样做？请看下面的代码：

```php
<?php
 $myname = "me";
 print "Hello, $myname! It's a fine name and my name
 too!";
 ?>
```

此代码生成以下 HTML：

Hello, me! 这是个好名字，也是我的名字！

此输出就像您先打印了 "Hello,"，然后打印存储在 $myname 中的值，然后打印 "! It's a fine name and my name too!" 一样。

PHP 处理器并不总是确切知道变量名在哪里结束，这会导致混淆。请看下面两行：

```php
$word = "apple";
print "$words are my favorite food";
```

PHP 处理器不知道您在字符串中尝试使用的变量是 $word。相反，它会查找名为 $words 的变量。要修复此问题，可以使用大括号将变量名括起来，如下所示：

```php
$word = "apple";
print "{$word}s are my favorite food";
```

或者您可以将美元符号放在大括号外，仅将名称本身括在大括号中，如 ${word}。

## 连接和拼合字符串

连接是计算机界以外的人似乎都不知道的一个词，而计算机界内的每个人在了解其含义后，几乎每天都会使用这种技术。如果您是连接的新手，可以肯定会在每天早上喝完咖啡后开始使用它。

## 是连接还是嵌入？

此时，您可能会想，在编写字符串和变量时哪种选择更好。假设 $a 包含字符串 "Hello"，$b 包含字符串 "there"。现在看看下面两行代码：

```
print $a."<br>".$b;
print "$a<br>$b";
```

这两行代码产生相同的输出。哪一个更好？这完全取决于您。就个人而言，大多数人觉得第二个版本更易于输入和理解。但是，请记住，当您使用数组和对象时，如果计划使用嵌入式格式，必须用大括号将变量名括起来，以免 PHP 处理器混淆。（有关数组的更多信息，请参见第 V 册，第 5 章；有关对象，请参见第 V 册，第 7 章。）下面是一个示例；请注意，在最后一行中，我在字符串内的变量周围加上了大括号（和括号）。

```
class MyClass {
 var $name;
}
$obj = new MyClass();
$obj->name = array("George",
"Washington");
print "{$obj->name[0]}<br>{$obj->name[1]}";
```

此代码生成以下 HTML 输出：
George<br>Washington

连接只是将两个字符串拼合成一个大字符串。在 PHP 中连接字符串，可以使用 .（点）运算符，如下面的示例所示：

```
$a = "php is ";
$b = "great";
$c = "as everybody knows";
print $a.$b."<br>".$c;
```

这将生成以下 HTML：

```
php is great<br>as everybody knows
```

当在浏览器中打开此 HTML 时，它看起来是这样的：

```
php is great
as everybody knows
```

如您所见，在我的字符串中包含一个 <br> HTML 标签，该标签在浏览器屏幕上输出一个换行。

## 第 4 章：控制程序流程

### 本章内容

- 使用 if 语句
- 使用 while 循环
- 查看 for 循环
- 检查 switch 语句
- 中断和继续循环
- 使用循环构建 HTML 表格

编程语言的一个重要特性是在程序中跳转，而不仅仅是逐行执行语句。早期的脚本语言缺少 while 循环和 for 循环等控制结构。但是，随着时间的推移，程序员们认识到即使在脚本语言中，控制结构也很重要。因此，PHP 包括常见的各种控制结构：if 语句、while 循环、for 循环以及 case 或 switch 语句。我将在本章中讨论这些控制结构。

如果您熟悉 C++ 或本书中涵盖的语言（例如 Perl），您会发现许多 PHP 控制结构与 C++ 中的相似。了解这一点将节省您探索这些控制结构的时间。但是，PHP 确实存在一些差异；例如，PHP 具有 elseif 关键字。

### 使用 if 语句进行比较

控制结构的最简单形式是 if 语句。if 语句允许基于比较更改程序的流程：如果比较结果为 true，则执行一个代码块；如果比较结果为 false，则执行另一个代码块。

以下是 PHP 中 if 语句的示例：

```
<html><title>Car System</title>
<body>
<?php
$CarIsBrokenDown = true;
if ($CarIsBrokenDown) {
print ("Click here for the bus schedule");
}
?>
</body>
</html>
```

前面的示例是一个完整的 .php 文件，其中包含一个检查 $CarIsBrokenDown 是否为 true 的 if 语句。请注意，我使用了表达式的最简单形式：一个布尔变量。我只是使用了变量名 $CarIsBrokenDown。如果此表达式计算结果为 true（换句话说，如果 $CarIsBrokenDown 包含 true），则 PHP 处理器执行大括号内的代码。

考虑到我立即将变量设置为 true 然后测试它是否为 true，这个 if 语句本身并不十分有用。以下是一个更具威力的示例：

```
<html><title>Expired Hot Dogs</title>
<body>
<h2>Welcome to the hot dog web page!
Let's see if they're still good...</h2>
<?php
$today = getdate();
$todayastime = mktime($today);
print "Today is {$today['weekday']}, {$today['month']} {$today['mday']}, {$today['year']}.<br>\n";
$expiration = mktime(0, 0, 0, 12, 31, 2003);
$expstring = date("F j, Y", $expiration);
if ($todayastime == $expiration) {
print "They expire, like, NOW, so you better
hurry!<br>";
}
elseif ($todayastime > $expiration) {
print "They expired on $expstring. Better not risk
it.<br>";
}
else {
print "They're perfectly good! Enjoy!<br>";
}
?>
</body>
</html>
