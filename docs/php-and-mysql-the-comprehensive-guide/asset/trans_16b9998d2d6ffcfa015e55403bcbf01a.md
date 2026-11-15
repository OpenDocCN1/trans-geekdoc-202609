

![](img/ae7820c36e8f24c1623d26668b28e80e_208_0.png)

图 7.7 数组还将空格作为元素显示

当然，你也可以自己编写这个解决方案，这也有助于理解。只需将 split_loop.php 脚本作为基础。在循环中，你需要一个变量作为数组索引的计数器（$j）以及一个用于 substr() 相应起始位置的变量。后者在循环条件中也很重要，该条件在到达字符串末尾时终止。你可以在图 7.8 中看到结果。

```php
function str_split_own($string, $length = 1) {
	$result = array();
	for ($i = 0, $j = 0; $i < strlen($string); $i += $length, $j++) {
		$result[$j] = substr($string, $i, $length);
	}
	return $result;
}

$a = "PHP is great";
print_r (str_split_own($a, 4));
```

清单 7.11 "str_split()" 模拟 ("str_split_simulate.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_208_1.png)

图 7.8 模拟成功

### "str_word_count()"

如果 str_word_count(String) 只接收一个字符串作为参数，则它返回一个整数，表示字符串中的单词数量。但是，如果你还指定 str_word_count(String, Format)，则该函数返回包含所有单词的普通数组

（Format 的值为 1）或一个关联数组，其中单词位置作为键，单词作为值（Format 的值为 2）。你可以在图 7.9 和图 7.10 中看到这两种解决方案。

![](img/ae7820c36e8f24c1623d26668b28e80e_209_0.png)

图 7.9 不带空格的单独单词数组

```php
<?php
$a = "Always look on the bright side of life!";
print_r(str_word_count($a, 1));
?>
```

清单 7.12 字符串变成数组 ("str_word_count_array.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_209_1.png)

图 7.10 这里带有显示各单词起始位置的关联数组（通过值为 "2" 的 "Format" 实现）

> **注意**
> 作为第三个参数，你可以指定一个字符列表，这些字符被接受为单词的分隔符。如果你想使用的不只是空格，这很有帮助。

### 数组转字符串

要将数组转换为字符串，只需使用 `implode(connection_character, array)` 方法。如果你省略连接字符，元素将直接相互连接。

```php
<?php
$values = array("PHP", "CMS", "SHOP");
$result = implode(" ", $values);
echo $result;
?>
```

清单 7.13 "implode() ("implode.php")"

当然，这也适用于关联数组。⁴ 在这种情况下，元素按定义顺序相互连接。

```php
<?php
$values = array("R" => "FF", "G" => "AA", "B" => "00");
$result = implode($values);
echo "Color value: #" . $result;
?>
```

清单 7.14 "带关联数组的 implode() ("implode_asso.php")"

函数 join(connection_character, array) 与 implode() 的效果完全相同。因此，join() 也被称为 implode() 的别名。⁵

## 7.3 大小写

在网络上，很难控制用户如何在表单字段中输入某个文本。最重要的问题之一是大小写的区分。

字符——即字母、数字和特殊字符——可以用 ASCII 码表示（见 ）。字母的 ASCII 码对于字符串比较也很重要。⁶ 大写字母的 ASCII 码与小写字母不同（数值较低）。

要将大写转换为小写，反之亦然，你可以过滤 ASCII 码。ord(String) PHP 函数返回字母的 ASCII 码；char(Ascii) 是其对应项，可将 ASCII 码转换为相应的字符串。不过，PHP 开发人员已经为你完成了这项工作：strtolower(String) 将字符串中的所有字母转换为小写字母，strtoupper(String) 将所有字母转换为大写。其他字符，例如数字或特殊 c

图 7.11 一个著名的 ASCII 表可在 www.asciitable.com 上找到

4 一个具有从 0 到 n 的键值而不是索引的数组。关于这一点将在第 8 章中进一步介绍。

5 别名通常有历史原因：一个函数以编程语言中的一个名称而闻名，然后以第二个名称实现。你可以在 PHP 中找到别名列表，网址为 http://s-prs.co/v602267。

6 见第 5 章。

```php
<?php
$a = "PHP CMS SHOP";
echo strtolower($a);
?>
```

清单 7.15 "strtolower()" ("strtolower.php")

例如，前面的脚本生成以下输出：php cms shop。

> **提示**
> 许多函数（例如 `str_replace()`）都有不区分大小写的变体。对于 `str_replace()`，其变体是 `str_ireplace()`。在字符串比较函数中，你可以通过名称中的 "case" 术语来识别不区分大小写的变体。

此区域还包含两个辅助函数：

- ucfirst(String) 如果字符串的第一个字符之前是小写字母，则将其转换为大写字母。
- ucwords(String) 将所有单词首字母变为大写，但当然仅限于之前为小写的情况。

与大小写相关的各种函数的一个可能实际应用是论坛的“尖叫保护”。这意味着一个函数检查字符串中是否有许多大写字母，表明用户在大喊大叫。如果是这种情况，字符串将被转换。

以下简单函数实现了这一功能：首先，将各个单词拆分为数组。除第一个字母外，然后遍历每个单词的每个字母。使用 `ord()` 函数进行大小写区分，检查相应字符的 ASCII 码是小写字母还是大写字母，并在每种情况下递增一个计数器。其他字符被忽略。最后，比较计数器。你可以自由设置此处的值。如果大写字母多于小写字母，我们将字符串转换为小写字母，并将单词开头转换为大写字母。

```php
function screamprotection($string) {
$words = str_word_count($string, 1);
$big = 0;
$small = 0;
foreach($words as $word) {
    for ($i = 1; $i < strlen($word); $i++) {
        $ascii = ord(substr($word, $i, 1));
        if ($ascii >= 65 && $ascii <= 90) {
            $big++;
        } elseif ($ascii >= 97 && $ascii <= 122) {
            $small++;
        }
    }
}
if ($big > $small) {
    return ucwords(strtolower($string));
} else {
    return $string;
}
```

清单 7.16 简单的尖叫保护 ("big_small.php")

例如，如果用户现在输入 PHP CMS SHOP，该函数会将此条目转换为 Php Cms Shop。

另一方面，php cms shop 保持不变。你可以按需扩展和改进此函数。例如，可以检查变音字母，或者可以保护 PHP 等术语不被转换。

## 7.4 修剪

用于剪切字符串部分的一个函数是 substr()。它在本节中找到了真正的用武之地。还有其他一些辅助函数，例如用于删除空格。

### 7.4.1 剪切字符

substr(string, start position, length) 有三个参数：

- string 指定要剪切的字符串。
- start position 确定剪切开始的位置。
- length 指定要截断的字符数。此参数是可选的。如果省略，substr() 将返回从起始位置到字符串末尾的所有字符。

substr() 的特点是其相对较高的灵活性。请看几个例子。起点是以下字符串：

