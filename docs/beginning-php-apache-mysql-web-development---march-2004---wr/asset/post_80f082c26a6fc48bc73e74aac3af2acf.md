
# An Introduction to PEAR

coding standards. Each package is developed by a team or individual, and must contain specific information such as documentation and a list of dependencies (both and from other packages).

The packages are defined as "nodes" on a "tree". For example, the XML_Parser node is grouped with other XML packages. This grouping is for organizational purposes—dependencies have nothing to do with the locations of nodes on a tree. The Mail package, for example, depends on the Net_SMTP package, even though they are not connected nodes.

PEAR package developers are required to follow a strict set of coding standards called logically enough, the PEAR Coding Standards. One of the great things about PEAR (and open source development in general) is that anyone can develop a package and insert it into the PEAR package. ("PEAR tree—isn't that clever? I'm just waiting for the first person to create a Partridge package)

The big package we are going to discuss in this appendix is the database PEAR DB. While there are many excellent packages, this one is probably the most used. Many love it, and many hate it. It has its benefits, but it has a few downsides. We'll touch on shortly.

We'll also take a look at a few other package nodes, including Authentication, Mail, Payment, XML, and HTML.

# PEAR DB

Before you delve into PEAR, you must be aware that most PEAR packages use objects and classes. If you are not familiar with PHP's implementation of object-oriented programming, you might want to read the Classes and Objects section of the PHP manual (www.php.net/oop).

In order to use PEAR DB (also written as PEAR:DB), you must include the file db.php in your page. This is your "window" to the PEAR DB classes, and it is the only file you need to include. It will implement a class called DB_common, which is contained in the DB/common.php file.

In common.php, you find the code that is common across different databases and some basic utility functions. If necessary, some of the classes will be overwritten, depending on the specific database driver you load.

This brings us to the third file: driver. This file is loaded dynamically, on which database you specify as the one you use. If you are using MySQL, for example, DB/mysql.php is loaded. It implements a class called DB_mysql that extends DB_common, and contains classes and functions specific to the needs of MySQL databases.

What does this mean? Basically, it's as transparent to you as database access goes. You include db.php in your page and specify the database you are accessing (along with user, host, and database, as usual), and PEAR DB does the rest.

Let's say you have a database with the following two tables. You may remember these tables from Chapter 9. Let's use these tables in an example to see how PEAR DB compares to standard database functions. All of our examples will use these two tables.

# Appendix H

| id | league_id | alias | real_name |
|---|---|---|---|
| 1 | 2 | Average Man | Bill Smith |
| 2 | 2 | The Flea | Tom Jacobs |
| 3 | 1 | Albino Dude | George White |
| 4 | 3 | Amazing Woman | Mary Jones |

| id | league |
|---|---|
| 1 | Amazing People |
| 2 | Dynamic Dudes |
| 3 | Stupendous Seven |
| 4 | Justice Network |

Our first example uses MySQL-specific commands to retrieve all of the records and display them on the screen. For simplicity, we will include the database constants in the same code. Just remember the best coding practice is to put them into a config.php file and include them.

```php
<?php
$host = 'localhost';
$uname = 'username';
$passwd = 'password';
$db_name = 'yourdatabase';

$conn = mysql_connect($host, $uname, $passwd)
or die('Could not connect to MySQL database.' . mysql_error());

mysql_select_db($db_name, $conn);

$sql = "SELECT * FROM users, league s WHERE u.id = s.league_id";
$result = mysql_query($sql) or die(mysql_error());

while ($row = mysql_fetch_array($result)) {
    echo $row['alias'] . ' ( ' . $row['real_name'] . ' ) is a member of ';
    echo 'the ' . $row['league'] . ' League.<br>';
}
?>
```

Here is what the code looks like if you use PEAR:

```php
<?php
$host = 'localhost';
$uname = 'username';
$passwd = 'password';
$db_name = 'yourdatabase';
$db_type = 'mysql';
?>
```

# An Introduction to PEAR

```php
require_once('DB.php');
$dsn = '$db_type:username=$password@host=$db_name';
$conn = DB::connect($dsn);
if ($db->isError($conn)) {
    die('Unable to connect: ' . $conn->getMessage() . ' \n');
} 

$sql = 'SELECT * FROM heroes s, league l WHERE l.id = s.league_id';
$result = $conn->query($sql);
if ($db->isError($result)) {
    die('Query failed: ' . $result->getMessage() . ' \n');
} 

while ($row = $result->fetchrow(DB_FETCHMODE_ASSOC)) {
    echo $row['alias'] . ' (' . $row['real_name'] . ') is a member of ';
    echo 'the ' . $row['league'] . '<br>';
}
?>
```

If you load this in your browser, you will see the following on the screen:

Average Man (Bill Smith) is a member of the Dynamic Dudes League.
Thea (Tom Jacobi) is a member of the Dynamic Dudes League.
Albino Duke (George White) is a member of the Amazing People League.
Amazing Woman (Mary Jones) is a member of the Stupendous Seven League.

The PEAR method takes more lines, and the syntax is a little different (which can be especially difficult if you are not familiar with objects). So why would you use PEAR?

Remember that PEAR DB acts as an abstraction layer to help interface with your database. If you look closely at the PEAR code, you'll notice that none of the functions refer to the type of database you are using. In fact, they are quite generic. In contrast, the first code snippet uses mysql throughout the code. That's not a problem, as long as you always use MySQL.

So, should you install and use PEAR? Perhaps you need to weigh the benefits against potential problems and determine if it's right for you. In the meantime, if you are working on a big PHP project, make sure you are sure what database you will accessing. You can avoid a lot of headaches in the future (your IT Manager will thank you for that).

# Other PEAR Packages

PEAR::DB may be the most popular package available, but it is not the only package available. Let's take a look at a few of the other packages available in PEAR, including HTML, Authentication, Payment, and Mail.

For more information on PEAR DB and other PEAR packages, visit http://pear.php.net.

# HTML

The HTML node contains a few packages, designed to make HTML functions easier. A good example of this is HTML_BBCodeParser. This piece of code takes UBB style tags (`[b]`, `[img]`, and so on) and converts them to `<b>`, `<img>`, and so on. If you have ever been to a forum online (such as phpbuilder/board), you have seen these tags in action. This package allows you to create your own custom BBCode, and it claims to generate valid XHTML 1.0 code.

Other HTML packages includes:

- HTML_Menu, which enables the easy creation and maintenance of an HTML menu navigation system
- HTML_QuickForm, which provides methods for creating, validating, and processing HTML forms.
- Pager for HTML pagination (1–10, 11–20, and so on).
