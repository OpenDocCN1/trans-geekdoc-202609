# Building a Content Management System

# Getting Started
Typically, this is where you threw into a “Try It” section and where you enter code. We’ll get to that shortly. First, we want to let you know that this is a relatively large application, larger than any you have done before. If you don't want to type it all in, that's not a problem—just go to the Web site and download it. Just make sure you go through the “How It Works” section to learn and understand the important concepts. You can download from here:

www.wrox.com

The CMS you are going to build will allow registered users to post articles. Those articles will be labeled “pending” until a user with the proper permissions publishes the article. It’s published, it will show up as the newest article on the home page. Unregistered users will be able to read articles but not be able to post new ones.

Registered users will be able to post comments about an article. When a visitor views a article, all comments will be displayed below it. Sound simple? We’re going to do it with about 20 PHP pages. That might sound like a lot, but it's fairly typical of a standard Web application such as this. There are pages for display (index, admin, pending articles, article review, and on), editing (compose, user account, control panel), and transaction files (for users and article). There are also files used as includes (such as header and footer). Don’t worry—some are only a few lines long. The application contains around 1,000 lines of code, which is pretty short by many application standards.

Let’s do some coding.

# Try It Out The Content Management System Application

As mentioned, there are around 20 PHP pages. Enter each of these files in your favorite PHP editor, and save them with the given filename. We’re going to give you the filename of each one, and introductions whenever necessary. Make sure all files are saved in the same directory as your web server. Our are saved in a directory “CMS”.

+   1. The first file is conn.php. This file will go at the top of each page in the application where you need to connect to the database.

Be sure to enter your own host, username, password, and database. (If you don't have a database created yet, you'll need to create one. Chapter 9 will help you see that you need to.)

```
<?php
def('SQL_HOST', 'yourhost');
def('SQL_USER', 'joeuser');
def('SQL_PASS', 'yourpassword');
def('SQL_DB', 'yourdatabase');

$conn = mysqli_connect(SQL_HOST, SQL_USER, SQL_PASS)
or die('Could not connect to the database: ' . mysqli_error());

mysql_select_db(SQL_DB, $conn)
or die('Could not select database: ' . mysqli_error());

?>?>
```