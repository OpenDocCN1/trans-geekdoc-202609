
name="mode">\n";
$ret_str .= "<input type="HIDDEN" value="$this->msg_uid"
name="msg_uid">\n";
$ret_str .= "<div align="CENTER">"><table cellspacing="2"
cellpadding="5" width="90%" border="1">\n";

如果 $is_news 标志未启用，请让用户选择使用 SMTP 服务器或内置 mail() 函数来发送电子邮件：

```
if (!$is_news) {
	$ret_str .= "<tr>\n";
	$ret_str .= "<th width=\"100\" colspan=\"2\"><input
	type="CHECKBOX" name="use_smtp" value="ON">
	USE SMTP</th>\n";
	$ret_str .= "</tr>\n";
	$ret_str .= " <tr>\n";
	$ret_str .= "<th width=\"30%\">SMTP HOST</th>\n";
	$ret_str .= "<td width=\"70%\"><input type="TEXT"
	name="smtp_host" size=\"20\"></td>\n";
	$ret_str .= "</tr>\n";
	$ret_str .= " <tr>\n";
	$ret_str .= "<th width=\"30%\">SMTP PORT</th>\n";
	$ret_str .= "<td width=\"70%\"><input type="TEXT"
	name="smtp_port" size=\"5\" value=\"25\"></td>\n";
	$ret_str .= "</tr>\n";
	$ret_str .= " <tr>\n";
	$ret_str .= "<th width=\"30%\">TO</th>\n";
	$ret_str .= "<td width=\"70%\"><input type="TEXT"
	name="mail_to" value="$mail_to" size=\"20\"></td>\n";
	$ret_str .= "</tr>\n";
	$ret_str .= " <tr>\n";
	$ret_str .= "<th width=\"30%\">CC</th>\n";
	$ret_str .= "<td width=\"70%\"><input type="TEXT"
	name="mail_cc" value="$mail_cc" size=\"20\"></td>\n";
	$ret_str .= "</tr>\n";
	$ret_str .= " <tr>\n";
	$ret_str .= "<th width=\"30%\">BCC</th>\n";
	$ret_str .= "<td width=\"70%\"><input type="TEXT"
	name="mail_bcc" size=\"20\"></td>\n";
	$ret_str .= "</tr>\n";
}
```

NNTP 主机信息已知，用户只需输入要发布文章的新闻组：

```
} else {
	$ret_str .= "<tr>\n";
	$ret_str .= "<th width=\"30%\">Newsgroups</th>\n";
	$ret_str .= "<td width=\"70%\"><input type="TEXT"
	name="mail_to" value="$mail_to" size=\"20\"></td>\n";
	$ret_str .= "</tr>\n";
}
```

## 是否设置了 References 头？

```
if (!empty($mail_references)) {
    $ret_str .= "<tr>\n";
    $ret_str .= "<th width=\"30%\">References</th>\n";
    $ret_str .= "<td width=\"70%\"><input
            type=\"HIDDEN\" name=\"mail_references\"
            value=\"$mail_references\" size=\"20\"></td>\n";
    $ret_str .= "</tr>\n";
}
```

该方法的其余部分非常直接。与之前的版本相比未做任何更改：

```
$ret_str .= "<tr>\n";
$ret_str .= "<th width=\"30%\">FROM</th>\n";
$ret_str .= "<td width=\"70%\"><input name=\"mail_from\"\
            size=\"20\"></td>\n";
$ret_str .= "</tr>\n";
$ret_str .= "<tr>\n";
$ret_str .= "<th width=\"30%\">REPLY-TO</th>\n";
$ret_str .= "<td width=\"70%\"><input name=\"mail_reply_to\"\
            value=\"$mail_reply_to\" size=\"20\"></td>\n";
$ret_str .= "</tr>\n";
$ret_str .= "<tr>\n";
$ret_str .= "<th width=\"30%\">ATTACHMENT</th>\n";
$ret_str .= "<td width=\"70%\"><input type=\"FILE\"\
            name=\"userfile\"></td>\n";
$ret_str .= "</tr>\n";
$ret_str .= "<tr>\n";
$ret_str .= "<th width=\"30%\">TYPE</th>\n";
$ret_str .= "<td width=\"70%\"><input type=\"RADIO\" checked\
            value=\"text\" name=\"mail_type\">TEXT\n";
$ret_str .= "<input type=\"RADIO\" value=\"html\"\
            name=\"mail_type\">HTML\n";
$ret_str .= "</td>\n";
$ret_str .= "</tr>\n";
$ret_str .= "<tr>\n";
$ret_str .= "<th width=\"30%\">ENCODING</th>\n";
$ret_str .= "<td width=\"70%\"><input type=\"RADIO\" value=\"7bit\"\
            name=\"mail_encoding\" checked>7BIT\n";
$ret_str .= "<input type=\"RADIO\" value=\"8bit\"\
            name=\"mail_encoding\">8BIT\n";
$ret_str .= "</td>\n";
$ret_str .= "</tr>\n";
$ret_str .= "<tr>\n";
$ret_str .= "<th width=\"30%\">CHARACTER SET</th>\n";
$ret_str .= "<td width=\"70%\"><input type=\"RADIO\" value=\"us-\
            ascii\" name=\"mail_charset\" checked>US-ASCII\n";
$ret_str .= "<input type=\"RADIO\" value=\"euc-kr\"\
            name=\"mail_charset\">EUC-KR\n";
$ret_str .= "</td>\n";
$ret_str .= "</tr>\n";
$ret_str .= "<tr>\n";
$ret_str .= "<th width=\"30%\">SUBJECT</th>\n";
$ret_str .= "<td width=\"70%\"><input size=\"40\"
name=\"mail_subject\" value=\"$mail_subject\">\n</td>\n";
$ret_str .= "</tr>\n";
$ret_str .= "<tr>\n";
$ret_str .= "<th width=\"30%\">BODY</th>\n";
$ret_str .= "<td width=\"70%\"><textarea name=\"mail_body\"\nrows=\"10\" cols=\"60\">$mail_body</textarea></td>\n";
$ret_str .= "</tr>\n";
$ret_str .= "<tr>\n";
$ret_str .= "<th width=\"30%\" colspan=\"2\"><input type=\"SUBMIT\""
value=\"Send\" name=\"SUBMIT\">\n";
$ret_str .= "<input type=\"RESET\" value=\"Reset\""
name=\"RESET\"></th>\n";
$ret_str .= "</tr>\n";
$ret_str .= "</table>\n";
$ret_str .= "</div>\n";
$ret_str .= "</form>\n";

return $ret_str;
}
```

## sendWebmail()

sendWebmail() 方法可以不使用 NNTP 信息，因为在初始化 Webmail 类时已提供该信息。删除保存 NNTP 信息的全局变量。其余部分与之前的版本几乎相同，只是额外增加了一项功能：将每封发出的电子邮件副本发送到“Sent”邮箱：

```
function sendWebmail()
{
global $is_news, $use_smtp, $smtp_host, $smtp_port;
if (!$my_mail->send()) {
$this->buildErrorMsg($my_mail->errorMsg());
return false;
}

$mail_str = $my_mail->view_msg();
if (!$mail_str) return false;
```

请回顾，appendMail() 方法将给定的电子邮件消息复制到指定邮箱：

```
if (!empty($this->sent_mailbox)) {
if (!$this->appendMail($mail_str, $this->sent_mailbox)) {
return false;
}
}
return true;
}
```

## copyMsg()

该方法将给定的 UID 集合复制到指定邮箱。它是 copyMailMsg() 方法的封装：

```
function copyMsg()
{
    global $MSG_UIDS;
    if (!is_array($MSG_UIDS)) {
        $this->buildErrorMsg($this->ERR_STR_NO_UIDS);
        return false;
    }
    if (!$this->copyMailMsg(implode(",", $MSG_UIDS))) return false;
    return true;
}
```

## moveMsg()

该方法将给定的 UID 集合移动到指定邮箱。它是 moveMailMsg() 方法的封装：

```
function moveMsg()
{
    global $MSG_UIDS;
    if (!is_array($MSG_UIDS)) {
        $this->buildErrorMsg($this->ERR_STR_NO_UIDS);
        return false;
    }
    if (!$this->moveMailMsg(implode(",", $MSG_UIDS))) return 0;
    return true;
}
```

## deleteMsg()

该方法从当前邮箱中彻底删除给定的 UID 集合。它是 deleteMailMsg() 方法的封装。请注意，该方法实际会清除指定的消息。我们可以改进此方法的功能，在删除消息之前先将其移动到“Deleted”邮箱。使用 appendMail() 方法向此方法添加该功能并不麻烦：

```
function deleteMsg()
{
    global $MSG_UIDS;
    if (!is_array($MSG_UIDS)) {
        $this->buildErrorMsg($this->ERR_STR_NO_UIDS);
        return true;
    }
    if (!$this->deleteMailMsg(implode(",", $MSG_UIDS))) return 0;
    return true;
}
```

## createMailboxForm()

该方法返回一个表单，用户可通过该表单创建新邮箱。该表单显示在网页左侧邮箱列表的正下方，如第一张截图所示：

```
function createMailboxForm()
{
    global $PHP_SELF;

    if ($this->protocol != 'imap') return;
    $ret_str = "<form method=\"POST\" action=\"$PHP_SELF\">\n";
    $ret_str .= "<input type=\"HIDDEN\" name=\"action\"\n"
                value=\"createMailbox\">\n";
    $ret_str .= "<input type=\"TEXT\" name=\"new_mailbox\"\n"
                size=\"10\"><br>\n";
    $ret_str .= "<input type=\"SUBMIT\" value=\"Create\"\n"
                name=\"SUBMIT\">\n";
    $ret_str .= "</form>\n";
    return $ret_str;
}
```

## msgTableHeader(), msgTableRow(), and msgTableFooter()

用于绘制消息列表表格的简单实用方法：

```
function msgTableHeader()
{
    return "<table border=\"\\1\" width=\"90%\" cellpadding=\"\\2\"\n"
                cellspacing=\"\\1\">\n";
}

function msgTableRow($width, $cell_data, $is_th=0,
            $bg_color='#FFFFFF', $align='CENTER', $valign='TOP')
{
```

将 $is_th 参数设置为 true 以以粗体字体显示最近或未读消息：

```
if (!$is_th) $row_tag = 'td';
        else $row_tag = 'th';

    return "<$row_tag width=\"$width\" align=\"$align\"\n"
                valign=\"$valign\" bgcolor=\"$bg_color\"\n"
                nowrap>$cell_data</$row_tag>\n";
}

function msgTableFooter()
{
    return "</table>\n";
}
```

## listMsg()

该方法以表格形式返回消息列表：

```
function listMsg()
{
    global $PHP_SELF, $cur_page;
    $order = $this->reverse;
```
