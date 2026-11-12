
不过只是个 3。但那是 1 和 2 的和。事情是这样的：`+` 运算符不能用于字符串，只能用于数字。所以当 PHP 遇到加号时，它会自动将加号两侧的字符串转换为数字 1 和 2。然后处理器将这两个数字相加得到 3，并将其存储在 `$combined` 中。请注意，`$combined` 是一个整数。你可以通过在 print 语句后添加以下行来验证这一点：

```
var_dump($combined);
```

这行会产生以下输出：

```
int(3)
```

这行输出意味着该变量的类型是 int（即整数），并且包含值 3。换句话说，PHP 自动为你完成了转换。

假设字符串中没有数字，而是像下面这样将字符串 ham 和 sandwich 相加：

```
<?
    $a = "ham";
    $b = "sandwich";
    print $a + $b;
?>
```

PHP 在将两个字符串相加之前，会先将每个字符串转换为数字 0。同样，加号只用于数字；PHP 所能做的最好操作就是将这两个字符串转换为某个数字，所以它选择 0。因此这个示例打印 0。

当然，如果你想要的是字符串 "12" 而不是整数 3，可以使用点运算符：

```
$reallywanted = $a1 . $a2;
```

这会创建字符串 12，你可以通过 var_dump 验证，如下所示：

```
print "$reallywanted<br>\n";
var_dump($reallywanted);
```

在这个输出中，你会看到字符串 "12" 和 var_dump 的结果 string(2) "12"。

但如果你想要字符串 "3" 呢？那么你可以这样做：

```
$wantedastring = "$combined";
```

我只是将 `$combined` 变量放在引号内，这样就把 `$combined` 的值写入了字符串。以下是完整程序：

```
<?php
$a1 = '1';
$a2 = '2';
$combined = $a1 + $a2;
print "$combined<br>\n";
var_dump($combined);
print "<br>\n";
$reallywanted = $a1 . $a2;
print "$reallywanted<br>\n";
var_dump($reallywanted);
print "<br>\n";
$wantedastring = "$combined";
print "$wantedastring<br>\n";
var_dump($wantedastring);
?>
```

最后的 var_dump 验证了 wantedastring 是一个字符串：

```
string(1) "3"
```

或者，如果你愿意，以下示例展示了将数字转换为字符串的另外两种方法：

```
<?php
$a1 = '1';
$a2 = '2';
$combined = $a1 + $a2;
$anotherstring = strval($combined);
var_dump($anotherstring);
print "<br>\n";

$yetanotherstring = (string)$combined;
var_dump($yetanotherstring);
?>
```

第一种方法是调用 strval。第二种方法是使用强制转换。对于强制转换，你需要在要转换的变量名前面放入括号中的类型名。以下是这个最新且最棒程序的输出：

```
string(1) "3"
string(1) "3"
```

你可以用三种方式将数字转换为字符串：

- 将其放在引号中，如 "$combined"。
- 调用 strval，如 strval($combined)。
- 直接强制转换，如 (string)$combined。

你也可以走回头路，将字符串转换为数字，前提是字符串包含有效数字。这一次，你只有两种方法可用，因为引号只用于构建字符串。以下是一些示例代码：

```
<?php
$somestring = "123";
$wantnumber1 = intval($somestring);
$wantnumber2 = (int)$somestring;

var_dump($wantnumber1);
print "<br>\n";
var_dump($wantnumber2);
print "<br>\n";
?>
```

以下是这段代码的详细说明：

- 第一行存储字符串 "123"。
- 第二行通过使用名为 intval 的函数将字符串转换为整数。
- 第三行通过直接强制转换将字符串转换为整数。
- （有趣的是，你可以在强制转换中使用 int 或 integer 这两个词中的任意一个，都可以。）
- 最后一组行会转储有关变量的信息，证明（毫无疑问）这两个变量实际上是整数。

因此你可以用两种方式将字符串转换为整数：

- 调用 intval，如 intval($somestring)。
- 直接强制转换，如 (int)$somestring。

除了在字符串和整数之间转换之外，你还可以将浮点数加入列表。与其讨论所有可能性（将浮点数转换为整数、将字符串转换为浮点数、将鸭嘴兽转换为……嗯，你明白我的意思），我将在下面的列表中展示一些示例代码。以下是如何进行特定转换的详细说明：

- 将浮点数转换为整数：使用 intval($myfloat)，将浮点数传递给函数。或者强制转换，如 (int)$myfloat。
- 将整数转换为浮点数：使用 floatval($myint)，将整数传递给函数。或者强制转换，如 (float)$myfloat。
- 将字符串转换为浮点数：使用 floatval($mystring)，将字符串传递给函数。或者将字符串强制转换为浮点数，如 (float)$mystring。
- 将浮点数转换为字符串：使用 strval($myfloat)，将浮点数传递给函数。

floatval 函数从 PHP 版本 4.2.0 开始可用。如果你使用的是更早的版本，则无法访问此函数。在这种情况下，只需使用强制转换即可。

在 CD-ROM 上，在源代码目录的 Book5/Chap7 目录中查找文件 convertfloats.php，以获取所有这些转换的完整示例。或者直接访问 www.jeffcogswell.com/dummies/convertfloats.php。

## 关于引用变量

在开始谈论引用变量之前，我想提醒你，如果你熟悉某种其他语言（提示：C++）中的引用变量，请忘记你所知道的，至少在 PHP 编程时如此。

引用变量是另一个变量的别名。引用变量只是变量的另一个名称。例如，假设你有一个名为 $platypus 的变量。然后你为此变量设置了一个名为 $duckbill 的引用。这意味着你有两个名称指向同一个变量。通常，你会在函数内这样做，例如，当你有一个全局变量，并且想要为变量赋予一个更适合函数用途的名称时。

如果你是 C++ 程序员，你可能会说：“嗯，这不就是 C++ 中的引用吗？”相信我，我说：不是。C++ 中的引用是指向另一个变量的指针。但是当你在 PHP 中创建引用时，你会得到一个新符号，它引用同一个变量。所以对于我的哺乳动物示例（是的，鸭嘴兽是哺乳动物），你有两个符号，$platypus 和 $duckbill，它们引用同一个变量。（如果你有很强的 Unix 背景，PHP 手册将引用比作硬链接。）换句话说，你有一个变量有两个不同的名称：$platypus 和 $duckbill。在 C++ 中，引用变量引用另一个变量。在 PHP 中，两个名称引用同一个变量；它们互为别名。

那么如何创建引用变量呢？如下所示：

```
$platypus = 10;
$duckbill = & $platypus;
```

这段代码首先创建一个名为 $platypus 的变量并将 10 存储在其中。接下来，代码创建一个名为 $duckbill 的变量，并使用 =& 符号将其作为 $platypus 的别名或引用。

要创建引用，请键入引用变量的名称，然后是 =& 运算符，后跟新变量将作为其别名的变量的名称。（确保使用等号后跟与符号，而不是反过来。如果你输入 $x &= $y，你将通过对当前在 $x 中的值和 $y 中的值执行逻辑 *and* 运算符来修改 $x。）

![](img/3f967ab8a8fddc723173059f56621648_477_0.png)

下面是更多代码，展示了那只长着鸭嘴的鸭嘴兽被账单所影响的含义：

```
<?php
$platypus = 10;
$duckbill = & $platypus;

$platypus = 20;
print "$duckbill<br>\n";

$duckbill = 30;
print "$platypus<br>\n";
```

```
?>
```

仔细看看这段代码。前两行与之前的代码相同。然后我将 20 存储在 $platypus 中并打印出另一个变量 $duckbill。你看到了什么？20。接下来，我将 30 存储在 $duckbill 中，并打印出另一个变量 $platypus。你看到了什么？30。正如示例所示，这两个变量名是同一个变量的别名。

在将变量名设置为另一个变量的引用后，你稍后可以让它引用另一个变量。以下是示例程序：

```
<?
$platypus = 20;
$manatee = 50;

$coolmammal = & $platypus;
$coolmammal = 30;
print "$platypus<br>\n";
```
