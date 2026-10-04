# Chapter 13

If the administrator did not choose "all" in the select list, you must limit your selection to the specific users who are subscribed to the mailing list administrator. You do this by tacking on the AND condition:

```
if (\$_POST['ml_id'] != 'all')
{
  $sql = " AND mls.ml_id=" . $_POST['ml_id'];
}
```

Now execute the SQL statement, and return the results:

```
$result = mysql_query($sql) or die(\'Could not get list of e-mail addresses. ' . mysql_error());
```

You may remember that from Chapter 10. This is how you do the From: Header to an e-mail. It is fairly self-explanatory:

```
$headers = "From: " . ADMIN_E_MAIL . "\r\n";
```

The pretty piece of work is nothing than a way to build up a custom message, depending on whether the administrator is sending the e-mail to all mailing lists, or to a specific one:

```
while ($row = mysql_fetch_array($result))
{
  if (is_numeric($_POST['ml_id'])) {
    $ft = "You are receiving this message as a member of the ";
    $ft .= \$firstname . "n mailing list. If you have received,\
    $ft .= "this e-mail in error, or would like to remove you\";
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

Wrap the message of the quickmail.php form inside some disclaimer text before you send it to the mailing list (1) function:

```
$msg = stripslashes($_POST['msg']) . "\n\n";
$msg .= "--------------------------------------\n";
$msg .= \$ft;

mail($row['e-mail'],
     stripslashes($_POST['subject']),
     \$msg, \$$headers) or die(\'Could not send e-mail.\');
```

436