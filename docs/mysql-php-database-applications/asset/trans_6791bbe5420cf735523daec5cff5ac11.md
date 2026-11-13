
echo $myarray[$i] . "<br>\n";
}

第一次遍历时，$i 被赋值为 0，因此会打印数组中的第一个元素。在接下来的每次遍历中，$i 都会递增 1。循环将在 $i 等于数组长度（即 4）时立即结束。请记住，数组元素从 0 开始，因此上述数组的最后一个元素是 $myarray[3]。

你也可以将 for 循环中的任意三个表达式留空。如果将第二个表达式留空，if 条件将求值为 true，你需要确保循环最终会遇到一个 break 语句（我们将在本章后面的“break”部分讨论 break）。

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_175_0.png)

运行以下代码会非常糟糕：它会无限运行，耗尽你的内存和 CPU。你必须终止 Web 服务器才能让这个脚本停止。它可能会让你的整个机器崩溃。

```
for ($i = 0;; $i++) {
    echo "$i <br>\n";
}
```

## foreach

foreach 结构专用于数组。在大多数情况下，你可以用它来替代 list() = each()。该结构会从数组的开头一直处理到结尾，将每个元素赋值给你用 as 关键字指定的标量变量（一个只有一个值的变量，例如整数或布尔值，与多元素数组或复杂对象相对）。以下代码将打印数组 $names_array 中的所有值：

```
$names_array = array("jay", "brad", "ernie", "bert");
foreach ($names_array as $first_name)
{
    echo $first_name;
}
```

如果你处理的是关联数组，可能需要访问每个数组元素的键和值。以下语法可让你实现这一点：

```
$jay_info = array ("fname" => "jay", "lname" => "greenspan", "hobby" =>"juggling");
```

```
foreach ($jay_info as $key => $value)
{
     echo "<b>$key:</b> $value <br>\n";
}
```

与 list() = each() 不同，foreach() 在之后不要求你重置数组。它使用数组的临时副本进行操作。由于它通常也比 list() = each() 更快，因此更可取。

## continue and break

在循环中，你可能需要要么完全跳出循环，要么跳到循环中要处理的下一项。针对这些情况，你可以分别使用 continue 和 break。continue 和 break 都可以接受一个数值参数。该参数指定要跳出多少层循环。此功能很少使用。

### continue

假设你正在从文件系统读取内容，希望脚本处理特定目录中的每个文件，但不需要处理任何子目录。当 PHP 从目录读取名称时，你不知道该项目是文件还是目录，因此需要使用 is_dir() 函数进行测试。你希望跳过目录列表项。脚本如下所示：

```
$directory=opendir('/home/jay/');
echo "Files are:<br>\n";
while ($file = readdir($directory))
{
     if (is_dir($file)) { continue; }
     echo "$file <br>\n";
     //process files here;
}
closedir($directory);
```

请注意，这里并非必须使用 continue。你也可以按照以下示例编写此脚本，有些人认为这是更好的方法：

```
$directory=opendir('/home/jay/');
echo "Files are:<br>\n";
while ($file = readdir($directory))
{
     if (!is_dir($file)){
     echo "$file <br>\n";
     }
}
closedir($directory);
```

### break

break 会让脚本脱离控制结构而不停止脚本的执行。几乎总是最好避免使用 break。if 语句通常可以完成相同的事情，并能写出更简洁的代码。

你可能希望在循环内部出现错误时使用 break。在以下示例中，我们遍历 MySQL 查询返回的行，调用一个函数进行初始处理，然后调用第二个函数来处理第一个函数的结果。如果这两个函数中的任何一个失败，我们希望立即停止处理，不再继续处理其余行。

```
while ($row = mysql_fetch_assoc($result))
{
    $setup_result = setup($row);
    if ($setup_result == FALSE)
    {
        print "Error in calling 'setup()'\n";
        break;
    }
    $process_result = process($setup_result);
    if ($process_result == FALSE)
    {
        print "Error in calling 'process()'\n";
        break;
    }
}
```

## 摘要

在本章中，你了解了 PHP 语言的构建模块。你学习了如何使用循环和 if 块。如果你阅读了讨论变量的第 4 章，那么你现在已掌握使用 PHP 编程所需的所有基础知识。

编程本质上是关于使用变量、循环和 if 块。这些元素的各种组合将处理你在应用程序中需要完成的一切。然而，仍有一个主要部分需要学习：函数。第 6 章展示了 PHP 的内置函数如何作用于你的脚本。

## 第 6 章

## PHP 的内置函数

## 本章内容

- 使用 PHP 的内置函数
- 函数语法
- 使用函数

PHP 拥有大量的内置函数和扩展（“扩展”是指不属于核心 PHP 代码的相关函数集合）。只有在使用特定选项编译 PHP 时，其中许多才可用。例如，如果你需要进行可扩展标记语言（XML）解析，PHP 有两个扩展可以帮助你。（一个采用基于事件的方法，另一个采用基于文档的方法。）如果你需要轻量级目录访问协议（LDAP）、互联网邮件访问协议（IMAP）或可移植文档格式（PDF）函数，相应的扩展都可用。此外，PHP 为地球上几乎每种关系型数据库都提供了应用程序接口（API）。但本书无需介绍其中的大部分函数。

还需要记住一点是，函数集几乎每天都在变化。PHP 的内部结构使得程序员非常容易添加更多函数。事实上，如果你熟悉 C 语言，可能只需几个小时就能向 PHP 添加一个新函数。因此，你可以期待核心函数集会定期新增。

和往常一样，你最好的朋友是在线 PHP 手册：http://www.php.net/manual。它是你可以确信函数列表或多或少是最新的唯一来源。如果你想直接查看某个函数的说明，只需在浏览器中打开 http://www.php.net/function_name。

在开始之前，我们还想指出一件事。本书的最后两个部分包含若干应用程序。在创建这些应用程序的过程中，我们使用了 150 多个 PHP 内置函数。因此，虽然存在数千个内置函数，但你可能只会经常使用其中相对较少的一部分。

> **提示：** 一个非常不错的资源是 http://www.zugeschaut-und-mitgebaut.de/php/ 上的函数表。

## 函数基础

函数都采用相同的基本形式：

```
return_type function_name (argument1, argument2, argument3)
```

首先，return_type 是函数被调用时返回的输出类型：整数、布尔值、数组、字符串等等。这些被称为返回值。接下来是函数名称；请注意，函数名不区分大小写。

最后，在函数名之后是一组括号。括号内是函数需要的任何参数，用逗号分隔。虽然参数本身是可选的，但括号本身不是。我们将先讨论参数，然后是返回值，因为这是函数处理它们的顺序。

## 参数

参数只是函数期望的一个值（或对值的引用）。函数可能期望零个、一个、两个、三个或更多参数，任何参数都可以是任何变量类型——可能是字符串、整数、数组或其他内容。为了让你更好地了解参数是什么，这里有一个示例：一个处理字符串的函数。

str_replace() 函数非常有用。假设你有以下字符串：

```
$str = "My name is Jay.";
```

假设在 $str 变量中，你需要查找 Jay 并将其替换为 John。执行替换的函数需要三个参数：要搜索的字符串、要查找的字符串和替换字符串。在 PHP 中，参数的顺序恰好如下：

```
str_replace(string to search for, replacement string, string to be searched through);
```

或者，实际操作如下：

```
$str = "My name is Jay.";
$new_str = str_replace("Jay", "John", $str);
```
