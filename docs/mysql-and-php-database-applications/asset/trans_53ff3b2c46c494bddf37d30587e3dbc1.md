

# 第二部分：使用 PHP

## 在 LIST() = EACH() 中使用 WHILE

在 ways `list() each()` 结构时，数组是另一个经常用到的地方。该结构将数组中的元素分配给命名的变量。它会遍历数组，当没有更多元素可以提取时，它将测试为 FALSE，循环随之停止。从数组中提取元素时，`list()` 期望一个关联数组并接收两个变量：第一个用于键，第二个用于值。

```php
$knicks = array (center => "Ewing", point => "Childs",
shooting_guard => "Houston",
forward => "Sprewell", strong_forward => "Johnson"
);
echo "<h2>尼克斯 1999 年首阵容是</h2>";
while (list($key,$value) = each ($knicks))
```

```php
echo "$key: $value <br>\n";
```

运行完之前的代码后，数组指针将位于数组的末尾。如果你想再次遍历它，必须使用 `reset` 将指针移到数组的开头。在前面的示例中，`reset ($knicks)` 即可生效。

![](img/245156cc770929860a3ede93c01f9981_136_0.png)

注意，如果你没有关联数组并想要获取数组值，你可能需要在 `list()` 中考虑这一点。通过在括号中包含一个逗号来实现。

```php
$names = array("John", "Jacob", "Jason", "Josh");
while (list ($value) = each ($names))
```

```php
echo "$value <br>\n";
```

如果你没有在 `$value` 前面加逗号，每个元素的顺序位置将被分配给 `value`，代码将打印 "0, 1, 2, 3.\n"。如果你想从关联数组中提取键，你的 `list` 语句应该包含像 `list($key, )` 这样的内容。

`List` 在 `mysql_fetch_array()` 中也非常有用。通过关联数组引用来不断引用值（例如 `$row["first_name"]`）可能会很麻烦。

# 第 5 章：控制结构

如果你使用 `list() = each()`，你就不需要将每条记录分配给变量并作为关联数组引用它。以下代码运行良好：

```php
$query = "select fname, lname from users";
$result = mysql_query($query) or
die(mysql_error());
while (list($fname, $lname) = each " . $lname . "<br>\n")) {
    echo $fname;
}
```

如你所知，`list()` 有几种用途。尽管我们正在通过 `each()` 语句来强调它，但它通常可以被认为是一个“数组析构函数”。也就是说，它从数组中提取元素。同样，`each()` 是一个“数组迭代器”，它遍历数组中的所有元素，它不需要配合 `list()` 使用，尽管这是目前最常见的用法。

继续使用循环处理 mysql 查询，你可能需要一段快速代码来打印查询结果。为了这一点，你需要一组嵌套循环。外层循环从数据库获取每条单独的记录。内层循环打印每个记录的内容。

```php
while($row = mysql_fetch_array($result, MYSQL_ASSOC)) {
    while (list($key, $value) = each ($row)) {
        echo "<b>$key:</b> \$value<br>\n";
    }
}
```

注意 `MYSQL_ASSOC` 的使用。如果你不使用，`mysql_fetch_array` 将返回两次每一列，一次使用顺序引用，一次使用关联键。

# 替代的 WHILE... 语法

如果你愿意，可以这样写一个 while 循环：

```php
while (condition) {
    // 在处编写代码
endwhile;
```

这也被废弃了。你最好不要使用它。

![](img/245156cc770929860a3ede93c01f9981_137_0.png)

# do ...while

`do...while` 循环与上面讨论的循环几乎相同。唯一的区别是条件在相关代码运行一次后进行测试。

```php
do
{
    // 在处使用使用的代码。
} while (condition);
```

这种结构对你可能有用。它甚至对你需要编写的脚本至关重要。但在编写本书的七个应用程序的过程中，我们一次也没有用到过它。

# for

`for` 循环接受三个表达式。第一个表达式仅在循环第一次时求值。第二个参数是一个条件，每次循环时都会求值；如果第二个参数中的条件测试为假，循环将结束。第三个表达式在第一次循环后的每次循环中都会执行。

例如，以下代码将遍历数组中的每个值并打印每个元素的值。

```php
$myarray = array(jay, bray, john, kristin);
for ($i = 0; $i < count($myarray); $i++))
{
  echo $myarray[$i] . "<br>\n";
}
```

第一次，$i$ 被赋值为 0，因此将打印数组中的第一个元素。下一次以及随后的每次，$i$ 都会加 1。

当 $i$ 等于数组长度时，循环将停止。如果你想从关联数组中提取键，你的 `list` 语句应该包含像 `list($key, )` 的内容。如果你没有关联数组并且想要获取数组值，你需要在你的 `list()` 中考虑这一点。通过在括号中包含一个逗号来实现。

```php
$names = array("John", "Jacob", "Jason", "Josh");
while (list ($value) = each ($names))
```

```php
echo "$value <br>\n";
```

如果你没有在 `$value` 前面加逗号，每个元素的顺序位置将被分配给 `value`，代码将打印 "0, 1, 2, 3.\n"。如果你想从关联数组中提取键，你的 `list` 语句应该包含像 `list($key, )` 这样的内容。

`List` 在 `mysql_fetch_array()` 中也非常有用。通过关联数组引用来不断引用值（例如 `$row["first_name"]`）可能会很麻烦。

如果你使用 `list() = each()`，你就不需要将每条记录分配给变量并作为关联数组引用它。以下代码运行良好：

```php
$query = "select fname, lname from users";
$result = mysql_query($query) or
die(mysql_error());
while (list($fname, $lname) = each " . $lname . "<br>\n")) {
    echo $fname;
}
```

如你所知，`list()` 有几种用途。尽管我们正在通过 `each()` 语句来强调它，但它通常可以被认为是一个“数组析构函数”。也就是说，它从数组中提取元素。同样，`each()` 是一个“数组迭代器”，它遍历数组中的所有元素，它不需要配合 `list()` 使用，尽管这是目前最常见的用法。

继续使用循环处理 mysql 查询，你可能需要一段快速代码来打印查询结果。为了这一点，你需要一组嵌套循环。外层循环从数据库获取每条单独的记录。内层循环打印每个记录的内容。

```php
while($row = mysql_fetch_array($result, MYSQL_ASSOC)) {
    while (list($key, $value) = each ($row)) {
        echo "<b>$key:</b> \$value<br>\n";
    }
}
```

注意 `MYSQL_ASSOC` 的使用。如果你不使用，`mysql_fetch_array` 将返回两次每一列，一次使用顺序引用，一次使用关联键。

# 替代的 WHILE... 语法

如果你愿意，可以这样写一个 while 循环：

```php
while (condition) {
    // 在处编写代码
endwhile;
```

这也被废弃了。你最好不要使用它。

![](img/245156cc770929860a3ede93c01f9981_137_0.png)

# do ...while

`do...while` 循环与上面讨论的循环几乎相同。唯一的区别是条件在相关代码运行一次后进行测试。

```php
do
{
    // 在处使用使用的代码。
} while (condition);
```

这种结构对你可能有用。它甚至对你需要编写的脚本至关重要。但在编写本书的七个应用程序过程中，我们一次也没有用到过它。

# for

`for` 循环接受三个表达式。第一个表达式仅在循环第一次时求值。第二个参数是一个条件，每次循环时都会求值；如果第二个参数中的条件测试为假，循环将结束。第三个表达式在第一次循环后的每次循环中都会执行。

例如，以下代码将遍历数组中的每个值并打印每个元素的值。

```php
$myarray = array(jay, bray, john, kristin);
for ($i = 0; $i < count($myarray); $i++))
{
  echo $myarray[$i] . "<br>\n";
}
```

第一次，$i$ 被赋值为 0，因此将打印数组中的第一个元素。下一次以及随后的每次，$i$ 都会加 1。当 $i$ 等于数组长度时，循环将停止。

