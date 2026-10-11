

# HTML 注释和 PHP 标签

HTML 注释和 PHP 标签也会被剥离。这是硬编码的，无法通过 `allowable_tags` 更改。

| `<br>` | `>` | `<br/>` |
| --- | --- | --- |

在 PHP 5.3.4 及更高版本中，自闭合 XHTML 标签会被忽略，因此在 `allowable_tags` 中应仅使用非自闭合标签。例如，要同时允许 `<br>` 和 `<br/>`，应使用：

```
allowable_tags = "<br><br/>"
```

# 第 101 章：安全

## 第 101.6 节：文件包含

### 远程文件包含

远程文件包含（也称为 RFI）是一种允许攻击者包含远程文件的漏洞类型。

此示例注入了一个包含恶意代码的远程托管文件：

```
include($_GET['file']);
```

### 本地文件包含

本地文件包含（也称为 LFI）是通过 Web 浏览器在服务器上包含文件的过程。

```
include("includes/" . $_GET['page'] . ".php");
```

### RFI 和 LFI 的解决方案

建议仅允许包含你批准的文件，并仅限于这些文件。

```
$allowed = array('page1', 'page2', 'page3');
if (in_array($_GET['page'], $allowed)) {
    include($_GET['page'] . '.php');
}
```

## 第 101.7 节：错误报告

默认情况下，如果脚本中发生意外情况，PHP 会直接在页面上输出错误、警告和通知消息。这对于解决脚本的特定问题很有用，但同时也会输出你不想让用户知道的信息。

因此，在生产环境中，避免显示那些会泄露服务器信息（例如目录树）的消息是一种良好的实践。在开发或测试环境中，这些消息可能仍然有利于显示以进行调试。

### 快速解决方案

你可以将它们关闭，使消息完全不显示，但这会使调试脚本变得更难。

```
ini_set('display_errors', 0);
```

或直接在 `php.ini` 中更改它们：

```
display_errors = 0
```

### 错误处理

一个更好的选择是将这些错误消息存储在一个更有用的地方，比如数据库：

```
set_error_handler(function ($errno, $errstr, $errfile, $errline) {
    // 记录到数据库
    $db->query("INSERT INTO error_log (message, file, line) VALUES (?, ?, ?)", [$errstr, $errfile, $errline]);
    return true; // 阻止默认处理程序
});
```

此方法将消息记录到数据库，如果失败则记录到文件，而不是直接回显到页面中。这样你可以追踪用户在你网站上遇到的问题，并在出错时立即收到通知。

## 第 101.8 节：上传文件

如果你想让用户向你的服务器上传文件，在实际将上传的文件移动到 Web 目录之前，你需要进行一些安全检查。

### 上传的数据

`$_FILES` 数组包含用户提交的数据，并非文件本身的信息。虽然通常这些数据由浏览器生成，但可以使用软件轻松地向同一表单发起 POST 请求。

```
$_FILES['userfile']['name']
$_FILES['userfile']['type']
$_FILES['userfile']['tmp_name']
$_FILES['userfile']['error']
$_FILES['userfile']['size']
```

### 利用文件名

通常操作系统不允许文件名中包含特定字符，但通过伪造请求可以添加这些字符，从而导致意外情况发生。例如，将文件命名为：

```
../script.php%00.png
```

仔细观察该文件名，你应该会注意到几点。

1.  首先注意到的是 `../`，这在文件名中是完全非法的，但如果你要将文件从一个目录移动到另一个目录，这却完全没问题，对吧？
2.  你可能认为你在脚本中正确验证了文件扩展名，但此漏洞利用依赖于 URL 解码，将 `%00` 转换为空字符，基本上告诉操作系统字符串到此结束，从而从文件名中剥离 `.png`。

所以现在我已将 `script.php` 上传到另一个目录，绕过了简单的文件扩展名验证。它还绕过了禁止在上传目录中执行脚本的 `.htaccess` 文件。

### 安全地获取文件名和扩展名

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

### MIME 类型验证

检查文件扩展名以确定文件类型是不够的，因为文件可能命名为 `image.png`，但很可能包含 PHP 脚本。通过将上传文件的 MIME 类型与文件扩展名进行对比，可以验证文件是否包含其名称所指的内容。

你甚至可以更进一步来验证图像，即实际打开它们：

```
$imageInfo = getimagesize($_FILES['userfile']['tmp_name']);
if ($imageInfo === false) {
    die('Not a valid image');
}
```

你可以使用内置的 `mime_content_type()` 函数或 `finfo` 类来获取 MIME 类型。

### 为上传文件建立白名单

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

# 第 102 章：密码学

## 第 102.1 节：使用 OpenSSL 对大文件进行对称加密和解密

PHP 缺少用于加密和解密大文件的内置函数。`openssl_encrypt()` 可用于加密字符串，但将巨大的文件加载到内存中是个坏主意。

所以我们必须编写一个用户空间函数来实现。此示例使用对称 AES-128-CBC 算法加密大文件的较小块，并将它们写入另一个文件。

### 加密文件

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

### 解密文件

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

### 如何使用

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

## 第 102.2 节：对称密码

此示例演示了 CBC 模式下的 AES 256 对称密码。需要初始化向量，因此我们使用 openssl 函数生成一个。变量 `$strong` 用于确定生成的 IV 是否具有加密学强度。

### 加密

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
```

