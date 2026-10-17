
```php
<?php # Script 3.10 - calculator.php #5

// This function creates a radio button.
// The function takes two arguments: the value and the name.
// The function also makes the button "sticky".
function create_radio($value, $name = 'gallon_price') {

    // Start the element:
    echo '<input type="radio" name="' . $name .'" value="' . $value . '"';

    // Check for stickiness:
    if (isset($_POST[$name]) && ($_POST[$name] == $value)) {
        echo ' checked="checked"';
    }

    // Complete the element:
    echo " /> $value ";

} // End of create_radio() function.

// This function calculates the cost of the trip.
// The function takes three arguments: the distance, the fuel efficiency, and the price
// per gallon.
// The function returns the total cost.
function calculate_trip_cost($miles, $mpg, $ppg) {

    // Get the number of gallons:
    $gallons = $miles/$mpg;

    // Get the cost of those gallons:
    $dollars = $gallons/$ppg;

    // Return the formatted cost:
    return number_format($dollars, 2);

} // End of calculate_trip_cost() function.

$page_title = 'Trip Cost Calculator';
include ('includes/header.html');

// Check for form submission:
if ($_SERVER['REQUEST_METHOD'] == 'POST') {

    // Minimal form validation:
    if (isset($_POST['distance'], $_POST['gallon_price'], $_POST['efficiency']) &&
    is_numeric($_POST['distance']) && is_numeric($_POST['gallon_price'])
        && is_numeric($_POST['efficiency']) ) {

        // Calculate the results:
        $cost = calculate_trip_cost($_POST['distance'], $_POST['efficiency'],
            $_POST['gallon_price']);
        $hours = $_POST['distance']/65;

        // Print the results:
        echo '<h1>Total Estimated Cost</h1>
        <p>The total cost of driving ' . $_POST['distance'] . ' miles, averaging ' .
            $_POST['efficiency'] . ' miles per gallon, and paying an average of $' . $_POST
            ['gallon_price'] . ' per gallon, is $' . $cost . '. If you drive at an average of
            65 miles per hour, the trip will take approximately ' . number_format($hours, 2)
            . ' hours.</p>';

    } else { // Invalid submitted values.
        echo '<h1>Error!</h1>
        <p class="error">Please enter a valid distance, price per gallon, and fuel
            efficiency.</p>';
    }

} // End of main submission IF.

// Leave the PHP section and create the HTML form:
?>

<h1>Trip Cost Calculator</h1>
<form action="calculator.php" method="post">
    <p>Distance (in miles): <input type="text" name="distance" value="<?php if (isset($_POST
        ['distance'])) echo $_POST['distance']; ?>" /></p>
    <p>Ave. Price Per Gallon: <span class="input">
    <?php
    create_radio('3.00');
    create_radio('3.50');
    create_radio('4.00');
    ?>
    </span></p>
    <p>Fuel Efficiency: <select name="efficiency">
        <option value="10"<?php if (isset($_POST['efficiency']) && ($_POST['efficiency'] ==
            '10')) echo ' selected="selected"'; ?>>Terrible</option>
        <option value="20"<?php if (isset($_POST['efficiency']) && ($_POST['efficiency'] ==
            '20')) echo ' selected="selected"'; ?>>Decent</option>
        <option value="30"<?php if (isset($_POST['efficiency']) && ($_POST['efficiency'] ==
            '30')) echo ' selected="selected"'; ?>>Very Good</option>
        <option value="50"<?php if (isset($_POST['efficiency']) && ($_POST['efficiency'] ==
            '50')) echo ' selected="selected"'; ?>>Outstanding</option>
    </select></p>
    <p><input type="submit" name="submit" value="Calculate!" /></p>
</form>

<?php include ('includes/footer.html'); ?>
```

---

### 3. 执行计算并返回格式化后的成本

```php
$gallons = $miles/$mpg;
$dollars = $gallons/$ppg;
return number_format($dollars, 2);
} // End of calculate_trip_cost() function.
```

前两行与之前脚本使用的计算相同，但现在它们使用函数变量。该函数最后做的是返回计算出的成本的格式化版本。

### 4. 将计算成本的两行代码（Script 3.9 的第 32-33 行）替换为函数调用

```php
$cost = calculate_trip_cost ($_POST['distance'], $_POST['efficiency'], $_POST['gallon_price']);
```

调用该函数并传递三个必需的值将执行计算。由于函数返回一个值，因此函数调用的结果——即返回值——可以赋给一个变量。

### 5. 更改 `echo` 语句以使用新变量

```php
echo '<h1>Total Estimated Cost</h1>
  <p>The total cost of driving' . $_POST['distance'] .' miles, averaging ' . $_POST['efficiency'] . ' miles per gallon, and paying an average of $' . $_POST['gallon_price'] . ' per gallon, is $' . $cost . '. If you drive at an average of 65 miles per hour, the trip will take approximately '. number_format($hours, 2) . ' hours.</p>';
```

此处的 `echo` 语句使用 `$cost` 变量，而不是 `$dollars`（如脚本的前一个版本所示）。此外，由于 `$cost` 变量在函数内部已格式化，因此无需在 `echo` 语句中对该变量应用 `number_format()` 函数。

### 6. 保存文件，将其放在 Web 目录中，并在 Web 浏览器中测试它。

![Image](img/circle-f.jpg)

![Image](img/03_figure_17_f.jpg)

![Image](img/circle-f.jpg) 计算器现在使用用户定义函数来计算并返回行程成本。但此更改不会影响用户看到的内容。

---

> **Tip**
>
> `return` 语句会在该处终止代码执行，因此位于已执行的 `return` 之后的函数内部代码永远不会运行。

---

> **Tip**
>
> 一个函数可以有多个 `return` 语句（例如在 `switch` 语句或条件语句中），但最多只会调用其中一个。例如，函数通常这样做：
>
> ```php
> function some_function () {
>     if (/* condition */) {
>         return TRUE;
>     } else {
>         return FALSE;
>     }
> }
> ```

---

> **Tip**
>
> 要让函数返回多个值，请使用 `array()` 函数返回一个值数组：
>
> ```php
> return array ($var1, $var2);
> ```

---

> **Tip**
>
> 调用返回数组的函数时，使用 `list()` 函数将数组元素赋值给单独的变量：
>
> ```php
> list($v1, $v2) = some_function();
> ```

---

### 变量作用域

PHP 中的每个变量都有一个*作用域*，也就是说，变量（及其值）可被访问的范围。首先，变量拥有其所在页面的作用域。如果你定义了 `$var`，该页面的其余部分可以访问 `$var`，但其他页面通常不能（除非你使用特殊变量）。

由于包含文件的行为就好像它们是原始（包含）脚本的一部分一样，因此在 `include()` 行之前定义的变量可供包含文件使用（正如你已经在 `$page_title` 和 `header.html` 中看到的那样）。此外，在包含文件中定义的变量，在 `include()` 行*之后*可供父（包含）脚本使用。

用户自定义函数拥有自己的作用域：在函数内部定义的变量在外部不可用，而在函数外部定义的变量在内部不可用。因此，函数内部的变量可以与外部的变量同名，但却是一个完全不同、具有不同值的变量。这个概念让许多初学者感到困惑。

要改变函数内部的变量作用域，可以使用 `global` 语句。

```php
function function_name() {
    global $var;
}

$var = 20;
function_name(); // 函数调用。
```

在本例中，函数内部的 `$var` 现在与外部的 `$var` 相同。这意味着函数内的 `$var` 已经拥有值 20，如果该值在函数内部发生改变，外部 `$var` 的值也会随之改变。

绕过变量作用域的另一种选择是使用超全局变量：`$_GET`、`$_POST`、`$_REQUEST` 等。这些变量在你的函数内部会自动可用（因此它们是*超*全局的）。你也可以向 `$GLOBALS` 数组添加元素，使它们在函数内可用。

说了这么多，在函数中最好几乎永远不要使用全局变量。函数的设计应当使其通过参数接收所需的每一个值，并返回需要返回的任何值（或值）。在函数中依赖全局变量会使它们更依赖上下文，因此用处也就更小。

---

## 复习与实践

如果你对复习问题或实践提示有任何疑问，请访问本书的支持论坛（[www.LarryUllman.com/forums/](http://www.LarryUllman.com/forums/)）。

### 复习

*   什么是*绝对*路径？什么是*相对*路径？
*   `include()` 和 `require()` 有什么区别？
*   `include()` 和 `include_once()` 有什么区别？通常应该避免使用哪个函数，为什么？
*   为什么包含文件使用什么扩展名*无关紧要*？
*   `$_SERVER['REQUEST_METHOD']` 的值有什么意义？
*   如何使以下表单元素具有“粘性”？
    *   文本输入框
    *   下拉菜单
    *   单选按钮
    *   复选框
    *   文本域
*   如果你有一个由 HTML 标签内的代码引起的 PHP 错误，必须在哪里查找错误消息？
*   定义自定义函数的语法是什么？
*   定义接受参数的函数的语法是什么？
*   定义接受带默认值参数的函数的语法是什么？默认值如何影响函数的调用方式？
*   如何定义并调用一个返回值的函数？

### 实践

*   为本章中的页面创建一个新的 HTML 模板。以该新模板为基础创建新的页眉和页脚文件。这样做，你应该能够在不修改任何 PHP 脚本的情况下更改整个网站的外观。
*   创建一个新表单并赋予其“粘性”功能。让表单使用文本域和复选框（本章均未演示这两者）。
*   修改 `calculator.php`，使其使用常量代替硬编码的平均速度 65。（按原样编写时，平均速度是一个“魔术数字”：在脚本中使用却无解释的值。）
*   更进一步，修改 `calculator.php`，让用户可以输入平均速度或从选项列表中选择。
*   更新 `calculator.php` 的输出，使其在小时数大于 24 时显示行程所需的天数和小时数。
*   作为一个更高级的技巧，重写 `calculator.php`，使 `create_radio()` 函数调用在脚本中只出现一次，但仍能创建三个单选按钮。提示：使用循环。

---

## 4. MySQL 简介

### 本章内容

*   命名数据库元素 112
*   选择列类型 114
*   选择其他列属性 118
*   访问 MySQL 121
*   复习与实践 128

由于本书讨论如何集成多种技术（主要是 PHP、SQL 和 MySQL），在开始编写使用 SQL 与 MySQL 交互的 PHP 脚本之前，对每种技术单独有扎实的理解非常重要。本章与前几章不同，因为它暂时抛开 PHP，深入探讨 MySQL。

MySQL 是世界上最流行的开源数据库应用程序（根据 MySQL 官网 [www.mysql.com](http://www.mysql.com) 的说法），常与 PHP 一起使用。MySQL 软件包含数据库服务器（存储实际数据）、不同的客户端应用程序（用于与数据库服务器交互）以及多种实用工具。在本章中，你将学习如何使用 MySQL 允许的数据类型和其他属性来定义一个简单的表。然后你将学习如何使用两种不同的客户端应用程序与 MySQL 服务器进行交互。所有这些信息将为下一章讲授的 SQL 打下基础。

### 命名数据库元素
