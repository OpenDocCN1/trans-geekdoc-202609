# Building a Content Management System

```
$result = mysql_query($sql) or die(mysql_error());

$sql = <<EOS
CREATE TABLE IF NOT EXISTS cms_users (
  user_id int(11) NOT NULL auto_increment,
  e-mail varchar(255) NOT NULL default '',
  passwd varchar(50) NOT NULL default '',
  name varchar(100) NOT NULL default '',
  access_lvl tiny(4) NOT NULL default '1',
  PRIMARY KEY (user_id),
  UNIQUE KEY uniq_e-mail (e-mail)
)
EOS;
$result = mysql_query($sql) or die(mysql_error());

$admin-mail = "admin@yoursite.com";
$adminpass = "admin";
$adminname = "Admin";

$sql = "INSERT IGNORE INTO cms_users VALUES (\n'$admin-mail', '$adminname', 3);\n"
$result = mysql_query($sql) or die(mysql_error());";

echo "<head><title>CMS Tables Created</title></head><body>";

echo "CMS Tables created. Here is your initial login information:\n";
	echo "<ul><ul><li><strong>login:</strong> " . $admin-mail . "</li>\n";
	echo "<li><strong>password:</strong> " . $adminpass . "</li>\n";
	echo "</ul>\n<a href="login.php">Login</a> to the site now.\n";

echo "</body></html>";
?>
```

+   3. Some functions are used on many pages. Those are included in the file outputfunctions.php, which is included at the top of each appropriate page:

```
?php

function trimBody($text, $lmt=500, $s_char="\n", $s_cnt=2) {
$pos = 0;
$trimmed = FALSE;
for ($i=1; $i <= $s_cnt; $i++) {
  if ($tmp = strpos($text, $s_char, $pos)) {
    $pos = $tmp;
    $trimmed = TRUE;
  } else {
    $pos = strlen($text) - 1;
    $trimmed = FALSE;
    break;
  }
}
$text = substr($text, 0, $pos);

if (strlen($text) > $lmt) {
  $text = substr($text, 0, $lmt);
```