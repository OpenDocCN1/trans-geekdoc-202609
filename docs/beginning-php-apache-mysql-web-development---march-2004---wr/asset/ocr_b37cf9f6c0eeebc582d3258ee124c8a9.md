# Building Databases

```
</form>
<a href="charlist.php?>Return to Home Page</a>
</body>
</html>
```

2. Enter the following code, and save it as charlist.php:

```
<?php
require('config.php');

$ord = $_GET['ord'];
if (is_numeric($ord)) {
  $ord = round(max($ord, 1), 3);
} else {
  $ord = 1;
}

$order = array(
  1 => 'alias ASC',
  2 => 'name ASC',
  3 => 'align ASC, ASC'
);
```

```
$conn = mysql_connect(SQL_HOST, SQL_USER, SQL_PASS)
or die("Could not connect to MySQL database. " . mysql_error());
mysql_select_db($conn, $db);
```

```
$sql = "SELECT c.id, p.name FROM char_main c JOIN char_power p ON char_link_pk ON c.id = char_power_id AND p.id = pk_power_id";
```

```
$result = mysql_query($sql) or die(mysql_error());
if (mysql_num_rows($result) > 0) {
  while ($row = mysql_fetch_assoc($result)) {
    $p[$row['id']] = $row['power'];
  }
}
nforeach ($p as $key => $value) {
  $powers[$key] = implode(",", * ", $value);
}
```

```
$sql = "SELECT c.id, n.alias FROM char_main c JOIN char_good_bad n ON c.id = char_good_bad AND n.id = gb_bad_id"
OR (n.id = gb_good_id AND c.id = gb_bad_id";
```

```
$result = mysql_query($sql) or die(mysql_error());
if (mysql_num_rows($result) > 0) {
  while ($row = mysql_fetch_assoc($result)) {
    $e[$row['id']] = $row['alias'];
  }
}
foreach ($e as $key => $value) {
  $enemelenies[$key] = implode(",", * ", $value);
}
```

```
$table = "<table><tr><td align=\"center\>No characters currently exist.</td></tr>"
```

255