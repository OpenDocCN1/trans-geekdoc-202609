
```html
Password: <input type="password" name="password" /><br /><br />
<img src="captcha.php" /><br />
<input type="text" name="captcha" /><br /><br />
<input type="submit" name="Sign Up" />
</p>
</form>
```

文件 captcha.php 然后使用 GD 库生成 CAPTCHA 图像（参见列表 14-3）：

### 列表 14-3：captcha.php

```php
<?
session_start();

$img = imagecreate(400,100);
$captcha = "";
for ( $i=rand(5,7); $i >= 0; $i-- )
    $captcha .= chr(rand(ord('A'),ord('Z')));

$white = imagecolorallocate($img, 255, 255, 255);
$black = imagecolorallocate($img, 0, 0, 0);

imagestring($img, 5, 3, 3, $captcha, $black);

header("Content-type:image/jpeg");
imagejpeg($img);

$_SESSION['captcha'] = $captcha;
?>
```

表单处理页面随后会将 $_SESSION['captcha'] 的值与表单中提供的值进行比对。

该系统存在一些缺陷，其中最严重的是无法同时打开多个带有 CAPTCHA 的表单并使它们同时正常工作。代码执行后会变得显而易见的另一点是，这种 CAPTCHA 很容易被传统的 OCR（光学字符识别）技术读取。它仅用作示例。

改进此示例的一些非常简单的方法包括：

- 使用 True Type 字体（TTF）代替默认的 GD 字体。
- 使字母相互接触和/或在某些字母上画非直线，使其更难区分彼此。
- 添加一些颜色。
- 按字母分别变化字体大小和 Y 轴上的位置。

## 摘要

您可以采取各种措施来加固 MySQL 服务器。最重要的是只向用户授予必要的权限。例如，您绝不应该看到：

- 具有 `SUPER` 权限的应用用户。
- 具有 `CREATE` 权限的应用用户。
- 任何有权访问 mysql 元数据模式的人。
- MySQL 用户主机名为 `'%'`，允许来自世界各地的访问。

此外，PHP 提供了许多功能，可在应用程序中实现更好的安全性，包括对加密的强力支持和多种不同的哈希算法。然而，如果网站未受到常见（甚至不常见）漏洞的保护，这些都毫无用处。本章涵盖的一些漏洞包括：

- SQL 注入
- 重放攻击
- 跨站脚本攻击（XSS）
- 跨站请求伪造（CSRF）
- 自动化

了解每个漏洞都很重要。然而，最重要的是要明白，并非总是最佳做法为应用程序定制安全方案。诸如 CAPTCHA 和 XSS 攻击防护等问题已是已解决的问题，库提供了在不重新发明轮子或编写大量代码的情况下轻松实现功能和修复的方法。

## 15

## 命令行和 Web 服务

### 本章内容

- 构建命令行服务
- 创建周期性任务
- 使用 WSDL 描述 Web 服务
- 构建 RESTful Web 服务
- 使用 SOAP 构建 Web 服务

PHP 和 MySQL 的用途远不止面向消费者的网站。它们能够做更多的事情。迄今为止，本书已介绍了将 PHP 用作 Gearman 工作器以及重写 URL 的工具。本章探讨了 PHP 的一些不太传统的用途，扩展了前几章中表达的主题。

本章还讨论了使用 PHP 创建 Web 服务，即两个方之间通信的端点。这些方可以是应用程序和另一台服务器、应用程序和用户，甚至是应用程序和任何可以从访问部分应用程序信息中受益的第三方。

## 创建命令行脚本

当谈到命令行脚本时，PHP 并不是首先想到的语言。虽然使用 PHP 来实现这一目的与使用其他语言一样常见，但 PHP 非常强大。本节介绍如何使用 PHP CLI（命令行界面）创建命令行脚本。本章主要关注 UNIX/Linux；然而，许多概念同样适用于 Windows。

创建命令行脚本的第一步是创建一个独立的可执行文件。这在第 11 章中已介绍，当时您创建了一个动态重写映射。CLI 不关心文件名是否以 PHP 结尾，因此文件可以有任何扩展名（常见做法是根本没有扩展名）。重要的是文件以以下两种方式之一启动：

- 作为 php 的参数：`php ./filename`
- 直接：`./filename`

虽然第二种方法更受青睐，但由于有两个要求，设置起来更麻烦。第一个要求是文件的第一行必须是 shebang——指示 shell 使用特定程序执行文件的指令。PHP 的 shebang 通常如下所示：

```
#!/usr/bin/php
```

如果 shell 不知道文件是可执行的，shebang 将永远不会被读取。因此第二个要求是文件具有正确的权限。在 UNIX/Linux 上，这很简单：

```
chmod +x ./filename
```

大多数文件版本控制系统会维护可执行状态。完成此操作后，只需在命令行键入 ./filename 即可执行文件。最好在其中放入 <?= "hello world"; ?> 之类的内容。否则它只会启动并立即退出。

本节构建一个命令行类，可为任何命令行应用程序扩展。每个功能部分都扩展了基类。在命令行部分结束时，您将获得完成的基类的列表。但首先，应用程序必须能够读取用户输入。

### 读取命令行输入

基类完成了处理参数的大部分繁重工作。派生类注册每个参数。使用注册方法意味着您不会直接操作参数，确保可以拥有多个继承层级并协同工作。

第 14 章介绍了加密和安全，在这个非常简单的应用程序中再次使用，并且将接受要编码的数据。数据从命令行读取。此外，您可以指定密码、密钥、编码模式和初始化向量。

新类中的注册函数接受多个参数：

- 选项标志的简写
- 选项标志的长写
- 一个布尔值，指定该标志是否应跟随一个值
- 该标志的帮助字符串
- 验证回调函数

实际上只需要简写标志。第一个注册函数如下所示：

```
$this->registerParameter("c", "cipher", true,
    "The cipher to use. Use the -l option to list all valid ciphers.",
    array($this,"isValidCipher"));
```

前面的注册行将接受以下两种形式之一的输入：

```
./phpcrypt -c=DES "text to encrypt"
./phpcrypt --cipher=DES "text to encrypt"
```

它使用成员方法 isValidCipher() 验证输入。有关使用回调函数的更多信息，请参阅第 1 章。注册所有这些开关的好地方是在构造函数中。您新类的构造函数如下所示：

```
public function __construct() {
    parent::__construct();
    $this->registerParameter("c", "cipher", true,
        "The cipher to use. Use the -l option to list all valid ciphers.",
        array($this, "isValidCipher"));
    $this->registerParameter("m", "mode", true, "The encoding mode to use.",
        array($this, "isValidMode"));
    $this->registerParameter("I", "iv", true, "The initialization vector to use.",
        array($this, "isValidIV"));
    $this->registerParameter("s", "secret", true, "The secret key to use.",
        "strlen");
    $this->registerParameter("i", "interactive", false, "Use interactive encryption.");
    $this->registerParameter("l", "list", false, "Lists all valid encoding modes.");
}
```

注册顺序对验证很重要。例如，为了确保初始化向量有效，重要的是首先设置加密密码，因为不同密码需要不同长度的向量。

验证方法如下所示：

```
public function isValidIV( $iv ) {
    return ( strlen($iv) != mcrypt_get_iv_size($this->cipher, $this->mode) );
}

public function isValidCipher( $cipher ) {
    return in_array($cipher, mcrypt_list_algorithms());
}

public function isValidMode( $mode ) {
    return in_array($mode, mcrypt_list_modes());
}
```

在幕后，它通过变量 $argc 和 $argv 访问参数。$argc 变量包含通过命令行传递的参数数量。$argv 变量包含这些参数的数组。脚本的文件名始终计为第一个参数，因此通过 CLI 执行脚本时至少总会有一个参数。
