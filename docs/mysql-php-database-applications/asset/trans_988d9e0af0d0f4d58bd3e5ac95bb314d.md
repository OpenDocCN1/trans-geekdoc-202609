
但有时变量转换会更极端一些，将字符串转换为数组，或将数组转换为字符串。你可能会问，为什么要这么做？请考虑如下字符串：

24,16,9,54,21,88,17

那么，你有了这个整数字符串，可能是从文本文件中检索的。要如何按升序对其进行排序呢？如果把它当作字符串来处理，代码会变得非常糟糕。然而，如果你能利用PHP丰富的数组函数，生活就容易多了。你可以直接使用sort()函数。请看：

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

这将打印以下内容：

9,16,17,21,24,54,88

关于sort()函数的更多内容，本章稍后将介绍。

## TYPE CONVERSION FUNCTIONS USED IN THIS BOOK

本章示例中使用的类型转换函数如下。

### EXPLODE()

该函数将字符串转换为数组。

```
array explode (string separator, string string [, int limit])
```

第一个参数是分隔不同元素的字符或字符串。在前面的示例中，字符串由逗号分隔。第二个参数是你希望拆分为数组的字符串。

第三个参数限制结果数组中的元素数量。如果你使用以下代码

```
$str = "24,16,9,54,21,88,17";
//turn $str into an array
$my_array = explode(",", $str, 3);
```

$my_array将包含三个元素：$my_array[0] => 24 $my_array[1] => 16 $my_array[2] => 9,54,21,88,17。可以看到，最后一个元素包含原始字符串中剩余的部分。如果你想只对字符串中的前三个元素进行排序并丢弃其余部分，可以这样做：

```
$str = "24,16,9,54,21,88,17";
//turn $str into an array
$array = explode(",", $str, 4);
unset($array[3]);
sort($array, SORT_NUMERIC);
echo implode(",", $array);
```

如果字符串分隔符不存在，整个字符串将被放入数组元素零中。如果字符串不存在，空字符串将被放入第一个元素中。

### IMPLODE()

正如你可能猜到的，implode()是explode()的相反操作：它将数组转换为字符串。

```
string implode (string glue, array pieces)
```

第一个参数是将分隔字符串元素的字符串。第二个参数是要分隔的数组。

implode()的一个典型用例是执行SQL删除命令的页面。假设你提供了一系列复选框来指示要从数据库中删除哪些行。你可能需要将要删除的元素放在一个数组中传递。在执行删除操作的脚本中，你可以这样做：

```
//say $delete_items from an HTML page and
//contains (1,3,7)
if (is_array($delete_items))
{
    $str = implode(",", $delete_items);
    $query = "delete from table where item_id in ($str)";
    mysql_query($query);
}
```

### SPLIT()

split()函数的作用与explode()相同，但它允许你将正则表达式指定为分隔字符串。

```
array split (string pattern, string string [, int limit])
```

如果你希望根据多个元素分隔字符串，split()函数就可以派上用场。假设你有一个字符串需要转换为数组，其元素可以由换行符（\n）或制表符（\t）分隔。以下代码可以实现：

```
//note there is a tab between 524 and 879
//and a tab between 879 and 321
$items = "524\t879\t321\n444\n221";
$array = split("[\n\t]", "$items");
```

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_197_0.png)

### PREG_SPLIT()

```
array preg_split (string pattern, string subject [, int limit [, int flags]])
```

该函数的工作方式与split()类似，只是它使用Perl正则表达式作为模式。

请注意，如果标志为PREG_SPLIT_NO_EMPTY，空项将不会被放入数组中。

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_197_1.png)

要将句子拆分为组成单词（按空白字符分隔），可以执行以下操作：

```
$sentence = "Soup is good food."
$words = preg_split("\\s", $sentence);
```

$words的内容如下：

```
[0] => Soup
[1] => is
[2] => good
[3] => food.
```

gettype()和settype()可用于直接更改变量的类型。

### GETTYPE()

```
string gettype (mixed var)
```

该函数以字符串形式返回变量的类型：Boolean、string、array、integer等等。

### SETTYPE()

```
bool settype (mixed var, string type)
```

该函数以变量作为参数，将变量设置为指定类型：Boolean、integer、float、string、array、object或null。

### INTVAL() AND FLOATVAL()

```
int intval (mixed var [, int base])
float floatval (mixed var)
```

这两个函数接受任何标量变量，并分别返回一个整数或浮点数变量。

### COMPACT()

compact()和extract()分别用于将数组元素转换为变量以及反之。

```
array compact (mixed varname [, mixed ...])
```

给定一组变量名（可以作为单独参数或数组传递），compact()输出一个数组，其键为变量名，值为这些变量的相应值。只有已赋值的变量才会包含在输出数组中。

### EXTRACT()

```
int extract (array assoc_array [, int extract_type_constant [, string prefix]])
```

要从数组中提取键/值对并将其转换为独立变量，请使用extract()。元素键将成为变量名，元素值将成为变量值。因此，这段代码

```php
$array = array("name" => "Jay",
               "brand" => "Cohiba");
extract($array, "name");
echo $name;
```

将输出：

Jay

extract_type_constant参数控制如何处理命名空间冲突。该常数可取八个预定义值中的任何一个（有关详情请参见http://php.net/extract上的PHP手册页面），例如EXTR_OVERWRITE和EXTR_SKIP。这些值决定了解析器在遇到冲突时应采取的操作。

### NUMBER_FORMAT()

```
string number_format (float number [, int decimals [, string dec_point , string thousands_sep]])
```

给定一个浮点数，该函数返回一个为人类可读而格式化的字符串，其中包含带有千位分隔符和小数分隔符的数字。默认情况下，它们分别是逗号和句点，但也可以指定其他符号。

### JOIN()

```
string join (string glue, array pieces)
```

给定一个数组和一个字符串，join()返回一个由数组元素按顺序连接而成的字符串，每两个元素之间插入粘合字符串。

join()与implode()函数相同。

### RANGE()

```
array range (mixed from, mixed to [, int increment])
```

该函数创建一个数组，并自动用从from到to的元素填充它。如果在第三个参数中指定了步长增量，则该增量将作为元素之间的增量；否则，增量为1。

## TYPE CONVERSION FUNCTIONS NOT USED IN THIS BOOK

除了上一节中的函数外，你还可以使用`spliti()`，它使用不区分大小写的模式匹配。除了对字母字符不区分大小写外，`spliti()`的工作方式与`split()`完全相同。请看：

```
$audienceResponse1 = "oooooAAAooooh";
$audienceResponse2 = "ooooooaaaaoooh";
list ($part1, $part2) = split('AAA', $audienceResponse1);
list ($part3, $part4) = spliti('[aaa]', $audienceResponse2);
```

结果是，$part1和$part3包含ooooo，而$part2和$part4包含ooooh。

## Array functions

我们非常喜欢PHP中可用的数组函数。几乎任何你想对数组执行的操作，都可以使用内置函数来完成。PHP开发者做得很好，确保你几乎不需要（甚至不需要）频繁遍历数组。

撰写本文时，PHP手册列出了整整60个数组函数。在你阅读本章时，很可能会有更多函数。所以请务必查阅手册，了解所有可用数组函数的完整范围。

> 有关如何创建、添加到以及遍历数组的讨论，请参见第5章。

## ARRAY FUNCTIONS USED IN THIS BOOK

以下是本书中使用的数组函数概述。

### ARRAY_FLIP()

该函数对关联数组很有用，它会交换键和值。也就是说，键变为值，值变为键。

```
array array_flip ( array trans )
```

本书中只使用了一次此函数，如下所示：

```
$trans = array_flip(get_html_translation_table(HTML_ENTITIES));
$title = strtr($title, $trans);
```
