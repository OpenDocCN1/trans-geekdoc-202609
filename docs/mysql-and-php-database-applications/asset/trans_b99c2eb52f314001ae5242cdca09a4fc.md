

```php
$str = "my little text string";
strstr($str, "text");
```

```php
$str = "my little text string";
if (strstr($str
```但但在下面的示例中，没有找到字符串，因此函数将返回 FALSE 且不会打印任何内容。

```php
$str = "my little text string";
$new_str = strstr($str, "nothing");
if($new_str)
{
    echo "nothing to print"; // 这不会被打印
}
```

值得注意的是，在你在编程过程中创建的函数通常需要返回 TRUE 或 FALSE 值。你可以通过返回 TRUE 或 FALSE，或者如果你愿意的话，返回 1 或 0 来创建函数。如果你不知道如何使用它们，请参阅第 6 章节关于函数的概述。请看这个示例：

```php
// 测试变量是否以 "http://" 开头
function url_test($url)
{
    if (strtolower(substr($url,0,7))=="http://")
    {
        return TRUE; // 这也可以是 1
    }
    else {
        return FALSE; // 可以是 0
    }
}
```

```php
$myurl = "http://www.theonion.com";
if (url_test ($myurl))
{
    echo "Thanks for entering a valid URL.";
```

## 第二部分：使用 PHP

## 比较运算符

PHP 中的比较运算符并不多。表 5-1 列出了它们。

表 5-1 PHP 比较运算符

| 符号 | 运算符 | 描述 |
| --- | --- | --- |
| == (两个符号) | 等于 | 确定两个数量是否相等。 |
| === (三个符号) | 相同 | 确定两个值是否相同且变量类型相同。 |
| != | 不等于 | 确定值是否不等。 |
| > | 大于 | 确定符号左侧的值是否大于右侧的值。 |
| < | 小于 | 确定符号左侧的值是否小于右侧的值。 |
| >= | 大于等于 | 确定左侧的值是否大于或等于右侧的值。 |
| <= | 小于等于 | 确定左侧的值是否小于或等于右侧的值。 |

## 逻辑运算符

除了比较运算符外，你将在脚本中使用逻辑运算符。表 5-2 列出了这些逻辑运算符。

表 5-2 PHP 逻辑运算符

| 符号 | 示例 | 描述 |
| --- | --- | --- |
| and | if ($a ==0 and $b==1) | 检查两个条件。 |
| && | if ($a ==0 && $b==1) | 与上一行相同，但优先级更高（见下文注释）。 |

## 第 5 章：控制结构 99

| 符号 | 示例 | 描述 |
| --- | --- | --- |
| or | if ($a ==0 or $b ==1) | 确定其中一个是否满足条件。 |
| || | if ($a ==0 || $b==1) | 与上一行相同，但优先级更高（见下文注释） |
| xor | if ($a ==0 xor $b==1) | 这被称为“异或”。确定两个中是否为一个真但并非全为。如果这两个条件都为真，整个测试将为假。 |
| ! | if (!empty($a)) | 确定某事并非如此。在本示例中，如果 $a 有值，则条件为真。 |

![](img/245156cc77092986aede93f131_0.png)

`&&` 和 `||` 之间的区别在于它们的优先级。PHP 必须先确定哪些运算符优先。你可以在列表中找到：[http://www.php.net/manual/language/operators.precedence.php](http://www.php.net/manual/language/operators.precedence.php)。

## 复杂的 if 语句

使用表 5-1 和 5-2 中的运算符，可以创建比本章开头的基础语句稍微复杂的语句。这里有几个示例：

```php
if ($var == 1 && $var <= 5 && !empty($var)) {
    // 执行一些操作
}
```

由于我们正在处理数据库，我们将展示当测试选择查询是否返回了任何行时，可以使用以下 if 语句：

```php
$query = "select * from my_table";
$result = mysql_query($query) or
die(mysql_error());
if (mysql_num_rows($result) > 0) {
    // 在这里执行某些操作。
}
```

类似的结构适用于 update 和 delete 语句：

```php
$query = "update myfile set coll='my text' where id = 1";
mysql_query($query) or die(mysql_error());
if (mysql_affected_rows() == 0) {
    echo "query did nothing";
}
```

## if ... else 语句

如果你对前面的部分很清楚，这里没有什么会让你惊讶的。`if... else` 语句允许你在指定条件为假时执行代码。

```php
$a = 2;
if ($a == 1) {
    echo "it's equal";
} else {
    echo "it is not equal";
}
```

这段代码将打印 "it is not equal"。

## if ... elseif 语句

你经常需要对变量进行一组检查。例如，你可能有一个页面，用于插入、编辑和删除数据库中的记录。通常做法是在 HTML 表单中提交时，提交按钮的值可以通过多个 `elseif` 语句进行检查，以指示要运行脚本的哪个部分：

```php
if ($submit == "edit")
    // 编辑数据库的代码
} elseif ($submit == "update") 
{
    // 更新记录的代码
} elseif ($submit == "delete")
{
    // 删除记录的代码
} else 
{
    echo "I have no idea what I should be doing.";
}
```

"else'" 不是 "else"。如果你在单词之间有空格，不会得到错误，但可能会得到奇怪的行为。

## 替代 if... 结构

编写语句有几种不同的方法。第一种是用冒号替换左大括号，用分号替换右大括号。这种语法已经过时了。你最好不要使用它。

```php
if ($a==1):
    echo "I knew a was equal to one.";
elif ($a>1):
    echo "a is a bigger than I thought.";
else:
    echo "a is a little number."
endif;
```

另一种替代 if 结构被称为三元运算符。它本质上是 `if ... else` 语句的简化形式。

```php
$result = (condition) ? "true" : "false";
```

## switch ... case

`switch` 结构是多个 `if else` 语句的替代方案，但在某些情况下，`switch` 可以帮助你消除复杂的语法。例如，如果 $submit 等于 "insert"：

```php
switch ($submit) {
  case "insert":
    // 插入数据库的代码
    break;
  case "update":
    // 更新数据库的代码
    break;
  case "display":
    // 显示的代码
    break;
}
```

## 循环

无论你过去使用过什么语言，你都知道循环是编程的重要部分。PHP 拥有丰富的循环满足所有的编程需求。

### while...

这是最常见的循环，因此我们先讨论它。你给 while 循环一个需要验证的条件。只要该条件为真，大括号内的代码就会执行。

```php
while (condition)
{
  //在这里执行代码;
}
```

对于一个非常基本的示例，以下代码将打印 0 到 10 之间的所有数字：

```php
$a = 0;
while ($a<=10)
{
  echo "$a <br> \n";
  $a++;
}
```

对于更实用的东西，你将使用 while 循环遍历数据库查询返回的每一行。因为如果没有行可供提取，`mysql_fetch_array()` 将返回 FALSE，所以它与 `while...` 循环配合得很好。

```php
$query = "select fname, lname from people";
$result = mysql_query($query) or
die(mysql_error());
while ($row = mysql_fetch_array($result))
{
  echo $row["fname"] . ", " . $row["lname"] . "<br> \n";
}
```

