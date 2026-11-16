
$download_action 参数包含用于下载邮件正文部分的链接，而 $mail_action 保存指向邮件撰写表单的链接：

```
if (!$this->msg_uid) {
    $this->buildErrorMsg($this->ERR_STR_MSG_UID_INVALID,
        imap_last_error()));
    return false;
}

$msg_no = imap_msgno($this->stream, $this->msg_uid);
```

获取包含头部块摘要的对象：

```
$headers = @imap_header($this->stream, $msg_no);
if (!$headers) {
    $this->buildErrorMsg($this->ERR_STR_MSG_NO_INVALID,
        imap_last_error()));
    return false;
}
```

格式化 Date 头部的值：

```
$arr["date"] = gmstrftime("%b %d %Y %H:%M:%S", strtotime
    ($headers->date));
```

使电子邮件地址可点击，并在另一个数组元素中保留其原始格式：

```
$arr["raw_from"] = $this->decodeHeader($headers->fromaddress);
$arr["raw_cc"] = $this->decodeHeader($headers->ccaddress);
$arr["from"] = $this->makeAddress($headers->from,
    "mail_action&msg_uid=$this->msg_uid&mailbox=$this->mailbox");
$arr["cc"] = $this->makeAddress($headers->cc,
    "mail_action&msg_uid=$this->msg_uid&mailbox=$this->mailbox");
```

尝试解码 Subject 头部：

```
$arr["subject"] = $this->decodeHeader($headers->subject);
if (empty($arr["subject"])) $arr["subject"] = $this->STR_NO_SUBJECT;
```

对于新闻文章，我们还需要 Message-ID 和 References 头部的值：

```
$arr["message_id"] = $headers->message_id;
$arr["references"] = $headers->references;
```

获取包含消息元数据的对象：

```
$struct = @imap_fetchstructure($this->stream,
    $this->msg_uid, FT_UID);
```

`parts` 数组的第一个元素是消息正文。`$html` 变量是一个标志，指示正文部分是否为 HTML 文本：

```
$arr["num_parts"] = count($struct->parts) - 1;
$html = 0;
```

编码类型 3 表示 base64 编码，而 4 表示 quoted-printable 编码：

```
if ($struct->parts[0]->encoding == 3) {
    $arr["body"] = imap_base64(imap_fetchbody($this->stream,
    $this->msg_uid, 1, FT_UID));
    if (strtolower($struct->parts[0]->subtype) == 'html') $html = 1;
} else if ($struct->parts[0]->encoding == 4) {
    $arr["body"] = imap_qprint(imap_fetchbody($this->stream,
    $this->msg_uid, 1, FT_UID));
    if (strtolower($struct->parts[0]->subtype) == 'html') $html = 1;
} else {
    if ($struct->encoding == 3) {
    $arr["body"] = imap_base64(imap_fetchbody($this->stream,
    $this->msg_uid, 1, FT_UID));
    if (strtolower($struct->subtype) == 'html') $html = 1;
    } else if ($struct->encoding == 4) {
    $arr["body"] = imap_qprint(imap_fetchbody($this->stream,
    $this->msg_uid, 1, FT_UID));
    if (strtolower($struct->subtype) == 'html') $html = 1;
    } else {
    $arr["body"] = imap_fetchbody($this->stream,
    $this->msg_uid, 1, FT_UID);
    if (strtolower($struct->subtype) == 'html') $html = 1;
    }
}
```

如果正文中包含链接，则转换这些链接。如果链接已可点击（消息为 HTML 格式），则跳过该代码块：

```
if (!$html) {
    $arr["body"] = str_replace("\r\n", "<br>", $arr["body"]);
    $arr["body"] = eregi_replace("http://([-a-z0-9\..-]+)", "<a href=\"http://\1\">http://\1</a>", $arr["body"]);
    $arr["body"] = eregi_replace("ftp://([-a-z0-9\..-]+)", "<a href=\"ftp://\1\">ftp://\1</a>", $arr["body"]);
    $arr["body"] = eregi_replace("([-a-z0-9\._]+)@([-a-z0-9\_]+)", "<a href=\"PHP_SELF?$mail_action&email=\1@\2\">\1@\2</a>", $arr["body"]);
}
```

如果存在附件，则为附件添加链接：

```
for ($i = 0; $i < count($struct->parts); $i++) {
```

参数数组包含一个名为 NAME 的属性，用于提取附件文件的名称：

```
foreach ($struct->parts[$i]->parameters as $attr) {
    if (strtolower($attr->attribute) == 'name') {
        $filename = $this->decodeHeader($attr->value);
        break;
    }
}
$arr["parts"][$i] = $this->buildUrl("$download_action&mailbox=$this->mailbox&msg_uid=$this->msg_uid&part_no=$i&filename=$filename", $filename);
}
return $arr;
}
```

### downloadAttachment()

该方法将指定正文部分的内容传递到标准输出，即 Web 浏览器：

```
function downloadAttachment()
{
    $struct = @imap_fetchstructure($this->stream,
    $this->msg_uid, FT_UID);

    if (!$struct) {
        $this->buildErrorMsg($this->ERR_STR_MSG_UID_INVALID .
        $this->msg_uid, imap_last_error());
        return false;
    }
}
```

获取正文部分的主类型：

```
switch ($struct->parts[$this->part_no]->type) {
case 0: $type = 'text';
    break;

case 1: $type = 'multipart';
    break;

case 2: $type = 'message';
    break;

case 3: $type = 'application';
    break;

case 4: $type = 'audio';
    break;
case 5: $type = 'image';
    break;
case 6: $type = 'video';
    break;
default: $type = 'other';
    break;
}
```

如果正文部分包含 GIF 图像，则 type 属性设置为 image，subtype 设置为 gif：

```
$subtype = $struct->parts[$this->part_no]->subtype;
```

调用 header() 函数以输出 HTML 头部：

```
header("Content-Type: $type/$subtype");
```

Content-Disposition 头部会导致浏览器将给定的文件名用作 filename 属性的值：

```
header("Content-Disposition: attachment; filename=$this->filename");
```

![](img/9cf7789dba9b16ef3f8576d5aea89186_436_0.png)

再次检查编码类型：

```
if ($struct->parts[$this->part_no]->encoding == 3) {
    echo (@imap_base64(imap_fetchbody($this->stream, $this->msg_uid,
        $this->part_no + 1, FT_UID)));
} else if ($struct->parts[$this->part_no]->encoding == 4) {
    //QUOTED_PRINTABLE
    echo (@imap_qprint(imap_fetchbody($this->stream, $this->msg_uid,
        $this->part_no + 1, FT_UID)));
} else {
    echo (@imap_fetchbody($this->stream, $this->msg_uid,
        $this->part_no + 1, FT_UID));
}
return true;
}
```

## 测试 Webmail 类

现在，可以使用 Webmail 类读取邮件。以下脚本演示了如何扩展该类并使用新添加的功能：

```
<?php
// webmail_class_test3.php

include("./webmail_class_ver3.php");
class My_Webmail extends Webmail
{
```

首先，需要重写 start() 方法。请注意 $action 参数如何用于从扩展类中选择方法：

```
function start($action)
{

```

switch 语句根据 $action 变量的值从多种不同方法中进行选择：

```
switch($action) {
case 'readMsg':
```

定义利用 Webmail 类中方法的自有方法：

```
$msg = $this->readMsg();
if (!$msg) return false;
echo($msg);
break;
```

某些方法可以直接从扩展类中调用：

```
case 'downloadAttachment':
    if (!$this->downloadAttachment()) return 0;
    break;

default:
    $msgs = $this->getMsgList('action=readMsg', 'action=mailForm');
    if (!$msgs) return false;
    foreach ($msgs as $msg)
        echo($msg["subject"] . " - " . $msg["from"] . "<br>");
    break;
}
}
```

readMsg() 方法调用 Webmail 类中定义的 getMsg() 方法以获取指定的电子邮件：

```
function readMsg()
{

```

需要提供 getMsg() 使用的 action 值，以便在用户单击附件或电子邮件地址时确定应采取的操作：

```
$msg = $this->getMsg('action=downloadAttachment',
    'action=mailForm&mode=reply');

if (!$msg) return false;
$ret_str = "<strong>From: </strong>" . $msg["from"] . "<br>\n";
if (!empty($msg["cc"])) $ret_str .= "<strong>Cc: </strong>" .
    $msg["cc"] . "<br>\n";
$ret_str .= "<strong>Subject: </strong>" . $msg["subject"] .
    "<br>\n";
$ret_str .= "<br><br>\n";

$ret_str .= "<blockquote>" . $msg["body"] . "</blockquote><br>\n";

if ($msg["num_parts"] > 0) {
    $ret_str .= "<center><hr width=\"90%\" size=\"1\"></center>\n";
    for ($i = 0; $i < count($msg["parts"]); $i++) $ret_str .=
        $msg["parts"][$i] . "<br>\n";
}

return $ret_str;
}
```

```
$host = "mail.whatever.com";
$protocol = "imap";
$sport = 143;
$userid = "wankyu";
$userpassword = "12345";

$wmail = new My_Webmail();
```

```
if (!$wmail->init($host, $protocol, $sport, $userid, $userpassword))
    echo($wmail->errorMsg());
```

使用全局 $action 变量调用 start() 函数并检查其返回值：

```
if (!$wmail->start($action)) {
    echo($wmail->errorMsg());
}
$wmail->end();
?>
