

## 6. PHP – 运算符类型

**什么是运算符？** 可以使用表达式 4 + 5 等于 9 来简单回答。
这里 4 和 5 被称为操作数，+ 被称为运算符。PHP 语言支持以下类型的运算符。

- 算术运算符
- 比较运算符
- 逻辑（或关系）运算符
- 赋值运算符
- 条件（或三元）运算符

让我们逐个查看所有运算符。

### 算术运算符

PHP 语言支持以下算术运算符：

假设变量 A 保存 10，变量 B 保存 20，则：

| 运算符 | 描述 | 示例 |
|---|---|---|
| + | 将两个操作数相加 | A + B 将得到 30 |
| - | 用第一个操作数减去第二个操作数 | A - B 将得到 -10 |
| * | 将两个操作数相乘 | A * B 将得到 200 |
| / | 用分子除以分母 | B / A 将得到 2 |
| % | 取模运算符，整数除法后的余数 | B % A 将得到 0 |
| ++ | 自增运算符，将整数值加 1 | A++ 将得到 11 |
| -- | 自减运算符，将整数值减 1 | A-- 将得到 9 |

### 示例

尝试以下示例以理解所有算术运算符。将以下 PHP 程序复制粘贴到 test.php 文件中，放在 PHP 服务器的文档根目录下，并使用任何浏览器访问它。

```
<html>
<head><title>Arithmetical Operators</title></head>
<body>
<?php
$a = 42;
$b = 20;

$c = $a + $b;
echo "Addition Operation Result: $c <br/>";
$c = $a - $b;
echo "Subtraction Operation Result: $c <br/>";
$c = $a * $b;
echo "Multiplication Operation Result: $c <br/>";
$c = $a / $b;
echo "Division Operation Result: $c <br/>";
$c = $a % $b;
echo "Modulus Operation Result: $c <br/>";
$c = $a++;
echo "Increment Operation Result: $c <br/>";
$c = $a--;
echo "Decrement Operation Result: $c <br/>";
?>
</body>
</html>
```

这将产生以下结果：

```
Addition Operation Result: 62
Subtraction Operation Result: 22
Multiplication Operation Result: 840
Division Operation Result: 2.1
Modulus Operation Result: 2
Increment Operation Result: 42
Decrement Operation Result: 43
```

### 比较运算符

PHP 语言支持以下比较运算符。

假设变量 A 保存 10，变量 B 保存 20，则：

| 运算符 | 描述 | 示例 |
| :--- | :--- | :--- |
| == | 检查两个操作数的值是否相等，如果是，则条件为真。 | (A == B) 不为真。 |
| != | 检查两个操作数的值是否相等，如果值不相等，则条件为真。 | (A != B) 为真。 |
| > | 检查左操作数的值是否大于右操作数的值，如果是，则条件为真。 | (A > B) 不为真。 |
| < | 检查左操作数的值是否小于右操作数的值，如果是，则条件为真。 | (A < B) 为真。 |
| >= | 检查左操作数的值是否大于或等于右操作数的值，如果是，则条件为真。 | (A >= B) 不为真。 |
| <= | 检查左操作数的值是否小于或等于右操作数的值，如果是，则条件为真。 | (A <= B) 为真。 |

### 示例

尝试以下示例以理解所有比较运算符。将以下 PHP 程序复制粘贴到 test.php 文件中，放在 PHP 服务器的文档根目录下，并使用任何浏览器访问它。

```
<html>
<head><title>Comparison Operators</title></head>
<body>
<?php
	$a = 42;
	$b = 20;

	if( $a == $b ){
		echo "TEST1 : a is equal to b<br/>";
	}else{
		echo "TEST1 : a is not equal to b<br/>";
	}
	if( $a > $b ){
    echo "TEST2 : a is greater than  b<br/>";
	}else{
    echo "TEST2 : a is not greater than b<br/>";
	}
	if( $a < $b ){
    echo "TEST3 : a is less than b<br/>";
	}else{
    echo "TEST3 : a is not less than b<br/>";
	}
	if( $a != $b ){
    echo "TEST4 : a is not equal to b<br/>";
	}else{
    echo "TEST4 : a is equal to b<br/>";
	}
	if( $a >= $b ){
    echo "TEST5 : a is either greater than or equal to b<br/>";
	}else{
    echo "TEST5 : a is neither greater than nor equal to b<br/>";
	}
	if( $a <= $b ){
    echo "TEST6 : a is either less than or equal to b<br/>";
	}else{
    echo "TEST6 : a is neither less than nor equal to b<br/>";
	}
?>
</body>
</html>
```

这将产生以下结果：

```
TEST1 : a is not equal to b
TEST2 : a is greater than b
TEST3 : a is not less than b
TEST4 : a is not equal to b
TEST5 : a is either greater than or equal to b
```

### 逻辑运算符

PHP 语言支持以下逻辑运算符。

假设变量 A 保存 10，变量 B 保存 20，则：

| 运算符 | 描述 | 示例 |
| --- | --- | --- |
| and | 逻辑 AND 运算符。如果两个操作数都为真，则条件为真。 | (A and B) 为真。 |
| or | 逻辑 OR 运算符。如果两个操作数中有任何一个非零，则条件为真。 | (A or B) 为真。 |
| && | 逻辑 AND 运算符。如果两个操作数都非零，则条件为真。 | (A && B) 为真。 |
| || | 逻辑 OR 运算符。如果两个操作数中有任何一个非零，则条件为真。 | (A || B) 为真。 |
| ! | 逻辑 NOT 运算符。用于反转其操作数的逻辑状态。如果条件为真，则逻辑 NOT 运算符将其变为假。 | !(A && B) 为假。 |

### 示例

尝试以下示例以理解所有逻辑运算符。将以下 PHP 程序复制粘贴到 test.php 文件中，放在 PHP 服务器的文档根目录下，并使用任何浏览器访问它。

```
<html>
<head><title>Logical Operators</title></head>
<body>
<?php
  $a = 42;
  $b = 0;

if( $a && $b ){
    echo "TEST1 : Both a and b are true<br/>";
}else{
    echo "TEST1 : Either a or b is false<br/>";
}

if( $a and $b ){
    echo "TEST2 : Both a and b are true<br/>";
}else{
    echo "TEST2 : Either a or b is false<br/>";
}

if( $a || $b ){
    echo "TEST3 : Either a or b is true<br/>";
}else{
    echo "TEST3 : Both a and b are false<br/>";
}

if( $a or $b ){
    echo "TEST4 : Either a or b is true<br/>";
}else{
    echo "TEST4 : Both a and b are false<br/>";
}

$a = 10;
$b = 20;

if( $a ){
    echo "TEST5 : a is true <br/>";
}else{
    echo "TEST5 : a is false<br/>";
}

if( $b ){
    echo "TEST6 : b is true <br/>";
}else{
    echo "TEST6 : b is false<br/>";
}

if( !$a ){
    echo "TEST7 : a is true <br/>";
}else{
    echo "TEST7 : a is false<br/>";
}

if( !$b ){
    echo "TEST8 : b is true <br/>";
}else{
    echo "TEST8 : b is false<br/>";
}
?>
</body>
</html>
```

这将产生以下结果：

```
TEST1 : Either a or b is false
TEST2 : Either a or b is false
TEST3 : Either a or b is true
TEST4 : Either a or b is true
TEST5 : a is true
TEST6 : b is true
TEST7 : a is false
TEST8 : b is false
```

### 赋值运算符

PHP 支持以下赋值运算符：

| 运算符 | 描述 | 示例 |
| :--- | :--- | :--- |
| = | 简单赋值运算符，将右侧操作数的值赋给左侧操作数 | C = A + B 将把 A + B 的值赋给 C |
| += | 加且赋值运算符，它将右操作数加到左操作数上并将结果赋给左操作数 | C += A 等效于 C = C + A |
| -= | 减且赋值运算符，它从左操作数中减去右操作数并将结果赋给左操作数 | C -= A 等效于 C = C - A |
| *= | 乘且赋值运算符，它将右操作数与左操作数相乘并将结果赋给左操作数 | C *= A 等效于 C = C * A |
| /= | 除且赋值运算符，它用左操作数除以右操作数并将结果赋给左操作数 | C /= A 等效于 C = C / A |
| %= | 取模且赋值运算符，它使用两个操作数取模并将结果赋给左操作数 | C %= A 等效于 C = C % A |

### 示例

尝试以下示例以理解所有赋值运算符。将以下 PHP 程序复制粘贴到 test.php 文件中，放在 PHP 服务器的文档根目录下，并使用任何浏览器访问它。

```
<html>
<head><title>Assignment Operators</title></head>
<body>
<?php
    $a = 42;
    $b = 20;

    $c = $a + $b; /* Assignment operator */
    echo "Addition Operation Result: $c <br/>";

    $c += $a; /* c value was 42 + 20 = 62 */
    echo "Add AND Assignment Operation Result: $c <br/>";

    $c -= $a; /* c value was 42 + 20 + 42 = 104 */
    echo "Subtract AND Assignment Operation Result: $c <br/>";

    $c *= $a; /* c value was 104 - 42 = 62 */
    echo "Multiply AND Assignment Operation Result: $c <br/>";

    $c /= $a; /* c value was 62 * 42 = 2604 */
    echo "Division AND Assignment Operation Result: $c <br/>";

    $c %= $a; /* c value was 2604/42 = 62*/
    echo "Modulus AND Assignment Operation Result: $c <br/>";
?>
</body>
</html>

