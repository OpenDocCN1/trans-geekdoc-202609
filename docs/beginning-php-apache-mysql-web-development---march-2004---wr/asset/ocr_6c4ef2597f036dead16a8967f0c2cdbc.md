# Chapter 15

```
}
redirect('index.php');
break;
case 'Modify Account':
if (isset($_POST['name'])
  and isset($_POST['email'])
  and isset($_POST['accesslvl'])
  and isset($_POST['userid']))
(
  $sql = "UPDATE forum_users \
    SET email=\'" . $_POST['email'] . \', \
    name=\'" . $_POST['name'] . \', \
    accesslvl=\'" . $_POST['accesslvl'] . \', \
    signature=\'" . $_POST['signature'] . \', \
    WHERE id=\'" . $_POST['userid'] . \'";
  mysql_query($sql, $conn)
  or die('Could not update user account...<br>SQL: ' . $sql);
}
irect('admin.php');
break;
case 'Edit Account':
if (isset($_POST['name'])
  and isset($_POST['email'])
  and isset($_POST['accesslvl'])
  and isset($_POST['userid']))
(
  $chg_pw=FALSE;
if (isset($_POST['oldpassword'])
  and $_POST['oldpassword'] != '')
{
    $sql = "SELECT oldpassword FROM forum_users \
      WHERE id=\'" . $_POST['userid'] . \'";
    $result = mysql_query($sql) or die(mysql_error());
    if ($row = mysql_fetch_array($result)) {
      if (($row[0]['oldpasswd'] == $_POST['oldpasswd']
        and (isset($_POST['password']))
        and ($row[0]['oldpasswd2'] == $_POST['password2'])) {
          $chg_pw = TRUE;
        }
    }
else
irect('useraccount.php?error=nopassetted');
  break;
    }
}
$sql = "UPDATE forum_users \
  SET email=\'*" . $_POST['email'] . \'";
```

538