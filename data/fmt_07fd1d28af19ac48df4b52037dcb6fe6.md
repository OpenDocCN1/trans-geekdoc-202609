
```php
$indexArrDemo = array(11, 4, 5, 1, 2, 5, 6);
$assocArrDemo = array('A'=>12, 'B'=>5, 'C'=>20);
echo array_search(5, $indexArrDemo);
echo array_search(20, $assocArrDemo);
var_dump(array_search('B', $assocArrDemo));
```

输出：

`2`

`C`

`bool(false)`

在第一个 `echo` 语句中，我们使用 `array_search()` 函数在 `$indexArrDemo` 中搜索 `5`。虽然有两个 `5` 的实例，但只返回第一个匹配值的索引。在第二个 `echo` 语句中，我们使用 `array_search()` 在 `$assocArrDemo` 中搜索 `20`。我们得到了 `C`。

## `print_r()`

`print_r()` 函数与 `var_dump()` 函数类似。然而，它的输出更简洁，因为它没有给出每个元素的数据类型。例如，`print_r($myArray);`

给了我们以下输出：

```
Array ( [0] => 2 [1] => 5.1 [2] => PHP [3] => 105 )
```

## `array_merge()`

最后，我们有 `array_merge()` 函数。该函数合并两个多个数组并返回合并后的数组。

### 示例 1：

```php
$countDemo = array(1, 4, 5, 1, 2);
echo count($countDemo);
```

输出：

`5`

### 示例 2：

```php
$addDemo = array(1, 5, 3, 9);
$addDemo[] = 7;
```

在上面的示例中，我们向 `$addDemo` 添加了 `7`。数组变成了 `(1, 5, 3, 9, 7)`。

### 示例 3：

```php
$addDemoAssoc = array('Peter'=>20, 'Jane'=>15);
$addDemoAssoc['James'] = 17;
```

在这里，我们向 `$addDemoAssoc` 添加了 `'James'=>17`。数组变成了 `('Peter'=>20, 'Jane'=>15, 'James'=>17)`。

### 示例 4：

```php
$colors = array("red", "black", "pink", "white");
array_splice($colors, 2);
```

在这里，我们指示让 `array_splice()` 从 `$colors` 中删除所有元素，从位置 `2` 的元素（包括该元素）开始。`$colors` 变成了 `("red", "black")`。

### 示例 5：

```php
$awardwinners = array("Gold"=>"Max", "Silver"=>"Boots", "Bronze"=>"Dora");
array_splice($awardwinners, 1);
```

在这里，我们想要 `array_splice()` 从 `$awardwinners` 中删除所有元素，从位置 `1`（包括该元素）开始。`$awardwinners` 变成了 `("Gold"=>"Max")`。

### 示例 6：

```php
$pets = array("corgi", "poodle", "golden retriever", "jack russell");
array_splice($pets, 1, 2);
```

在这里，我们想要从 `$pets` 中删除 `2` 个元素，从位置 `1`（包括该元素）开始。`$pets` 变成了 `("corgi", "jack russell")`。

### 示例 7：

```php
$anotherAssocMDArr = array(
"first player" => array("name" => 'John', "age" => 25),
"second player" => array("name" => 'Tim', "age" => 35)
);
```

在上面的示例中，`$anotherAssocMDArr["first player"]` 存储了 `array("name" => 'John', "age" => 25)`。如果我们写：

```php
echo $anotherAssocMDArr["first player"]["age"];
```

我们将得到输出 `25`。

### 示例 8：

```php
$myArray = array(2, 5.1, 'PHP', 105);
var_dump($myArray);
```

输出：

```
array(4) { [0]=> int(2) [1]=> float(5.1) [2]=> string(3) "PHP" [3]=> int(105) }
```

### 示例 9：

```php
print_r($myArray);
```

输出：

```
Array ( [0] => 2 [1] => 5.1 [2] => PHP [3] => 105 )
```

### 示例 10：

```php
$indexArrDemo = array(11, 4, 5, 1, 2, 5, 6);
$assocArrDemo = array('A'=>12, 'B'=>5, 'C'=>20);
echo array_search(5, $indexArrDemo);
echo array_search(20, $assocArrDemo);
var_dump(array_search('B', $assocArrDemo));
```

输出：

`2`

`C`

`bool(false)`

### 示例 11：

```php
$countDemo = array(1, 4, 5, 1, 2);
echo count($countDemo);
```

输出：

`5`

### 示例 12：

```php
$num1 = array(100, 111, 120);
$num2 = array(1, 3, 5);
$result = array_merge($num1, $num2);
```

### 示例 13：

```php
$num1 = array(0 => "apple", 1 => "banana");
$num2 = array(0 => "cherry", 1 => "date");
$result = array_merge($num1, $num2);
```

当使用字符串键时，后面的值将覆盖具有相同字符串键的先值。

如果两边的值相等且数据类型相同，则返回 `true`（例如，`5 === 5` 返回 `true`，而 `5 === 5.0` 返回 `false`）。

不等于 (`!=` 或 `<>`)：如果两边的值不相等，则返回 `true`（例如 `5 != 7` 和 `5 <> 7` 均返回 `true`）。

不相同 (`!==`)：如果两边的值不相等或数据类型不相同，则返回 `true`（例如 `5 !== 5.0` 返回 `true`，因为 `5` 和 `5.0` 属于不同的数据类型）。

### 大于 (`>`)

如果左侧的值大于右侧的值，则返回 `true`（例如 `7 > 2` 返回 `true`）。

### 大于等于 (`>=`)

如果左侧的值大于或等于右侧的值，则返回 `true`（例如 `8 >= 5` 和 `6 >= 6` 均返回 `true`）。

### 小于 (`<`)

如果左侧的值小于右侧的值，则返回 `true`（例如 `9 < 12` 返回 `true`）。

### 小于等于 (`<=`)

如果左侧的值小于或等于右侧的值，则返回 `true`（例如 `10 <= 14` 和 `13 <= 13` 均返回 `true`）。

### 船位运算符 (`<=>`)

PHP 7 中引入。

如果两边的值相等（不一定完全相同），则返回 `0`。

如果左侧的值大，返回 `1`。

如果左侧的值小，返回 `-1`（例如 `5 <=> 7` 返回 `-1`，而 `5 <=> 5.0` 返回 `0`）。

## 6.2 逻辑运算符

接下来，我们有一组逻辑运算符。常用的运算符包括：

### NOT

NOT (`!`) 运算符当它跟在一个为假的表达式之前时返回 `true`。例如，`!(5 > 10)` 返回 `true`，因为 `5 > 10` 是假的（即 `5` 不大于 `10`）。

### AND

AND 运算符允许我们组合两个比较，并在两个比较都为 `true` 时返回 `true`。我们可以使用 `and` 关键字（不区分大小写）或 `&&` 符号。两者相似，但优先级不同。让我们来看一些示例：

示例 1：

```php
$a = 5 > 3 and 4 < 10;
$b = 5 > 3 && 4 < 10;
$c = 5 > 1 && 13 < 5;
var_dump($a);
var_dump($b);
var_dump($c);
```

输出：

`bool(true) bool(true) bool(false)`

在上面的示例中，`$a` 和 `$b` 为 `true`，因为两个比较（`5 > 3` 和 `4 < 10`）都是 `true`。相比之下，`$c` 为 `false`，因为第二个比较（`13 < 5`）为 `false`。

示例 2：

```php
$d = 3 > 2 && 3 < 1;
$e = 3 > 2 and 3 < 1;
var_dump($d);
var_dump($e);
```

输出：

`bool(false) bool(true)`

此示例说明了 `and` 关键字与 `&&` 符号之间的优先级差异。`&&` 的优先级高于赋值运算符 (`=`)。因此，语句 `$d = 3 > 2 && 3 < 1;` 的评估方式为：

`$d = (3 > 2 && 3 < 1);`

`$d` 为 `false`，因为 `3 < 1` 为假。相比之下，`and` 关键字的优先级低于赋值运算符。因此，语句 `$e = 3 > 2 and 3 < 1;` 的评估方式为：

`($e = 3 > 2) and 3 < 1;`

`$e` 为 `true`，因为只有第一个比较（`3 > 2`）的结果被赋值给了它。在大多数情况下，由于优先级更高，优于使用 `&&`。

### OR

接下来是 OR 运算符。当至少有一个比较为 `true` 时，该运算符返回 `true`。我们可以使用 `or` 关键字或 `||` 符号。不过，我鼓励你使用 `||`，因为它优先级更高。

示例：

```php
$f = 4 < 7 || 10 > 3;
$g = 3 < 2 || 3 > 1;
$h = 10 > 15 || 12 < 1;
var_dump($f);
var_dump($g);
var_dump($h);
```

输出：

`bool(true) bool(true) bool(false)`

`$f` 为 `true`，因为两个比较都是 `true`。`$g` 为 `true`，即使第一个比较（`3 < 2`）为假。这是因为 `||` 只需要至少有一个比较为真。`$h` 为 `false`，因为没有任何比较为真。

## 3. 控制结构

现在我们已经熟悉了比较，准备好讨论 PHP 中的各种控制结构了。

### 3.1 If 语句

第一个是 `if` 语句。该语句允许程序评估是否满足特定条件，并根据评估结果执行适当的操作。`if` 语句的语法如下：

```php
if (条件 1) {
    // 执行任务 A
} elseif (条件 2) {
    // 执行任务 B
} elseif (条件 3) {
    // 执行任务 C
} else {
    // 执行任务 D
}
```

让我们来看一个真实的示例：

```php
$a = 7;
if ($a < 0) {
    echo '第一块';
} elseif ($a < 5) {
    echo '第二块';
} elseif ($a < 10) {
    echo '第三块';
} else {
    echo 'else 块';
}
```

如果 `$a` 是 `7`，输出将是 `'第三块'`。

### 3.2 三元运算符

接下来，让我们讨论三元运算符。在之前的示例中，我们有一个相对复杂的 `if` 语句。如果你只想进行简单的 if-else 测试（没有 `elseif` 块），可以使用三元运算符 (`?`)。语法为：`条件 ? 任务 A : 任务 B`。

三元运算符首先检查左侧的条件。如果为真，执行任务 A。否则，执行任务 B。

示例：

```php
$a = (7 == 7 ? 'Yes' : 'No');
echo $a;
```

这里的测试条件是 `7 == 7`。由于该条件成立，三元运算符执行第一个任务并返回字符串 `'Yes'`。我们将该字符串赋值给 `$a`，并使用 `echo` 语句在下一行显示其值。

### 3.3 Switch 语句

接下来，我们有 `switch` 语句。该语句与 `if` 语句类似，如果有许多条件需要测试，它的速度更快。它通常用于条件涉及将变量与单个值比较（而不是值范围）。语法如下：

```php
switch (用于切换的变量) {
    case 情况情况:
        任务 A;
        break;
    case 第二种情况:
        任务 B;
        break;
    default:
        默认任务;
}
```

示例：

```php
$b = 20;
switch ($b) {
    case 10:
        echo '巧克力';
        break;
    case 20:
        echo '柠檬';
        break;
    case 25:
        echo '草莓';
        break;
    default:
        echo '默认任务';
}
```

如果 `$b` 是 `20`，输出将是 `'柠檬'`。

```php
14echo 'None of the above<BR>'; 15 }
```

在上面的示例中，我们首先声明了一个名为 `$b` 的变量并赋值为 `20`。

接下来，我们有一个从第 3 行到第 15 行的 `switch` 语句。在第 3 行，`switch` 语句使用 `$b` 的值来决定执行哪个 `case`。当满足某个 `case` 时，将执行从下一行开始的所有内容，直到遇到 `break` 语句。如果 `$b` 为 `10`，则满足 `case10`。程序将执行第 5 行之后的所有内容，直到遇到第 7 行的 `break` 语句。换句话说，它执行了第 6 行并输出 `"Chocolate"` 作为输出。另一方面，如果 `$b` 为 `20`，则满足 `case20`。然而，这个 `case` 没有 `break` 语句。因此，程序将执行从第 9 行开始的所有内容，直到遇到第 12 行的 `break` 语句。换句话说，它执行了 `case20` 和 `case25`，并依次输出 `"Lemon"` 和 `"Strawberry"`。接下来，如果 `$b` 为 `25`，则满足 `case25`。程序执行第 11 行并输出 `"Strawberry"` 作为输出。最后，如果 `$b` 不是 `10`、`20` 或 `25`，则执行 `default` case，我们将得到 `"None of the above"` 作为输出。

`default` case 是可选的。此外，我们可以在 `switch` 语句中包含任意数量的 `cases`。在示例中，我们有三个 `cases`。如果你运行上面的 `switch` 语句，你将得到：

Lemon

Strawberry

作为输出。尝试将第 1 行的 `$b` 修改为其他值并重新运行代码，以充分理解 `switch` 语句的工作原理。

### 3.4 For 循环

接下来，让我们来看下 `for` 循环。这种控制结构会重复执行一个代码块，直到测试条件不再有效。其语法如下：

```
for (初始值; 测试条件; 值的修改) 
{ //执行某些任务
}
```

让我们看一个示例：

```
for ($c = 1; $c < 5; ++$c){ 
  echo 'The value of $c is '.$c.'<BR>'; 
}
```

`for` 循环的重点是第一行。该行包含三个部分，每个部分由分号隔开。在我们的示例中，有这一行：`for ($c = 1; $c < 5; ++$c)`。

第一部分声明了一个变量 `$c` 并将其初始化为 `1`。第二部分测试 `$c` 是否小于 `5`。如果是，将执行随其后的大括号内部的语句。在我们的示例中，由于只有一个语句要执行，因此大括号是可选的。在执行完大括号中的语句后，程序返回到第三部分（`++$c`）。这部分修改用于测试的变量的值。在我们的示例中，我们使用自增运算符将 `$c` 的值加 `1`。结果是 `$c` 变成了 `2`。自增后，程序测试 `$c` 的新值是否仍然小于 `5`。如果是，它会再次执行大括号中的代码。这种测试和更新 `$c` 的值将不断重复，直到条件 `$c < 5` 不再为真。此时，程序退出。

### 3.5 Foreach 循环

接下来，让我们来看 `foreach` 循环。这种循环与 `for` 循环类似，但用于遍历数组。它有两种语法：

```
foreach ($array as $value) {
  //代码
}

foreach ($array as $key => $value) {
  //代码
}
```

假设我们有一个关联数组：

```
$arr2 = array('Aaron'=>12, 'Ben'=>23, 'Carol'=>35);
```

使用第一个 `foreach` 循环：

```
foreach ($arr2 as $name) { 
  echo $name.' is.' years old.'; 
}
```

这将输出 `Aaron is 12 years old, Ben is 23 years old, Carol is 35 years old`。

### 3.6 While 循环
