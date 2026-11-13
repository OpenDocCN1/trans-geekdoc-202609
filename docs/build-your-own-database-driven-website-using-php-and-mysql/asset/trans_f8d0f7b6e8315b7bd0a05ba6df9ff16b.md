

## 正则表达式

要实现我们自己的标记语言，我们需要一个脚本来识别笑话文本中的自定义标签，并将它们替换为相应的 HTML 等价物，然后再将笑话文本输出到用户的浏览器。任何有正则表达式经验的人都知道，它们非常适合这类工作。

正则表达式是包含特殊代码的文本字符串，这些代码允许它与几个 PHP 函数一起用于搜索和操作其他文本字符串。例如，这是一个搜索文本 "PHP"（不含引号）的正则表达式：

PHP

没什么复杂的，对吧？要使用正则表达式，你必须熟悉 PHP 中可用的正则表达式函数。ereg 是最基本的，可用于确定特定文本字符串是否满足正则表达式。请考虑以下代码：

```
$text = "PHP rules!";

if (ereg("PHP", $text)) {
  echo( '$text contains the string "PHP".' );
} else {
  echo( '$text does not contain the string "PHP".' );
}
```

在这个示例中，正则表达式被满足，因为变量 $text 中存储的字符串包含 "PHP"。因此，上述代码将输出以下内容（请注意，单引号防止 PHP 填充变量 $text 的值）：

$text contains the string "PHP".

eregi 是一个与 ereg 行为几乎相同的函数，区别在于它在查找匹配项时忽略文本的大小写：

```
$text = "What is Php?";

if (eregi("PHP", $text)) {
  echo( '$text contains the string "PHP".' );
} else {
  echo( '$text does not contain the string "PHP".' );
}
```

同样，这将输出相同的消息，尽管该字符串实际上包含 "Php"：

$text contains the string "PHP".

如前所述，正则表达式中可以使用一些特殊代码。其中一些非常令人困惑且难以记住，因此如果你打算广泛使用它们，一份好的参考资料可能会很有用。标准正则表达式语法的教程式参考可在 http://www.delorie.com/gnu/docs/rx/rx_toc.html 找到。让我们通过几个示例来学习基本的正则表达式语法。

首先，插入符号 (^) 可用于指示字符串的开头，而美元符号 ($) 可用于指示字符串的结尾：

```
PHP // Matches "PHP rules!" and "what is PHP?"
^PHP // Matches "PHP rules!" but not "What is PHP?"
PHP$ // Matches "I love PHP" but not "What is PHP?"
^PHP$ // Matches "PHP" but nothing else
```

显然，你有时可能希望使用 ^、$ 或其他特殊字符来表示搜索字符串中的相应字符，而不是正则表达式语法所暗示的特殊含义。要删除字符的特殊含义，请在其前加上反斜杠：

```
\$\$\$$ // Matches "Show me the $$$!" but not "$10"
```

方括号可用于定义可能匹配的字符集。例如，以下正则表达式将匹配任何包含 1 到 5（含）之间数字的字符串。

```
[12345] // Matches "1" and "39", but not "a" or "76"
```

也可以指定数字和字母的范围。

```
[1-5] // Same as previous
^[a-z]$ // Matches any single lowercase letter
[0-9a-zA-Z] // Matches any string with a letter or number
```

字符 ?、+ 和 * 也具有特殊含义。具体来说，? 表示“前一个字符是可选的”，+ 表示“一个或多个前一个字符”，* 表示“零个或多个前一个字符”。

```
bana?na // Matches "banana" and "banna",
     // but not "banaana".
bana+na // Matches "banana" and "banaana",
     // but not "banna".
bana*na // Matches "banna", "banana", and "banaaana",
     // but not "bhna".
^[a-zA-Z]+$ // Matches any string of one or more
     // letters and nothing else.
```

括号可用于将字符串分组，以便将 ?、+ 或 * 应用于整个分组。

```
ba(na)+na // Matches "banana" and "banananana",
     // but not "bana" or "banaana".
```

以下是正则表达式中匹配特殊字符的几个代码：

```
\n   // Matches a newline character
.   // Matches any character except a newline
\r   // Matches a carriage return character
\t   // Matches a tab character
```

正则表达式还有更多特殊代码和语法技巧，任何参考资料（如上面提到的）都应该涵盖所有这些内容。目前，我们已有足够多的内容来满足我们的目的。

### 使用正则表达式进行字符串替换

使用我们刚刚学习的正则表达式语法配合 ereg 或 eregi，可以轻松检测给定文本字符串中是否存在标签。然而，我们需要做的是定位这些标签，并将它们替换为相应的 HTML 标签。为此，我们需要了解 PHP 提供的另外几个正则表达式函数：ereg_replace 和 eregi_replace。

ereg_replace 与 ereg 类似，接受一个正则表达式和一个文本字符串，并尝试在字符串中匹配正则表达式。此外，ereg_replace 还接受第二个文本字符串，并将正则表达式的每个匹配项替换为该字符串。

ereg_replace 的语法如下：

```
$newstr = ereg_replace(regexp, replacewith, oldstr);
```

在这里，regexp 是正则表达式，replacewith 是将替换 oldstr 中 regexp 匹配项的字符串。该函数返回替换操作产生的新字符串。在上述代码中，这个新生成的字符串存储在 $newstr 中。

如你所料，eregi_replace 与 ereg_replace 相同，区别在于查找匹配项时不考虑字母的大小写。

我们现在准备好构建我们的自定义标记语言了。

### 加粗和斜体文本

让我们从实现创建加粗和斜体文本的标签开始。假设我们希望 [B] 开始加粗文本，[EB] 结束加粗文本。显然，我们必须将 [B] 替换为 <b>，将 [EB] 替换为 </b>。实现这一点是 eregi_replace 的简单应用：

```
$joketext = eregi_replace("\[[b]\]", "<b>", $joketext);
$joketext = eregi_replace("\[[eb]\]", "</b>", $joketext);
```

请注意，因为 [ 通常表示正则表达式中可接受字符集的开始，所以我们在其前加上反斜杠以删除其特殊含义。如果没有匹配的 [，则 ] 失去其特殊含义，因此不需要反斜杠，尽管如果你想要周全，也可以在其前加上反斜杠。

还要注意，由于我们使用的是不区分大小写的 eregi_replace，因此 [B] 和 [b] 都将在我们的自定义标记语言中作为标签工作。

斜体文本也可以以同样的方式实现：

```
$joketext = eregi_replace("\\[i\]", "<i>", $joketext);
$joketext = eregi_replace("\\[ei\]", "</i>", $joketext);
```

### 段落

虽然我们可以像上面为加粗和斜体文本创建标签一样为段落创建标签，但更简单的方法更有意义。由于用户将在允许他们使用回车键格式化文本的表单字段中输入内容，我们将把单个换行符 (\n) 作为换行符 (<br />)，双换行符 (\n\n) 作为新段落 (</p><p>)。当然，因为 PC 将新行表示为换行符-回车符对 (\n\r)，我们必须先去除回车符。实现这一切的代码如下：

```
// Strip out carriage returns
$joketext = eregi_replace("\\r","",$joketext);
// Handle paragraphs
$joketext = ereg_replace("\\n\\n","</p><p>",$joketext);
// Handle line breaks
$joketext = ereg_replace("\\n","<br />",$joketext);
```

就是这样！文本现在将以用户期望的段落形式出现，而用户无需学习任何自定义标签来格式化他们的内容。

### 超链接

虽然在笑话文本中支持超链接包含似乎有些愚蠢，但此功能在其他应用程序中很有意义。超链接比将固定代码片段简单转换为 HTML 标签要复杂一些。我们需要能够输出 URL，以及应作为链接出现的文本。

ereg_replace 和 eregi_replace 的另一个功能在此发挥作用。如果用括号括起来正则表达式的一部分，你可以捕获匹配文本的相应部分，并在替换字符串中使用它。为此，你将使用代码 \n，其中 n 是正则表达式中第一个带括号的部分的 1，第二个的 2，一直到第九个的 9。请考虑以下示例：

