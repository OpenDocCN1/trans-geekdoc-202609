
# Chapter 11

## Friendlier Logins Using PHP’s Session and Cookie Functions

This section is not just for restricted access to certain PHP files; these functions are used to require that users of your Web site be authorized before they use the Web pages to their full functionality. Keep in mind that this is really useful when protecting sections of Web pages, not for protecting all files and directories. (This will make more sense when you jump into the code).

This form of authorization could be used in an administration area of a Web site where an administrator can change content that is viewable by the public. Note that this can be used in conjunction with htaccess for higher security, if needed.

## Try It Out Using PHP for Logins

Now let's use some code within PHP to authorize the user’s username and password.

- 1. Open your favorite text editor.
- 2. Create a new PHP file, saving it as template.php. This file will be the template we’ll use to illustrate how you protect a page.
- 3. Start off each Web page you wish to protect with this code:

```php
<?php
include 'auth.inc.php';
?>
<html>
<head>
<title>Beginning PHP, Apache, MySQL Web Development</title>
</head>
<body>
<h1>This is the Template Page</h1>
</body>
</html>
```

The preceding template is just an example of what you would do to protect a PHP page. In a real working situation, you can replace everything between the opening and closing <body> tags to protect any PHP page that you feel necessary.

This takes us to the authorization file, which is checking if the user has successfully started a session logging in. If not, the user is redirected to the login page.

- 4. Use the following code to create a page and save it as auth.inc.php.

```php
<?php
session_start();
if ($_SESSION['logged'] != 1) {
    $redirect = $_SERVER['PHP_SELF'];
    header("Refresh: 0, URL=login.php?redirect=$redirect");
    echo "You are being redirected to the login page!<br>";
    echo "(If your browser doesn't support this, <a href=\"login.php?redirect=$redirect\">click here</a>)\n";
    die();
}
?>
```

- 5. Now that you have the template page and the authorization page done, let's create the login page that you use to create sessions that allow you to gain access to your protected pages. Enter the following code, which actually does the login authorization and the creation of session for the user once he has successfully provided the correct username and password.

```php
<?php
session_start();
$_SESSION['logged'] = 0;

if (isset($_POST['submit'])) {
    if ($_POST['username'] == "xrowbooks" && $_POST['password'] == "aregreat") {
        $_SESSION['logged'] = 1;
        header("Refresh: URL=" . $_POST['redirect']);
    }
}
}
?>
<body>
</body>
</html>
```This may seem to be a less-than-useful example, but it shows that you can protect pages so not just any Joe Moe can gain access to them. In fact, this example would work fine if you need to have just one or two users and/or administrators share usernames and passwords.

Later in the chapter, we will show you how you can use PHP in conjunction with MySQL to create user-driven login systems. We also show how to allow multiple administrators, multiple usernames and passwords, and privilege levels that can be managed with the MySQL database.

## How It Works

Now that you have all the code typed in, you can navigate to the template.php page you created. Because you haven't logged in, the auth.inc.php file we included redirects you to the login.php page that requires you to log in to view the initial page requested.

Try inputting the incorrect information so you can see how the login page works. You will see a screen similar to the one in Figure 11-4.

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_346_0.png)

## Using Logins, Profiles, and Personalization

Input the correct information: xrowbooks for the username, and aregreat for the password. At this point, you are redirected to the page you originally requested because you supplied the information correctly: You will see a screen similar to Figure 11-5.

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_347_0.png)

Figure 11-5

This is a very useful way to protect your PHP files to limit use to logged-in users and administrators. However, there are a couple of minor drawbacks that you will solve later when you integrate the database-driven system:

- This is manageable only for a few users with login information.
- It's somewhat labor intensive when the need to move to a user-driven database system arises.

## Using Database-Driven Information

We will now show you what you can do with a database-driven Web site. Obviously, we will be using a MySQL database as our preferred database, but keep in mind that PHP can be used with many other databases as well.

We first set up a couple of tables in our database. For this we will show you the table schema we will need. We call our database registration and our tables admin and user.

- 1. We set up a couple of tables in our database. For this we will show you the table schema we will need. We call our database registration and our tables admin and user. We first set up a couple of tables in our database. For this we will show you the table schema we will need. We call our database registration and our tables admin and user. We first set up a couple of tables in our database. For this we will show you the table schema we will need. We call our database registration and our tables admin and user.

- 1. We set up a couple of tables in our database. For this we will show you the table schema we will need. We call our database registration and our tables admin and user. We first set up a couple of tables in our database. For this we will show you the table schema we will need. We call our database registration and our tables admin and user.

- 1. We set up a couple of tables in our database. For this we will show you the table schema we will need. We call our database registration and our tables admin and user.

- 1. We set up a couple of tables in our database. 

```sql
CREATE TABLE admin (
    id int AUTO_INCREMENT PRIMARY KEY,
    username varchar(50) NOT NULL,
    password varchar(255) NOT NULL,
    first_name varchar(50) NOT NULL,
    last_name varchar(50) NOT NULL,
    email varchar(50) NOT NULL,
    admin_level int DEFAULT 0
);
```

```sql
CREATE TABLE user_info (
    id int AUTO_INCREMENT PRIMARY KEY,
    username varchar(50) NOT NULL,
    password varchar(255) NOT NULL,
    first_name varchar(50) NOT NULL,
    last_name varchar(50) NOT NULL,
    email varchar(50) NOT NULL,
    city varchar(50) NOT NULL,
    state varchar(50) NOT NULL,
    hobbies varchar(255) NOT NULL
);
```