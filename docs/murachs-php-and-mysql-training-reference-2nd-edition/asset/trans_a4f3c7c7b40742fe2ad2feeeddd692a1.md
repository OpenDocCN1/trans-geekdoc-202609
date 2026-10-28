
## 用于对数组执行数学计算的函数

| 函数 | 描述 |
|---|---|
| `array_sum($array)` | 返回 `$array` 中元素的总和。 |
| `array_product($array)` | 返回 `$array` 中元素的乘积。 |

### 如何计算数组中所有值的总和

```php
$prices = array(141.95, 212.95, 411, 10.95);
$sum = array_sum($prices);                         // 776.85
```

## 用于搜索数组的函数

| 函数 | 描述 |
|---|---|
| `in_array($value, $array[, $strict])` | 如果 `$value` 存在于 `$array` 中，则返回 TRUE。如果 `$strict` 为 TRUE，则仅当数据类型也匹配时才返回 TRUE。 |
| `array_key_exists($key, $array)` | 如果 `$key` 被用作 `$array` 中的键，则返回 TRUE。 |
| `array_search($value, $array[, $strict])` | 如果 `$value` 存在于 `$array` 中，则返回对应的键；如果未找到，则返回 FALSE。`$strict` 参数的作用与 `in_array` 函数中的相同。 |
| `array_count_values($array)` | 统计 `$array` 中每个值被使用的次数。返回一个新数组，以值作为键，其值为该值出现的次数。 |

### 如何搜索数组

```php
$tax_rates = array('NC' => 7.75, 'CA' => 8.25, 'NY' => 8.875);
$is_found  = in_array(7.75, $tax_rates);             // TRUE
$is_found  = in_array('7.75', $tax_rates);           // TRUE
$is_found  = in_array('7.75', $tax_rates, true);     // FALSE
$key_exists = array_key_exists('CA', $tax_rates);    // TRUE
$key = array_search(7.75, $tax_rates);                // 'NC'
```

### 如何统计数组中某个值出现的次数

```php
$names = array('Mike', 'Mike', 'Mike', 'Anne', 'Joel', 'Joel');
$occurrences = array_count_values($names);
echo $occurrences['Mike'];                            // 3
echo $occurrences['Anne'];                            // 1
echo $occurrences['Joel'];                            // 2
```

*图 11-9 — 如何搜索数组并获取其元素的总和或乘积*

## 如何对数组进行排序

图 11-10 展示了如何使用函数对数组进行排序。数组排序函数的不同之处在于：是按升序还是降序排序，是保留键还是对数组重新索引，以及是按值还是按键排序。不过，所有排序函数都会修改原始数组。

排序函数还使用三个常量来控制排序期间的比较方式。默认情况下，SORT_REGULAR 常量使用关系运算符的常规类型转换规则来执行排序。大多数时候，该常量都能满足你的需求。但如果不行，你可以使用 SORT_STRING 常量在比较前将每个值转换为字符串。或者，可以使用 SORT_NUMERIC 常量在比较前将每个值转换为数字。

sort 函数按值升序对数组排序并重新索引数组。rsort 函数按值降序对数组排序并重新索引数组。这些函数通常用于整数索引的数组，如前三组示例所示。

asort 函数按值升序对数组排序并保留元素键。arsort 函数按值降序对数组排序并保留元素键。这些函数通常用于关联数组，如第四组示例所示。

ksort 函数按键升序对数组排序。krsort 函数按键降序对数组排序。两者在排序时都会保持键和值在一起。这些函数通常用于关联数组，如第四组示例所示。

## 用于修改数组的函数

| 函数 | 描述 |
|---|---|
| `array_unique($array[, $compare])` | 返回移除重复值后的 `$array`。`$compare` 参数的作用与排序函数中的相同，只是默认值为 `SORT_STRING`。 |
| `array_reverse($array [, $keys])` | 返回元素顺序反转后的 `$array`。如果 `keys` 为 `FALSE`（默认值），元素会被重新索引；否则使用原始键。 |
| `shuffle($array)` | 将 `$array` 中的值按随机顺序打乱。元素会被重新索引。 |
| `array_rand($array [, $count])` | 从 `$array` 中返回一个随机键。如果 `$count` 大于 1，则返回一个包含 `$count` 个随机键的数组。 |

### 如何修改数组

```php
$names = array('Mike', 'Mike', 'Mike', 'Anne', 'Joel', 'Joel');
$names = array_unique($names);                 // Mike, Anne, Joel
$names = array_reverse($names);                // Joel, Anne, Mike
shuffle($names);                               // Mike, Joel, Anne (for example)
```

### 如何修改关联数组

```php
$tax_rates = array('NC' => 7.75, 'NY' => 8.875, 'CA' => 8.25);
$tax_rates = array_reverse($tax_rates, true);
```

### 如何从数组中获取随机键

```php
$names = array('Mike', 'Anne', 'Joel', 'Ray', 'Pren');
$key = array_rand($names);                    // 2       (for example)
$names_rand = array_rand($names, 3);           // 0, 1, 3 (for example)
```

### 如何洗牌并发牌

```php
// Create the deck of cards
$faces = array('2', '3', '4', '5', '6', '7', '8',
               '9', 'T', 'J', 'Q', 'K', 'A');
$suits = array('h', 'd', 'c', 's');
$cards = array();
foreach($faces as $face) {
    foreach($suits as $suit) {
        $cards[] = $face . $suit;
    }
}

// Shuffle the deck and deal the cards
shuffle($cards);
$hand = array();
for ($i = 0; $i < 5; $i++) {
    $hand[] = array_pop($cards);
}
echo implode(',', $hand);                     // 9c,6d,Ks,4c,7h (for example)
```

*图 11-11 — 如何修改数组*

## 如何处理数组的数组

数组的数组，也称为二维数组，是一种每个元素都是另一个数组的数组。

### 理解数组的数组

图 11-12 提供了三张示意图，帮助你理解和直观认识数组的数组是如何工作的。第一张示意图展示了带整数索引的简单数组。这是你迄今为止在本章中使用的数组类型。每个元素显示为括号中的索引，位于阴影框内值的上方。在该数组中，每个元素的值都是一个字符串。

第二张示意图展示了一种二维数组，称为*矩形数组*。在这种情况下，所有嵌套数组的长度都相同。图中顶部的外层数组使用整数索引，嵌套数组使用字符串索引。你可以使用这样的矩形数组来存储表格数据。例如，这里的矩形数组存储了五个人的数据。

第三张示意图展示了另一种二维数组，称为*不规则数组*。在这种情况下，嵌套数组的长度不同。图中的外层数组使用字符串索引，而嵌套数组使用整数索引。虽然不规则数组不像矩形数组那样常用，但在某些情况下你可能需要使用它们。

虽然此图没有展示，但 PHP 还允许你创建*多维数组*，即将数组嵌套三层或更深。PHP 对数组嵌套深度没有技术限制，但应用程序的逻辑以及运行应用程序的 Web 服务器会对嵌套数组的深度造成实际限制。

### 简单数组

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_360_0.png)

### 矩形数组

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_360_1.png)

### 不规则数组

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_360_2.png)

### 说明

- 数组的数组，或二维数组，是一种元素也是数组的数组。
- 如果数组中的嵌套数组大小相同，则该数组称为矩形数组；如果嵌套数组大小不同，则该数组称为不规则数组。
