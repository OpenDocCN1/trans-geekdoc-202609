

```php
if(is_string($unfiltered_value))
{
    return $unfiltered_value;
}
```

print_r(array_filter($first_array, "filter_array"));

# 输出:

Array (
[first_name] => Pete
[last_name] => Smith
[address] => 123 Main Street
[city] => Atlanta
[state] => GA
)

此示例将过滤掉所有非字符串的空值。

如果没有提供函数，它将过滤掉空字符串、NULL 或 FALSE。

# 示例:

```php
$first_array = array('first_name' => ' ', 'last_name' => NULL , 'address' => FALSE , 'city' => 'Atlanta', 'state' => 'GA', 'zip' => 30001);
```

```php
print_r(array_filter($first_array));
```

# 输出:

Array (
[city] => Atlanta
[state] => GA
[zip] => 30001
)

可以使用 PHP 比较函数来代替用户自定义函数。这些函数包括 strcmp、strcasecmp、strncasecmp、substrcmp 或其他返回结果为 < 0、0 或 > 0 的 PHP 比较函数。

# array_flip — 返回数组中所有的键及其关联的值

“array_flip() 返回一个翻转顺序的数组，即数组的键变为值，而数组的值变为键。”

语法:

```php
array array_flip ($array)
```

# 示例:

```php
$first_array = array('first_name' => 'Pete', 'last_name' => 'Smith', 'address' => '123 Main Street', 'city' => 'Atlanta', 'state' => 'GA', 'zip_code' => 30001);
```

```php
$result = array_flip($first_array);
```

```php
print_r($result);
```

输出:

```
Array (
    [Pete] => first_name
    [Smith] => last_name
    [123 Main Street] => address
    [Atlanta] => city
    [GA] => state
    [30001] => zip_code
)
```

在此示例中，数组 $first_array 的键和值被反转了。

# array_pad — 用指定的值填充数组到指定的长度

array_pad() 返回数组的副本，该副本根据 `size` 指定的大小用 `value` 值进行填充。如果 `size` 为正，则在数组右侧填充；如果是负数，则在左侧填充。

# 语法:

```php
array array_pad ( array $array, int $size , mixed $value )
```

# 示例:

```php
$first_array = array('Pete', 'Smith', '123 Main Street', 'Atlanta', 'GA', '30001');
$second_array = array('Sally', 'Parisi', '101 South Street', 'Atlanta', 'GA', '30001');
```

```php
$first_array = array_pad($first_array, 8, "No Value");
$second_array = array_pad($second_array, -8, "No Value");
```

```php
print_r($first_array);
print_r($second_array);
```

# 输出:

```
Array (
[0] => Pete
[1] => Smith
[2] => 123 Main Street
[3] => Atlanta
[4] => GA
[5] => 30001
[6] => No Value
[7] => No Value
)
```

```
Array (
[0] => No Value
[1] => No Value
[2] => Sally
[3] => Parisi
[4] => 101 South Street
[5] => Atlanta
[6] => GA
[7] => 30001
)
```

first_array 在数组末尾增加了两个元素。原始数组长度为 6，填充大小为 8，因此创建了两个额外位置。second_array 在数组开头增加了两个元素。填充大小为 -8。

# array_pop — 弹出数组末尾的元素

“array_pop() 弹出并返回数组的最后一个值，使数组缩短一个元素。”

# 语法:

```php
mixed array_pop ( array &$array )
```

# 示例:

```php
$first_array = array('Pete', 'Smith', '123 Main Street', 'Atlanta', 'GA', '30001');
```

```php
print array_pop($first_array);
```

```php
print_r($first_array);
```

输出:

30001
Array (
[0] => Pete
[1] => Smith
[2] => 123 Main Street
[3] => Atlanta
[4] => GA
)

first_array 的最后一个元素已从数组取出并打印。数组大小比原来减少了。

# array_push — 将一个或多个元素推入数组末尾

“array_push() 将数组视为栈，并将传递的变量推入数组末尾。数组的长度增加了变量的数量。”

# 语法:

```php
int array_push ( array &$array, mixed $value1 [, mixed ...] )
```

# 示例:

```php
$customer_record = array(
    array('Pete', 'Smith', '123 Main Street', 'Atlanta', 'GA', 30001),
    array('Sally', 'Parisi', '101 South Street', 'Atlanta', 'GA', 30001)
);
```

```php
$customer_info = array('Happy', '111 North Street', 'Atlanta', 'GA', 30001);
```

```php
array_push($customer_record, $customer_info);
```

```php
print_r($customer_record);
```

# 输出:

Array (
[0] => Array (
[0] => Pete
[1] => Smith
[2] => 123 Main Street
[3] => Atlanta
[4] => GA
[5] => 30001
)
[1] => Array (
[0] => Sally
[1] => Parisi
[2] => 101 South Street
[3] => Atlanta
[4] => GA
[5] => 30001
)
[2] => Array (
[0] => Happy
[1] => 111 North Street
[2] => Atlanta
[3] => GA
[4] => 30001
)
)

array_push 将数组添加到现有数组的末尾。

# array_shift — 移出数组开头的元素

“array_shift() 移出并返回数组的第一个值，使数组缩短一个元素并将后续向下移动。所有数字键将从零开始修改，而字面键不受影响。”

# 语法:

```php
mixed array_shift ( array &$array )
```

$first_array = array('first_name' => 'Pete', 'last_name' => 'Smith', 'address' => '123 Main Street', 'city' => 'Atlanta', 'state' => 'GA', 'zip_code' => 30001);

$second_array = array('Sally', 'Parisi', '101 South Street', 'Atlanta', 'GA', 30001);

```php
array_shift($first_array);
```

```php
array_shift($second_array);
```

```php
print_r($first_array);
```

```php
print_r($second_array);
```

# 输出:

Array (
[last_name] => Smith
[address] => 123 Main Street
[city] => Atlanta
[state] => GA
[zip_code] => 30001
)

Array (
[0] => Parisi
[1] => 101 South Street
[2] => Atlanta
[3] => GA
[4] => 30001
)

$first_array 的 first_name 已从数组开头移除。在 $second_array 中，Sally 被移除且索引从 0 开始重新编号。

# array_shift — 将一个或多个元素插入到数组开头

“array_shift() 将元素插入到数组前面。注意元素列表是作为一个整体插入的，以确保插入的元素保持原有顺序。所有数字键将从零开始计数，而字面键不受影响。”

语法:

```php
int array_shift ( array &$array, mixed $value1 [, mixed ... ] )
```

# 示例:

```php
$first_array = array('Pete', 'Smith', '123 Main Street', 'Atlanta', 'CA', 30001);
```

```php
print(array_shift($first_array, "770-777-7777", "adm@no.co"));
```

```php
print_r($first_array);
```

输出:

8

Array (
[0] => 770-777-7777
[1] => adm@no.co
[2] => Pete
[3] => Smith
[4] => 123 Main Street
[5] => Atlanta
[6] => CA
[7] => 30001
)

array_unshift 将项追加到数组开头。该函数返回数组的新大小。在此示例中，$first_array 在开头增加了两个项。

# compact — 创建包含变量及其值的数组

语法:

```php
array compact ( mixed $varname1 [, mixed ...] ]
```

# 示例: (注：此处原文为 array compact，但根据上下文应为 compact 且示例中为 $zip_code = 30001; 之后)

```php
$first_name = "Pete";
$last_name = "Smith";
$address = "123 Main Street";
$city = "Atlanta";
$state = "GA";
$zip_code = 30001;
```

```php
$keys = array("first_name", "last_name", "address", "city", "state", "zip_code");
```

```php
$first_array = compact($keys);
```

```php
print_r($first_array);
```

# 输出:

Array (
[first_name] => Pete
[last_name] => Smith
[address] => 123 Main Street
[city] => Atlanta
[state] => GA
[zip_code] => 30001
)

compact 从传递的现有变量名构建数组。它使用变量名作为键创建一个关联数组。在此示例中，传入了一个变量名数组，它提取变量中的值并创建所示数组。如果变量不存在，则将忽略它。

# range — 创建包含范围元素的数组

# 语法:

```php
array range ( mixed $start , mixed $end [, number $step = 1 ] )
```

# 示例:

```php
print_r(range(1,10));
```

# 输出:

Array (
[0] => 1
[1] => 2
[2] => 3
[3] => 4
[4] => 5
[5] => 6
[6] => 7
[7] => 8
[8] => 9
[9] => 10
)

