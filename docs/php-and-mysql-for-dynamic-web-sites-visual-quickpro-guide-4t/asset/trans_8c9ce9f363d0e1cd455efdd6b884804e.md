
您为参数使用的变量名与脚本的其余部分无关（更多内容请参阅本章末尾的“[变量作用域](#ch03.html#ch03sb03)”栏），但请尽量使用有效且有意义的名称。

函数定义后，您可以像调用 PHP 中的任何其他函数一样调用它，向其传递字面值或变量：

```
print_hello ('Jimmy', 'Stewart');

$surname = 'Stewart';

print_hello ('Jimmy', $surname);
```

与 PHP 中的任何函数一样，未发送正确数量的参数会导致错误 ![Image](graphics/circle-b.jpg)。

![Image](graphics/03_figure_13_b.jpg)

![Image](graphics/circle-b.jpg)未能向函数发送适当数量（有时还有类型）的参数会产生错误。

为了演示这一概念，让我们重写计算器表单，以便用户定义的函数创建每加仑价格的单选按钮。这样做将有助于清理混乱的表单代码。

### 定义接受参数的函数

**1.** 在文本编辑器或 IDE 中打开 **`calculator.php`** ([脚本 3.6](#ch03.html#ch03ex06))。

**2.** 在初始 PHP 标记之后，开始定义 **`create_gallon_radio()`** 函数 (**[脚本 3.8](#ch03.html#ch03ex08)**)：

```
function create_gallon_radio ($value) {
```

该函数将创建如下代码：

```
<input type="radio" name="gallon_price" value="XXX" checked="checked" /> XXX
```

或：

```
<input type="radio" name="gallon_price" value="XXX" /> XXX
```

为了能够动态设置每个单选按钮的值，每次调用时必须将该值传递给函数。因此，这是该函数接受的唯一参数。

请注意，用作参数的变量不是 **`$_POST['gallon_price']`**。函数的参数变量专属于此函数，并拥有自己的名称。

**脚本 3.8.** `calculator.php` 表单现在使用函数来创建单选按钮。与 `create_ad()` 用户定义函数不同，此函数接受一个参数。

* * *

```
1   <?php # Script 3.8 - calculator.php #3
2
3   // This function creates a radio button.
4   // The function takes one argument: the value.
5   // The function also makes the button "sticky".
6   function create_gallon_radio($value) {
7
8       // Start the element:
9       echo '<input type="radio" name="gallon_price" value="' . $value . '"';
10
11      // Check for stickiness:
12      if (isset($_POST['gallon_price']) && ($_POST['gallon_price'] == $value)) {
13          echo ' checked="checked"';
14      }
15
16      // Complete the element:
17      echo " /> $value ";
18
19  } // End of create_gallon_radio() function.
20
21  $page_title = 'Trip Cost Calculator';
22  include ('includes/header.html');
23
24  // Check for form submission:
25  if ($_SERVER['REQUEST_METHOD'] == 'POST') {
26
27      // Minimal form validation:
28      if (isset($_POST['distance'], $_POST['gallon_price'], $_POST['efficiency']) &&
29      is_numeric($_POST['distance']) && is_numeric($_POST['gallon_price']) &&
30          is_numeric($_POST['efficiency']) ) {
31
32          // Calculate the results:
33          $gallons = $_POST['distance'] / $_POST['efficiency'];
34          $dollars = $gallons * $_POST['gallon_price'];
35          $hours = $_POST['distance']/65;
36
37          // Print the results:
38          echo '<h1>Total Estimated Cost</h1>
39          <p>The total cost of driving ' . $_POST['distance'] . ' miles, averaging
40          ' . $_POST['efficiency'] . ' miles per gallon, and paying an average of $' .
41          $_POST['gallon_price'] . ' per gallon, is $' . number_format ($dollars, 2) . '.
42          If you drive at an average of 65 miles per hour, the trip will take
43          approximately ' . number_format($hours, 2) . ' hours.</p>';
44
45      } else { // Invalid submitted values.
46          echo '<h1>Error!</h1>
47          <p class="error">Please enter a valid distance, price per gallon, and fuel
48              efficiency.</p>';
49      }
50
51  } // End of main submission IF.
52
53  // Leave the PHP section and create the HTML form:
54  ?>
55
56  <h1>Trip Cost Calculator</h1>
57  <form action="calculator.php" method="post">
58      <p>Distance (in miles): <input type="text" name="distance" value="<?php if
59          (isset($_POST['distance'])) echo $_POST['distance']; ?>" /></p>
60      <p>Ave. Price Per Gallon: <span class="input">
61      <?php
62      create_gallon_radio('3.00');
63      create_gallon_radio('3.50');
64      create_gallon_radio('4.00');
65      ?>
66      </span></p>
67      <p>Fuel Efficiency:
68      <select name="efficiency">
69          <option value="10"<?php if (isset($_POST['efficiency']) && ($_POST['efficiency']
70              == '10')) echo ' selected="selected"'; ?>>Terrible</option>
71          <option value="20"<?php if (isset($_POST['efficiency']) && ($_POST['efficiency']
72              == '20')) echo ' selected="selected"'; ?>>Decent</option>
73          <option value="30"<?php if (isset($_POST['efficiency']) && ($_POST['efficiency']
74              == '30')) echo ' selected="selected"'; ?>>Very Good</option>
74          <option value="50"<?php if (isset($_POST['efficiency']) && ($_POST['efficiency']
75              == '50')) echo ' selected="selected"'; ?>>Outstanding</option>
76      </select></p>
77      <p><input type="submit" name="submit" value="Calculate!" /></p>
78  </form>
79
80  <?php include ('includes/footer.html'); ?>
```

* * *

**3.** 开始创建单选按钮元素：

```
echo '<input type="radio" name="gallon_price" value="' . $value . '"';
```

这段代码开始单选按钮的 HTML，包括其 **`value`** 属性，但不完成单选按钮，以便接下来处理“粘性”。输入的值来自函数参数。

**4.** 如果合适，使输入具有“粘性”：

```
if (isset($_POST['gallon_price']) && ($_POST['gallon_price'] == $value)) {
    echo ' checked="checked"';
}
```

这段代码与原始表单中的代码类似，只是现在比较的值来自函数的参数。

**5.** 完成表单元素和函数：

```
echo " /> $value ";
} // End of create_gallon_radio() function.
```

最后，**`input`** 标签闭合，随后显示该值，两侧各有一个空格。

**6.** 用三个函数调用替换表单中硬编码的单选按钮：

```
<?php
create_gallon_radio('3.00');
create_gallon_radio('3.50');
create_gallon_radio('4.00');
?>
```

要创建这三个按钮，只需调用三次函数，每次传递不同的值。此处数值加上引号，否则 PHP 会去掉末尾的零。

**7.** 将文件保存为 **`calculator.php`**，将其放在您的 Web 目录中，并在 Web 浏览器中测试 ![Image](graphics/circle-c.jpg)。

![Image](graphics/03_figure_14_c.jpg)

![Image](graphics/circle-c.jpg)虽然使用用户定义函数来创建单选按钮（请参阅[脚本 3.8](#ch03.html#ch03ex08)），但对用户而言最终结果没有任何不同。

### 设置默认参数值

定义您自己的函数的另一种变体是预设参数的值。为此，在函数定义中为参数赋值：

```
function greet ($name, $msg = 'Hello') {
    echo "$msg, $name!";
}
```

设置默认参数值的最终结果是，调用函数时该特定参数变为可选。如果向其传递了值，则使用传递的值；否则，使用默认值。

您可以为任意数量的参数设置默认值，只要这些参数在函数定义中排在最后面即可。换句话说，必需的参数必须始终列在最前面。

