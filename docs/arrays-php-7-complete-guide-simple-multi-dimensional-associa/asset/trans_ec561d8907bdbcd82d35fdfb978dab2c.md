
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

print_r(array_intersect_uassoc($first_array, $second_array, "key_compare", "value_compare"));

# 输出:

Array (
  [address] => 123 Main Street
  [city] => Atlanta
)
```

此函数需要用户提供键和值。PHP 函数会返回所用过的键和值（例如 `strncasecmp`）。用户提供的函数（除由于使用 `==` 而不是 `===` 导致的情况外）会精确匹配地返回键和值。在这个示例中，地址和城市是唯一的匹配项（键和值均匹配）。

 PHP 比较函数可以代替用户定义的函数。这些可以包括 `strcmp`、`strncasecmp`、`substrcmp` 或返回结果为 `< 0`、`0` 或 `>` 的其他 PHP 比较函数。

array_intersect_uassoc — 计算数组交集，通过回调函数比较数据

> “返回一个包含 array1 中所有在所有参数中都值的数组。”

语法：

```php
array_uintersect ( array $array1, array $array2 [, $... ], callable $value_compare_func )
```

示例：

```php
$first_array = array('first_name' => 'Pete', 'last_name' => 'Smith', 'address' => '123 Main Street', 'city' => 'Atlanta', 'state' => 'CA', 'zip_code' => 30001);

$second_array = array('firstname' => 'Pete', 'last_name' => 'Jones', 'address' => '123 Main Street', 'city' => 'Atlanta', 'state' => 'GA', 'zipcode' => 30001);

function value_compare($first_value, $second_value)
{
    if ($first_value == $second_value)
        return 0;
    else if ($first_value > $second_value)
        return 1;
    else
        return -1;
}

print_r(array_uintersect($first_array, $second_array, "value_compare"));
```

输出：

```php
Array (
    [first_name] => Pete
    [address] => 123 Main Street
    [city] => Atlanta
    [zip_code] => 30001
)
```

此函数将忽略键（下标）的差异。它使用用户提供的函数来比较值。如果值匹配，则返回来自第一个数组 (`$first_array`) 的键和值。

在这个示例中，返回了由于名字、地址、城市和邮政编码，因为它们存在于两个数组中，尽管每个数组中的键（下标）有所不同。

用户可以修改所示的比较（例如使用 `===` 代替 `==`）来确定什么是“相等”。该函数必须返回 `< 0`、`0` 和 `> 0` 的值。

```php
print_r(array_uintersect($first_array, $second_array, "strcmp"));
```

PHP 比较函数可以代替用户定义的函数。这些可以包括 `strcmp`、`strcasecmp`、`strnatcasecmp`、`substrcmp` 或其他返回结果为 `< 0`、`0` 或 `> 0` 的 PHP 比较函数。

# 合并数组

array_combine - 使用一个数组作为键，另一个数组作为值来创建一个数组

“使用键数组中的值作为键，使用值数组中的值作为对应的值创建一个数组。”

语法：

```php
array_combine ( array $keys , array $values )
```

示例：

```php
$first_names = array('Pete', 'Sally', 'Fred');
$last_names = array('Smith', 'Parisi', 'Jones');
$names = array_combine($last_names, $first_names);

print_r($names);
```

输出：

```php
Array
(
    [Smith] => Pete
    [Parisi] => Sally
    [Jones] => Fred
)
```

此示例使用 `$last_names` 数组填充键，使用 `$first_names` 数组填充值。

array_intersect_assoc — 计算带有额外索引检查的数组交集

“array_intersect_assoc() 返回一个包含 array1 中所有在所有数组中都存在的值的数组。注意，与 array_intersect() 不同，键也被用于比较。”

此函数比较数组并返回两个数组中共同有的部分。索引和值都必须相同。

语法：

```php
array_intersect_assoc ( array $array1, array $array2 [ , array ... ]
```

# 示例：

```php
$first_array = array('first_name' => 'Pete', 'last_name' => 'Smith', 'address' => '123 Main Street', 'city' => 'Atlanta', 'state' => 'GA', 'zip_code' => 30001);
$second_array = array('firstname' => 'Sally', 'lastname' => 'Parisi', 'address' => '101 South Street', 'city' => 'Atlanta', 'state' => 'GA', 'zipcode' => 30001);

$result_array = array_intersect_assoc($first_array, $second_array);

print_r($result_array);
```

# 输出：

```php
Array
[city] => Atlanta
[state] => GA
```

注意邮政编码没有被包含；因为索引不相同。只有城市和州在两个数组中是相同的。

array_intersect_key — 使用键比较数组的交集

array_intersect_key() 返回 array1 中在所有参数中都存在的条目。

# 语法：

```php
array_intersect_key ( array $array1, array $array2 [ , array ... ]
```

# 示例：

```php
$first_array = array('first_name' => 'Pete', 'last_name' => 'Smith', 'address' => '123 Main Street', 'city' => 'Atlanta', 'state' => 'GA', 'zip_code' => 30001);
$second_array = array('firstname' => 'Sally', 'lastname' => 'Parisi', 'address' => '101 South Street', 'city' => 'Atlanta', 'state' => 'GA', 'zipcode' => 30001);

$result_array = array_intersect_key($first_array, $second_array);

print_r($result_array);
```

# 输出：

```php
Array (
  [address] => 123 Main Street
  [city] => Atlanta
  [state] => GA
)
```

此函数仅比较键，并返回第一个数组中在第二个数组中匹配的键值对。在这个示例中，尽管每个数组中的值不同，但地址、城市和州的键是相同的。

