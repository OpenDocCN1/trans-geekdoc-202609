
通过引用传递变量允许函数修改原始变量的值。请看下面的示例：

```
<?php
// File: example13-16.php

function reverseIt(&$strString) {
    $strString = strrev($strString);
}
$strName = "Simon";
echo "<p>$strName ";
reverseIt($strName);
echo "reversed is $strName</p>";
?>
```

上述脚本输出如下：

Simon reversed is nomiS

### 在函数内调用函数

函数可以在自身内部调用其他函数。请看下面的脚本：

```
<?php
// File: example13-17.php
function decimal($floNum) {
    $floNum = round($floNum, 2);
    return $floNum;
}

function multiply($floNumber) {
    $floNumber *= 3.12;
    echo "<p>$floNumber</p>";
    $floNumber = decimal($floNumber);
    echo "<p>$floNumber</p>";
}

$floNumber = 5.2234;
multiply($floNumber);
?>
```

在此脚本中，定义了一个浮点数并将其传递给 multiply() 函数：

```
$floNumber = 5.2234;
multiply($floNumber);
```

该函数将数值乘以3.12，然后显示其当前值：

```
$floNumber *= 3.12;
echo "<p>$floNumber</p>";
```

图13.6 一个函数调用另一个函数的输出

![](img/b2471264f405d17994ef173e4b9cec92_406_0.png)

然后它调用 decimal() 函数，将 $floNumber 的值传递给它，并假定该值会被返回。最后显示该数值：

```
$floNumber = decimal($floNumber);
echo "$floNumber";
```

decimal() 函数接收该变量，并使用预定义函数 round() 将该数值四舍五入到两位小数，然后返回该值：

```
function decimal($floNum) {
    $floNum = round($floNum, 2);
    return $floNum;
}
```

上述脚本的输出如图13.6所示。

### 递归函数

递归函数是指调用自身的函数。递归函数在计算某些类型的数学函数时非常有用。以下示例是一个用于判断一个数是否为2的幂的递归函数：

```
<?php
// File: example13-18.php

function isPowerOfTwo($intNumber) {
    if ($intNumber == 1)
        return "<p>yes</p>";
    elseif ($intNumber%2 == 1)
        return "<p>no</p>";
    else {
        $intNumber /= 2;
        return isPowerOfTwo($intNumber);
    }
}

echo isPowerOfTwo(256) ;
?>
```

在此示例中，通过将数字256传递给 isPowerOfTwo() 函数来检查它是否为2的幂：

```
echo isPowerOfTwo(256) ;
```

当函数被调用时，一个if语句会检查该数字是否等于1。如果是，则显示'yes'。如果不是，则使用另一个if语句检查 $intNumber 的当前值除以2的余数是否等于1。如果此条件成立，则显示'no'：

```
if ($intNumber == 1)
    return "<p>yes</p>";
elseif ($intNumber%2 == 1)
    return "<p>no</p>";
```

如果该数字不满足这两个条件中的任何一个，则将其除以2，函数调用自身（通过使用return关键字），并重复此过程：

```
$intNumber /= 2;
return isPowerOfTwo($intNumber);
```

在此示例中，生成的输出为：

yes

## 13.2 拆分源文件

函数允许我们将代码划分为易于管理的部分；然而，另一种划分代码的方式是将一个大型的PHP脚本拆分成多个较小的脚本。这样可以使您更容易地共享和重用脚本的各个部分。

请看下面的脚本：

```
<?php
// File: example13-19.php

function temperatureConvert($floTemp, $strType = "C") {
    if ($strType == "F") {
        $floCelsius = (5/9)*($floTemp-32);
        echo "<p>$floTemp<sup>o</sup>F = 
            $floCelsius<sup>o</sup>C</p>";
    }
    else {
        $floFahrenheit = (9/5)*$floTemp+32;
        echo "<p>$floTemp<sup>o</sup>C = 
            $floFahrenheit<sup>o</sup>F</p>";
    }
}
?>
```

上述脚本只是前面示例中的 temperatureConvert() 函数。现在再看：

```
<?php
// File: example13-20.php

include_once ("example13-19.php");

echo "<h2>Some nice holiday temperatures:</h2>";
for($intCount=25;$intCount<40;$intCount++)
    temperatureConvert($intCount);
?>
```

上述脚本使用 'include_once' 语句在指定位置包含 'example13-19.php' 脚本的一个副本。该脚本的输出与图13.4所示相同。

> **注意** 'include' 和 'include_once' 之间的区别在于，即使被要求再次包含该文件，'include_once' 也只会包含该文件一次。

'require' 和 'require_once' 语句的工作方式与 'include' 和 'include_once' 语句完全相同。唯一的区别在于它们处理失败的方式。使用 'require' 和 'require_once' 时，如果找不到文件，将生成致命错误并终止脚本的执行。

## 13.3 获取时间和日期

能够访问系统时间和日期是一项非常实用的能力。日期和时间可用于各种任务，从在网页上显示正确的日期和时间这一简单操作，到创建数据库记录创建时间的时间戳。

日期和时间都可以通过一个名为 getdate() 的函数来访问：

```
$array = getdate();
```

getdate() 函数返回一个包含当前日期和时间的数组。该数组是一个字符串索引数组，其索引值在表13.1中描述。

以下脚本演示了使用 getdate() 函数访问日期：

```
<?php
// File: example13-21.php

$arrDate = getdate();

$intSeconds = $arrDate['seconds'];
$intMinutes = $arrDate['minutes'];
```

图13.7 日期函数

![](img/b2471264f405d17994ef173e4b9cec92_410_0.png)

此函数返回一个由两部分组成的字符串：

'msec sec'

'sec' 的值是自1970年1月1日午夜以来经过的秒数。字符串的 'msec' 部分是当前秒的微秒小数部分。以下是在脚本中使用该函数的示例：

```
<?php
// File: example13-22.php

$strSecs = microtime();
echo "<p>$strSecs</p>";
?>
```

在执行上述脚本时，输出为：

0.29059500 1131475671

虽然我们意识到 microtime() 函数看起来并不起眼，但它实际上非常有用。在本章稍后生成随机数时，我们将再次使用该函数。

### 检查有效日期

有时用户需要通过表单输入日期。虽然并非所有日期都能一眼看出是否正确，但最好检查该日期是否确实有效，例如，以下哪些日期是有效的：

-   6,29,2005
-   13,19,2005
-   2,28,2005
-   2,29,2000

上述操作使用从 microtime() 函数获取当前时间时产生的随机数来为随机数生成器设置种子。我们现在可以获取随机数了，rand() 函数使我们能够实现这一点。此函数的格式为：

```
$number = rand();
```

可以在不带任何参数的情况下调用 rand() 函数，此时它将返回一个随机数，其最大值和最小值不在您的控制范围内。不过，您可以通过包含起始参数和结束参数来限制生成的随机数范围，如下所示：

```
$number = rand($start, $end);
```

以下脚本演示了生成一个1到6之间的随机数。因此，此脚本可用于模拟掷骰子：

```
<?php
// File: example13-24.php

srand( (double) microtime() * 1000000);
$intRandVal = rand(1,6);
echo "<p>Random Number: $intRandVal</p>";
?>
```

## 13.5 水果机示例

我们将把所学的关于函数和随机数的知识结合起来，创建一个水果机脚本。该脚本使用一些简单的图片来表示水果机中的水果。如图13.8所示。

这些图片存储在脚本所在目录下的 'graphics' 子目录中：

```
<?php
// File: example13-25.php

$arrFruits = array (1=>"apple", 2=>"orange", 3=>"lemon", 4=>"plum");

function randomNumber ($intStart, $intEnd) {
    srand( (double) microtime() * 1000000);
    $intRandVal = rand($intStart,$intEnd);
    return $intRandVal;
}

$strFirst = $arrFruits[randomNumber(1,4)];
$strSecond = $arrFruits[randomNumber(1,4)];
$strThird = $arrFruits[randomNumber(1,4)];

echo "<h2>Try your luck at the fruit machine ...</h2>";
echo "<table width='450'><tr>";
echo "<td><img src='graphics/$strFirst.gif' alt='$strFirst'/></td>";
```

