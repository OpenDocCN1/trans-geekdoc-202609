

## moveMailMsg()

将给定范围的消息移动到新邮箱。我们使用 CP_MOVE 参数调用 imap_mail_copy() 函数。没有什么能阻止你使用 imap_mail_move() 函数：

```php
function moveMailMsg($msg_set)
{
    if (!imap_mail_copy($this->stream, $msg_set, "{$this->server}
    $this->new_mailbox", CP_UID | CP_MOVE)) {
        $this->buildErrorMsg($this->ERR_STR_CANT_MOVE_MESSAGE,
        imap_last_error());
        return false;
    }
    @imap_expunge($this->stream);
    return true;
}
```

## setMsgFlag()

为给定范围的消息设置标志：

```php
function setMsgFlag($msg_set, $flags)
{
    if (!imap_setflag_full($this->stream, $msg_set, $flags, ST_UID)) {
        $this->buildErrorMsg($this->ERR_STR_CANT_SET_FLAGS,
        imap_last_error());
        return false;
    }
    return true;
}
```

## clearMsgFlag()

清除给定范围消息中的指定标志：

```php
function clearMsgFlag($msg_set, $flags)
{
    if (!imap_clearflag_full($this->stream, $msg_set,
    $flags, ST_UID)) {
        $this->buildErrorMsg($this->ERR_STR_CANT_UNSET_FLAGS,
        imap_last_error());
        return false;
    }
    return true;
}
```

就这么多。你终于拥有了一个可以处理 POP3、IMAP 和 NNTP 的健壮 Webmail 类。

下一节将演示如何使用此类来构建基于 Web 的电子邮件系统。

## Web-Based E-Mail System

面向对象编程的两大优点是可扩展性和继承性。在我们为其展示了一些测试脚本时，你已经看到了扩展 Webmail 类的一种方法。我们要构建的基于 Web 的电子邮件系统并不比编写那些脚本更困难。

首先，我们应该扩展 Webmail 类并覆盖其 start() 方法。我们将通过在之前的 Webmail 类中包含以下代码片段来构建最终的 Webmail 类：

```php
// webmail.php

include("./webmail_class_final.php");
class My_Webmail extends Webmail
{

```

### Properties

这个基于 Web 的电子邮件应用程序可以使用 mail() 或远程 SMTP 服务器发送电子邮件。我们定义了一些属性，包含提供这些功能的类的名称：

```php
var $sendmail_class = 'my_mime_mail';
var $smtp_class = 'my_smtp_mime_mail';
```

新闻文章是使用我们在上一章中构建的 NNTP 类发布的：

```php
var $nntp_class = 'my_nntp';
```

用户可以指定他们要连接的 SMTP 服务器的主机名和端口号：

```php
var $smtp_host = '';
var $smtp_port = 24;
```

将用于存储外发电子邮件副本的邮箱名称：

```php
var $sent_mailbox = '';
```

请注意，应将此属性设置为现有邮箱。

每页显示的电子邮件消息或新闻文章数量：

```php
var $msg_per_page = 10;
```

应用程序动态创建的网页的默认标题和字符集：

```php
var $HTML_TITLE = 'Welcome to My Webmail!';
var $CHARSET = 'EUC-KR';
```

几条自定义消息：

```php
var $STR_NO_MESSAGE = 'No message.';
var $ERR_STR_NO_UIDS = 'No message selected!';
```

## start()

应该覆盖 start() 方法。$action 参数中的值选择要运行的方法。该方法在成功时返回 true，在出错时返回 false：

```php
function start($action)
{
    switch($action) {
    case 'readMsg':
        $msg = $this->readMsg();
        if (!$msg) return 0;
        return $this->interface('', $msg);
        break;

    case 'downloadAttachment':
        if (!$this->downloadAttachment()) return false;
        break;

    case 'createMailbox':
        if (!$this->createMailbox()) return false;
        return $this->interface('', '');
        break;

    case 'renameMailbox':
        if (!$this->renameMailbox()) return false;
        return $this->interface('', '');
        break;

    case 'deleteMailbox':
        if (!$this->deleteMailbox()) return false;
        return $this->interface('', '');
        break;

    case 'copyMsg':
        if (!$this->copyMsg()) return false;
        return $this->interface('', '');
        break;

    case 'moveMsg':
        if (!$this->moveMsg()) return false;
        return $this->interface('', '');
        break;

    case 'deleteMsg':
        if (!$this->deleteMsg()) return false;
        return $this->interface('', '');
        break;

    case 'mailForm':
        return $this->interface('', $this->mailForm());
        break;
    case 'mail':
        return $this->sendWebmail();
        break;
    default:
        return $this->interface('');
        break;
    }
    return true;
}
```

## interface()

interface() 方法为应用程序设置主界面，绘制一个两列表格：左侧列出可用邮箱，右侧包含消息列表，如下图所示：

![](img/9cf7789dba9b16ef3f8576d5aea89186_452_0.png)

interface() 方法接受两个参数，分别放入表格的左列或右列。由于此类中定义的大多数方法返回一系列 HTML 字符串，因此它们的返回值可以直接作为参数传递给 interface() 方法：

```php
function interface($first_col, $second_col='')
{
    $mailboxes = $this->listMailbox();

    if (!$mailboxes) return false;

    $first_col = $mailboxes . $this->createMailboxForm() .
        $this->menu() . $first_col;

    if (empty($second_col)) {
        $msgs = $this->listMsg();
        if (!$msgs) $msgs = $this->STR_NO_MESSAGE;
        $second_col = $msgs;
    }

    echo($this->htmlHeader($this->HTML_TITLE, $this->CHARSET));

    echo("<table border=\"0\" width=\"100%\" cellspacing=\"0\"
        cellpadding=\"0\">\n");
    echo("<tr>\n");
    echo("<td width=\"30%\" valign=\"TOP\">$first_col</td>\n");
    echo("<td width=\"70%\" valign=\"TOP\">$second_col</td>\n");
    echo("</tr>\n");
    echo("</table>\n");

    echo($this->htmlFooter());

    return true;
}
```

## menu()

menu() 方法显示一个发送电子邮件或发布文章的链接。你可以通过创建新方法并在该方法中添加指向它们的其他链接来提供新功能：

```php
function menu()
{
    if ($this->protocol == 'nntp') {
        $menu_str = $this->buildUrl("action=mailForm&mode=article&
        mailbox=$this->mailbox", '[Post]');
    } else {
        $menu_str = $this->buildUrl('action=mailForm&mode=new',
        '[Send]');
    }

    return $menu_str;
}
```

## mailForm()

我们在上一章中已经见过这个方法。不过，它已得到很大改进，可以根据用户选择的 $mode 显示不同的表单：

```php
function mailForm()
{
    global $PHP_SELF, $mode, $email;

    $is_news = false;
```

如果用户正在回复电子邮件，则删除原始消息并相应地设置标头值：

```php
if ($mode == 'reply') {
    $msg = $this->getMsg('', '');
    if (!$msg) $mail_to = $email;
    else {
        $mail_date = $msg["date"];
        $mail_to = $msg["raw_from"];
        $mail_cc = $msg["raw_cc"];
        $mail_subject = "Re: " . $msg["subject"];
        $mail_body = "--- Original Message($mail_date) ---\r\n" .
            eregi_replace("<br>", "\r\n", $msg["body"]);
    }
}
```

用户想要转发当前电子邮件。保留 From 标头，并在 Subject 标头前加上字符串 "Fwd:"：

```php
} else if ($mode == 'forward') {
    $msg = $this->getMsg('', '');
    if (!$msg) return false;
    $mail_from = $msg["raw_from"];
    $mail_date = $msg["date"];
    $mail_subject = "Fwd: " . $msg["subject"];
    $mail_reply_to = $mail_from;
    $mail_body = "--- Original Message($mail_date) ---\r\n" .
        eregi_replace("<br>", "\r\n", $msg["body"]);
}
```

用户想要发布新闻文章，打开 $is_news 标志：

```php
} else if ($mode == 'article') {
    $mail_to = $this->mailbox;
    $is_news = true;
}
```

如果用户回复新闻文章，我们还需要设置 References 标头。获取原始 References 标头值并添加当前文章的 Message-ID 标头：

```php
} else if ($mode == 'followup') {
    $mail_to = $this->mailbox;
    $msg = $this->getMsg('', '');
    $mail_references = $msg["references"] . " "
        . $msg["message_id"];
    $mail_subject = "Re: " . $msg["subject"];
    $is_news = true;
}
```

```php
$ret_str = "<form name=\"MAIL_FORM\" action=\"$PHP_SELF\"
method=\"POST\" enctype=\"MULTIPART/FORM-DATA\">\n";
$ret_str .= "<input type=\"HIDDEN\" value=\"mail\"
name=\"action\">\n";
$ret_str .= "<input type=\"HIDDEN\" value=\"$mode\"
name=\"mode\">\n";
```

