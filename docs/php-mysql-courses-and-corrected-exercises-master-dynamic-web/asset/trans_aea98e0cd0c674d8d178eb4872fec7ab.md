
echo "<pre>";
print_r($fruits);
echo "</pre>";
?>

在这个示例中，`$fruits` 数组按升序排列，结果为：

```
Array
(
    [0] => apple
    [1] => banana
    [2] => orange
    [3] => strawberry
)
```

- **array_push()** 函数用于在数组末尾添加一个或多个元素。它直接就地修改数组，并返回数组中元素的新数量。示例如下：

```php
<?php

$fruits = ["orange", "apple", "banana", "strawberry"];
array_push($fruits, "Pineapple", "kiwi");

echo "<pre>";
print_r($fruits);
echo "</pre>";

?>
```

在这个示例中，元素 "Pineapple" 和 "kiwi" 被追加到数组 `$fruits` 的末尾，结果为：

`array_pop()` 函数删除数组的最后一个元素并返回该元素。它直接修改当前数组。示例如下：

```php
<?php
$fruits = ["orange", "apple", "banana", "strawberry"];
$last_fruit = array_pop($fruits);
echo "The last fruit was: ". $last_fruit ."<br>";
echo "<pre>";
print_r($fruits);
echo "</pre>";
?>
```

在这个示例中，**array_pop()** 函数删除 `$fruits` 数组的最后一个元素（即 "strawberry"）。变量 `$last_fruit` 现在包含值 "strawberry"，数组 `$fruits` 修改如下：

![](img/caba2aa22f5409ba73dea47176330677_248_0.png)

- **array_slice()** 函数根据指定参数返回给定数组的一部分。它不修改原始数组，而是返回包含所选元素的新数组。

以下是 array_slice() 函数的一般语法：

```php
array_slice($array, $start, $length = null, $preserve_keys = false)
```

- `$array`: 要从中提取一部分的原始数组。
- `$start`: 开始提取元素的索引。
- `$length`: 要提取的元素数量。如果省略此参数，则将包含从 `$start` 开始的所有元素。
- `$preserve_keys`: 一个布尔值，指示结果数组中是否应保留关联键。默认情况下，键将从零重新索引。

以下是使用 array_slice() 的示例：

```php
<?php
$fruits = ["apple", "banana", "orange", "strawberry", "pineapple"];
$portion = array_slice($fruits, 1, 3);

echo "<pre>";
print_r($portion);
echo "</pre>";
?>
```

此示例从索引 1（第二个元素 "banana"）开始提取 `$fruits` 数组的一部分，并包含接下来的三个元素。生成的数组 `$portion` 将包含元素 "banana"、"orange" 和 "strawberry"。请注意，原始 `$fruits` 数组未被修改。请注意，如果不指定要提取的元素数量，将提取从 `$start` 开始的所有元素。

```
Array
(
    [0] => banana
    [1] => orange
    [2] => strawberry
)
```

- **array_merge()** 函数用于将两个或多个数组合并为一个数组。它会考虑作为参数给出的数组，并返回一个包含源数组所有元素的新数组。

以下是 array_merge() 函数的一般语法：

| 函数 | 要合并的数组 | 输出类型 |
| --- | --- | --- |
| array_merge | $tab1, $tab2, ...$tabn | array |

**tab1, $tab2, ... $tabn**: 要合并的数组。您可以提供用逗号分隔的多个数组。

以下是使用 array_merge() 的示例：

```php
<?php
$tab1 = ["a" => "apple", "b" => "banana"];
$tab2 = ["c" => "orange", "d" => "strawberry"];
$tab3 = ["e" => "ananas"];

$result = array_merge($tab1, $tab2, $tab3);
echo "<pre>";
print_r($result);
echo "</pre>";
?>
```

在这个示例中，**array_merge()** 函数将数组 `$tab1`、`$tab2` 和 `$tab3` 合并为一个数组 `$result`。合并后的数组将包含源数组的所有元素；如果键是唯一的，则保留键，否则键将从零重新索引。执行此代码将产生以下结果：

```
Array
(
    [a] => apple
    [b] => banana
    [c] => orange
    [d] => strawberry
    [e] => ananas
)
```

- `array_key_exists()` 函数用于检查给定数组中是否存在特定键。如果键存在，则返回 true；否则返回 false。

array_key_exists() 函数的语法如下：

`array_key_exists($key, array $tab): bool`

key：要在表格中搜索的键。

$tab：要在其中搜索键的表格。

以下是使用 array_key_exists() 的示例：

```php
<?php

$person = [
    "lastname" => "Dupont",
    "firstname" => "John",
    "age" => 30
];

if (array_key_exists("firstname", $person)) {
    echo "The key 'firstname' exists in the array person.";
} else {
    echo "The key 'firstname' does not exist in the array person.";
}
?>
```

在这个示例中，array_key_exists() 函数检查键 "firstname" 是否存在于 `$person` 数组中。由于数组中存在键 "firstname"，条件为 true，因此将显示消息 "The key 'firstname' exists in the array person."。

- `array_replace()` 函数用一个或多个其他数组的元素替换数组的元素。它将第一个数组中现有的键值替换为替换数组中对应的值，并添加不存在的键。

array_replace() 函数的语法如下：

![](img/caba2aa22f5409ba73dea47176330677_255_0.png)

$tab1：要替换其元素的数组。

$tab2, $Other_arrays：替换数组。您可以指定所需数量的数组。

该函数返回一个包含更新元素的新数组。

以下是使用 array_replace() 的示例：

```php
<?php
$array1 = ["a" => "red", "b" => "green", "c" => "blue"];
$array2 = ["b" => "yellow", "d" => "orange"];
$new_array = array_replace($array1, $array2);
echo "<pre>";
print_r($new_array);
echo "</pre>";
?>
```

在这个示例中，数组 `$array1` 被 `$array2` 数组中的值替换。`$array1` 和 `$array2` 中的 "b" 键都存在，因此 `$new_array` 中键 "b" 的值将被 `$array2` 中的值替换。键 "a"、"c" 和 "d" 仅存在于其中一个数组中，因此它们将被添加到 `$new_array`。

```
Array
(
    [a] => red
    [b] => yellow
    [c] => blue
    [d] => orange
)
```

## 日期和时间函数

在 PHP 中，有许多内置函数可方便地操作日期和时间。这些函数可用于格式化日期、对日期执行算术运算、计算两个日期之间的差值等。

以下是一些用于处理日期和时间的最常用函数：

- **date(format, timestamp) 函数**：返回表示当前日期和时间，或由 timestamp 指定的日期和时间的格式化字符串。format 参数定义输出字符串的格式，而 timestamp 参数（可选）指定用作转换基础的 Unix 时间戳。如果未提供 timestamp 参数，则函数使用当前时间戳。

```php
<?php
// Gets the current date in "d-m-Y H:i:s" format
$currentDate = date("d-m-Y H:i:s");
echo $currentDate . "<br>";
// Gets current date in "d/m/Y" format
$currentDate2 = date("d/m/Y");
echo $currentDate2 . "<br>";
?>
```

在这些示例中，**date()** 函数用于格式化当前日期。如果运行此代码，您将得到类似于以下的结果：

![](img/caba2aa22f5409ba73dea47176330677_259_0.png)

- `getdate()` 函数返回一个包含当前日期信息的关联数组。示例如下：

```php
<?php
    $currentdate = getdate();

echo "<pre>";
print_r($currentdate);
echo "</pre>";
?>
```

