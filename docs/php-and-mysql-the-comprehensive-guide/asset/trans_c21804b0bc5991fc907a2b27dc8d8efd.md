

![](img/ae7820c36e8f24c1623d26668b28e80e_188_0.png)

### 图 6.19 动态生成函数的输出

### "call_user_func()"

call_user_func(函数名, 参数1, 参数2) 辅助函数用于调用函数。

```php
function difference($a, $b) {
   return $a - $b;
}
echo call_user_func("difference", 5, 2);
```

清单 6.35 "call_user_func()" ("call_user_func.php")

前面的脚本输出正确的结果。call_user_func() 主要用于需要动态生成参数的情况。

此外，还存在 call_user_func_array(函数名, 参数数组)。使用这个辅助函数时，所有参数都存储在数组中，而不是用逗号分隔。

## 6.1.10 PHP 的函数

PHP 的功能主要体现在函数中。因此，PHP 文档中最重要的部分是 _函数参考_。您可以在文档中找到它，也可以直接访问 _http://php.net/manual/funcref.php_。迄今为止介绍的、有助于处理自定义函数的函数，也可以在函数参考中找到（参见图 6.20）。

> **注意**
>
> PHP 函数本身也在不断发展。这里仅举两个例子：自 PHP 5 起，许多扩展已（也）转换为面向对象的操作。然后它们通过对象、方法和属性访问功能。在 PHP 8 中，PHP 自身函数的类型错误处理在某些地方最终被标准化为 TypeError 错误。

![](img/ae7820c36e8f24c1623d26668b28e80e_189_0.png)

### 图 6.20 PHP 函数参考

在文档中，函数在语法上以与实际函数声明相似的风格表示。以下是 htmlspecialchars() 的示例：

```php
htmlspecialchars ( string $string , int $flags = ENT_COMPAT | ENT_HTML401 ,
string $encoding = ini_get("default_charset") , bool $double_encode = true ) :
string
```

首先是函数名。圆括号内跟随参数。每个参数之前都有函数期望的数据类型。mixed 代表任何数据类型。

可选参数，即不一定必须设置的参数，在文档中会列出其各自的默认值。这些值可以是简单值，也可以像本例中那样是常量或函数调用。

最后，有一个表示函数返回的数据类型的缩写。对于 isset()，这是布尔值（bool）。特殊数据类型 void 表示函数没有返回值或不期望任何参数。

> **提示**
>
> 如果您在 php.net/ 后直接输入函数名——例如，php.net/htmlspecialchars——则会直接跳转到相应函数的文档。

## 6.2 语言结构

语言结构不是函数。但是，它们与函数非常相似。您可以通过两种方式区分它们：

- 语言结构可以在没有圆括号的情况下包含参数。因此，`echo "Test";` 和 `echo("Test");` 都是可能的。
- 语言结构不能存储在变量中，也无法访问变量。因此，以下代码会失败（参见图 6.21）：

```php
<?php
$functionname = "echo";
$functionname("test");
?>
```

![](img/ae7820c36e8f24c1623d26668b28e80e_190_0.png)

### 图 6.21 对 "echo()" 函数的调用失败，因为它是语言结构

并且超越这两个始终适用的点之外，语言结构还有一些特殊功能。例如，echo() 可以接受多个参数，如

```php
echo "Hello ", "PHP 8.3";
```

或

```php
echo ("Hello "), ("PHP 8.3");
```

但是，如果参数用圆括号括起来，则会失败（参见图 6.22）：

```php
echo ("Hello ", "PHP 8.3");
```

![](img/ae7820c36e8f24c1623d26668b28e80e_191_0.png)

### 图 6.22 "echo()" 带圆括号会生成语法错误

> **提示**
>
> 最终，您是处理语言结构还是函数并不那么重要。您需要知道相应命令的工作原理以及它期望哪些参数。在本书中，当您探索 Web 开发者的各种任务时，您将认识更多函数以及一些语言结构。

一些语言结构用于输出。其中包括 echo() 和 print()。两者在第 4 章的开头就已介绍。现在您将了解一些变体及其使用频率较低的同事。

## 6.2.1 "heredoc"

对于较长的字符串，PHP 提供了最初来自 Perl 的 heredoc 语法。其工作原理如下：使用 <<< 启动 heredoc 字符串。随后跟随一个唯一名称。在末尾，字符串在新行中用此名称终止。

名称后跟一个分号。例如，您可以将此类字符串保存在变量中，然后根据需要对其进行处理或输出（参见图 6.23）。

5 在 Perl 中，<< 运算符。

```php
<?php
$test = <<<HEREDOC
Content of the heredoc text
spread over several lines
and expanded.
HERE;
echo $test;
?>
```

清单 6.36 "heredoc" 语法 ("heredoc.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_192_0.png)

### 图 6.23 换行符在浏览器中消失了，但在源文本中仍然可见

### 注意

heredoc 字符串的开始和结束必须由拼写相同的同一词组成。请注意，区分大写和小写。

在 PHP 7.2 之前，这个结束名称必须位于行首并后跟分号。名称周围禁止有任何类型的字符和空格。

自 PHP 7.3 起，情况不再如此受限：可以出现空格，并且可以省略分号。然而，也有一些陷阱：首先，仅当其上的字符串内容也缩进时，才允许缩进；其次，名称本身不能是内容的一部分，否则会发生解析器错误。请看下面的示例：

```php
<?php
$test = <<<Content
Content of the heredoc text
spread over several lines
and expanded.
Content;
echo $test;
?>
```

在此示例中，heredoc 名为 Content，该名称出现在字符串的第一行。之后的所有内容都会导致解析器错误（参见图 6.24），因为 PHP 在名称第二次出现后终止字符串。

![](img/ae7820c36e8f24c1623d26668b28e80e_193_0.png)

### 图 6.24 解析器错误：名称已出现在内容中

在 heredoc 字符串中，可以使用双引号字符串中也允许的所有转义序列。变量的值也会插入到字符串中。

## 6.2.2 "nowdoc"

与 heredoc 非常相似的是 nowdoc 语法。唯一的区别是，它不像双引号字符串那样反应，而是像单引号字符串那样反应。这也可以从语法本身中看出。这与 heredoc 完全相同，只是开头的关键字用单引号括起来。

```php
<?php
$test = <<<'NOW'
Content of the nowdoc text
spread over several lines
and expanded.
NOW;
echo $test;
?>
```

清单 6.37 "nowdoc" 语法 ("nowdoc.php")

nowdoc 字符串中不能插入变量，这与单引号相对应。最终进入字符串的所有内容都会直接输出。除此之外，行为没有区别。字符串的结束必须与开始使用相同的关键字指定，但不带引号。同样，必须注意大小写区分。在 PHP 7.2 之前，字符串的结束也必须在单独的行上，没有缩进，并且后面紧跟分号。

## 6.2.3 格式化字符串

使用 printf(默认字符串, 参数)，您输出一个字符串并将其他参数作为占位符传递。占位符由百分号和一个指示要输出的参数数据类型的字母组成。

```php
<?php
$sum = 200;
$format = "%d Euro";
printf($format, $sum);
?>
```

清单 6.38 "printf()" ("printf.php")

前面的脚本生成以下输出：

200 Euro

如果您使用多个参数，可以对占位符编号，以便始终使用正确的参数（参见图 6.25）。

```php
<?php
$sum1 = 200;
$sum2 = 400;
$format = "%2\$d euros are more than %1\$d euros";
printf($format, $sum1, $sum2);
?>
```

清单 6.39 用数字交换占位符 ("printf_multiple.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_194_0.png)

### 图 6.25 第二个参数出现在第一个之前

除了参数位置的数字和转换类型之外，还有其他元素，您可以在百分号后指定。这些元素按顺序为：

