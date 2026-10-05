

# 知识检查

- 1. 下列哪种是 PHP 中定义函数的正确方法？
   a. function {function body}
   b. data type functionName(parameters) {function body}
   c. functionName(parameters) {function body}
   d. function functionName(parameters) {function body}

- 2. 类型提示（Type Hinting）是在 PHP 的哪个版本引入的？
   a. PHP 4
   b. PHP 5
   c. PHP 5.3
   d. PHP 6

- 3. 此函数调用中会发生什么？
   <?php
function calc($price, $tax)
{
   $total = $price + $tax;
}
$pricetag = 15;
$taxtag = 3;
calc($pricetag, $taxtag);
?>
   a. 值传递
   b. 引用传递
   c. 默认参数值
   d. 类型提示 

## 基础计算机编程：PHP

4. 下面 PHP 代码的输出是什么？

```php
<?php
function calc($price, $tax="")
{
  $total = $price + ($price * $tax);
  echo "$total";
}
calc(42);
?>
```

   a. 错误
   b. 0
   c. 42
   d. 84

5. 下列哪些是有效的函数名？

- i) function ()
- ii) €($)
- iii) $function ()
- iv) $function ()

   a. 仅 ii)
   b. 以上提到的没有。
   c. 以上提到的都是。
   d. iii) 和 iv)

## 复习题

- 1. 编写一个程序在 PHP 中创建一个自定义函数。
2. 编写一个将数组传递给函数的程序。
3. 编写一个通过引用传递函数参数的程序。
4. 编写一个在函数中使用默认参数的程序。
5. 编写一个使用非标量类型作为默认值的程序。

## 检查你的结果

- 1. (d) 2. (b) 3. (a) 4. (c) 5. (a)

## 参考文献

- 1. Head First PHP & MySQL – Lynn Beighley & Michael Morrison
- 2. http://zetcode.com/lang/php/functions/
- 3. Learn PHP & MySQL – Zero to Hero Programming Course – Paul Madoff
- 4. Learning PHP, MySQL, JavaScript, and CSS: A Step-by-Step Guide to Creating Dynamic Websites – Robin Nixon
- 5. PHP & MySQL Novice to Ninja – Kevin Yank
- 6. PHP & MySQL Web Development – Luke Welling & Laura Thompson
- 7. PHP & MySQL: The Missing Manual – Brett McLaughlin
- 8. The Joy of PHP Programming: A Beginner’s Guide – Alan Forbes

```php
$query = http_build_query($query)
} else {
$query = $sqs;
$queryString = $components['query'];
} elseif ($query) {
$queryString = http_build_query($query, '', '&');
}
$server['REQUEST_URI'] = $components['path'].($query ? '?'.$query : '');
$server['QUERY_STRING'] = $queryString;

return self::createRequestFromFactory($query, $request, $n
```

# 第 4 章

# PHP：字符串 (STRING)

> “弦理论将能量和物质描述为微小的、振动的能量线，它们看起来就像弦。弦的振动频率决定了其效应的本质。”
> Roy H. Williams

## 学习目标

学习本章后，你将能够：

- 定义 PHP 字符串函数的基础
- 了解 PHP 中解析（parsing）的使用

## 基础计算机编程：PHP

### 引言

字符串是字符序列，其中字符等同于字节。这意味着 PHP 仅支持 256 个字符的集合，因此不提供原生的 Unicode 支持。

字符串是编程中的一种数据类型，类似于整数和浮点单元，但用于表示文本而不是数字。它由一组字符组成，也可以包含空格和数字。例如，单词“hamburger”和句子“I ate 3 hamburgers”都是字符串。即使“12345”也可以是一个字符串。（注：提供的 OCR 文本在中间部分包含严重的乱码/重复错误；根据标准 PHP 文档，以下是重构的字符串定义逻辑流）。

字符串字面量可以通过四种方式指定：
- 单引号
- 双引号
- Heredoc 语法
- Nowdoc 语法（自 PHP 5.3 起）

#### 4.1.1 单引号

指定字符串最简单的方法是使用单引号（'）将其括起来。要指定一个字面量反斜杠，请将其写两次（\\）。所有其他反斜杠实例都将被视为字面量反斜杠：这意味着你可能使用的其他转义序列（如 \n）将以字面形式输出，而不是具有任何特殊含义。与双引号和 heredoc 语法不同，变量和特殊字符的转义序列出现在单引号字符串时不会被解析。

```php
<?php
echo 'this is a simple string';
echo 'You can also have embedded newlines instrings this way as it is';

// 输出: Arnold once said: "I'll be back"
echo 'I\'ll be back';
```

#### 4.1.2 双引号

如果字符串被双引号（""）括，PHP 将解释以下特殊字符的转义序列：

| 转义字符 | 含义 |
| --- | --- |
| \n | 换行符 (LF 或 ASCII 中的 0x0A) |
| \r | 回车符 (CR 或 ASCII 中的 0x0D) |
| \t | 水平表符 (HT 或 ASCII 中的 0x09) |
| \v | 垂直制表符 (VT 或 ASCII 中的 0x0B）（自 PHP 5.2.5 起） |
| \$ | 美元符号 ($) |
| " | 单双引号 (") |
| \\ | 反斜杠 (\) |

