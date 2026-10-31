
- 逻辑 `!` 非运算符返回单个操作数的逆布尔值。
- 按位运算符 `|`, `&`, `~`, `^`, `<<` 和 `>>` 允许对整数中的特定位进行求值和操作。
- 前缀变量的递增 `++` 或递减 `--` 运算符将其值更改 1 并返回结果。
- 后缀变量的递增 `++` 或递减 `--` 运算符返回其当前值，然后将其值更改 1。
- 运算符优先级决定表达式如何分组求值。
- 当运算符具有相同优先级时，其结合性决定表达式如何分组求值。
- `var_dump()` 函数可用于查看表达式得到的类型和值。
- 特殊的 `NULL` 常量表示一个完全没有值的变量，甚至不是零。

# 4 测试条件

*本章演示了决定脚本如何进行的各种 PHP 控制结构。*

[寻求真理](#chapter04.xhtml#sec27)
[提供替代方案](#chapter04.xhtml#sec28)
[切换分支](#chapter04.xhtml#sec29)
[匹配表达式](#chapter04.xhtml#sec30)
[执行循环](#chapter04.xhtml#sec31)
[在为真时循环](#chapter04.xhtml#sec32)
[从循环中跳出](#chapter04.xhtml#sec33)
[摘要](#chapter04.xhtml#sec34)

## 寻求真理

![image](images/pg58_1.jpg)

`if` 关键字用于执行基本的条件测试，将给定表达式求值为布尔值 TRUE 或 FALSE。求值后花括号内的语句只有在表达式被判定为 TRUE 时才会被执行。当表达式被判定为 FALSE 时，PHP 解析器会直接跳到脚本的下一部分。

`if` 条件测试语句的语法如下：

```
if ( test-expression ) { statement-to-execute-when-true ; }
```

当测试为 TRUE 时可能有多个语句需要执行，但每个语句都必须以分号结尾：

```
if ( test-expression )
{
statement-to-execute-when-true ;
statement-to-execute-when-true ;
statement-to-execute-when-true ;
}
```

![image](images/hot.jpg)

`if` 结构是 PHP 中最重要的特性之一，也是大多数其他编程语言中的重要特性。

可以使用逻辑 `&&` 或 `and` 运算符测试多个表达式，以确保只有当两个表达式都被判定为 TRUE 时，后续语句才会被执行，如下所示：

```
if ( ( test-expression ) && ( test-expression ) )
{
statement-to-execute-when-true ;
statement-to-execute-when-true ;
statement-to-execute-when-true ;
}
```

另外，`if` 条件测试语句可以嵌套以测试多个表达式，以便只有当所有测试都被判定为 TRUE 时，语句才会被执行，如下所示：

```
if ( test-expression )
{
if ( test-expression )
{
statement-to-execute-when-true ;
statement-to-execute-when-true ;
statement-to-execute-when-true ;
}
}
```

![image](images/hot.jpg)

当要执行的代码只是单个语句时，花括号可以省略，但你可能更喜欢始终包含花括号以保持一致性。

可以使用多个 `if` 条件测试语句为脚本提供替代路径。

![image](images/1p.jpg) 在 PHP 标签之间，使用初始化整数变量的语句开始脚本

```php
<?php
$num = 8 ;
```

![image](images/commonp.jpg)

`if.php`

![image](images/2p.jpg) 接下来，添加在数值大小的条件测试被判定为 TRUE 时输出结果的语句

```php
if ( $num > 5 ) { echo "$num exceeds 5<br>" ; }
if ( $num <= 5 ) { echo "$num is below 6<br>" ; }
```

![image](images/3p.jpg) 现在，添加在奇偶性条件测试被判定为 TRUE 时输出结果的语句

```php
if ( $num % 2 == 0 ) { echo "$num is Even<br>" ; }
if ( $num % 2 != 0 ) { echo "$num is Odd<br>" ; }
?>
```

![image](images/4p.jpg) 将文档保存到你的 Web 服务器的 `/htdocs` 目录下，命名为 `if.php`，然后通过 HTTP 打开页面以查看成功测试的结果

![image](images/pg59_1.jpg)

![image](images/5p.jpg) 编辑整数变量，然后保存修改后的脚本并刷新浏览器以查看其他成功测试的结果

```php
$num = 3 ;
```

![image](images/pg59_2.jpg)

![image](images/forget.jpg)

当测试条件为 FALSE 时，PHP 解析器会忽略其语句块并继续处理。

## 提供替代方案

![image](images/pg60_1.jpg)

通常最好通过附加 `else` 语句来扩展 `if` 语句，指定在 `if` 语句求值的表达式被判定为 FALSE 时执行的花括号内语句，语法如下：

```
if ( test-expression )
{
statement-to-execute-when-true ;
statement-to-execute-when-true ;
statement-to-execute-when-true ;
}
else
{
statement-to-execute-when-false ;
statement-to-execute-when-false ;
statement-to-execute-when-false ;
}
```

在条件测试中也可以通过添加 `elseif` 语句来求值替代表达式，指定在替代表达式被判定为 TRUE 时执行的花括号内语句。这里也可以附加 `else` 语句，以指定在 `if` 和 `elseif` 语句求值的表达式被判定为 FALSE 时执行的花括号内语句，语法如下：

```
if ( test-expression )
{
statement-to-execute-when-true ;
statement-to-execute-when-true ;
statement-to-execute-when-true ;
}
elseif ( test-expression )
{
statement-to-execute-when-true ;
statement-to-execute-when-true ;
statement-to-execute-when-true ;
}
else
{
statement-to-execute-when-false ;
statement-to-execute-when-false ;
statement-to-execute-when-false ;
}
```

![image](images/hot.jpg)

`elseif` 关键字也可以写成两个独立的词：`else if`。

这是一种基本的编程技术，根据求值结果为脚本提供不同的执行方向，被称为“条件分支”。

![image](images/snake.jpg)

你可能会遇到一些使用 `:` 冒号字符而不是花括号的 PHP 脚本。这不推荐，因为只有在使用花括号时，`if` 和 `else if` 才会被视为完全相同。

![image](images/1p.jpg) 在 PHP 标签之间，使用仅在测试表达式为 TRUE 时输出结果的语句开始脚本

```php
<?php
if ( 4 > 2 ) { echo '<p>Yes, 4 is greater than 2 <br>' ; }
```

![image](images/commonp.jpg)

`ifelse.php`

![image](images/2p.jpg) 接下来，添加仅在两个测试表达式都被判定为 TRUE 时输出结果的语句

```php
if ( ( 4 > 2 ) && ( 8 > 4 ) )
{ echo '4 is greater than 2 AND 8 is greater than 4<br>' ; }
```

![image](images/3p.jpg) 现在，添加在测试表达式被判定为 TRUE 或 FALSE 时输出结果的语句

```php
if ( 4 > 8 )
{ echo '4 is greater than 8 <br>' ; }
else
{ echo '4 is less than 8 <br>' ; }
```

![image](images/4p.jpg) 最后，添加在两个测试表达式中任一被判定为 TRUE 或两个测试表达式都被判定为 FALSE 时输出结果的语句

```php
if ( 4 > 8 )
{ echo 'This test is True </p>' ; }
elseif ( 8 > 4 )
{ echo 'Alternative test is True </p>' ; }
else
{ echo 'Both tests are False </p>' ; }
?>
```

![image](images/5p.jpg) 将文档保存到你的 Web 服务器的 `/htdocs` 目录下，命名为 `else.php`，然后通过 HTTP 打开页面以查看条件分支的结果

![image](images/pg61_1.jpg)

![image](images/forget.jpg)

