
# 使用 `strtotime()` 和 `date()` 函数组合

使用 `date()` 函数可以解析不同的英文文本描述为日期：

```php
// Gets the current date
echo date("m/d/Y", strtotime("now")), "\n";
// prints the current date
echo date("m/d/Y", strtotime("10 September 2000")), "\n";
// prints September 10, 2000 in the m/d/Y format
echo date("m/d/Y", strtotime("-1 day")), "\n";
// prints yesterday's date
echo date("m/d/Y", strtotime("+1 week")), "\n";
// prints the result of the current date + a week
echo date("m/d/Y", strtotime("+1 week 2 days 4 hours 2 seconds")), "\n";
// same as the last example but with extra days, hours, and seconds added to it
echo date("m/d/Y", strtotime("next Thursday")), "\n";
// prints next Thursday's date
echo date("m/d/Y", strtotime("last Monday")), "\n";
// prints last Monday's date
echo date("m/d/Y", strtotime("First day of next month")), "\n";
// prints date of first day of next month
echo date("m/d/Y", strtotime("Last day of next month")), "\n";
// prints date of last day of next month
echo date("m/d/Y", strtotime("First day of last month")), "\n";
// prints date of first day of last month
echo date("m/d/Y", strtotime("Last day of last month")), "\n";
// prints date of last day of last month
```

# Section 18.4: 使用预定义常量进行日期格式化

我们可以在 `date()` 中使用预定义的日期格式常量，而不是传统的日期格式字符串（自 PHP 5.1.0 起可用）。

## 可用的预定义日期格式常量

| 常量 | 说明 | 示例 |
| :--- | :--- | :--- |
| `DATE_ATOM` | Atom | 2016-07-22T14:50:01+00:00 |
| `DATE_COOKIE` | HTTP Cookies | Friday, 22-Jul-16 14:50:01 UTC |
| `DATE_RSS` | RSS | Fri, 22 Jul 2016 14:50:01 +0000 |
| `DATE_W3C` | World Wide Web Consortium | 2016-07-22T14:50:01+00:00 |
| `DATE_ISO8601` | ISO-8601 | 2016-07-22T14:50:01+0000 |
| `DATE_RFC822` | RFC 822 | Fri, 22 Jul 16 14:50:01 +0000 |
| `DATE_RFC850` | RFC 850 | Friday, 22-Jul-16 14:50:01 UTC |
| `DATE_RFC1036` | RFC 1036 | Fri, 22 Jul 16 14:50:01 +0000 |
| `DATE_RFC1123` | RFC 1123 | Fri, 22 Jul 2016 14:50:01 +0000 |
| `DATE_RFC2822` | RFC 2822 | Fri, 22 Jul 2016 14:50:01 +0000 |
| `DATE_RFC3339` | Same as `DATE_ATOM` | 2016-07-22T14:50:01+00:00 |

## 使用示例

```php
// 示例代码图片占位符：Image00486.jpg
```

# Chapter 19: 控制结构

## Section 19.1: if else

示例中的 `if` 语句允许在条件满足时执行代码片段。当你想要在条件不满足时执行代码片段时，可以用 `else` 扩展 `if`。

```php
// 示例代码图片占位符：Image00487.jpg
```

参考：[PHP Manual - Control Structures - Else](http://php.net/manual/en/control-structures.else.php)

### 三元运算符作为 if-else 的简写语法

[三元运算符](http://php.net/manual/de/language.operators.comparison.php#language.operators.comparison.ternary) 根据条件是否为真来求值。它是一个比较运算符，常用于以更短的形式表达简单的 if-else 条件。它允许快速测试条件，并经常替换多行的 `if` 语句，使代码更紧凑。

```php
$a = 1;
$b = 2;
```

这是一个使用三元表达式和变量值的示例：

```php
echo ($a > $b) ? "a is greater than b" : "a is NOT greater than b";
```

输出：`a is NOT greater than b`。

## Section 19.2: 控制结构的替代语法

PHP 为某些控制结构提供了替代语法：`if`、`while`、`for`、`foreach` 和 `switch`。

| 结构 | 结束关键字 |
| :--- | :--- |
| `if` | `endif;` |
| `while` | `endwhile;` |
| `for` | `endfor;` |
| `foreach` | `endforeach;` |
| `switch` | `endswitch;` |

与普通语法相比，区别在于左大括号被冒号 (`:`) 替代，右大括号被对应的结束关键字（如 `endif;`）替代。有关单独示例，请参阅控制结构替代语法主题。

```php
// 示例代码图片占位符：Image00489.jpg
```

使用简写语法的多个 `elseif` 语句：

```php
// 示例代码图片占位符：Image00490.jpg
```

参考：[PHP Manual - Control Structures - Alternative Syntax](http://php.net/manual/en/control-structures.alternative-syntax.php)

## Section 19.3: while

`while` 循环会在指定条件为真时重复执行代码块。

```php
// 示例代码图片占位符：Image00491.jpg
```

输出：
```
123456789
```

详细信息请参阅 Loops 主题。

## Section 19.4: do-while

`do-while` 循环首先无条件执行一次代码块，然后在指定条件为真时重复执行该代码块。

```php
// 示例代码图片占位符：Image00492.jpg
```

详细信息请参阅 Loops 主题。

## Section 19.5: goto

`goto` 运算符允许跳转到程序的另一部分。自 PHP 5.3 起可用。

```php
goto MyLabel;
```

`goto` 指令后跟随目标标签。

```php
MyLabel:
```

跳转目标由标签加冒号 (`:`) 指定。

```php
// 示例代码图片占位符：Image00493.jpg
```

此例将输出 `Hello World!`。

## Section 19.6: declare

`declare` 用于为一段代码设置执行指令。

可识别的指令有：

*   [ticks](http://php.net/manual/en/control-structures.declare.php#control-structures.declare.ticks)
*   [encoding](http://php.net/manual/en/control-structures.declare.php#control-structures.declare.encoding)
*   [strict_types](http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration.strict)

例如，设置 ticks 为 1：

```php
// 示例代码图片占位符：Image00494.jpg
```

要启用严格类型模式，请结合 `strict_types` 声明使用 `declare` 语句：

```php
// 示例代码图片占位符：Image00496.jpg
```

## Section 19.7: include & require

### require

`require` 类似于 `include`，不同之处在于失败时会产生致命的 `E_COMPILE_ERROR` 级别错误。`require` 失败会停止脚本执行；`include` 失败仅发出 `E_WARNING` 且不停止脚本。

```php
// 示例代码图片占位符：Image00497.jpg
```

参考：[PHP Manual - Control Structures - Require](http://php.net/manual/en/function.require.php)

### include

```php
// 示例代码图片占位符：Image00498.jpg
```

注意这种方法，因为它被认为是一种 [代码异味](https://en.wikipedia.org/wiki/Code_smell)，因为被包含的文件会改变给定作用域中已定义变量的数量和内容。

你也可以包含返回值的文件。这对于处理配置数组非常有用：

```php
// 示例代码图片占位符：Image00499.jpg
// 示例代码图片占位符：Image00500.jpg
```

这种方法可以防止被包含的文件用改变或新增的变量污染当前作用域。参考：[PHP Manual - Control Structures - Include](http://php.net/manual/en/function.include.php)

`include` 和 `require` 也可用于在文件返回值时将值赋给变量。

示例：`include1.php` 文件：

```php
// 示例代码图片占位符：Image00501.jpg
```

`index.php` 文件：

```php
// 示例代码图片占位符：Image00502.jpg
```

## Section 19.8: return

`return` 语句将程序控制权返回给调用函数。

当在函数内部调用 `return` 时，当前函数的执行将结束。

```php
// 示例代码图片占位符：Image00503.jpg
```

当你运行 `returnEndsFunctions();` 时，输出将为 `This is executed`。

当在函数内部带参数调用 `return` 时，当前函数的执行将结束，并将参数的值返回给调用函数。

## Section 19.9: for

`for` 循环通常用于你有一段想要重复指定次数的代码时。

```php
// 示例代码图片占位符：Image00504.jpg
```

输出：
```
123456789
```
