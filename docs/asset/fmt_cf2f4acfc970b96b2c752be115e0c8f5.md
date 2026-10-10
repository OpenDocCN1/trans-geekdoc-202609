
## 显示颜色 (red, blue)

```php
print("<PRE>");
print_r($colors);
print("<PRE>\n");
?>
```

## `boolean array_push(array stack, expression, ...)`

`array_push` 函数将一个或多个值添加到数组末尾。它将数组视为栈。使用 `array_pop` 从栈移除元素。`array_shift` 和 `array_unshift` 在开头操作。

```php
<?php
// 设置一个颜色名称数组
$colors = array("red", "blue", "green");
// 推入两个颜色名称
array_push($colors, "purple", "yellow");
// 打印所有值
(red, blue, green, purple, yellow)
print("<PRE>");
print_r($colors);
print("<PRE>\n");
?>
```

## `array array_reverse(array data)`

`array_reverse` 函数以反向顺序返回 `data` 参数。元素没有经过任何排序。它们只是处于相反顺序。

```php
<?php
//创建测试数据
$data = array(3, 1, 2, 7, 5);
// 反转顺序
$data = array_reverse($data);
// 按反向打印
//5, 7, 2, 1, 3
print("<PRE>");
print_r($data);
print("</PRE>\n");
?>
```

## `value array_shift(array stack)`

`array_shift` 函数返回数组的第一个元素，并将其移除。这允许你将数组视为栈。`array_unshift` 函数在开头添加元素。

```php
<?php
// 设置一个颜色名称数组
$colors = array("red", "blue", "green");
$firstColor = array_shift($colors);
// 打印 "red"
print($firstColor . "<BR>\n");
// 显示颜色 (blue, green)
print("<PRE>");
print_r($colors);
print("<PRE>\n");
?>
```

## `array array_slice(array data, integer start, integer stop)`

`array_slice` 函数返回数组的一部分，从由 `start` 参数指定的元素开始。如果为 `start` 指定一个负值，则起始位置将位于最后一个元素之前。可选的 `stop` 参数允许你指定返回多少个元素或在何处停止返回值。正值被视为返回元素的最大数量。负值 `stop` 值则用于从最后一个元素开始向后计数，以指定停止的位置。

将此函数与 `array_merge` 和 `array_slice` 进行比较。

```php
<?php
function printElement($element)
{
    print("$element<BR>\n");
}
// 设置一个颜色名称数组
$colors = array("red", "blue", "green", "purple", "cyan", "yellow");
// 获取由切片组成的新数组
// 从 "green" 到 "cyan"
$colors_slice = array_slice($colors, 2, 3);
// 打印所有值
array_walk($colors_slice, "printElement");
?>
```

## `array_splice(array data, integer start, integer stop, array insert_data)`

`array_splice` 移除数组的一部分并在此处插入另一个。数组是原地修改的，而不是返回。从由 `start` 参数指定的元素开始，继续删除元素直到达到 `stop` 指定元素。如果省略了 `stop`，则删除将持续到数组末尾。如果 `stop` 为负数，则它从数组末尾向后引用。你可以指定不删除任何值的 `start` 和 `stop` 值。例如，`stop` 值可以是正数且小于 `start`。这是使用 `array_splice` 插入数组而不删除任何元素的有效方法。

如果提供了作为 `insert_data` 参数传递的数组，则将替换插入到被删除元素的位置。声明该参数是可选的，因为你可能只想删除某些元素。如果你想向数组中插入单个元素，则不需要为 `insert_data` 提供数组。

## Core PHP 编程

将此函数与 `array_merge` 和 `array_slice` 进行比较。

```php
<?php
function printElement($element)
{
    print("$element<BR>\n");
}
// 设置一个颜色名称数组
$colors = array("red", "blue", "green",
    "yellow", "orange", "purple");
// 删除 green
array_splice($colors, 2, 2);
// 在 "blue" 之后插入 "pink"
array_splice($colors, 2, 0, "pink");
// 在 "orange" 和 "purple" 之间插入
// "cyan" 和 "black"
array_splice($colors, 4, 0, array("cyan", "black"));
// 打印所有值
array_walk($colors, "printElement");
?>
```

## `boolean array_unshift(array stack, expression, entry, ...)`

`array_unshift` 函数如果数组被视为栈，则向数组开头添加一个或多个值。使用 `array_shift` 从数组开头移除元素。将此函数与在数组末尾操作的 `array_pop` 和 `array_push` 进行比较。

```php
<?php
function printElement($element)
{
    print("$element<BR>\n");
}
// 设置一个颜色名称数组
$colors = array("red", "blue", "green");
// 推入两个颜色名称
array_unshift($colors, "purple", "yellow");
// 打印所有值
array_walk($colors, "printElement");
?>
```

IT-SC 书 229

## Core PHP 编程

## `array array_values(array data)`

`array_values` 函数仅返回数组元素，并用整数重新索引。

```php
<?php
// 设置一个颜色名称数组
$UserInfo = array("First Name"=>"Leon",
    "Last Name"=>"Atkinson",
    "Favorite Language"=>"PHP");
// 重新索引整数
$UserInfo = array_values($UserInfo);
// 打印所有值及其
// 新的索引
for($n=0; $n=count($UserInfo); $n++) {
    print("$n $UserInfo[$n]<BR\n");
}
?>
```

## `boolean array_walk(array data, string function)`

`array_walk` 函数在给定数组的每个元素上执行指定的函数。该函数必须恰好接收一个元素；否则将生成错误消息。数组元素将通过引用传递，因此指定函数对它们做的任何更改都将永久应用在数组中。指定的函数必须是你创建的，而不是 PHP内置函数。

```php
<?php
$colors = array("red", "blue", "green");
function printElement($element) {
    print("$element<BR\n");
}
array_walk($colors, "printElement");
?>
```

## `arsort(array unsorted_array)`

`asort` 函数根据其值反序对数组进行排序。索引会随值移动。这种排序适用于关联数组。第 15 章“排序、搜索和随机数”将深入讨论排序。

## Core PHP 编程

```php
<?php
// 构建数组
$users = array("bob"=>"Robert",
    "steve"=>"Stephen",
    "jon"=>"Jonathan");
// 排序数组
arsort($users);
// 打印值
for(reset($users); $index=key($users); next($users)) {
    print("$index : \$users[$index]\n");
}
?>
```

## `asort(array unsorted_array)`

`asort` 函数根据其值对数组进行反序排序。索引会随值移动。这种排序适用于关联数组。第 15 章“排序、搜索和随机数”将深入讨论排序。

```php
<?php
// 构建数组
$users = array("bob"=>"Robert",
    "steve"=>"Stephen",
    "jon"=>"Jonathan");
// 排序数组
arsort($users);
// 打印值
for(reset($users); $index=key($users); next($users)) {
    print("$index : \$users[$index]\n");
}
?>
```

## `array compact(...)`

`compact` 函数返回包含变量名和值的数组。可以传递任意数量的参数，它们会在当前作用域创建变量。此函数与 `extract` 互补。

图 9-4. compact.

```
Array (
  [name] => Leon
  [language] => PHP
  [color] => blue
)
```

## `integer count(variable)`

`count` 函数返回数组中的元素数量。如果变量从未设置，`count` 返回 0。如果变量不是数组，`count` 返回 1。

```php
<?php
$colors = array("red", "green", "blue");
print(count($colors));
?>
```

## `value current(arrayname)`

`current` 函数返回 PHP 内部指针指向的元素。`reset` 函数将指针移动到第一个元素。

```php
<?php
$colors = array("red", "green", "blue");
reset($colors);
print(current($colors));
?>
```

## `array each(arrayname)`

`each` 函数返回表示当前元素的数组。四个元素（0, 1, key, value）引用键和值。你可以反复使用 `each` 遍历整个数组，如下例。

```php
<?php
// 创建测试数据
$colors = array("red", "green", "blue");
// 遍历数组
// 输出类似于 "0 = red"
while(list($key, $value) = each($colors))
{
    print("$key<BR>\n");
}
?>
```

## `end(arrayname)`

`end` 函数将 PHP 内部指针移动到数组的最后一个元素。`reset` 函数将指针移动到第一个元素。

```php
<?php
$colors = array("red", "green", "blue");
end($colors);
?>
```

## Core PHP 编程

```php
print(current($colors));
?>
```

## `array explode(string delimiter, string data)`

`explode` 函数从字符串创建数组。分隔符参数将数据参数划分为元素。此函数安全用于二进制字符串。`implode` 函数将数组转换为字符串。

```php
<?php
/*
 ** 将制表符列表转换为数组
 */
$data = "red\tgreen\tblue";
$colors = explode("\t", $data);
```

## `extract(array variables, integer mode, string prefix)`

`extract` 函数根据变量在局部作用域中创建变量。不是以字符串索引的元素将被忽略。可选的 `mode` 参数控制变量如何覆盖或重命名以避免冲突。有效模式见表 9.1。如果省略，则假设为 `EXT_OVERWRITE` 模式。`prefix` 参数仅在使用 `EXT_PREFIX_SAME` 或 `EXT_PREFIX_ALL` 模式时才需要。如果使用，会在提取的变量名称前添加前缀和下划线。

```php
<?php
$new_variables = array('Name'=>'Leon', 'Language'=>'PHP');
$Language = 'English';
extract($new_variables, EXT_PREFIX_SAME, "collision");
// 打印提取的变量
print($Name) . "<BR\n";
print($collision_Language . "<BR\n");
?>
```

核心 PHP 编程

## `boolean型 in_array(value query, array data)`

如果查询参数 `query` 是数据参数 `data` 中的一个元素，则 `in_array` 函数返回 TRUE。

| 模式 | 描述 |
| --- | --- |
| EXTR_OVERWRITE | 覆盖任何同名的变量。 |
| EXTR_SKIP | 跳过任何同名的变量。 |
| EXTR_PREFIX_SAME | 为同名的变量添加前缀。 |
| EXTR_PREFIX_ALL | 为所有变量添加前缀。 |

```
// 测试用数据
$colors = array("red", "green", "blue");
// 检查是否存在 green
if (in_array("green", $colors)) {
    print("Yes, green is present!");
}
?>
```

## `string implode(array data, string delimeter)`

`implode` 函数将数组转换为字符串。元素之间通过分隔符（delimeter）连接。要执行相反的功能，请使用 `explode`。

```php
/*
** 将数组转换为逗号分隔的字符串
 */
$colors = array("red", "green", "blue");
$colors = implode(",", $colors);
print($colors);
?>
```

## `join`

你可以将 `join` 作为 `implode` 函数的别名。

IT-SC 书 235

### 核心 PHP 编程

## `value型 key(array arrayname)`

`key` 函数返回当前元素的索引。使用 `current` 查找当前元素的值。

```php
<?php
$colors = array("FF0000"=>"red",
    "00FF00"=>"green",
    "0000FF"=>"blue");
for(reset($colors); $key = key($colors); next($colors)) {
    print("$key is $colors[$key]<br>\n");
}
?>
```

## `boolean型 ksort(array data)`

`ksort` 函数按键的反向顺序对数组进行排序——即较大的值在前。元素值会随键一起移动。这主要是为了关联数组的方便，因为按整数索引的数组可以按照键的顺序轻松遍历。

```php
<?php
$colors = array("red"=>"FF0000",
    "green"=>"00FF00",
    "blue"=>"0000FF");
// 按键对数组进行排序
ksort($colors);
// 输出值
foreach($colors as $key=>$value) {
    print("$key : $value <br>\n");
}
?>
```

## `boolean型 ksort(array data)`

`ksort` 函数按键或索引值对数组进行排序。元素值会随键一起移动。这主要是为了关联数组的方便，因为按整数索引的数组可以按照键的顺序轻松遍历。

```php
<?php
$colors = array("red"=>"FF0000",
    "green"=>"00FF00",
    "blue"=>"0000FF");
// 按键对数组进行排序
ksort($colors);
// 再次按键对数组进行排序
ksort($colors);
// 输出值
foreach($colors as $key=>$value)
{
```
