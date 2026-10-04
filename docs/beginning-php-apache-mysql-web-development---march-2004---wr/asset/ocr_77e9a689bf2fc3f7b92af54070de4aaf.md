# Chapter 15

```
CREATE TABLE IF NOT EXISTS forum_bbcode (
id int(11) NOT NULL auto_increment,
template varchar(255) NOT NULL default '',
replacement varchar(255) NOT NULL default '',
PRIMARY KEY (id)
)

EOS;
$result = mysql_query($sql) or die(mysql_error());
$tables[] = "forum_bbcode";

******/ Forum Table *******/
$sql = <<EOS
CREATE TABLE forum_row (
id int(11) NOT NULL auto_increment,
forum_name varchar(100) NOT NULL default '',
forum_desc varchar(255) NOT NULL default '',
forum_moderator int(11) NOT NULL default '0',
PRIMARY KEY (id)
)

EOS;
$result = mysql_query($sql);
switch(mysql_errno()) {
case 1050:
break;
case 0:
$sql = "INSERT INTO forum_forum VALUES (NULL, 'New Forum', \"
'This is the initial forum created when installing the \"
'database. Change the name and the description after \\n'installation.', 'i');";
$result = mysql_query($sql) or die(mysql_error());
break;
default:
die(mysql_error());
break;
}
$tables[] = "forum-forum";

******/ Post Count Table *******/
$sql = <<EOS
CREATE TABLE forum_postcount (
user_id int(11) NOT NULL default '0',
count int(9) NOT NULL default '0',
PRIMARY KEY (user_id)
)

EOS;
$result = mysql_query($sql);
switch(mysql_errno()) {
case 1050:
break;
case 0:
$sql = "INSERT INTO forum_postcount VALUES (1,1);\"
$result = mysql_query($sql) or die(mysql_error());
break;

```

508