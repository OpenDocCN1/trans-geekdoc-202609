
# Chapter 15

## setup.php

We're doing things differently here from the way we did in other chapters. Previously, when creating a database, we used CREATE TABLE IF NOT EXISTS. That is a good way to create a new table avoid errors if the table already exists. But what if data needs to be inserted into the table? How do you know whether the table was created or already exists? By the CREATE TABLE command, you can't.

Instead, we are going to trap the error caused by creating an existing table. If the error occurs, then we know the table already exists, and we will skip over data insertions and continue with the next table. If any other error occurs, we will halt execution with the die() command, as usual.

First, we create our SQL statement and run it with the mysql_query command. Note the creation of a text index for the subject and body fields. This makes searches much faster (which we will cover shortly). Also note the IF NOT EXISTS keywords.

```php
$sql = <<EOS
CREATE TABLE forum_posts (
  id int(11) NOT NULL auto_increment,
  topic_id int(11) NOT NULL default '0',
  forum_id int(11) NOT NULL default '0',
  author_id int(11) NOT NULL default '0',
  update_id int(11) NOT NULL default '0',
  date_created datetime NOT NULL default '0000-00-00 00:00:00',
  date_updated datetime NOT NULL default '0000-00-00 00:00:00',
  subject varchar(255) NOT NULL default '',
  body text NOT NULL,
  PRIMARY KEY (id),
  KEY IdArticle(forum_id,topic_id,author_id,date_posted),
  FULLTEXT IdText(subject,body)
)
EOS;
$result = mysql_query($sql);
```

Next, we test for the error condition caused by the table existing in the database. The error code is 1050 and is returned by the function mysql_errno(). If we receive that particular error code, everything is ok, but insert will not take place. If there is no table, the creation worked, and we inserted our new data. Any other error handles the program.

```php
switch(mysql_errno()) {
  case 1050:
    break;
  case 0:
    $sql = "INSERT INTO forum_posts VALUES (NULL, 0, 1, 1, 0, '*')";
    date('Y-m-d H:i:s', time()), 0, 'Welcome', 'Welcome to your \nnew Bulletin Board System. Do not forget to change your admin \npassword after installation. Have fun!");
    $result = mysql_query($sql) or die(mysql_error());
    break;
  default:
    die(mysql_error());
    break;
}
```

## Creating a Bulletin System

You may assume we have a vast knowledge of MySQL; just because we know the error code for creating a table that already exists is 1050. The fact is, we did not know the code: We simply ran a CREATE query on a table we knew existed, and echoed the resulting mysql_errno to the screen. Then we knew the code and could trap it for.

Why do we give away a secret? Some may find yourself trying to trap a particular error in your code, and you won't know the code you are looking for. Rather than scouring the Internet hoping to find the code, you can usually induce the error number to the screen. Once you have the code number, you can trap it for, just as we did in the preceding code.

One comment about setup.php before we move on: You may notice that in some cases we used IF NOT EXISTS. If you do not need to know whether you are duplicating a table, then IF NOT EXISTS will work nicely. We included it in cases where we did not need to insert any.

Next, let's take a look at our login procedure. There isn't much new to see here, but it gives us a chance to discuss authentication with you for a moment.

## A Last Look at User Authentication

The CBA uses user authentication, but it is by no means totally. For a board application, it is probably secure enough. However, if there is human data containing sensitive information, you might want to make it a bit more secure.

> This book does not attempt to help you create a virtual Fort Knox. If you have such a need, we strongly suggest looking for a good book on security, and perhaps look at a few online resources. A good start is www.w3.org/Security/Faq/.

Let's take a look at our security model, and see there might be some places to improve it. If you look at the PHP pages that make up the application, you see where we check for a user's access level before displaying items. For example, take a look at header.php.

Because header.php is included at the top of almost every Web page, we do most of our authentication checking. By checking the existence of the user_id session variable, we know whether the user is logged in. By if access_lvl is greater than 2, we know whether the user has administrator access. This allows us to choose the main menu depending on whether the user is logged in, and what access level he or she possesses. It also allows us to access the user by name.

```php
echo '<a href="index.php">Home</a>';
if (isset($_SESSION['user_id'])) {
    echo '<a href="login.php">Log In</a>';
    echo '<a href="useraccount.php">Register</a>';
} else {
    echo '<a href="trans-user.php?action=Logout">Logout</a>';
}
echo "Log out " . $_SESSION['name'] . " </a>";
if ($_SESSION['access_lvl'] > 2) {
    echo '<a href="admin.php">Admin</a>';
}
echo 'useraccount.php';
```

So, if users are not logged in, we give them links to log in or register as a new user. If they are logged in, they can log out or view their profile. And, if they are administrators, they will have access to the admin functions.

That brings us to the admin.php page. We were able to get here by clicking the Admin link, which is available only if you are logged in as the administrator. So, far, good. What if the user attempts to access the admin.php page directly?

Try it yourself. Load index.php in your browser, and make... (Note: text seems to be incomplete based on OCR source)
