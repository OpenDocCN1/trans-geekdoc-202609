
# Updating Records with PHP

# Review and Pursue

Now that you have a sufficient amount of PHP, SQL, and MySQL experience under your belt, it’s time to put all of the technologies together. PHP’s strong integration with MySQL is just one reason so many programmers have embraced it; it’s impressive how easily you can use the two together.

This chapter will use the existing `sitename` database—created in Chapter 5, “Introduction to SQL”—to build a PHP interface for interacting with the `users` table. The knowledge taught and the examples used here will be the basis for all of your PHP-MySQL Web applications, as the principles involved are the same for any PHP-MySQL interaction.

Before heading into this chapter, you should be comfortable with everything covered in the first eight chapters, including the error debugging and handling techniques just taught in the previous chapter. Finally, remember that you need a PHP-enabled Web server and access to a running MySQL server in order to execute the following examples.

## Modifying the Template

Since all of the pages in this chapter and the next will be part of the same Web application, it’ll be worthwhile to use a common template system. Instead of creating a new template from scratch, the layout from Chapter 3, “Creating Dynamic Web Sites,” will be used again, with only a minor modification to the header file’s navigation links.

### To make the header file

**1.** Open `header.html` (Script 3.2) in your text editor or IDE.

**2.** Change the list of links to read (Script 9.1):

```html
<li><a href="index.php">Home Page</a></li>
<li><a href="register.php">Register</a></li>
<li><a href="view_users.php">View Users</a></li>
<li><a href="password.php">Change Password</a></li>
<li><a href="#">link five</a></li>
```

All of the examples in this chapter will involve the registration, view users, and change password pages. The date form and calculator links from Chapter 3 can be deleted.

**3.** Save the file as `header.html`.

**4.** Place the new header file in your Web directory, within the `includes` folder along with `footer.html` (Script 3.3) and `style.css` (available for download from the book’s supporting Web site, www.LarryUllman.com).

**Script 9.1.** The site’s header file, used for the pages’ template, modified with new navigation links.

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
    <title><?php echo $page_title; ?></title>
    <link rel="stylesheet" href="includes/style.css" type="text/css" media="screen" />
    <meta http-equiv="content-type" content="text/html; charset=utf-8" />
</head>
<body>
    <div id="header">
        <h1>Your Website</h1>
        <h2>catchy slogan...</h2>
    </div>
    <div id="navigation">
        <ul>
            <li><a href="index.php">Home Page</a></li>
            <li><a href="register.php">Register</a></li>
            <li><a href="view_users.php">View Users</a></li>
            <li><a href="password.php">Change Password</a></li>
            <li><a href="#">link five</a></li>
        </ul>
    </div>
    <div id="content"><!-- Start of the page-specific content. -->
<!-- Script 9.1 - header.html -->
```

**5.** Test the new header file by running `index.php` in your Web browser.

![Image](graphics/09_figure_01_a.jpg)

The dynamically generated home page with new navigation links.

> **Tip**
>
> For a preview of this site’s structure, see the sidebar “Organizing Your Documents” in the next section.

> **Tip**
>
> Remember that you can use any file extension for your template files, including `.inc` or `.php`.

> **Warning: Read This!**
>
> PHP and MySQL have gone through many changes over the past decade. Of these, the most important for this chapter, and one of the most important for the rest of the book, involves what PHP functions you use to communicate with MySQL. For years, PHP developers used the standard MySQL functions (called the `mysql` extension). As of PHP 5 and MySQL 4.1, you can use the newer Improved MySQL functions (called the `mysqli` extension). These functions provide improved performance and take advantage of added features (among other benefits).
>
> As this book assumes you’re using at least PHP 5 and MySQL 5, all of the examples will only use the Improved MySQL functions. *If your server does not support this extension, you will not be able to run these examples as they are written!* Most of the examples in the rest of the book will also not work for you.
>
> If the server or home computer you’re using does not support the Improved MySQL functions, you have three options: upgrade PHP and MySQL, read the second edition of this book (which teaches and primarily uses the older functions), or learn how to use the older functions and modify all the examples accordingly. For questions or problems, see the book’s corresponding forum (www.LarryUllman.com/forums/).

## Connecting to MySQL

The first step for interacting with MySQL—connecting to the server—requires the appropriately named `mysqli_connect()` function:

```php
$dbc = mysqli_connect(hostname, username, password, db_name);
```

The first three arguments sent to the function (hostname, username, and password) are based upon the users and privileges established within MySQL (see Appendix A, “Installation,” for more information). Commonly (but not always), the host value will be `localhost`.

The fourth argument is the name of the database to use. This is the equivalent of saying `USE databasename` within the mysql client.

If the connection was made, the `$dbc` variable, short for *database connection* (but you can use any name you want, of course), will become a reference point for all of your subsequent database interactions. Most of the PHP functions for working with MySQL will take this variable as its first argument.

If a connection problem occurred, you can call `mysqli_connect_error()`, which returns the connection error message. It takes no arguments, so would be called using just:

```php
mysqli_connect_error();
```

Once you’ve connected to the database, you should set the encoding for the interaction. You can do so (as of PHP 5.0.5) with the `mysqli_set_charset()` function:

```php
mysqli_set_charset($dbc, 'utf8');
```

The value used as the encoding—the second argument—should match that of your PHP scripts and the collation of your database (see Chapter 6, “Database Design,” for more on MySQL collations). If you fail to do this, all data will be transferred using the default character set, which could cause problems.

To start using PHP with MySQL, let’s create a special script that makes the connection. Other PHP scripts that require a MySQL connection can then include this file.

### To connect to and select a database

**1.** Create a new PHP document in your text editor or IDE, to be named `mysqli_connect.php` (Script 9.2):

```php
<?php # Script 9.2 - mysqli_connect.php
```

This file will be included by other PHP scripts, so it doesn’t need to contain any HTML.

**2.** Set the MySQL host, username, password, and database name as constants:

```php
DEFINE ('DB_USER', 'username');
DEFINE ('DB_PASSWORD', 'password');
```
