
以及在需要将目录及其子目录从一个系统传输到另一个系统时的下载。

例如，以下代码连接到 FTP 服务器上的远程目录，并将包括子目录在内的内容复制到本地计算机上的某个目录¹：

```php
<?php
// Set time limit to infinite
set_time_limit(0);

// Include PEAR::Net_FTP
require_once 'Net/FTP.php';

// Define server, username and password
$ftpServer = 'ftp.uselinux.org';
$ftpUser = 'anonymous';
$ftpPass = 'user@domain.com';

// Local Directory to place files
$localDir = 'ftpdownloads/';

// Remote Directory to fetch files from
$remoteDir = '/pub/software/web/html-utils/';

// Instantiate Net_FTP
$ftp = new Net_FTP();

// Set host and login details
$ftp->setHostname($ftpServer);
$ftp->setUsername($ftpUser);
$ftp->setPassword($ftpPass);

// Connect and login
$ftp->connect();
$ftp->login();

// Specify the extensions file
$ftp->getExtensionsFile('extensions.ini');

// Get the remote directory contents
if ($ftp->getRecursive($remoteDir, $localDir)) {
    echo 'Files transferred successfully';
} else {
    echo 'Transfer failed';
}
?>
```

¹显然，如果没有安全保护，你可不想把这个放在你的网站上。

请注意，Net_FTP 的 getExtensionsFile 方法允许你指定一个文件，用于定义特定的文件扩展名（例如 .gif 和 .jpg）为二进制或 ASCII 格式，以确保它们以正确的方式传输。getRecursive 方法会获取指定远程目录的内容，包括其子目录。

假设你有权在服务器上放置文件，可以使用 putRecursive 方法轻松将相同操作反向应用。这在本地开发系统与网站之间传输项目时非常有用，尤其是在从命令行使用 PHP 时。

凭借根据扩展名正确传输文件的能力，Net_FTP 也非常适合单个的“put”和“get”文件操作，因为它消除了你需要自己设置正确传输模式的必要。

## 如何使用 PHP 管理文件下载？

开发者在构建发布供下载文件的网站时，经常会遇到如何管理这些文件的问题。也许有些文件不应公开提供。你可能还希望在访客通过 Web 表单提供其详细信息后再交付文件。处理下载可能不仅仅是将文件存储在公开目录中并从站点链接到它。

处理下载的诀窍是使用几个特殊的 HTTP 头部，让 PHP 为你“提供”文件：

```php
<?php
// Specify a file to download
$fileName = 'sample.zip';
$mimeType = 'application/zip';
if (strpos($_SERVER['HTTP_USER_AGENT'], 'MSIE 5') or
    strpos($_SERVER['HTTP_USER_AGENT'], 'Opera 7'])) {
    $mimeType = 'application/x-download';
}
// Tell the browser it's a file for downloading
header('content-disposition: attachment; filename=' . $fileName);
header('content-type: ' . $mimeType);
header('content-length: ' . filesize($fileName));

// Display the file
readfile($fileName);
?>
```

content-disposition 头部告诉浏览器将文件视为下载（即不在浏览器窗口中显示），并为其指定文件名。content-type 头部也告诉浏览器正在发送的文件类型。在大多数情况下，应选择与所发送文件类型相匹配的值；但是，Internet Explorer 5 和 Opera 浏览器有一个不良习惯，即无论 content-disposition 头部如何，都会在浏览器中显示已识别类型的文件，因此我们对这些浏览器将 MIME 类型设置为虚构的值 application/x-download。最后，content-length 头部告诉浏览器文件的大小，以便它能够显示下载进度条。

## 首先发送 HTTP 头部

请记住，头部必须在发送任何其他内容到浏览器之前传送。

请注意，PHP 的输出控制函数在此处很有帮助，因为它们允许你按正确的顺序将内容发送到浏览器：你可以“保留”PHP 已经发送到输出的内容，同时让头部通过。有关输出控制的更多详细信息，请参见第 II 卷第 5 章。

既然文件传输已受你控制，你可以将此功能集成到身份验证系统中，例如控制谁可以下载文件。

## 文件分发策略

互联网中无法解决的问题之一是如何最好地从网站分发文件。例如，如果你以 JPEG 格式出售艺术品，你将如何处理从客户处接受付款，然后仅允许他们下载已付款的图片这一过程？你如何确保他们不会重新分发购买的图片？客户可以下载已付款的图片多少次？

没有完美的解决方案。如果有人决定复制他们从你这里购买的图片并在你不知情的情况下重新分发这些副本，该怎么办？除非你提供专门为分发目的修改过的文件（例如受水印保护的图像文件），否则几乎不可能阻止他们这样做。

分发的几种不同策略如下：

- [ ] 通过电子邮件发送文件。这对于小文件很有用，因为它几乎可以保证送达，但许多电子邮件系统会限制用户可接收的文件大小（通常为一两兆字节）。

- [ ] 为客户提供唯一链接，他们可以在有限的时间内（例如一周）使用该链接下载文件。如果下载尝试失败（例如，客户在下载过程中失去 Internet 连接），此策略允许他们重试。可以生成一个唯一的随机数，并将其用于下载 URL 中。该数字与数据库中的条目对应，并在指定的时间段后过期。这至少可以限制文件被下载的次数，并应有助于防止通过相同 URL 重新分发文件。PayPal Antifraud[8] 等服务采用此方法。

- [ ] 为客户提供用户名和密码组合，供其登录网站并下载自己的文件。这种方法对 PHP Architect[9] 网站尤其有效，该网站使用它以 Adobe Acrobat 格式分发 PHP Architect 杂志。Acrobat 文件“即时生成”，并使用客户登录网站时使用的相同密码进行保护。这显然会阻止客户重新分发杂志，因为他们将不得不泄露自己的密码。

如我所说，这个问题没有完美的解决方案。但是，如果在正在下载的文件中内置某种形式的安全性（例如软件的许可证密钥），可以实现更强的保护。

## 如何使用 PHP 创建压缩的 ZIP/TAR 文件？

也许你有一个包含许多文件、不同类型的文件以及子目录的目录。可能存在需要创建整个目录下载并保留其原始结构的情况。在基于 Unix 的系统上，实现此目的的典型命令行方法是首先创建一个“归档”文件（例如 .tar 文件（.tar 文件是“磁带归档”，最初设计用于帮助将文件系统备份到磁带上）），然后使用 gzip 或 bzip2 压缩该文件。如果你有一个名为 mywork 的目录想要将其存储为单个压缩文件，可能会在命令行中输入以下内容：

```
tar cvf mywork.tar ./mywork
gzip mywork.tar
```

这会生成一个名为 mywork.tar.gz 的文件。要解压缩并提取文件，可以输入：

```
gunzip mywork.tar.gz
tar xvf mywork.tar
```

这会在当前工作目录下重新创建 mywork 目录。请注意，在典型的 Linux 发行版中，如果使用 ’z’ 标志，可以将上述示例合并在一行中：压缩 tar zcvf mywork.tar.gz ./mywork，提取 tar zxvf mywork.tar.gz。

使用 PHP 的 system 函数，你可以从 PHP 脚本中执行这些命令，前提是你的 Web 服务器有权限使用 tar 和 gzip/bzip2 可执行文件（但可能没有）。那么，如何从存储在数据库中的数据，或者 XML 文档中的节点创建归档文件呢？

多亏了 PEAR::Archive_Tar[10]，这一切都成为可能。基本功能允许你构建 .tar 文件；前提是已安装 zlib 或 bz2 扩展，你也可以压缩文件。

让我们使用本章前面处理过的一些文件创建一个归档文件：

[10] http://pear.php.net/Archive_Tar
