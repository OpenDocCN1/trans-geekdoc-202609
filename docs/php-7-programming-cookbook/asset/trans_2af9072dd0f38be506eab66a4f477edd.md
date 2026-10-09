

## 工作原理……

最佳实践是将所有逻辑相关的函数放入一个单独的 PHP 文件中。创建一个名为 `chap_03_developing_functions_library.php` 的文件，并将这些函数（前文已描述）放入其中：

- someName()
- someOtherName()
- someInfinite()
- someDirScan()
- someTypeHint()

然后，在调用这些函数的代码中引入该文件。

```php
include (__DIR__ . DIRECTORY_SEPARATOR . 'chap_03_developing_functions_library.php');
```

若要调用 `someName()` 函数，请使用该函数名称并提供参数。

```php
echo someName('TEST');    // 返回 "INIT" 以及 TEST"
```

你可以使用一个或两个参数来调用 `someOtherName()` 函数，如下所示：

```php
echo someOtherName(1);     // 返回  1
echo someOtherName(1, 1);  //  返回 2
```

`someInfinite()` 函数接受无限（或可变）数量的参数。以下是调用此函数的几个示例：

```php
echo someInfinite(1, 2, 3);
echo PHP_EOL;
echo someInfinite(22.22, 'A', ['a' => 1, 'b' => 2]);
```

## 使用 PHP 函数式编程

输出结果如下：

![](img/39390f6d56c5a83b28db083a8bd5185c_80_0.png)

我们可以按照以下方式调用 `someDirScan()`：

```php
echo someInfinite(1, 2, 3);
echo PHP_EOL;
echo someInfinite(22.22, 'A', ['a' => 1, 'b' => 2]);
```

输出结果如下：

![](img/39390f6d56c5a83b28db083a8bd5185c_80_1.png)

## 提示数据类型

在许多开发函数的场景中，你可能需要在其他项目中重用相同的函数库。此外，如果你在一个团队中工作，你的代码可能会被其他开发人员使用。为了控制代码的使用，采用**类型提示**可能更为合适。这涉及指定你的函数对特定参数所期望的数据类型。

### 如何实现……

1.  函数中的参数可以加上类型提示前缀。以下类型提示在 PHP 5 和 PHP 7 中均可用：
    - Array
    - Class
    - Callable
2.  如果调用函数时传递了错误的参数类型，则会抛出 TypeError。以下示例要求一个数组、一个 DateTime 实例以及一个匿名函数：

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

    > 你不需要为每个参数都提供类型提示。仅在传递不同数据类型会对函数的处理产生负面影响时使用此技术。例如，如果你的函数使用 `foreach()` 循环，而你未提供数组或实现了 Traversable 接口的对象，则会产生错误。
3.  在 PHP 7 中，假设已做出适当的 `declare()` 指令，则允许**标量**（即整型、浮点型、布尔型和字符串型）类型提示。另一个函数展示了如何实现这一点。在包含该函数的代码库文件顶部，紧跟在 PHP 开始标签之后添加此 `declare()` 指令：

    ```php
    declare(strict_types=1);
    ```

4.  现在你可以定义包含标量类型提示的函数：

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

5.  在 PHP 7 中，假设已声明严格类型提示，布尔类型提示的工作方式与其他三种标量类型（即整型、浮点型和字符串型）略有不同。你可以提供任何标量作为参数，且不会抛出 TypeError！然而，一旦传入函数，传入的值会自动转换为布尔数据类型。如果你传入除标量（即数组或对象）以外的任何数据类型，则会抛出 TypeError。下面是一个定义布尔数据类型的函数示例。请注意，返回值将自动转换为布尔值：

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

若要测试 `someTypeHint()`，请调用该函数两次，第一次使用正确的数据类型，第二次使用错误的类型。不过，这会抛出 TypeError，因此你需要将函数调用包裹在 `try { ... } catch ( ) { ... }` 块中：

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

如果你现在尝试相同的函数调用，但传入非标量数据类型，则会抛出 TypeError：

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

1.  本示例向你展示如何为函数返回值分配数据类型。要分配返回数据类型，首先像往常一样定义函数。在右括号之后，添加一个空格，然后依次加上数据类型和冒号：

    ```php
    function returnsString(DateTime $date, $format) : string
    {
        return $date->format($format);
    }
    ```

    ![](img/39390f6d56c5a83b28db083a8bd5185c_85_0.png)

    > PHP 7.1 引入了一种返回数据类型变化的形式，称为**可空类型**。你只需将 `string` 改为 `?string`。这允许函数返回 `string` 或 NULL。
2.  无论函数内部的数据类型如何，函数返回的任何值都会作为返回值转换为声明的数据类型。注意，在此示例中，`$a`、`$b` 和 `$c` 的值被相加产生一个总和并返回。通常，我们期望返回值是数值数据类型。然而，在这种情况下，返回数据类型被声明为 `string`，这覆盖了 PHP 的类型转换过程：

    ```php
    function convertsToString($a, $b, $c) : string
    {
        return $a + $b + $c;
    }
    ```

