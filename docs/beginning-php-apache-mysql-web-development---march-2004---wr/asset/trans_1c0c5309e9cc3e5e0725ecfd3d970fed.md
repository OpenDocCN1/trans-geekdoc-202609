

# 邮件列表

```php
case 'Add New Mailing List':
$sql = 'INSERT INTO ml_lists (listname) VALUES (' .
$_POST['listname'] . '.*');
nmql_query($sql)
or die('Could not add mailing list. ' . mysql_error());
break;
```

```php
case 'Delete Mailing List':
mysql_query('DELETE FROM ml_lists WHERE ml_id=' . $_POST['ml_id'])
or die('Could not delete mailing list. ' . mysql_error());
```

如果有人订阅了该邮件列表，你必须删除这些订阅：

```php
$sql = 'DELETE FROM ml_subscriptions WHERE ml_id=' .
$_POST['ml_id'];
mysql_query($sql)
or die('Could not delete mailing list subscriptions. ' .
mysql_error());
```

当你发送消息时，你希望让用户知道你指的是哪一个邮件列表。如果邮件列表 ID (ml_id) 是 "all" 而不是数字，你希望将其引用为：

```php
case 'Send Message':
if (isset($_POST['msg']) && isset($_POST['ml_id']))
{
	if (is_numeric($_POST['ml_id'])) {
	$sql = 'SELECT listname FROM ml_lists WHERE ml_id=' .
	$_POST['ml_id'] . ' *';
	$result = mysql_query($sql, $conn)
	or die(mysql_error());
	$row = mysql_fetch_array($result);
	$listname = $row['listname'];
	} else
	$listname = 'Master';
}
```

接下来是你迄为止编写的更复杂的 SQL 语句，但并不困难。这里发生的情况的情况是你正在从 `ml_users` 表中获取电子邮件、名称和用户 ID，其中邮件列表 ID (ml_id) 与它们在 `ml_subscriptions` 表中的用户 ID 匹配。这是通过使用 `INNER JOIN` 命令实现的，因为我们正在等待订阅确认，所以只选择 `pending = 0` 或 `false` 的记录。如果 `pending = 1` (true)，则会被忽略。

```sql
$sql = 'SELECT DISTINCT user.e-mail, user.username, user.user_id '
'FROM ml_users user * '
'INNER JOIN ml_subscriptions mls * '
'ON user.user_id = mls.user_id '
'WHERE mls.pending=0';
```

# 第 13 章

如果管理员没有在选择列表中选择 "all"，你必须将选择限制在订阅了邮件列表管理员的特定用户。你通过添加 `AND` 条件来实现这一点：

```php
if (\$_POST['ml_id'] != 'all')
{
  $sql = " AND mls.ml_id=" . $_POST['ml_id'];
}
```

现在执行 SQL 语句并返回结果：

```php
$result = mysql_query($sql) or die('Could not get list of e-mail addresses. ' . mysql_error());
```

你可能在第 10 章记得过。这就是你为电子邮件设置 `From:` Header的方法。它非常自而易见：

```php
$headers = "From: " . ADMIN_E_MAIL . "\r\n";
```

这段精妙的工作不过是构建自定义消息的方法，取决于管理员是将电子邮件发送给所有邮件列表，还是发送给特定的一个：

```php
while ($row = mysql_fetch_array($result))
{
  if (is_numeric($_POST['ml_id'])) {
    $ft = "You are receiving this message as a member of the ";
    $ft .= \$firstname . "\n mailing list. If you have received,";
    $ft .= "this e-mail in error, or would like to remove you";
    $ft .= "name from this mailing list, please visit the\n";
    $ft .= "following URL:\n";
    $ft .= "http://" . \$_SERVER['PHP_HOST'] . "\n"
    dirname(\$_SERVER['PHP_SELF']) . "/remove.php?u=";
    \$row['user_id'] = \$_POST['ml_id'];
  } else {
    $ft = "You are receiving this e-mail because you subscribed:\n";
    $ft .= "to one or more mailing lists. Visit the following:\n";
    $ft .= "URL to change your subscriptions:\n";
    $ft .= "http://" . \$_SERVER['PHP_HOST'] . "\n"
    dirname(\$_SERVER['PHP_SELF']) . "/user.php?u=";
  }
}
```

在将消息发送到邮件列表 (1) 函数之前，将 `quickmail.php` 表单中的消息封装在一些免责文本中：

```php
$msg = stripslashes($_POST['msg']) . "\n\n";
$msg .= "--------------------------------------\n";
$msg .= \$ft;

mail($row['e-mail'],
     stripslashes($_POST['subject']),
     \$msg, \$headers) or die('Could not send e-mail.');
```

# 邮件列表

它就开始运行了，在你回到 `while` 循环的顶部并对下一个用户再次执行之前。注意你正在遍历拥有的每一个电子邮件地址，并使用 `mail()` 命令向每个地址发送电子邮件。需要注意的是，页面在发送所有电子邮件之前都不会完成加载。

