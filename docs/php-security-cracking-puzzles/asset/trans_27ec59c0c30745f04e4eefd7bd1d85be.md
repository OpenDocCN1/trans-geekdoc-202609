

请注意，第一个常量 `FIRST` 是在第一个文件中定义的，并在 `2.php` 处理器中对其进行检查。如果未定义该常量，说明没有通过 `include` 指令将第二个文件包含在第一个。这意味着正在尝试直接访问该文件。

`if (!defined('FIRST')) exit();` 语句通过绕过 HTML 授权表单来防止对文件进行数据编辑。

## II.7.2. 密码加密

加密密码数据的方便方法是使用不可逆加密，即对数据进行加密使其无法被解密。初看这可能很奇怪，但这种加密非常常见。不可逆加密的函数被称为哈希函数（hashing functions）。它们会为编码后的字符串创建一个唯一的“指纹”。最常见的哈希算法是 MD5，它通过同名函数实现，如下所示：

```
string md5(string str [, bool raw_output])
```

该函数接收必须加密的 `str` 字符串并返回其唯一的 128 位哈希值。如果可选参数 `raw_output` 的值为 `true`，则返回一个 16 字符的二进制字符串。两个字符串产生相同代码的概率趋于零。

类似的函数 `md5_file()` 通常用于为通过网络传输的文件创建唯一的哈希值。下载文件后，可以通过计算其 MD5 哈希值并与开发者提供的哈希值进行比较来验证其完整性。此过程可以确保通过网络传输的文件没有损坏。此外，它还可以防止文件被篡改，并经常用于保护大型软件发行版。

![](img/a893312ec68b8170fe567f785e95c06e_278_0.png)

注册用户的代码（列表 II.3.30）必须通过添加代码进行修改，使用 `md5()` 函数对其密码进行加密（列表 II.7.3）。

![](img/a893312ec68b8170fe567f785e95c06e_278_1.png)

列表 II.7.3 仅显示部分代码；完整的用户注册代码可以在附带 CD-ROM 中的 `scripts/7.7.2/1.php` 文件中找到。

![](img/a893312ec68b8170fe567f785e95c06e_278_2.png)

### 列表 II.7.3. 用户注册脚本

```
<?php
/////////////////////////////////////////////////
// 用户注册块
/////////////////////////////////////////////////
// 将数据存储在文本文件中
$fd = fopen($filename
fwrite($fd,$str);
close($fd);
...
?>
```

如列表 II.7.3 所示，`$_POST['pass']` 在保存到文件之前经过了 `md5()` 函数的处理。

现在，当密码被加密后，必须必须修改用户授权系统（列表 II.7.1 和 II.7.2）。列表 II.7.1 中的一个代码块必须按照列表 II.7.4 所示**加粗**的部分进行修改。

## 列表 II.7.4. 修改后的用户注册代码

```php
<?php
if(md5($_POST['pass']) != $temp['password'][$index])
{
    exit("Wrong password!");
}
// 如果输入正确的密码，
// 并显示编辑数据的表单
include "2.php"; // 第二个 HTML 表单的处理器
?>
<table>
<form method="post">
<input type="hidden" name="name"
value='<?php htmlspecialchars($temp['name'][$index]); ?>'>
<input type="hidden" name="pass"
value='<?php htmlspecialchars($_POST['pass]); ?>'>
<input type="hidden" name="edit" value=edit
<tr
<td>Password:</td>
<td><input type="password" name="passw"
value='<?php htmlspecialchars($_POST['pass]); ?>'></</td>>
</tr>
<tr>
<td>Password:</td>
<td><input type="password" name="pass again"
value='<?php htmlspecialchars($_POST['pass]); ?>'></</td>>
</tr>
<tr>
<td>Email:</td>
<td><input type=text name=email value="<?= htmlspecialchars($temp['email'][$index]); ?>"></</td>>
</tr>
<tr>
<td>URL:</td>
<td><input type=text name='url' value="<?= htmlspecialchars($temp['url'][$index]); ?>"></</td>>
</tr>
<tr>
<td>&nbsp;</td>
<td><input type="submit" value='Edit'></</td>>
</tr>
</form>
</table>
<?php
}
?>
```

此外，必须修改编辑表单的处理器，以便加密新密码（列表 II.7.5）。

## 列表 II.7.5. 修改后的编辑表单处理器

```php
<?php
///////////////////////////////////////////////////////
// 编辑数据文件
///////////////////////////////////////////////////////
$arr = file($filename);
$linefile = array();
foreach($arr as $line)
{
    // 在分隔符处拆分行
    $data = explode(":", $line);
    if($data[0] == $temp['name'][$index])
    {
        // 构建新字符串以替换旧字符串
        $linefile[] = $_POST['name'].":".md5($_POST['passw']).":".$_POST['email'].":".$_POST['url'];
        $_POST['passw'] = $_POST['passw'];
        $temp['email'][$index] = $_POST['email'];
        $temp['url'][$index] = $_POST['url'];
    }
    else
    $linefile[] = trim($line);
}
?>
```

### II.7.3. 猜密码

猜密码是通过遍历字符的所有可能组合来实现的，从单字符密码开始，在耗尽前一个长度的所有组合后，长度每次增加一个字符。在这种情况下，你知道密码长度 $n$ 大于四，且只使用小写字母。由于字符代码占据了从 97 到 122 的连续范围，它们通常在循环中生成。尽管如此，脚本更加灵活，允许使用所有字符，并将可能的字符都放入 `$pass` 数组中。由于密码长度通常未知且可能变化，脚本使用一个名为 `decrypt_md5($pass, $answer)` 的递归函数构建，该函数接受两个参数。第一个参数是加密字符串。另一个参数用于技术目的：使用它发送当前密码，在第一次调用函数时，其值为空字符串。函数返回猜到的密码；如果当前密码长度超过了指定的限制（即四个字符），则返回空字符串。

### II.7.6. 猜 MD5 密码

```php
<?php
//为脚本设置无限运行时间
set_time_limit(0);

// 从密码文件中读取密码
$pass = file("password");

foreach($pass as $password)
{
  // 记录猜密码过程的时间
  $begin = time();
  echo decrypt_md5(trim($password));
}

// 密码枚举函数
// $pass - 要猜的密码
// $answer - 当前的答案（第一次调用时为空字符串）
function decrypt_md5($pass, $answer)
{
  $arr = array('a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z');
  // 假设密码超过四个字符
  $max_number = 3;
  if (strlen($answer) > $max_number) return;

  for($j = 0; $j < count($arr); $j++) {
    $temp = $answer.$arr[$j];
    if (md5($temp) == $pass) return $temp;
    // 递归调用函数以增加猜密码的长度
    $result = decrypt_md5($pass, $temp);
    // 如果返回非空字符串，说明已猜到密码，不再继续搜索
    if (strlen($result) > 0) return $result;
  }
}
?>
```

脚本执行可能需要大量时间，因此在脚本代码开头通过调用 `set_time_limit()` 函数消除了执行时间限制。该函数的唯一参数是指定新最大执行时间的整数。如果该参数为零，则执行时间无限。

之后，`password` 文件的内容被拆分为字符串。这些字符串被放入 `$pass` 数组，并在循环中传递给递归函数 `decrypt_md5()`。

![](img/a893312ec68b8170fe567f785e95c06e_283_0.png)

> 注意，$pass 数组中的字符串经过了 `trim` 函数，以去除可能存在的不可见尾随字符 `\r\n`。

