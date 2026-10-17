
## 第 101 章：错误处理与文件上传

### 错误处理示例

```
set_error_handler(function ($errno, $errstr, $errfile, $errline) {
    // 记录到数据库
    $db->query("INSERT INTO error_log (message, file, line) VALUES (?, ?, ?)", [$errstr, $errfile, $errline]);
    return true; // 阻止默认处理程序
});
```

此方法将消息记录到数据库，如果失败则记录到文件，而不是直接回显到页面中。这样你可以追踪用户在你网站上遇到的问题，并在出错时立即收到通知。

### 第 101.8 节：上传文件

如果你想让用户向你的服务器上传文件，在实际将上传的文件移动到 Web 目录之前，你需要进行一些安全检查。

#### 上传的数据

`$_FILES` 数组包含用户提交的数据，并非文件本身的信息。虽然通常这些数据由浏览器生成，但可以使用软件轻松地向同一表单发起 POST 请求。

```
$_FILES['userfile']['name']
$_FILES['userfile']['type']
$_FILES['userfile']['tmp_name']
$_FILES['userfile']['error']
$_FILES['userfile']['size']
```

#### 利用文件名

通常操作系统不允许文件名中包含特定字符，但通过伪造请求可以添加这些字符，从而导致意外情况发生。例如，将文件命名为：

```
../script.php%00.png
```

仔细观察该文件名，你应该会注意到几点。

1.  首先注意到的是 `../`，这在文件名中是完全非法的，但如果你要将文件从一个目录移动到另一个目录，这却完全没问题，对吧？

2.  你可能认为你在脚本中正确验证了文件扩展名，但此漏洞利用依赖于 URL 解码，将 `%00` 转换为空字符，基本上告诉操作系统字符串到此结束，从而从文件名中剥离 `.png`。

所以现在我已将 `script.php` 上传到另一个目录，绕过了简单的文件扩展名验证。它还绕过了禁止在上传目录中执行脚本的 `.htaccess` 文件。

#### 安全地获取文件名和扩展名

你可以使用 `pathinfo()` 以安全的方式推断名称和扩展名，但首先我们需要替换文件名中的不需要字符：

```
$filename = basename($_FILES['userfile']['name']);
$filename = preg_replace('/[^a-zA-Z0-9._-]/', '', $filename);
$pathinfo = pathinfo($filename);
$extension = $pathinfo['extension'];
```

虽然现在我们有了可用于存储的文件名和扩展名，但我仍然倾向于将该信息存储在数据库中，并给该文件一个生成的名称，例如 `md5(uniqid() . microtime())`：

```
$newFilename = md5(uniqid() . microtime());
move_uploaded_file($_FILES['userfile']['tmp_name'], '/uploads/' . $newFilename);
```

| id | title | extension | mime | size | filename | time |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | myfile | txt | text/plain | 1020 | 5bcdaeddbfbd2810fa1b6f3118804d66 | 2017-03-11 00:38:54 |

这将解决重复文件名和文件名中不可预见的漏洞问题。这也会导致攻击者必须猜测文件存储在哪里，因为他或她无法专门针对该文件进行执行。

#### MIME 类型验证

检查文件扩展名以确定文件类型是不够的，因为文件可能命名为 `image.png`，但很可能包含 PHP 脚本。通过将上传文件的 MIME 类型与文件扩展名进行对比，可以验证文件是否包含其名称所指的内容。

你甚至可以更进一步来验证图像，即实际打开它们：

```
$imageInfo = getimagesize($_FILES['userfile']['tmp_name']);
if ($imageInfo === false) {
    die('Not a valid image');
}
```

你可以使用内置的 `mime_content_type()` 函数或 `finfo` 类来获取 MIME 类型。

#### 为上传文件建立白名单

最重要的是，你应该根据每个表单对文件扩展名和 MIME 类型建立白名单。

```
$allowedMimes = ['image/jpeg', 'image/png', 'image/gif'];
$allowedExts = ['jpg', 'jpeg', 'png', 'gif'];

$finfo = new finfo(FILEINFO_MIME_TYPE);
$mime = $finfo->file($_FILES['userfile']['tmp_name']);
$ext = strtolower(pathinfo($_FILES['userfile']['name'], PATHINFO_EXTENSION));

if (!in_array($mime, $allowedMimes) || !in_array($ext, $allowedExts)) {
    die('Invalid file type');
}
```

## 第 102 章：密码学

### 第 102.1 节：使用 OpenSSL 对大文件进行对称加密和解密

PHP 缺少用于加密和解密大文件的内置函数。`openssl_encrypt()` 可用于加密字符串，但将巨大的文件加载到内存中是个坏主意。

所以我们必须编写一个用户空间函数来实现。此示例使用对称 AES-128-CBC 算法加密大文件的较小块，并将它们写入另一个文件。

#### 加密文件

```
function encryptFile($source, $dest, $password) {
    $method = "aes-128-cbc";
    $ivLength = openssl_cipher_iv_length($method);
    $iv = openssl_random_pseudo_bytes($ivLength);
    $key = hash('sha256', $password, true);
    
    $fpSource = fopen($source, 'rb');
    $fpDest = fopen($dest, 'wb');
    
    fwrite($fpDest, $iv);
    
    while (!feof($fpSource)) {
        $buffer = fread($fpSource, 8192);
        $encrypted = openssl_encrypt($buffer, $method, $key, OPENSSL_RAW_DATA, $iv);
        fwrite($fpDest, $encrypted);
    }
    
    fclose($fpSource);
    fclose($fpDest);
}
```

#### 解密文件

要解密使用上述函数加密的文件，可以使用此函数。

```
function decryptFile($source, $dest, $password) {
    $method = "aes-128-cbc";
    $ivLength = openssl_cipher_iv_length($method);
    $key = hash('sha256', $password, true);
    
    $fpSource = fopen($source, 'rb');
    $fpDest = fopen($dest, 'wb');
    
    $iv = fread($fpSource, $ivLength);
    
    while (!feof($fpSource)) {
        $buffer = fread($fpSource, 8192);
        $decrypted = openssl_decrypt($buffer, $method, $key, OPENSSL_RAW_DATA, $iv);
        fwrite($fpDest, $decrypted);
    }
    
    fclose($fpSource);
    fclose($fpDest);
}
```

#### 如何使用

如果你需要一小段代码片段来了解其工作原理或测试上述函数，请查看以下代码。

```
$password = 'secret_password';
$plainFile = 'testfile.txt';
$encryptedFile = 'testfile.txt.enc';
$decryptedFile = 'testfile.txt.dec';

file_put_contents($plainFile, 'This is a test file content.');

encryptFile($plainFile, $encryptedFile, $password);
decryptFile($encryptedFile, $decryptedFile, $password);

echo file_get_contents($decryptedFile); // Should output: This is a test file content.
```

这将创建三个文件：

1.  `testfile.txt` 包含明文
2.  `testfile.txt.enc` 包含加密文件
3.  `testfile.txt.dec` 包含解密文件。其内容应与 `testfile.txt` 相同

### 第 102.2 节：对称密码

此示例演示了 CBC 模式下的 AES 256 对称密码。需要初始化向量，因此我们使用 openssl 函数生成一个。变量 `$strong` 用于确定生成的 IV 是否具有加密学强度。

#### 加密

```
$method = "aes-256-cbc"; // 密码方法
$iv_length = openssl_cipher_iv_length($method); // 获取所需的 IV 长度
$strong = false; // 设为 false 供下一行使用
$iv = openssl_random_pseudo_bytes($iv_length, $strong); // 生成初始化向量

/* 注意：稍后需要检索 IV，因此将其存储在数据库中。但是，不要重复使用相同的 IV 来再次加密数据。 */

if (!$strong) { // 如果 IV 不具备加密学强度则抛出异常
    throw new Exception("IV not cryptographically strong!");
}

$data = "This is a message to be secured."; // 我们的秘密消息
$pass = "Stack0verfl0w"; // 我们的密码

/* 注意：密码应通过 HTTPS 会话以 POST 方式提交。 */

$enc_data = openssl_encrypt($data, $method, $pass, true, $iv); // 加密
```

#### 解密

```
/* 从数据库检索 IV，并从 POST 请求获取密码 */

$dec_data = openssl_decrypt($enc_data, $method, $pass, true, $iv); // 解密
```

#### Base64 编码与解码

| `base64_encode()` | `base64_decode()` |
| --- | --- |

如果加密数据需要以可打印文本的形式发送或存储，则应分别使用 `base64_encode()` 和 `base64_decode()` 函数。

## 第 103 章：密码哈希函数

随着更安全的 Web 服务避免以明文格式存储密码，PHP 等语言提供了各种（不可解密的）哈希函数来支持更安全的行业标准。本主题提供了在 PHP 中正确哈希的文档。

### 第 103.1 节：创建密码哈希

| `password_hash()` |
| --- |

使用 `password_hash()` 创建密码哈希，以采用当前行业最佳实践标准的哈希或密钥派生。在撰写本文时，标准是 [bcrypt](https://en.wikipedia.org/wiki/Bcrypt)，这意味着 `PASSWORD_DEFAULT` 包含相同的值。

第三个参数不是强制性的。

'cost' 值应根据您的生产服务器硬件来选择。增加它将使密码生成的成本更高。生成成本越高，任何试图破解它的人生成它所需的时间也就越长。成本理想情况下应尽可能高，但在实践中，应设置为不会使所有操作过度变慢。0.1 到 0.4 秒之间是可以接受的。如果不确定，请使用默认值。

#### 版本 < 5.5

| `password_*` |
| --- |

在低于 5.5.0 的 PHP 版本中，`password_*` 函数不可用。您应该使用 [兼容包](https://github.com/ircmaxell/password_compat) 来替代这些函数。请注意，兼容包需要 PHP 5.3.7 或更高版本，或已回移植 `$2y` 修复的版本（如 RedHat 提供的版本）。

| `crypt()` | 作为 `password_hash()` |
| --- | --- |

| `crypt()` |
| --- |

如果您无法使用那些函数，可以使用 `crypt()` 实现密码哈希。由于 `password_hash()` 是作为 `crypt()` 函数的封装器实现的，因此您无需损失任何功能。

```php
// 这是一个简单的 bcrypt 哈希实现，其他方面与
// `password_hash()` 兼容
// 不保证保持完整 `password_hash()`
// 实现的相同加密强度
// 如果 `CRYPT_BLOWFISH` 为 1，意味着 bcrypt（使用 blowfish）
// 在您的系统上可用
if (CRYPT_BLOWFISH == 1) {
    $salt = mcrypt_create_iv(16, MCRYPT_DEV_URANDOM);
    $salt = base64_encode($salt);
    // crypt 使用一种修改过的 base64 变体
    $source = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/';
    $dest = './ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
    $salt = strtr(rtrim($salt, '='), $source, $dest);
    $salt = substr($salt, 0, 22);

    // `crypt()` 通过传入的 salt 字符串的形式
    // 来确定使用哪种哈希算法
    $hashedPassword = crypt($plaintextPassword, '$2y$10$' . $salt . '$');
}
```

#### 密码哈希的 Salt

尽管 crypt 算法可靠，但仍然容易受到 [彩虹表](https://en.wikipedia.org/wiki/Rainbow_table) 攻击。这就是为什么建议使用 salt 的原因。

Salt 是在哈希前附加到密码上的某些数据，以使源字符串唯一。给定两个相同的密码，由于它们的 salt 是唯一的，因此生成的哈希也将是唯一的。

随机 salt 是您密码安全最重要的组成部分之一。这意味着即使拥有已知密码哈希的查找表，攻击者也无法将您用户的密码哈希与数据库中的密码哈希匹配，因为使用了随机 salt。您应该始终使用随机且加密安全的 salt。[阅读更多](http://www.springer.com/us/book/9781484221198)

| `password_hash()` |
| --- |

使用 `password_hash()` 的 bcrypt 算法，明文 salt 会与生成的哈希一起存储，这意味着哈希可以在不同的系统和平台间传输，仍然可以针对原始密码进行验证。

#### 版本 < 7.0

尽管不鼓励这样做，但您可以使用 salt 选项来定义您自己的随机 salt。

**重要。** 如果省略此选项，`password_hash()` 将为每个哈希密码生成一个随机 salt。这是预期的操作模式。

#### 版本 ≥ 7.0

自 PHP 7.0.0 起，salt 选项已被[弃用](http://php.net/manual/ru/function.password-hash.php)。现在首选直接使用默认生成的 salt。

### 第 103.2 节：确定现有密码哈希是否可以升级为更强的算法

如果您使用 `PASSWORD_DEFAULT` 方法让系统选择最佳算法来哈希您的密码，随着默认算法强度的增加，您可能希望在用户登录时重新哈希旧密码。
