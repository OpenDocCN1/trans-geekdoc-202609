

# 第 9 章：调查

225

之所以可以这样做，是因为 PHP 处理变长参数的能力。你设计 `table_row` 函数来循环遍历所有参数（其中一些是对 `table_cell()` 函数的调用）。你可能在想这些函数是如何处理表格属性、宽度、对齐等等的。你该如何针对特定的表格修改它们呢？这些属性及其值必须包含在函数调用中。函数将通过变量类型来识别属性。也就是说，函数会更改参数的变量类型，如果它是一个数组（关联数组），函数将假设它包含了属性信息，并将数组中的键值对转换为字符串中的 `name=value` 属性对。一个更复杂的函数调用看起来像这样：

```
print (table_row(array("bgcolor" => $bgcolor),
    table_cell("new entry"),
    table_cell(text_field("entered_by", "", "10")),
    table_cell(submit_field("submit", "insert"))
);
```

这里，第一个参数 `array("bgcolor" => $bgcolor)` 标识了行的背景颜色；其余参数创建表格单元格。作为额外奖励，这些表格单元格包含了表单元素。

记住，稍后将解释实现嵌套函数调用的方法。应用程序还将使用 MySQL。在整个应用程序中，MySQL 函数的使用比第 8 章中更广泛。

# 代码解析

与留言板应用一样，代码为了方便起见进行了拆分。仅由此应用程序使用的函数位于 `/book/survey/header.php` 文件中。该文件将被包含在每个文件中。`start_page.php` 和 `end_page.php` 分别包含头部和页脚信息。

由于我们在第 8 章已经涵盖了 `/book/functions/functions.php` 文件中的函数，因此我们不再对其进行回顾。但我们这次增加了一点小奖励。

# 可重用函数

随着你的应用程序变得复杂，你将不断使用某些 HTML 元素——表单、表格、段落标签、锚点等。因此，我们添加了一系列函数，使得创建重复的 HTML 元素变得更加容易。还将一些常用的数据库函数移动到了它们自己的文件中。

# 第三部分：简单应用程序

# FUNCTIONS /BOOK/FUNCTIONS/DB.PHP

如果你学习过第 8 章的留言应用，这部分内容看起来会很熟悉。但请记住，对于其余应用程序，你可以在此文件中找到函数。我们不会涵盖每一个函数，只涵盖那些需要解释的。

`SET_RESULT_VARIABLE()` 此函数将查询结果转换为全局变量。

```
function set_result_variables($result)
{
    if(!$result || mysql_num_rows($result)) { return; }
    $row = mysql_fetch_array($result,MYSQL_ASSOC);
    if(!is_array($row)) {
        print "<no array returned : result=$result row=$$row";
        return $result;
    }
    while (list($key,$value) = each($row)) {
        global $$key;
        $$key = $value;
    }
}
```

如果你记得我们在第 7 章关于变量作用域的讨论，你会记得通过 GET 或 POST 传递或在函数外部声明的变量都是全局变量，它们在 `GLOBAL` 数组中可用。

你经常会需要将查询中使用的列名作为变量。能够不通过通过 `mysql_fetch_array()` 遍历关联数组而直接使用它们是非常棒的。这个函数将你查询中使用的变量转换为整个脚本中的全局变量。

```
$query = "select distinct fname, lname from table_1 where id=1";
$result_safe_query($query);
set_result_variables($result);
```

这段代码将使变量 `$fname` 和 `$lname` 及其值作为全局变量可用。如果向查询发送包含多行的结果集，此函数仅使用第一行。

注意此函数中变量名的使用。

```
while (list($key,$value) = each($row))
{
    global $$key;
```

# 第 9 章：调查

$$key = $value;
}

每个元素都从 `mysql_fetch_array()` 获取的数组中提取。键（列名）被声明为全局变量。该全局变量被赋值 `$value` 的内容。变量变量在第 7 章中讨论过。

此函数旨在配合 `fetch_record()` 函数使用。

`FETCH_RECORD()` 此函数有助于创建查询。

```
function fetch_record($table, $key="", $value="")
{
    $query = "select * from $table";
    if (!empty($key) && !empty($value))
        if (is_array($key) && is_array($value))
{
            $query .= " = where ";
            $and = "";
            while (list($i,$v) = each($key))
{
                $query .= "&and $v = ".$value[$i];
                $and = " and";
            }
        }
        else
{
            $query .= " where $key = $value ";
        }
    $result = safe_query($query);
    if (!empty($key) && !empty($value) && mysql_num_rows($result) == 1)
{
        set_result_variables($result);
    }
    return $result;
}
```

如果你需要使用，它并不复杂。在此应用程序以及许多应用程序中，`$value` 将作为关联数组中的键。此函数对于从数据库创建下拉框和其他元素非常有用。如果你需要使用，它并不复杂。在 应用程序以及许多应用程序中，`$value` 将作为关联数组中的键。

# 第三部分：简单应用程序

首先，检查发送的是单个值还是多个值。第二个参数是特定标签所需的属性数组。例如，一个 `<img>` 标签如果没有 `src` 属性毫无意义。因此，如果该函数是从另一个创建标签的函数调用的，第二个参数应该是包含一个元素的数组，类似于 `$myarray("src"="$myimage.gif")`。

第一个参数将接收另一个包含其他属性的数组。对于 `<img>` 标签，它可能包含 alt 文本、宽度和高度——`$myarray array("alt="My image." "width="20" "height="25.")`。

