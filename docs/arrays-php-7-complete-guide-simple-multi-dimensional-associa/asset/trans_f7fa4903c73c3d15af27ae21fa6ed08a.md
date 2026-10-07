

```
[9] => 10
)
```

`range` 提供了一种为数组生成顺序值值的快速方法。

# 示例：

```
print_r(range('A', 'F'));
```

# 输出：

```
Array (
[0] => A
[1] => B
[2] => C
[3] => D
[4] => E
[5] => F
)
```

你并不局限于数值值。

# 示例：

```
print_r(range('F', 'A'));
```

# 输出：

```
Array (
[0] => F
[1] => E
[2] => D
[3] => C
[4] => B
[5] => A
)
```

你并不局限于升序排列。

# 数组的拆分与切片

array_chunk — 将数组拆分成多个块

“将数组分成若干具有 `size` 个元素的数组。最后一个块包含的元素可能少于 `size`。”

语法：

```
array_chunk ( array $array , int $size [, bool $preserve_keys = false )
```

示例：

```
$test_array = array('Jeff', 'Smith', '123 Main Street', 'Atlanta', 'GA', '30001');
```

```
print_r(array_chunk($test_array, 2));
```

输出：

Array

```
(
  [0] => Array
  (
    [0] => Jeff
    [1] => Smith
  )
```

```
[1] => Array
(
  [0] => 123 Main Street
  [1] => GA
)
```

```
[2] => Array
(
  [0] => 30001
)
```

)

向函数传递 `2` 将将原始数组拆分为一个包含 3 个元素的二维数组。

# 示例：

```
$test_array = array('Jeff', 'Smith', '123 Main Street', 'Atlanta', 'GA', '30001');
print_r(array_chunk($test_array, 2));
```

# 输出：

Array

```
([0] => Array
(
    [0] => Jeff
    [1] => Smith
)
([1] => Array
(
    [2] => 123 Main Street
    [3] => GA
)
([2] => Array
(
    [4] => 30001
)
```

在此示例中，原始键名（下标）保留在新的二维数组中。

**array_slice** 提取数组的切片

> “array_slice() 根据 `offset`（偏移量）和 `length`（长度）参数返回数组中的元素序列。”

# 语法：

```
array_slice ( array $array , int $offset [, int $length = NULL [, bool $preserve_keys = false ] ] )
```

# 示例：

```
$second_array = array('Sally', 'Parisi', '101 South Street', 'Atlanta', 'GA', 30001);
print_r(array_slice($second_array, 2));
print_r(array_slice($second_array, -2, 1));
print_r(array_slice($second_array, 0, 2));
print_r(array_slice($second_array, 2, -1, true));
```

# 输出：

```
Array (
[0] => 101 South Street
[1] => Atlanta
[2] => GA
[3] => 30001
)
Array (
[0] => GA
)
Array (
[0] => Sally
[1] => Parisi
)
Array (
[0] => 101 South Street
[1] => Atlanta
[2] => GA
```

) Array => (
[2] => 101 South Street
[3] => Atlanta
[4] => GA
)

仅传递一个 `2`，将返回从位置 2 开始的所有值（101 South Street, Atlanta, 30001）。

传递 `-2` 和 `1`，将从右侧而非左侧进行切片，从倒数第二个位置开始并返回一个值（GA）。

传递 `0` 和 `2`，将从位置 0 开始并返回两个值（Sally, Parisi）。

传递 `2` 和 `-1`，将从位置 2 开始并返回直到倒数第二个元素之前的所有项（101 South Street, Atlanta）。

传递 `2`, `-1`, `TRUE` 将返回与上一个示例相同的结果，但保留了原始索引。

array_splice — 移除数组的一部分并用其他内容替换

> “从输入数组中删除由 `offset` 和 `length` 指定的元素，如果提供了替换数组，则用替换数组中的元素替换它们。”

语法：

```
array_splice ( array &$input, int $offset, int $length = 0 [,n$replacement = array() ] )
```

示例：

```
$second_array = array('Sally', 'Parisi', '101 South Street', 'Atlanta', 'GA', 30001);
```

```
print_r(array_splice($second_array, 2));
print_r(array_splice($second_array, 0, 1));
```

# 输出：

```
Array (
[0] => 101 South Street
[1] => Atlanta
[2] => GA
[3] => 30001
)
Array (
[0] => Sally
)
```

在第一个示例中，传递了 `2`，要求保留 `$second_array` 数组中从索引 2（地址）开始的内容。在第二个示例中，传递了 `0` 和 `1`，表示应保留位置 0 和 1（姓名）。

# 数组排序

array_multisort — 对多个数组或多维数组进行排序

`array_multisort()` 可同时对多个数组，或通过一个或多个维度对多维数组进行排序。关联键（字符串）将被保留，但数字键将重新索引。

排序标志：

- SORT_REGULAR - 正常比较项目（不改变类型）
- SORT_NUMERIC - 以数值比较项目
- SORT_STRING - 将项目作为字符串比较
- SORT_LOCALE_STRING - 根据当前语言区域将项目作为字符串比较。可以使用 `setlocale()` 进行更改。
- SORT_NATURAL - 使用“自然排序”（如 `natsort`）比较项目
- SORT_CASE - 可以与 `SORT_STRING` 结合（按位运算）

语法：

```
array_multisort ( array &$array1, mixed $array1_sort = SORT_REGULAR, ... )
```

示例：

```
$first_array = array('Jeff', 'Smith', '123 Main Street', 'Atlanta', 'GA', '30001');
$second_array = array('Sally', 'Parisi', '101 South Street', 'Atlanta', 'GA', 30001);
```

```
array_multisort($first_array, SORT_ASC, $second_array, SORT_DESC);
```

```
print_r($first_array);
print_r($second_array);
```

输出：

Array (
[0] => 123 Main Street
[1] => 30001
[2] => Atlanta
[3] => GA
[4] => Pete
[5] => Smith
)

Array (
[0] => 101 South Street
[1] => 30001
[2] => Atlanta
[3] => GA
[4] => Sally
[5] => Parisi
)

在此示例中，`$first_array` 的值按升序排列，`$second_array` 的值按降序排列（数字 123, 30001）。

array_reverse — 返回一个反序的数组

“接收一个输入数组并返回一个顺序反转的新数组。”

```
Array (
[5] => 30001
[4] => GA
[3] => Atlanta
[2] => 101 South Street
[1] => Parisi
[0] => Sally
)
```

在此示例中，`$first_array` 的元素按反序返回。`$second_array` 也按反序返回。在第二个参数中传递 `TRUE` 时将保留原始数字索引。

arsort — 反序排序数组并保留索引

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

arsort 用于关联数组的值排序。它按反字母顺序对值进行排序。在此示例中，邮政编码因为是数字所以排在第一个。其余值按反序排列。键（下标）被保留。

