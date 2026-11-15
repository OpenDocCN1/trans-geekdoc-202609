

### Binary

该系统仅使用 0 和 1。如果有 1，则对应的数字存在；如果有 0，则不存在。数字从右向左读取。最右边的第一位表示 1，其左边一位表示 2，再左边一位表示 4，再左边一位表示 8，以此类推。因此，二进制 101 转换为十进制 5。

### Octal

该数字系统基于数字 8。八进制数也从右向左读取。要将其转换为十进制数，将最右边的数字乘以 1，其左边一位乘以 8，再左边一位乘以 64，再左边一位乘以 512，以此类推。因此，八进制 143 转换为十进制 99。

> **注意**
>
> 自 PHP 8.1 起，八进制数的表示法有了新变化。它们仍然以前导 0 开头，之后加上小写字母 o：
>
> $octal = 0o143;

手动将十进制数字系统转换为这三种系统未免过于复杂。PHP 为此提供了三个转换函数：

- dechex(number)
- decbin(number)
- decoct(number)

> **注意**
>
> 转换函数返回字符串作为结果。PHP 中没有十六进制、二进制和八进制数的数据类型。反向转换函数同样使用字符串作为参数。

同样有三个函数用于反向转换。名称始终遵循相同的约定。转换所源自的数字系统位于前面：

- hexdec(String)
- bindec(String)
- octdec(String)

以下示例显示了一个简单的表单（见图 9.1），可用于将十进制数转换为其他三种数字系统。

```
<?php
if (isset($_POST["send"])) {
    $decimal = $_POST["decimal"];
    $hexa = dechex($decimal);
    $binary = decbin($decimal);
    $octal = decoct($decimal);
}
?>
```

```
<html>
<head>
<title>Converter</title>
</head>
<body>
<form method="POST">
<input type="text" name="decimal" value="<?=isset($decimal)?$decimal:''?>" />
The decimal number<br /><br />
<input type="text" name="hexa" value="<?=isset($hexa)?$hexa:''?>" />
in hexadecimal notation<br />
<input type="text" name="binary" value="<?=isset($binary)?$binary:''?>" />
in binary notation<br />
<input type="text" name="octal" value="<?=isset($octal)?$octal:''?>" />
in octal notation<br />
<input type="submit" name="send" value="Convert" /> </form>
</body>
</html>
```

清单 9.4 数字系统转换（“convert_numbers.php”）

![](img/ae7820c36e8f24c1623d26668b28e80e_269_0.png)

图 9.1 从十进制到其他数字系统的简单转换器

如果要进行更灵活的转换，可以使用 base_convert(number, source system, target system)。在此处，将要转换的数字作为字符串输入。对于源系统，基数跟随当前数字——即十进制为 10，二进制为 2，十六进制为 16，八进制为 8。对于目标系统，输入要转换至的系统的基数。两种系统的最大可能数为 36，因为这涵盖了 0 到 9 的所有数字以及 A 到 Z 的所有字母。

以下示例将二进制数转换为十六进制数。

```
<?php
$a = "1101";
echo base_convert($a, 2, 16);
?>
```

清单 9.5 转换所有数字系统（“base_convert.php”）

转换的结果是 d。在十进制系统中，该数字将是 ... 你知道吗？

## 9.1.4 随机数

如果你想在编程中与命运抗衡，随机数总是有用的。许多计算机游戏依赖随机性带来的惊喜元素，但随机性在严肃的应用中也很有意义。例如，随机生成的密码、随机选择的背景颜色或随机生成的广告横幅。

在较旧版本中，PHP 的随机函数有些令人困惑且经常更改。自版本 8.2 起，这里终于使用了一个新类。因此，我们花点时间仔细了解一下常规的和旧的改进的随机函数，以及新类。

### "rand()" 函数

使用 rand(Minimal, Maximal)，你可以获得介于最小值和最大值限制之间的整数随机值。

```
rand(1, 6)
```

因此返回 1 到 6 之间的随机数，且仅限整数！

> 注意
>
> 使用 srand(基值) 函数，可以为随机数设置一个基值。基值可以是当前日期，例如。

如果从 rand() 中省略限制，你将获得介于 0 和系统相关的上限之间的随机值。你可以使用 getrandmax() 读取此上限（见图 9.2）。这是最大可能的随机值。

```
<?php
echo "Random value: " . rand() . "<br />";
echo "Largest possible random value: " . getrandmax();
?>
```

清单 9.6 "rand()" 和 "getrandmax()"（“getrandmax.php”）

![](img/ae7820c36e8f24c1623d26668b28e80e_271_0.png)

图 9.2 随机值和系统上的最大可能值

### "mt_ ..."

mt_rand(Min, Max) 是 rand() 的较新对应函数。其特点就在前面的 mt 中：mt 代表 Mersenne Twister（梅森旋转算法），这是一种众所周知的随机算法，能提供更好的随机数。在这里，更好意味着随机数更可靠地随机，且算法运行更快。

> 注意
>
> 对于 mt_rand()，还有 mt_srand(base_value) 可用于为随机数设置基值。自 PHP 7.1 起，srand() 是 mt_srand() 的别名。还有一个返回上限的方法：mt_getrandmax()。如果你从 mt_rand() 中省略最大值，则需要此上限。

### "Random\Randomizer" 类

自 PHP 8.2 起，随机数终于有了面向对象的选项：Random\Randomizer 类。名称诚然合乎逻辑，但有些笨拙。然而，在功能上有许多可能性——例如：

- getInt(Min, Max) 返回整数作为结果。Min 和 Max 分别指定下限和上限。
- getFloat(Min, Max) 返回浮点数。仅 PHP 8.3 及以上版本可用。
- getBytes(length) 返回指定长度的随机字节字符串。
- shuffleArray(Array) 随机打乱数组的条目。
- pickArrayKeys(Array, Number) 随机选择指定数量的数组元素。

在以下示例中，Random\Randomizer 类掷出 1 到 6 之间的整数。

```
<?php
$random = new Random\Randomizer();

for($i = 0; $i < 100; $i++) {
    echo $random->getInt(1, 6) . "<br />";
}
?>
```

清单 9.7 “random” 对象生成随机数（“random.php”）

## 9.1.5 最大值、最小值和舍入

有时数字需要先进行修剪，或从多个数字中选择正确的数字。PHP 也为最重要的数学任务提供了现成的函数。

### 最大值和最小值

max(参数1, 参数2 ...) 和 min(参数1, 参数2 ...) 函数从任意数量的参数中确定最大值或最小值。请参考以下示例；结果见图 9.3。

```
<?php
$a = 10;
$b = 5;
$c = 7;

echo "Maximum: " . max($a, $b, $c) . "<br />";
echo "Minimum: " . min($a, $b, $c);
?>
```

清单 9.8 确定最大值和最小值（“maximal_minimal.php”）

![](img/ae7820c36e8f24c1623d26668b28e80e_272_0.png)

图 9.3 最大值和最小值

如果只指定一个参数，则它必须是一个数组。在这种情况下，max() 和 min() 返回数组中的最大值或最小值。

```
<?php
$numbers = array(10, 5, 7, 15, 12, 2, 8, 16, 1);
echo "Maximum: " . max($numbers) . "<br />";
echo "Minimum: " . min($numbers);
?>
```

清单 9.9 从数组中获取最大值和最小值（“maximal_array.php”）

> **注意**
>
> 此函数中不能同时使用数组和其他参数。

### 舍入

最重要的舍入函数是 round(number, precision)。在此处输入要舍入的数字。precision 确定小数位数。它是可选的。如果省略，PHP 会自动舍入为整数。

```
$a = 4.537;
echo round($a, 2);
```

结果为 4.54 的舍入数值。

以下函数也以较窄或较广义进行舍入：

- floor(number) 返回浮点数的下一个最小整数：

```
$a = 4.537;
echo floor($a);
```

这些行因此提供 4。

- ceil(number) 给出浮点数的下一个最大整数：

```
$a = 4.439;
echo ceil($a);
```

这些行因此提供 5。

- abs(number) 返回数字的绝对值。因此负值变为正值。该函数不更改小数位数：

```
$a = -4.3;
echo abs($a);
```

这些行因此提供 4.3。

