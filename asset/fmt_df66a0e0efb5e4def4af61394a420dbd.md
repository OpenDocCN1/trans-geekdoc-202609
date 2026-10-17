
要在双引号字符串中使用字面上的 `"`，也必须对其进行转义（使用 `\`）：

```php
echo "A famous programmer, Olav Mjelde said, \"They don't make bugs like Bunny anymore.\"";
```

输出结果为：

```
A famous programmer, Olav Mjelde said, "They don't make bugs like Bunny anymore."
```

请注意，双引号包含的字符串可以包含单引号而无需转义。同样，单引号包含的字符串可以包含双引号而无需转义后者：

```php
echo 'Jane said, "Hi John!"<br/>';
echo "John said, 'Hi Jane!'";
```

此代码输出：

```
Jane said, "Hi John!"
John said, 'Hi Jane!'
```

请参阅在线文档了解有关单引号字符串[^1] 和双引号字符串及字符串转义字符[^2] 的更多信息。

[1] 单引号字符串: http://phpa.me/php-single-strings

[2] 字符串转义字符: http://php.net/language.types.string.php#language.types.string.syntax.double

### Heredoc

PHP 定义了一种特殊的字符串定界方式，称为 heredoc，它允许你在 `<<<` 序列后定义一个标识符，后跟换行符。`EOT`（“end of text”）是常用的字符序列用作标识符。从这一行之后直到同一标识符后跟分号 `;` 在其单独一行上的所有内容都被定界为字符串。这种语法允许你在无需转义单引号或双引号的情况下定义大段文本：

```php
echo <<<EOT
Cupcake ipsum dolor. Sit amet cake ice cream sweet pudding
tootsie roll marshmallow cake. "Lemon" drops apple pie fruitcake
caramels lollipop's sweet roll. Sesame snaps lemon drops topping.
EOT;
```

输出结果为：

```
Cupcake ipsum dolor. Sit amet cake ice cream sweet pudding
tootsie roll marshmallow cake. "Lemon" drops apple pie fruitcake
caramels lollipop's sweet roll. Sesame snaps lemon drops topping.
```

在线文档对字符串[3] 有更详细的说明。

### Exercises

### 练习

创建脚本 `strings.php` 执行以下操作：

- 1. 将名字和姓氏分别赋给两个变量。然后，使用连接输出全名。

- 2. 再次使用名字和姓氏，使用字符串插值输出姓氏、逗号，然后是名字。

- 3. 将姓氏设置为 `O'Connor` 并输出全名。

[3] 字符串: http://php.net/language.types.string

## Chapter 5

## 第 5 章

## Operators, Expressions, and Basic Arithmetic

## 运算符、表达式和基本算术

> “如果它不能正常工作也不用担心。如果一切都正常，你就失业了。”

> – Mosher’s Law of Software Engineering

### Operators and Expressions

### 运算符和表达式

#### Operators

#### 运算符

运算符是根据某些规则产生结果的符号。示例包括：

| 部分运算符 |

|---| 

| `+` |

| `-` |

| `=` |

| `<` |

| `>` |

运算符可以在左侧或右侧被操作数包围。

#### Operands

#### 操作数

操作数是被运算符操作的数据对象。操作数可以是字符串、数字、布尔值、对象或它们的组合。

#### Expressions

#### 表达式

表达式是一组运算符和操作数，由 PHP 解释器进行求值。图 5.1 显示了一个表达式的简单示例。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_58_0.png)

#### Assignments

#### 赋值

字面值和变量的内容使用赋值 (`=`) 运算符赋给变量。`=` 左侧的变量被赋予 `=` 右侧变量的值或内容。请查阅手册以了解赋值运算符[1] 的完整说明。

[1] 赋值运算符: http://php.net/language.operators.assignment

以下是使用 `=` 运算符的示例：

```php
$temperature_fahrenheit = 32;
$current_temperature = $temperature_fahrenheit;
```

#### Compound Assignment operators

#### 复合赋值运算符

像许多现代编程语言一样，PHP 具有复合赋值运算符。以下是使用算术复合赋值运算符的几个示例：

| 复合赋值 | 等价于... | 含义 |

|---|---|---|

| `$a += $b` | `$a = $a + $b` | 加法 |

| `$a -= $b` | `$a = $a - $b` | 减法 |

| `$a *= $b` | `$a = $a * $b` | 乘法 |

| `$a /= $b` | `$a = $a / $b` | 除法 |

| `$a %= $b` | `$a = $a % $b` | 取模 |

#### Operator Precedence

#### 运算符优先级

在 PHP（以及许多其他编程语言）中，优先级决定了运算符的求值顺序及其结合性。以下表格列出了所有 PHP 运算符的优先级和结合性：

| 运算符 | 描述 | 结合性 |

|---|---|---|

| `()` | 括号 | 从左到右 |

| `new` | 创建对象 | 非结合 |

| `[]` | 数组下标 | 从右到左 |

| `++ --` | 自动递增、递减 | 非结合 |

| `! ~ -` | 逻辑非、按位非、取反 | 非结合 |

| `(int) (float) (string) (array) (object)` | 类型转换 | 右 |

| `instanceof` | 判断变量是否为某个类的实例化对象 | 左 |

| `!` | 非 | 非结合 |

| `()` | 括号 | 从左到右 |

| `* / .` | 算术乘、除、字符串连接 | 左 |

| `<< >>` | 按位左移、右移 | 左 |

| `< <= > >=` | 小于、小于等于、大于、大于等于比较 | 非结合 |

| `&` | 按位与 | 左 |

| `^` | 按位异或 | 左 |

| `|` | 按位或 | 左 |

| `&&` | 逻辑与 | 左 |

| `||` | 逻辑或 | 左 |

| `??` | 空合并 | 右 |

| `= += -= *= **= /= .= %= &= |= ^= <<= >>= ??=` | 赋值、复合赋值、复合取模、复合按位逻辑、复合按位移位、复合空合并 | 右 |

请参阅在线文档了解有关运算符优先级[2] 的更多信息。

#### Basic Arithmetic

#### 基本算术

像许多编程语言一样，PHP 提供了五种基本算术运算符：

| 运算符 | 名称 | 示例 | 含义 |

|---|---|---|---|

| `+` | 加法 | `$a + $b` | 和 |

| `-` | 减法 | `$a - $b` | 差 |

| `*` | 乘法 | `$a = $a * $b` | 积 |

| `/` | 除法 | `$a / $b` | 商 |

| `%` | 取模 | `$a % $b` | 余数 |

[2] 运算符优先级: http://php.net/language.operators.precedence

## 5. 运算符、表达式与基本算术

在执行除法时，如果除数能被被除数整除，`/` 运算符返回一个整数，否则返回一个浮点数：

```php
$whole_number = 12 / 4   // $whole_number will be an integer (3)
$float_value = 7 / 2    // $float_value will be a float (3.5)
```

`%` 运算符返回除法运算的余数。`%` 运算符的一个典型用途是判断一个数是奇数还是偶数：

```php
if (($odd_or_even % 2) == 1)
{
    echo "$odd_or_even is an odd number.";
}
else if (($odd_or_even % 2) == 0)
{
    echo "$odd_or_even is an even number.";
}
```

这可以进一步简化为：

```php
if (($odd_or_even % 2) == 1)
{
    echo "$odd_or_even is an odd number.";
}
else
{
    echo "$odd_or_even is an even number.";
}
```

PHP 文档提供了有关基本算术运算符的更多信息。[^3]

> [^3]: 基本算术运算符：[http://php.net/language.operators.arithmetic](http://php.net/language.operators.arithmetic)

### 数学函数

PHP 语言提供了一套相对标准的数学函数供你使用。下面是一些常见数学函数的示例。

### abs()

`abs()` 函数返回给定参数的绝对值：

```php
$value = -42;
$absolute_value = abs($value);
echo "The absolute value of $value is $absolute_value";
```

输出：

```
The absolute value of -42 is 42
```

### pow()

`pow()` 函数返回以第一个参数为底、第二个参数为指数的幂值：

```php
echo pow(10, 3) . '<br/>'; // 1000
echo pow(10, -1) . '<br/>'; // 0.1
```

输出：

```
1000
0.1
```

### round()

`round()` 函数返回给定参数按默认或指定的小数位数精度四舍五入后的值。如果未指定精度，默认精度为 0：

```php
echo round(4.4) . '<br/>'; // 4
echo round(4.5) . '<br/>'; // 5
```

输出：

```
4
5
```

更多数学函数信息请参阅在线文档[4]。

[4] 数学函数：http://php.net/ref.math

### 练习

请为以下练习创建一个脚本 `operators.php`：

- 1. 将两个数值分别赋给不同的变量。输出这两个数以及它们的和、差、积、商，每个占一行。

- 2. 输出上述两个值的模。

- 3. 使用 `pow()` 将第一个值分别提高到二次幂和三次幂，并输出每个结果。

- 4. 将第二个值乘以 1.15，四舍五入到最接近的整数——加分项：将其四舍五入到小数点后两位。输出你的结果。

## 第6章 数组

> “Python 是 BASIC 的直接替代品，就如同擎天柱是卡车的直接替代品一样。”

> 

> - Cory Dodt

当我们拥有逻辑上相互关联的数据时，通常希望将这些数据组合到一个单独的数据结构中来容纳它们。收集一组相关信息最基本的数据结构就是数组。

PHP 中的数组是一种有序映射，它将值与键关联起来。PHP 中的数组可以使用整数或字符串作为键，并与相应的值匹配。

### PHP 中的简单数组

简单数组使用整数作为键，通常从 0 开始，一直到 n-1（n 是数组中的元素个数）。这种实现方式类似于其他编程语言中访问数组的方式。这类数组被称为“数字”数组或“索引”数组。

### 创建

以下是在 PHP 中创建数字数组的方法：

```php
$us_states = array(); // Empty array

// Populated array
$us_states = array("California", "Florida", "Wisconsin");
```

### 短数组语法

在 PHP 5.4 版本之前，程序员必须使用 `array()` 函数来创建数组。PHP 5.4 引入了短数组语法，允许使用方括号（`[ & ]`）创建数组。下面演示如何使用短数组语法创建上述数组：

```php
$us_states = []; // Empty array (short array syntax)

// Populated array (short array syntax)
$us_states = ["California", "Florida", "Wisconsin"];
```

### 访问单个元素

以 `$us_states` 为例，我们可以通过数字键访问数组的各个值。数字数组的索引键从 0 开始，我们通过将键放在数组变量名后面的一组方括号（`[ & ]`）中来访问对应的值：

```php
echo "Sacramento is the capital of $us_states[0].<br/>";
echo "Tallahassee is the capital of $us_states[1].<br/>";
echo "Madison is the capital of $us_states[2].";
```

### 关联数组

关联数组使用字符串作为键，与数组中的值建立关联。

### 枚举数组与关联数组

关联数组非常有用，因为它允许开发者将一个有意义的单词作为键与值关联，而不必依赖任意的数值——这些数值通常与其映射的值没有明显关联。

### 创建

在 PHP 中创建关联数组的语法稍有不同，因为在创建键值对元素时，需要同时指定键及其关联的值。键和值之间用 `=>` 运算符（有时称为“火箭”运算符）分隔：

```php
$us_state_capitals = array(
  "California" => "Sacramento",
  "Florida" => "Tallahassee",
  "Wisconsin" => "Madison"
);
```

### 短数组语法

下面演示如何使用短数组语法创建上述数组：

```php
$us_state_capitals = [
  "California" => "Sacramento",
  "Florida" => "Tallahassee",
  "Wisconsin" => "Madison"
];
```

### 访问单个元素

以 `$us_state_capitals` 为例，我们可以通过关联键访问数组中的各个值。与数字数组类似，将键放在数组变量名后的方括号（`[ & ]`）中即可访问对应值：

```php
echo "The capital of California is {$us_state_capitals['California']}.<br/>";
echo "The capital of Florida is {$us_state_capitals['Florida']}.<br/>";
echo "The capital of Wisconsin is {$us_state_capitals['Wisconsin']}.<br/>";
```

### 添加值

PHP 中的数组是可变的。也就是说，它们在初始创建之后可以被修改。这一特性使我们可以向数组中添加和删除元素。

有两种方法可以将值添加到数组末尾。第一种是使用 `array_push()`[1] 函数：

```php
// Add value to end of numeric array
array_push($us_states, 'Wisconsin');

// Add value to end of associative array
array_push($us_state_capitals, 'California' => 'Sacramento');
```

第二种是使用以下语法：

```php
// Add value to end of numeric array
$us_states[] = 'Wisconsin';

// Add value with this key to end of associative array
$us_state_capitals['California'] = 'Sacramento';
```

### 显式语法与短数组语法

通常，短数组语法比使用 `array` 关键字更受青睐，因为它更加简洁。

### 有用的数组函数

### count()

你常常需要知道数组中有多少个元素。`count()`[2] 函数返回数组中的元素个数：

```php
$us_states_i_lived_in = ["California", "Florida", "Wisconsin"];
$number_of_states = count($us_states_i_lived_in);

echo "I have lived in $number_of_states<br/>";
```

[1] `array_push()`: http://php.net/array-push

[2] `count()`: http://php.net/count

### array_pop()

如果需要获取数组的最后一个元素并将其从数组中移除，可以使用 `array_pop()`[3] 函数。下面是一个使用示例：
