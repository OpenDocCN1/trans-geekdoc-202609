

测试在以下环境中进行：

- **CGI Perl 脚本**
  一两年前编码网站和应用程序的传统方式
- **FastCGI Perl 脚本**
  一种改进 CGI 脚本性能问题的机制
- **Python CGI 脚本**
  在这种情况下，我们使用 Python 编写 CGI 脚本
- **mod_python Python 脚本**
  一个 Apache 模块，让 Apache 无需调用 Python 解释器即可运行 Python 代码
- **C CGI 脚本**
  作为 CGI 程序运行的编译 C 脚本
- **mod_perl Perl 脚本**
  一个 Apache 模块，让 Apache 无需执行 Perl 解释器即可运行 Perl 脚本
- **PHP**
  为了将其他语言与 PHP 进行比较，相同的测试也在 PHP 上运行

经过多次基准测试，涉及不同的脚本类型和服务器负载，发现 mod_perl、FastCGI 和 PHP 是速度最快的选项，结果非常相似。因此，如果 PHP 网站或脚本面临性能问题，解决方案是优化代码而不是更改语言。

## 基准测试

测试 1 – 对一个非常短的脚本执行 1000 次：

| 语言 | 时间（秒） |
|---|---|
| C | 20.6 |
| Perl | 23.8 |
| Python | 45.2 |
| PHP | 16.0 |
| mod_python | 30.0 |
| mod_perl | 16.4 |
| FastCGI | 16.4 |

测试 2 – 对一个长脚本执行 1000 次，代码行数超过 1000 行：

| 语言 | 时间（秒） |
|---|---|
| C | 258 |
| Perl | 963 |
| Python | 978 |
| PHP | 304 |
| mod_python | 347 |
| mod_perl | 476 |
| FastCGI | 280 |

## 优化 PHP 代码

程序员提到**预优化**任务，例如："我会将这个向量改为哈希表以提高性能" 或 "我会将这个 `ereg()` 函数改为几个 `str_replace()` 函数，它们会更快"。他们非常错误。

首先，这类修改通常只能使脚本性能提升不到 0.01 秒，因此并不重要，而且可能会大大降低代码可读性。其次，预优化是浪费宝贵编程时间的最常见方式。

只有在确定确实需要优化时，优化才是良好的实践。我们需要一种提升性能的方法，专业的做法是：

- [ ] 分析代码以查找瓶颈
- [ ] 分类瓶颈
- [ ] 攻击瓶颈以优化代码

## 代码分析

一旦检测到性能问题，第一项任务应该是构建代码分析，其中我们测量脚本用于多个任务和函数的时间量。然后，我们可以利用这些信息找到脚本花费大部分时间的地方。这些有问题的函数称为**瓶颈**。

分析之后，我们可能会发现许多令人惊讶的情况，例如脚本在数据库查询上花费了 99% 的时间，或者其他非常重要的瓶颈，例如读取大文件或日志的磁盘 I/O。如果没有良好的分析工作，优化就不是一项严肃的编程技术。

## 如何分析 PHP 脚本

要为 PHP 脚本制作分析，我们需要在脚本的多个函数和任务周围放置计时器，以测量函数执行所需的时间。

假设我们有以下 PHP 脚本：

```
<?php
// Some initializations
require_once("some_class.php");

$foo = new some_class();

$res1 = $foo->do_a_method();
$res2 = $foo->do_a_method2();

echo($res1);
echo($res2);
?>
```

如果我们在该脚本上遇到性能问题，有三个嫌疑对象——第一个嫌疑对象是在创建 $foo 对象时调用的 some_class() 构造函数。

第二个和第三个嫌疑对象是被调用的两个方法。因此，如果我们知道脚本执行需要 2.3 秒，我们想找出这段时间在三个嫌疑对象之间是如何分配的。

第四个次要嫌疑对象可能是 require_once() 调用所用的时间，如果通过 some_class() 包含了太多文件。出于本章的目的，我们假设 require_once() 调用只占用脚本使用的 2.3 秒中的很少一部分。

PHP 有一个 time() 函数，返回自 1970 年以来的秒数。然而，这几乎无用，因为许多脚本的执行时间不到一秒，而在执行需要几秒的脚本中，我们需要比这更精确的精度来找到时间花在哪里。我们必须使用的函数是 microtime()。

## microtime() 函数

microtime() 返回格式为 "msec sec" 的字符串，其中 msec 是微秒部分，sec 是自 1970 年以来的秒数，例如：

```
<?php
echo(microtime());
?>
```

这可能返回：

0.15672253 987612546

在尝试计算差异时，这对我们来说不太有用，因此我们必须按以下方式操纵结果：

```
<?php
$time_portions = explode( ' ', microtime() );
$actual_time = $time_portions[1] . substr($time_portions[0], 1);
echo($actual_time);
?>
```

使用该代码，我们将：

0.15672253 987612546

转换为：

987612546.15672253

现在，我们需要在执行函数或代码段之前和之后获取该数字，并计算差值。bcsub() 函数用于以足够精度获取差值，如下所示：

```
<?php
$elapsed_time = bcsub($end_time, $start_time, 6);
?>
```

> 要测试此脚本，bcmath 扩展应使用 --enable-bc-math 选项编译到 PHP 中。

此处 6 是我们希望在结果中保留的小数位数。

## 构建计时器类

如果我们已经有适用于 PHP 的分析器工具，则不需要计时器类。

该类维护多个计时器。基本函数为：

- timerStart()
  让我们启动一个新计时器，或者将其作为默认计时器。要启动一个命名计时器，我们使用 timer_start( 'foo' )。

- timerStop()
  停止给定的计时器或默认计时器，如果未给出名称。它返回计时器的经过时间。

```
<?php
class Timer
{
	var $Timers = array();

	function Timer()
	{
		// Nothing
	}
}
```

```php
function timerStart($name = 'default')
{
    $time_portions = explode(' ', microtime());
    $actual_time = $time_portions[1] . substr($time_portions[0], 1);
    $this->timers[$name] = $actual_time;
}

function timerStop($name = 'default')
{
    $time_portions = explode(' ', microtime());
    $actual_time = $time_portions[1] . substr($time_portions[0], 1);
    $elapsed_time = bcsub($actual_time, $this->timers[$name], 6);
    return $elapsed_time;
}
?>
```

Timer 类使用 bcsub() 函数将一个数字减去另一个数字，以确保扩展精度算术。

如果您看到错误消息 undefined function bcsub......，则表示您没有将 bcmath 函数编译到 PHP 中。将 -enable-bcmath 添加到您的配置字符串，重新编译 PHP，然后重试。

> 这里我们了解了计时器类的基本工作原理。另一个计时器类作为 PEAR 的一部分，可在 PHP 安装的 pear/Benchmark/Timer.php 文件中找到。PEAR 类更完整、更复杂。

编写另一个 Time_Info 类，用于显示执行 phpinfo() 函数和 multiply() 函数（该函数用于乘以大数）所用的时间：

```php
<?php
// This test class displays the time taken in executing a function
// containing phpinfo() and another function multiplying a large number.
class Time_Info
{
    // Constructor
    function Time_Info()
    {
        // Method 1: containing the builtin function phpinfo()
        function phpinf()
        {
            phpinfo();
        }

        // Method 2: multiplying large numbers
        function multiply()
        {
            $multiplied=10000*10000*10000*10000;
        }
    }
}
?>
```

现在，让我们基于上述示例编写一个高级脚本。在这里，我们将每个嫌疑对象放在 timerStart() 和 timerStop() 调用之间，以测量每个嫌疑对象所用的时间：

```
<?php
// Some initializations
require_once("Timer.php");
require_once("Time_Info.php");

$tim = new Timer();
$tim->timerStart('total');

$tim->timerStart();
$foo = new Time_Info();
print("Constructor: " . $tim->timerStop() . "<br>");

$tim->timerStart();
$res1 = $foo->phpinf();
print("Method1: " . $tim->timerStop() . "<br>");

$tim->timerStart();
$res2 = $foo->multiply();
print("Method2: " . $tim->timerStop() . "<br>");

echo($res1);
echo($res2);

print("Total execution time: " . $tim->timerStop('total') . "<br>");
?>
```

让我们检查构造函数、phpinf() 和 multiply() 所用的时间，以及脚本的总运行时间。

Constructor: 0.000084
Method1: 0.037100
Method2: 0.000101
Total execution time: 0.037980

通过多次运行此测试，我们可以找到确定哪个函数应进行优化所需的所有信息。因此，我们为有问题的脚本构建了一个分析。

## 分类瓶颈

分析用于查找瓶颈，一旦找到瓶颈，就应根据多个因素对其进行分类。首先，应衡量每个瓶颈的严重性。其次，估计优化每个瓶颈的复杂度。

考虑这些因素将决定脚本中哪些函数、代码部分或方法应进行优化。

