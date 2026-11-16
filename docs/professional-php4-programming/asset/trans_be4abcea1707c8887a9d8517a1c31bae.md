

## 注释

良好的编程实践是在函数声明中包含描述性注释，以解释该函数的功能（类似于 Python 中使用的文档字符串）。在包含许多函数和/或非常长函数的脚本中，使用注释指示函数的结束也很有帮助。这有助于开发者浏览脚本。在多开发者组织中，为广泛使用的函数包含更多详细信息也是明智之举，例如函数作者的姓名和任何其他相关详细信息：

```
function isIntInRange($mVal, $iLow, $iHigh)
{
    // True if mVal is an integer between iLow and iHigh inclusive

    /*
        Written by Christopher Scollo scollo@taurix.com
        To do: Improve error handling if iLow or iHigh is not an int
    */

    ...

} // end isIntInRange()
```

## 数组

数组是一个可以存储多个值的列表，是编程中不可或缺的工具。数组由元素组成，每个元素可以存储一个值。每个元素通过其索引（或键）引用。最基本的数组类型使用整数作为索引。在 PHP 中，数值索引数组是从零开始的，意味着第一个元素的索引为 0，第二个元素的索引为 1，依此类推。如本章后面所见，有些数组的索引为字符串。

在接下来的几个部分中，我们将探讨 PHP 中数组的用法，包括数组声明、遍历和排序。

## 初始化数组

有多种方法可以初始化数组变量。一种方法是直接开始为数组变量的元素赋值。下面的代码创建了一个名为 $aLanguages 的数组，包含三个元素。由于我们未指定任何索引，PHP 默认分配数值索引 0、1 和 2：

```
$aLanguages[] = "Arabic";
$aLanguages[] = "German";
$aLanguages[] = "Korean";

echo($aLanguages[2]); // Prints "Korean"
```

要显式指定索引，请在方括号中包含它：

```
$aLanguages[0] = "Arabic";
$aLanguages[1] = "German";
$aLanguages[2] = "Korean";
echo($aLanguages[2]); // Prints "Korean"
```

数组元素无需按顺序声明。下面的代码将创建一个包含四个元素的数组，其索引分别为 100、400、300 和 401：

```
$aLanguages[100] = "Arabic";
$aLanguages[400] = "German";
$aLanguages[300] = "Korean";
$aLanguages[] = "Tagalog";
echo($aLanguages[300]); // Prints "Korean"
echo($aLanguages[401]); // Prints "Tagalog"
```

由于我们未为最后一个元素指定索引，PHP 分配了在迄今使用的最高索引之后的第一个可用整数：401。

array() 构造提供了定义数组的替代方法。array() 接收一个用逗号分隔的值列表以放入数组：

```
$aLanguages = array("Arabic", "German", "Korean", "Tagalog");
echo($aLanguages[2]); // Prints "Korean"
```

同样，由于我们未指定任何索引，数组的元素被分配了默认索引。要使用 array() 构造显式指定索引，请使用 => 运算符：

```
$aLanguages = array("Arabic", 3 => "German", "Korean", "Tagalog");
echo($aLanguages[0]); // Prints "Arabic"
echo($aLanguages[3]); // Prints "German"
echo($aLanguages[4]); // Prints "Korean"
echo($aLanguages[5]); // Prints "Tagalog"
```

如前所述，数组索引也可以是字符串：

```
$aLanguages = array(
	"ar" => "Arabic",
	"de" => "German",
	"tl" => "Tagalog"
);
echo($aLanguages["tl"]); // Prints "Tagalog"
```

```
$aLanguages["ko"] = "Korean";
echo($aLanguages["ko"]); // Prints "Korean"
```

## 遍历数组

在 PHP3 中，遍历数组通常涉及 each 函数的复杂实现，该函数与 list 构造和 while 循环一起使用。PHP4 引入了 foreach 循环，极大地改进了此任务，Perl 程序员对此已非常熟悉。其语法很简单：

```
foreach (array as [$key =>] $value) {
statements
}
```

foreach 为数组中的每个元素迭代一次。在每次迭代中，它将元素的索引填入 $key 变量，将元素的值填入 $value 变量。这两个变量名是任意的；下面的代码同样有效：

```
foreach ($aLanguages as $sIdx => $sVal) {
echo("$sIdx is $sVal <br />");
}
```

如概要所示，保存索引的变量是可选的，因为它通常在循环中不需要。在本示例中，我们完全省略了 $key 变量，并使用名为 $sLang 的变量代替 $value：

```
echo(
"Available Languages: <br />\n" .
"<ul>\n"
);
foreach ($aLanguages as $sLang) {
echo("<li>$sLang</li>\n");
}
echo("</ul>\n");
```

## 内置数组函数

PHP 提供了一系列丰富的函数来方便数组操作。下面介绍了一些有用的函数。有关完整列表，请参阅在线文档 http://www.php.net/manual/en/ref.array.php。

### count()

count() 接收一个数组参数并返回元素的数量。如果变量未设置，或已设置但包含零个元素，则返回零。

```
int count(mixed var)
```

### in_array()

该函数在 haystack 数组中搜索 needle 值，如果在数组中找到则返回 true，否则返回 false。

```
boolean in_array(mixed needle, array haystack [, bool strict])
```

### reset()

PHP 中的每个数组都有一个内部指针，用于跟踪数组中的当前位置。在使用 foreach 等结构时，我们无需关心指针，因为 foreach 会勤勉地将指针重置到数组的开头。但是，许多数组函数（例如 prev() 和 next()）会将指针移动到数组中的新位置。这可能会影响对未来函数（例如 array_walk()）的调用，后者将从指针当前所在的位置开始处理。

reset() 函数用于确保数组的指针位于第一个元素。它返回第一个元素的值：

```
// Set pointer to beginning:
reset($aLanguages);

// Now apply my_function to every element of the array:
array_walk($aLanguages, "my_function");
```

有关 array_walk() 的更多信息，请参阅在线文档。

### sort()

该函数用于对数组中的值进行排序。可选的第二个参数 sort_flags 可用于指定排序时数据应如何处理。可能的值为 SORT_REGULAR、SORT_NUMERIC（强制按数值比较）或 SORT_STRING（强制按字符串比较）。

PHP 包含许多语法与 sort() 非常相似的排序函数。这些函数在行为上有所不同，以在排序过程中提供各种选项，包括排序方向的更改、键的处理以及所使用的比较算法。有关 arsort()、asort()、ksort()、natsort()、natcasesort()、rsort()、usort()、array_multisort() 和 uksort() 的更多信息，请参阅在线文档。

### explode() 和 implode()

这两个函数官方上被视为字符串函数，但它们确实涉及数组。explode() 用于使用提供的参数作为分隔符将字符串拆分为数组的独立元素。implode() 则正好相反：它使用“粘合”参数将数组的元素压缩为一个字符串：

```
// Turn the languages array into a single string,
// separated by semicolons:
$sLangString = implode('; ', $aLanguages);
echo($sLangString);

$sSentence = 'Never ruin an apology with an excuse';
// Turn the sentence into an array of individual words:
$aWords = explode(' ', $sSentence);
```

## 预定义数组

PHP 的一些预定义变量是数组。在我们关于 PHP 中函数的讨论中，我们描述了内置的 $GLOBALS 数组，它保存脚本的所有全局变量。其他内置数组包含这些信息的特定子集，例如 $HTTP_POST_VARS、$HTTP_GET_VARS 和 $HTTP_COOKIE_VARS，它们分别保存通过 HTTP POST 方法、HTTP GET 方法和 Cookie 传递给脚本的变量。

## 多维数组

当数组的元素本身包含数组（而这些数组又可能包含它们自己的数组，依此类推）时，即存在多维数组。

所有相同的数组初始化方法都适用于多维数组，包括嵌套的 array() 构造：

```
$aLanguages = array(
"Slavic" => array("Russian", "Polish", "Slovenian"),
"Germanic" => array("Swedish", "Dutch", "English"),
"Romance" => array("Italian", "Spanish", "Romanian")
);
```

要访问多维数组中深层嵌套的元素，需要使用额外的一组方括号。因此，$aLanguages["Germanic"] 引用包含日耳曼语言的数组，而 $aLanguages["Germanic"][2] 引用嵌套数组中的第三个元素（"English"）。

可以使用嵌套循环遍历多维数组：

```
foreach ($aLanguages as $sKey => $aFamily) {
// Print the name of the language family:
echo(
"<h2>$sKey</h2>\n" .
"<ul>\n" // Start the list
);

// Now list the languages in each family:
foreach ($aFamily as $sLanguage) {
echo("<li>$sLanguage</li>\n");
}
}
```

