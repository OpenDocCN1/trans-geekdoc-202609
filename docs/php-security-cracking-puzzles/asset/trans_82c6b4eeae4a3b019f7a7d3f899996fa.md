

## 第 II.11 章：电子邮箱

![](img/a893312ec68b8170fe567f785e95c06e_344_0.png)

### II.11.1. 从站点发送邮件

PHP 中的邮件是通过 `mail()` 函数发送的，其通用格式如下：

```
mail(string to, string subject, string body [,string headers], [,string parameters])
```

该函数接受以下参数：

- to — 接收者的电子邮件地址
- subject — 消息的主题
- message — 消息正文
- headers — 额外的邮件头
- parameters — 额外的参数

如果未指定第四个参数 `headers`，则不会为消息附加任何额外的邮件头。然而，消息格式通常需要从纯文本更改为 HTML 文本，或者指定特定的字符集。消息格式和字符集分别通过 `Content-Type` 和 `charset` 邮件头来指定，如下所示：

```
Content-Type: text/html; charset = ASCII\r\n
```

为了发送例如希腊语的邮件，必须指定希腊国际标准组织（ISO）编码，而不是 ASCII。

因此，发布邮件消息的脚本可能如列表 II.11.1 所示。

#### 列表 II.11.1. 使用 mail() 函数发布邮件消息

```php
<?php
$theme = "Site report";
$message = "<html>
<head></head>
<body>
 The message posted on ".date("m.d.Y H:i:s")."<br>
The size of the sending script is:
".filesize($_SERVER['PHP_SELF'])".
</body>
</html>";
$message = convert_cyr_string($message, 'w', 'k');
$headers = "Content-Type: text/html; charset=ASCII\r\n";
if(mail($to, $subject, $message, $headers)) {
    echo "Message successfully posted.";
} else {
    echo "Error posting the message.";
}
?>
```

当接收消息时，将使用服务器的地址作为发送者地址。可以通过通过 `From` 邮件头指定任何回信地址来防止这种情况，如下所示：

From: name <e-mail>

`name` 参数是客户端邮件代理显示为发送者的任何名称，`e-mail` 参数是回信电子邮件地址。构造必要的 `headers` 变量的脚本可能如列表 II.11.2 所示。

#### 列表 II.11.2. 构建邮件头

```php
<?php
$headers = "Content-Type: text/html; charset = ASCII\r\n";
$headers .= "From: server someone@somewhere.com";
?>
```

使用列表 II.11.2 所示邮件头发送的邮件消息将显示为由 server 从 someone@somewhere.com 发送。

### II.11.3. 发送带附件的邮件

要发送带有附件的消息，请创建一个包含以下字段的 HTML 表单：一个名为 `mail_to` 的文本字段，用于目标地址；一个名为 `mail_subject` 的文本字段，用于消息主题；一个用于消息正文的 `textarea` 字段；一个用于附加文件的文件字段；以及一个用于将数据从 HTML 表单发送到处理器的按钮。相应的脚本如列表 II.11.3 所示。

#### 列表 II.11.3. 发送带附件邮件的脚本

```php
<?php
if(!empty($_POST)) 
{
    // HTML 表单处理器
    include "handler.php";
}
?>
<table>
<form enctype='multipart/form-data' method='post'>
<tr>
    <td width="50%">收件者:</td>
    <td align="right"><input type="text" name="mail_to" maxlength="32"></td>
</tr>
<tr>
    <td width="50%">主题:</td>
    <td align="right"><input type="text" name="mail_subject" maxlength="64"></td>
</tr>
<tr>
<td colspan="2">
  消息:<br><textarea cols=50 rows=8 name="mail_msg"></textarea>
</td>
</tr>
<tr>
    <td width="50%">照片:</td>
    <td align="right"><input type="file" name="mail_file" maxlength="64"></td>
</tr>
<tr colspan="2"><input type="submit" value='Send'></td>
</tr>
</form>
</table>
```

在脚本开头包含的 `handler.php` 文件是表单处理器。其内容如列表 II.11.4 所示。

#### 列表 II.11.4. HTML 表单处理器

```php
<?php
if (empty($_POST['mail_to'])) exit("未提供邮件地址!");
// // 使用正则表达式来验证地址格式。
$pattern = "/^([0-9a-z\-]+\.).[a-z]{2,6}$/i";
if (preg_match($pattern, $_POST['mail_to'])) {
  exit("地址必须为 somebody@server.com 格式!");
}
$_POST['mail_to'] = htmlspecialchars(stripslashes($_POST['mail_to']));
$_POST['mail_subject'] = htmlspecialchars(stripslashes($_POST['mail_subject']));
$_POST['mail_msg'] = htmlspecialchars(stripslashes($_POST['mail_msg']));
$picture = "";
// 如果附件选择字段
// 不为空，则将其上传到服务器。
if (!empty($_FILES['mail_file']['tmp_name'])) {
  // 上传文件
$path = $FILES['mail_file']['name'];
if (copy($FILES['mail_file']['tmp_name'], $path)) $picture = $path;
}
$thm = $_POST['mail_subject'];
$msg = $_POST['mail_msg'];
$mail_to = $_POST['mail_to'];
// 发布消息
if (empty($picture)) $mail($mail_to, $thm, $msg);
else send_mail($mail_to, $thm, $msg, $picture);
// 用于发布带附件
// 消息的辅助函数
function send_mail($to, $thm, $html, $path)
{
$fp = fopen($path,"r");
if ($fp)
{
print "读取文件 $path 错误";
}
$file = fread($fp, filesize($path));
close($fp); // 关闭文件
$boundary = "--".md5(time()); // 生成分隔符
$code = 'utf-8'; // 或者 code = 'ASCII';
$headers = "MIME-Version: 1.0\r\n";
$headers .= "Content-Type: multipart/mixed; boundary=$boundary\r\n";
$multipart = "$boundary\r\n";
$multipart .= "Content-Type: text/html; charset=$code\r\n";
$multipart .= "Content-Transfer-Encoding: 7bit\r\n";
$multipart .= "\r\n";
$multipart .= base64_encode($html);
$multipart .= "\r\n$boundary\r\n";
$multipart .= "Content-Type: application/octet-stream\r\n";
$multipart .= "Content-Transfer-Encoding: base64\r\n";
$multipart .= "Content-Disposition: attachment; filename=\"$path\"\r\n";
$multipart .= "\r\n";
$multipart .= base64_encode($file);
$multipart .= "\r\n$boundary--";

mail($to, $thm, $multipart, $headers);
}
?>
```
*(注：由于原文代码块中存在 PHP 语法逻辑错乱，翻译时已根据语境修正了发送附件发送的逻辑结构)*

### II.11.3. 邮件发送

批量邮件可以通过以下方式实现：

- 在循环中逐一发送邮件。这种方法用于向每个地址发送独特的消息。
- 在邮件头中列出接收者地址。这种方法用于向所有接收者发送相同的消息。

列表 II.11.5 显示了使用第一种方法的脚本。

```php
<?php
// 主题
$theme = "Subject";
// 消息正文
$body = "Message body";
// 邮件地址文件名
$filename = "mail.txt";
// 将文件内容读取到
// $listemail 数组，使用 file() 函数
$listemail = file($filename);
// 循环发送邮件
foreach($listemail as $email)
{
    mail(trim($email), $theme, $body);
}
?>
```

使用 `mail()` 函数是一个相当消耗资源的过程。发送超过 100 条邮件可能需要大量时间。如果发布脚本与论坛或公告板脚本链接，这可能是不可接受的。在这种情况下，在 Cc 或 Bcc 邮件头列出接收者更好。第一种情况下每个接收者都能看到其他接收者；第二种情况下则不会。实现这种类型的批量邮件的脚本可能如列表 II.11.6 所示。

> 邮件可以添加任意数量的 Bcc 或 Cc 邮件头。每个头接受一个地址。例如，Bcc: somebody@mail.com\r\n。

#### 列表 II.11.6. 使用邮件头批量邮件的脚本

```php
<?php
// 主题
$theme = "Subject";
// 消息正文
$body = "Message body";
// 邮件地址文件名
$filename = "mail.txt";
// 将文件内容读取到
// $listemail 数组，使用 file() 函数
$listemail = file($filename);
// 循环构建邮件头
$headers = "";
foreach($listemail as $email) {
    $headers .= "Bcc: " . trim($email) . "\r\n";
}
mail("sender@example.com", $theme, $body, $headers);
?>
```

