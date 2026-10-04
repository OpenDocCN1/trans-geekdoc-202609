# Building a Content Management System

In order to use the array we created earlier within this function, we must declare it global. Now the function can access the data in the array.

```
global $a_users;
```

This function will be called more than once. Each time, a different value will be contained in the $l1 variable. The following SQL pulls the appropriate data according to the $l1 value:

```
$sql = "SELECT user_id, name, e-mail FROM cms_users * \n"WHERE access_l1 = $l1 ORDER BY name";

$result = mysql_query($sql) or die(mysql_error());
```

If users are not found in this access level, we display a message explaining that those users were not found. Then we use the array we created earlier:

```
if (mysql_row_rows($result) == 0) {
echo "$a_users[$l1] . *created.</em>";
```

A user cannot modify his or her record. Instead, his or her name is shown in plain text, with

```
} else {
while ($row = mysql_fetch_array($result)) {
if ($row['user_id'] == $_SESSION['user_id']) {
echo htmlspecialchars($row['name']) . " <br />\n";
```

Other's name is displayed on the screen, a link that leads useraccount.php.

```
} else {
echo "<a href='useraccount.php?userid=' . $row['user_id'] . " title='" . htmlspecialchars($row['e-mail']) . '\'>" . htmlspecialchars($row['name']) . "</a><br />\n";
}
```

Here's the end of the function. Note that nothing has been output to the screen.

```
}
}
}
```

Then you display the page title:

```
?
<h2>User Administration</h2>
```

Then you loop through the code three times, running the function each time with a different level value:

```
<?php
for($i=1;$i<=3;$i++) {
echo "<h3>" . $a_users[$i] . "</h3>\n";
echo "<div class='scroller'>\n";
echoUserList($i);
echo "</div>\n";
}
?>
```