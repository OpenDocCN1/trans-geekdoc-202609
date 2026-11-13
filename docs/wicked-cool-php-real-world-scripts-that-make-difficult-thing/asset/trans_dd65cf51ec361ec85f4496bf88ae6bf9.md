
脚本首先验证卡片 ID 并在数据库中查找卡片：

```php
<?php
require_once("card_include.php");

/* Validate card ID. */
$ID = $_REQUEST['ID'];
if ((!is_numeric($ID)) || ($ID == "") || ($ID < 1) ) {
    die("Invalid ID");
}

$sql = "SELECT ID, category, content, width, height, description
FROM card_list
WHERE ID = $ID";

$result = @mysql_query($sql, $connection) or die (mysql_error());
if (mysql_num_rows($result) == 0) {
    die('Invalid ID.');
}
$card = mysql_fetch_array($result);
```

现在是时候通过检查参数来查看我们是在显示表单还是发送卡片了。我们将从发送卡片的情况开始。首要任务是检查输入参数。我们将使用的方法很简单；你很可能想要添加一个 CAPTCHA（参见“#66：创建 CAPTCHA（安全）图像”，第 129 页）或某种有效电子邮件地址格式检查。

```php
/* Determine mode - Are we displaying or sending a card? */
if (isset($_POST['rec_email'])) {
    /* Sending card */

    /* Check and clean data. */
    $sender_email = substr($_POST['sender_email'], 0, 50);
    $send_name = substr($_POST['sender_name'], 0, 50);
    $rec_email = substr($_POST['rec_email'], 0, 50);
    $rec_name = substr($_POST['rec_name'], 0, 50);
    $message = substr($_POST['message'], 0, 600);
    $message = strip_tags($message);
    $rec_name = strip_tags($rec_name);
    $send_name = strip_tags($send_name);

    if ($_POST['message'] == '') {
        die("You must give a message!");
    }
}
```

脚本刚刚从消息中删除了所有 HTML 标签，但你可能想要在其中添加某种格式，因此我们将使用来自“#42：将纯文本转换为 HTML 就绪标记”，第 77 页的 `autop()` 函数。

```php
/** Transform the text message into HTML. */
require("autop.php");
$message = autop($message);

/** Create a pickup token. */
$token = md5(strval(time()) . $send_email . $rec_email . $ID);

/** Insert the row into sent cards. */
$sql = 'INSERT INTO cards_sent
        (sender_email, sender_name, message,
         recip_email, recip_name, token, ID)
        VALUES
        ("' . $send_email . '","' .
        mysql_escape_string($send_name) . '","' .
        mysql_escape_string($message) . '","' .
        $rec_email . '","' .
        mysql_escape_string($rec_name) . '","' .
        $token . '","' .
        $ID . '")';
$result = @mysql_query($sql, $connection) or die (mysql_error());

/** PHPMailer class for sending mail */
include_once("phpmailer/class.phpmailer.php");
$mail = new PHPMailer;

$mail->ClearAddresses();
$mail->AddAddress($rec_email, $rec_name);
print "$rec_email, $rec_name<br />";
$mail->From = 'cards@example.com';
$mail->FromName = $send_name;
$mail->Subject = "You have received an e-card from $send_name!";
$mail->Body = "You have received an e-card!\n";
$mail->Body .= "Please go to
http://www.example.com/card_show.php?token=$token to view it.\n\n";
$mail->Body .= "Sincerely,\nThose e-card guys";

if ($mail->Send()) {
    print 'Your e-card was sent!';
} else {
    print 'There was an error: ' . $mail->ErrorInfo;
}
}
```

当给定表单数据时，发送卡片就只需这些。注意外发电子邮件消息中对最终脚本 card_show.php 及其 token 参数的引用。你需要修改前面片段的部分内容，特别是 URL，你可能希望将其放在 card_include.php 中。此外，此脚本应将用户重定向到另一个看起来更好的页面。

如果我们只是显示表单，任务就归结为琐碎的工作：

```php
} else {
/* Display card and sending form. */
    print '<span style="font-family: sans-serif; font-size: 12px;">';
    print '<form action="card_send.php" method="post">';
    print '<input name="ID" type="hidden" value="" . $card['ID'] . "">';
    display_card($card);
    print '<br />';
?>
Recipient Email:<br />
<input name="recip_email" type="text" size="30" maxlength="50">
<br /><br />
Recipient Name:<br />
<input name="recip_name" type="text" size="30" maxlength="50">
<br /><br />
Message (No HTML, 600 characters max):<br />
<textarea name="message" cols="40" rows="6"></textarea>
<br /><br />
Sender Email:<br />
<input name="sender_email" type="text" size="30" maxlength="50">
<br /><br />
Sender Name:<br />
<input name="sender_name" type="text" size="30" maxlength="50"></td></tr>
<br /><br />
<input name="" type="submit" value="Send Your Card!"></td></tr>
</form>
</span>
<?php
}
?>
```

图 12-4 显示了表单。

![](img/19183d2b75bf6b509317c631c0e7b817_184_0.png)

图 12-4：发送卡片

## 查看卡片

我们快完成了；现在只需要 card_show.php 脚本来向收件人显示卡片并通知发件人卡片已被查看。第一部分与几乎任何其他脚本一样；它加载包含文件并清理输入参数。在此示例中，我们丢弃 token 参数中的任何非字母数字字符：

```php
<?php
require_once("card_include.php");
$token = preg_replace('/[^a-z0-9]/i', '', $_REQUEST['token']);

$sql = "SELECT S.sender_name, S.sender_email, S.message,
        S.recip_name, S.recip_email, S.notified,
        C.content, C.width, C.height
        FROM cards_sent S, card_list C
        WHERE C.ID = S.ID
        AND S.token = '$token'";
$result = @mysql_query($sql, $connection) or die (mysql_error());
if (mysql_num_rows($result) == 0) {
    die('Invalid card.');
}
$row = mysql_fetch_array($result);
```

注意 cards_sent 中的 notified 字段：这指示卡片是否已被查看。它应在发送卡片后始终设置为 0。

打印卡片和消息是乏味的工作，但幸运的是我们有来自 card_include.php 的 display_card() 函数，因此不必记住如何根据数据库字段进行显示。

```php
print '<span style="font-family: sans-serif; font-size: 12px">';
print '<p>A card for you!</p>';
display_card($row);
print '<br />';
print '<strong>'. stripslashes($row["sender_name"]) . '</strong> writes:';
print '<br />';
print stripslashes($row["message"]);
```

现在让我们处理通知。显然，如果这不是卡片第一次被查看，我们不想再次向发件人发送电子邮件，因此我们首先检查这一点。与我们在 card_send.php 中所做的一样，我们将使用 PHPMailer 发送电子邮件：

```php
if (!$row['notified']) {
    /* Notify sender that the message was picked up. */
    include_once("phpmailer/class.phpmailer.php");
    $mail = new PHPMailer();
    $mail->ClearAddresses();
    $mail->AddAddress($row['sender_email'], $row['sender_name']);
    $mail->From = 'example@example.com';
    $mail->FromName = 'E-card People';
    $mail->Subject = 'e-card retrieved';
    $mail->Body = "Your e-card to $row[recip_name] has been picked up.
                    Sincerely,
                    Those e-card guys";
    $mail->Send();
}
```

现在我们更新 cards_sent 表中卡片的 notified 字段，以便这是唯一会发出的通知消息：

```php
$sql = "UPDATE cards_sent
    SET notified = 1
    WHERE token = '$token'";
@mysql_query($sql, $connection);
}
?>
```

图 12-5 显示了收件人从 card_show.php 看到的内容。显然，这并不十分花哨，但作为 HTML 高手的你，没有困难将其美化起来，对吧？

![](img/19183d2b75bf6b509317c631c0e7b817_186_0.png)

## 黑客脚本

改进此系统有多种方法。首要且最重要的改进之一是安装 CAPTCHA 或类似系统，以使自动发送卡片作为垃圾邮件变得困难（参见 #66：创建 CAPTCHA（安全）图像，第 129 页）。

另一个重要组成部分是管理工具，可让你添加、编辑和禁用卡片。当卡片数量达到一定程度时，在单个页面上显示和管理它们会变得困难，因此你应该添加搜索功能。

## 76：博客系统

博客很常见，因为它们非常容易编写——你真正需要的是一个跟踪日期和内容的系统。此处出现的基本博客包括用于添加条目、添加评论和查看条目的工具。该系统将条目和评论存储在 MySQL 数据库中，并使用 Smarty 进行显示模板。

以下是博客条目的主表，最初名为 blog_entries：

```sql
CREATE TABLE `blog_entries` (
  `id` INT NOT NULL AUTO_INCREMENT ,
  `title` VARCHAR( 120 ) NOT NULL ,
  `content` TEXT NOT NULL ,
  `teaser` TINYTEXT NOT NULL ,
  `entry_time` DATETIME NOT NULL ,
```
