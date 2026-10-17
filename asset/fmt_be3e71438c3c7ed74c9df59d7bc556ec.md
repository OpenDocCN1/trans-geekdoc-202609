
```php
function someTypeHint(Array $a, DateTime $t, Callable $c)
{
    $message = '';
    $message .= 'Array Count: ' . count($a) . PHP_EOL;
    $message .= 'Date: ' . $t->format('Y-m-d') . PHP_EOL;
    $message .= 'Callable Return: ' . $c() . PHP_EOL;
    return $message;
}
```

> 你不需要为每个参数都提供类型提示。仅在传递不同数据类型会对函数的处理产生负面影响时使用此技术。例如，如果你的函数使用 `foreach()` 循环，而你未提供数组或实现了 `Traversable` 接口的对象，则会产生错误。

### 3. 在 PHP 7 中，假设已做出适当的 `declare()` 指令，则允许**标量**（即整型、浮点型、布尔型和字符串型）类型提示。另一个函数展示了如何实现这一点。在包含该函数的代码库文件顶部，紧跟在 PHP 开始标签之后添加此 `declare()` 指令：

```php
declare(strict_types=1);
```

### 4. 现在你可以定义包含标量类型提示的函数：

```php
function someScalarHint (bool $b, int $i, float $f, string $s) {
    return sprintf ("\n%20s : %5s\n%20s : %5d\n%20s " .
                    ": %5.2f\n%20s : %20s\n\n",
                    'Boolean', ($b ? 'TRUE' : 'FALSE') ,
                    'Integer' , $i,
                    'Float' , $f,
                    'String', $s);
}
```

### 5. 在 PHP 7 中，假设已声明严格类型提示，布尔类型提示的工作方式与其他三种标量类型（即整型、浮点型和字符串型）略有不同。你可以提供任何标量作为参数，且不会抛出 `TypeError`！然而，一旦传入函数，传入的值会自动转换为布尔数据类型。如果你传入除标量（即数组或对象）以外的任何数据类型，则会抛出 `TypeError`。下面是一个定义布尔数据类型的函数示例。请注意，返回值将自动转换为布尔值：

```php
function someBoolHint (bool $b)
{
    return $b;
}
```

### 工作原理……

首先，你可以将 `someTypeHint()`、`someScalarHint()` 和 `someBoolHint()` 这三个函数放入一个单独的文件中以便引入。在本例中，我们将该文件命名为 `chap_03_developing_functions_type_hints_library.php`。别忘了在顶部添加 `declare(strict_types=1)`！

在调用代码中，然后引入该文件：

```php
include (__DIR__ . DIRECTORY_SEPARATOR . 'chap_03_developing_functions_type_hints_library.php');
```

若要测试 `someTypeHint()`，请调用该函数两次，第一次使用正确的数据类型，第二次使用错误的类型。不过，这会抛出 `TypeError`，因此你需要将函数调用包裹在 `try { ... } catch ( ) { ... }` 块中：

```php
try {
    $callable = function () { return 'Callback Return'; };
    echo someTypeHint ([1,2,3], new DateTime(), $callable);
    echo someTypeHint ('A', 'B', 'C');
} catch (TypeError $e) {
    echo $e->getMessage();
    echo PHP_EOL;
}
```

正如你在本小节末尾显示的输出结果中看到的，传递正确的数据类型时没有问题。当传递错误的类型时，会抛出 `TypeError`。

![](img/39390f6d56c5a83b28db083a8bd5185c_83_0.png)

> 在 PHP 7 中，某些错误已被转换为 `Error` 类，其处理方式与 `Exception` 类有些相似。这意味着你可以捕获 `Error`。`TypeError` 是 `Error` 的一个特定子类，在将错误的数据类型传递给函数时抛出。PHP 7 中所有 `Error` 类都实现了 `Throwable` 接口，`Exception` 类也是如此。如果你不确定是否需要捕获 `Error` 还是 `Exception`，可以添加一个捕获 `Throwable` 的代码块。

接下来你可以测试 `someScalarHint()`，使用正确和错误的值各调用一次，并将调用包裹在 `try { ... } catch () { ... }` 块中：

```php
try {
    echo someScalarHint(TRUE, 11, 22.22, 'This is a string');
    echo someScalarHint('A', 'B', 'C', 'D');
} catch (TypeError $e) {
    echo $e->getMessage();
}
```

预期之中，第一次调用函数成功，第二次抛出 `TypeError`。

当进行布尔值的类型提示时，传递任何标量值都不会导致抛出 `TypeError`！相反，该值会被解释为其布尔等价物。如果你随后返回此值，数据类型将变为布尔型。

若要测试这一点，请调用前面定义的 `someBoolHint()` 函数，并传入任意标量值作为参数。`var_dump()` 方法显示数据类型始终为布尔型：

```php
try {
    // 正向结果
    $b = someBoolHint(TRUE);
    $i = someBoolHint(11);
    $f = someBoolHint(22.22);
    $s = someBoolHint('X');
    var_dump($b, $i, $f, $s);
    // 反向结果
    $b = someBoolHint(FALSE);
    $i = someBoolHint(0);
    $g = someBoolHint(0,0);   
    $$s = someBoolHint('');
    var_dump($b, $i, $f, $s);
} catch (TypeError $e) {
    echo $e->getMessage();
}
```

如果你现在尝试相同的函数调用，但传入非标量数据类型，则会抛出 `TypeError`：

```php
try {
    $a = someBoolHint([1,2,3]);
    var_dump($a);
} catch (TypeError $e) {
    echo $e->getMessage();
}
try {
    $o = someBoolHint(new stdClass());
    var_dump($o);
} catch (TypeError $e) {
    echo $e->getMessage();
}
```

这是整体输出结果：

![](img/39390f6d56c5a83b28db083a8bd5185c_84_0.png)

## 另请参阅

PHP 7.1 引入了一种新的类型提示 `iterable`，它允许使用数组、`Iterators` 或 `Generators` 作为参数。请查阅此处获取更多信息：

- https://wiki.php.net/rfc/iterable

关于实现标量类型提示背后的基本原理的背景讨论，请查看这篇文章：

- https://wiki.php.net/rfc/scalar_type_hints_v5

## 使用返回值数据类型

PHP 7 允许你指定函数的返回值数据类型。然而，与标量类型提示不同，你无需添加任何特殊声明。

### 如何实现……

1. 本示例向你展示如何为函数返回值分配数据类型。要分配返回数据类型，首先像往常一样定义函数。在右括号之后，添加一个空格，然后依次加上数据类型和冒号：

```php
function returnsString(DateTime $date, $format) : string
{
    return $date->format($format);
}
```

![](img/39390f6d56c5a83b28db083a8bd5185c_85_0.png)

> PHP 7.1 引入了一种返回数据类型变化的形式，称为**可空类型**。你只需将 `string` 改为 `?string`。这允许函数返回 `string` 或 NULL。

2. 无论函数内部的数据类型如何，函数返回的任何值都会作为返回值转换为声明的数据类型。注意，在此示例中，`$a`、`$b` 和 `$c` 的值被相加产生一个总和并返回。通常，我们期望返回值是数值数据类型。然而，在这种情况下，返回数据类型被声明为 `string`，这覆盖了 PHP 的类型转换过程：

```php
function convertsToString($a, $b, $c) : string
{
    return $a + $b + $c;
}
```

3. 你还可以将类作为返回数据类型。在这个例子中，我们指定返回类型为 **DateTime**，它是 PHP **DateTime** 扩展的一部分：

```php
function makesDateTime($year, $month, $day) : DateTime
{
    $date = new DateTime();
    $date->setDate($year, $month, $day);
    return $date;
}
```

`makesDateTime()` 函数可能是标量类型提示的良好候选者。如果 `$year`、`$month` 或 `$day` 不是整数，在调用 `setDate()` 时会产生一个 `Warning`（警告）。如果你使用标量类型提示，且传入了错误的数据类型，则会抛出 `TypeError`（类型错误）。虽然产生警告还是抛出 `TypeError` 其实无所谓，但抛出 `TypeError` 至少能让那些误用你代码的开发者警醒起来！

4. 如果一个函数有返回数据类型，而你在函数代码中返回了错误的数据类型，则会在运行时抛出 `TypeError`。此函数指定了 `DateTime` 作为返回类型，但实际上返回了一个字符串。将会抛出 `TypeError`，但这不会立即发生，而是等到运行时 PHP 引擎检测到这种不一致时才会发生：

```php
function wrongDateTime($year, $month, $day) : DateTime
{
    return date($year . '-' . $month . '-' . $day);
}
```

如果返回数据类型类不是内置 PHP 类之一（即不是 SPL 的一部分），你需要确保该类已被自动加载或被包含进来。

## 工作原理...

首先，将前面提到的函数放入一个名为 `chap_03_developing_functions_return_types_library.php` 的库文件中。该文件需要在调用这些函数的 `chap_03_developing_functions_return_types.php` 脚本中包含：

```php
include (__DIR__ . '/chap_03_developing_functions_return_types_library.php');
```

现在你可以调用 `returnsString()`，并传入一个 `DateTime` 实例和一个格式字符串：

```php
$date = new DateTime();
$format = 'l, d M Y';
$now = returnsString($date, $format);
echo $now . PHP_EOL;
var_dump($now);
```

如预期那样，输出是一个字符串：

![](img/39390f6d56c5a83b28db083a8bd5185c_87_0.png)

现在你可以调用 `convertsToString()` 并传入三个整数作为参数。注意返回类型是字符串：

```php
echo "\nconvertsToString()\n";
var_dump(convertsToString(2, 3, 4));
```

![](img/39390f6d56c5a83b28db083a8bd5185c_87_1.png)

为了演示可以将类作为返回值进行赋值，调用 `makesDateTime()` 并传入三个整型参数：

```php
echo "\nmakesDateTime()\n";
$d = makesDateTime(2015, 11, 21);
var_dump($d);
```

![](img/39390f6d56c5a83b28db083a8bd5185c_87_2.png)

最后，调用 `wrongDateTime()` 并传入三个整型参数：

```php
try {
    $e = wrongDateTime(2015, 11, 21);
    var_dump($e);
} catch (TypeError $e) {
    echo $e->getMessage();
}
```

注意，在运行时抛出了 `TypeError`：

![](img/39390f6d56c5a83b28db083a8bd5185c_88_0.png)

## 更多知识...

PHP 7.1 添加了一种新的返回值类型：`void`。当你不希望从函数中返回任何值时使用它。有关更多信息，请参阅 [https://wiki.php.net/rfc/void_return_type](https://wiki.php.net/rfc/void_return_type)。

## 另请参阅

有关返回类型声明的更多信息，请参阅以下文章：

- http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration.strict
- https://wiki.php.net/rfc/return_types

有关可空类型的信息，请参阅此文章：

- https://wiki.php.net/rfc/nullable_types

## 使用迭代器

`迭代器`（iterator）是一种特殊的类，允许你`遍历`（traverse）*容器*或列表。这里的关键词是*遍历*。这意味着迭代器提供了遍历列表的手段，但它本身并不执行遍历。

SPL 提供了丰富的通用和专用迭代器，适用于不同的上下文。例如，`ArrayIterator` 旨在允许对数组进行面向对象的遍历。`DirectoryIterator` 旨在用于文件系统扫描。

某些 SPL 迭代器旨在与其他迭代器协同工作，并增加其价值。示例包括 `FilterIterator` 和 `LimitIterator`。前者允许你从父迭代器中移除不需要的值。后者提供分页功能，你可以指定要遍历的项目数量以及确定起始位置的偏移量。

最后，有一系列*递归*迭代器，允许你重复调用父迭代器。一个例子是 `RecursiveDirectoryIterator`，它扫描目录树，从起点一直扫描到最后一个可能的子目录。

## 实现方法...

1. 我们首先查看 `ArrayIterator` 类。它极其易于使用。你所需要做的只是在构造器中提供一个数组作为参数。之后，你可以使用所有基于 SPL 的迭代器所特有的任何标准方法，例如 `current()`、`next()` 等。

```php
$iterator = new ArrayIterator($array);
```

![](img/39390f6d56c5a83b28db083a8bd5185c_89_0.png)

2. 作为一个迭代器实际用途的例子，看看这个示例。它接受一个迭代器并生成一系列 HTML `<ul>` 和 `<li>` 标签：

```php
function htmlList($iterator)
{
    $output = '<ul>';
    while ($value = $iterator->current()) {
        $output .= '<li>' . $value . '</li>';
        $iterator->next();
    }
    $output .= '</ul>';
    return $output;
}
```

3. 或者，你可以简单地将 `ArrayIterator` 实例包裹在一个简单的 `foreach()` 循环中：
