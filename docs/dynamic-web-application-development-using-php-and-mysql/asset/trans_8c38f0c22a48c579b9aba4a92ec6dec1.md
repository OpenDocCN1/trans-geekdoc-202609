
调用新脚本的网页。这是一个非常重要的安全特性，因为我们可以确保登录安全不会轻易被绕过。最后，我们学习如何将用户从一个网页重定向到另一个网页。

## 13.1 函数

函数是一段脚本，只有在函数被调用时才会被执行。如果函数从未被调用，与函数关联的脚本也永远不会被执行。函数非常强大，因为它们允许我们将代码分解为模块化的块，从而帮助脚本设计。由于函数可以从脚本中的任何位置按需调用任意多次，它们还有助于减少为应用程序编写的代码量，因为函数内的代码可以在脚本中一遍又一遍地“重用”。我们在之前的许多示例中已经使用过函数，但这些都是由他人为我们使用而编写的函数。我们将学习如何创建自己的函数。好消息是它们的工作方式与你一直使用的函数完全相同，并且一旦编写完成，你就可以与他人分享它们，让他们的编程生活更轻松，就像 PHP 开发者与你分享他们的函数库一样。

我们知道所有函数都可以接收多个参数，这些参数会传递给函数进行处理。我们也从过去使用已定义函数的经验中知道，函数可以返回一个单一值。这在图 13.1 中有所说明。

函数不必接收任何参数，也不必返回值。它们可以仅仅由用户定义的 PHP 语句组成。

### 用户定义的函数

当我们希望定义自己的函数时，我们需要使用 ‘function’ 关键字并使用以下语法：

```
function name (arguments...) {
...
...
}
```

函数使用关键字 ‘function’ 定义，后跟函数的唯一名称。每个函数必须有一个唯一名称。函数名称后面跟着一对括号，括号内包含以逗号分隔的参数列表（如果有的话）。构成函数的脚本语句被包含在大括号内。

**图 13.1** 函数调用

![](img/b2471264f405d17994ef173e4b9cec92_393_0.png)

> **注意** — 即使函数没有参数，括号仍然需要包含。

我们稍后会研究函数如何“返回”值。然而，现在让我们研究如何创建函数：

```php
<?php
// File: example13-1.php

echo "<p>Fahrenheit To Celsius</p>";
function fahrenheitToCelsius() {
    $floFahrenheit = 212;
    $floCelsius = (5/9)*($floFahrenheit-32);
    echo "<p>$floFahrenheit<sup>o</sup>F = $floCelsius<sup>o</sup>C</p>";
}
?>
```

上述脚本定义了一个名为 fahrenheitToCelsius() 的函数，该函数不接收任何参数。函数内的关联脚本将华氏温度值转换为摄氏温度值。然而，当我们运行脚本时，函数内的代码不会被处理。原因是我们没有调用函数。在上述脚本中，我们将通过以下调用来执行此操作：

```php
fahrenheitToCelsius();
```

例如：

```php
<?php
// File: example13-2.php

echo "<p>Fahrenheit To Celsius</p>";

function fahrenheitToCelsius() {
    $floFahrenheit = 212;
    $floCelsius = (5/9)*($floFahrenheit-32);
    echo "<p>$floFahrenheit<sup>o</sup>F = $floCelsius<sup>o</sup>C</p>";
}

fahrenheitToCelsius();
?>
```

上述脚本的输出是：

```text
212°F = 100°C
```

> **注意** — 在 PHP 中，函数是在函数调用之前还是之后定义并不重要！

### 变量和作用域

你会注意到示例函数在函数内部声明了 $floFahrenheit 的值。这并不实用，因为函数将始终执行相同的计算。我们需要的是在函数外部定义 $floFahrenheit 的值，以便我们可以调整它，例如像这样：

```php
<?php
// File: example13-3.php

echo "<p>Fahrenheit To Celsius</p>";

function fahrenheitToCelsius() {
    $floCelsius = (5/9)*($floFahrenheit-32);
    echo "<p>$floFahrenheit<sup>o</sup>F = $floCelsius<sup>o</sup>C</p>";
}

$floFahrenheit = 212;
fahrenheitToCelsius();
?>
```

在上面的示例中，$floFahrenheit 的值是在函数外部定义的：

```php
$floFahrenheit = 212;
fahrenheitToCelsius();
```

不幸的是，函数的输出不起作用，因为它给出了一个奇怪的结果：

0F = -17.7777777780C

你也可能会收到类似这样的几个警告通知：

```
Notice: Undefined variable: floFahrenheit in
C:\wamp\www\PHPLessonExamples\Lesson13\example13-3.php
```

你可以尝试将变量声明和函数调用移到函数之前，像这样：

```php
<?php
// File: example13-4.php

echo "<p>Fahrenheit To Celsius</p>";

$floFahrenheit = 212;
fahrenheitToCelsius();

function fahrenheitToCelsius() {
    $floCelsius = (5/9)*($floFahrenheit-32);
    echo "<p>$floFahrenheit<sup>o</sup>F = $floCelsius<sup>o</sup>C</p>";
}
?>
```

不幸的是，它仍然不起作用，并且可能会出现更多警告通知！原因在于函数被设计为工作的方式。函数被设计为与脚本的其余部分隔离。在函数外部声明的变量在函数内部不可见。这被称为变量的作用域。有趣的是，在函数内部定义的变量在函数外部也不可用！

注意
变量具有作用域，通常在函数内部或函数外部！

考虑以下脚本：

```php
<?php
// File: example13-5.php
echo "<p>Fahrenheit To Celsius</p>";
function fahrenheitToCelsius() {
    $floFahrenheit = 212;
    $floCelsius = (5/9)*($floFahrenheit-32);
}

fahrenheitToCelsius();
echo "<p>$floFahrenheit<sup>o</sup>F = $floCelsius<sup>o</sup>C</p>";
?>
```

在上面的脚本中，我们修改了之前的示例，使显示转换的 echo 语句位于函数外部。然而，$floFahrenheit 的原始值和 $floCelsius 的计算值都在函数内部，因此输出为以下结果也就不足为奇了：

0°F = 0°C

是的，你猜对了，脚本仍然不起作用，并且可能会出现警告通知！事实上，变量作用域意味着我们可以这样做：

```php
<?php
// File: example13-6.php
echo "<p>Fahrenheit To Celsius</p>";
function fahrenheitToCelsius() {
    $fltFahrenheit = 212;
    $fltCelsius = (5/9)*($fltFahrenheit-32);
    echo "<p>$fltFahrenheit<sup>o</sup>F = $fltCelsius<sup>o</sup>C</p>";
}

$fltFahrenheit = 100;
fahrenheitToCelsius();
echo "<p>$fltFahrenheit<sup>o</sup>F </p>";
?>
```

在上面的示例中，我们声明变量 $fltFahrenheit 并将其赋值为 100：

```
$fltFahrenheit = 100;
```

然后我们调用函数 fahrenheitToCelsius()：

```
fahrenheitToCelsius();
```

最后，我们显示 `$fltFahrenheit` 的值：

```
echo "<p>$fltFahrenheit<sup>o</sup>F </p>";
```

上述脚本的输出如 图 13.2 所示。这向我们展示的是，虽然我们在函数外部声明了一个名为 `$fltFahrenheit` 的变量，并在函数内部声明了同名变量，但它们被视为两个完全不同的变量，并且各自的值得以保持。

为了推进函数的使用，我们需要某种方法让函数能够看到函数外部的变量值。实现此目的的方法是通过使用函数参数。

### 创建带参数的函数

参数用于向函数传递值。这些可以是常量，也可以是在函数外部声明的变量。以下是修改后的脚本示例，其中包含了一个参数：

```php
<?php
// File: example13-7.php

echo "<p>Fahrenheit To Celsius</p>";

function fahrenheitToCelsius($floFahrenheit) {
    $floCelsius = (5/9)*($floFahrenheit-32);
    echo "<p>$floFahrenheit<sup>o</sup>F = $floCelsius<sup>o</sup>C</p>";
}
fahrenheitToCelsius(100);
?>
```

在上述脚本中，有两个主要区别需要注意。第一个是在函数定义中，其中括号现在包围了一个名为

**图 13.2 — 变量作用域**

![](img/b2471264f405d17994ef173e4b9cec92_397_0.png)
