
使用 PCRE 函数的主要原因是它们让你在“贪婪”与“非贪婪”匹配之间做出选择。以下是一个快速示例，请看下面的字符串。

```
$str = "I want to match to here. But end up matching to here"
```

使用 ereg() 或 ereg_replace() 时，没有办法从“I”匹配到“here”的第一次出现。以下代码不会像你期望的那样工作：

```
$str = "I want to match to here. But end up matching to here";
$new_str = ereg_replace("I.*here", "Where", $str);
echo $new_str;
```

这将打印“Where”且没有其他内容。整个字符串将被替换。使用 ereg_replace() 没有办法指示你想要匹配到“here”的第一次出现。然而，使用 preg_replace()，你可以这样做：

```
$str = "I want to match to here. But end up matching to here";
$new_str = preg_replace("/I.*?here/", "Where", $str);
echo $new_str;
```

在此实例中，.*? 表示“匹配所有字符直到第一次出现”。

## 本书中使用的 PCRE 函数

### PREG_MATCH()

这与 ereg() 函数类似，因为你可以将可选的第三个参数赋值为匹配的子模式数组（如果在正则表达式中找到了）。preg_match 返回找到的模式匹配数，如果未找到则返回 False。

```
int preg_match (string pattern, string subject [, array matches])
```

### PREG_REPLACE()

这基于 Perl 正则表达式进行替换。

```
mixed preg_replace (mixed pattern, mixed replacement, mixed subject
[, int limit])
```

这与 ereg_replace() 类似，不过这里的模式必须是 Perl 正则表达式。它还可以使用 \digit 将匹配的子字符串回显到结果中。可选的第四个参数将限制 preg_replace 所做的替换次数。

```
preg_replace("/[<br>&nbsp;\s]*$/i","",$body);
```

此示例取自内容管理系统应用程序，将删除所有出现换行符（<br>）、不间断空格（&nbsp;）或空白（空格、制表符、换行符）连续出现的情况。此替换不区分大小写（“i” 标志决定这一点），以确保同时匹配 <BR> 和 <br>。

方括号表示方括号内的任何内容将开始匹配。星号表示如果第一个匹配后的字符也是方括号内字符之一，则模式匹配并应进行替换。

## 本书中未使用的 PCRE 函数

我们未使用以下几个 PCRE 函数来创建这些应用程序。它们是：
- `preg_match_all`
- `preg_quote()`
- `preg_grep()`

请参阅在线手册了解其用法。请注意，我们将在下一节讨论 `preg_split()`。

## 类型转换函数

这是一个我自己创建的类别。在手册中，这些函数会归入其他标题下。然而，我们认为这些函数的专业性质需要一个独特的类别。

第 4 章详细讨论了 PHP 变量，包括 PHP 灵活的变量类型。如果你还记得，如果你需要将字符串作为整数进行求值，可以使用 `intval()` 函数。有关类似的变量转换函数，请参阅第 4 章。

但有时变量转换会更极端，将字符串转换为数组并将数组转换回字符串。你可能会问，为什么要这样做？考虑以下字符串：

```
24,16,9,54,21,88,17
```

所以你有一个整数字符串，也许是从文本文件中检索到的。你将如何按升序对其进行排序？如果必须将其作为字符串处理，代码会变得非常糟糕。然而，如果你可以使用众多的数组函数，生活会容易得多。你可以简单地使用 `sort()` 函数。看一下：

```
$str = "24,16,9,54,21,88,17";
//turn $str into an array
$array = explode(",", $str);
//sort the array in ascending order
sort($array, SORT_NUMERIC);
//turn the array back into a string and print
$new_str = implode(",", $array);
echo $new_str;
```

这将打印：

```
9,16,17,21,24,54,88
```

稍后将详细介绍 sort() 函数。

## 本书中使用的类型转换函数

以下类型转换函数在本书示例中使用。

### EXPLODE()

此函数将字符串转换为数组。

```
array explode (string separator, string string [, int limit])
```

第二个参数是你希望拆分为数组的字符串。第一个是分隔不同元素的字符或字符。在上面的示例中，字符串以逗号分隔。

第三个参数限制结果数组中的元素数量。如果你使用以下代码

```
$str = "24,16,9,54,21,88,17";
//turn $str into an array
$my_array = explode(",", $str, 3);
```

$my_array 将有三个元素：$my_array[0] => 24 $my_array[1] => 16 $my_array[2] => 9,54,21,88,17。你可以看到最后一个元素包含原始字符串的剩余部分。如果你只想对字符串中的前三个元素进行排序并丢弃其余部分，你可以这样做：

```
$str = "24,16,9,54,21,88,17";
//turn $str into an array
$array = explode(",", $str, 4);
unset($array[3]);
sort($array, SORT_NUMERIC);
echo implode(",", $array);
```

如果字符串分隔符不存在，整个字符串将被放在数组元素零中。如果字符串不存在，则空字符串将被放在第一个元素中。

### IMPLODE()

正如你所期望的，implode() 是 explode() 的相反操作：它将数组转换为字符串。

```
string implode (string glue, array pieces)
```

第一个参数是分隔字符串元素的字符串。第二个是要分隔的数组。

使用 implode() 的一个好例子是在运行 SQL 删除命令的页面中。假设在某个页面中你展示了一系列复选框以指示你希望从数据库中删除的行。你可能希望将要删除的元素作为数组传递。在执行删除的页面中，你可以运行如下脚本：

```
//say $delete_items comes from an HTML page and
//contains (1,3,7)
if( is_array($delete_items) )
{
    $str = implode(".", $delete_items);
    $query = "delete from table where item_id in ($str)";
    mysql_query($query);
}
```

### SPLIT()

split 函数与 explode 做同样的事情，但它允许你指定正则表达式作为分隔字符串。

```
array split (string pattern, string string [, int limit])
```

如果想要基于多个元素分隔字符串，这可能会派上用场。假设你有一个字符串需要作为数组，其元素可以由换行符或制表符分隔。以下代码即可实现：

```
//note there is a tab between 524 and 879
//and a tab between 879 and 321
$items = "524    879    321
444
221";
$array = split("[\n\t]", $items);
```

![](img/de0823012275cf4ceebdb822a56e6b71_174_0.png)

split() 比 explode() 更灵活，但也更慢。

### PREG_SPLIT()

这与 split() 类似，只是它使用 Perl 正则表达式作为模式。

```
array preg_split (string pattern, string subject [, int limit [, int flags]])
```

请注意，如果标志为 PREG_SPLIT_NO_EMPTY，则空项不会被放入数组中。

再次强调，如果 explode() 可以做到，请务必使用它。

## 本书中未使用的类型转换函数

除了上一节中的函数外，你还可以使用 spliti()，它使用不区分大小写的模式匹配。

## 数组函数

我是 PHP 4 中可用数组函数的忠实粉丝。你想对数组做的几乎任何事情都可以用内置函数完成。PHP 的开发人员做得很好，确保你很少需要遍历数组。

在 PHP 4.0.2 手册中，列出了恰好 47 个数组函数。到你阅读本章时，很可能已经有更多函数。因此，请务必查阅手册以了解所有可用数组函数的完整范围。

![](img/de0823012275cf4ceebdb822a56e6b71_175_0.png)

请参阅第 5 章，了解如何创建、添加以及遍历数组。

## 本书中使用的数组函数

当处理数据库应用程序时，你的大部分逻辑应包含在 SQL 语句中。因此，在本书中介绍的应用程序中，所需的数组函数相当少。以下是我们使用的函数概述。

### ARRAY_FLIP()

此函数在关联数组中很有用，它交换键和值。也就是说，键变为值，值变为键。

```
array array_flip (array trans)
```

这在本书中出现一次，在以下代码中：

```
$trans = array_flip(get_html_translation_table(HTML_ENTITIES));
$title = strtr($title, $trans);
```

在 array_flip() 函数之前，数组将返回许多元素。以下是几个示例：

```
[(c)] => &copy
[(r)] => &reg
```
