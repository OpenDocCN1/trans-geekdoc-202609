# Login Sucess

![](bbox=[0.095, 0.068, 0.683, 0.115])

Login was successful.

Your html/PHP goes here.

Click here to log out.

Figure 7-38: LoginSuccess.php page.

# Logout.php

The log out page is very similar to a protected page. You start by maintaining the current session. Then change the $_SESSION login value to "0". You can also use the PHP method session_destroy to clear after all the session information. However, after a lot of testing I found that I was still able to access protected pages even after I used this method because the session global variables are not set. Therefore, the shortest method that I found that actually works was to change the login value. Otherwise you can clear the values using $_SESSION = array() and session_destroy() (2 line of code, compared to 1 line of code). Finally, once the user is logged out you can redirect them back to another page.

```
<?php
session_start();
$_SESSION['login']=0;
?>
n<html>
<head>
<title>Logout</title>
</head>
<body>Log out was successful.
<p>
Put your redirect code here or a link to your home page.
<p>
<a href="Login.php">Click here to try the demo again.</a>
</p>
</body>
</html>
```

> session_destroy(): Destroys all data registered to a session. It does not unset associated with the session or unset the session code. To unset all the session variables you would:

$_SESSION = array();
session_destroy();

http://us3.php.net/manual/en/function.session-destroy.php