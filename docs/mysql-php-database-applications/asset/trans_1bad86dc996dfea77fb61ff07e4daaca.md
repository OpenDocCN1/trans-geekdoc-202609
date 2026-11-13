

### RESET()

mixed reset (array array)

此函数将数组的指针重置到开头，并返回数组第一个元素的值。

## 本书未使用的数组函数

再说一遍，PHP 包含许多出色的数组函数。以下是其中一些亮点（就我们的观点而言）。

### ARRAY_COUNT_VALUES()

这个实用的函数将返回一个关联数组，其键将是数组中所有唯一的值。

array array_count_values (array input)

结果数组的值将是一个整数，表示该值在数组中出现的次数：

```
$array = array("yes", "no", "no", "yes", "why");
$result = array_count_values($array);
```

此后 $result 将包含：

```
[yes] => 2, [no] => 2, [why] => 1
```

### ARRAY_RAND()

此函数将从数组中选取一个或多个随机元素。

mixed array_rand (array input [, int num_req])

请注意，array_rand() 选取的不是值，而是所选元素的键。例如：

```
srand ((double) microtime() * 1000000);
$names = array("jay", "brad", "john", "Jeff");
$rand_keys = array_rand ($names, 2);
```

在此示例中，$rand_keys 将包含带有两个数字的数组。要从 $names 数组中获取值，你首先需要获取 array_rand() 提取的键值，因此你需要使用类似这样的内容：

```
echo $names[$rand_keys[0]];
```

每个脚本只对随机数生成器播种一次。你甚至可能想考虑使用共享变量，这样你就可以只对生成器播种一次，就此为止，以应对随着处理器速度越来越快而开始越来越频繁出现的问题。如果处理器速度继续增加且事务量增加，将达到一个上限，届时随机数将不再是随机的，因为两次连续调用中的 microtime() 值相同。

### SHUFFLE()

此函数将数组中的元素随机化。

```
void shuffle (array array)
```

在使用之前，你需要对随机数生成器进行播种。例如：

```
srand ((double) microtime() * 1000000);
shuffle ($array);
```

### SORT()

如果未给出第二个参数，此函数将按升序或字母顺序对数组进行排序。

```
void sort (array array [, int sort_flags])
```

标志分为两种：

- SORT_NUMERIC – 数值比较项目
- SORT_STRING – 按字符串比较项目

如果你要排序的数组仅包含数字，PHP 将按数值对其进行排序；如果数组仅包含字符串，则将按字母顺序对其排序。如果数组同时包含字符串和数字，则默认按字符串排序。

PHP 提供了许多其他对数组进行排序的方法。请查看 arsort()、ksort()、rsort() 和 usort() 的手册条目。

## 对象/类函数

PHP 有许多与类（即用于创建对象的模板）和对象本身相关的函数。本书中的示例使用了几个用于检索有关已定义对象、类和方法的信息的函数。如下所示。

### is_a()

使用此函数确定给定对象是否是给定类的实例或是从给定类派生的类的实例。在第一个参数中指定对象，在第二个参数中指定类名；如果一个是另一个的实例，该函数将返回 TRUE。

```
bool is_a (object object, string class_name)
```

### is_object()

此函数与其他 is_ 函数类似，如果参数是对象，则返回 TRUE，否则返回 FALSE。

```
bool is_object (mixed var)
```

### get_class()

给定一个对象，此函数返回该对象是其实例的类名。

```
string get_class (object obj)
```

### get_object_vars()

给定一个对象，此函数返回一个包含该对象当前属性的关联数组。

```
array get_object_vars (object obj)
```

### method_exists()

给定一个对象和一个方法名，如果该方法（函数）已为对象定义，则此函数返回 TRUE。

```
bool method_exists (object object, string method_name)
```

## 打印函数

有几个函数可让你将信息打印到屏幕上。本书中只出现了两个，但你应该了解本节中列出的所有函数。

## 本书使用的打印函数

在这种情况下，“函数”一词可能有点不准确。例如，print() 或许更好描述为语言结构。（有用的区别在于，你不需要在参数周围使用括号。）无论如何，你将像使用函数一样使用所有这些内容；因此，它们包含在此处。

### PRINT()

如你所料，这将打印你指定的内容。

```
void print ( 'string str' )
```

### ECHO()

这也不是函数，而是语言结构。我们在整本书中不断使用它，所以到这一点你可能知道它的作用。

```
void echo ( string str1 [, string strN ... ] )
```

请记住，你可以在双引号内混合变量和字面字符串：

```
$var = "this string";
echo "Please print $var";
```

这将打印 Please print this string。
但是，在单引号内字符串将被按字面处理：

```
$var = "this string";
echo 'Please print $var';
```

前面的代码将打印 Please print $var。混合变量名和字符串字面量的概念在第 4 章中有更详细的讨论。

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_210_0.png)

print 与 echo。你应该使用哪个？这很大程度上是个人偏好的问题：使用你认为在脚本中看起来更好的那个。两者之间只有一个主要区别，这可能会影响你的决定。echo 可以接受多个参数。也就是说，使用 echo 时，不同部分可以用逗号分隔。这将有效：
echo "this is part 1", "this is part 2";
但这将无效：
print "this is part 1", "this is part 2";

## 本书未使用的打印函数

它们在此处未出现，但了解这些非常重要。

### SPRINTF()

```
string sprintf (string format [, mixed args])
```

此函数可用于按照指定的 C 样式模式输出格式化字符串。模式的参数在在线 PHP 文档中有详细介绍（http://www.php.net/sprintf）。

### PRINT_R()

这个函数非常适合将你原本可能花在抓头发上的时间用在有成效的事情上。它将任何变量（尤其是数组和对象）的完整内容打印到屏幕上。

```
void print_r (mixed expression)
```

它对于调试非常有价值。当我们无法从数组或对象中获得预期结果时，我们会频繁使用它。

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_211_0.png)

### VAR_DUMP()

此函数的行为类似于 print_r，但会提供更多信息。

```
void var_dump (mixed expression)
```

除了打印变量的内容外，它还包括数据类型——包括数组或对象中每个元素的数据类型。print_r() 中给出的相同谨慎建议也适用于 var_dump()。

## 日期/时间函数

将 PHP 和 MySQL 作为团队使用时，你需要了解两组日期/时间函数——它们差异很大。有关 MySQL 时间和日期函数的详细介绍，请参见附录 J。

## 本书使用的日期/时间函数

以下是本书应用程序中使用的一些日期/时间函数。

### DATE()

你可以使用此函数和下面列出的指示符来返回日期和时间。

```
string date (string format [, int timestamp])
```

如果你包含第二个参数，该时间/日期值将按你指定的方式格式化。否则，将使用当前时间和日期。

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_212_0.png)

函数返回的时间和日期基于服务器上的时间。你需要使用 JavaScript 来了解客户端计算机上的时间。

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_212_1.png)

通常，第二个参数将是 mktime() 函数的产物，我们将在下一节讨论该函数。

你可以使用表 6-1 中的任何指示符来格式化日期。

## 表 6-1 date() 函数的指示符

| 指示符 | 含义 |
|---|---|
| a | am 或 pm |
| A | AM 或 PM |
| B | Swatch Internet 时间 |
| d | 月份中的天数，两位数字带前导零；01 到 31 |
| D | 星期几，文本，三个字母；例如，Fri |
| F | 月份，文本，长形式；例如，January |
| g | 小时，12 小时格式不带前导零；1 到 12 |
| G | 小时，24 小时格式不带前导零；0 到 23 |
| h | 小时，12 小时格式；01 到 12 |
| H | 小时，24 小时格式；00 到 23 |
| i | 分钟；00 到 59 |
| I [大写 i] | 如果是夏令时，则为 1，否则为 0 |
| j | 月份中的天数不带前导零；1 到 31 |

