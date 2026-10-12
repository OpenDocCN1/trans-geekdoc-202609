
# PHP 变量与作用域

## 情况 1：`$$foo['bar']['baz']`

| 表达式 | PHP5 解释 | PHP7 解释 |
| :--- | :--- | :--- |
| `$$foo['bar']['baz']` | `${$foo['bar']['baz']}` | `($$foo)['bar']['baz']` |
| `$foo['bar']['baz']` | `$foo['bar']['baz']` | `$foo['bar']['baz']` |
| `($$foo)['bar']['baz']` | `${$foo['bar']['baz']}` | `($$foo)['bar']['baz']` |

![](img/Image00039.jpg)

## 情况 2：`$foo->$bar['baz']`

| 表达式 | PHP5 解释 | PHP7 解释 |
| :--- | :--- | :--- |
| `$foo->$bar['baz']` | `$foo->{$bar['baz']}` | `($foo->$bar)['baz']` |
| `$foo->{$bar['baz']}` | `$foo->{$bar['baz']}` | `$foo->{$bar['baz']}` |
| `($foo->$bar)['baz']` | `$foo->{$bar['baz']}` | `($foo->$bar)['baz']` |

![](img/Image00040.jpg)

## 情况 3：`$foo->$bar['baz']()`

| 表达式 | PHP5 解释 | PHP7 解释 |
| :--- | :--- | :--- |
| `$foo->$bar['baz']()` | `$foo->{$bar['baz']}()` | `($foo->$bar)['baz']()` |
| `$foo->{$bar['baz']}()` | `$foo->{$bar['baz']}()` | `$foo->{$bar['baz']}()` |
| `($foo->$bar)['baz']()` | `$foo->{$bar['baz']}()` | `($foo->$bar)['baz']()` |

![](img/Image00041.jpg)

## 情况 4：`Foo::$bar['baz']()`

| 表达式 | PHP5 解释 | PHP7 解释 |
| :--- | :--- | :--- |
| `Foo::$bar['baz']()` | `Foo::{$bar['baz']}()` | `(Foo::$bar)['baz']()` |
| `Foo::{$bar['baz']}()` | `Foo::{$bar['baz']}()` | `Foo::{$bar['baz']}()` |
| `(Foo::$bar)['baz']()` | `Foo::{$bar['baz']}()` | `(Foo::$bar)['baz']()` |

![](img/Image00042.jpg)

## 第 2.2 节：数据类型

针对不同目的有不同的数据类型。PHP 没有显式的类型定义，变量的类型由赋给它的值的类型决定，或者由它被转换成的类型决定。这是关于类型的简要概述，详细文档和示例请参阅 PHP 类型主题。

PHP 中有以下数据类型：`null`、`boolean`、`integer`、`float`、`string`、`object`、`resource` 和 `array`。

### Null

`Null` 可以赋值给任何变量。它表示一个没有值的变量。

![](img/Image00043.jpg)

这会使变量失效，如果调用它，其值将是未定义或空的。变量将从内存中清除并由垃圾回收器删除。

### Boolean

这是最简单的类型，只有两个可能的值。

![](img/Image00044.jpg)

布尔值可用于控制代码流程。

![](img/Image00045.jpg)

### Integer

整数是正或负的整数。它可以用于任何数制。整数的大小取决于平台。PHP 不支持无符号整数。

![](img/Image00046.jpg)

### Float

浮点数、"双精度数"或简称为"浮点数"是十进制数字。

![](img/Image00047.jpg)

### Array

数组就像一个值列表。数组最简单的形式是由整数索引，并按索引排序，第一个元素位于索引 0 处。

```php
$foo = array(1, 2, 3); // 一个整数数组
```

![](img/Image00048.jpg)

```php
$bar = ["A", true, 123 => 5]; // 短数组语法，PHP 5.4+
```

![](img/Image00049.jpg)

数组也可以将非整数索引的键关联到一个值。在 PHP 中，所有数组在底层都是关联数组，但当我们专门提到“关联数组”时，通常指包含一个或多个非整数键的数组。

![](img/Image00050.jpg)

### String

字符串就像一个字符数组。

![](img/Image00051.jpg)

像数组一样，字符串可以被索引以返回其单个字符：

![](img/Image00052.jpg)

### Object

对象是类的实例。其变量和方法可以通过 `->` 运算符访问。

![](img/Image00053.jpg)

### Resource

资源变量持有打开的文件、数据库连接、流、图像画布区域等的特殊句柄（正如[手册](https://secure.php.net/manual/en/language.types.resource.php#language.types.resource.casting)中所述）。

```php
$fp = fopen('file.ext', 'r'); // fopen() 是在磁盘上将文件作为资源打开的函数。
var_dump($fp); // 输出：resource(2) of type (stream)
```

### `gettype`

要以字符串形式获取变量的类型，请使用 `gettype()` 函数：

![](img/Image00055.jpg)

## 第 2.3 节：全局变量最佳实践

我们可以用以下伪代码来说明这个问题：

![](img/Image00056.jpg)

你的第一个问题显而易见：

![](img/Image00057.jpg)

`$bob` 是从哪来的？

你困惑了吗？很好。你刚刚了解了为什么全局变量令人困惑，并被视为不良实践。

如果这是一个真实的程序，你接下来的“乐趣”就是去追踪所有 `$bob` 的实例，并希望你能找到正确的那个（如果 `$bob` 到处都在用，情况会更糟）。更糟的是，如果其他人定义了 `$bob`（或者你忘记了并重用了该变量），你的代码可能会崩溃（在上面的代码示例中，拥有错误的对象或根本没有对象会导致致命错误）。

### 包含文件与全局变量的问题

```php
include 'file.php';
```

由于几乎所有 PHP 程序都使用类似 `);` 的代码，随着文件数量的增加，维护此类代码的难度将呈指数级上升。

此外，这使得应用程序测试变得非常困难。假设你使用全局变量来保存数据库连接：

![Image00058.jpg](img/Image00058.jpg)

为了单元测试此函数，你必须覆盖全局变量 `$dbConnector`，运行测试，然后将其重置为原始值，这非常容易出错：

![Image00059.jpg](img/Image00059.jpg)

### 如何避免全局变量？

避免全局变量的最佳方式是一种称为 **依赖注入** 的理念。即将所需的工具（依赖）传递给函数或类。

![Image00060.jpg](img/Image00060.jpg)

这更易于理解和维护。无需猜测 `$bob` 在哪里被设置，因为调用者负责知道这一点（它将我们所需的内容传递给我们）。更棒的是，我们可以使用 [类型声明](http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration) 来限制传入的内容。

因此我们知道 `$bob` 要么是 `Bar` 类的实例，要么是 `Bar` 子类的实例，这意味着我们知道可以使用该类的方法。结合标准自动加载器（自 PHP 5.3 起可用），我们现在可以追踪 `Bar` 的定义位置。PHP 7.0 或更高版本包含扩展的类型声明，你也可以使用标量类型（如 `int` 或 `string`）。

> Version = 4.1

### 超全局变量

PHP 中的超全局变量是预定义变量，始终可用，可在脚本的任何作用域中访问。

无需执行 `global $variable;` 即可在函数/方法、类或文件中访问它们。

以下是 PHP 超全局变量列表：

![Image00061.jpg](img/Image00061.jpg) [$GLOBALS](http://php.net/manual/en/reserved.variables.globals.php)

[$_SERVER](http://php.net/manual/en/reserved.variables.server.php)

[$_REQUEST](http://php.net/manual/en/reserved.variables.request.php)

[$_POST](http://php.net/manual/en/reserved.variables.post.php)

[$_GET](http://php.net/manual/en/reserved.variables.get.php)

[$_FILES](http://php.net/manual/en/reserved.variables.files.php)

[$_ENV](http://php.net/manual/en/reserved.variables.environment.php)

[$_COOKIE](http://php.net/manual/en/reserved.variables.cookies.php)

[$_SESSION](http://php.net/manual/en/reserved.variables.session.php)

## 第 2.4 节：未初始化变量的默认值

虽然在 PHP 中并非强制要求，但初始化变量是一个非常好的实践。未初始化变量根据其使用上下文，具有其类型的默认值：

### Unset AND unreferenced

![Image00062.jpg](img/Image00062.jpg)

### Boolean

![Image00063.jpg](img/Image00063.jpg)

### String

![Image00064.jpg](img/Image00064.jpg)

### Integer

![Image00065.jpg](img/Image00065.jpg)

### Float/double

![Image00066.jpg](img/Image00066.jpg)

### Array

![Image00067.jpg](img/Image00067.jpg)

### Object

```php
$unset_obj->foo = 'bar';
var_dump($unset_obj); // Outputs: object(stdClass)#1 (1) { ["foo"]=> string(3) "bar" }
```

![Image00068.jpg](img/Image00068.jpg)

依赖未初始化变量的默认值在将一个文件包含到另一个使用相同变量名的文件中时会有问题。

## 第 2.5 节：变量值的真假性与全等运算符

在 PHP 中，变量值具有关联的“真假性”，因此即使是非布尔值也会等同于 `true` 或 `false`。这允许在条件块中使用任何变量，例如：

![Image00069.jpg](img/Image00069.jpg)

以下是不同类型变量值的一些基本规则：

![Image00070.jpg](img/Image00070.jpg)

![Image00071.jpg](img/Image00071.jpg)

```php
floatval('0') == floatval('-0')
```

在其双精度浮点数表示中，即 `)` 为 `true`。

![Image00072.jpg](img/Image00072.jpg)

### 全等运算符

在 [PHP 文档比较运算符](http://php.net/manual/en/language.operators.comparison.php) 中，有一个全等运算符 `===`。该运算符可用于检查变量是否与参考值完全相同：

![Image00073.jpg](img/Image00073.jpg)

它有一个对应的不全等运算符 `!==`：

![Image00074.jpg](img/Image00074.jpg)

| is_null |
| --- |

全等运算符可作为语言函数（如 `()`）的替代方案。

| strpos |
| --- |

### USE CASE WITH `strpos()`

```php
strpos($haystack, $needle)
```

| strpos |
| --- |

`strpos()` 语言函数用于定位 `$needle` 在 `$haystack` 中出现的索引位置，或判断其是否出现。`strpos()` 函数区分大小写；如果需要不区分大小写的查找，可以使用 `stripos()`。

```php
stripos($haystack, $needle)
```

`strpos` 和 `stripos` 函数还包含第三个参数 `offset` (int)，如果指定，搜索将从字符串开头开始计算的该字符数处开始。与 `strrpos` 和 `strripos` 不同，`offset` 不能为负数。

该函数可返回：

![Image00075.jpg](img/Image00075.jpg)

- 如果 `$needle` 在 `$haystack` 开头找到，返回 `0`；
- 如果在开头以外位置找到，返回非零整数索引；
- 如果未找到，返回 `false`。

| strpos |
| --- |

由于在 PHP 中 `0` 和 `false` 的真假性均为 `false`，但代表 `strpos()` 的不同情况，因此区分它们并使用全等运算符 `===` 精确查找 `false` 而非仅等同于 `false` 的值非常重要。

![Image00076.jpg](img/Image00076.jpg)

或者，使用不全等运算符：

![Image00077.jpg](img/Image00077.jpg)

# Chapter 3: 变量作用域

变量作用域指代码中可访问变量的区域，也称为可见性。在 PHP 中，作用域块由函数、类以及整个应用程序可用的全局作用域定义。

## Section 3.1: 超全局变量

超全局变量由 PHP 定义，无需 `global` 关键字即可从任何地方使用。

![Image00078.jpg](img/Image00078.jpg)

## Section 3.2: 静态属性与变量

定义为 `public` 可见性的静态类属性在功能上等同于全局变量。可从定义该类的任何位置访问。

![Image00079.jpg](img/Image00079.jpg)

函数也可在其自身作用域内定义静态变量。这些静态变量会在多次函数调用中持久化，这与函数作用域中定义的常规变量不同。这是实现单例设计模式的一种非常简单易用的方法：

```php
class Singleton {
    public static function getInstance() {
        // Static variable $instance is not deleted when the function ends
        static $instance;

        // Second call to this function will not get into the if-statement,
        // Because an instance of Singleton is now stored in the $instance
        // variable and is persisted through multiple calls
        if (!$instance) {
            // First call to this function will reach this line,
            // because the $instance has only been declared, not initialized
            $instance = new Singleton();
        }
    }
}
```

![Image00080.jpg](img/Image00080.jpg)

![Image00081.jpg](img/Image00081.jpg)

## Section 3.3: 用户定义的全局变量

任何函数或类之外的作用域均为全局作用域。当 PHP 脚本包含另一个脚本（使用 `include` 或 `require`）时，作用域保持不变。如果脚本在函数或类外部被包含，其全局变量将包含在同一全局作用域中；但如果脚本从函数内部被包含，则被包含脚本中的变量处于该函数的作用域内。

在函数或类方法的作用域内，可使用 `global` 关键字来访问用户定义的全局变量。

![Image00082.jpg](img/Image00082.jpg)

访问全局作用域变量的第二种方法是使用 PHP 预定义的特殊 `$GLOBALS` 数组。
