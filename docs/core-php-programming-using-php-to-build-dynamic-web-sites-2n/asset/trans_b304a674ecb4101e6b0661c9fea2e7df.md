

```php
print($headers[$index]) . "<BR>\n";
imap_close($mailbox);
?>
```

# string imap_last_error()

使用 imap_last_error 获取由 IMAP 函数生成的最后一个错误。

# imap_list

imap_list 函数是 imap_listmailbox 的别名。

# imap_list_full

imap_list_full 函数是 imap_getmailboxes 的别名。

# array imap_listmailbox(integer stream)

使用 imap_listmailbox 获取数组中每个邮箱箱的名称。

```php
<?php
$mailbox=imap_open("{mail.server.com}INBOX",
"leon","password");
$mailboxes = imap_listmailbox($mailbox);
for($index = 0; $index < count($mailboxes);
$index++) {
	print($mailboxes[$index]) . "<BR>\n";
}
imap_close($mailbox);
?>
```

# imap_listscan

imap_listscan 函数是 imap_scanmailbox 的别名。

# integer imap_mail(string to, string subject, string message, string headers, string cc, string bcc, string rpath)

# PHP 核心编程 (Core PHP Programming)

imap_mail 函数是 mail 函数的替代方案。区别在于特定标头的参数。

# string imap_mail_compose(array envelope, array body)

imap_mail_compose 函数根据描述信封和正文的数组返回 MIME 消息。信封（envelope）参数可能包含以下元素：bcc, cc, date, from, message_id, reply_to, return_path, to。正文（body）参数可能包含以下元素：bytes, contents.data, encoding, id, md5, subtype, type。

# boolean imap_mail_copy(integer stream, string list, string mailbox, integer flags)

imap_mail_copy 函数将消息复制到另一个邮箱箱。消息列表可以是消息列表或范围。可选的 flags 参数是一个位字段，可以使用 CP_UID 设置，表示指定列表包含 UIDs；或者使用 CP_MOVE，它指示函数在复制后删除原始消息。后一种功能可以通过 imap_mail_move 函数实现。

```php
<?php
$mailbox = imap_open("{mail.server.com}INBOX", "leon", "password");
imap_mail_copy($mailbox, "OLD", "17");
imap_close($mailbox);
?>
```

# boolean imap_mail_move(integer stream, string list, string mailbox)

imap_mail_move 函数将消息从当前邮箱箱移动到新邮箱箱。消息列表可以是消息列表或范围。

```php
<?php
$mailbox = imap_open("{mail.server.com}INBOX", "leon", "password");
imap_mail_move($mailbox, "OLD", "17");
imap_close($mailbox);
?>
```

# object imap_mailboxmsginfo(integer stream)

使用 imap_mailboxmsginfo 返回有关当前邮箱箱的信息。该对象将具有表 14.7 列出的属性。

```php
<?php
$mailbox = imap_open("mail.server.com", "INBOX", "leon", "password");
$info = imap_mailboxmsginfo($mailbox);
print("Driver: " . $info->Driver);
imap_close($mailbox);
?>
```

# integer imap_msgno(integer stream, integer uid)

imap_msgno 函数根据 UID 返回消息编号。要根据消息编号获取 UID，请使用 imap_uid。

| 表 14.7. imap_mailboxmsginfo 的属性 | |
| :--- | :--- |
| Date | |
| Driver | |
| Mailbox | |
| Nmsgs | |
| Recent | |
| Size | |
| Unread | |

# integer imap_num_msg(integer stream)

imap_num_msg 函数返回当前邮箱箱中的消息数量。

```php
<?php
$mailbox = imap_open("mail.server.com", "INBOX", "leon", "password");
print("Number of Messages: " . imap_num_recent($mailbox));
imap_close($mailbox);
?>
```

# integer imap_num_recent(integer stream)

# PHP 核心编程 (Core PHP Programming)

imap_num_recent 函数返回当前邮箱箱中最新消息的数量。

```php
<?php
$mailbox = imap_open("{mail.server.com}INBOX",
"leon", "password");
print("Number of Messages: " . 
imap_num_msg($mailbox));
imap_close($mailbox);
?>
```

# integer imap_open(string mailbox, string username, string password, integer flags)

使用 imap_open 开始连接。邮箱箱通常用大括号括起。添加 /pop 会导致 imap_open 连接 POP 服务器而不是 IMAP 服务器。可选的 flags 参数是一个位字段，使用表 14.8 中列出的常量。

| 表 14.8. imap_open 使用的常量 | 描述 |
| :--- | :--- |
| ANONYMOUS | 不使用 |
| DEBUG | 调试 |
| EXPUN | 彻底删除 |
| HALFOPEN | 打开但不删除 |
| PROTOTYPE | 返回原型 |
| READONLY | 以只读打开 |
| SECURE | 使用安全 |
| SHORT | 使用短连接 |
| SILENT | 静默 |

```php
<?php
$mail_ = array("INBOX", "leon", "password");

// 连接到 POP 服务器而不是 IMAP 服务器
imap_open($mail_[0] . "/pop", $mail_[1], $mail_[2]);
?>
```

# boolean imap_ping(integer stream)

imap_ping 函数检查流是否存活。如果连接断开，则重新打开。

```php
<?php
$mailbox = imap_open("mail.server.com", "leon", "password");

// 如果连接断开，则重新打开
if(!imap_ping($mailbox)) {
    // 错误处理
}
?>
```

# integer imap_popen(integer stream)

imap_popen 函数打开连接。邮箱箱通常用大括号括起。

```php
<?php
imap_open("{mail.server.com}INBOX", "leon", "password");
?>
```

# string imap_mail_compose(array envelope, array body)

imap_mail_compose 函数根据描述信封和正文的数组返回 MIME 消息。信封（envelope）参数可能包含以下元素：bcc, cc, date, from, message_id, reply_to, return_path, to。正文（body）参数可能包含以下元素：bytes, contents.data, encoding, id, md5, subtype, type。

# string imap_qprint(string text)

imap_qprint 函数将字符串转换为打印字符串。

```php
<?php
  $string = "Hello World";
  $converted = imap_qprint($string);
?>
```

# string imap_rename(integer stream, string old_name, string new_name)

imap_rename 函数更改邮箱箱的名称。

```php
<?php
$mailbox = imap_open("{mail.server.com}INBOX", "leon", "password");
imap_rename($mailbox, "OLD", "NEW");
?>
```

# boolean imap_reopen(integer stream, string username, string password, integer flags)

imap_reopen 函数打开连接。操作与 imap_open 相同。

```php
<?php
$mailbox = imap_open("{mail.server.com}INBOX", "leon", "password");

// 如果连接断开，则重新打开
if(!imap_ping($mailbox)) {
    imap_reopen($mailbox, "leon", "password");
}
?>
```

# array imap_rfc822_parse_adrlist(string address, string host)

imap_rfc822_parse_adrlist 函数根据默认主机和对象数组解析邮箱地址。每个对象具有属性：mailbox, host, personal, adl。

```php
<?php
  $address = "Leon Atkinson <leon@clearink.com>, vicky";
  $info = imap_rfc822_parse_adrlist($address, "clearink.com");
  while(list($adr_info) = each($info))
    {
      print("$adr_info->personal ");
      print("$adr_info->mailbox ");
      print("$adr_info->host ");
      print("$adr_info->adl<BR>\n");
    }
?>
```

# string imap_rfc822_write_address(string mailbox, string host, string personal_info)

imap_rfc822_write_address 函数返回邮箱地址。正如其名所示，该函数根据 RFC 822 实现地址。

```php
<?php
  print(imap_rfc822_write_address("leon", "clearink.com", "Leon Atkinson"));
?>
```

# string imap_scan

你可以将 imap_scan 作为 imap_scanmailbox, string fragment 的别名

# array imap_scanmailbox(integer stream, string fragment)

imap_scanmailbox 返回包含给定片段的邮箱箱名称数组。

