
$an_html_string = "<b>This text is bold</b> and <u>This text is underlined</u>";
$new_html_string = preg_replace("/(<\\/?)(\\w+)([^>]*)/e",

strtoupper() 函数应用于表达式第二组圆括号匹配的每个 "\\2"；有关 \\ 引用说明，请参见上一节。结果是，"<" 和 ">" 之间的所有字母数字字符均转换为大写：

"\\1'.strtoupper('\\2').'\\3'", $an_html_string);
//$new_html_string 将包含 "<B>This text is bold</B> and <U>This text is underlined</U>"

反斜杠字符 "\\" 的一种用途是指定通用字符类型；类似地，"[[:alnum:]]" 和相关简写符号用于 POSIX 正则表达式。

下面是 PCRE 通用字符类型列表：

| 快捷方式 | 说明 |
|---|---|
| \d | 匹配任何十进制数字 |
| \D | 匹配任何不是十进制数字的字符 |
| \s | 匹配任何空白字符 |
| \S | 匹配任何不是空白字符的字符 |
| \w | 匹配任何“单词”字符 |
| \W | 匹配任何“非单词”字符 |

反斜杠的另一种用途是用于某些简单的断言。断言指定在匹配的特定点必须满足的条件，而不消耗主字符串中的任何字符。带反斜杠的断言如下：

| 快捷方式 | 说明 |
|---|---|
| \b | 单词边界 |
| \B | 非单词边界 |
| \A | 主字符串开头（与多行模式无关） |
| \Z | 主字符串结尾或末尾的换行符（与多行模式无关） |
| \z | 主字符串结尾（与多行模式无关） |

有关 PCRE、其语法和用途的完整讨论，请访问 http://www.pcre.org/。

## PCRE 相关 PHP 函数

现在让我们看看 PHP 如何处理 PCRE 相关函数。

### preg_match()

```
int preg_match(string pattern, string subject [, array matches])
```

该函数在字符串 subject 中搜索与 pattern 给定的正则表达式匹配的内容。如果提供了可选的第三个参数 matches，则将其填充为搜索结果。$matches[0] 将包含与完整模式匹配的文本，$matches[1] 将包含与第一个捕获的圆括号子模式匹配的文本，以此类推。

### preg_match_all()

```
int preg_match_all(string pattern, string subject,
array matches [, int order])
```

如果在 subject 字符串中找到了与 pattern 匹配的内容，则该函数返回 true；如果未找到匹配或发生错误，则返回 false。

该函数在 subject 中搜索与 pattern 给定的正则表达式的所有匹配项，并按 order 指定的顺序将它们放入 matches 中。找到第一个匹配项后，后续搜索将从上一个匹配项的末尾继续。order 可以是以下两者之一：

- PREG_PATTERN_ORDER
  此顺序使 $matches[0] 成为完整模式匹配的数组，$matches[1] 成为由第一个圆括号子模式匹配的字符串数组，以此类推

- PREG_SET_ORDER
  此顺序使 $matches[0] 成为第一组匹配的数组，$matches[1] 成为第二组匹配的数组，以此类推

如果未指定 order，则假定为 PREG_PATTERN_ORDER。查看以下代码可说明这一点：

```
$html_string = "<b>I am bold</b><a href=getme.html>Get Me</a>";
preg_match_all("/(<([\\w]+)[^>]*>)(.*)(<\\2>/" , $html_string,
$matches, PREG_PATTERN_ORDER);
for ($i=0; $i< count($matches[0]); $i++) {
 echo("matched: ".$matches[0][$i]."\n");
 echo("part 1: ".$matches[1][$i]."\n");
 echo("part 2: ".$matches[3][$i]."\n");
 echo("part 3: ".$matches[4][$i]."\n\n");
}
```

此代码段输出以下内容：

```
matched: <b>I am bold</b>
part 1: <b>
part 2: I am bold
part 3: </b>
matched: <a href=getme.html>Get Me</a>
part 1: <a href=getme.html>
part 2: Get Me
part 3: </a>
```

您需要查看 HTML 源代码，而不是呈现的 HTML 页面。现在如果将 order 更改为 PREG_SET_ORDER，输出如下：

```
matched: <b>I am bold</b>
part 1: <a href=getme.html>Get Me</a>
part 2:
part 3:

matched: <b>
part 1: <a href=getme.html>
part 2:
part 3:

matched: b
part 1: a
part 2:
part 3:

matched: I am bold
part 1: Get Me
part 2:
part 3:

matched: </b>
part 1: </a>
part 2:
part 3:
```

### preg_replace()

```
mixed preg_replace(mixed pattern, mixed replacement,
 mixed subject [, int limit])
```

以下函数在 subject 中搜索与 pattern 匹配的内容，并将其替换为 replacement。

如果指定了 `limit`，则只替换 `limit` 个匹配项；如果省略 `limit` 或为 -1，则替换所有匹配项。`replacement` 字符串可以包含形式为 `\\n` 的反向引用。其工作方式与函数 `ereg_replace()` 说明的完全相同。如前所述，如果 `pattern` 包含圆括号子字符串，则 `replacement` 可以包含形式为 `\\n` 的子字符串，它们将由与第 n 个圆括号子字符串匹配的文本替换。`\\0` 将生成字符串的全部内容。最多可使用九个子字符串。圆括号可以嵌套，在这种情况下，按左圆括号计数。

preg_replace() 的每个参数都可以是数组。如果 subject 是数组，则对 subject 的每个条目执行搜索和替换，返回值也是数组。如果 pattern 和 replacement 都是数组，则 preg_replace() 从每个数组中取一个值并用于对 subject 执行搜索和替换。如果 replacement 的值少于 pattern，则其余 replacement 值使用空字符串。如果 pattern 是数组而 replacement 是字符串，则此 replacement 字符串用于 pattern 的每个值。不过，反之则不然。

我们之前已经看到过从文本块中剥离 HTML 标签的示例，那么如何使用单次 preg_replace() 调用从同一代码块中剥离任何 JavaScript 或 VBScript 呢？具体操作如下：

```
<?php

$html_block = "<script language='javascript'>
function jobForm_Validator(f)
{
    if (f.elements[0].value.length < 3) {
        alert('You must type your name and it should be at
        least 3 character long');
        f.elements[0].focus();
        return(false);
    }
}
</script>
<title>Job Application</title>
</head>
<body bgcolor=#FFFFFF>
<h1 align=center>Job Application</h1>
";

// Regex to match script tags
$search = array ("'<script[^>]*>.*?</script>'si",
// Regex to match html tags
"'<[^>]+>'si");

$replace = array("", //Replace with null
""); //Replace with null

$plain_text = preg_replace($search, $replace, $html_block);

echo($plain_text);
?>

```

上面的代码输出：

![](img/9cf7789dba9b16ef3f8576d5aea89186_236_0.png)

您可能会想将 "<script[^>]*>.*.?</script>" 替换为 "<script.>"，但如果您仔细查看，或在修改后尝试该示例，您会发现返回的字符串为空，因为 "<script.*>" 中的 ">" 部分会匹配最后一个 ">" 而非第一个，此外脚本中的 ">" 运算符也会破坏正则表达式。

如前所述，/e 修饰符会使 preg_replace() 在完成相应引用替换后，将 replacement 参数视为 PHP 代码。请确保 replacement 构成有效的 PHP 代码字符串，否则 PHP 将在包含 preg_replace() 的行报告解析错误。

### preg_split()

```
array preg_split(string pattern, string subject [, int limit [, int flags]])
```

该函数返回一个数组，包含 subject 中沿与 pattern 匹配的边界分割的子字符串。如果指定了 limit，则仅返回最多 limit 个子字符串。如果 flags 为 PREG_SPLIT_NO_EMPTY，则仅返回非空片段。

### preg_quote()

```
string preg_quote(string str [, string delimiter])
```

该函数将 str 作为输入，并在每个属于正则表达式语法（. \ + * ? [ ^ ] $ ( ) { } = ! < | :）的字符前加上反斜杠。如果指定了可选的 delimiter，也会对其进行转义。这对于转义 PCRE 函数所需的定界符很有用。

## 摘要

在本章中，我们讨论了几个简单的概念，但这些概念构成了应用程序中用户交互的主要部分。我们讨论的内容包括：

- 获取用户输入
- 处理用户输入
- 以面向对象方式执行上述操作的更好方法
- 正则表达式及其高效用法

