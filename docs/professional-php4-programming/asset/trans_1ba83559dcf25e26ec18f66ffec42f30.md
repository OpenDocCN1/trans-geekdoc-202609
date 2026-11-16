

## socket_set_blocking()

```
int socket_set_blocking(int socket_descriptor, int mode)
```

此函数用于设置或取消套接字的阻塞 I/O 状态。第一个参数是套接字描述符，如果第二个参数为 true，则将套接字设置为阻塞套接字。如果第二个参数为 false，则将其设置为非阻塞套接字。

读取阻塞套接字的函数会一直等待，直到套接字上有数据可供读取。如果套接字是非阻塞的，当数据不可用时，此类函数会立即返回并带有错误条件。

## socket_set_timeout()

```
boolean socket_set_timeout(int socket_descriptor, int seconds, int micros)
```

此函数用以微秒为粒度设置套接字的超时。第一个参数是套接字描述符，第二个参数是超时周期的秒部分，第三个参数是超时周期的微秒部分。超时周期决定了套接字在没有任何 I/O 活动的情况下应保持打开的时间。

## read()

```
int read(int socket_descriptor, string buffer, int length [, int type])
```

此函数可用于从作为第一个参数指定的套接字描述符读取数据。length 参数表示要读取的字节数，buffer 参数表示存放读取数据的缓冲区。

可选的 type 参数可以指定为 PHP_NORMAL_READ 或 PHP_BINARY_READ。如果 type 为 PHP_NORMAL_READ，读取操作一旦遇到 \n（换行）或 \r（回车）字符即停止。如果 type 为 PHP_BINARY_READ，读取操作将持续进行，直到没有更多数据或已读取指定数量的字节。从 4.0.6 版本起，如果省略 type，默认行为与指定 PHP_NORMAL_READ 相同。该函数返回读取的字节数，如果发生错误则返回 FALSE。

## write()

```
int write(int socket_descriptor, string &buffer, int length)
```

此函数是 read() 函数的补充函数。它将第二个参数指定的缓冲区中的字节写入作为第一个参数指定的套接字描述符。第三个参数决定要写入的字节数。该函数返回写入的字节数，如果发生错误则返回 false。

## strerror()

```
string strerror(int errno)
```

套接字函数设置的错误号无法告诉我们出了什么问题。将错误号作为参数传递给 strerror()，会返回一个字符串，该字符串是错误消息的详细描述。

## Mail Client Application

在本节中，我们将开发一个应用程序，本质上是一个邮件客户端，它将允许我们应用对套接字 API 和 DNS 名称解析工作原理的理解。我们将使用 DNS API 获取邮件服务器的地址信息，并使用套接字 API 连接到邮件服务器，使用 SMTP（邮件协议）与其通信。此示例仅用于说明目的。任何严肃的应用程序都应依赖作为 PHP 发行版固有部分提供的 Mail API：

![](img/9cf7789dba9b16ef3f8576d5aea89186_488_0.png)

初始屏幕（mailer.html）的 HTML：

```html
<html>
<head>
<title>Simple SMTP mail client</title>
</head>
<body bgcolor="#999999" text="#000000" link="#0000EE"
vlink="#551A8B" alink="#FF0000">
<h1>Simple SMTP mail client</h1>
<form action="mailerPost.php" method="post" name="compose">
<table border="0" cellpadding="3" cellspacing="0" width="100%">
<tr>
<td><font size="2"><b>To:</b></font></td>
<td><input type="text" size="50" name="To" /></td>
</tr>
<tr>
<td><font size="2"><b>From:</b></font></td>
<td><input type="text" size="50" name="From" /></td>
</tr>
<tr>
<td><font size="2"><b>Subject:</b></font></td>
<td><input type="text" size="50" name="Subject" /></td>
</tr>
</table>
<table border="0">
<font size="2"><b>Message:</b></font><br>
<textarea name="Message" rows="15" cols="50"
wrap="virtual"></textarea>
<br><br>
<input type="submit" name="button" value="Send">
<input type="submit" name="button" value="Cancel"> </form>
</body>
</html>
```

mailerPost.php 脚本：

```php
<?php
error_reporting(E_ALL);
if ($button != "Send") {
    include("mailer.html");
} else {
    $tmp = explode('@', $To);
    if (!$tmp[0]) {
        usage();
    } else {
        $serverName = $tmp[1];
    }
    $tmp = explode('@', $From);
    if (!$tmp[0]) {
        usage();
    } else {
        $clientName = $tmp[1];
    }
$tmpSmtpServer = getmxrr($serverName, $mxhosts);
if ($tmpSmtpServer == FALSE) {
    //if no MX records are returned we attempt to
    // send it to the host portion of the e-mail address
    $smtpServer = $serverName;
} else {
    $smtpServer = $tmpSmtpServer[0];
}
$smtpServerIP = gethostbyname($smtpServer);
$smtpServerPort = getservbyname('smtp', 'tcp');
$socket = socket(AF_INET, SOCK_STREAM, 0);
if ($socket < 0) {
    errQuit("socket() failed: " . strerror($socket));
}
$conn = connect($socket, $smtpServerIP, $smtpServerPort);
if ($conn < 0) {
    errQuit("connect() failed: " . strerror($conn));
}
$msg = "HELO $clientName\r\n";
doProtocol($socket, $msg);

$msg = "MAIL FROM: 'From'\r\n";
doProtocol($socket, $msg);

$msg = "RCPT TO: '$To'\r\n";
doProtocol($socket, $msg);

$msg = "DATA\r\n";
doProtocol($socket, $msg);

$msg = "'$Message'\r\n.\r\n";
doProtocol($socket, $msg);

$msg = "QUIT\r\n";
doProtocol($socket, $msg);

close($socket);

echo("<h2>Message successfully sent to '$To' </h2>");
}

function doProtocol($socket, $msg)
{
    $ret = write($socket, $msg, strlen($msg));
    if ($ret < 0) {
        errQuit("write() failed: " . strerror($ret));
    }

    $out = " ";
    while(($ret = read($socket, $out, 4096)));

    if ($ret < 0) {
        errQuit("read() failed: " . strerror($ret));
    }
    return;
}

function errQuit($msg)
{
    echo($msg . "<br>");
    echo("<h3>Could not send message</h3>");
    exit(-1);
}

function usage()
{
    include("mailer.html");
    exit(-1);
}
?>
```

## Network Information Service

在前面关于 DNS 的章节中，我们了解到 DNS 充当分布式数据库，用于存储网络名称到地址的映射，客户端可以查询这些映射以获取映射信息。同样，通常有必要以这种方式存储用户、密码、网络信息和网络服务的相关信息，以便客户端可以跨网络访问这些信息数据库。

大多数早期的桌面操作系统（包括 UNIX）最初是为在单机上运行而设计的，而不是在网络上运行。这意味着用户和系统资源只需在特定机器上被唯一标识即可。例如，如果用户在工作站上有一个名为 jdoe 的登录名，那么在不同的工作站上使用相同的名称也是完全可以的。局域网络出现后，这有时有益，有时则相当麻烦。

在用户在多台机器上都有账户的网络中，他们需要记住每台机器的密码，并且当账户发生更改时，必须在所有机器上重复此更改。Sun Microsystems 设计了网络信息服务（NIS），早期称为 Yellow Pages，以解决其中的一些问题。

NIS 提供一组全网范围的信息数据库，允许不同机器上的客户端访问 NIS 为主机、网络和其他信息维护的数据库中的信息。但是，NIS 具有一些限制其在特定网络环境外使用的特性。首先，与 DNS 不同，它不是一个分层系统。NIS 符合扁平信息结构，给定的 NIS 服务器维护特定网络（称为域）的一组资源信息，不能将其指向另一个 NIS 服务器以获取其他网络上主机的相关信息。

让我们来看看构成 NIS 基础设施的各种实体：

![](img/9cf7789dba9b16ef3f8576d5aea89186_491_0.png)

