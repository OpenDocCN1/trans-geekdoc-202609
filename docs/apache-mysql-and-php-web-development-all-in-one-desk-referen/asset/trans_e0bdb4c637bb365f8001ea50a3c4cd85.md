

## 将字符串拆分为单个字符

如果你需要获取一个字符串，并创建一个由该字符串中单个字符组成的数组，可以使用 split 函数。为此，你需要为正则表达式使用一个空模式。以下是 Perl 示例：

```perl
$string = "abcdefghijklmnopqrstuvwxyz";
@chars = split(//, $string);
foreach (@chars) {
    print "$_\n";
}
```

正则表达式就是 //，但斜杠是分隔符，这意味着表达式本身是空的：完全没有表达式。

以下是 PHP 中的相同示例：

```php
<?php
$string = "abcdefghijklmnopqrstuvwxyz";
$chars = preg_split("//", $string);
foreach ($chars as $char) {
    print "$char\n";
}
?>
```

最后，以下是在 Tcl 中实现相同功能的方法：

```tcl
package require textutil
set str { abcdefghijklmnopqrstuvwxyz }
set chars [::textutil::splitx $str {}]
foreach char $chars {
    puts $char
}
```

## 拆分时进行捕获

拆分字符串时，还可以在正则表达式中包含括号以捕获文本。但是，仅仅添加括号不会自动导致各种 split 函数捕获文本。相反，你需要添加一个选项。

在 PHP 中，你将 PREG_SPLIT_DELIM_CAPTURE 选项作为第四个参数添加到 preg_split 函数中。（如果你要组合多个选项，请使用竖线字符分隔选项，就像我在以下示例中所做的那样。）以下是一个简短的演示：

```php
<?php
$str = "Hi there, everybody! This is cool.";
$result = preg_split('/(\W+)/', $str,
-1, PREG_SPLIT_NO_EMPTY |
PREG_SPLIT_DELIM_CAPTURE);
foreach ($result as $word) {
    print "word--$word--\n";
}
?>
```

这将拆分 $str 字符串，并在过程中捕获模式。请注意，我在 \W+ 周围加上了括号。因此，你得到的结果是整个字符串被拆分开：模式中指定的分隔符分隔的文本，以及分隔符本身。请记住，该模式是单词边界，包括通常的标点字符。因此，使用 PREG_SPLIT_DELIM_CAPTURE 时，你的最终列表中也会包含标点字符。（你可能想这样做，以防你想将句子重新连接起来，同时保留所有标点。）

我在 print 语句中在 $word 两边放了两个连字符，以便你可以看到输出中的任何空格。以下是输出：

```
word--Hi--
word-- --
word--there--
word--, --
word--everybody--
word--! --
word--This--
word-- --
word--is--
word-- --
word--cool--
word--. --
```

第一行输出是拆分出的单词之一。第二行输出是紧跟在第一个单词后面的分隔符；这个分隔符只是一个空格。向下移动到第四行，你可以看到在这种情况下分隔符是两个字符，一个逗号，然后是一个空格。（你可以看到逗号和两个连字符之间的空格。）

在 Perl 中，你不需要添加任何额外选项；你只需加入括号，戏就开始了。以下是用 Perl 编写的相同程序；它的输出与之前相同：

```perl
$str = "Hi there, everybody! This is cool.";
@result = split(/(\W+)/, $str);
foreach (@result) {
    print "word--$_--\n";
}
```

## 与乐队一起连接

拆分的逆操作是 *join*。在执行拆分并将所有单词放入数组中后（或者如果你只是创建了一个充满单词的数组），你可以轻松地使用 join 函数将它们重新拼接在一起。

使用 join 函数时不需要正则表达式。相反，你只需指定在将单词重新拉回字符串时用于单词之间的字符或字符串。

以下是 Perl 示例：

```perl
$paragraph =
    "I am bill at at dot com. I ate my kitchen, ".
    "and this is gr e. All th I know school is ".
    "all my brain.";

@words = split(/\W+/, $paragraph);
$final = join('@', @words);
print "$final\n";
```

此示例按单词拆分 `$paragraph` 字符串，然后将所有单词重新拼接在一起，在每个单词之间插入 `@` 字符。以下是充满秘密含义的输出：

```
I@am@bill@at@at@dot@com@I@ate@my@kitchen@and
@this@is@gr@e@All@th@I@know@school@is@all@my@brain
```

PHP 中的 join 同样简单；你使用标题有些吓人的 implode 函数：

```php
<?php
$paragraph =
    "I am bill at at dot com. I ate my kitchen, ".
    "and this is gr e. All th I know school is ".
    "all my brain.";

$words = preg_split('/\W+/', $paragraph);
$final = implode('@', $words);
print "$final\n";
?>
```

join（或 implode，如果你更喜欢更戏剧化的语言）的一个问题是，你总是被迫在单词之间插入相同的字符串，不管你拆分的原始字符串中包含什么。但是，如果你使用捕获方法同时抓取分隔符（请参阅本章前面的“拆分时进行捕获”部分），你可以在拼接单词时使用它们，如以下 Perl 程序所示：

```perl
$paragraph =
"I am bill at at dot com. I ate my kitchen, ".
"and this is gr e. All th I know school is ".
"all my brain.";
@words = split(/(\W+)/, $paragraph);
$final = join('', @words);
print "$final\n";
```

我在模式周围添加了括号，以在数组中捕获分隔符。此外，我在 join 函数中指定了空字符作为分隔符，因为我想重新压缩在一起的所有内容都在数组本身中。

运行此示例时，你会看到与 $paragraph 开头相同的字符串。

![](img/3f967ab8a8fddc723173059f56621648_695_0.png)

要在 PHP 中使用捕获的分隔符实现连接，你仍可以像以前一样使用 implode 函数。只需在 preg_split 函数中使用 PREG_SPLIT_DELIM_CAPTURE 选项捕获分隔符，然后调用 implode，为分隔符字符传递一个空字符串。

## 第 6 章：处理多行和文件

### 本章内容

- 处理文件中的每一行
- 将字符串作为单行或多行处理
- 确定文件中有多少行
- 搜索文件中的所有行
- 在搜索和替换中修改多个换行符

有一个想法：假设你不是在字符串中搜索模式，而是想在文件中搜索模式。你会遇到什么样的问题？

在回答之前，我需要设定一些假设：

- **你正在处理文本文件。** 正则表达式用于匹配文本，因此包含例如编译后 C++ 代码的文件是二进制数据，试图使用一个复杂的正则表达式来拆解编译代码根本行不通。换句话说，除了文本文件之外，对任何类型的文件使用正则表达式都没有意义。

- **你的文本文件被组织成文本行。** 也就是说，如果你在文本编辑器中打开文件，你会看到多行，而不是一行很长的线。一行很长的线几乎与单个字符串没有区别。

但是，如果你只有一行很长的线，并在文本编辑器中选择了自动换行选项怎么办？大多数文本编辑器都有此选项。在这种情况下，从技术上讲，你仍然只有一行文本。

当你打开自动换行功能时，你会得到文本段落，每个段落虽然在屏幕上显示为多行，但实际上是一行很长的文本。我怎么知道这一点？答案是我下一个假设：

- **每行文本以一个或两个行尾字符结尾。** 我说“一个或两个”是因为不同的操作系统使用不同的方式来表示行尾。Unix 使用单个换行符字符，其 ASCII 码为 10。Windows 使用两个字符，回车符后跟换行符，其 ASCII 码分别为 13 和 10。最后，Macintosh 也不甘示弱，仅使用回车符（ASCII 码为 13）来结束其行。在编写代码时，你可能在字符串中见过 \r 或 \n 或 \r\n。\r 指的是回车符，即 ASCII 码 13。\n 指的是换行符，即 ASCII 码 10。因此，\r\n 生成 ASCII 码 13 然后是 10。

为了本次讨论的目的，我说“换行”或“换行字符”来指代你的操作系统所使用的任何行尾字符（或两个字符）。

![](img/3f967ab8a8fddc723173059f56621648_696_0.png)

## 处理多行字符串

为什么要区分多行字符串和单行字符串？这一切都取决于你希望正则表达式引擎如何解释三个神奇的字符 ^、$ 和 .（点号）。默认情况下，这两个字符分别表示字符串的开头和结尾，而点号字符匹配除换行符外的任何字符。但是，如果切换到多行模式，^ 和 $ 突然表示行的开头和结尾。在多行模式下，正则表达式引擎会监视换行符，并按每行基础匹配 ^ 和 $。你还可以指定专门的单行模式，在这种情况下，点号匹配包括换行符在内的所有字符。（通常，正如我所述，点号字符不匹配换行符。）

以下是一个很好的例子。为了说明我的观点，我将把几行文本塞进一个字符串中。以下是 Perl 代码：

```perl
$a = "Don't eat my computer \nyet. cook it first.\n";
print $a;
print "=========\n";
$a =~ s/^(.*)(c.*)$/$1$2/mg;
print $a;
```

仔细看一下字符串。我在里面放了几个 \n 字符；因此，当你运行此代码时，首先你会看到原始字符串打印在多行上。为了帮助组织输出，我在单独一行上放了一堆等号，以将原始字符串与修改后的字符串分开。

仔细看一下正则表达式。记住，像往常一样，将这些东西拆解开来看。正则表达式以 s 开头，表示搜索和替换，末尾是 g 修饰符，表示搜索和替换将尽可能多次发生。但是，请注意，我在表达式的闭合斜杠后还放了一个 m。（他们称 m 为 m 修饰符。）这就是将搜索和替换神奇地转换为多行格式的关键。

搜索模式以 ^ 开头，在本例中表示行的开头。接下来是 (.*)、一个 c，然后是另一个 (.*。这将搜索最后

