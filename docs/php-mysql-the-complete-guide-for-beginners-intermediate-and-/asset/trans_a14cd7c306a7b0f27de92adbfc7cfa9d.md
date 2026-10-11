

# 第 5 章：字符串输出与格式化

## 第 5.4 节：printf 对比 sprintf

连接运算符的问题在于句点 `.` 在表达式中优先级较高。如果进行连接，上述表达式需要额外的括号才能表现出正确的行为。句点的优先级也会影响三元运算符。

![](Image00150.jpg)

[`printf`](http://php.net/manual/en/function.printf.php) 将使用占位符输出格式化字符串。

![](Image00151.jpg)

也可以使用这两个函数来格式化数字。这可用于格式化用于表示货币的十进制值，使其始终保留 2 位小数。

![](Image00152.jpg)

这两个函数 [`vprintf`](http://php.net/manual/en/function.vprintf.php) 和 [`vsprintf`](http://php.net/manual/en/function.vsprintf.php) 的操作方式与 [`printf`](http://php.net/manual/en/function.printf.php) 和 [`sprintf`](http://php.net/manual/en/function.sprintf.php) 相同，但它们接受一个格式字符串和一个值数组，而不是单独的变量。

## 第 5.5 节：输出大整数

在 32 位系统上，大于 `PHP_INT_MAX` 的整数会自动转换为浮点数。要将这些值作为整数输出（即非科学计数法），可以使用 `printf` 并利用浮点数表示法，如下所示：

![](Image00153.jpg)

```
echo " " , $i , " \n " ;
}

// 输出：
```

![](Image00154.jpg)

```
pow (1024,  1)  integer                     1024                         1024   1024
pow (1024,  2)  integer              1048576                         1048576   1048576
pow (1024,  3)  integer           1073741824                         1073741824   1073741824
pow (1024,  4)   double          1099511627776                         1099511627776   1099511627776
pow (1024,  5)   double  1.1258999068426E+15                         1125899906842624 1.1258999068426E+15
pow (1024,  6)   double  1.1529215046068E+18                       1152921504606846976 1.1529215046068E+18
pow (1024,  9)   double  1.2379400392854E+27          1237940039285380274899124224 1.2379400392854E+27
pow (1024, 12)   double  1.3292279957849E+36  1329227995784915872903807060280344576 1.3292279957849E+36
```

注意：留意浮点数精度，它并非无限的！

虽然这看起来不错，但在这个人为构造的示例中，所有数字都可以表示为二进制数，因为它们都是 1024 的幂（因此也是 2 的幂）。例如见：

![](Image00155.jpg)

## 第 5.6 节：输出多维数组及其索引和值并打印到表格中

![](Image00156.jpg)

![](Image00157.jpg)

在表格中输出带有索引和值的多维数组

![](Image00158.jpg)

# 第 6 章：常量

## 第 6.1 节：定义常量

常量是使用 `const` 语句或 `define` 函数创建的。惯例是常量名使用大写字母。

![](Image00159.jpg)

```
define ( "BETTER_APP_LANGUAGES" , [ "lu" , "de" ]); // 数组
```

如果你已有一个常量，可以基于它定义另一个常量：

![](Image00160.jpg)

```
const TAU = PI * 2;
define ( "EARTH_IS_ROUND" , ! EARTH_IS_FLAT );
define ( "MORE_UNKNOWN" , UNKNOWN );
define ( "APP_ENV_UPPERCASE" , strtoupper ( APP_ENV )); // 字符串操作也可以
// 上面的例子（函数调用）不适用于 const：
// const TIME = time(); # 会报致命错误！非常量标量表达式
define ( "MAX_SESSION_TIME_IN_MINUTES" , MAX_SESSION_TIME / 60);
const APP_FUTURE_LANGUAGES = [-1 => "es"] + APP_LANGUAGES; // 数组操作
define ( "APP_BETTER_FUTURE_LANGUAGES" , array_merge (["fr"], APP_BETTER_LANGUAGES ));
```

### 保留常量

某些常量名由 PHP 保留，无法重新定义。以下所有示例都会失败：

```
define ( "true" , false ); // 内部常量
define ( "false" , true ); // 内部常量
```

![](Image00161.jpg)

```
define ( "CURLOPT_AUTOREFERER" , "something" ); // 如果加载了 curl 扩展将会失败
```

并会发出一个 Notice（提示）：

![](Image00162.jpg)

### 条件定义

如果你有多个文件可能定义同一个变量（例如，主配置文件然后是本地配置文件），以下语法可能有助于避免冲突：

![](Image00163.jpg)

```
defined ( "PI" ) || define ( "PI" , 3.1415 ); // "如果 PI 尚未定义则定义它"
```

### const 对比 define

`define` 是运行时表达式，而 `const` 是编译时表达式。

因此 `define` 允许动态值（即函数调用、变量等），甚至动态名称和条件定义。但它始终相对于根命名空间进行定义。

`const` 是静态的（即仅允许与其他常量、标量或数组进行操作，且仅限于受限的操作集，即所谓的常量标量表达式，包括算术、逻辑和比较运算符以及数组解引用），但会自动加上当前活动命名空间作为前缀。

`const` 仅支持其他常量和标量作为值，不支持运算。

## 第 6.2 节：类常量

常量可以使用 `const` 关键字在类内部定义。

![](Image00164.jpg)

这对于存储项目类型很有用。

![](Image00165.jpg)

## 第 6.3 节：检查常量是否已定义

### 简单检查

要检查常量是否已定义，请使用 `defined` 函数。注意，该函数不关心常量的值，只关心常量是否存在。即使常量的值是 `null` 或 `false`，该函数仍将返回 `true`。

![](Image00166.jpg)

![](Image00167.jpg)

请注意，常量只有在定义它的那一行之后，在你的代码中才会变得“可见”：

![](Image00168.jpg)

### 获取所有已定义的常量

要获取所有已定义的常量（包括 PHP 创建的），请使用 `get_defined_constants` 函数：

![](Image00169.jpg)

要仅获取你的应用定义的常量，请在脚本开始时（通常在引导过程后）和结束时调用该函数：

![](Image00170.jpg)

这有时对调试很有用。

## 第 6.4 节：使用常量

要使用常量，只需使用其名称：

![](Image00171.jpg)

或者如果你事先不知道常量的名称，请使用 `constant` 函数：

![](Image00172.jpg)

## 第 6.5 节：常量数组

从 PHP 5.6 版本起，数组可用作普通常量和类常量：

![](Image00173.jpg)

![](Image00174.jpg)

```
const ANSWER = [2,4];
```

此外，从 PHP 7.0 版本起，此功能被移植到 [`define`](http://php.net/manual/en/function.define.php) 函数中，用于普通常量。

![](Image00175.jpg)

# 第 7 章：魔术常量

## 第 7.1 节：`__FUNCTION__` 与 `__METHOD__` 的区别

`__FUNCTION__` 仅返回函数名称，而 `__METHOD__` 返回类名连同函数名称：

![](Image00176.jpg)

## 第 7.2 节：`__CLASS__`、`get_class()` 与 `get_called_class()` 的区别

| `get_class()` |
| --- |

`__CLASS__` 魔术常量返回的结果与无参数调用的函数相同，它们都返回定义它的类的名称（即你编写函数调用/常量名的地方）。

| `get_class($this)` | | 和 | `get_called_class()` |
| --- | --- | --- | --- |

相比之下，函数调用将返回实际被实例化的类的名称：

![](Image00177.jpg)

![](Image00178.jpg)

## 第 7.3 节：文件与目录常量

### 当前文件

你可以使用 `__FILE__` 魔术常量获取当前 PHP 文件的名称（含绝对路径）。这最常用作记录/调试技术。

![](Image00179.jpg)

### 当前目录

要获取当前文件所在目录的绝对路径，请使用 `__DIR__` 魔术常量。

![](Image00180.jpg)

| `dirname` | | ( | `__FILE__` |
| --- | --- | --- | --- |

要获取当前文件所在目录的绝对路径，请使用 `)` 。

![](Image00181.jpg)

