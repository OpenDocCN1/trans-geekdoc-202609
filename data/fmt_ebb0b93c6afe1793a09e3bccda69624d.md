
“此函数对数组进行排序，使索引与其关联的元素保持一致。主要用于对实际元素顺序重要的关联数组。”

语法：

```
bool asort ( array &$array, int $sort_flags = SORT_REGULAR )
```

示例：

```php
$first_array = array('first_name' => 'Pete', 'last_name' => 'Smith', 'address' => '123 Main Street', 'city' => 'Atlanta', 'state' => 'CA', 'zip_code' => 30001);
```

```
arsort($first_array);
```

```
print_r($first_array);
```

输出：

Array (

[address] => 123 Main Street

[city] => Atlanta

[first_name] => Pete

[last_name] => Smith

[state] => CA

[zip_code] => 30001

)

`arsort` 用于关联数组的值排序。它按反字母顺序对值进行排序。在此示例中，邮政编码因为是数字所以排在第一个。其余值按反序排列。键（下标）被保留。

```
[state] => CA
[first_name] => Pete
[last_name] => Smith
[zip_code] => 30001
```

该函数用于关联数组以对值进行排序。它按字母顺序对值进行排序。在这个示例中，邮政编码列在最后，因为它是数值。其余值按字母顺序排列。键（下标）被保留。

### krsort — 按键反序对数组排序

> “按键反序对数组进行排序，保持键与数据之间的对应关系。这主要用于关联数组。”

### 语法：

```
bool krsort ( array &$array, int $sort_flags = SORT_REGULAR )
```

### 示例：

```
$first_array = array('first_name' => 'Pete', 'last_name' => 'Smith', 'address' => '123 Main Street', 'city' => 'Atlanta', 'state' => 'CA', 'zip_code' => 30001);
```

```
krsort($first_array);
print_r($first_array);
```

## 输出：

```
Array (
[zip_code] => 30001
[state] => CA
[last_name] => Smith
[first_name] => Pete
[city] => Atlanta
[address] => 123 Main Street
)
```

`ksort` 按字母反序键键排序。在这个示例中，`zip_code` 现在位于数组的第一位，`address` 在最后。

### ksort — 按键对数组排序

“按键对数组进行排序，保持键与数据之间的对应关系。这主要用于关联数组。”

### 语法：

```
bool ksort ( array &$array, int $sort_flags = SORT_REGULAR )
```

### 示例：

```
$first_array = array('first_name' => 'Pete', 'last_name' => 'Smith', 'address' => '123 Main Street', 'city' => 'Atlanta', 'state' => 'CA', 'zip_code' => 30001);
```

```
ksort($first_array);
print_r($first_array);
```

## 输出：

```
Array (
[address] => 123 Main Street
[city] => Atlanta
[first_name] => Pete
[last_name] => Smith
[state] => CA
[zip_code] => 30001
)
```

`ksort` 按字母顺序排序数组键。在这个示例中，`address` 现在位于数组的第一位，`zip_code` 在最后。

### natcasesort — 使用不区分大小写的“自然顺序”算法对数组进行排序

“此函数实现了一种排序算法，它按照人类的方式对字母数字字符串进行排序，同时保持键/值关联。这被称为‘自然排序’。”

### 语法：

```
bool natcasesort ( array &$array )
```

### 示例：

```
$name_array = array("Pete", "peter", "jones", "Jones");
```

```
natcasesort($name_array);
```

```
print_r($name_array);
```

## 输出：

```
Array (
[3] => Jones
[2] => jones
[0] => Pete
[1] => peter
)
```

`natcasesort` 以更符合人类的方式排列项目。在这个示例中，所有的 Jones 值都出现在任何 Peter 值之前。它忽略了大小写。

### natsort — 使用“自然顺序”算法对数组进行排序

“此函数实现了一种排序算法，它按照人类的方式对字母数字字符串进行排序，同时保持键/值关联。这被称为‘自然排序’。”

### 语法：

```
bool natsort ( array &$array )
```

### 示例：

```php
$name_array = array("Pete", "peter", "jones", "Jones");
```

```
natsort($name_array);
```

```
print_r($name_array);
```

## 输出：

```
Array (
[3] => Jones
[0] => Pete
[2] => jones
[1] => peter
)
```

`natsort` 以人类自然的方式排序数组。然而，它并没有忽略大小写。在上面的示例中，所有大写单词都出现在小写单词之前。但请注意键（下标）被保留了，与 `sort` 不同。

### rsort — 反序对数组排序

“此函数按反序对数组进行排序（从高到低）。”

### 语法：

```
bool rsort ( array &$array, int $sort_flags = SORT_REGULAR )
```

### 示例：

```php
$first_array = array('first_name' => 'Pete', 'last_name' => 'Smith', 'address' => '123 Main Street', 'city' => 'Atlanta', 'state' => 'CA', 'zip_code' => 30001);
```

```
rsort($first_array);
print_r($first_array);
```

## 输出：

```
Array (
[0] => 30001
[1] => Smith
[2] => Pete
[3] => CA
[4] => Atlanta
[5] => 123 Main Street
)
```

`rsort` 按反序对数组中的值。它不保留原始数组的键（下标）。

### shuffle — 打乱数组顺序

“此函数打乱数组中元素的顺序。”

### 语法：

```
bool shuffle ( array &$array )
```

### 示例：

```php
$first_array = array('first_name' => 'Pete', 'last_name' => 'Smith', 'address' => '123 Main Street', 'city' => 'Atlanta', 'state' => 'CA', 'zip_code' => 30001);
```

```
shuffle($first_array);
print_r($first_array);
```

## 输出：

```
Array (
[0] => CA
[1] => Pete
[2] => 123 Main Street
[3] => 30001
[4] => Smith
[5] => Atlanta
)
```

`shuffle` 随机打乱数组中的值。它不保留键（下标）。

### sort — 对数组进行排序

> “此函数按值进行排序。元素将从低到高对数组进行排序。”

### 语法：

```
bool sort ( array &$array, int $sort_flags = SORT_REGULAR )
```

### 示例：

```php
$first_array = array('first_name' => 'Pete', 'last_name' => 'Smith', 'address' => '123 Main Street', 'city' => 'Atlanta', 'state' => 'CA', 'zip_code' => 30001);
```

```
sort($first_array);
print_r($first_array);
```

## 输出：

```
Array (
[0] => 123 Main Street
[1] => Atlanta
[2] => CA
[3] => Pete
[4] => Smith
[5] => 30001
)
```

`sort` 按字母顺序排列值，它保留了键（下标）。

### usort — 使用自定义比较函数对数组进行排序

> “`usort` 使用用户提供的比较函数对数组的键进行排序。如果你需要根据某些非标准标准对关联数组进行排序，则应该使用此函数。”

### 语法：

```
bool usort ( array &$array , callable $value_compare )
```

### 示例：

```php
function value_compare($first_value, $second_value)
{
    if ($first_value == $second_value)
        return 0;
    else if ($first_value > $second_value)
        return 1;
    else
        return -1;
}
```

```
$first_array = array('first_name' => 'Pete', 'last_name' => 'Smith', 'address' => '123 Main Street', 'city' => 'Atlanta', 'state' => 'CA', 'zip_code' => 30001);
```

```
usort($first_array, 'value_compare');
```

```
print_r($first_array);
```

## 输出：

```
Array (
[address] => 123 Main Street
[city] => Atlanta
[state] => CA
[first_name] => Pete
[last_name] => Smith
[zip_code] => 30001
)
```

`uasort` 根据用户提供的函数对数组中的值进行升序排序，并保持键的关联。这主要用于需要根据特定标准进行排序的关联数组。

用户可以修改比较（例如使用 `===` 代替 `==`）来确定什么是“相等”。用户提供的函数必须返回小于 0、0 或大于 0 的值，如示例函数所示。

```
uasort($first_array, "strcmp");
print_r($first_array);
```

可以使用 PHP 比较函数代替自定义函数。这些可以包括 `strcmp`、`strcasecmp`、`strnatcasecmp`、`substrcmp` 或其他返回小于 0、0 或大于 0 结果的 PHP 比较函数

### uksort — 使用自定义比较函数按键对数组排序

“`uksort` 使用用户提供的比较函数对数组的键进行排序。如果你想要排序的数组需要根据某些复杂的标准进行排序，则应该使用此函数。”

### 语法：

```
bool uksort ( array &$Array , callable $key_compare )
```

### 示例：

```php
function key_compare($first_key, $second_key)
{
    if ($first_key == $second_key)
        return 0;
    else if ($first_key > $second_key)
        return 1;
    else
        return -1;
}
```

```
uksort($first_array, "key_compare");
print_r($first_array);
```

## 输出：

```
Array (
    [address] => 123 Main Street
    [city] => Atlanta
    [first_name] => Pete
    [last_name] => Smith
    [state] => CA
    [zip_code] => 30001
)
```

`uksort` 根据用户提供的比较对键（下标）对数组进行升序排序。

```php
if ($first_value == $second_value)
return 0;
else if ($first_value > $second_value)
return 1;
else
return -1;
}
```

```php
$first_array = array('first_name' => 'Pete', 'last_name' => 'Smith', 'address' => '123
Main Street', 'city' => 'Atlanta', 'state' => 'CA', 'zip_code' => 30001);
```

```php
usort($first_array, 'value_compare');
```

```php
print_r($first_array);
```

Output:

Array (
[0] => 123 Main Street
[1] => Atlanta
[2] => CA
[3] => Pete
[4] => Smith
[5] => 30001
)

`usort` 根据用户提供的函数对数组中每个元素的值进行升序排序，该函数用于评估值是否相等、大于或小于。数组的键（下标）不会按照原始数组的顺序保持。

用户可以修改此处所示的比较逻辑（例如使用 `===` 代替 `==`）来确定什么是“相等”。用户提供的函数必须返回一个小于 0、0 或大于 0 的值，如示例函数所示。

```php
usort($first_array, 'strcmp');
```

```php
print_r($first_array);
```

可以使用 PHP 比较函数代替用户自定义函数。这些函数包括 `strcmp`、`strcasecmp`、`strnatcasecmp`、`substrcasecmp` 或其它返回小于 0、0 或大于 0 的 PHP 比较函数。

# 练习

- 1. 创建一个 PHP 程序，其中包含一个包含班级所有学生姓名的数组。按姓氏的字母顺序对数组进行排序。同时也对数组进行反序排序。
- 2. 将第 1 题中的数组分为两个数组；一个包含名，另一个包含姓。

# 第 5 章 – PHP 函数 – 比较与合并数组

完成本章后，学生将能够……

- 创建一个简单的 PHP 程序，根据值、键或用户自定义函数比较两个数组。
- 创建一个简单的 PHP 程序，通过并集或交集合并两个数组。

在本章中，我们将简要查看比较和合并数组的 PHP 函数。许多此类函数适用于多种数组类型（单维、多维和/或关联数组）。

以下所有函数的描述均来自来自 www.php.net 上的在线 PHP 手册。文中还提供了每个函数的简要示例以及对这些示例结果的说明。这些示例仅用于让你初步了解。欲需获取所示函数的更详细描述和更多示例，请访问在线 PHP 手册。

## 比较数组

`array_diff_assoc` — 带有额外的索引检查，计算两个关联数组的差异

“比较 `array1` 和 `array2` 并返回差异。”

语法：

```
array_diff_assoc ( array $array1, array $array2 [, array $... ] )
```

示例：

```php
$first_array = array('first_name' => 'Pete', 'last_name' => 'Smith', 'address' => '123 Main Street', 'city' => 'Atlanta', 'state' => 'GA', 'zip_code' => 30001);
$second_array = array('first_name' => 'Sally', 'last_name' => 'Parisi', 'address' => '101 South Street', 'city' => 'Atlanta', 'state' => 'GA', 'zip_code' => 30001);
$difference = array_diff_assoc($first_array, $second_array);
print_r($difference);
```

Output:

```
Array
(
    [first_name] => Pete
    [last_name] => Smith
    [address] => 123 Main Street
)
```

此示例比较了 `$first_array` 和 `$second_array`。它返回第一个数组中不同的部分。

如果我们交换参数：

示例：

```php
```
