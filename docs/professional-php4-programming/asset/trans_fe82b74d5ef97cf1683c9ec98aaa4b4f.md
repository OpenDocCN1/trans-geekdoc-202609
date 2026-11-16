

将 $auto_expunge 属性设置为 true 后，调用 imap_close() 函数将清除任何标记为删除的消息：

```
var $auto_expunge = true;
```

我们需要一套全新的自定义消息。请注意，$ERR_ARGS_DELIMITER 属性用于分隔错误消息和随后的参数：

```
var $ERR_ARGS_DELIMITER = " ";
var $ERROR_MSG = '';

var $ERR_STR_CONNECTION_FAILED = 'Connection failed!';
var $ERR_STR_PROTOCOL_NOT_SUPPORTED = 'Protocol not supported!';
var $ERR_STR_CLOSE_FAILED = 'Error closing the stream!';
var $ERR_STR_MAILBOX_NOT_AVAILABLE = 'Mailbox not available!';
var $ERR_STR_OVERRIDE_START = "Override start() method!";
```

### init()

init() 方法通过将给定参数设置为内部属性来初始化类：

```
function init($host, $protocol='imap', $port=143,
	$userid='', $userpassword='')
{
	$this->host = $host;
	$this->protocol = $protocol;
	$this->port = $port;
	$this->userid = $userid;
	$this->userpassword = $userpassword;
}
```

$mailbox 属性的值从全局命名空间中获取：

```
$this->mailbox = $GLOBALS["mailbox"];
```

如果指定的协议不是 $supported_protocols 数组的元素，则被视为无效：

```
if (!in_array($this->protocol, $this->supported_protocols)) {
	$this->buildErrorMsg($this->ERR_STR_PROTOCOL_NOT_SUPPORTED,
		$this->protocol);
	return false;
}
```

如果要使用 NNTP 协议且 mailbox 属性为空，则应通过将 imap_open() 函数的第四个参数设置为 OP_HALFOPEN 来打开一个不选择邮箱的 IMAP 流。但是，如果 $mailbox 属性有值，则将其用作新闻组名称：

```
if ($this->protocol == 'nntp' && empty($this->mailbox)) {
	$mode = OP_HALFOPEN;
} else $mode = false;
```

```
$this->stream = @imap_open("{$this->host}/{$this->protocol}:{$this->port}{$this->mailbox}",
	$this->userid, $this->userpassword, $mode);

if (!$this->stream) {
	$this->buildErrorMsg($this->ERR_STR_CONNECTION_FAILED,
		imap_last_error());
	return false;
}
return true;
}
```

你可能会认为，拥有一个接受打开连接所需参数的构造函数会更简单。然而，构造函数是一种不返回值的特殊方法。如果我们依赖构造函数，将无法判断连接是否成功。

### start() 和 end()

要激活类的实例，我们调用 start() 方法；在使用完实例后，调用 end() 方法：

```
function start()
{
	$this->buildErrorMsg($this->ERR_STR_OVERRIDE_START);
	return false;
}
```

由于 Webmail 类不打算独立工作，start() 方法应由子类重写。它是所有派生类都要实现的接口方法：

end() 方法关闭打开的流：

```
function end()
{
	if ($this->auto_expunge) $ret = @imap_close($this->stream,
		CL_EXPUNGE);
	else $ret = @imap_close($this->stream);

	if (!$ret) {
		$this->buildErrorMsg($this->ERR_STR_CLOSE_FAILED,
			imap_last_error());
		return false;
	}
	return true;
}
```

PHP 不遗余力地确保在脚本终止前关闭所有打开的连接。但是，在基类中提供某种垃圾回收方法始终是良好的实践。

### buildErrorMsg() 和 errorMsg()

buildErrorMsg() 方法仅将 $ERROR_MSG 属性值设置为由 $ERR_ARGS_DELIMITER 分隔的给定参数：

```
function buildErrorMsg($err_msg, $err_arg='')
{
    $this->ERROR_MSG = $err_msg . $this->ERR_ARGS_DELIMITER . $err_arg;
}
```

我们还像往常一样定义了一个错误报告方法：

```
function errorMsg()
{
    return $this->ERROR_MSG;
}
?>
```

## 测试 Webmail 类

尝试使用不同的协议和主机来测试此类：

```
<?php
//webmail_class_test.php
include("../webmail_class_ver1.php");
class My_Webmail extends Webmail
{
    function start() {
        // Does nothing yet
        return true;
    }
}

$host = "mail.whatever.com";
$protocol = "imap";
$port = 143;
$userid = "wankyu";
$userpassword = "12345";

$wmail = new My_Webmail();

if (!$wmail->init($host, $protocol, $port, $userid, $userpassword))
    echo($wmail->errorMsg());
else echo("Connected!");
if (!$wmail->start()) echo($wmail->errorMsg());

$wmail->end();
?>
```

请注意，在本示例脚本中，我们扩展了 Webmail 类并重写了 start() 方法。该脚本除了连接到指定服务器之外，不做太多事情。我们需要向 Webmail 类添加新功能，才能从中获得一些有意义的结果。连接到 IMAP 服务器后，你首先想要做的事情可能是列出所选邮箱中的消息。

## 列出消息或文章

要获取邮箱中的电子邮件消息列表或新闻组中的新闻文章，可以调用 imap_header() 和 imap_fetchstructure() 函数。

### imap_header()

```
object imap_header(int stream, int msg_no [, int fromlength , int subjectlength, string defaulthost])
```

imap_header() 函数返回消息或文章中使用的标头摘要，而 imap_fetchstructure() 则提供其结构的详细报告。你也可以使用其别名 imap_headerinfo() 调用 imap_header()。

该函数返回一个包含给定消息标头块信息的对象，具有以下属性：

| 标头 | 说明 |
|---|---|
| Date | 消息创建日期，或 Date 标头。 |
| Subject | Subject 标头。 |
| message_id | Message-ID 标头。 |
| References | References 标头。 |
| toaddress | To、From 和 Reply-To 标头的副本。 |
| fromaddress | |
| reply_toaddress | |
| to, from, reply_to | 包含标头中每个电子邮件地址作为元素的对象数组。每个元素针对电子邮件地址 "Wankyu Choi <wankyu@whatever.com>" 具有以下属性：personal – 全名，即 "Wankyu Choi"；mailbox – 邮箱名，即 "wankyu"；host – 主机名，即 "whatever.com"。该对象有一个名为 ad1 的附加属性。消息发送者可能希望指示其消息应遵循的传输路径，这称为"源路由"。但是，它很少使用，且该属性通常不包含任何内容。 |
| Recent | 如果最近且已查看，则为 'R'；如果最近且未查看，则为 'N'；如果不最近，则为 ''。 |
| Unseen | 如果未查看且不最近，则为 'U'；如果已查看或未查看且最近，则为 ''。 |
| Answered | 如果已回复，则为 'A'；如果未回复，则为 ''。 |
| Deleted | 如果标记为删除，则为 'D'；如果未标记为删除，则为 ''。 |
| Draft | 如果是草稿，则为 'X'；如果不是草稿，则为 ''。 |
| Flagged | 如果已标记，则为 'F'；如果未标记，则为 ''。 |
| Msgno | 消息序列号。 |
| Size | 消息大小（字节）。 |
| fetchfrom | 按 fromlength 参数格式化的 From 标头值。如果缺少参数且使用此属性，则不返回任何内容。请注意，包含非 ASCII 字符的 From 标头需要使用我们稍后将介绍的 IMAP 函数进行解码。截断标头会破坏编码后的标头值。 |
| fetchsubject | 按 subjectlength 参数格式化的 Subject 标头值。如果缺少参数且使用此属性，则不返回任何内容。使用编码后的 Subject 标头值时，会出现与 fetchfrom 属性相同的问题。 |

请注意，最近的消息也被视为未查看。你需要同时检查 Recent 和 Unseen 标志，以确定消息是否已被阅读。

你可以使用此函数获取消息的元数据，如下所示：

```
$msg = imap_header($stream, 10, 30, 40);

if ($msg->Unseen == 'U' || $msg->Recent == 'R') {
    $flag = "(Unseen)";
} else $flag = "(Seen)";
```

### 格式化 Date 标头以获取其简短版本：

```
$msg_date = gmstrftime("%b %d %Y", strtotime($msg->date));
```

### 使 From 地址可点击：

```
$from_addr = $msg->from[0]->mailbox . "@" . $msg->from[0]->host;
if ($msg->from[0]->personal != '') {
	$from_addr = "From: <a href=\"mailto: $from_addr\">".
		$msg->from[0]->personal . "</a>";
} else {
	$from_addr = "From: <a href=\"mailto: $from_addr\">$from_addr</a> ";
}
```

### 使 Cc 地址可点击：

```
for ($i=0; $i < count($msg->cc); $i++) {
	$cc_addr = $msg->cc[$i]->mailbox . "@" . $msg->cc[$i]->host;
	if ($msg->cc[$i]->personal != '') {
		$ccs[] = "<a href=\"mailto:$cc_addr\">". $msg->cc[$i]->personal . "</a>";
	} else {
		$ccs[] = "<a href=\"mailto: $cc_addr\">$cc_addr</a>";
	}
}
```

### 是否至少有一个 Cc 地址？

```
if (count($ccs) > 0) {
	$cc_adr = "Cc: " . implode(",", $ccs);
}
```

### 将它们输出：

```
echo("Date: $msg_date <br>");
echo("From: $from_addr<br>");
if (count($ccs) > 0) {
	echo("Cc: $cc_adr<br>");
}
echo("Size: $msg->Size bytes<br>");
echo("Subject: $msg->subject<br>");
```

imap_header() 不返回消息的 UID。我们需要 imap_uid() 来获取消息的唯一 ID。

### imap_uid() 和 imap_msgno()

```
int imap_uid(int stream, int msg_no)
int imap_msgno(int stream, int uid)
```

