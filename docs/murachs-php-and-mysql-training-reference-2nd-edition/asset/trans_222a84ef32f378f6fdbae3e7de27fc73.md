
## 如何为参数提供默认值

图 13-4 显示了如何为函数的参数提供默认值。如果你为参数提供默认值，该参数就变为可选。然后，如果在调用函数时未传递参数，函数将使用该参数的默认值。

第一个示例为参数添加了默认值。为此，它在参数列表中参数后添加等号和默认值。这里，$type 参数的默认值为“coin”。因此，如果你没有向此参数传递参数，函数将使用“coin”的默认值。否则，函数将使用传递给函数的参数。

当你为默认值编码时，必须使用标量值或标量值的数组。*标量值* 是字符串字面量、数字字面量、布尔值或 NULL。换句话说，你不能使用表达式、函数调用或对象作为参数的默认值。

如果你需要提供更复杂的默认值，可以在参数列表中使用 NULL 作为占位符。然后，在函数体中，你可以使用 isset 函数来测试参数。如果未设置，你可以使用任何表达式初始化该参数。

第二个示例说明了这种技术。这里，is_leap_year 函数中的 $date 参数使用 NULL 作为默认值。然后，在函数内部，代码检查 $date 参数是否已设置。如果没有，代码将参数初始化为新的 DateTime 对象，其中包含当前日期和时间。这是必要的，因为你不能将新的 DateTime 对象用作参数的默认值。

当你混合必需参数和默认参数时，必须在参数列表中将默认参数放在任何必需参数之后，如第三个示例所示。这里，函数有一个必需参数和两个默认参数。因此，调用此函数的代码可以提供一个、两个或三个参数。

当你调用具有默认值的函数时，可以传递一些或全部可选参数。这由下一组示例说明。这里，第一个示例展示了如何使用其默认值调用函数。为此，这些语句省略了所有可选参数。

然后，下一个示例展示了如何调用函数并提供一些或全部可选参数。请注意，对 display_error 函数的调用仅为第一个默认参数提供值。因此，此函数仍使用 $class 参数的默认值。

### 如何为参数分配默认值

### 具有一个默认参数的函数

```php
function get_rand_bool_text($type = 'coin') {
    $rand = mt_rand(0, 1);
    switch ($type) {
        case 'coin':
            $result = ($rand == 1) ? 'heads' : 'tails';
            break;
        case 'switch':
            $result = ($rand == 1) ? 'on' : 'off';
            break;
    }
    return $result;
}
```

### 具有可选参数的函数

```php
function is_leap_year($date = NULL) {
    if (!isset($date)) {
        $date = new DateTime();
    }
    if ($date->format('L') == '1') return true;
    else return false;
}
```

### 具有一个必需参数和两个默认参数的函数

```php
function display_error($error, $tag = 'p', $class = 'error') {
    $opentag = '<' . $tag . ' class="' . $class . '">';
    $closetag = '</' . $tag . '>';
    echo $opentag, $error, $closetag;
}
```

### 使用默认参数值调用函数

### 省略可选参数

```php
echo get_rand_bool_text();             // Displays 'heads' or 'tails'
echo display_error('Out of range');     // 'p' tag with error class
$is_leap_year = is_leap_year();         // true or false based on current date
```

### 提供可选参数

```php
echo get_rand_bool_text('switch');                         // Displays 'on' or 'off'
echo display_error('Out of range', 'li');
$is_leap_year = is_leap_year(new DateTime('March 15, 2015')); // false
```

### 描述

- 要为参数提供默认值，请将参数名称后跟等号和默认值进行编码。默认值必须是标量值、标量值的数组或 NULL。*标量值* 是字面数字、字符串或布尔值。标量值不能包含运算符、变量或函数调用。
- 要编写为参数设置默认值的函数，请将 NULL 分配给参数。然后，在函数内部，你可以检查参数是否包含 NULL。如果是，你可以编写设置参数默认值的代码。

图 13-4 如何为参数提供默认值

## 用于处理可变长度参数列表的三个函数

| 函数 | 描述 |
|---|---|
| func_get_args() | 返回包含传递给函数的参数的数组。 |
| func_num_args() | 返回传递给函数的参数数量。 |
| func_get_arg($i) | 返回指定索引处的参数。 |

### 如何编写具有可变参数列表的函数

### 添加数字列表的函数

```
function add() {
    $numbers = func_get_args();
    $total = 0;
    foreach($numbers as $number) {
        $total += $number;
    }
    return $total;
}

$sum = add(5, 10, 15);     // $sum is 30
```

### 计算一个或多个数字的平均值的函数

```
function average($x) {          // $x is here to force at least one argument
    $count = func_num_args();
    $total = 0;
    for($i = 0; $i < $count; $i++) {
        $total += func_get_arg($i);
    }
    return $total / $count;
}

$avg = average(75, 95, 100);     // $avg is 90
```

### 使用可变参数列表的必需参数

```
function array_append(&$array, $x) {
    $values = func_get_args();    // Also contains $array
    array_shift($values);        // Removes $array from front
    foreach($values as $value) {
        $array[] = $value;
    }
}

$data = array('apples', 'oranges');
array_append($data, 'grapes', 'pears');
```

### 描述

- 可变长度参数列表让你创建可处理可变数量参数的函数。
- 你可以通过在参数列表中使用占位符参数来要求最小参数数量。

## 如何创建和使用函数库

应用程序通常有许多函数。在这种情况下，通常有助于将这些函数组织在外部库中。这有两个目的。首先，你可以对多个应用程序使用库。其次，你可以让不同的开发人员在不同的库上工作，以减少构建应用程序所需的时间。

### 函数库

图 13-6 显示了一个包含三个函数的库，让用户在 Web 应用程序中处理购物车。这些函数以“cart_”为前缀，以表明它们都是同一库的一部分。

首先，cart_add_item 函数将商品添加到购物车。这里，$cart 参数是一个存储购物车商品的数组。然后，接下来的三个参数指定要添加到购物车的商品的名称、成本和数量。在函数内部，第一条语句计算商品的总价。然后，下一个语句为商品创建关联数组。最后，最后一条语句将商品添加到购物车。

cart_update_item 函数更新购物车中的商品。这里，$cart 参数存储购物车的商品，$key 参数指定要更新的商品，$quantity 参数指定商品的新数量。在函数内部，代码使用键检查商品是否存在于购物车中。如果存在，代码检查数量是否小于或等于零。如果是，此代码将商品从购物车中移除。否则，它会更新商品的数量，计算商品的新总价并更新总价。

cart_get_subtotal 函数通过将购物车中每个商品的总价相加来获取购物车的小计。然后，它对数字进行四舍五入和格式化，使其显示两位小数。最后，它返回小计。

一旦你开发了函数库，你可以使用以下其中一个函数将该库加载到应用程序中：include、include_once、require 或 require_once。在大多数情况下，最好使用本图底部所示的 require_once 函数。这样，如果 PHP 找不到你需要的库，require_once 函数会抛出致命错误并立即停止执行。另一方面，如果库已经加载，此函数会防止它被加载两次，从而防止致命错误。

一旦本图底部的代码加载了库，它就会创建一个数组来存储购物车。然后，它调用库中的全部三个函数来添加商品、更新该商品并获取购物车的小计。最后，此代码显示购物车的小计。
