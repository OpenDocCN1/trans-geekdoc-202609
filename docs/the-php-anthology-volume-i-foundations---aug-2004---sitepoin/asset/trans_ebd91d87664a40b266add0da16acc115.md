

files 会让你的代码用户感到不安，出于安全考虑，通常有必要能够使用不同的扩展名来识别配置文件，例如，可以使用 .htaccess 对其进行保护。方便的替代方案是 PHP 的 parse_ini_file 函数，它解析使用与 php.ini 相同格式的文件。

请参考以下文件：

```
File: demo/example.ini

; Settings to connect to MySQL
[Database_Settings]
host=localhost
user=harryf
pass=secret
dbname=sitepoint

; Default look of the site
[Preferences]
color=blue
size=medium
font=verdana
```

使用 parse_ini_file，PHP 将读取内容并使用它们构建一个二维数组：

```
File: 14.php

<?php
$iniVars = parse_ini_file('demo/example.ini', TRUE);

echo '<pre>';
print_r($iniVars);
echo '</pre>';
?>
```

请注意，我们用于 parse_ini_file 的第二个布尔参数告诉它文件包含子节（[Database_Settings] 和 [Preferences]），因此应使用这些子节来构建多维数组。

以下是输出：

```
Array
(
    [Database_Settings] => Array
    (
        [host] => localhost
        [user] => harryf
        [pass] => secret
        [dbname] => sitepoint
    )
    [Preferences] => Array
    (
        [color] => blue
        [size] => medium
        [font] => verdana
    )
)
```

使用我们在第 3 章中创建的 MySQL 类连接到 MySQL 现在可以这样实现：

```
$iniVars = parse_ini_file('demo/example.ini', TRUE);

$mysql = &new MySQL(
    $iniVars['Database_Settings']['host'],
    $iniVars['Database_Settings']['user'],
    $iniVars['Database_Settings']['pass'],
    $iniVars['Database_Settings']['dbname']
);
```

## 如何从远程服务器访问文件？

迄今为止我还没告诉你的是，在大多数情况下，PHP 可以通过 Internet 以几乎与访问本地文件完全相同的方式访问远程服务器上的文件。这里的主要限制是，你不能使用 `filesize` 函数，或其他用于获取文件信息的函数。

重用“如何读取本地文件？”中的 5.php，我们可以这样直接从 SitePoint 获取一直在使用的原始文件：

```
<?php
// Open the file handle for reading
$fp = fopen('http://www.sitepoint.com/print/758', 'r');
// Loop while the connection is good and not at end of file
while (!feof($fp)) {
    // Get a chunk to the next linefeed
    $chunk = fgets($fp);
    echo $chunk;
}

// Close the file handle!
fclose($fp);
?>
```

我们所要做的就是将 fopen 函数指向的位置改为一个 URL！

这种方法的问题是，我们采用了一个针对本地文件系统设计的函数，并用它来访问远程 Web 服务器。fopen 不太擅长处理你在 Internet 上通常会遇到的问题，例如超时，并且无法提供远程连接可能需要的详细错误报告。它还会删除远程 Web 服务器发送的 HTTP 响应头，这些头有时是必需的——例如，在 Web 服务中——并且会自动处理请求头，而你可能需要自己控制请求头。

让我们看看替代方案 fsockopen：

```
<?php
$host = 'www.sitepoint.com'; // Remote host
$port = '80'; // Port number
$timeout = '10'; // Timeout in seconds
$uri = '/print/758'; // Page to fetch

// Open remote socket
if (!$fp = fsockopen($host, $port, $errNo, $errMsg, $timeout)) {
    die('Error connecting: ' . $errNo . ' - ' . $errMsg);
}

// Build an HTTP request header
$requestHeader = "GET " . $uri . " HTTP/1.1\r\n";
$requestHeader .= "Host: " . $host . "\r\n\r\n";

// Send the request header
fputs($fp, $requestHeader);

// Loop while the connection is good and not at end of file
while (!feof($fp)) {
    // Get a chunk to the next linefeed
    $chunk = fgets($fp);
    echo $chunk;
}

// Close the file handle!
fclose($fp);
?>
```

查看上述脚本的原始输出，我们看到页面顶部有以下 HTTP 头：

```
HTTP/1.1 200 OK
Date: Sun, 09 Mar 2003 18:06:59 GMT
Server: Apache/1.3.27 (Unix) PHP/4.3.1
X-Powered-By: PHP/4.3.1
Connection: close
Content-Type: text/html
```

对 HTTP 协议的详细分析超出了本书的范围；不过，本章末尾建议了一些参考资料。

## 如何在 PHP 中使用 FTP？

PHP 的一大优点是其内置或仅需扩展即可使用的功能数量庞大；文件传输协议 (FTP) 也不例外。使用 PHP 的 FTP 功能，可以让 PHP 脚本充当 FTP 服务器的客户端。这对于从为 FTP 文件存储库构建 Web 接口，到开发从 PHP 开发环境更新站点的工具等，都非常有用。要使用 FTP 函数，需要确保主机已启用 PHP 的 FTP 功能（参见附录 B）。

![](img/5b6cdf7cf4cf53e30b19e047895dc464_151_0.png)

### FTP 不安全

无论通过何种方式连接到普通 FTP 服务器，你提供的用户名和密码都会以明文形式发送到服务器。这些信息可能会被任何在你与连接服务器之间“插入”的数据包嗅探器读取。请务必定期更改密码，并且一般来说，在有更好的替代方案时，尽量避免使用 FTP。

如果你有 SSH 权限访问站点并且使用 Windows，WinSCP[6] 是通过安全连接传输文件的一个好工具。

让我们从一个简单的示例开始：

```
<?php
// Set time limit to infinite
set_time_limit(0);

// Define server and target directory
$ftpServer = 'ftp.uselinux.org';
$targetDir = '/pub/redhat/updates/8.0/en/os/i386';

// Connect server
if (! $ftp = ftp_connect($ftpServer, 21, 30)) {
    die('Connection failed');
}

// Login anonymously
if (! ftp_login($ftp, 'anonymous', 'you@yourdomain.com')) {
    die('Login failed');
}
```

首先，我们使用 set_time_limit 函数删除脚本执行时间限制。在这个特定示例中，默认的 30 秒 PHP 脚本执行时间应该足够长，但对于涉及文件传输的脚本，可能确实需要更长的执行时间。

我们使用 ftp_connect 函数打开到 FTP 服务器的连接，指定服务器的端口号（可选：默认为 21）以及 PHP 放弃连接尝试前的秒数（默认为 90）。

之后，ftp_login 函数允许我们登录到 FTP 服务器。由于它是公共服务器，你可以以匿名用户身份登录（将电子邮件地址作为密码提供）。不过，这也可能是你 Web 服务器上的 FTP 帐户，在这种情况下，你需要提供有效的用户名和密码。

以下是示例的其余部分：

```
// Change directory
if (! ftp_chdir($ftp, $targetDir)) {
    die ('Unable to change directory to: ' . $targetDir);
}

// Display the remote directory location
echo '<b>Current Directory:</b> <code>' . ftp_pwd($ftp) .
     '</code><br />';

echo '<b>Files Available:</b><br />';

// Get a list of files on the server
$files = ftp_nlist($ftp, '.');

// Display the files
foreach ($files as $file) {
    echo $file . '<br />';
}
?>
```

接下来，我们使用 ftp_chdir 更改目录。使用 FTP 时，重要的是要记住，FTP 相关操作的根目录将是你登录服务器时所在的目录，而不是服务器的真正根目录。因此，在适当的时候请务必指定绝对路径。

为了表明我们在正确的位置，我们使用 ftp_pwd 显示当前工作目录。ftp_nlist 函数返回当前目录的文件数组，我们可以显示该数组。

列表应该如下所示：

```
Current Directory: /pub/redhat/updates/8.0/en/os/i386
Files Available:
lynx-2.8.5-7.1.i386.rpm
galeon-1.2.6-0.8.0.i386.rpm
ggv-1.99.9-5.i386.rpm
gv-3.5.8-19.i386.rpm
xinetd-2.3.7-5.i386.rpm
pam-0.75-46.8.0.i386.rpm
kamera-3.0.3-5.i386.rpm
pam-devel-0.75-46.8.0.i386.rpm
vnc-3.3.3r2-39.2.i386.rpm
```

这是 PHP FTP 函数实际运行的一个简单示例。完整的函数列表可在 PHP 手册[7]中找到。

在 PEAR::NET_FTP 中，我们有一个方便的类，可确保数据以正确的模式（ASCII 或二进制）传输，并解决与递归上传相关的问题。

