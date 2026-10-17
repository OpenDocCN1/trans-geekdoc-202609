
### PHP 函数

`swap` 函数交换 `$a` 和 `$b` 之间的数字。变量是一个存储位置内存地址，配对有一个关联的符号名称（标识符），它包含一个被称为“值”的已知或未知数量。在开始时，这两个变量被初始化。我们调用 `swap()` 函数。该函数接收 `$a` 和 `$b` 作为参数。

```
$a = 4;
$b = 7;
```

在 `swap()` 函数内部，我们更改了值。注意，`$a` 和 `$b` 变量是局部定义的。它们只在 `swap()` 函数内部有效。

```bash
$ php swap1.php

outside swap function:

$a is 4

$b is 7

inside swap function:

$a is 7

$b is 4

outside swap function:

$a is 4

$b is 7
```

输出显示原始变量没有受到影响。接下来的代码通过引用将值传递给函数。原始变量在 `swap()` 函数内部发生了变化。

```php
swap2.php
<?php
function swap(&$a, &$b) {
    $temp = $a;
    $a = $b;
    $b = $temp;
    echo "Inside swap function:\n";
    echo "\$a is $a \n";
    echo "\$b is $b \n";
    $a = 4;
    $b = 7;
    echo "outside swap function:\n";
    echo "\$a is $a \n";
    echo "\$b is $b \n";
    swap(&$a, &$b);
    echo "outside swap function:\n";
    echo "\$a is $a \n";
    echo "\$b is $b \n";
}
?>
```

该示例与上一个几乎完全相同，除了取地址符号 `&`。

```bash
$ php swap2.php

outside swap function:

$a is 4

$b is 7

inside swap function:

$a is 7

$b is 4

outside swap function:

$a is 4

$b is 7
```

在这里我们看到 `swap()` 函数确实改变了变量的值。

#### 3.1.9 PHP 递归

递归在数学和计算机科学中是一种定义函数的方法，其中被定义的函数被应用于自身的定义域内。换句话说，递归函数通过调用自己来完成工作。递归是迭代的替代方案。递归是函数式语言中的主要方法。

非负整数的阶乘表示为 `n!`，是所有小于 `n` 的正整数的乘积。

一个典型的例子是计算阶乘。

```php
recursion.php
<?php
function factorial($n) {
    if ($n==0) {
        return 1;
    } else {
        return $n * factorial($n - 1);
    }
}
echo factorial(4), "\n";
echo factorial(10), "\n";
?>
```

在这个代码示例中，我们计算数字的阶乘。在 `factorial` 函数体内部，我们通过参数调用自身。

```bash
$ recursion.php
24
3628800
```

这些是结果。

![](img/f8aa82c4ef45031ca4eadc2bb946c87_93.png)

那么定义函数的语法是什么样的？这里有一个简单的示例：

```php
<?php
function addNumbers($num1, $num2) {
    $result = $num1 + $num2;
    return $result;
}
```

#### 3.1.10 PHP 全局和局部变量

接下来我们将讨论变量的作用域。作用域是变量可以引用的范围。当我们处理函数时，有两个基本作用域：全局作用域和局部作用域。局部作用域也被称为函数作用域。

`scope1.php`

```php
<?php
$value = 1;
function simple() {
    var_dump($value);
}
simple();
?>
```

在函数体外部定义的变量在函数内部无法被引用。

```bash
$ php scope1.php
PHP Notice: Undefined variable: value in /home/janbodnar/prog/php/functions/scope1.php on line 7
NULL
```

`$value` 变量在 `simple()` 函数中为 NULL。

`scope2.php`

```php
<?php
$value = 4;
function simple() {
    $value = 3;
    echo $value, "\n";
}
simple();
echo $value, "\n";
```

在这个示例中，我们有两个同名的变量。它们由于存在于不同的作用域而不会冲突。

```bash
$ php scope2.php
3
4
```

值在函数内部是 3，在函数外部是 4。在下一个示例中，我们将修改函数内部的一个值。

`scope3.php`

```php
<?php
$value = 1;
function simple() {
    global $value;
    $value = 2;
}
echo $value, "\n";
simple();
echo $value, "\n";
?>
```

我们使用 `global` 关键字来引用函数体外部定义的变量。

```bash
$ php scope3.php
1
2
```

`$value` 在 `simple()` 函数内部被成功修改了。
在 PHP 教程的这一部分，我们涵盖了 PHP 函数。

### 3.2 CPU 使用率信息

我们将利用 `getrusage()` 函数。请记住，该函数在 Windows 平台上不可用。

```php
print_r(getrusage());
/* prints
Array
(
    [ru_oublock] => 0
    [ru_inblock] => 0
    [ru_msgsnd] => 2
    [ru_msgrcv] => 3
    [ru_maxrss] => 12692
    [ru_ixrss] => 764
    [ru_idrss] => 3864
    [ru_minflt] => 94
    [ru_majflt] => 0
    [ru_nsignals] => 1
    [ru_nvcsw] => 67
    [ru_nivcsw] => 4
    [ru_nswap] => 0
    [ru_utime.tv_use] => 0
    [ru_utime.tv_sec] => 0
    [ru_stime.tv_use] => 6269
    [ru_stime.tv_sec] => 0
)
*/
```

除非你已经有系统管理背景，否则这些看起来有些神秘。以下是每个值的解释（你不需要记忆这些内容）：

- `ru_oublock`: 块输出操作
- `ru_inblock`: 块输入操作
- `ru_msgsnd`: 发送的消息数
- `ru_msgrcv`: 接收的消息
- `ru_maxrss`: 最大驻留集大小
- `ru_ixrss`: 整数共享内存大小
- `ru_idrss`: 整数不共享数据大小
- `ru_minflt`: 页面回收
- `ru_majflt`: 页面缺页
- `ru_nsigals`: 接收的信号
- `ru_nvcsw`: 自愿性上下文切换
- `ru_nivcsw`: 非自愿上下文切换
- `ru_nswap`: 交换（swaps）
- `ru_utime,tv_use`: 用户时间（微秒）
- `ru_utime.tv_sec`: 用户时间（秒）
- `ru_stime,tv_use`: 使用的系统时间（微秒）
- `ru_stime.tv_sec`: 使用的系统时间（秒）

微秒是时间的一个 SI 单位，等于百万分之一（0.000001）或 `$10^{-6}$` 秒。要查看脚本消耗了多少 CPU 功率，我们需要查看“用户时间”和“系统时间”值。默认情况下秒和微秒部分分开提供。你可以将微秒除以 100 万，并加到秒上，即可得到小数形式的总秒数。

让我们来看一个例子：

```php
// 睡眠 3 秒（非忙碌）
sleep(3);
```

```php
$data = getrusage();
echo "User time: ".
($data['ru_utime.tv_sec'] +
$data['ru_utime.tv_use'] / 1000000);
echo "System time: ".
($data['ru_stime.tv_sec'] +
$data['ru_stime.tv_use'] / 1000000);
```

```php
/* prints
User time: 0.011552
System time: 0
*/
```

尽管脚本运行了大约 3 秒，但 CPU 使用率非常低。因为在睡眠操作期间，脚本实际上并没有消耗 CPU 资源。许多其他任务可能会消耗实际时间，但可能不会 CPU 时间，例如等待磁盘操作。所以如你看到的，CPU 使用率和实际运行长度并不总是一致的。

这是另一个例子：
```php
// 循环 1000 万次（忙碌）
for(i=0;$i<10000000;$i++) {
}
```

```php
$data = getrusage();
echo "User time: ".
($data['ru_utime.tv_sec'] +
$data['ru_utime.tv_use'] / 1000000);
echo "System time: ".
($data['ru_stime.tv_sec'] +
$data['ru_stime.tv_use'] / 1000000);
```

```php
/* prints
User time: 1.4245992
System time: 0.004204
*/
```

这消耗了大约 1.4 秒的 CPU 时间，几乎所有都是用户时间，因为没有系统调用。

系统时间是 CPU 代替程序内核执行系统调用花费的时间。以下是该示例：

```php
$start = microtime(true);
// 持续调用 microtime 大约3秒
while(microtime(true) - $start < 3) {
}
```

```php
$data = getrusage();
echo "User time: " .
($data['ru_utime.tv_sec'] + $data['ru_utime.tv_use'] / 1000000);
echo "System time: " .
($data['ru_stime.tv_sec'] + $data['ru_stime.tv_use'] / 1000000);
```

```php
/* prints
User time: 1.08817
System time: 1.67535
*/
```

现在你看到，由于存在系统调用，系统时间占了很大比例。

## 知识检查

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
   ```php
   <?php
   function calc($price, $tax)
   {
      $total = $price + $tax;
   }
   $pricetag = 15;
   $taxtag = 3;
   calc($pricetag, $taxtag);
   ?>
   ```
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
- 2. 编写一个将数组传递给函数的程序。
- 3. 编写一个通过引用传递函数参数的程序。
- 4. 编写一个在函数中使用默认参数的程序。
- 5. 编写一个使用非标量类型作为默认值的程序。

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

## PHP：字符串 (STRING)

> “弦理论将能量和物质描述为微小的、振动的能量线，它们看起来就像弦。弦的振动频率决定了其效应的本质。”
> Roy H. Williams

### 学习目标

学习本章后，你将能够：

- 定义 PHP 字符串函数的基础
- 了解 PHP 中解析（parsing）的使用

## 基础计算机编程：PHP

### 引言

字符串是字符序列，其中字符等同于字节。这意味着 PHP 仅支持 256 个字符的集合，因此不提供原生的 Unicode 支持。

字符串是编程中的一种数据类型，类似于整数和浮点单元，但用于表示文本而不是数字。它由一组字符组成，也可以包含空格和数字。例如，单词“hamburger”和句子“I ate 3 hamburgers”都是字符串。即使“12345”也可以是一个字符串。

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
