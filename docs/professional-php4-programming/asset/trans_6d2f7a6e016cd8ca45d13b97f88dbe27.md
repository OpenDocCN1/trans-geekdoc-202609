
最近的消息应该出现在列表顶部。按 SORTDATE 排序时反转顺序：

```php
if ($this->sort == 'SORTDATE') $this->reverse = (integer) !$this->reverse;
```

上面的 if 语句中的转换可能看起来多余，但有必要防止 $reverse 全局变量具有 null 值。

使用 IMAP，我们可以批量操作消息：

```php
if ($this->protocol == 'imap') {
$ret_str = "<form method=\"POST\" action=\"$PHP_SELF>\n";
$ret_str .= "<input type=\"HIDDEN\" name=\"mailbox\"
value=\"$this->mailbox>\n";
}
else $ret_str = '';
```

绘制表头单元格。单击表头单元格标题将按所选排序顺序对列表进行排序：

```php
$ret_str .= $this->msgTableHeader();
$t_str = $this->msgTableRow(10,'NO',1,"#CECECE");
$t_str .= $this->msgTableRow(50,$this->buildUrl("action=listMsg&mailbox=$this->mailbox&sort=SORTSUBJECT&reverse=$order", "SUBJECT"),1,"#CECECE");
$t_str .= $this->msgTableRow(20,$this->buildUrl("action=listMsg&mailbox=$this->mailbox&sort=SORTFROM&reverse=$order", "FROM"),1,"#CECECE");
$t_str .= $this->msgTableRow(20,$this->buildUrl("action=listMsg&mailbox=$this->mailbox&sort=SORTDATE&reverse=$this->reverse", "DATE"),1,"#CECECE");
$ret_str .= "<tr>\n$t_str</tr>\n";
```

调用 getMsgList() 方法获取消息列表：

```php
$msgs = $this->getMsgList('action=readMsg', 'action=mailForm&mode=reply');
if (!$msgs) return 0;
$num_msg = count($msgs);
```

提供了一系列导航链接，以便用户可以跳转到想要查看的任何页面：

```php
if (!$cur_page) $cur_page = 1;
if (!$num_msg) $num_page = 1;
else $num_page = ceil($num_msg / $this->msg_per_page);
if ($cur_page >= $num_page) $cur_page = $num_page;
```

获取可用邮箱的数量。如果没有邮箱，我们无法移动或复制消息：

```php
$mailboxes = $this->getMailboxList('', 1);
if (!$mailboxes) return false;

$start_num = ($cur_page - 1) * $this->msg_per_page;
$end_num = $cur_page * $this->msg_per_page;

if ($end_num > $num_msg) $end_num = $num_msg;

for ($i = $start_num; $i < $end_num; $i++) {
    $msg_no = $msgs[$i]["no"];
    $msg_uid = $msgs[$i]["uid"];
}
```

$MSG_UIDS 全局变量将把每条选定的消息作为数组元素保存：

```php
if (count($mailboxes) > 0 && $this->protocol == 'imap')
    $checkbox = "<input type=\"CHECKBOX\" name=\"MSG_UIDS[]\" value=\"$msg_uid\">";

$msg_subject = $msgs[$i]["subject"];
$msg_from = $msgs[$i]["from"];
$msg_date = $msgs[$i]["date"];
if ($msgs[$i]["unseen"]) $is_th = 1;
else $is_th = false;
```

在表格行中显示每条消息，将最近的消息设置为粗体：

```php
$t_str = $this->msgTableRow(10, $checkbox . $msg_no, $is_th,
        '#FFFFFF', 'LEFT');
$t_str .= $this->msgTableRow(50, $msg_subject, $is_th,
        '#FFFFFF', 'LEFT');
$t_str .= $this->msgTableRow(20, $msg_from, $is_th,
        '#FFFFFF', 'LEFT');
$t_str .= $this->msgTableRow(20, $msg_date, $is_th,
        '#FFFFFF', 'LEFT');

$ret_str .= "<tr>\n$t_str</tr>\n";

}

$ret_str .= $this->msgTableFooter();
```

仅在可用邮箱超过一个时，用户才能删除、复制或移动选定的消息：

```php
if ((count($mailboxes) > 1) && $this->protocol == 'imap') {
    $ret_str .= "DELETE<input type=\"RADIO\" value=\"deleteMsg\" name=\"action\">/\n";
    $ret_str .= "COPY<input type=\"RADIO\" value=\"copyMsg\" name=\"action\">/\n";
    $ret_str .= "MOVE<input type=\"RADIO\" value=\"moveMsg\" checked name=\"action\">/\n";
    $ret_str .= "TO<select name=\"new_mailbox\" size=\"1\"/>\n";
    foreach ($mailboxes as $mbox)
        if ($mbox != $this->mailbox && !(( $mbox == 'INBOX' ) &&
                (empty($this->mailbox)))) ) {
                $ret_str .= "<option value=\"$mbox\">$mbox</option>\n";
            }
        $ret_str .= "</select>\n";
        $ret_str .= "<input type=\"Submit\" value=\"GO!\">\n";
    }

$ret_str .= "</form>\n";
$ret_str .= "<br>\n";
$ret_str .= "<center>\n";
```

显示导航菜单，将每个页面设为超链接：

```php
for ($i = 1; $i <= $num_page; $i++) {
    if ($cur_page == $i) $ret_str .= "<strong>[$i]</strong>";
    else $ret_str .= $this->buildUrl("action=listMsg&mailbox=$this->mailbox&sort=$this->sort&reverse=$order&cur_page=$i", "[$i]");
}
$ret_str .= "</center>\n";
return $ret_str;
}
```

## listMailbox()

以一系列 HTML 字符串的形式返回邮箱列表：

```php
function listMailbox($mailbox = '')
{
    $str = "";
```

以数组形式获取邮箱列表：

```php
$mailboxes = $this->getMailboxList($mailbox);
if (!$mailboxes) return false;
```

向每个邮箱追加未读消息的数量：

```php
foreach ($mailboxes as $mbox => $unseen) {
    if ($this->protocol != 'nntp' && $this->protocol != 'pop3' && $mbox != 'INBOX') {
```

如果我们不是使用新闻服务器，请提供一个用户可以用来删除邮箱的链接。请注意，我们如何通过使用 JavaScript 的 confirm() 方法防止用户意外删除邮箱：

```php
$del_prefix = $this->buildUrl('action=deleteMailbox&del_mailbox=$mbox', " [X]", "if (!confirm('Are you sure?')) return false;");
} else $del_prefix = '';
```

```php
if ($this->protocol == 'nntp') {
    $str .= $this->buildUrl("action=listMsg&mailbox=$mbox", "$mbox($unseen)") . "<br>\n";
} else {
    $str .= $del_prefix . $this->buildUrl("action=listMailbox&mailbox=$mbox", "$mbox($unseen)") . "<br>\n";
}
    return $str;
}
```

## readMsg()

按照以下截图所示，以用户友好的 HTML 格式格式化并返回选定的消息：

![](img/9cf7789dba9b16ef3f8576d5aea89186_463_0.png)

```php
function readMsg()
{
```

将消息内容读入 $msg 数组变量。getMsg() 方法接受两个 action 参数，用于将附件和电子邮件地址转换为超链接。例如，单击附件后，应用程序将再次被调用，$action 变量设置为 downloadAttachment：

```php
$msg = $this->getMsg('action=downloadAttachment', 'action=mailForm&mode=reply');
if (!$msg) return false;
```

```php
$ret_str = "<strong>Date: </strong>" . $msg["date"] . "<br>\n";
$ret_str .= "<strong>From: </strong>" . $msg["from"] . "<br>\n";
if (!empty($msg["cc"])) $ret_str .= "<strong>Cc: </strong>" .
    $msg["cc"] . "<br>\n";
if (!empty($msg["references"])) $ret_str .= "<strong>References:</strong>" . $msg["references"] . "<br>\n";
$ret_str .= "<strong>Subject: </strong>" .
    $msg["subject"] . "<br>\n";
```

如果用户正在使用 NNTP 服务器，他可以回复当前文章。否则，他可以回复电子邮件或将其转发给其他人：

```php
if ($this->protocol == 'nntp') {
    $ret_str .= $this->buildUrl("action=mailForm&mailbox=$this->mailbox&mode=followup&msg_uid=$this->msg_uid", "[Reply to this article]");
} else {
    $ret_str .= $this->buildUrl("action=mailForm&mailbox=$this->mailbox&mode=forward&msg_uid=$this->msg_uid", "[Forward this message]");
}
$ret_str .= "<br><br>\n";

$ret_str .= "<blockquote>" . $msg["body"] . "</blockquote><br>\n";
```

检查消息是否包含附件：

```php
if ($msg["num_parts"] > 0) {
    $ret_str .= "<center><hr width='90%' size='1'></center>\n";
    for ($i = 0; $i < count($msg["parts"]); $i++) $ret_str .=
        $msg["parts"][$i] . "<br>\n";
}

return $ret_str;
}
```

## htmlHeader() 和 htmlFooter()

最后，有 htmlHeader() 和 htmlFooter() 方法，它们只需输出启动和结束网页所需的一组 HTML 标签。您可以从上一章构建的应用程序中复制粘贴它们：

```php
function htmlHeader($title = '', $charset = '') {

}

function htmlFooter() {

}
```

到目前为止定义的类的以下实例化代码部分现在应该看起来很熟悉：

```php
$host = "localhost";
$protocol = "imap";
$port = 143;
$userid = "wankyu";
$userpassword = "12345";

$wmail = new My_Webmail();
if (!$wmail->init($host, $protocol, $port, $userid, $userpassword))
    echo($wmail->errorMsg());

if (!$wmail->start($action)) echo($wmail->errorMsg());

$wmail->end();
?>
```

您也可以使用此应用程序连接到新闻服务器。更改设置并尝试 news.php.net。以下截图显示了连接到服务器并选择 php.test 新闻组时的外观。

> 大多数新闻服务器返回成千上万个可用的新闻组。如果您打算将此应用程序与其中一台新闻服务器一起使用，列出所有新闻组可能需要很长时间，或者应用程序在等待服务器响应时会超时。该应用程序设计为与 news.php.net 等小型新闻服务器一起工作。

![](img/9cf7789dba9b16ef3f8576d5aea89186_465_0.png)
