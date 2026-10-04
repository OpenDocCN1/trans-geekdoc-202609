# Building a Content Management System

or die('Could not connect to the database; ' . mysql_error());

The code in conn.php simply defines the constants, connect to the server, and then selects the database to use. If you are using more than one database, you simply need to change the mysql_select_db command to access the appropriate database before running any SQL commands.

# Create the Database Tables

Once conn.php is created, you can create your database tables. Do this with CMStables.php.

First, connect to the database.

```
require_once 'conn.php';
```

Next, create the table needed for access levels. All of the fields, their datatypes, and other parameters are defined in this SQL statement. We use NOT EXISTS SO THAT the CREATE command does not if the table already exists. If you wanted CMStables.php to create a new, clean version of the app, then you could use IF EXISTS and run the SQL command DROP TABLE filename before re-creating the table.

```
$sql = <<EOS
CREATE TABLE IF NOT EXISTS cms_access_levels (
access_lvl int(4) NOT NULL auto_increment,
access_name varchar(50) NOT NULL default '',
PRIMARY KEY (access_lvl)
nEOS;
$result = mysql_query($sql) or die($mysql_error());
```

The next lines insert data into your created cms_access_levels table. These access levels are used throughout the CMS application to determine which users have access to.

```
$sql = "INSERT IGNORE INTO cms_access_levels VALUES (1, 'User');";
$result = mysql_query($sql) or die($mysql_error());
```

We won't include every SQL statement from CMStables.php. If you are knowledgeable enough to read this book, then you can figure out the rest of the SQL commands. We are showing you the following command to illustrate the use of keys.

```
$sql = <<EOS
CREATE TABLE IF NOT EXISTS cms_articles (
article_id int(11) NOT NULL auto_increment,
author_id int(11) NOT NULL default '0',
is_published tinyint(1) NOT NULL default '0',
date_submitted datetime NOT NULL default '0000-00-00 00:00:00',
date_published datetime NOT NULL default '0000-00-00 00:00:00',
ntitle varchar(255) NOT NULL '',
body mediumtext NOT NULL,
PRIMARY KEY (article_id),
```