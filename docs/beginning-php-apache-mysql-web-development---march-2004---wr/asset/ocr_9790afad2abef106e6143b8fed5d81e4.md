# Building Databases

+   1. Open your favorite text editor, and enter the following code (making sure you use the proper values for your server):

```
<?php
define('SQL_HOST','yourhost');
define('SQL_USER','joeuser');
define('SQL_PASS','yourpass');
define('SQL_DB','yourdatabase');

?>
```

+   2. Save the file as config.php.

This file will be included on each subsequent PHP file that needs to access the database:

+   3. Type the following code in your favorite PHP editor, and save it as make_table.php:

```
<?php
require('config.php');

$conn = mysql_connect(SQL_HOST, SQL_USER, SQL_PASS)
or die("not connect to MySQL database: " . mysql_error($conn));

$mysql_select_db(SQL_DB,$conn);

$sql1 = 
CREATE TABLE IF NOT EXISTS char_main (
id int(11) NOT NULL auto_increment,
alias varchar(40) NOT NULL default '',
real_name varchar(80) NOT NULL default '',
lair_id int(11) NOT NULL default 0,
align enum('good','evil') NOT NULL default 'good',
PRIMARY KEY (id)
);

$sql2 =
CREATE TABLE IF NOT EXISTS char_power (
id int(11) NOT NULL auto_increment,
power varchar(40) NOT NULL default '',
PRIMARY KEY (id)
);

$sql3 =
CREATE TABLE IF NOT EXISTS char_power_link (
char_id int(11) NOT NULL default 0,
power_id int(11) NOT NULL default 0,
PRIMARY KEY (char_id,power_id)
);

$sql4 =
CREATE TABLE IF NOT EXISTS char_lair (
id int(11) NOT NULL auto_increment,...
```

249