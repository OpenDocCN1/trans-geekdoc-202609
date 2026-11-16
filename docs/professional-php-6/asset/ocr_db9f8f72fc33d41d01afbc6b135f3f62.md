```
```php
$smarty->assign_by_ref("user", $session->getUserObject());
$smarty->display ("main.tpl");
exit;
} else {
if (array_key_exists("login_name", $_REQUEST)) {
$smarty->assign('error', "Invalid login, try again.");
}
$smarty->display ("login.tpl");
exit;
}
```
```

```
```php
break;
case "logout":
$session->logout();
if ($session->isLoggedIn()) {
$smarty->assign_by_ref("user", $session->getUserObject());
$smarty->display ("main.tpl");
exit;
} else {
if (array_key_exists("login_name", $_REQUEST)) {
$smarty->assign('error', "Invalid login, try again.");
}
$smarty->display ("login.tpl");
exit;
}
break;
default:
if ($session->isLoggedIn()) {
$smarty->assign_by_ref("user", $session->getUserObject());
$smarty->display ("main.tpl");
exit;
} else {
if (array_key_exists("login_name", $_REQUEST)) {
$smarty->assign('error', "Invalid login, try again.");
}
$smarty->display ("login.tpl");
exit;
}
```
```

```
```php
} else {
if ($session->isLoggedIn()) {
$smarty->assign_by_ref("user", $session->getUserObject());
$smarty->display ("main.tpl");
exit;
} else {
if (array_key_exists("login_name", $_REQUEST)) {
$smarty->assign('error', "Invalid login, try again.");
}
}
```
```