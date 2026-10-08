

## 检查基本函数结构

你的做法与脚本中其他地方的相同——使用一个 PHP 结束标签，后跟 HTML：以下是对前面示例的合法修改，并会产生相同的输出：

```php
<?php
function my_function() {
?>
My function was called
<?php
}
?>
```

注意，PHP 代码被包含在匹配的 PHP 开启和结束标签之间。对于书中大多数短代码示例，我们没有显示这些标签。我们在这里显示它们是因为它们在示例中以及示例的上方和下方都是必须的。

## 命名你的函数

在命名函数时需要考虑的最重要的一点是，名称应该短且具有描述性。如果你创建一个页面页眉，`pageheader()`、`page_header()`、`draw_header()` 等可能都是很好的名称。

有以下几个限制：

- 你的函数名不能与现有函数重名。
- 你的函数名只能包含字母、数字和下划线。
- 你的函数名不能以数字开头。

许多语言允许重用函数名。这种特性被称为函数重载。然而，PHP 不支持函数重载，因此你的函数不能与任何内置函数或用户定义函数同名。（类内部存在某种形式的载，我们在第 6 章“面向对象的 PHP”中会讨论，但它与大多数语言的重载版本不同。）注意，尽管 PHP 脚本知道全局作用域内的所有内置函数，但用户定义函数仅存在于它们声明的脚本中。这意味着你可以在不同的文件中重用函数名，但这会导致混淆并应该避免。

以下函数名是合法的：

```php
name()
name2()
name_three()
name_four()
```

这些名称是非法的：

```php
name()
name-six()
fopen()
```

如果 `fopen` 已经作为 PHP 本身的一部分存在，它是合法的。

注意，虽然 `$name` 不是一个有效的函数名，但像 `$name();` 这样的函数调用可能会执行，取决于 `$name` 的值。原因是 PHP 会获取存储在 `name` 中的值，寻找同名的函数并尝试调用它。这种类型的函数被称为变量函数。

## 使用参数

为了完成你的工作，函数需要一个或多个参数。参数允许你将数据传递到函数中。这是一个需要参数的示例函数；它接收一个一维数组并将其作为表格：

```php
function create_table($data) {
  echo '<<table>>';
  reset($data);
  $value = current($data);
  while ($value) {
    echo '<tr><td>$value</td></tr>\n';
    $value = next($data);
  }
  echo '</table>';
}
```

如果你如下所示调用 `create_table()` 函数：

```php
$my_data = ['First piece of data','Second piece of data','And the third'];
create_table($my_data);
```

你将看到如图 5.4 所示的输出。

![](img/654520c37415debd4290b9b4aa2c03f2_177_0.png)

图 5.4 此 HTML 表格是调用 create_table() 的结果

## 使用参数 147

传递参数允许你将函数外部创建的数据（在这种情况下是数组 `$my_data`）引入函数中。

与内置函数一样，用户定义函数可以有多个参数和可选参数。你可以通过许多方式改进 `create_table()` 函数，一种方法是允许调用者指定其他属性，但你可以可选地设置表格的标题（caption），这里是函数的改进版本；它很类似，但允许你可选地设置表格的标题：

```php
function create_table($data, $header=NULL, $caption=NULL) {
  echo '<<table>>';
  if ($caption) {
    echo "<caption>$caption</caption>";
  }
  if ($header) {
    echo "<tr><td>$header</th></tr></tr>";
  }
  reset($data);
  $value = current($data);
  while ($value) {
    echo "<tr><td>$value</td><td>$value</td></tr>\n";
    $value = next($data);
  }
  echo '</table>';
}
```

```php
$my_data = ['First piece of data','Second piece of data','And the third'];
$my_header = 'Data about something';
$my_caption = '$my_data, $my_header, $my_caption';
create_table($my_array);
```

`create_table()` 的第一个参数仍然是。接下来两个是可选的，因为为它们定义了默认值。你可以通过此调用 `create_table()` 创建与图 5.4 所示类似的输出：

```php
create_table($my_array, 'A header');
```

如果你想在有表头但没有标题的情况下显示相同的数据，可以如下调用函数：

可选值并不需要全部提供；你可以提供一些并忽略另。参数从左到右分配。

请记住，你不能跳过一个可选参数但包含后面列出的一个。在这个示例中，如果你想...

## 理解作用域

你可能注意到，当我们使用 `require()` 和 `include()` 时，作用域的行为有所不同。PHP 有相当简单的规则：

- 在函数内部声明的变量的作用域从声明它们的语句开始到函数结束。这被称为函数作用域。这些被称为局部变量。
- 在函数外部声明的变量的作用域从声明它们的语句到文件结束。这被称为全局作用域。这些被称为全局变量。

- 特殊的全局变量在函数内部和外部都是可见的。（更多信息请参见第 1 章“PHP课程”。）

- `require()` 和 `include()` 语句不影响作用域。如果语句在函数内部，则应用函数作用域。不在函数内部，则应用全局作用域。

- `global` 关键字可以手动指定函数内部定义或使用的变量具有全局作用域。

- 可以通过 `unset($variable_name)` 手动删除变量。如果变量被删除，它就不再在作用域内。

以下示例有助于澄清作用域：
以下代码没有产生输出。在这里，我们在 `fn()` 内部声明了一个变量 `$var`。因为它在函数内部，它具有函数作用域，仅在声明处到函数结束有效。当你在外部引用 `$var` 时，会创建一个名为 `$var` 的新变量。这个新变量具有全局作用域，直到文件结束。遗憾，如果你对这个 `$var` 使用的唯一语句是 `echo`，它永远不会值。

```php
function fn() {
$var = "contents";
}
fn();
echo $var;
```

以下示例是相反的。在这里，你在函数外部声明变量，然后在函数内部使用它：

```php
<?php
function fn() {
echo 'inside the function, at first $var = ''.$var.'<br />';
$var = 2;
echo 'then, inside the function, $var = ''.$var.'<br />';
}
$var = 1;
fn();
echo 'outside the function, $var = ''.$var.'<br />';
?>
```

此代码的输出如下：
inside the function, at first $var = 
then inside the function, $var = 2
outside the function, $var = 1

