

## 循环

循环允许一段代码执行指定次数，或直到满足特定条件为止。它们常用于从数据库查询中读取记录、从文件中读取行，或遍历数组元素等任务。PHP 中有四种循环：while、do ... while、for 和 foreach。前三种将在下文介绍。foreach 将在本章后面讨论数组时介绍。

### while

while 是最简单的循环语句。它测试一个条件，只要该条件在每次迭代开始时求值为 true，就反复执行一段语句：

```
while (condition) {
    statements
}
```

循环常与递增或递减运算符一起使用，以控制循环何时开始和停止。为此使用的变量（如下例中的 $i）有时称为循环控制变量：

```
echo ("<select name=\"num_players\">\n");
$i = 0;

while (++$i <= $iMaxPlayers) {
    echo("<option value=\"$i\">$i</option>\n");
}

echo("</select>\n");
```

在某些循环中，布尔变量用作循环控制变量。例如，从文件中读取行的循环可能会使用类似 $bEOF 的变量，只要文件末尾未到达就继续循环。

break 语句用于停止循环。遇到 break 时，当前迭代停止，不再执行后续迭代：

```
echo("<select name=\"num_players\">\n");
$i = 0;

while (++$i <= $iMaxPlayers) {
    if (! is_legal_val($i)) {
        break; // Stop adding options to the select element
    }
    echo("<option value=\"$i\">$i</option>\n");
}

echo("</select>\n");
```

在某些情况下，我们可能希望仅停止当前迭代并跳到下一次迭代。为此我们使用 continue 语句：

```
echo("<select name=\"num_players\">\n");
$i = 0;

while (++$i <= $iMaxPlayers) {
    if (! is_legal_val($i)) {
        continue; // Skip ahead to next iteration.
        // Don't echo option for this value
    }
    echo("<option value=\"$i\">$i</option>\n");
}

echo("</select>\n");
```

### do ... while

do ... while 循环与 while 循环类似，只不过条件在每次迭代末尾测试，而不是开头测试。这意味着循环至少执行一次。在以下示例中，无论 $iMaxPlayers 的值如何，零始终是一个选项：

```
echo("<select name=\"num_players\">\n");
$i = 0;

do {
    echo("<option value=\"$i\">$i</option>\n");
} while (++$i <= $iMaxPlayers);

echo("</select>\n");
```

### for

for 循环的语法与 while 循环有很大不同。差异主要在于组织方式：for 循环将所有控制循环流程的表达式都放在第一行：

```
for (expression1; expression2; expression3) {
    statements
}
```

expression1 在循环开始前求值。它通常用于初始化循环控制变量。expression2 在循环的每次迭代开始时求值。它作为条件表达式：如果 expression2 求值为 true，循环继续；如果 false，循环停止。expression3 在每次迭代结束时求值，因此它非常适合递增或递减循环控制变量：

```
echo("<select name=\"num_players\">\n");

for ($i = 0; $i <= $iMaxPlayers; ++$i) {
    echo("<option value=\"$i\">$i</option>\n");
}

echo("</select>\n");
```

此示例与我们之前的 do ... while 示例效果相同。它创建一个从零到 $iMaxPlayers 的选项 <select> 元素。该示例演示了 for 结构最常见（也是预期）的用法：初始化控制变量、将变量与值进行比较，以及递增或递减该值。但是，for 也可以以其他方式使用。像在 C 和其他语言中一样，留空一个或多个表达式是合法的（如果省略，expression2 默认为 true）：

```
for ( ; ; ) {
    if (my_function() == "stop") break;
}
```

这个循环将一直执行，直到 my_function() 返回字符串 "stop"。虽然这完全合法，但这不是编写循环最清晰的方式。这段代码可以写得更合理：

```
while (my_function() != "stop");
```

### 循环的替代语法

与 if 语句一样，不同的循环也支持替代语法：

```php
<?php
while (my_function() > 0):
?>

<tr><td><input type="text" /></td></tr>

<?php
endwhile;
?>

...

<?php
for ($i = 10; $i > $iMinScore; --$i):
?>

<li>Another XHTML list item</li>

<?php
endfor;
?>
```

## 函数

函数是一段代码块，可以定义一次，然后从程序的其他部分调用（或称呼），从而实现集中化、模块化的代码。通常，函数接收一个或多个参数，使用这些参数执行某些操作，然后返回一个结果值。PHP 拥有大量内置函数，如 date() 和 gettype()，创建用户定义函数也是轻而易举。

### 定义函数

函数使用 function 语句声明。如果函数接受任何参数，它们在函数声明中作为变量声明：

```php
function kmToM($fKilometer)
{
    // Converts kilometers to miles
    return $fKilometer * 0.6214;
}

// Invoke the function:
echo(kmToM(5)); // prints 3.107
```

此函数只接受一个参数，即公里数。如果函数接受多个参数，则使用逗号分隔变量。return 语句用于将值发送回调用该函数的语句。并非所有函数都返回值。例如，向浏览器输出代码的函数可能没有返回值。return 语句也可用于在不返回值的情况下停止函数，这很类似于循环中的 break 语句。

保存参数传递值的变量称为 **参数**。因此，在前面的示例中，5 是参数，$fKilometer 是形参。默认情况下，参数按值传递，这意味着形参仅持有该值的副本。如果形参的值在函数内部更改，这不会影响函数外部任何变量的值：

```php
function half($fNumber)
{
    // Cut a number in half.
    $fNumber = $fNumber / 2;
    return $fNumber;
}

$fWage = 50.0;
echo(half($fWage)); // prints 25
echo($fWage); // prints 50
```

由于参数按值传递，$fWage 的值不会改变，即使在传递给 half() 之后也是如此。相比之下，当参数按引用传递时，对形参值的任何更改都会导致用作参数的变量发生变化。要指示参数应按引用传递，请在变量名之前放置一个和号 (&)：

```php
function half(&$fNumber)
{
    // Cut a number in half.
    $fNumber = $fNumber / 2;
    return $fNumber;
}

$fWage = 50.0;
echo(half($fWage)); // prints 25
echo($fWage); // prints 25
```

请注意，如果参数按值传递，它必须作为变量传递，而不能是文本或常量。

要为参数设置默认值，请在函数声明中为其赋值。分配默认值会使参数变为可选。如果未提供该参数，则假定使用默认值。将所有可选参数声明放在任何非可选参数声明的右边非常重要：

```php
function raise(&$fWage, $fPercent = 4.0)
{
    // Raise fWage by given percent
    $fWage += $fWage * $fPercent/100;
}

$fWage = 50.0;
raise($fWage); // Raises 4%
echo($fWage); // Prints 52
raise($fWage, 10); // Raises 10%
echo($fWage); // Prints 57.2
```

从 PHP4 开始，函数也可以接受可变数量的参数。内置函数 func_num_args()、func_get_arg() 和 func_get_args() 用于测试这类函数。func_num_args() 返回传递给函数的参数数量。func_get_arg() 接收一个整数索引，并返回参数列表中与其匹配的参数。索引从零开始，因此 func_get_arg(0) 返回第一个参数，func_get_arg(1) 返回第二个参数，以此类推。func_get_args() 返回一个包含函数所有参数的数组：

```php
function argTest()
{
    // Test arguments

    // How many arguments:
    echo(func_num_args()); // Prints 5

    // Print first argument:
    echo(func_get_arg(0)); // Prints a

    // Print second argument:
    echo(func_get_arg(1)); // Prints b
}

argTest("a", "b", "c", "d", "e");
```

处理函数时另一个可能有用的内置函数是 function_exists()，它用于确定函数是否已定义。有关处理函数的内置函数的完整列表，请参阅 [在线 PHP 手册](http://www.php.net/manual/en/ref.funchand.php)。

### 变量作用域

默认情况下，函数中的变量具有局部作用域。对局部变量值的更改不会影响函数外部的变量，即使局部变量和外部变量同名也是如此：

```
function printWage()
{
    // Print fWage to the browser
```

