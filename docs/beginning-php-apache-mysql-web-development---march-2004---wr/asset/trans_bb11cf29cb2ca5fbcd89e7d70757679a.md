

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

运行此 PHP 脚本时，如果出现任何问题，请确保在再次运行之前删除 postcard 数据库。否则，你将得到错误（数据库已存在）且执行将停止。

如果你需要关于 MySQL 命令的更多信息，请查看附录 F，或访问 www.mysql.com/documentation/index.html。

我们将在下一节“获取确认”中包含使用 `images` 表的代码。

## 获取确认

到为止，你已经有了一个非常酷的明信片应用程序。任何用户都可以向他们想发送的任何人发送明信片，并由 PHP 负责发送。遗憾的是，该应用程序有一个小问题。

按照目前的程序，用户很容易在“发件人”（From）字段中使用任何电子邮件地址。这是一坏事，因为可以冒他人的名义发送恶意邮件，而你不希望这样做。为了防止这种恶意行为，你必须先向“发件人”发送一封确认邮件。一旦收到确认，你就知道用户输入了正确的邮箱，就可以继续发送邮件。

这种实现确认的行为是创建工作流应用程序的第一步。我们将在第 12 章中详细地介绍工作流应用程序，但现在请理解，工作流应用程序是一种在到达目的地之前需要从各个部分获取输入的程序。

## 尝试一下

## 获取确认

为了适应这种工作流，我们在 `pc_sendmail.php` 中已经使用的大部分代码将进行复用。如果你是一位经验丰富的开发者，我们相信你非常熟悉如何“拆解”你的旧代码！如果你不熟悉拆解，现在是编写你以前在另一个应用程序中写过的函数了。经过几次修改，它就能在你的应用中运行。所以，将其复制粘贴到你的应用程序中并进行必要的更改。漂亮，这是你的第一次拆解！

为了确认电子邮件地址，明信片信息需要存储在表中以便以后检索，确认已建立：

- 1. 打开你的 PHP 编辑器并创建一个新的 PHP 文件 `db_makeconfirm.php`：确保使用正确的服务器、用户名和密码。

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

- 2. 运行 `db_makeconfirm.php`，然后检查你的 MySQL 服务器，确保数据库中确实创建了 `confirm` 表。

- 3. 在你喜欢的 PHP 编辑器中输入新改进的 `postcard.php` 并保存：

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

