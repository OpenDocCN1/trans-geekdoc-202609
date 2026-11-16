

指定远程 NNTP 服务器及其监听的端口号：

```php
var $nntp_host = '';
var $nntp_port = 119;
```

我们还需要一个占位符，用于存放文章应发布到的新闻组。多个新闻组之间用逗号分隔：

```php
var $newsgroups = '';
```

References 头部占位符：

```php
var $references = '';
```

其他自定义错误消息字符串：

```php
var $ERR_NNTP_HOST_NOT_SET = 'NNTP host not set!';
var $ERR_NNTP_CONNECTION_FAILED = 'Failed to connect to the specified NNTP host!';
var $ERR_NNTP_NOT_CONNECTED = 'Establish a connection to an NNTP server first!';

var $ERR_EMPTY_FROM = "Empty From header!";
var $ERR_EMPTY_NEWSGROUPS = "No newsgroup(s) specified!";

var $ERR_GROUP_WITHOUT_ARG = 'GROUP command needs an argument!';
var $ERR_POST_WITHOUT_ARG = 'POST command with empty article content!';

var $ERR_UNKNOWN_RESPONSE_FROM_SERVER = 'Unknown response from the server!';
var $ERR_POSTING_NOT_ALLOWED = "Posting not allowed on this server!";
var $ERR_GROUP_POSTING_NOT_ALLOWED = "Posting not allowed on this newsgroup!";
var $ERR_GROUP_FAILED = 'GROUP command failed!';
var $ERR_NO_SUCH_GROUP = 'No such group!';
var $ERR_POST_FAILED = 'POST command failed!';
var $ERR_QUIT_FAILED = 'QUIT command failed!';
```

## connect()

此方法用于建立与 NNTP 服务器的连接并设置 `$socket` 属性。请注意，您应具有连接到服务器的权限。大多数 NNTP 服务器通过检查 IP 地址来验证访问权限，以判断您是否来自有效域。该方法还会测试指定的新闻服务器是否允许发布。响应代码 201 表示不允许发布，在这种情况下，在将内部错误消息属性相应设置后，它将返回 false：

```php
function connect()
{
    if (empty($this->nntp_host)) {
        $this->ERROR_MSG = $this->ERR_NNTP_HOST_NOT_SET;
        return false;
    }

    $this->socket = fsockopen($this->nntp_host, $this->nntp_port,
        &$err_no, &$err_str);

    if (!$this->socket) {
        if (!$err_no) $err_str = $this->ERR_INIT_SOCKET_ERROR;
        $this->ERROR_MSG = $this->ERR_NNTP_CONNECTION_FAILED .
            " $err_no: $err_str";
        return false;
    }
    if (!$this->getResponse()) {
        $this->ERROR_MSG = $this->ERR_UNKNOWN_RESPONSE_FROM_SERVER .
            ": " . $this->response_msg;
        return false;
    }

    if ($this->response_code == 200) return true;
    else if ($this->response_code == 201) {
        $this->ERROR_MSG = $this->ERR_POSTING_NOT_ALLOWED;
        return false;
    } else {
        $this->ERROR_MSG = $this->ERR_NNTP_CONNECTION_FAILED;
        return false;
    }

    return true;
}
```

## getResponse()

此方法解析返回的服务器响应，并将响应代码和注释字符串分别放入 `$response_code` 和 `$response_msg` 属性中。与其先前版本的唯一区别在于出错时设置的消息：

```php
function getResponse()
{
    if (!$this->socket) {
        $this->ERROR_MSG = $this->ERR_NNTP_NOT_CONNECTED;
        return false;
    }

    $server_response = fgets($this->socket, 1024);
    if (ereg("^([0-9]{3})(.*)$", $server_response, $match)) {
        $this->response_code = $match[1];
        $this->response_msg = $match[2];
        return true;
    }

    $this->response_msg = $server_response;
    return false;
}
```

## talk()

`talk()` 方法与 my_smtp 类中的方法非常相似。唯一的区别在于，当给定操作成功时，它期望接收到的服务器响应代码不同：

```php
function talk($cmd, $arg='')
{
    if (!$this->socket) {
        $this->ERROR_MSG = $this->ERR_NNTP_NOT_CONNECTED;
        return false;
    }

    switch ($cmd) {
```

发布文章不需要 GROUP 命令。它用于验证类中的新闻组名称：

```php
case "GROUP":
    if (empty($arg)) {
        $this->ERROR_MSG = $this->ERR_GROUP_WITHOUT_ARG;
        return false;
    }

    $nntp_cmd = "GROUP $arg\r\n";
    fwrite($this->socket, $nntp_cmd);
    if (!$this->getResponse()) {
        $this->ERROR_MSG = $this->ERR_UNKNOWN_RESPONSE_FROM_SERVER .
            ": " . $this->response_msg;
        return false;
    }

    if ($this->response_code != 211 &&
        $this->response_code != 411) {
        $this->ERROR_MSG = $this->ERR_GROUP_FAILED . " " .
            $this->response_code . " " . $this->response_msg;
        return false;
    }

    if ($this->response_code == 411) {
        $this->ERROR_MSG = $this->ERR_NO_SUCH_GROUP . " " .
            $this->response_code . " " . $this->response_msg . " " .
            $arg;
        return false;
    }

    break;
```

如果指定的新闻组不允许发布，POST 命令将失败。如果文章格式不正确，它也会失败。您需要遵循新闻文章的标准格式。例如，如果缺少必需的头部，POST 命令注定会失败：

```php
case "POST":
    if (empty($arg)) {
        $this->ERROR_MSG = $this->ERR_POST_WITHOUT_ARG;
        return false;
    }

    $nntp_cmd = "POST\r\n";
    fwrite($this->socket, $nntp_cmd);
    if (!$this->getResponse()) {
        $this->ERROR_MSG = $this->ERR_UNKNOWN_RESPONSE_FROM_SERVER .
            ": " . $this->response_msg;
        return false;
    }
    if ($this->response_code != 340 &&
        $this->response_code != 440) {
        $this->ERROR_MSG = $this->ERR_POST_FAILED . " " .
            $this->response_code . " " . $this->response_msg;
        return false;
    }
```

440 代码表示不允许在此新闻组上发布：

```php
if ($this->response_code == 440) {
    $this->ERROR_MSG = $this->ERR_GROUP_POSTING_NOT_ALLOWED .
        " " . $this->response_code . " " . $this->response_msg;
    return false;
}

$nntp_cmd = "$arg\r\n" . "." . "\r\n";
fwrite($this->socket, $nntp_cmd);
if (!$this->getResponse()) {
    $this->ERROR_MSG = $this->ERR_UNKNOWN_RESPONSE_FROM_SERVER .
        ":" . $this->response_msg;
    return false;
}
```

发布成功时返回 240 代码：

```php
if ($this->response_code != 240) {
    $this->ERROR_MSG = $this->ERR_POST_FAILED . " " .
        $this->response_code . " " . $this->response_msg;
    return false;
}

break;

case "QUIT":
    $nntp_cmd = "QUIT\r\n";
    fwrite($this->socket, $nntp_cmd);
    if (!$this->getResponse()) {
        $this->ERROR_MSG = $this->ERR_UNKNOWN_RESPONSE_FROM_SERVER .
            ":" . $this->response_msg;
        return false;
    }
    if ($this->response_code != 205) {
        $this->ERROR_MSG = $this->ERR_QUIT_FAILED . " " .
            $this->response_code . " " . $this->response_msg;
        return false;
    }
    break;

default:
    $this->ERROR_MSG = $this->ERR_COMMAND_UNRECOGNIZED;
    return false;
    break;
}
return true;
}
```

## buildHeaders()

它构建通常的文章头部。请注意 Newsgroups 头部：

```php
function buildHeaders()
{
    if (empty($this->from)) {
        $this->ERROR_MSG = $this->ERR_EMPTY_FROM;
        return false;
    } else if (empty($this->subject)) {
        $this->ERROR_MSG = $this->ERR_EMPTY_SUBJECT;
        return false;
    } else if (empty($this->body)) {
        $this->ERROR_MSG = $this->ERR_EMPTY_BODY;
        return false;
    } else if (empty($this->newsgroups)) {
        $this->ERROR_MSG = $this->ERR_EMPTY_NEWSGROUPS;
        return false;
    }

    $this->headers[] = "From: $this->from";
    if (!empty($this->reply_to)) $this->headers[] = "Reply-To: $this->reply_to";
```

如果当前要发布的文章是对其他文章的回复，则相应地设置 References 头部的值：

```php
if (!empty($this->references)) $this->headers[] = "References: $this->references";
```

Newsgroups 头部不得包含空白字符：

```php
$this->headers[] = "Newsgroups: " . ereg_replace("[ ;]", ".", $this->newsgroups);
$this->headers[] = "Subject: $this->subject";
return true;
}
```

## viewMsg()

新的 viewMsg() 方法现在返回新闻文章的逐字副本：

```php
function viewMsg()
{
    if (count($this->files) > 0) $this->has_attach = true;

    $this->headers = array();
    $this->buildHeaders();
```

请注意，新闻文章没有 To 头部。Newsgroups 和 Subject 头部现在在 buildHeaders() 方法中添加：

