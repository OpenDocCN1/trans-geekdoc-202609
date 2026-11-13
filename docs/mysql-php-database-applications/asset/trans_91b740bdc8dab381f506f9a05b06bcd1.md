

了解这个函数的首要一点是，默认情况下，它不仅会打印带有属性的起始 <p> 标签，还会打印结束 </p> 标签以及两者之间可能出现的所有内容。这可能包括锚点标签、图像标签，或者几乎任何其他内容。以下函数调用运行良好，实际上已在调查应用程序中使用：

```
print paragraph(anchor_tag('block_domain.php','Return to Domain
List'));
```

这个函数调用中有一个参数，而该参数又是另一个带有两个参数的函数调用。实际上，当一个函数调用嵌套在另一个函数调用内部时，PHP 会先执行内部调用。因此，首先会调用 anchor_tag() 函数，创建类似 '<a href="admin_block.php">' 的字符串。然后执行外部函数，因此对 paragraph 函数的调用实际上会如下所示：

```
print paragraph('<a href="admin_block.php">Return to Domain
List</a>');
```

请注意这变得多么灵活。通过遍历参数的数量，你可以向 paragraph 函数发送任意数量的其他函数调用。而且你可以随意将文本和函数调用混合在一起，因为在 paragraph() 看到它时，全部都是文本。因此，以下是对 paragraph 函数的完全合法的调用：

```
print paragraph(
    "<b>Blocked by:</b> $block_by <br>"
    . "<b>Date Blocked:</b> $block_dt <br>"
    . "<b>Date Released:</b> $release_dt <br>"
    . "<b>Last Modified:</b> $modify_dt <br>"
);
```

### START_PARAGRAPH()

你可能注意到，paragraph() 函数会检查是否传入了名为 'start' 的参数，如果是，则只返回起始 <p> 标签。有时你需要以这种方式使用该函数，因为段落内的内容太复杂，无法包含在值列表中。在这种情况下，你可以直接使用 'start'=>TRUE 属性调用 paragraph()，也可以使用 start_paragraph() 函数，如下所示：

```
function start_paragraph()
{
    $p = func_get_args();
    $p[] = array('start'=>'yes');
    return call_user_func_array('paragraph', $p);
}
```

start_paragraph() 函数会获取传入的参数并添加一个 'start' 参数。接下来是有趣的部分。PHP 函数 call_user_func_array() 接受一个函数名和一个参数数组，并用它们来调用命名函数。参数数组中的元素会像在普通函数调用中一样原样传递。所以

```
call_user_func_array('myfunc', array(1,2,3));
```

与以下代码完全相同：

```
myfunc(1,2,3);
```

call_user_func_array() 策略让 start_paragraph() 能够作为 paragraph() 函数的一种前端。对 start_paragraph() 的调用，如下例所示：

```
start_paragraph(array('align'=>'center'));
```

相当于

```
paragraph(array('align'=>'center', 'start'=>'yes'));
```

两次调用都会生成相同的 HTML 输出：

```
<p align="center">
```

### END_PARAGRAPH()

此函数只是打印一个结束段落标签 (</p>)，如下所示：

```
function end_paragraph ()
{
    $output = "\n</p>\n";
    return $output;
}
```

它存在的主要原因，除了与 start_paragraph() 形成一对漂亮的搭配之外，是让你能够关闭可能想要硬编码到段落开始处的任何起始标签——例如 <font> 标签。

### UL_LIST()

使用此函数可以创建项目符号列表。最常见的情况是将数组传递给该函数，每个元素前都加上 <li> 标签。该函数也处理仅发送字符串作为参数的情况。

```
function ul_list ()
{
    static $_defaults = array(
        'values' => array()
        , 'contents' => NULL
        , 'allowed' => array('Common','compact','type')
    );
    static $_simple = array('values');
    $p = func_get_args();
    $p = parse_arguments($p, $_simple, $_defaults);
    $attlist = get_attlist($p);

    $output = "<ul $attlist>\n";

    if (!empty($p['values'])
        && is_array($p['values'])
        && !is_object($p['values']))
    {
        $output .= $p['values'];
    }
    else
    {
        array_key_remove($p,array('_defaults','_simple','allowed'));
    }
    foreach ((array)$p['values'] as $p['text'])
    {
        $output .= li_tag($p);
    }
}
$output .= $p['contents'];
$output .= "</ul>\n";
return $output;
}
```

### START_TABLE()

每个 HTML 表格几乎都以相同的代码开始，因此我们有了一个函数来为我们生成它。

```
function start_table ()
{
    static $_defaults = array(
        'cellspacing' => 0
        , 'cellpadding' => 1
        , 'allowed' =>
    array('Common','border','cellpadding','cellspacing'
    ,'datapagesize','frame','rules','summary','width','align','bgcolor'
    );
    static $_simple = array('width');
    $p = func_get_args();
    $p = parse_arguments($p, $_simple, $_defaults);
    $attlist = get_attlist($p);
    $output = "\n<table $attlist>\n";
    return $output;
}
```

### END_TABLE()

表格的结尾也是如此——它是样板代码，而样板代码应以编程方式生成。下面是一个实现此功能的函数。

```
function end_table ()
{
    $output = "\n</table>\n";
    return $output;
}
```

### TABLE()

在此处，与类似的段落函数不同，start_table() 是知道如何生成起始 <table> 标签的函数，而整体 table() 函数会调用它。这是因为当我们只打开一个表格时，希望能够将宽度作为参数传入。但是，在创建完整表格时，任何未标记的参数都将成为生成表格中的行。由于这两种情况需要 $__simple 的不同值，start_table() 不能仅作为 table() 的前端。

```
function table ()
{
    static $_defaults = array(
        'rows' => array()
    );
    static $_simple = array('rows');

    $p = func_get_args();
    $p = parse_arguments($p, $_simple, $_defaults);

    $output = start_table($p);

    foreach ((array)$p['rows'] as $row)
    {
        $output .= table_row($row);
    }

    $output .= end_table($p);

    return $output;
}
```

### TABLE_ROW()

此函数不仅打印起始 <tr> 标签及其属性，还会打印将嵌套在 <tr> 标签内的表格单元格。

```
function table_row ()
{
    static $_defaults = array(
        'cells' => array()
        , 'allowed' =>
    array('Common','align','valign','char','charoff'
        ,'bgcolor'
    );
    static $_simple = array('cells');
    $p = func_get_args();
    $p = parse_arguments($p, $_simple, $_defaults);
    $attlist = get_attlist($p);
    $output = "\n <tr $attlist>\n";
    foreach ((array)$p['cells'] as $cell)
    {
        if (!preg_match('/<t[dh]/i', $cell))
        {
            $output .= table_cell($cell);
        }
        else
        {
            $output .= $cell;
        }
    }
    $output .= "\n </tr>\n";
    return $output;
}
```

以下 table_row() 调用有两个参数，其中一个本身也是另一个函数调用。table_cell() 函数（稍后描述）会先被执行，结果会传递给 table_row()。

```
print table_row(
    '<b>A simple cell</b>',
    table_cell(array('value'=>"A not-so-simple cell",
    'align'=>"right"))
);
```

因此，当 table_row() 遍历其 $cells 参数中的值时，会发现一个普通字符串 ('<b>A simple cell</b>')，它会将该字符串自身通过 table_cell() 处理，以及一个已格式化的单元格（即初始代码中 table_cell() 调用的输出），然后直接将其追加到输出字符串中。

### TABLE_CELL()

这里没有太多新内容。值得指出的是 $value 属性的处理方式：你需要检查它是数组还是对象，因为 PHP 允许将对象强制转换为数组——你会得到一个包含对象属性的关联数组。

```
function table_cell ()
{
    static $defaults = array(
        'align' => 'left'
        , 'valign' => 'top'
        , 'value' => ''
        , 'allowed' =>
    array('Common','abbr','align','axis','char','charoff'
        ,'colspan','headers','rowspan','scope','valign','width','height'
```

