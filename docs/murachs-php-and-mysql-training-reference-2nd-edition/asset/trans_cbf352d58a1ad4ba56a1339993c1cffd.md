
## 如何使用 foreach 循环处理数组

foreach 循环通常用于处理关联数组。图 11-6 展示了这种类型的循环是如何工作的。

正如此图顶部的语法所示，foreach 循环不需要像 for 循环那样使用单独的表达式来初始化、测试和递增索引计数器。相反，你声明一个变量来存储数组中每个元素的值。此外，你还可以选择声明一个变量来存储每个元素的键。然后，在循环内部，你可以使用这些变量来处理数组中的每个元素。

第一个示例显示关联数组中的值。在这里，第一条语句创建了一个存储各州税率的关联数组。然后，代码使用 foreach 循环将全部三个元素的值作为无序列表中的列表项显示出来。

第二个示例的工作方式与第一个示例非常相似。但它同时显示关联数组的键和值。为此，foreach 循环使用箭头运算符（=>）来声明键和值的变量。在循环内部，代码使用这些变量来显示键和值。

第三个示例展示了如何使用 foreach 循环处理一个带有空隙的常规数组中的所有元素。这与图 11-3 中第四个示例完成了相同的任务。然而，如果你比较这两个示例的代码，我想你会同意，对于这个任务，foreach 循环比 for 循环更好。

### foreach 循环的语法

```php
foreach ($array_name as [ $key => ] $value) {
    // Statements that use $key and $value
}
```

### 显示关联数组中值的 foreach 循环

```php
$tax_rates = array('NC' => 7.75, 'CA' => 8.25, 'NY' => 8.875);
echo '<ul>';
foreach ($tax_rates as $rate) {
    echo '<li>$rate</li>';
}
echo '</ul>';
```

### 浏览器中显示的结果

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_348_0.png)

### 显示键和值的 foreach 循环

```php
$tax_rates = array('NC' => 7.75, 'CA' => 8.25, 'NY' => 8.875);
echo '<ul>';
foreach ($tax_rates as $state => $rate) {
    echo '<li>$state ($rate)</li>';
}
echo '</ul>';
```

### 浏览器中显示的结果

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_348_1.png)

### 显示常规数组中值的 foreach 循环

```php
$numbers = array(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
unset($numbers[2], $numbers[6]);
$numbers_string = '';
foreach($numbers as $number) {
    $numbers_string .= $number . ' ';
}
echo $numbers_string;                 // Displays: 1 2 4 5 6 8 9 10
```

### 说明

- 你可以使用 *foreach* 语句创建 *foreach 循环*，它只访问数组中已定义的元素。

图 11-6  如何使用 foreach 循环处理数组

## 用于创建数组的函数

| 函数 | 描述 |
|---|---|
| `range($lo, $hi [, $step])` | 返回一个数组，包含从 $lo 到 $hi 的值，以 $step 为步长递增得到下一个值。如果省略，$step 默认为 1。 |
| `array_fill($start, $count, $value)` | 返回一个数组，从索引 $start 开始包含 $count 个 $value 的副本。 |
| `array_pad($array, $size, $value)` | 返回一个数组，将 $value 添加到 $array 的末尾，直到数组包含 $size 个元素。如果 $size 为负数，则将该值添加到数组的开头。 |
| `array_merge($array1, $array2, ...)` | 返回一个数组，将两个或多个数组的元素合并到一个数组中。$array2 中的字符串键会覆盖 $array1 中的字符串键，但数字键会被追加。 |
| `array_slice($array, $index [, $len [, $keys]])` | 返回数组的一部分，从 $index 开始并包含 $len 个元素。如果省略 $len，则返回直到数组末尾的所有元素。如果 $keys 为 TRUE，则使用原始键。否则，切片从 0 开始重新索引。 |
| `array_splice($array, $index [, $len [, $new]])` | 修改 $array，从 $index 开始用 $new 中的元素替换其元素，替换 $len 个元素。数组会被重新索引。注意，此函数不返回数组，而是修改 $array 参数中的元素。 |

### 如何创建一个包含值范围的数组

```php
$numbers = range(1, 4);                  // 1, 2, 3, 4
$numbers = range(10, 22, 4);              // 10, 14, 18, 22
```

### 如何填充和补齐数组

```php
$numbers = array_fill(0, 5, 1);           // 1, 1, 1, 1, 1
$numbers = array_pad($numbers, 10, 0);    // 1, 1, 1, 1, 1, 0, 0, 0, 0, 0
```

### 如何合并两个数组

```php
$employees = array('Mike', 'Anne');
$new_hires = array('Ray', 'Pren');
$employees = array_merge($employees, $new_hires);
print_r($employees);
                         // Array ( [0] => Mike [1] => Anne [2] => Ray [3] => Pren )
```

### 如何截取数组的一部分

```php
$employees = array('Mike', 'Anne', 'Ray', 'Pren');
$new_hires = array_slice($employees, 2);
print_r($new_hires);             // Array ( [0] => Ray [1] => Pren )
```

### 如何拼接两个数组

```php
$employees = array('Mike', 'Anne', 'Joel');
$new_hires = array('Ray', 'Pren');
array_splice($employees, 1, 2, $new_hires);
print_r($employees);             // Array ( [0] => Mike [1] => Ray [2] => Pren )
```

图 11-7 — 如何填充、合并、截取和拼接数组

## 如何使用队列和堆栈

图 11-8 展示了四个函数，你可以使用它们处理两种特殊类型的数组：队列和堆栈。

一个 *堆栈* 实现了一个 *后进先出（LIFO）* 的值集合。你可以把堆栈想象成一叠盘子。你放到堆栈上的最后一个盘子，是你必须从堆栈上取下的第一个盘子。

第一个示例展示了如何使用堆栈。首先，第一条语句创建一个数组。然后，第二条语句使用 array_push 函数将一个值放入堆栈。接下来，第三条语句使用 array_pop 函数将该值从堆栈中取出。最后，第四条语句显示刚刚从堆栈中取出的值。

另一方面，一个 *队列* 实现了一个 *先进先出（FIFO）* 的值集合。你可以把队列想象成在银行里排成一队等待的人。队伍中的第一个人是第一个被服务并离开队伍的人。

第二个示例展示了如何使用队列。首先，第一条语句创建一个数组。然后，第二条语句使用 array_push 函数将一个值推入队列的末尾。接下来，第三条语句使用 array_shift 函数从队列开头移除该值，并将队列中的其余元素向前移动以占据其位置。最后，第四条语句显示刚刚从队列中移除的值。

在使用堆栈时，从数组的哪一侧添加和移除值并不重要，只要你始终使用数组的同一侧进行操作。本图中的示例使用 array_push 和 array_pop 函数操作数组的末尾。不过，你也可以使用 array_unshift 和 array_shift 函数操作数组的开头来实现堆栈。

类似地，在使用队列时，你总是向数组的一侧添加值，并从另一侧移除值。因此，你可以使用 array_push 和 array_shift 函数来创建队列。或者，也可以使用 array_unshift 和 array_pop 函数来创建队列。

在查看本图中的函数时，请注意它们会修改传递给函数的数组。换句话说，它们不会返回新数组。

## 如何获取元素的总和与乘积

图 11-9 展示了如何使用 array_sum 函数将数组中的元素相加。在第一个示例中，第一条语句创建一个包含四个价格的数组，第二条语句使用 array_sum 函数将全部四个价格加在一起。这以更少的代码完成了与图 11-3 中第三个示例相同的任务。

此图没有展示 array_product 函数的示例。不过，这个函数的工作方式与 array_sum 函数类似，只是它将值相乘而不是相加。

## 如何搜索数组

此图中的第二个表总结了用于搜索数组的函数。然后，第一个搜索示例展示了如何使用三个函数搜索数组。第一条语句创建一个包含三个具有键和值的元素的关联数组。第二条语句使用 in_array 函数搜索该数组，以检查它是否包含值 7.75。

第三条语句搜索数组中字符串值 “7.75”。默认情况下，in_array 函数使用相等运算符进行此比较。因此，它会在比较之前将值转换为相同的数据类型，并返回 TRUE 值。

第四条语句执行与第三条语句相同的比较，但它为第三个参数指定了 TRUE 值。因此，此语句使用全等运算符执行严格比较。由于这种比较不会在比较前转换数据类型，所以它返回 FALSE 值。

第五条语句使用 array_key_exists 函数检查数组中是否存在某个键。这里，‘CA’ 这个键存在于数组中，因此该语句返回 TRUE 值。

第六条语句使用 array_search 函数在数组中搜索值 7.75。如果未在数组中找到此值，该函数返回 FALSE 值。但是，如果找到此值，该函数将返回该值的键。相比之下，in_array 函数如果找到该值，则返回 TRUE 值。

第二个搜索示例展示了如何使用 array_count_values 函数统计数组中每个值出现的次数。这里，第一条语句创建一个包含六个值、但只有三个唯一值的数组。然后，第二条语句使用 array_count_values 函数返回一个关联数组，该数组统计原数组中每个值出现的次数。本图中的最后三条语句展示了这一点。
