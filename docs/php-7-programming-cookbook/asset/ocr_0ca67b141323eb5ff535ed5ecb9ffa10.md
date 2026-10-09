You can see in the next screenshot that we are now an authenticated user without entering the username or password:

![](bbox=[0.28, 0.18, 0.97, 0.51])

You can now implement the changes discussed in the preceding steps. Copy the file created previously to `chap_12_session_protected.php`. Now go ahead and regenerate the session ID:

```
```php
<?php
define('THUMB_PRINT_DIR', __DIR__ . '/../data/');
session_start();
session_regenerate_id();
```
```

Next, initialize variables and determine the logged in status (as before):

```
```php
$username = 'test';
$password = 'password';
$info = 'You Can Now See Super Secret Information!!!';
$loggedIn = $_SESSION['isLoggedIn'] ? FALSE;
$loggedUser = $_SESSION['user'] ?? 'guest';
```
```

You can add a session thumb-print using the remote address, user agent, and language settings:

```
```php
$remotePrint = md5($_SERVER['REMOTE_ADDR']
    . $_SERVER['HTTP_USER_AGENT'])
```
```