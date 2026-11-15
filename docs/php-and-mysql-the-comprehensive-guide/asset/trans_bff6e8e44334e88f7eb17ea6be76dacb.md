

$global = "Global-Local";
$local = "Local";
echo "$global $local<br />";
}
output();
echo $global . $local;
?>

### 清单 6.9 变量的有效性 ("function_validity.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_168_0.png)

### 图 6.6 局部变量仅在函数内部有效，全局变量仅在外部有效

### "global"

如果要在函数中使用全局变量，必须使用 global 关键字显式定义它。这样 PHP 解释器就知道必须获取该全局变量（参见图 6.7）。

```php
<?php
$global = "Global variable";
function output() {
global $global;
echo $global;
}
output();
?>
```

### 清单 6.10 全局变量 ("function_global.php")

> **注意**
> 一旦设置，你也可以更改全局变量的值。但是，在实际中很少使用带 global 的全局变量。

![](img/ae7820c36e8f24c1623d26668b28e80e_169_0.png)

### 图 6.7 你现在可以在函数中访问全局变量。

### $GLOBALS

$GLOBALS 数组包含所有全局变量。你可以使用它从任何地方访问全局变量或更改其值。

```php
<?php
$global = "Global variable";
function output() {
echo $GLOBALS["global"];
}
output();
?>
```

### 清单 6.11 "$GLOBALS" 数组 ("function_globalsArray.php")

## 6.1.3 返回值

使用参数，你可以将值传递给函数。要从函数中获取返回值，需要使用 return 关键字。它会终止函数；也就是说，return 之后的所有语句都会被忽略。return 处的值会被返回。

```
function Name(Parameter) {
Statements;
return ReturnValue;
}
```

然后你需要对这个返回值做些什么。当然，你可以立即输出它。但是，你通常会将其保存在一个变量中：

```
$Variable = Name(Parameter);
```

> **注意**
> 任何使用过 Pascal 编程的人都知道确切的区别。没有返回值的函数实际上是一个 _过程_。有些语言为过程和函数使用不同的关键字（例如，Visual Basic）。但在 PHP 中，这种区别没有意义。这就是为什么我们通常称之为 _函数_。

下一个清单展示了一个简单示例。函数接收一个参数，添加一个字符串，并返回它。然后输出返回值。

```php
<?php
function output($par) {
    return "Hello $par";
}
$return = output("world");
echo $return;
?>
```

### 清单 6.12 带返回值的函数 ("function_return.php")

**提示**
函数（尤其是带有返回值的函数）只有在包含更复杂的语句并且被多次使用时，才能发挥其全部效用。

### 多个返回值

使用 `return`，你只能接收一个返回值。通常使用数组来获取多个值。你将在第 8 章了解更多关于数组的内容。以下示例生成一个乘法系列，并将其作为数组返回（参见图 6.8）。

![](img/ae7820c36e8f24c1623d26668b28e80e_170_0.png)

### 图 6.8 作为数组的乘法系列

```php
<?php
function multiplication($a) {
    $products = [];
    for ($i = 1; $i <= 10; $i++) {
        $products[$i] = $a * $i;
    }
    return $products;
}
$result = multiplication(2);
foreach ($result as $ele) {
    echo "$ele<br />";
}
?>
```

### 清单 6.13 函数将数组作为返回值返回 ("function_array.php")

### 返回引用

你可以将函数的返回值作为引用接收。为此，请在函数名和调用函数时输入 & 符号。²

```php
<?php
$authors = ["tobias", "christian"];

function &return(&$authors, $i) {
    print_r($authors);
    print "<br />";
    return $authors[$i];
}

$author = &return($authors, 1); //$author == "christian"
$author = "wolfgang"; //$author == "wolfgang"
print_r($authors);
?>
```

### 清单 6.14 作为引用的返回 ("function_reference.php")

如果你从函数中接收较大的数组或对象，这种变体很有用。因为只传递引用，而不传递数组或对象本身（参见图 6.9），因此这种方法可以提高性能。

![](img/ae7820c36e8f24c1623d26668b28e80e_171_0.png)

### 图 6.9 当函数以引用方式调用时，数组的第二个元素会发生变化

² 也可以将参数作为引用传递给函数。但是，在较新的 PHP 版本中，不再推荐这样做，并且会发出警告。

## 6.1.4 变量中的函数名

PHP 中经常提到的一种选择是³。你可以将函数名保存在变量中，然后像原始函数调用一样使用它们。这里有一个示例：函数名为 output()，并期望一个参数。你可以将函数名保存在变量中，然后使用圆括号（甚至必要的参数）来调用该变量。

```php
<?php
function output($par) {
    echo "Hello $par";
}
$functionname = "output";
$functionname("PHP 8.3");
?>
```

### 清单 6.15 函数名存储在变量中 ("function_variables.php")

**注意**

要测试变量是否包含可调用的函数，可以使用 is_callable(Variable) 函数。它返回一个布尔值。

尽管此功能非常令人兴奋，但它有两个缺点：首先，性能会受到一定影响，因为 PHP 总是要先检查带有圆括号的变量是否是函数。其次——这是更严重的缺点——由于这种结构，代码会变得相当令人困惑。因此，此功能在实际中仅在特殊情况下使用，例如在使用单独的函数通过 usort() 进行排序时。

## 6.1.5 匿名函数

匿名函数（也称为闭包）是——顾名思义——没有名称的函数。此类匿名函数可在其他函数调用中定义，也可以赋值给变量。以下示例将匿名函数赋给变量 $output，随后可随时再次调用。

```php
<?php
$output = function($parameter) {
    echo 'My ' . $parameter . '<br />';
};

$output('Output 1');
$output('Output 2');
?>
```

### 清单 6.16 匿名函数的使用 ("anonymous_functions.php")

³ 通常带有不同的名称，例如变量函数。

> **注意**
> 如前所述，匿名函数可以用于其他函数调用。在那里，它们是所谓的回调函数。一个示例是使用 `usort()` 进行排序。但是，匿名函数也可以通过 `call_user_func()` 在函数调用中使用。

![](img/ae7820c36e8f24c1623d26668b28e80e_173_0.png)

### 图 6.10 匿名函数的输出

匿名函数也可以在其他函数内部使用。在这种情况下，可以使用 use 关键字将变量分配给匿名函数，这些变量随后在函数内部可用。

```php
<?php
function output($separator) {
    $address = 'My ';
    $func = function($parameter) use ($address, $separator) {
        echo $address . $parameter . $separator;
    };

    $func('Output 1');
    $func('Output 2');
}

output('<br />');
?>
```

### 清单 6.17 匿名函数中的变量 ("anonymous_functions_variables.php")

> **提示**
> 使用 `func_num_args()`、`func_get_arg()` 和 `func_get_args()` 重载函数的选项在匿名函数中也可用。

> **注意**
> 自 PHP 5.6 起，use 也可用于函数和常量。自 PHP 5.4 起，你也可以在闭包中使用 `$this`，但前提是匿名方法是类的一部分。

## 6.1.6 递归函数

递归函数是调用自身的函数。例如，递归函数可以以类似于循环的方式使用。这意味着函数调用位于函数内部。但是，你仍然需要一个变化，否则使用递归函数会产生无限循环。

以下脚本使用递归函数计算阶乘⁴（参见图 6.11）。

```php
<?php
function factorial($i) {
    if ($i > 0) {
        return $i * factorial($i-1);
    } else {
        return 1;
    }
}
echo factorial(5);
?>
```

### 清单 6.18 使用递归函数计算阶乘 ("function_recursive.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_174_0.png)

### 图 6.11 5 的阶乘是 120

你也可以使用循环达到相同的结果，如下一个示例所示。

```
$result = 1;
for ($i = 5; $i > 0; $i--) {
    $result *= $i;
}
echo $result;
```

### 清单 6.19 计算阶乘的循环 ("loop_factorial.php")

在某些情况下，递归函数被认为很优雅，许多计算机科学家非常欣赏递归编程。但是，它通常更难读懂——尤其是对于没有编写该脚本的人。

⁴ 阶乘也通常写作 n!，并用 n * (n - 1) * (n - 2) * ... * 1 进行计算。例如，阶乘用于组合数学。

