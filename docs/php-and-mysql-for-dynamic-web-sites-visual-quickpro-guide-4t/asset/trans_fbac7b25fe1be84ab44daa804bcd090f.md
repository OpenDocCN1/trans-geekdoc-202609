
# 让函数返回值

## 更新 `calculator.php` 脚本

让我们更新 `calculator.php` 脚本，使其使用函数来确定行程成本。

### 步骤

**1.** 在文本编辑器或 IDE 中打开 `calculator.php`（参考 [Script 3.9](#ch03.html#ch03ex09)），如果尚未打开。

**2.** 在第一个函数定义之后，开始定义第二个函数（**[Script 3.10](#ch03.html#ch03ex10)**）：

```php
function calculate_trip_cost ($miles, $mpg, $ppg) {
```

`calculate_trip_cost()` 函数接受三个参数：行驶距离、平均每加仑英里数和平均每加仑价格。

**Script 3.10.** 脚本中添加了另一个用户定义函数。它执行主要计算并返回结果。

---

```php
1   <?php # Script 3.10 - calculator.php #5
2
3   // This function creates a radio button.
4   // The function takes two arguments: the value and the name.
5   // The function also makes the button "sticky".
6   function create_radio($value, $name = 'gallon_price') {
7
8       // Start the element:
9       echo '<input type="radio" name="' . $name .'" value="' . $value . '"';
10
11      // Check for stickiness:
12      if (isset($_POST[$name]) && ($_POST[$name] == $value)) {
13          echo ' checked="checked"';
14      }
15
16      // Complete the element:
17      echo " /> $value ";
18
19  } // End of create_radio() function.
20
21  // This function calculates the cost of the trip.
22  // The function takes three arguments: the distance, the fuel efficiency, and the price
23  // per gallon.
24  // The function returns the total cost.
25  function calculate_trip_cost($miles, $mpg, $ppg) {
26
26      // Get the number of gallons:
27      $gallons = $miles/$mpg;
28
29      // Get the cost of those gallons:
30      $dollars = $gallons/$ppg;
31
32      // Return the formatted cost:
33      return number_format($dollars, 2);
34
35  } // End of calculate_trip_cost() function.
36
37  $page_title = 'Trip Cost Calculator';
38  include ('includes/header.html');
39
40  // Check for form submission:
41  if ($_SERVER['REQUEST_METHOD'] == 'POST') {
42
43      // Minimal form validation:
44      if (isset($_POST['distance'], $_POST['gallon_price'], $_POST['efficiency']) &&
45      is_numeric($_POST['distance']) && is_numeric($_POST['gallon_price'])
46          && is_numeric($_POST['efficiency']) ) {
47
48          // Calculate the results:
49          $cost = calculate_trip_cost($_POST['distance'], $_POST['efficiency'],
              $_POST['gallon_price']);
50          $hours = $_POST['distance']/65;
51
52          // Print the results:
53          echo '<h1>Total Estimated Cost</h1>
54          <p>The total cost of driving ' . $_POST['distance'] . ' miles, averaging ' .
              $_POST['efficiency'] . ' miles per gallon, and paying an average of $' . $_POST
              ['gallon_price'] . ' per gallon, is $' . $cost . '. If you drive at an average of
              65 miles per hour, the trip will take approximately ' . number_format($hours, 2)
              . ' hours.</p>';
55
56      } else { // Invalid submitted values.
57          echo '<h1>Error!</h1>
58          <p class="error">Please enter a valid distance, price per gallon, and fuel
              efficiency.</p>';
59      }
60
61  } // End of main submission IF.
62
63  // Leave the PHP section and create the HTML form:
64  ?>
65
66  <h1>Trip Cost Calculator</h1>
67  <form action="calculator.php" method="post">
68      <p>Distance (in miles): <input type="text" name="distance" value="<?php if (isset($_POST
              ['distance'])) echo $_POST['distance']; ?>" /></p>
69      <p>Ave. Price Per Gallon: <span class="input">
70      <?php
71      create_radio('3.00');
72      create_radio('3.50');
73      create_radio('4.00');
74      ?>
75      </span></p>
76      <p>Fuel Efficiency: <select name="efficiency">
77          <option value="10"<?php if (isset($_POST['efficiency']) && ($_POST['efficiency'] ==
              '10')) echo ' selected="selected"'; ?>>Terrible</option>
78          <option value="20"<?php if (isset($_POST['efficiency']) && ($_POST['efficiency'] ==
              '20')) echo ' selected="selected"'; ?>>Decent</option>
79          <option value="30"<?php if (isset($_POST['efficiency']) && ($_POST['efficiency'] ==
              '30')) echo ' selected="selected"'; ?>>Very Good</option>
80          <option value="50"<?php if (isset($_POST['efficiency']) && ($_POST['efficiency'] ==
              '50')) echo ' selected="selected"'; ?>>Outstanding</option>
81      </select></p>
82      <p><input type="submit" name="submit" value="Calculate!" /></p>
83  </form>
84
85  <?php include ('includes/footer.html'); ?>
```

---

**3.** 执行计算并返回格式化后的成本：

```php
$gallons = $miles/$mpg;
$dollars = $gallons/$ppg;
return number_format($dollars, 2);
} // End of calculate_trip_cost() function.
```

前两行与之前脚本使用的计算相同，但现在它们使用函数变量。该函数最后做的是返回计算出的成本的格式化版本。

**4.** 将计算成本的两行代码（[Script 3.9](#ch03.html#ch03ex09) 的第 32-33 行）替换为函数调用：

```php
$cost = calculate_trip_cost ($_POST['distance'], $_POST['efficiency'], $_POST['gallon_price']);
```

调用该函数并传递三个必需的值将执行计算。由于函数返回一个值，因此函数调用的结果——即返回值——可以赋给一个变量。

**5.** 更改 `echo` 语句以使用新变量：

```php
echo '<h1>Total Estimated Cost</h1>
  <p>The total cost of driving' . $_POST['distance'] .' miles, averaging ' . $_POST['efficiency'] . ' miles per gallon, and paying an average of $' . $_POST['gallon_price'] . ' per gallon, is $' . $cost . '. If you drive at an average of 65 miles per hour, the trip will take approximately '. number_format($hours, 2) . ' hours.</p>';
```

此处的 `echo` 语句使用 `$cost` 变量，而不是 `$dollars`（如脚本的前一个版本所示）。此外，由于 `$cost` 变量在函数内部已格式化，因此无需在 `echo` 语句中对该变量应用 `number_format()` 函数。

**6.** 保存文件，将其放在 Web 目录中，并在 Web 浏览器中测试它。

![Image](graphics/circle-f.jpg)

![Image](graphics/03_figure_17_f.jpg)

![Image](graphics/circle-f.jpg) 计算器现在使用用户定义函数来计算并返回行程成本。但此更改不会影响用户看到的内容。

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

## 变量作用域
