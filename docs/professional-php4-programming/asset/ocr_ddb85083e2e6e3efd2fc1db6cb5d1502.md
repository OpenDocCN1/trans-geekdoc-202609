```
// Use the ternary operator to give them the correct display
// for how many times they have visited the page.
echo ("Welcome back to my page, $my_cookie[0]! You've been here" .
$my_cookie[1] . ($my_cookie[1] == 1 ? " time!" : " times!"));
} else {
?>
<form action="<?=$PHP_SELF?>" method="POST">
Username: <input type="text" name="username" /><br />
<input type="submit" name="submit" value="Log In">
</form>
<?php
}
?>

```

![](bbox=[0.2, 0.34, 0.83, 0.5])

We can make interesting applications using cookie methods and definitions:

```
<?php
if ($submit) {
// set a cookie that expires on close
setcookie("user_cookie", stripslashes($username));
// The cookie isn't accessible until the next page view...
header("Location: $PHP_SELF");
}
if ($user_cookie) {
?>

<html> Welcome back,<strong>
<?php echo stripslashes($user_cookie) ?></strong>!

<? } else { ?>

<form method="post">
Welcome, visitor. We strive to be as user-friendly as possible, so if
you'll please leave us your name, we'll kindly greet you on your next
visit!
<p>
Your name:
```