# Activating Sessions

+   - Activate sessions on a per-script basis with the function session_start().

From a performance point-of-view, the latter option is the best one.

```
<?php
session_start();
echo 'Sessions activated.';
?>
```

Activating Sessions (session_start.php)

# Reading and Writing Sessions

```
<?php
session_start();
echo 'Sessions activated.<br />';
$_SESSION['version'] = phpversion();
echo 'Session data written.<br />';
echo "Session data read: {$_SESSION['version']}.";
?>
```

All session data is accessible from a PHP script via the $_SESSION array. Because the data itself is stored on the server-side, you can write session data and read it in the next PHP statement, without the requirement of a round-trip to the server as it was with cookies. Just remember to call session_start() first and then access $_SESSION. The preceding listing creates a session file that Figure 5.6 shows.