

# 基础计算机编码：PHP

```php
public $john = "John Smith";
public $jane = "Jane Smith";
public $robert = "Robert Paulsen";

public $smith = "Smith";
}

$people = new people();

```php
echo "\$people->john drank \$some[0] juice".PHP_EOL;
echo "\$people->john said hello to \$people->jane".PHP_EOL;
echo "\$people->wife greeted \$people->robert".PHP_EOL;
echo "\$people->robert greeted the two \$people->smiths"; // 此将不起工作
```

上述示例将输出：
He drank some apple juice.
He drank some orange juice.
He drank some purple juice.
John Smith drank apple juice.
John Smith said hello to Jane Smith.
John Smith's wife greeted Robert Paulsen.
Robert Paulsen 7.1.0 greeted the two.
从 PHP 7.1.0 起，也支持负数数值索引。

示例 #10 负数数值索引

```php
<?php
$string = 'string';
echo "The character at index -2 is \$string[-2].",PHP_EOL;
\$string[-3] = 'o';
echo "Changing the character at index -3 to o gives \$string", PHP_EOL;
?>
```

上述示例将输出：
The character at index -2 is n.
Changing the character at index -3 to o gives strong.
对于任何复杂的内容，您应该使用复杂的语法。

# 4.2.2 复杂（大括号）语法

这之所以被称为复杂，并不是因为语法本身复杂，而是因为它允许使用复杂的表达式。任何具有字符串表示的标量变量、数组元素或对象属性都可以通过此语法包含。只需像它在字符串外部出现的那样编写表达式，然后将其封装在 { } 中。由于 { 无法被转义，只有当 $ 紧紧跟在 { 之后时，这种语法才会被识别。使用它来获取字面量的 $[。以下是一些为了清晰的示例：

```php
<?php
// 显示所有错误
error_reporting(E_ALL);
```

```php
$great = 'fantastic';
```

```php
// 此不起工作，输出：This is { fantastic}
echo "This is {$great}";
```

```php
// 此工作，输出：This is fantastic
echo "This is {$great}";
```

```php
// 此工作
echo "This square is {$square->width}00 centimeters broad."
```

```php
// 此工作，带引号的键在使用大括号语法时有效
echo "This works: {$arr['key']}";
```

```php
// 此工作
echo "This works: {\$arr[4][3]}";
```

```php
// 此是错误的，原因与 $foo[bar] 在字符串外是错误的原因相同。
// 换句话说，它仍然有效，但仅是因为 PHP 首先查找名为 foo 的常量；
// 会抛出一个级别为 E_NOTICE 的错误（未定义的常量）。
echo "This is wrong: {\$arr[foo][3]}";
```

当使用多维数组时，在字符串内部始终始终对数组使用大括号
echo "This works: {\$arr['foo'][3]}";

有效。
echo "This works: " . \$arr['foo'][3]};

echo "This works too: {\$obj->values[3]->name}";

echo "This is the value of the var named $name: {\$name}";

echo "This is the value of the var named by the return value of getName(): {\$getName()}";

echo "This is the value of the var named by the return value of object->getName(): {\$object->getName()}";

```php
// 此不起工作，输出：This is the return value of getName(): {getName()}
echo "This is the return value of getName(): {\$getName()}";
```

# PHP: 字符串

可以使用这种语法在字符串内部使用变量访问类属性。

```php
<?php
class foo {
    var $bar = 'I am bar.';
}

$foo = new foo();
$bar = 'bar';
$baz = array('foo', 'bar', 'baz', 'quux');
echo "{$foo->\$bar}\n";
echo "{$foo->\$baz[1]}\n";
?>
```

上述示例将输出：
I am bar.
I am bar.

使用单大括号 (()) 无法访问函数或方法的返回值或静态类变量的值。

# 记忆

```php
<?php
// 显示所有错误。
error_reporting(E_ALL);

class beers {
    const drink = 'rootbeer';
    public static $ale = 'ipa';
}

{} 内部的函数、方法调用、静态类变量和类常量在 PHP 中有效。然而，该值将被解释为定义字符串的作用域内的变量名。

$rootbeer = 'A';
$ipa = 'Alexander';

// 此工作；输出：I’d like A
echo "I’d like {$beers::drink}\n";

// 此同样有效；输出：I’d like Alexander
echo "I’d like {$ipa}\n";
?>

# 4.2.3 字符串的访问与修改

可以通过在字符串后使用方括号指定所需字符的从零开始的偏移来访问和修改字符串内的字符，例如 $str[4]。为了此目的，可以将字符串视为字符数组。当您想要提取或替换超过 1 个字符时，可以使用 `substr()` 和 `substr_replace()` 函数。

整数、浮点数、静态类变量和类常量在 {} 内部在 PHP 中有效。然而，该值将被解释为定义字符串的作用域内的变量名。

$rootbeer = 'A';
$ipa = 'Alexander';

// 此工作；输出：I’d like A
echo "I’d like {$beers::drink}\n";

// 此同样有效；输出：I’d like Alexander
echo "I’d like {$ipa}\n";
?>

# 4.2.4 转换为字符串

可以使用 (string) 转换或 `strval()` 函数将值转换为字符串。字符串转换在表达式需要字符串时自动完成。类型和类型转换将使以下内容更清晰。

布尔 TRUE 值转换为字符串 "1"。布尔 FALSE 转换为 ""（空字符串）。这允许在布尔和字符串之间转换。

整数或浮点数转换为表示数字的字符串。浮点数可以使用指数计数法（4.1E+6）。

小数点字符定义在脚本的区域设置中（LC_NUMERIC）。

数组始终转换为字符串 "Array"；因此 echo 和 print 无法显示数组的内容。要查看元素，请使用如 `$arr['key']` 的结构。

为了将对象转换为字符串，必须使用 `__toString` 方法。

资源始终转换为字符串 "Resource #1"，其中 1 是 PHP 在运行时分配给资源的资源号。虽然不应依赖此字符串的精确结构并且可能会更改，但在执行脚本的生命周期内（即一个 Web 请求或 CLI 进程），它是唯一的且不会重用。要获取资源的类型，使用 `get_resource_type()` 函数。

NULL 始终转换为空字符串。如所述，直接将数组、对象或资源转换为字符串无法提供有关类型之外的有用信息。`print_r()` 和 `var_`

2004年7月14日，PHP 5 包含了由新的 Zend Engine II 驱动的新功能。PHP 5 包含了许多新功能，例如改进的面向对象编程支持、PHP Data Objects (PDO) 扩展（它定义了访问数据库的轻量且一致的接口）以及大量的性能改进。

