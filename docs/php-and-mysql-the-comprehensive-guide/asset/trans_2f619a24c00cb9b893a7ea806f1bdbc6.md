

为演示目的，我们将使用一个现有的验证码——即来自 PEAR Text_CAPTCHA 项目的验证码，安装方法如下：

```php
pear install Text_CAPTCHA
```

> **注意**
>
> 如果在书籍出版时软件包尚未发布稳定版本，则必须明确声明软件包的状态——例如，如下所示：
>
> `pear install Text_CAPTCHA-alpha`
>
> 您可以在软件包主页 <http://s.prs.co/v602248> 上找到当前版本号。您还需要事先安装 Image_Text 和 Text_Password PEAR 软件包，以便验证码软件包的安装正常工作。

安装软件包后，您可以按如下方式请求验证码图形并接收它——在我们的示例中，为 PNG 格式：

```php
<?php
require_once 'Text/CAPTCHA.php';

$c = Text_CAPTCHA::factory('Image'); //graphic CAPTCHA
$c->init(200, 80); //200, 80 pixels

$phrase = $c->getPhrase(); //text in CAPTCHA
$png = $c->getCAPTCHAAsPNG();
?>
```

然而，仅凭这些并不能起到多大作用。您还需要处理管理工作。以下示例直接基于软件包文档。验证码中的术语存储在会话变量中，并按此方式检查。但首先，需要启动 PHP 会话支持：

```php
session_start();
```

$ok 变量用于记录验证码是否已解答：

```php
$ok = false;
```

在浏览器中显示的文本保存在 $info 变量中：

```php
$info = "Please enter text in the image!";
```

如果要再次显示验证码（此时 $ok 为 false），则会生成新图形，并将生成的 PNG 图像保存到文件中。然后将此文件与文本输入表单字段一起显示：

```php
if (!$ok) {
require_once 'Text/CAPTCHA.php';

$c = Text_CAPTCHA::factory('Image');
$c->init(200, 80);

$_SESSION["phrase"] = $c->getPhrase();

file_put_contents(sha1(session_id()) . ".png", $c->getCAPTCHAAsPNG());

echo "<form method=\"POST\">" .
"<img src=\"" . sha1(session_id()) . ".png?" . time() . "\" />" .
"<input type=\"text\" name=\"phrase\" />" .
"<input type=\"submit\" /></form>";
}
```

> > **提示**
> > 附加当前的纪元格式时间（使用 `time()` 调用）可防止Web浏览器将旧验证码保存在缓存中。

但是，当用户尝试解答验证码时会发生什么？在这种情况下，输入会与会话变量中的验证码解答词进行比较，并相应地设置 `$ok` 变量（以及 `$info` 变量）：

```php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
if (isset($_POST["phrase"]) && isset($_SESSION["phrase"]) &&
strlen($_POST["phrase"]) > 0 && strlen($_SESSION["phrase"]) > 0 &&
$_POST["phrase"] == $_SESSION["phrase"]) {
$info = "OK!";
$ok = true;
unset($_SESSION['phrase']);
} else {
$info = "Please try again!";
unset($_SESSION['phrase']);
}
unlink(sha1(session_id()) . ".png");
}
```

状态消息在末尾输出：

```php
echo "<p>$info</p>";
```

以下代码清单展示了此示例的完整代码：图 32.10 显示了输出。

```php
<?php
    session_start();
    $ok = false;
    $info = "Please enter text in the image!";
    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        if (isset($_POST["phrase"]) && isset($_SESSION["phrase"]) &&
            strlen($_POST["phrase"]) > 0 && strlen($_SESSION["phrase"]) > 0 &&
            $_POST["phrase"] === $_SESSION["phrase"]) {
            $info = "OK!";
            $ok = true;
            unset($_SESSION['phrase']);
        } else {
            $info = "Please try again!";
            unset($_SESSION['phrase']);
        }
        unlink(sha1(session_id()) . ".png");
    }

echo "<p>$info</p>";

if (!$ok) {
    require_once 'Text/CAPTCHA.php';

    $c = Text_CAPTCHA::factory('Image');
    $c->init(200, 80);

    $_SESSION["phrase"] = $c->getPhrase();

    file_put_contents(sha1(session_id()) . ".png", $c->getCAPTCHAAsPNG());

    echo "<form method=\"POST\">" .
        "<img src=\"" . sha1(session_id()) . ".png?" . time() . "\" />" .
        "<input type=\"text\" name=\"phrase\" />" .
        "<input type=\"submit\" /></form>";
}
?>
```

### 清单 32.10 使用验证码的代码 ("captcha-code.php")

### 图 32.10 使用中的验证码

## 32.8 加密密码

最后，我们将探讨另一个PHP也很好地涵盖的安全问题，即使底层编程错误不如XSS、SQL注入或CSRF那么明显。这里的主题是密码的安全存储。近期（甚至更久远）过去的无数案例表明，许多公司在数据存储方面非常不谨慎。Have I Been Pwned网站（https://haveibeenpwned.com）是一个知名资源，在重大访问数据被盗案例中始终活跃，并提供一项测试，告诉您自己的电子邮件地址是否已被成功窃取。

### 图 32.11 Have I Been Pwned

成功入侵的原因有很多——例如，SQL注入或仅仅是公司内部人员访问并转发数据。这里密码特别值得关注。如果这些密码以明文形式存储在数据库中，灾难将达到极致。因此，加密是至关重要的。然而，这里也存在潜在的缺点：Web应用程序可能需要再次解密数据，例如在进行登录尝试时。如果攻击者成功从应用程序读取数据，他们可能也可以访问应用程序本身，因此可以访问密钥。

因此，多年前许多Web应用程序就采用了不存储密码，而仅存储一种指纹的做法。从此指纹中无法再恢复密码。然而，当用户登录应用程序时，Web应用程序会从指定的密码创建一个新指纹。这与保存的指纹相同，登录即可成功。

然而，如果攻击者访问应用程序的数据库，他只拥有指纹，而没有“真实”密码。尽管攻击成功了，但在其他地方使用相同密码的任何人确实都必须在几秒钟内更改它（但不应花费太长时间）。

然而，用于指纹的方法至关重要——过去，通常使用MD5（及其PHP函数 md5()）和SHA1（或PHP中的 sha1()）。此过程已有一段时间不再安全；可以使用标准硬件并在相对较短的时间内从MD5哈希（即所称的指纹）中恢复密码——或者可以确定另一个具有相同MD5哈希的密码。稍微安全一些的SHA1变体能抵抗解密更长时间，但这种方法现在也被认为已被攻破。

当然，还有其他加密和哈希机制，但即使在PHP中，它们也一直有点笨拙。因此，有了Password Hashing API。关于此内置扩展的所有信息可在 http://php.net/password 上找到。您无需任何配置或进一步的设置步骤即可使用此功能。在内部，所提供的功能依赖于强大的 crypt() 函数，但Password Hashing API本身将所有内容浓缩为四个单独的函数：

- password_hash()
  - 从输入（如密码）生成哈希
- password_verify()
  - 检查输入是否与哈希匹配
- password_get_info()
  - 提供关于哈希的信息
- password_needs_rehash()
  - 检查哈希是否具有某些属性

前两个函数是最重要的。过程相对简单：使用 `password_hash()` 生成哈希。除了输入本身外，还必须指定要使用的算法；PHP提供两个常量，`PASSWORD_DEFAULT`（默认情况下，这是 `bcrypt`，但未来的PHP版本中可能会更改）和 `PASSWORD_BCRYPT`。

这是一个示例：

```php
password_hash("top secret", PASSWORD_DEFAULT);
```

以下是可能的输出：

```
$2y$10$Bz8Kut2TCB17TfOYzLBHMugxG2eOBSYXI1vFcZrkp9hNo/1UwzOtu
```

此哈希现已存入数据库；从此无法看到密码。但是，我们可以使用 `password_verify()` 来检查输入是否与哈希匹配：

```php
password_verify("top secret", "$2y$10$Bz8Kut2TCB17TfOYzLBHMugxG2eOBSYXI1vFcZrkp9hNo/1UwzOtu");
```

返回值则不出所料地为 true。这样一来，例如，您可以调整 *第15章，清单15.6* 中的登录逻辑。

作为 `password_hash()` 的第三个参数，您可以使用关联数组指定加密选项：cost，即生成哈希值的算法成本。越高越好，但计算时间越长。10是默认值，但只要性能良好，也可以增加它。

以下是这方面的一个小示例：

```php
password_hash("top secret", PASSWORD_BCRYPT, ["cost"=>15]);
```

例如，此代码在一次测试运行中生成了以下返回值——等待几秒钟后：

```
$2y$15$LyWFa9f0JQB81Cfh1bN9KumpOXY0tKgfw8br3j1Qzt7.eStTPGBjG
```

如您所见，哈希还包含有关算法和成本的信息。其余部分即为实际哈希。

**注意**

在过去，还可以指定 *盐* 值——即附加到要哈希的字符串上的“盐”，以使哈希更难以追踪。PHP每次都会使用随机且安全的盐值，因此此配置选项已在PHP 8中移除。

这让您可以使用一个非常简单的API，它仍能安全地加密密码。MD5和SHA1哈希已不再足够。

