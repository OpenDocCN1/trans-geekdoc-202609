
```php
$counter = 0;
while ( $counter < 5 )
{
    $counter++;
    if ( $counter == 3 )
    {
        echo “continue\n”;
        continue;
    }
    echo “Last line in loop: counter=$counter\n”;
}
echo “First line after loop\n”;
```

该语句的输出如下：

```
Last line in loop: counter=1
Last line in loop: counter=2
continue
Last line in loop: counter=4
Last line in loop: counter=5
First line after loop
```

与 `break` 语句循环不同，这个循环并没有在 `continue` 语句处结束。它只是停止了循环的第三次重复，并跳回循环顶部。随后在完成第四次第五次重复后完成循环，然后执行循环之后的语句。

`break` 语句的一个用途是防止无限循环。循环内部的以下语句可以在合理的点停止循环：

```php
$test4infinity++;
if ($test4infinity > 100 )
{
    break;
}
```

如果你确定循环永远不会重复超过 100 次，请使用这些语句在循环变得无止时停止它。根据你正在构建的循环使用任何认为合理的数字。

## 使用函数

应用程序通常在脚本的不同点或不同的脚本中执行相同的任务。函数的设计允许你在不同的位置重用相同的代码。`函数`是一组执行特定任务的 PHP 语句。你可以在任何需要执行该任务的地方使用函数。

例如，假设你在整个网站中频繁通过以下语句显示你的公司 Logo：

```php
echo “<p><img src=’Images/logo.jpg’ width=’50’ height=’50’ hspace=’10’ align=’left’ /></p>”;
echo “<p style=’font-size: x-large’>My Fine Company</p>”;
echo “<p style=’font-style: italic’>quality products</p>”;
```

与其在脚本中每个需要显示 Logo 的地方都输入这些代码，你可以创建一个包含这些语句的函数并将其命名为 `display_logo`。然后，你只需要在需要显示 Logo 的时候使用该函数即可。使用函数的形式如下：`display_logo();`。

你可以看到，使用这一行代码节省大量的大量的工作，并且比在每个需要 Logo 的地方输入 `echo` 语句更容易易读和理解。

### 创建函数

你可以通过将代码放入函数块中来创建一个函数。其通用格式如下：

```php
function functionname()
{
    // 语句块；
    return;
}
```

例如，你可以使用以下语句创建在前节中讨论的 `display_logo()` 函数：

```php
function display_logo()
{
    echo “<p><img src=’Images/logo.jpg’ width=’50’ height=’50’ hspace=’10’ align=’left’ /></p>”;
    echo “<p style=’font-size: x-large’>My Fine Company</p>”;
    echo “<p style=’font-style: italic’>quality products</p>”;
}
```

然后你可以在任何想要显示 Logo 的地方调用函数，如下：`display_logo();`。

函数末尾的 `return` 语句会停止函数并将控制交回调用脚本。然而，函数末尾不需要 `return` 语句，因为函数本身就会停止。`return` 语句使函数更易理解。`return` 语句将在“从函数返回值”节中进行详细讨论。

你可以在脚本的任何地方使用函数定义语句创建函数，但通常的做法是将所有函数放在脚本的开头或结尾。你计划在多个脚本使用的函数可以定义在单独的文件，并在任何需要这些函数的脚本中包含它。

### 在函数中使用变量

你可以在函数内部创建并使用变量。这种变量对于函数来说是`局部`的。然而，该变量在函数外部是不可用的；主脚本无法访问。如果你想在函数外部使用该变量，必须将其设为全局变量（`global`）。例如，变量 `$name` 在以下函数中创建：

```php
function format_name()
{
    $first_name = “John”;
    $last_name = “Smith”;
    $name = $last_name, “.$first_name;
}
format_name();
echo “$name”;
```

这些语句没有产生输出。在 `echo` 语句中，`$name` 不包含任何值。变量是在函数内部创建的，因此在函数外部不存在。

通过使用 `global` 语句，你可以在函数内部创建一个在外部存在的变量。以下语句在相同函数的基础上增加了 `global` 语句：

```php
function format_name()
{
    global $name;
    $first_name = “John”;
    $last_name = “Smith”;
    $name = $last_name, “.$first_name;
}
format_name();
echo “$name”;
```

脚本现在输出：Smith, John

你必须在使用该变量之前将其设为全局变量。如果 `global` 语句在 `$name` 赋值语句之后，脚本将不会产生输出。也就是说，在前面的函数中，如果 `global` 语句在 `$name =` 语句之后，函数将无法正常工作。

同样，如果变量是在函数外部创建的，除非它是全局的，否则你无法在函数内部使用它。在以下语句中， `global` 语句在函数内部：

```php
$first_name = “John”;
$last_name = “Smith”;
function format_name()
{
    global $first_name, $last_name;
    $name = $last_name, “.$first_name;
    echo “$name”;
}
format_name();
```

由于代码没有在函数外部包含全局声明（`global`），函数内部的 `$last_name` 和 `$first_name` 与函数外创建的 `$last_name` 和 `$first_name` 是不同的变量。函数内部的变量 `$last_name` 和 `$first_name` 在你命名它们时创建，且没有值。因此，`$name` 只输出一个逗号，如下：

,

为了让函数正常工作，你需要 `global` 语句。

## 向函数传递值

你可以在调用函数时通过将值放在括号之间来向函数传递值，如下所示：

```php
functionname(value, value,...);
```

当然，变量不能凭空出现。函数必须接收这些变量。函数语句包含了它所期望的值的变量名，如下：

```php
function functionname($varname1, $varname2,...)
{
    $statements
    return;
}
```

例如，以下函数计算销售税：

```php
function compute_salestax($amount, $custState)
{
    switch ($custState)
    {
        case "OR":
            $salestaxrate = 0;
            break;
        case "CA":
            $salestaxrate = 1.0;
            break;
        default:
            $salestaxrate = .5;
            break;
    }
    $salestax = $amount * $salestaxrate;
    echo "$salestax<br />";
}
```

第一行显示该函数期望两个值—— `$amount` 和 `$custState`。当你调用函数时，你向它传递两个值，如下：

```php
$amount = 2000.00;
$custState = "CA";
compute_salestax($amount, $custState);
```

在这种情况下，传递的金额是 2000.00，州是 CA。输出是 2000，因为 CA 的 `$salestaxrate` 为 1.0。

## 传递正确类型的值

你可以直接传递值（包括计算后的值），也可以传递包含值的变量。以下调用是有效的：

```php
compute_salestax(2000,"CA");
compute_salestax(2*1000,"");
compute_salestax(2000,"C". "A");
```

你可以传递任何数据类型的值。请参见本微型书籍第 1 章关于数据类型的讨论。通常，你想要测试传递的值以检查它们是否为预期的数据类型。例如，以下函数期望一个数组：

```php
function add_numbers($numbers)
{
    if(is_array($numbers))
    {
        for($i=0; $i < sizeof($numbers); $i++)
        {
            $sum = $sum + $numbers[$i];
        }
        echo $sum;
    }
    else
    {
        echo "value passed is not an array";
        return;
    }
}
```

你可以使用以下语句调用 `add_numbers` 函数：

```php
$arrayofnumbers = array(100,200);
add_numbers($arrayofnumbers);
```

该函数显示 300，即 100 加 200 的和。如果传递的值不是数组，如下所示：

```php
add_numbers(100);
```

该函数显示消息：`value passed is not an array`。

## 按正确顺序传递值

函数按照传递的顺序接收值。也就是说，假设你有如下函数：

```php
functionx($x,$y,$z)
{
    do stuff
}
```

你按照如下方式调用函数：

```php
functionx($var1,$var2,$var3);
```

`functionx` 设置 `$x=$var1`、`$y=$var2` 和 `$z=$var3`。如果你传递的值不符合预期顺序，函数在执行任务时将使用错误的值。例如，也许你计算销售税的函数定义如下：

```php
function compute_salestax($orderCost,$custState)
{
    // compute tax
}
```

`$orderCost` 是订单成本，而 `$custState` 是客户居住的州。但假设你使用了以下调用：

```php
compute_salestax($custState,$orderCost);
```

函数将 `$custState` 变量的值作为订单成本，由于它是字符串，函数将其设为 0。它将 `$orderCost` 变量设置为数字，但这与它的任何分类都不匹配。输出将是 0。

## 传递正确数量的值

函数被设计为接收特定数量的值。如果你发送的值不够，函数会将缺漏的值设为 `NULL`。如果你开启了警告消息，则会显示警告消息（描述请参阅本微型书籍第 1 章中错误信息的章节）。例如，假设你有如下格式化名称的函数：

```php
function format_name($first_name,$last_name)
{
    $name = "$last_name, $first_name";
    echo $name;
}
```

该函数期望接收两个值。假设你向它传递了两个值。...（此处原文后续似乎存在逻辑混乱或重复的乱码，已按预期逻辑翻译翻译）

如果你想让函数将值返回给主脚本，请使用 `return` 语句。主脚本可以将该值放入变量中，或以处理任何值的方式使用它。

## 从函数返回值

要从函数返回一个值，请在函数内部编写 `return` 语句。通用格式如下：

`return value;`

例如，两个数字相和的函数可能如下：

```php
function add_2_numbers($num1,$num2)
{
$total = $num1 + $num2;
return $total;
}
```

返回两个数字之和。你如下所示调用该函数：

```php
$sum = add_2_numbers(5,6);
```

此时`$sum` 等于函数返回的 `$total` 中的值 —— 11。事实上，我们可以使用快捷方式，通过一条语句将总和返回给主脚本：

```php
return $num1 + $num2;
```

主脚本可以使用任何常规方式使用该值。以下语句以有效的方式使用了函数调用：

```php
$total_height = add_2_numbers($height1,$height2);
$totalSize = $current_size + add_2_numbers($size1,$size2);
if (add_2_numbers($costSocks,$costShoes) > 200.00 )
$echo “No sale”;
```

`return` 语句只能返回一个值。然而，返回的值可以是一个数组，因此你实际上可以从函数中返回多个值。

你可以在条件语句中使用 `return` 语句来结束函数，如下：

```php
function find_value($array,$value)
{
for($i=1;$i<sizeof($array);$i++)
{
if($array[$i] = $value)
{
echo “$i. $array[$i]<br />”;
return;
}
}
}
}
```

该函数检查数组中是否包含某个值。例如，你可以使用以下语句调用函数：

```php
$names = array(“Joe”,”Sam”，“Juan”);
find_value($names，“Sam”);
```

该函数遍历数组中的值以寻找 `Sam`。如果找到了 `Sam`，它就会停止搜索。输出显示找到 `Sam` 的数组项，如下：

1. Sam

通常函数设计为返回布尔值（`true` 或 `false`），如下函数所示：

```php
function is_over_100($number)
{
if($number > 100)
{
return true;
}
else
{
return false;
}
}
```

等于或小于 100 的数字返回 `false`；大于 100 的数字返回 `true`。另一种常见的函数设计是在函数成功时返回一个值，而在未成功时返回 `false`。例如，你可以这样设计 `find_value` 函数：

```php
function find_value($array,$value)
{
for($i=1;$i<sizeof($array);$i++)
{
if($array[$i] == $value)
{
return $i$;
}
}
return false;
}
```

如果函数在数组中找到了该值，它会返回找到 `$value` 的元素索引。但是，如果在数组任何地方都没有找到该值，它将返回 `false`。

## 组织脚本

### 使用内置函数

PHP 的许多内置函数是 PHP 如此强大且实用的原因之一。PHP 包含的函数都是普通函数。它们与你自己创建的函数没有区别。只是 PHP 已经为你完成了所有工作。

你可以像调用自己创建的函数一样使用 PHP 的内置函数。你只需要使用函数名并传递函数所需的任何值。

我们在整本书中都会讨论特定的 PHP 函数。例如，在本章的前面部分，我们讨论了几个可以用来检查变量是否存在或其是否为空的函数。这里是其中几个函数：

```php
isset($varname)
empty($varname)
```

PHP 在线文档在 `www.php.net/manual/en/funcref.php` 描述了所有内置函数。此外，PHP 文档提供了一个搜索功能，当你只记得函数名但记不住确切语法时它非常有用。在 Web 页面顶部的“Search For”文本框中输入函数名，并在下拉列表中选择 `Function List`。

### 使用 include 文件进行组织

脚本是一系列 PHP 语句，每条语句执行一个操作。PHP 从脚本开始并按顺序执行每条语句。某些语句是复杂语句，会条件性或重复地执行简单语句。

一个应用程序通常由多个 PHP 脚本组成。通常，一个脚本执行一个主要任务。例如，一个应用程序可能包含一个用于显示表单的脚本和一个将数据存储在数据库中的脚本。

然而，这只是准则而非规则。某些脚本既显示表单又处理数据。

每个脚本都应该组织成不同的部分。每个部分都以描述该部分作用的注释开头（我们在第二本书中会介绍注释）。用空行将各个部分隔开。例如，一个登录脚本可能如下：

```php
#显示登录表单
*显示登录表单的语句*

#检查用户名和密码
*检查用户名和密码的语句*
```

无论你何时需要执行该任务。创建和使用函数在本章稍后的“使用函数”部分中已经讨论过。

另一种重用代码的方法是将代码存储在单独的文件中并在需要的地方将该文件引入脚本。你可以通过 `include` 语句将外部文件引入脚本，这将在本书章节稍后的“使用 include 文件进行组织”部分进行讨论。

### 使用函数组织
