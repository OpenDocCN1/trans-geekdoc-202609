
## 示例代码：`index.php` (脚本 3.7)

```php
<?php # Script 3.7 - index.php #2

// This function outputs theoretical HTML
// for adding ads to a Web page.
function create_ad() {
    echo '<p class="ad">This is an annoying ad! This is an annoying ad! This is an
      annoying ad! This is an annoying ad!</p>';
} // End of the function definition.

$page_title = 'Welcome to this Site!';
include ('includes/header.html');

// Call the function:
create_ad();
?>

<h1>Content Header</h1>

<p>This is where the page-specific content goes. This section, and the
corresponding header, will change from one page to the next.</p>

<p>Volutpat at varius sed sollicitudin et, arcu. Vivamus viverra. Nullam turpis.
Vestibulum sed etiam. Lorem ipsum sit amet dolore. Nulla facilisi. Sed tortor.
Aenean felis. Quisque eros. Cras lobortis commodo metus. Vestibulum vel purus.
In eget odio in sapien adipiscing blandit. Quisque augue tortor, facilisis sit
amet, aliquam, suscipit vitae, cursus sed, arcu lorem ipsum dolor sit amet.</p>

<?php

// Call the function again:
create_ad();

include ('includes/footer.html');
?>
```

在实际函数中，代码将输出实际的 HTML，而不是一段文本。（实际的 HTML 将由您用于生成和跟踪广告的服务提供。）

**4.** 关闭函数定义：

```php
} // End of the function
definition.
```

在函数定义的末尾放置注释很有帮助，这样您就知道定义从哪里开始、到哪里结束（至少对于较长的函数定义是有帮助的）。

**5.** 在包含页眉之后、退出 PHP 代码块之前，调用该函数：

```php
create_ad();
```

对 `create_ad()` 函数的调用最终会在此处插入函数的输出。

**6.** 在包含页脚之前，再次调用该函数：

```php
create_ad();
```

**7.** 保存文件并在 Web 浏览器中测试它。

***

> **提示**
>
> 如果您看到 `call to undefined function function_name` 错误，这意味着您正在调用一个尚未定义的函数。如果您拼错了函数名称（无论是在定义时还是调用时），或者未能包含定义该函数的文件，就可能发生这种情况。

***

> **提示**
>
> 由于用户定义函数会占用一些内存，您应该谨慎决定何时使用它。一般来说，函数最适合用于可能在脚本或网站的多个位置执行的代码块。

## 创建接受参数的函数

就像 PHP 的内置函数一样，您编写的函数也可以接受*参数*。例如，`strlen()` 函数接受一个字符串作为参数，以确定其字符长度。

函数可以接受任意数量的参数，但您列出它们的顺序至关重要。要允许参数，请在函数定义中添加变量：

```php
function print_hello($first, $last) {
    // Function code.
}
```

您为参数使用的变量名与脚本的其余部分无关（更多内容请参阅本章末尾的“变量作用域”栏），但请尽量使用有效且有意义的名称。

函数定义后，您可以像调用 PHP 中的任何其他函数一样调用它，向其传递字面值或变量：

```php
print_hello ('Jimmy', 'Stewart');

$surname = 'Stewart';

print_hello ('Jimmy', $surname);
```

与 PHP 中的任何函数一样，未发送正确数量的参数会导致错误。

![Image](img/03_figure_13_b.jpg)

未能向函数发送适当数量（有时还有类型）的参数会产生错误。

为了演示这一概念，让我们重写计算器表单，以便用户定义的函数创建每加仑价格的单选按钮。这样做将有助于清理混乱的表单代码。

### 定义接受参数的函数

**1.** 在文本编辑器或 IDE 中打开 `calculator.php` (脚本 3.6)。

**2.** 在初始 PHP 标记之后，开始定义 `create_gallon_radio()` 函数 (脚本 3.8)：

```php
function create_gallon_radio ($value) {
```

该函数将创建如下代码：

```html
<input type="radio" name="gallon_price" value="XXX" checked="checked" /> XXX
```

或：

```html
<input type="radio" name="gallon_price" value="XXX" /> XXX
```

为了能够动态设置每个单选按钮的值，每次调用时必须将该值传递给函数。因此，这是该函数接受的唯一参数。

请注意，用作参数的变量不是 `$_POST['gallon_price']`。函数的参数变量专属于此函数，并拥有自己的名称。

**脚本 3.8.** `calculator.php` 表单现在使用函数来创建单选按钮。与 `create_ad()` 用户定义函数不同，此函数接受一个参数。

* * *

```php
<?php # Script 3.8 - calculator.php #3

// This function creates a radio button.
// The function takes one argument: the value.
// The function also makes the button "sticky".
function create_gallon_radio($value) {

    // Start the element:
    echo '<input type="radio" name="gallon_price" value="' . $value . '"';

    // Check for stickiness:
    if (isset($_POST['gallon_price']) && ($_POST['gallon_price'] == $value)) {
        echo ' checked="checked"';
    }

    // Complete the element:
    echo " /> $value ";

} // End of create_gallon_radio() function.

$page_title = 'Trip Cost Calculator';
include ('includes/header.html');

// Check for form submission:
if ($_SERVER['REQUEST_METHOD'] == 'POST') {

    // Minimal form validation:
    if (isset($_POST['distance'], $_POST['gallon_price'], $_POST['efficiency']) &&
    is_numeric($_POST['distance']) && is_numeric($_POST['gallon_price']) &&
        is_numeric($_POST['efficiency']) ) {

        // Calculate the results:
        $gallons = $_POST['distance'] / $_POST['efficiency'];
        $dollars = $gallons * $_POST['gallon_price'];
        $hours = $_POST['distance']/65;

        // Print the results:
        echo '<h1>Total Estimated Cost</h1>
        <p>The total cost of driving ' . $_POST['distance'] . ' miles, averaging
        ' . $_POST['efficiency'] . ' miles per gallon, and paying an average of $' .
        $_POST['gallon_price'] . ' per gallon, is $' . number_format ($dollars, 2) . '.
        If you drive at an average of 65 miles per hour, the trip will take
        approximately ' . number_format($hours, 2) . ' hours.</p>';

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
    <p>Distance (in miles): <input type="text" name="distance" value="<?php if
        (isset($_POST['distance'])) echo $_POST['distance']; ?>" /></p>
    <p>Ave. Price Per Gallon: <span class="input">
    <?php
    create_gallon_radio('3.00');
    create_gallon_radio('3.50');
    create_gallon_radio('4.00');
    ?>
    </span></p>
    <p>Fuel Efficiency:
    <select name="efficiency">
        <option value="10"<?php if (isset($_POST['efficiency']) && ($_POST['efficiency']
            == '10')) echo ' selected="selected"'; ?>>Terrible</option>
        <option value="20"<?php if (isset($_POST['efficiency']) && ($_POST['efficiency']
            == '20')) echo ' selected="selected"'; ?>>Decent</option>
        <option value="30"<?php if (isset($_POST['efficiency']) && ($_POST['efficiency']
            == '30')) echo ' selected="selected"'; ?>>Very Good</option>
        <option value="50"<?php if (isset($_POST['efficiency']) && ($_POST['efficiency']
            == '50')) echo ' selected="selected"'; ?>>Outstanding</option>
    </select></p>
    <p><input type="submit" name="submit" value="Calculate!" /></p>
</form>

<?php include ('includes/footer.html'); ?>
```

* * *

**3.** 开始创建单选按钮元素：

```php
echo '<input type="radio" name="gallon_price" value="' . $value . '"';
```

这段代码开始单选按钮的 HTML，包括其 `value` 属性，但不完成单选按钮，以便接下来处理“粘性”。输入的值来自函数参数。

**4.** 如果合适，使输入具有“粘性”：

```php
if (isset($_POST['gallon_price']) && ($_POST['gallon_price'] == $value)) {
    echo ' checked="checked"';
}
```

这段代码与原始表单中的代码类似，只是现在比较的值来自函数的参数。

**5.** 完成表单元素和函数：

```php
echo " /> $value ";
} // End of create_gallon_radio() function.
```

最后，`input` 标签闭合，随后显示该值，两侧各有一个空格。

**6.** 用三个函数调用替换表单中硬编码的单选按钮：

```php
<?php
create_gallon_radio('3.00');
create_gallon_radio('3.50');
create_gallon_radio('4.00');
?>
```

要创建这三个按钮，只需调用三次函数，每次传递不同的值。此处数值加上引号，否则 PHP 会去掉末尾的零。

**7.** 将文件保存为 `calculator.php`，将其放在您的 Web 目录中，并在 Web 浏览器中测试。

![Image](img/03_figure_14_c.jpg)

虽然使用用户定义函数来创建单选按钮（请参阅脚本 3.8），但对用户而言最终结果没有任何不同。

## 设置默认参数值

定义您自己的函数的另一种变体是预设参数的值。为此，在函数定义中为参数赋值：

```php
function greet ($name, $msg = 'Hello') {
    echo "$msg, $name!";
}
```

设置默认参数值的最终结果是，调用函数时该特定参数变为可选。如果向其传递了值，则使用传递的值；否则，使用默认值。

您可以为任意数量的参数设置默认值，只要这些参数在函数定义中排在最后面即可。换句话说，必需的参数必须始终列在最前面。

利用刚才定义的示例函数，以下调用均可正常工作：

```php
greet($surname, $message);

greet('Zoe');

greet('Sam', 'Good evening');
```

然而，仅调用 `greet()` 将无法工作。此外，若不给 `$name` 传值，就无法给 `$msg` 传值（参数值必须按顺序传递，且不能跳过必需参数）。

为了利用默认参数值，让我们创建一个改进版的 `create_gallon_radio()` 函数。按原写法，该函数仅能创建名为 `gallon_price` 的单选按钮。如果该函数能在表单中多次使用，为多组单选按钮服务，那就更好了（尽管在本脚本中不会那样使用该函数）。

### 设置默认参数值

**1.** 在文本编辑器或 IDE 中打开 `calculator.php`（参考 脚本 3.8），如果尚未打开的话。
