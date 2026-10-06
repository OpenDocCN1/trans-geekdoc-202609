

## 第二部分：学习语言

## 使用 str_pad() 进行字符串填充

你已经看到过如何使用 `printf()` 在字符串的开头或结尾添加填充。然而，PHP 有一个专门的函数 `str_pad()`，它比 `printf()` 的方法更灵活，也更易操作。

要使用 `str_pad()`，请传递要填充的字符串以及最终字符串所需的宽度。该函数返回使用空格字符（默认情况下）在右侧填充的字符串：

```php
echo '<pre>';
echo str_pad("Hello");
```

如果想使用空格以外的字符，可以传递一个字符串作为可选的第三参数。注意，这可以是单个字符，也可以是一组字符字符串；如果是后者，该字符串将根据需要重复，以填充输出字符串：

```php
// 显示 "Hello, world!*****"
echo str_pad("Hello, world!", 20, "*") . "\n";
```

```php
// 显示 "Hello, world!1231231"
echo str_pad("Hello, world!", 20, "123") . "\n";
```

你还可以让 `str_pad()` 在字符串的左侧填充，或者在字符串的左右两侧都填充。要做到这一点，请传递由内置常量组成的可选第四参数：

- STR_PAD_RIGHT：在字符串右侧填充（默认设置），使字符串左对齐。
- STR_PAD_LEFT：在字符串左侧填充，使字符串右对齐。
- STR_PAD_BOTH：在字符串的左右两侧都填充，尽可能使结果居中。

以下示例在字符串的左右两侧都添加了填充：

## 使用 wordwrap() 对文本进行换行

有时，你需要向用户显示大量文本，例如在网页或电子邮件消息中。如果你的脚本接收到的文本是单行文本——这可能是输入的结果，或者是由于特定数据库中文本格式化的方式——你可能希望将文本拆分成单独的行以便阅读。

PHP 的 `wordwrap()` 函数接收单行文本字符串，并使用换行符 (`"\n"`) 将其拆分成几行，在单词末尾换行以避免拆分单词。要使用它，请传递要换行的字符串，函数将返回换行后的字符串：

## 第5章：字符串

```php
$String = "But think not that this famous town has only harpooners";
```

```php
echo "<pre>";
echo wordwrap($String);
echo "</pre>";
```

这段代码显示了以下输出：

But think not that this famous town has only harpooners, cannibals, bumpkins to show her visitors. Not at all. Still New Bedford is a queer place. Had it not been for us whalemen, tract of land would this day perhaps have been in as howling condition as the cost of Labrador.

默认情况下，`wordwrap()` 使每行长度不超过 75 个字符，但你可以通过传递一个可选参数来更改它：

```php
$String = "But think not that this famous town has only harpooners";
```

```php
echo "<pre>";
echo wordwrap($String, 40);
echo "</pre>";
```

结果如下：

But think not that this famous town has
only harpooners, cannibals, and
bumpkins to show her visitors. Not at
all. Still New Bedford is a queer place.
Had it not been for us whalemen, that
tract of land would this day perhaps
have been in as howling condition as the
cost of Labrador.

如果你更愿意使用不同的字符或字符，可以传递你想要使用的字符作为可选的第三参数。例如，通过使用 HTML 换行符 `<br />` 拆分行，示例脚本只需要将输出封装在 `<pre>...</pre>` 标签中即可：

```php
$String = "But think not that this famous town has only harpooners, cannibals, and bumpkins to show her visitors. Not at all. Still New Bedford is a queer place. Had it not been for us whalemen, tract of land would this day perhaps have been in as howling condition as the cost of Labrador.";
```

```php
echo wordwrap($String, 40, "<br />");
```

## 第二部分：学习语言

顺便一下，如果你想将字符串中的换行符转换为 HTML `<br />` 元素，可以使用 PHP 的 `nl2br()` 函数。它接收一个字符串作为参数，并返回将所有换行符转换为 `<br />` 的字符串。

你还可以向 `wordwrap()` 传递一个可选的第四参数。如果该参数为 true（默认是 false），函数会将字符串换行到指定的宽度，即使这意味着会拆分超过行宽的单词。这里有一个示例：

```php
$myString = "This string has averylongwordindeed.";
echo wordwrap($myString, 10, "<br />");
echo "<br /><br />";
echo wordwrap($myString, 10, "<br />", true);
```

这是这段代码的输出：

This
string has
averylongwordindeed.

This
string has
averylong
ordinded.

## 使用 number_format 格式化数字

PHP 的 `number_format` 函数为你提供了一种易于阅读格式化数字的方法，并将千位分隔符四舍五入到最近的整数。

## 第5章：字符串

PHP 还有另一个实用的函数 `money_format()`，你可以用它根据货币习惯格式化货币值，其语法类似于 `printf()`。唯一的缺点是它在 Windows 平台上不可用（至少在写作期间）。更多详情请参见 http://www.php.net/money_format。

## 总结

在本章中，你探索了 PHP 中的字符串，并查看了 PHP 提供的一些重要的字符串处理函数。你学习了如何在代码中使用单双引号以及 `hered` 和 `nowdoc` 语法创建字符串字面量。你还学习了如何查找字符串长度、字符串中的单词数、访问字符串中的单个字符以及字符串中的字符组。

接着你查看了搜索字符串和替换字符串内文本的函数，包括：

- `strstr()`、`strpos()` 和 `strrpos()` 用于搜索文本
- `substr_count()` 用于统计字符串中搜索项的出现次数
- `strbrk()` 用于搜索一组字符中的任何一个字符
- `str_replace()` 用于替换字符串中搜索项的所有出现处
- `substr_replace()` 用于替换字符串中的某些字符

接下来，你将查看大小写敏感的问题，并探索几个函数 —— `strtolower()`、`strtoupper()`、`ucfirst()`、`lcfirst()` 和 `uwords` —— 你可以使用它们转换大小写。

最后，你学习了 PHP 的 `printf()` 和 `sprintf()` 函数，你可以用多种方式格式化字符串，并了解了一些其他格式化函数，如 `trim()`、`ltrim()`、`rtrim()`、`str_pad()`、`wordwrap()` 和 `number_format()`。

