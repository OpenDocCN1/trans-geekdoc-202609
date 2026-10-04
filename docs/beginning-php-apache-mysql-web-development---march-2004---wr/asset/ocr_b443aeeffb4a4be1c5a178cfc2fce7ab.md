# Mailing Lists

```
echo $msg;
?>

<body>
</html>
```

4. One more file to go, and it's a short one. The e-mail that you sent has a link on allowing yours to remove themselves from the mailing list, if they desire. Enter that file now, and save it as remove.php:

```
<?php
require('config.php');

$conn = mysql_connect(SQL_HOST, SQL_USER, SQL_PASS)
die('Could not connect to MySQL database. ' . mysql_error());

$mysql_select_db($SQL_DB, $conn);

if (isset($_GET['ml']) && isset($_GET['user'])) {
$sql = "DELETE FROM ml_subscriptions \
WHERE user_id='" . $_GET['user'] . \\nAND ml_id='" . $_GET['ml'] . \'";
$result = mysql_query($sql, $conn);
} else {
die('Incorrect parameters passed for deletion');
}

if ($result) {
$msg = "<h2>Removal Successful</h2>h2>";
} else {
$msg = "<h2>Removal Failed</h2>";
}

$ml_id = $_GET['ml'];
$sql = "SELECT * FROM ml_lists WHERE ml_id = '" . $ml_id . "'";
$result = mysql_query($sql);
die('Invalid query: ' . mysql_error());
if (mysql_num_rows($result)) {
$row = mysql_fetch_array($result);
$msg = "<li>You have been removed from the <li>"
$row['listname'] . "</li> mailing list.<br />";
} else {
$msg = "<li>Sorry, could not find Mailing List id#" . $ml_id . "#</li>";
}

$msg .= "<a href='user.php?u='" . $_GET['user'] . "'>\ 
'Return to Mailing List Signup page</a>";
echo $msg;
?>
```

Excellent job! Now it's time to test your code and figure out how it works. Follow these steps:

443