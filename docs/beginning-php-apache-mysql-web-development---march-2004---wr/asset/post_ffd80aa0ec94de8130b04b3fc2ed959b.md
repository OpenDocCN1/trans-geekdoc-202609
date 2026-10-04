
# Chapter 15

534

## Creating a Bulletin Board System

```php
default:
    redirect('index.php');
} else {
    redirect('index.php');
}
```

20. Enter transact-post.php, the second of four transaction pages. This one deals with forum posts.

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_557_0.png)

21. Create transact-user.php, the third of four transaction pages. This one handles related to the users (such as logging in).

```php
<?php
require_once 'conn.php';
require_once 'http.php';

if (isset($_REQUEST['action'])) {
  switch ($_REQUEST['action']) {
    case 'Login':
      if (isset($_POST['email'])
        and isset($_POST['passwd']))
      {
```

536

## Creating a Bulletin Board System

```php
$sql = "SELECT id, access_lvl, last_login *"
FROM forum_users
WHERE email='" . $_POST['email'] . "'";
AND password='" . $_POST['password'] . "'";
$result = mysql_query($sql, $conn)
or die("Could not look up user information: ' . mysql_error($result));
```

```php
if ($row = mysqli_fetch_array($result)) {
    session_start();
    $_SESSION['user_id'] = $row['id'];
    $_SESSION['access_lvl'] = $row['access_lvl'];
    $_SESSION['name'] = $row['name'];
    $_SESSION['last_login'] = $row['last_login'];
    $sql = "UPDATE forum_users SET last_login = '" .
    date("Y-m-d H:i:s", time()) . "'"
    WHERE id='" . $row['id'];
    mysql_query($sql,$conn)
    or die(mysql_error($conn) . "<br>" . $sql);
}
redirect('index.php');
break;
```

```php
case 'Logout':
    session_start();
    session_unset();
    session_destroy();

    redirect('index.php');
break;
```

```php
case 'Create account':
    if (isset($_POST['name'])
    and isset($_POST['email'])
    and isset($_POST['password'])
    and isset($_POST['password2']) == $_POST['password2']) {
```

```php
mysql_query($sql,$conn)
or die("Could not create user account: ' . mysql_error($conn));

session_start();
$_SESSION['user_id'] = mysql_insert_id($conn);
$_SESSION['access_lvl'] = 1;
$_SESSION['name'] = $_POST['name'];
$_SESSION['login_time'] = date("Y-m-d H:i:s", time());
```

## Creating a Bulletin Board System

```php
}
redirect('index.php');
break;
case 'Modify Account':
if (isset($_POST['name'])
  and isset($_POST['email'])
  and isset($_POST['accesslvl'])
  and isset($_POST['userid']))
{
  $sql = "UPDATE forum_users \
    SET email='" . $_POST['email'] . "', \
    name='" . $_POST['name'] . "', \
    accesslvl='" . $_POST['accesslvl'] . "', \
    signature='" . $_POST['signature'] . "', \
    WHERE id='" . $_POST['userid'] . "";
  mysql_query($sql, $conn)
  or die('Could not update user account...<br>SQL: ' . $sql);
}
else
redirect('admin.php');
}
break;
case 'Edit Account':
if (isset($_POST['name'])
  and isset($_POST['email'])
  and isset($_POST['accesslvl'])
  and isset($_POST['userid']))
{
  $chg_pw=FALSE;
  if (isset($_POST['oldpassword'])
  and $_POST['oldpassword'] != '')
  {
    $sql = "SELECT oldpassword FROM forum_users \
      WHERE id='" . $_POST['userid'] . "'";
    $result = mysql_query($sql) or die(mysql_error());
    if ($row = mysql_fetch_array($result)) {
      if (($row[0]['oldpasswd'] == $_POST['oldpasswd']
        and (isset($_POST['password']))
        and ($row[0]['oldpasswd2'] == $_POST['password2'])) {
          $chg_pw = TRUE;
        }
    }
    else
    redirect('useraccount.php?error=nopassetted');
    break;
    }
  }
}
$sql = "UPDATE forum_users \
  SET email='" . $_POST['email'] . "'";
```

538

## Creating a Bulletin Board System

```php
"', name=' . $_POST['name'] .
  ', access_lvl=' . $_POST['accesslvl'] .
  ', signature=' . $_POST['signature'];
if ($chg_pw) {
  $sql = ' password='=$__POST['password'];
  $sql .= ' WHERE id=' . $_POST['userid'] . "'";
  mysql_query($sql,$conn)
  or die('Could not update user account... ' . mysql_error() .
  '<br>SQL: ' . $sql);
}
  redirect('account.php?blah=' . $_POST['userid']);
  break;
case 'Send my reminder':
  if (isset($_POST['email'])) {
    $sql = 'SELECT passwd FROM forum_users 
            WHERE email=' . $_POST['email'] . "'";

    $result = mysql_query($sql,$conn)
    or die('Could not look up password: ' . mysql_error());

    if (mysql_num_rows($result)) {
      $row = mysql_fetch_array($result);
      $subject = 'Comic site password reminder';
      $body = 'Just a reminder, your password for the ' . 
              '\nYou can use this to log in at: "://' . $row['passwd'] . 
              '\nComic Book Appreciation site is: ' . 
              $_SERVER['HTTP_HOST'] . 
              dirname($_SERVER['PHP_SELF']) . '/login.php?e=' . 
              $_POST['email'] . "'";
      $headers = 'From: admin@yite.com\r\n';
      mail($_POST['email'],$subject,$body,$headers)
      or die('Could not send reminder email.');
    }
    redirect('login.php');
  }
  break;
}
```

22. Create transact-affirm "page" that does send data to the client. If a function requires confirmation, the user is sent here and redirected forward.

## Creating a Bulletin Board System

```php
<?php
require_once 'conn.php';
require_once 'functions.php';
require_once 'http.php';
require_once 'header.php';
?>
<script type='text/javascript'>
function deletePost(id,redir) {
    if (id > 0) {
        window.location = "transact-post.php?action=delete&post=" + id + "&redir=" + redir;
    } else {
        history.back();
    }
}
function deleteForum(id,redir) {
    if (id > 0) {
        window.location = "transact-forum.php?action=delete&forum=" + id + "&redir=" + redir;
    } else {
        history.back();
    }
}
</script>
<?php
if (isset($_REQUEST['action'])) {
  switch ($_REQUEST['action']) {
    case 'delete':
      $sql = "DELETE FROM forum_posts WHERE id='" . $_GET['post'] . "'";
      mysql_query($sql, $conn)
      or die("Could not delete post: ' . mysql_error($conn));
      redirect($_REQUEST['redir']);
      break;
  }
}
```
