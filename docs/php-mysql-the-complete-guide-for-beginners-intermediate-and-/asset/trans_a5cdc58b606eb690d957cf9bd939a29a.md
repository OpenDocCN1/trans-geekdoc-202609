

# PHP 资源类型与类型系统

资源有不同的（子）类型。你可以使用 [`get_resource_type()`](https://secure.php.net/manual/en/function.get-resource-type.php) 来检查资源类型：

![Image00211.jpg](Image00211.jpg)

![Image00212.jpg](Image00212.jpg)

你可以在[这里](https://secure.php.net/manual/en/resource.php)找到内置资源类型的完整列表。

## 类型转换

PHP 通常会根据变量使用的上下文正确推断你想要使用的数据类型；不过，有时手动强制转换类型很有用。这可以通过在声明前加上括号括起来的目标类型名称来实现：

![Image00213.jpg](Image00213.jpg)

但要小心：并非所有类型转换都如预期那样工作：

![Image00214.jpg](Image00214.jpg)

```php
// 以下 3 条语句适用于 32 位系统 (PHP_INT_MAX=2147483647)
// 大于 PHP_INT_MAX 的整数值会自动转换为浮点数：
var_dump(999888777666); // float(999888777666)
// 强制转为 (int) 会导致溢出：
var_dump((int) 999888777666); // int(-838602302)
// 但在字符串中它只返回 PHP_INT_MAX
var_dump((int) "999888777666"); // int(2147483647)

var_dump((bool) []);       // bool(false) (空数组)
var_dump((bool) [false]);  // bool(true)  (非空数组)
```

## 类型演变

PHP 是一门弱类型语言。它不需要显式声明数据类型。变量使用的上下文决定了其数据类型；转换会自动进行：

![Image00215.jpg](Image00215.jpg)

![Image00216.jpg](Image00216.jpg)

## Null

PHP 使用 [`null`](http://php.net/manual/en/language.types.null.php) 关键字表示“无值”。它有点类似于 C 语言中的空指针和 SQL 中的 `NULL` 值。

将变量设置为 null：

![Image00217.jpg](Image00217.jpg)

检查变量是否被设置为 null：

![Image00218.jpg](Image00218.jpg)

### Null 与未定义变量

| 通知 | | 未定义变量 | | `nullvar` |
| :--- | :--- | :--- | :--- | :--- |

如果变量未定义或已被 unset，那么针对 `null` 的任何测试都会成功，但同时也会生成一个通知：

![Image00219.jpg](Image00219.jpg)

![Image00220.jpg](Image00220.jpg)

因此，必须使用 [`isset()`](http://php.net/manual/en/function.isset.php) 来检查未定义的值：

```php
if (!isset($nullvar)) {
    // 变量为 null 甚至未定义
}
```

## 整数

PHP 中的整数可以原生地以二进制（基数 2）、八进制（基数 8）、十进制（基数 10）或十六进制（基数 16）指定。

![Image00221.jpg](Image00221.jpg)

整数长度为 32 位或 64 位，取决于平台。常量 `PHP_INT_SIZE` 以字节为单位保存整数大小。

`PHP_INT_MAX` 和（自 PHP 7.0 起）`PHP_INT_MIN` 也可用。

![Image00222.jpg](Image00222.jpg)

```php
printf("Integers are %d bits long" . PHP_EOL, PHP_INT_SIZE * 8);
printf("They go up to %d" . PHP_EOL, PHP_INT_MAX);
```

整数值会根据需要自动从浮点数、布尔值和字符串创建。如果需要显式类型转换：

![Image00223.jpg](Image00223.jpg)

整数溢出将通过转换为浮点数来处理：

![Image00224.jpg](Image00224.jpg)

PHP 中没有整数除法运算符，但可以通过隐式转换来模拟，它总是通过丢弃小数部分来“舍入”。自 PHP 7 版本起，新增了一个整数除法函数。

![Image00225.jpg](Image00225.jpg)

# 第 10 章：运算符

运算符是指接受一个或多个值（或用编程术语说是表达式）并产生另一个值的东西（以便该结构本身成为一个表达式）。

运算符可以根据它们接受的值的数量进行分组。

## Null 合并运算符 (??)

Null 合并是 PHP 7 中引入的新运算符。如果第一个操作数已设置且不为 `NULL`，则返回该操作数。否则，返回第二个操作数。

以下示例：

![Image00226.jpg](Image00226.jpg)

等同于以下两种写法：

![Image00227.jpg](Image00227.jpg)

和：

![Image00228.jpg](Image00228.jpg)

该运算符也可以链式使用（具有右结合语义）：

![Image00229.jpg](Image00229.jpg)

等同于：

![Image00230.jpg](Image00230.jpg)

**注意：**

在字符串连接上使用合并运算符时，别忘了使用括号 `()`。

![Image00231.jpg](Image00231.jpg)

这将只输出 `John`，如果 `$firstName` 为 `null` 而 `$lastName` 为 `Doe`，则会输出 `Unknown Doe`。为了输出 `John Doe`，我们必须像这样使用括号：

![Image00232.jpg](Image00232.jpg)

![Image00233.jpg](Image00233.jpg)

```php
echo ($firstName ?? "Unknown") . " " . ($lastName ?? "");
```

这将输出 `John Doe` 而不是仅输出 `John`。

## 太空船运算符 (<=>)

PHP 7 引入了一种新型运算符，可用于比较表达式。如果第一个表达式小于、等于或大于第二个表达式，该运算符将分别返回 `-1`、`0` 或 `1`。

![Image00234.jpg](Image00234.jpg)

对象不可比较，因此这样做会导致未定义行为。

| `<=>` |
| :--- |

![Image00235.jpg](Image00235.jpg)

该运算符在使用 `usort`、`uasort` 或 `uksort` 编写用户定义的比较函数时特别有用。例如，给定一个按其 `weight` 属性排序的对象数组，匿名函数可以使用 `<=>` 返回排序函数所期望的值。

```php
usort($list, function ($a, $b) {
    return $a->weight <=> $b->weight;
});
```

在 PHP 5 中，这需要一个相当复杂的表达式。

![Image00236.jpg](Image00236.jpg)

## 执行运算符 (``)

PHP 执行运算符由反引号 (``) 组成，用于运行 shell 命令。命令的输出将被返回，因此可以存储在变量中。

![Image00237.jpg](Image00237.jpg)

| [`shell_exec()`](http://php.net/manual/en/function.shell-exec.php) |
| :--- |

注意，执行运算符和 [`shell_exec()`](http://php.net/manual/en/function.shell-exec.php) 会给出相同的结果。

## 递增 (++) 和递减 (--) 运算符

变量可以分别使用 `++` 或 `--` 递增或递减 1。它们可以位于变量之前或之后，语义略有不同，如下所示。

![Image00238.jpg](Image00238.jpg)

关于递增和递减运算符的更多信息，请参阅[官方文档](http://php.net/manual/en/language.operators.increment.php)。

## 三元运算符 (?:)

三元运算符可以看作是一个内联的 `if` 语句。它由三部分组成：条件和两个结果。语法如下：

![Image00239.jpg](Image00239.jpg)

| `<true value>` |
| :--- |

| `<false value>` |
| :--- |

如果条件评估为 `true`，则返回第一块中的值 (`<true value>`)；否则返回第二块中的值 (`<false value>`)。因为我们将 `$value` 设置为三元运算符的结果，所以它将存储返回的值。

**示例：**

![Image00240.jpg](Image00240.jpg)

| `empty` | `(` | `$_POST` | `['action']` |
| :--- | :--- | :--- | :--- |

| `$_POST` | `['action']` |
| :--- | :--- |

如果 `empty($_POST['action'])` 评估为 `true`，`$action` 将包含字符串 `'default'`。否则，它将包含 `$_POST['action']` 的值。

| `expr3` |
| :--- |

| `expr1` | `)` | `?` | `(` | `expr2` |
| :--- | :--- | :--- | :--- | :--- |

![Image00241.jpg](Image00241.jpg)

表达式 `(expr1) ? (expr2) : (expr3)` 在 `expr1` 评估为 `true` 时求值为 `expr2`，在 `expr1` 评估为 `false` 时求值为 `expr3`。

| `expr1` | `?` | `:` | `expr3` |
| :--- | :--- | :--- | :--- |

可以省略三元运算符的中间部分。表达式 `expr1 ?: expr3` 在 `expr1` 评估为 `TRUE` 时返回 `expr1`，否则返回 `expr3`。`?:` 常被称为 Elvis 运算符。

这与 Null 合并运算符 `??` 行为类似，不同之处在于 `??` 要求左操作数严格为 `null`，而 `?:` 尝试将左操作数解析为布尔值并检查其是否为布尔 `false`。

**示例：**

![Image00242.jpg](Image00242.jpg)

在此示例中，`setWidth` 接受一个 `width` 参数，或默认值 `0`，以更改宽度的会话值。如果 `$width` 为 `0`：

| `getDefaultWidth()` |
| :--- |

| `getDefaultWidth()` |
| :--- |

