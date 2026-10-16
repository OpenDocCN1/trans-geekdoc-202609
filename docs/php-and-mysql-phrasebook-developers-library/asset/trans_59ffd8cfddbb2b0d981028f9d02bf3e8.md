
```
<?php
$input = 'My parents <i>hate</i> me, <br />' .
'therefore I <b>crack</b> websites. ' .
'<script>alert("Nice try!");</script> ' .
'<img src="explicit.jpg" />';

echo strip_tags($input, '<b><br><i>');
?>
```

![](img/2862989e5dc7f1b1d0bc64321737f084_24_0.png)

图 1.1 部分HTML标签已被剥离，但并非全部。

## 使用换行符

```
<?php
$input = "One\nTwo\r\nThree";
echo nl2br($input);
?>
```

在每个换行处添加 <br /> 元素（nl2br.php）

在HTML中如何使用换行符？这很简单：使用 <br /> HTML元素即可。但是，如果数据中包含\n或\r\n换行符呢？人们可能会想到搜索替换；然而，使用PHP内置函数nl2br()要容易得多。该函数解析字符串并将所有换行符转换为<br />元素，如前面的脚本所示。

如你所见，换行符仍然存在，但<br />元素已经被添加。

## 加密字符串

```
<?php
$pass = (isset($_GET['pass'])) ? $_GET['pass'] : '';
$encpass = '$1$FK3.qn2.$S15Kh...';

if (crypt($pass, $encpass) === $encpass) {
    echo 'Login successful.';
} else {
    echo 'Login failed.';
}
?>
```

使用加密密码检查登录（crypt.php）

密码绝不应原样存储在数据库中，而应加密存储。某些数据库在内部提供加密功能；对于其他所有情况，

PHP可以帮忙。crypt() 函数使用数据加密标准（DES）对字符串进行加密。这是一种单向加密，因此无法还原。此外，每次调用 crypt() 都会产生不同的结果。

例如，字符串 'TopSecret' 被加密为 $1$FK3.qn2.$5i5KhnprsRb.N.SEF4GMW0（还有 $1$Sm61.i12.$0p1j3EHWk1XycncyepP1FZ0 和 $1$9S3.c/3.$5I01Bm4v3cnBNOb1AECi1.，但本示例采用第一个）。要检查某个值是否对应于调用 crypt() 得到的结果，可以再次调用 crypt()：crypt($value, $encryptedValue) 必须返回 $encryptedValue。

前面的脚本检查通过URL提供的密码是否与之前 crypt() 的结果匹配。使用GET参数 pass=TopSecret 调用此脚本可以成功登录；所有其他密码都会失败。

**注意：** 更详细地说：crypt() 的第二个参数是用于加密数据的盐（初始化值）。你也可以在加密原始密码时使用盐。但是，必须确保盐值是唯一的；否则加密将不安全。因此，不要使用自定义盐值，让 PHP 来处理。另外需要提醒的是，DES 加密大约在24小时内就可能被破解，因此它已不再是万无一失的。一个更新的替代方案是高级加密标准（AES）。

## 字符串校验和

```
<?php
    $pass = (isset($_GET['pass'])) ? $_GET['pass'] : '';
    
    $md5pass = '6958b43cb096e036f872d65d6a4dc01b';
    $sha1pass = '61c2feed11e0e53eb8e295ab8da78150be12f301';
    
    if (sha1($pass) === $sha1pass) {
        echo 'Login successful.';
    } else {
        echo 'Login failed.';
    }
    
    // Alternatively, using MD5:
    // if (md5($pass) === $md5pass) {
    //     echo 'Login successful.';
    // } else {
    //     echo 'Login failed.';
    // }
?>
```

使用 SHA1 和 MD5 哈希检查登录
(checksum.php)

PHP 提供了两个主要函数来创建校验和：

- `md5()` 计算字符串的 MD5 哈希值。
- `sha1()` 计算字符串的 SHA1 哈希值。

将 crypt() 用于字符串类似于为某些内容创建校验和；可以很容易地判断字符串是否与校验和匹配；但是，从校验和反推原始字符串并不（容易）可行。

正是为了实现这种校验和，有两种算法：安全哈希算法1（SHA1）和消息摘要算法5（MD5）。它们生成这样的校验和（即哈希）。这两种算法与 DES/crypt() 所用算法的主要区别在于，字符串的 SHA1 或 MD5 校验和始终相同，因此验证数据非常容易。如图 1.2 所示，甚至 PHP 发行版也在其网站上标明了 MD5 校验和，用于验证下载文件的完整性。

![](img/2862989e5dc7f1b1d0bc64321737f084_28_0.png)

图 1.2 PHP 下载页面显示了 PHP 发行版的 MD5 哈希值。

同样，目标是验证用户通过 GET 提供的密码（如前所述，这是不好的做法，仅出于演示目的）。

正确的密码依旧是 'TopSecret'，其哈希值如下：

- 6958b43cb096e036f872d65d6a4dc01b 是 MD5 哈希。
- 61c2feed11e0e53eb8e295ab8da78150be12f301 是 SHA1 哈希。

从安全角度来看，你不应依赖 MD5（因为它可以用现代计算机破解）。鉴于硬件性能的进步，SHA1 也不再完全安全。你应该考虑额外的保护措施：

- 在对值进行哈希之前，先对它加盐——即添加一个已知的前缀字符串，使攻击者更难以破解。不过，这并不能抵御使用暴力破解并尝试几乎所有可能输入组合的攻击者。
- 将 crypt() 与更安全的算法（如 DES）一起使用。

## 提示：

在计算文件的 MD5 或 SHA1 哈希时，无需调用 file_get_contents() 或其他文件函数；PHP 提供了两个计算文件哈希的函数（并负责打开和读取文件数据）：

- `md5_file()`
- `sha1_file()`

## 提取子字符串

### substr()

```
<?php
$php = "PHP: Hypertext Preprocessor";
echo substr($php, 15, 4); //returns "Prep"
?>
```

*使用 substr() 提取子字符串（substr.php；摘录）*

substr() 函数返回字符串的一部分。你提供一个字符串和要提取的第一个字符的位置（请记住，第一个字符的索引为0）。从该字符开始，返回字符串的其余部分。如果只想返回其中一部分，请在第三个参数中提供长度。前面的代码演示了 substr() 的用法，并从 PHP: Hypertext Preprocessor 中提取了 Prep。

**提示：** 如果要从字符串末尾开始计数，请将 substr() 的第二个参数设为负数：

```
echo substr($php, -12, 4);
```

如果为 substr() 的第三个参数提供负值（例如 -n），则最后 n 个字符不包含在子字符串中。

```
echo substr($php, -12, -8);
```

所有这些对 substr() 的调用都会返回 Prep，并且包含在完整代码中。

## 保护电子邮件地址

### 使用ASCII码

```php
<?php
function protectMail($s) {
    $result = '';
    $s = 'mailto:' . $s;
    for ($i = 0; $i < strlen($s); $i++) {
        $result .= '&#' . ord(substr($s, $i, 1)) . ';';
    }
    return $result;
}

echo '<a href="' .
    protectMail('email@address.xy') .
    '">Send mail</a>';
?>
```

*保护电子邮件地址（protectMail.php）*

在浏览器中，你只会看到一个电子邮件链接，但底层的 HTML 代码却难以辨认：

```html
<a
href="&#109;&#97;&#105;&#108;&#116;&#111;&#58;
&#101;&#109;&#97;&#105;&#108;&#64;&#97;&#100;&#100;&#114;
&#101;&#115;&#115;&#46;&#120;&#121;">Send
mail</a>
```

然而，请看图 1.3：Web 浏览器正确地解码了电子邮件地址，如状态栏所示。

![](img/2862989e5dc7f1b1d0bc64321737f084_32_0.png)

**图 1.3** 机器胜过人类（在解读电子邮件地址时）。

有些特殊字符在字符串中使用起来很困难，因为很难用键盘输入。但它们都有 ASCII 值。PHP 提供了两个函数来处理这个问题：

- `chr()` 将 ASCII 码转换为相应的字符。
- `ord()` 返回一个字符的 ASCII 码。

例如，这可用于保护电子邮件地址。由于垃圾邮件发送者会编写软件来搜索网页上的特定模式（电子邮件地址），因此这有助于减少垃圾邮件。诀窍是使用 HTML 字符代码来表示电子邮件地址，使垃圾邮件机器人更难找到电子邮件数据。

前面的代码将一个电子邮件地址（格式为 `email@address.xy`）作为参数，并返回 `mailto:email@address.xy`——但已转换为 HTML 实体。例如，`mailto:` 中的 m 的 ASCII
