```
<?php

// connect to database, generate $link

$business = mysql_real_escape_string($_GET['name'], $link);
$sql = 'UPDATE users SET business=' . $business . ' WHERE id=' . $ID;

?>
```

The advantage to using this function is that it takes care of all the various escaping, which goes beyond single and double quotes. The obvious problem is it requires a MySQL link, so it cannot be used unless the data will be stored in a database. Or, at the very least, you need to have access to a database. An incorrect usage of this function will result in an error, as seen in Figure 7.2.

# FIGURE 7.2

Error message displayed when a MySQL database link is not available

![](bbox=[0.12, 0.43, 0.75, 0.81])