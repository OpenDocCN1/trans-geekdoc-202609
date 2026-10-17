
```php
$subject = $_POST["subject"];
$messagebody = $_POST["message"];
$boundary = "=MP_boundarycc948x=";
$headers = "MIME-Version: 1.0\r\n";
$headers .= "Content-type: multipart/alternative; boundary=$boundary\r\n";
$headers .= "CC: . \r\n";
$headers .= "BCC: . \r\n";
$headers .= "From: . \r\n";
$message = "This is a Multipart Message in MIME format\r\n";
$message .= "--$boundary\r\n";
$message .= "Content-type: text/html;charset=iso-8859-1\r\n";
$message .= "Content-Transfer-Encoding: 7bit\r\n\r\n";
$message .= $messagebody\r\n;
$message .= "--$boundary\r\n";
$message .= "Content-type: text/plain;charset=iso-8859-1\r\n";
$message .= "Content-Transfer-Encoding: 7bit\r\n\r\n";
$message .= $messagebody\r\n;
$message .= "--$boundary\r\n";
$mailsent = mail($to, $subject, $message, $headers);
if ($mailsent) {
    echo "恭喜！<br>";
    echo "收件人: " . $to . "<br>";
    echo "发件人: " . $from . "<br>";
    echo "主题: " . $subject . "<br>";
    echo "消息: <br>" . $messagebody;
} else {
    echo "发生了错误。";
}
?>
</body>
</html>
```

## 使用 PHP 发送邮件

现在你已经创建了数据库，请选择该数据库。

```php
mysql_select_db("postcard", $conn);
```

在数据库中创建 `images` 表，包含三列。如果成功，在屏幕上打印 "images table created"。

```php
$sql = 'CREATE TABLE images (id int NOT NULL primary key
auto_increment, img_url VARCHAR (255) NOT NULL,
img_desc text);
$success = mysql_query($sql, $conn) or die (mysql_error());
echo "images table created.';
```

现在创建两个值数组以放入 `images` 表中。我们需要知道在第 1 步中输入的明信片的位置及其描述。每个 URL 对应另一个数组中的一个描述。

遍历这些数组，提取位置和描述文本并将其插入到 `images` 表中。如果没有错误，在屏幕上打印 "Data created"，你就完成了。

```php
Echo "Data created.";
```

运行此 PHP 脚本时，如果出现任何问题，请确保在再次运行之前删除 `postcard` 数据库。否则，你将得到错误（数据库已存在）且执行将停止。

如果你需要关于 MySQL 命令的更多信息，请查看附录 F，或访问 `www.mysql.com/documentation/index.html`。

我们将在下一节“获取确认”中包含使用 `images` 表的代码。

## 获取确认

到为止，你已经有了一个非常酷的明信片应用程序。任何用户都可以向他们想发送的任何人发送明信片，并由 PHP 负责发送。遗憾的是，该应用程序有一个小问题。

按照目前的程序，用户很容易在“发件人”（From）字段中使用任何电子邮件地址。这是一坏事，因为可以冒他人的名义发送恶意邮件，而你不希望这样做。为了防止这种恶意行为，你必须先向“发件人”发送一封确认邮件。一旦收到确认，你就知道用户输入了正确的邮箱，就可以继续发送邮件。

这种实现确认的行为是创建工作流应用程序的第一步。我们将在第 12 章中详细地介绍工作流应用程序，但现在请理解，工作流应用程序是一种在到达目的地之前需要从各个部分获取输入的程序。

## 尝试一下

### 获取确认

为了适应这种工作流，我们在 `pc_sendmail.php` 中已经使用的大部分代码将进行复用。如果你是一位经验丰富的开发者，我们相信你非常熟悉如何“拆解”你的旧代码！如果你不熟悉拆解，现在是编写你以前在另一个应用程序中写过的函数了。经过几次修改，它就能在你的应用中运行。所以，将其复制粘贴到你的应用程序中并进行必要的更改。漂亮，这是你的第一次拆解！

为了确认电子邮件地址，明信片信息需要存储在表中以便以后检索，确认已建立：

1. 打开你的 PHP 编辑器并创建一个新的 PHP 文件 `db_makeconfirm.php`：确保使用正确的服务器、用户名和密码。

```php
<?php
$conn = mysql_connect("server", "joeuser", "yourpass");
mysql_select_db("postcard", $conn);
$sql = <<EOD
CREATE TABLE confirm (
id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
validator VARCHAR (52) NOT NULL,
to_email VARCHAR (100) NOT NULL,
tname VARCHAR (50) NOT NULL,
from_email VARCHAR (100) NOT NULL,
fromname VARCHAR (50) NOT NULL,
bcc_e_mail VARCHAR (100),
cc_e_mail VARCHAR (100),
subject VARCHAR (255),
postcard VARCHAR (255) NOT NULL,
message text
);
EOD;
$query = mysql_query($sql, $conn) or die(mysql_error());
echo "<table>$confirm</table> created.";
?>
```

2. 运行 `db_makeconfirm.php`，然后检查你的 MySQL 服务器，确保数据库中确实创建了 `confirm` 表。

3. 在你喜欢的 PHP 编辑器中输入新改进的 `postcard.php` 并保存：

```html
<html
<head>
<title>输入电子邮件数据</title>
</head>
<body>
<form name="theform" method="post" action="sendconf.php">
<center>
<table width="640" padding="0" cellpadding="4" cellspacing="0">
<tr>
<td colspan="2"><h2>明信片发送者/</h2></td>
</tr>
<tr bgcolor="#CCCCCC">
<td>收件人：</td>
<td><input type="text" name="toname" size="30"></td>
</tr>
<tr>
<td>邮箱：</td>
<td><input type="text" name="to" size="40"></td>
</tr>
<tr>
<td>发件人：</td>
<td><input type="text" name="fromname" size="30"></td>
</tr>
<tr>
<td>邮箱：</td>
<td><input type="text" name="from" size="40"></td>
</tr>
<tr bgcolor="#CCCCCC">
<td>抄送：</td>
<td><input type="text" name="cc" size="40"></td>
</tr>
<tr>
<td>密送：</td>
<td><input type="text" name="bcc" size="40"></td>
</tr>
<tr>
<td colspan="2">选择明信片：
<select name="postcard" onchange="changepostcard(this.value)">
<?php
include("includes/conn_mimic.inc");
$sql = "SELECT * FROM images ORDER BY img_desc";
$images = mysqli_query($sql, $conn) or die(mysql_error());
$loop = 0;
while ($imagearray = mysqli_fetch_array($images)) {
//$id = $imagearray['id'];
$url = $imagearray['img_url'];
$desc = $imagearray['img_desc'];
if ($loop == 0) {
echo "<option value='$url'>$desc</option>\n";
$img_url = $imagearray['img_url'];
} else {
echo "<option value='$url'>$desc</option>\n";
}
$loop++;
?>
?>
</select><br>
</body>
</html>
```

# 第10 章

接下来是 `pc_confirm.php`。该文件在浏览器中加载，通过 URL 中的 ID 指定指定哪一个保存的明信片正在等待确认，然后将明信片发送给指定的接收者。再次，部分内容可以从旧的 `pc_sendmail.php` 中提取。

```php
<?php
$id = $_GET['id'];
require('./includes/conn_mimic.inc');
$sql = 'SELECT * FROM form WHERE validator = '$id';
$query = mysql_query($sql, $conn) or die(mysql_error());
$pcarray = mysql_fetch_array($query);
if (!is_array($pcarray)) {
    echo "Oops! 没有确认。请联系\n您的管理员;";
    exit;
}

$to = $pcarray['to_e_mail'];
$toname = $pcarray['toname'];
$from = $pcarray['from_e_mail'];
$fromname = $pcarray['fromname'];
$bcc = $pcarray['bcc_e_mail'];
$cc = $pcarray['cc_e_mail'];
$subject = $pcarray['subject'];
$postcard = $pcarray['postcard'];
$messageBody = $pcarray['message'];

$boundary = "=MP_Boundary_xcycr948xe=";
$headers = "MIME-Version: 1.0\r\n";
$headers = "Content-type: multipart/alternative;boundary=$boundary\r\n";
if ($cc != "") {
    $headers = "CC: " . $cc . "\r\n";
}
if ($bcc != "") {
    $headers = "BCC: " . $bcc . "\r\n";
}
$headers = "From: " . $from . "\r\n";

$html_msg = "<center>";
$html_msg .= "<table width='500' border=0 cellpadding='4'>";
$html_msg .= "<tr><td>Greetings, $toname!</td></tr>";
$html_msg .= "<tr><td></td></tr>";
$html_msg .= "<tr><td>from $fromname 今天给您发送了一张明信片。<br>祝得愉快!</td></tr>";
$html_msg .= "<tr><td align='center'></td></tr>";
$html_msg .= "<img src='$postcard' border='0'>";
$html_msg .= "<tr><td align='center'></td></tr>";
$html_msg .= "<tr><td>$messageBody</td></tr>";
$html_msg .= "</td></tr></table></center>";

$message = "这是一个 MIME 格式的多部分邮件消息\n\n";
$message .= "--$boundary\n\n";
$message .= "Content-type: text/html; charset=iso-8859-1\n\n";
$message .= "Content-Transfer-Encoding: 7bit\n\n";
$message .= $html_msg . " \n";
$message .= "--$boundary--\n\n";
$message .= "Content-Type: text/plain; charset=iso-8859-1\n\n";
```

## 使用 PHP 发送邮件

```php
$message = "\$Content-Transfer-Encoding: 7bit\n";
$message = $messagebody . "\n";
$message = "$boundary-";
$mailent = mail($to, $subject, $message, $headers);
?>
<html>
<head>
<title>明信片已发送！</title>
</head>
<body>
<?php
if ($mailent) {
    echo "恭喜！以下消息已发送：<br><br>";
    echo "收件者:" . $to . "<br>";
    echo "发件者:" . $from . "<br>";
    echo "主题:" . $subject . "<br>";
    echo "消息:" . $message . "<br>";
    echo $html_msg;
} else {
    echo "发生了错误...";
}
?>
</body>
</html>
```

6. 让我们创建一个允许用户查看 `postcard.php` 的框架。（许多东西共同工作才实现功能，这种感觉很奇妙，不是吧？）`viewpostcard.php` 的棒之处在于，它的大部分内容与 `pc_confirm.php` 非常相似。是的，现在你可以复用你的一些代码了！

```php
<?php
$id = $_GET['id'];
require(includes/conn_mimic.inc');
$sql = "SELECT * FROM config WHERE validator = '$id'"
$query = mysqli_query($sql, $conn) or die(mysqli_error($conn));
$parray = mysqli_fetch_array($query);
$path = "" . ($_SERVER['HTTPS']=="on"?"https":"http") . "/" . $_SERVER['SERVER_NAME'];
strrev(strrev(strrev($_SERVER['PHP_SELF']),*/)); 
if (!$parray) {
    echo "糟糕！未找到明信片。请联系您的管理员。
    exit;
}
$to = $parray['to_e-mail'];
$toname = $parray['toname'];
$from = $parray['from_e-mail'];
$fromname = $parray['fromname'];
$bcc = $parray['bcc_e-mail'];
$cc = $parray['cc_e-mail'];
$subject = $parray['subject'];
$postcard = $parray['postcard'];
$messagebody = $parray['message'];

$html_msg = "<table width='500' border=0 padding='4**"
```
