

# PHP 核心编程

```php
{
    $header = imap_header($mailbox
```

```php
?>
```

# string imap_clearflag_full(integer stream, string sequence flag, string options)

imap_clearflag_full 函数用于删除消息序列上的标记。`options` 参数如果提供，可以设置为 `ST_UID`，该标志表示 `sequence` 参数包含的是 UIDs 而不是消息号。

```php
<?php
    $mbox = imap_open("{news.server.com/ntp:119", "leon", "password");
    imap_clearflag_full($mbox, "12-15", "U", ST_UID);
    imap_close($mbox);
?>
```

# boolean imap_close(integer stream, integer flags)

使用 `imap_close` 关闭与邮箱的连接。`stream` 参数是由 `imap_open` 返回的整数。`flags` 参数可以设置为 `CL_EXP`，这将导致邮箱在关闭前被清理。

# imap_create

你可以将 `imap_create` 作为 `imap_createmailbox` 的别名。

# boolean imap_createmailbox(integer stream, string mailbox)

使用 `imap_createmailbox` 创建邮箱。

```php
<?php
// 创建一个名为 PHP List 的邮箱
$mailbox = imap_open("{mail.server.com}INBOX", "leon","password");
imap_createmailbox($mailbox, "PHP List");
imap_close($mailbox);
?>
```

# boolean imap_delete(integer stream, integer message)

imap_delete 函数将消息标记为删除。使用 `imap_expunge` 使消息永久删除。

```php
<?php
// 删除编号为 3 的消息
$mailbox = imap_open("{mail.server.com}INBOX", "leon","password");
imap_delete($mailbox, 3);
imap_close($mailbox);
?>
```

# boolean imap_deletemailbox(integer stream, string mailbox)

imap_deletemailbox 函数删除命名的邮箱。

```php
<?php
// 删除一个邮箱
$mailbox = imap_open("{mail.server.com}INBOX", "leon","password");
imap_deletemailbox($mailbox, "PHP List");
imap_close($mailbox);
?>
```

# array imap_errors()

# PHP 核心编程

使用 `imap_errors` 获取由 IMAP 函数生成的所有错误数组，将其从内部堆栈中移除。你可以使用 `imap_last_error` 获取最后一个错误。

# boolean imap_expunge(integer stream)

使用 `imap_expunge` 所有被标记为删除的消息。

```php
<?php
// 清理消息
$mailbox = imap_open("{mail.server.com}INBOX", "leon", "password");
imap_expunge($mailbox);
imap_close($mailbox);
?>
```

# array imap_fetch_overview(integer stream, integer message)

imap_fetch_overview 函数返回一个数组，提供消息头部的概览。该数组包含以下元素：answered, date, deleted, draft, flagged, from, message_id, msgno, recent, references, seen, size, subject, uid。

# string imap_fetchbody(integer stream, integer message, integer part, integer flags)

imap_fetchbody 函数获取消息的特定部分。主体部分采用 base64 编码，必须通过 `imap_base64` 才能作为文本查看。`flags` 参数接受表 14.2 中描述的标记。

```php
<?php
// 获取第一条消息的第一部分
$mailbox = imap_open("{mail.server.com}INBOX", "leon", "password");
$part1 = imap_fetchbody($mailbox, 1, 1);
imap_close($mailbox);
?>
```

# string imap_fetchheader(integer stream, integer message, integer flags)

# PHP 核心编程

使用 `imap_fetchheader` 获取消息完整 RFC 822 头部文本。`flags` 参数是一个接受以下常量字段：FT_UID, FT_INTERNAL, FT_PREFETCHTEXT。`FT_UID` 和 `FT_INTERNAL` 常量的含义与在 `imap_body` 函数中使用时相同。`FT_PREFETCHTEXT` 会导致同时获取消息正文。

```php
<?php
  $mailbox=imap_open("{mail.server.com}INBOX", "leon", "password");
  print(imap_fetchheader($mailbox, 1, FT_PREFETCHTEXT));
  imap_close($mailbox);
?>
```

# object imap_fetchstructure(integer stream, integer message)

imap_fetchstructure 返回一个包含指定消息信息的对象。表 14.4 列出了该对象的属性。

| 表 14.4. imap_fetchstructure 属性 |
| --- | --- |
| 属性 | 数据类型 |
| type | Integer |
| encoding | Integer |
| ifsubtype | Boolean |
| subtype | String |
| ifdescription | Boolean |
| description | String |
| ifid | Boolean |
| id | String |
| lines | Integer |
| bytes | Integer |
| ifdisposition | Boolean |
| disposition | String |
| ifparameters | Boolean |
| dparameters | 对象数组 |
| ifparameters | Boolean |
| parameters | 对象数组 |
| parts | 对象数组 |
| 结构 | 关于指定消息的结构

```php
<?php
// 获取结构
$mailbox = imap_open("{mail.server.com}INBOX", "leon", "password");
$structure = imap_fetchstructure($mailbox, 1);
imap_close($mailbox);
?>
```

# string imap_fetchtext

你可以将 `imap_fetchtext` 作为 `imap_body` 的别名。

# array imap_getmailboxes(integer stream, string reference)

imap_getmailboxes 函数返回邮箱的详细信息。`reference` 参数是 IMAP 服务器格式。`pattern` 参数控制哪些邮箱被返回。返回的数组包含三个属性：name, delimiter, attributes，属性可以与表 14.5 中的常量进行测试。

```php
<?php
$mailbox = imap_open("{mail.server.com}INBOX", "leon", "password");
$boxes = imap_getmailboxes($mailbox, "{mail.server.com}: "*");
imap_close($mailbox);

foreach($boxes as $box) {
    print($box->name . "\n");
}
?>
```

# array imap_subscribed(integer stream, string reference)

# PHP 核心编程

表 14.5 属性中的常量

| 常量 | 描述 |
| --- | --- |
| LATT_NOFERIOR | 邮箱不包含其他邮箱。 |
| LATT_NOSELECT | 邮箱仅为容器，无法打开。 |
| LATT_MARKED | 邮箱已标记。 |
| LATT_UNMARKED | 邮箱未标记。 |

# object image_header(integer stream, integer message, integer flags)

image_header 返回一个包含指定消息信息的对象。表 14.6 列出了该对象的属性。

| 表 14.6. image_header 属性 |
| 属性 | 描述 |
| --- | --- |
| answered | 已回复。 |
| bcc | 对象数组。 |
| deleted | 已删除。 |
| draft | 草稿。 |
| flagged | 已标记。 |
| from | 对象数组。 |
| message_id | 服务器分配的唯一 ID。 |
| msgno | 消息号。 |
| newsgroups | 新组行。 |
| references | 引用行。 |
| size | 消息大小。 |
| subject | 消息的主题。 |
| to | 对象数组。 |
| update | 时间戳 |
| unseen | 如果消息未读。 |

```php
<?php
  $mailbox = imap_open("{mail.server.com}INBOX", "leon", "password");
  $header = imap_header($mailbox, 1);
  print("Subject: " . $header->subject);
  imap_close($mailbox);
?>
```

# imap_headerinfo

imap_headerinfo 函数是 `imap_header` 的别名。

# array imap_headers(integer stream)

imap_headers 函数返回一个字符串数组，每条消息一个元素。每个字符串总结了消息的头部。

```php
<?php
$mailbox = imap_open("{mail.server.com}INBOX", "leon", "password");
$headers = imap_headers($mailbox);
for($index = 0; $index < count($headers); $index++)
{
    print($headers[$index]);
}
imap_close($mailbox);
?>
```

