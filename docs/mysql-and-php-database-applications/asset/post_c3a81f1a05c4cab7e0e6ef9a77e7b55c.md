
# Introduction

# xxxiii

scripts will live inside the folder designated to hold Web pages. For Apache, this will usually be /htdocs.

# BASIC SYNTAX

One thing about PHP is that it lets you move between straight HTML and commands that are part of the PHP programming language. It works like this: The sections of your script between the opening tag <?php and a closing tag ?> will be interpreted by the PHP engine, and portions not within these tags will be treated as plain HTML. Check out the following PHP page.

```php
<?php
echo "Hi.";
?>
```

When run through the Web server, this would create a Web page that prints, simply, "Hi, mom." PHP's echo command manages the first part of the line. But, of course, PHP can go quite bit more than that. Like any programming language, it can work with variables and make decisions.

```php
<?php
echo "hi, mom.";

$var = date("H");
if ($var < 11)
{
    echo "good morning";
}
elseif ($var > 11 and $var < 18)
{
    echo "good afternoon";
}
else
{
    echo "good evening";
}
?>
```

In this page, after printing the greeting, there is some real programming, I've used PHP's built-in date function to grab the time of the day in 24-hour format. That value is immediately assigned to a variable named $var. Then a decision is made, and the appropriate text is printed, depending on the time of day. Notice the syntax here. Each PHP command ends with a semicolon. In the if statement, curly braces hold the commands to be executed depending on the condition. And the condition itself is held within parentheses.

# xxxiv Introduction

The date() function and echo, which are used in the previous example, are two of functions built into PHP, many of which you will learn to use in the course. If you are going to access the database, you're going to need a few more.

# CONNECTING TO THE DATABASE

While you're installing PHP; you should let it know that you plan on using MySQL. If you do not do this, we will discuss it later. Even if PHP is aware that you're using MySQL, in your scripts you must identify the exact database you need. In this case, that will be the guestbook you created.

```php
mysql_connect("localhost","nobody","password") or
die("Could not connect to database");

mysql_select_db("guestbook") or
die("Could not select database");
```

The first line that the Web server (the entity) is on the local machine, has username nobody, and password password. If the connection is successful, the specific database is selected with mysql_select_db(). These lines safely tucked away in your scripts, should be able to manipulate the database. Because you're going to need these lines in every page, it makes sense to save them in a file of their own and include them in every page. If you've done any programming at all, you know that this involves the contents of that file being accessed. These lines will be kept in a file named dbconnect.php. At the top of every other file in the application will be the following line:

```php
include("dbconnect.php");
```

# INSERTING INFORMATION INTO THE DATABASE

Because you have yet to put users in the database, we'll start by reviewing the script that will allow that. But first, we need to tell you a little more about PHP variables. A bit earlier about variables within a PHP script, as this is a client/server environment, you're going to get data from the client (Web browser) to PHP. You'll usually do this with HTML forms. There is a basic round to how HTML forms have a name, and when a form is submitted the names of form elements become available as variables in the PHP script the form was submitted to. With the following example, as soon as the form is submitted, the variables $username and $submit become available in the PHP script myscript.php. In the PHP script myscript.php, the value of $username will be whatever the user enters into the text field. The value of $submit will be the string "submit".

```html
<form action="myscript.php">
<input type="text" name="username">
<input type="submit" name="submit" value="submit">
</form>
```

Before we show the script itself, now is a good time to note that Web programming is slightly different from other types of programming in one important respect: it is stateless. To display a page, a Web server must first receive a request from a browser. The language they speak is called HTTP, the Hypertext Transfer Protocol. The request will include several things—the page browser wishes to see, the data, the type of browser being used, and the IP address the browser is using. Based on this information, the Web server will decide what to serve.

Once it has served this page, the server maintains no memory of what it served. Each HTTP request is dealt individually with no regard to what came before. For this reason, in Web programming you need to come up with some way of maintaining state. That is, if you are progressing through an application, you will need some way of letting the server know what happened. Essentially, you need ways of passing variables from page to page. This will come up in our applications. The applications will solve this problem in one of three ways: by using hidden form elements, cookies, or by using sessions.

Now back to our script.

```html
<form action="myscript.php">
<input type="text" name="surname">
<input type="submit" name="submit" value="submit">
</form>
```

You can decide what you will display on a page based on the variable information that comes from HTML forms. For instance, you could check if the preceding form has been submitted by checking if the variable $submit has a value of "submit". This very technique will come into play when it comes to creating the page for inserting information into the database.

There is one page in our application, called sign.php, that has an HTML form. Here’s the page in all its glory:

```html
<h2>Sign my Guest Book!</h2>
```

```html
<form method="post" action="create_entry.php">
<b>Name:</b>
<input type="text" size="40" name="name">
<br>
<b>Location:</b>
<input type="text" size="40" name="location">
<br>
```

# xxxvi Introduction

When the user fills out this form and submits it, the information will be sent to create_entry.php. The first thing to do on this page is to check-that-the-form has been submitted. If it has, take the values entered into the form and use them to create a query that you will send to MySQL. Don't worry about the specifics of the query you just wrote. Just know that it will insert a row into the database.

```php
<?php
include("dbconnect.php");

if ($submit == "Sign!")
{
    $query = "INSERT INTO guestbook (name,location,email,comments) VALUES ('name', '$location', '$email', '$comments')";

    mysql_query($query) or
    die(mysql_error());
}
<h2>Thanks!</h2>
<h2><a href="view.php">View My Guest Book!!!</a></h2>
<?php
else
{
    include("sign.php");
}
?>
```

If the form, which is in sign.php, hasn't been submitted, it is included and therefore will show the same form.

# VIEWING INFORMATION IN THE DATABASE

This shouldn't be too tough. You already know that the file will need to include dbconnect.php. Other than that, we've already mentioned that databases store information in tables. Each row of the table will contain information on a specific person who signed the guestbook, so to view all of the information, the page will need to retrieve and print every row of data. Here's the script that will do it:

```php
<?php include("dbconnect.php"); ?>

<h2>View My Guest Book!!</h2>
```
