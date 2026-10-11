
# 从 PHP 脚本发送电子邮件

如果你没有提供 SMTP 邮件服务的服务提供商，你可以将本地系统设置为 SMTP 邮件服务器来测试 `mail()`。

如果你运行的是 Linux/Unix 系统，设置邮件服务器很简单。只需以守护进程模式运行 `sendmail`。

如果你运行的是 Windows 系统，设置邮件服务器会稍微难一些。但如果你的系统上运行着 IIS（Internet Information Services，互联网信息服务），它也提供 SMTP 服务。以下是检查方法：

1. 进入控制面板 / 服务，确保简单邮件传输协议 (SMTP) 正在运行。
2. 打开命令窗口，并运行以下命令：

```
>telnet localhost 25

220 localhost Microsoft ESMTP MAIL Service, Version: 6.0.2600.1106...
help
214-This server supports the following commands:
214 HELO EHLO STARTTLS RCPT DATA RSET MAIL QUIT HELP AUTH BDAT VRFY
quit
221 2.0.0 localhost Service closing transmission channel
```

如果你得到了类似上述的输出，说明你的 IIS 作为 SMTP 邮件服务器运行正常。

## 配置 PHP 并发送测试邮件

一旦我们有了可用的 SMTP 邮件服务器，就可以尝试从 PHP 脚本发送电子邮件了。

首先，你需要验证 PHP 初始化文件 `\php\php.ini`，确保以下设置配置正确：

```
SMTP = localhost
smtp_port = 25
```

然后编写并运行以下 PHP 脚本 `MailTest.php`：

```
<?php
#  MailTest.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
mail("nobody","Testing","This is a test.","From: herong@localhost");
?>
```

在命令窗口中检查邮件是否已投递：

```
>dir \inetpub\mailroot\drop

... d9765b3001c54a1200000001.eml

>type \inetpub\mailroot\drop\d9765b3001c54a1200000001.eml

x-sender: herong@localhost
x-receiver: nobody@localhost
Received: from localhost ([127.0.0.1]) by localhost with Microsoft...
Subject: Testing
To: nobody
From: herong@localhost
Return-Path: herong@localhost
......

This is a test.
```

如果你能跟随我走到这里，说明你已成功使用 PHP 引擎从 PHP 示例脚本发送了一封电子邮件。

# 在 Linux 系统上发送电子邮件

本节提供了一个教程示例，说明如何使用 `mail()` 函数将电子邮件发送到本地 SMTP 邮件服务器。

如果你使用的是 Linux 系统，也可以按照本教程所示从 PHP 脚本发送电子邮件。

1. 确保 `sendmail` 命令工作正常：

```
herong$ which sendmail
/usr/sbin/sendmail

herong$ sendmail -r "herong@localhost" joe@localhost
Subject: Last Test

Hi Joe, This is the last test. Bye!
.

jeo$ mailx ~/Maildir
& $
Message 334:
From herong@localhost Sat Jun 11 14:13:01 2021
Return-Path: <herong@localhost>
X-Original-To: joe@localhost
Delivered-To: jeo@localhost
Subject: Last Test
Date: Sat, 12 Jun 2021 14:13:00 +0800 (CST)
From: Herong Yang <herong@localhost>
Status: RO

Hi Joe, This is the last test. Bye!
```

2. 检查 `sendmail` 日志文件：

```
herong$ sudo grep joe /var/log/maillog
Jun 12 14:04:43 mail postfix/local[697852]: ...: to=<joe@localhost>,
relay=local, delay=23, delays=23/0.01/0/0.07, dsn=2.0.0,
status=sent (delivered to maildir)
```

3. 编写 PHP 脚本以使用内置的 `mail()` 函数。

```
<?php
#  Mail-Test-2.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.

echo 'SMTP = ' . ini_get('SMTP') . "\n";
echo 'smtp_port = ' . ini_get('smtp_port') . "\n";
echo 'sendmail_from = ' . ini_get('sendmail_from') . "\n";
echo 'post_max_size = ' . ini_get('post_max_size') . "\n";
echo 'sendmail_path = ' . ini_get('sendmail_path') . "\n";

$to = "doe@localhost";
$subject = "Testing";
$message = "This is a test.";
$headers = "From: herong@localhost";
mail($to, $subject, $message, $headers);
?>
```

4. 运行上述 PHP 脚本，你应该会看到以下输出：

```
herong$ php Mail-Test-2.php

SMTP = localhost
smtp_port = 25
sendmail_from =
post_max_size = 10M
sendmail_path = /usr/sbin/sendmail -t -i
```

5. 检查 `sendmail` 日志文件：

```
herong$ sudo grep joe /var/log/maillog

Jun 11 17:26:16 mail postfix/local[703828]: ***: to=<doe@localhost>,
relay=local, delay=0.12, delays=0.08/0/0/0.04, dsn=2.0.0,
status=sent (delivered to maildir)
```

# 在 CentOS 系统上安装 PHPMailer

本节提供了一个教程示例，说明如何在 CentOS 系统上安装 PHPMailer。

使用 `mail()` 函数只能通过本地系统上的 `sendmail` 命令发送电子邮件。

如果你想通过远程邮件服务器发送电子邮件，可以使用 PHPMailer 包。

PHPMailer 具有以下功能：

* 集成 SMTP 支持 – 无需本地邮件服务器即可发送
* 支持多个收件人、抄送、密送和回复地址
* 添加附件，包括内联附件
* 支持 UTF-8 内容以及 8bit、base64、binary 和 quoted-printable 编码
* 通过 SMTPS 和 SMTP+STARTTLS 传输支持 LOGIN、PLAIN、CRAM-MD5 和 XOAUTH2 机制的 SMTP 认证
* 自动验证电子邮件地址
* 防止标题注入攻击
* 提供 50 多种语言的错误消息！
* 支持 DKIM 和 S/MIME 签名

以下是在我的 CentOS 8 计算机上安装 PHPMailer 的步骤。

1. 确保已安装 PHP Composer：

```
herong$ /usr/local/bin/composer --version
  Composer version 2.1.3 2021-06-09 16:31:20
```

2. 使用 `composer require` 命令安装 PHPMailer：

```
herong$ /usr/local/bin/composer require phpmailer/phpmailer
Using version ^6.4 for phpmailer/phpmailer
./composer.json has been created
Running composer update phpmailer/phpmailer
Loading composer repositories with package information
Updating dependencies
Lock file operations: 1 install, 0 updates, 0 removals
  - Locking phpmailer/phpmailer (v6.4.1)
Writing lock file
Installing dependencies from lock file (including require-dev)
Package operations: 1 install, 0 updates, 0 removals
  - Downloading phpmailer/phpmailer (v6.4.1)
  - Installing phpmailer/phpmailer (v6.4.1): Extracting archive
```

3. 查找 PHPMailer 类目录：

```
herong$ /usr/local/bin/composer show phpmailer/phpmailer
  name     : phpmailer/phpmailer
  descrip. : PHPMailer is a full-featured email creation and transfer
             class for PHP
  keywords :
  versions : * v6.4.1
  path     : /home/herong/local/php/vendor/phpmailer/phpmailer
  names    : phpmailer/phpmailer
```

4. 编写 PHP 脚本以测试 PHPMailer 类：

```
herong$ vi PHPMail-Test.php

<?php
#  PHPMailer-Test.php
#- Copyright 2019 (c) HerongYang.com. All Rights Reserved.

use PHPMailer\PHPMailer\PHPMailer;
use PHPMailer\PHPMailer\SMTP;
use PHPMailer\PHPMailer\Exception;

$srcDir = "/home/herong/local/php/vendor/phpmailer/phpmailer/src/";
require "$srcDir/PHPMailer.php";
require "$srcDir/SMTP.php";
require "$srcDir/Exception.php";

$mail = new PHPMailer(true);

herong$ php PHPMail-Test.php
?>
```

我从 `PHPMailer-Test.php` 的执行中未看到错误消息，因此 PHPMailer 已在我 CentOS 计算机上正确安装。

# 使用 PHPMailer 发送本地邮件

本节提供了一个教程示例，说明如何使用 `mail()` 函数和 `sendmail` 程序通过 PHPMailer 发送本地邮件。

PHPMailer 支持 3 种将邮件投递给收件人的选项：

* `$mail->isMail()` - 调用此方法可使用 PHP 内置的 `mail()` 函数将邮件投递到本地主机。这是默认选项。

