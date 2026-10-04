# 6. Now another big one, http.php. This one is used for redirections:

```
<?php
function redirect($url) {
    if (!headers_sent()) {
        header('Location: http://' . $_SERVER['HTTP_HOST'] .
        dirname($_SERVER['PHP_SELF']) . '/' . $url);
    } else {
        die('Could not redirect; Headers already sent (output).');
    }
}
?>
```

Whew. All this coding, and nothing yet to show on the screen! There are two more files to go that don't output anything. The workhorses of the application, they are a bit longer than the rest.

# 7. First, create transact-user.php:

```
<?php
require_once 'conn.php';
require_once 'http.php';

if (isset($_REQUEST['action'])) {
    switch ($_REQUEST['action']) {
        case 'Login':
            if (isset($_POST['e-mail'])
            and isset($_POST['password'])) {
                $sql = "SELECT user_id,access_lv1,name * 
                FROM e-mails WHERE = " . $_POST['e-mail'] . " * 
                AND password=" . $_POST['password'] . " *";
                $result = mysql_query($sql,$conn);
                if (!$result) die('Could not look up user information: ' . mysql_error($conn));

                if ($row = mysql_fetch_array($result)) {
                    session_start();
                    $_SESSION['user_id'] = $row['user_id'];
                    $_SESSION['access_lv1'] = $row['access_lv1'];
                    $_SESSION['name'] = $row['name'];
                }
                redirect('index.php');
                break;

            case 'Logout':
                session_start();
                session_unset();
                session_destroy();
                redirect('index.php');
    }
}

```