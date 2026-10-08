

# PHP 核心编程

![](img/58e6a0f5d6a8a41d4645d8c07b3bf1e3_550_0.png)

```php
<?php
/*
 ** SessionID
 ** generates a session id
 */
function getSessionID($length=16)
{
    // Set pool of possible characters
    $Pool = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    $Pool .= "abcdefghijklmnopqrstuvwxyz";
    $lastChar = strlen($Pool) - 1;

    for($i = 0; $i < $length; $i++)
    {
        $sid .= $Pool[mt_rand(0, $lastChar)];
    }
    return($sid);
}

// Seed the generator
mt_rand(100000000 * (double)microtime());

if($sid != "")
{
    print("Old Session ID was $sid<BR>\n");
}

$sid = getSessionID();

print("< HREF=\"PHP_SELF?id=$sid\">");
print("Get Another Session ID");
print("</A>\n");
?>
?>

IT-SC 书 550

# 列表 15.12 随机横幅广告

```php
<?php
//Seed the generator
mt_srand(doubleval(microtime()) * 1000000000);

//choose banner
switch(mt_rand(1
```

# 第 16 章：解析与字符串评估

## 分词化 (Tokenizing)

正则表达式

定义正则表达式

在 PHP 脚本中使用正则表达式

解析是将一个整体拆分为若干组件的行为，通常是指将一个句子拆分为单词。PHP 在将脚本转换为 HTML 文档的第一步中，必须解析你编写的代码。在未来，会有一个时刻，你将面对提取或验证字符串中收集的数据的情况。这可能只是简单的制表符分隔列表，也可能是复杂的浏览器用于向 Web 服务器标识身份的字符串。你可以选择对字符串进行分词，将其拆分成碎片；你也可以选择应用正则表达式。本章将介绍 PHP 用于解析和字符串评估的函数。

## 分词化

PHP 允许使用简单的模型对字符串分词。你选择的某些字符被视为分隔符。分隔符之间的字符序列被视为标记（tokens）。在每次从字符串中提取标记时，你都可以更改分隔符集合，这对于不规则的字符串——即不是简单的逗号分隔列表的字符串非常方便。

列表 16.1 接受一个句子并使用第 9 章“数据函数”中描述的 `strtok` 函数将其拆分为单词。对于脚本而言，单词被空格、标点符号或句子的结尾包围。单引号和双引号保留作为单词的一部分。

列表 16.1 字符串分词

# PHP 核心编程

### 列表 16.1 - Microsoft Internet Explorer

| 文件 | 编辑 | 查看 | 背景 | 工具 | 帮助 |
|---|---|---|---|---|---|
| 提交的文本：When in the Course of human events, it becomes necessary for one to dissolve the political bands which have connected them with another, and to assume the powers of the earth, the separate and equal station to which the Laws of Nature and of Nature's God entitle them, a decent respect to the opinions of mankind requires that they should declare the causes which impel them to the separation. | | | | | |

### 找到 71 个单词

- the (9)
- of (5)
- to (5)
- and (3)
- them (3)

* 完成

```php
<?php
/*
 * 如果提交了句子，则解析它 */
if (isset($sentence)) {
    print("<B>Submitted text:</B>");
    print("$sentence<BR><BR>\n");
}

// add end marker
$sentence .= "<END>";

// set characters that separate tokens
$separators = " .,!?";

// get each token
for ($token = strtok($sentence, $separators); $token != "<END>"; $token = strtok($separators)) {
    // skip empty tokens
    if ($token != "") {
        // count each word
        $word_count[strtolower($token)]++;
    }
}
// 起始按单词排序
ksort($word_count);
// 接着按频率排序
arsort($word_count);

print("<B>total Words Found</B>\n");
print("<ul>");
foreach ($word_count as $key => $value) {
    print("<li>$key ($value)</li>");
}
print("</ul>");
?>
```

# PHP 核心编程

注意变量中添加的 `<END>`。这个特殊标记允许算法检测输入的结束。当 `strtok` 遇到输入结束时，它会返回 `FALSE`，因此你的第一直觉可能是在 `for` 循环中测试 `FALSE`。如果两个分隔符连续出现，`strtok` 将如你所料那样返回一个空字符串。由于我们不想停止分词，因此我们在末尾放置一个我们知道输入中不存在的标记。在字符串中，我们可以先将其剥离，但这超出了本文的范畴，而且它不是会被意外输入的内容。由于没有过早分词的风险，我更倾向于让它产生无效结果。`strtok` 函数仅适用于简单的情况。一个例子可能是读取一个制表符分隔的文件，使用制表符从行中填充每个标记，并继续获取下一行。

# 正则表达式

幸运的是，PHP 提供了比 `strtok` 更强大的工具：正则表达式。正则表达式使用自己的语言编写，描述了与字符串进行比较的模式。PHP 源代码包含了符合 POSIX 标准的正则表达式实现。这允许使用旧式的表达式，但与 PHP 原生表达式相比具有现代优势。它们使得复制表达式变得更容易。学习更多正则表达式的极佳资源是官方文档 <http://www.perl.com/CPAN/doc/manual/perl.html>。你需要阅读 Perl 和 PHP 实现之间的差异 <http://www.php.net/manual/pcre.php>。

# 定义正则表达式

在最高层，正则表达式是由竖线 (`|`) 分隔的一个或多个分支。该字符被认为具有逻辑“或”的属性。任何分支都可能与评估后的字符串匹配。表 16-1 提供了几个示例。每个分支包含一个或多个原子。这些原子后面可能会跟着修改原子匹配次数的字符。表 16-2。星号 (`*`) 意味着原子可以匹配任意次数。加号 (`+`) 意味着原子至少匹配一次。问号 (`?`) 表示原子可能匹配一次或完全不匹配。

或者，原子可以是限定的，这意味着它后面跟着大括号 `{}`，如果大括号内包含单个数字，则原子必须精确匹配该次数。如果括号内包含一个数字后跟着逗号，则原子必须匹配该次数或更多。如果括号内包含两个用逗号分隔的数字，则原子必须至少匹配第一个数字次数，但不能超过第二个数字。

原子是一系列具有特殊含义的字符，而其他字符仅代表可能匹配的字符。点 (`.`) 匹配任何字符。美元符号 (`$`) 匹配字符串末尾。如果你需要匹配特殊字符 `^ [ ] | *?` 之一，请在前面加上反斜杠。任何被反斜杠之前的字符将被视为字面量，即使它没有特殊含义。任何没有特殊含义的字符将被视为仅待匹配的字符，无论是否有反斜杠。你还可以用括号将原子分组，使其被视为一个原子。

## 表 16-1. 正正则表达式中的分支

| 示例 | 描述 |
|---|---|
| apple | 匹配单词 apple。 |
| apple|ball | 匹配 apple 或 ball。 |
| begin|end|break | 匹配 begin、end 或 break。 |

## 表 16-2. 正则表达式中的模式重复

| 示例 | 描述 |
|---|---|
| a(b*) | 匹配 a, ab, abb, ... — 一个 a 加上任意次数的 b。 |
| a(b+) | 匹配 ab, abb, abbb, ... — 一个 a 加上一个或多个 b。 |
| a(b?) | 匹配 a 或 ab — 一个 a 可能跟着一个 b。 |
| a(b3) | 仅匹配 abbb。 |
| a(b,2) | 匹配 abb, abbb, abbbb, ... — 一个 a 后面两个或多个 b。 |
| a(b,4) | 匹配 abb, abbb, abbbb, abbb — 一个 a 后面二到四个 b。 |

