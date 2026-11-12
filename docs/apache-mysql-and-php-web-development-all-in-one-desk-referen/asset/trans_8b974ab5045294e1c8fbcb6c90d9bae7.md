
这段奇怪的代码在您的浏览器中会产生以下输出：

```
1000000
-1000000
```

之所以会得到这个结果，是因为当您对字符串执行数值运算（例如减去 1000000）时，PHP 处理器会将该字符串视为数值 0。因此，0 减去 1000000 等于 -1000000，这正是您在输出中看到的结果。

## 使用字符串处理字符

字符串是字符序列。PHP 的一大优点（尤其是如果您来自 C 编程世界）是其对字符串的支持。在接下来的章节中，我将为您提供大量关于字符串及其操作方法的有趣信息。

### 指定字符串

PHP 允许您以三种不同的方式指定字符串：

- 使用单引号
- 使用双引号
- 使用称为 heredoc 的格式

每种方法的结果略有不同。以下各部分将提供详细信息。

### 使用引号指定

首先，您可以将字符串用单引号包围，如下所示：

```
print 'Where did all the time go?<BR>';
```

或者您可以用双引号包围它，如下所示：

```
print "Where did all the time go?<BR>";
```

这两行代码的结果相同；不过，这两种方法略有不同。您可能注意到，在本小书中，我将某些字符串嵌入了 \n，这称为转义字符。这个特定的转义字符表示换行。现在，为了说明单引号和双引号指定字符串方法之间的区别，请尝试在前面两行代码的末尾各添加一个 \n，后面再跟几个字符：

```
print 'Where did all the time go?<BR>\n...';
print "Where did all the time go?<BR>\n...";
```

这两行代码看起来相似，但在生成的 HTML 中会产生不同的输出。运行这两行代码会产生以下输出：

```
Where did all the time go?<BR>\n...Where did all the time
go?<BR>
...
```

看到了发生了什么吗？单引号内的 \n 导致输出中出现了字面字符 \n。但是，双引号导致 PHP 处理器将 \n 转换为换行符。

如果您计划在字符串中使用转义字符，或者计划嵌入变量（本章后面“嵌入变量 [以及打印它们]”部分中有描述），则必须使用双引号。这些字符和变量将被正确转换。但是，如果您希望文本原样打印——包括反斜杠、美元符号等——则请使用单引号。

您正一帆风顺，度过美好的一天，突然遇到一个重大错误，发现 Web 浏览器中出现了一堆 \n。问题很可能是您不小心使用了单引号，而本应使用双引号。我是说，嗯，出于经验。（没错。）

如果您运营的网站访问量很大，并且正在寻找尽可能多的方法来最大化速度，那么除非需要在字符串中嵌入转义序列或变量，否则请始终使用单引号风格的字符串。PHP 处理器处理单引号字符串比处理双引号字符串稍快一些。

### 使用 heredoc 指定

如果您来自传统编程语言（如 C++ 或 Pascal）的视角，第三种指定字符串的方法可能看起来有点奇怪。您可以使用一种称为 heredoc 的字符串指定方法。heredoc 的理念是，您在代码文件中输入字符串行应该呈现的确切样子。下面是一个示例：

```
<?php
$tome =
<<<EOT
Well hello there, everybody! I'm your speaker here at the
PHP for Life conference, where you'll be immersed in all
the PHP you can handle now and in subsequent lives.
Let us all hold hands and recite the PHP mantra.
EOT;
print "<p>";
print $tome;
print "</p>";
?>
```

下面是我创建字符串的方法：我写了一行没有缩进的行，以三个小于号（<）开头，后跟我选择的标识符。我选择了 EOT（在我疯狂的脑子里，这要么代表 End of Text，要么代表 Eat Only Truffles，取决于我的心情）。字符串从下一行的开头开始。（如果您缩进，缩进将成为字符串的一部分！）为了标记字符串的结束，我重复我选择的标识符，在本例中是 EOT。而且，因为这是一个变量赋值，就像所有变量赋值一样，我以分号结束。

这将生成以下 HTML：

```
<p>Well hello there, everybody! I'm your speaker here at the
PHP for Life conference, where you'll be immersed in all
the PHP you can handle now and in subsequent lives.
Let us all hold hands and recite the PHP mantra.</p>
```

您可以使用任何想要的标识符来启动 heredoc 字符串，前提是该标识符遵循与有效 PHP 变量相同的规则（以字母开头，可以包含数字和下划线），并且在 heredoc 字符串的末尾使用相同的标识符。如果您想将标识符命名为 HEREDOC，那没问题。或者，如果您更喜欢更个人化、更贴近内心的标识符，比如 PIZZA 或 ANDROMEDAGALAXY，那也很好。不过，我确实鼓励您保持一致，在所有代码中使用相同的标识符。哦，对了，您不必全用大写字母，尽管我鼓励您这样做，因为这有助于标识符突出显示。

结束字符串的行必须仅由您选择的标识符和分号（如果语句需要分号）组成。如果您在该行上放入任何其他内容，PHP 处理器会假设该行不是结束标识符，处理器会继续逐行处理，使那个庞大的字符串变得更长。这是一个错误，您的程序将无法正确运行。另外，请确保在结束标识符后面不放置任何内容（请记住，它必须位于最左列），后面可以跟一个分号（如果需要）。

虽然我在前面的 heredoc 示例中没有展示，但 heredoc 字符串与双引号字符串具有相同的功能，即您可以嵌入转义序列和变量名。下面是一个示例：

```
<?php
$name = "Perseus Harold Pock (but call me PHP)";
$tome2 = <<<EOT
Greetings, Earthlings! I am $name.
\tIt is my pleasure to welcome you to my own galaxy,
\t\t\t\t the Andromeda galaxy. I own it.
EOT;

        print "<p>";
        print $tome2;
        print "</p>";
?>
```

heredoc 字符串的第一行包含变量 $name，PHP 处理器会将其替换为 $name 的值。字符串的第二行和第三行以 \t 开头，这是制表符的转义字符。因此，当您运行此程序时，生成的 HTML 包含：

```
<p>Greetings, Earthlings! I am Perseus Harold Pock (but call me PHP).
   It is my pleasure to welcome you to my own galaxy,
   the Andromeda galaxy. I own it.</p>
```

heredoc 方法还有一个特别有用的应用。如果您在 HTML 中使用 <pre> 标签，heredoc 就很方便。<pre> 标签的常见用途是在浏览器中显示程序代码。单词 pre 代表预格式化。通过在 HTML 文件中使用预格式化文本，浏览器不会将所有空格视为单个空格，从而不会弄乱输出。前面关于 Perseus Harold Pock 的示例就是这种情况：我的 HTML 制表符（由 PHP 代码中的 \t 产生）和换行符不会出现在浏览器中——它们会被空格替换。

下面是将 heredoc 与 <pre> 标签一起使用的示例：

```
<html><head><title>Your Program</title></head>
<body>
Your code is:<p>
<pre>
<?php
$myname = "Perseus of Andromeda";
$code =
<<<EOT
#include <iostream.h>
int main() {
cout << "$myname" << endl;
return 0;
}
EOT;
print $code;
?>
</pre>
```

Please review it carefully and check for errors.<p> Thanks!
</body>
</html>
```

我将本示例的 PHP 部分加粗，以帮助您将其与其余代码区分开来。PHP 部分之前是一段 HTML 代码，以打开的 <pre> 标签结尾。然后是 PHP，其中包含一个 heredoc 语句，用于输出另一段文本，在此示例中是 C++ 代码。（您不需要懂 C++ 就能理解此示例；我只是想在输出中使用另一种语言。就 PHP 而言，这只是文本。PHP 处理器不会尝试运行 C++ 代码。对 PHP 来说，C++ 垃圾只是一个字符串。）

但是看！在这个字符串中，我嵌入了一个 PHP 变量 $myname。如果您是从数据库读取值到 $myname 变量，而不是像我在这里那样将字符串 Perseus of Andromeda 硬编码，那么您可以大大自定义输出。以下是 PHP 处理器处理代码后最终 HTML 的样子：

```
<html><head><title>Your Program</title></title>
<body>
Your code is:<p>
<pre>
#include <iostream.h>

int main() {
cout << "Perseus of Andromeda" << endl;
return 0;
