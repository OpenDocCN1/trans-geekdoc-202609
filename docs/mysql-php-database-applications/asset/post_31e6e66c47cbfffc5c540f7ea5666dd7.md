
```
mysql> use guestbook;
Database changed
mysql> create table guestbook
-> (
-> 	 name 			 varchar(40) null,
-> 	 location 		 varchar(40) null,
-> 	 email 		 varchar(40) null,
-> 	 url 			 varchar(40) null,
-> 	 comments 		 text null
-> ) 
-> ;
Query OK. 0 rows affected (0.00 sec)
mysql>
```

Then you have to give your application permission to use the table:

```
mysql> grant delete, insert, select, update on guestbook
-> 		 to nobody@localhost identified by 'ydobon';
Query OK. 0 rows affected (0.00 sec)
```

Then you issue a quick statement that forces the server to re-read the permissions tables, effectively putting the new ones into effect:

```
mysql> FLUSH PRIVILEGES;
```

So now you have a database named guestbook and a table, also named guestbook, within the database. Now it's time to write an application in PHP that will enable you to insert, edit, and view information kept in this guestbook.

## Your PHP script

Now's the time to move to the text editor. In the course of configuring your Web server, you need to let it know which files should be handed off to PHP so the engine can interpret the page. Most often these files have a .php extension, though it is possible to have PHP interpret anything, including .html files. These scripts live inside the folder designated to hold Web pages. For Apache, this is usually /htdocs.

## BASIC SYNTAX

One neat thing about PHP is that it lets you move between straight HTML and commands that are part of the PHP programming language. It works like this: The sections of your script between the opening tag (<?php) and the closing tag (?> ) are interpreted by the PHP engine, and portions not within these tags are treated as plain HTML. Check out the following PHP page.

```
<?php
echo "Hi, ";
?>
mom.
```

When run through the Web server, this code creates a Web page that prints, simply, Hi, mom. PHP's echo command manages the first part of the line. But, of course, PHP can do quite a bit more than that. Like any other programming language, it can work with variables and make decisions.

```
<?php
echo "Hi, mom. ";

$var = date("H");
if ($var <= 11)
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

In the preceding code, after printing out the greeting, there is some real programming. We have used PHP's built-in date function to grab the hour of the day in 24-hour format. That value is immediately assigned to a variable named $var. Then a decision is made, and the appropriate text is printed, depending on the time of day. Notice the syntax here. Each PHP command ends with a semicolon (;). In the if statement, curly braces ({}) hold the commands to be executed depending on the condition. And the condition itself is held within parentheses (()).

The date() function and echo, which are used in the previous example, are just two of the hundreds of functions built into PHP, many of which you learn to use in the course of this book. If you are going to access the database, you're going to need a few more.

## CONNECTING TO THE DATABASE

While you're installing PHP you should let it know that you plan on using MySQL with it. If you don't do this, what we discuss now won't work. Even if PHP is aware that you're using MySQL, in your specific scripts you must identify the exact database you need access to. In this case, that is the guestbook database you just created.

```
mysql_connect("localhost","nobody","ydobon")
or die("<h3>could not connect to MySQL</h3>\n");
mysql_select_db("guestbook")
or die("<h3>could not select database 'guestbook'</h3>\n");
```

The first line in the preceding code tells MySQL that the Web server (the entity running the script) is on the local machine, has a username of *nobody*, and has a password of *ydobon*. Then, if the connection is successful, the specific database is selected with the `mysql_select_db()` command. With these lines safely tucked away in your scripts, you should be able to manipulate the database with your commands.

Because you're going to need these lines in every page in this application, it makes sense to save some typing, put them in a file of their own, and include them in every page. If you've done any programming at all, you know that this involves dumping the entire contents of that file into the file being accessed. These lines are kept in a file called dbconnect.php. At the top of every other file in this application will be the following line:

```
include('dbconnect.php');
```

## INSERTING INFORMATION INTO THE DATABASE

Because you have yet to put any users in the database, we start by reviewing the script that enables you to do that. But first, we need to tell you a little bit more about PHP variables. A bit earlier in this introduction in the section “Basic Syntax,” we showed that you can create variables within a PHP script, but because this is a client/server environment, you’re going to need to get variable data from the client (the Web browser) to PHP. You usually do this with HTML forms.

There’s a basic rundown of HTML forms in Appendix B. Check that if you need to. For now we just want to point out that every form element has a name and that when a form is submitted, the names of those form elements become available as variables in the PHP script the form was submitted to.

In older versions of PHP, these variables would automatically be created as global variables: If you submitted a form with a field named firstname, the script receiving the form would have a variable named $firstname defined when it began. This can lead to some serious security problems, however. So now, the values are available as elements in the system-defined “superglobal” arrays, such as $_GET (for fields passed in as part of the URL) and $_POST (for fields submitted from forms). The simplest of these to use is $_REQUEST, which combines GET, POST, and cookie values. If you’re not understanding all of this right now, don’t worry about it; these concepts are covered in greater detail later in the book, particularly in Chapter 9.

As soon as the following form is submitted, the variables $_REQUEST['surname'] and $_REQUEST['submit'] become available in the PHP script myscript.php. The value of $_REQUEST['surname'] is whatever the user enters into the text field. The value of $_REQUEST['submit'] is the text string submit.

```
<form action="myscript.php">
<input type="text" name="surname">
<input type="submit" name="submit" value="submit">
</form>
```

Before we show the script itself, now is a good time to note that Web programming is slightly different from other types of programming in one important respect: It is stateless. To display a page, a Web server must first receive a request from a browser. The language they speak is called HTTP, the Hypertext Transfer Protocol. The request includes several things— the page the browser wishes to see, the form data, the type of browser being used, and the IP address the browser is using. Based on this information, the Web server decides what to serve.

Once it has served this page, the server maintains no connection to the browser. It has absolutely no memory of what it served to whom. Each HTTP request is dealt with individually with no regard to what came before it. For this reason, in Web programming you need to come up with some way of maintaining state. That is, if you are progressing through an application, you need some way of letting the server know what happened. Essentially, you need ways of passing variables from page to page. This comes up in our applications. The applications have three ways in which to do this: by passing hidden form elements, by using cookies, or by using sessions.

Now back to the script.

```
<form action="myscript.php">
<input type="text" name="surname">
<input type="submit" name="submit" value="submit">
</form>
```

You can decide what you display on a page based on the variable information that comes from HTML forms. For example, you can find out whether the preceding form has been submitted by checking if the variable name $_REQUEST['submit'] has a value of submit. This very technique comes into play when we create the page for inserting information into the database.

There is one page in our application, called sign.php, that has an HTML form. The action of the form (the program to run as a result of the submission) in this page is create_entry.php. Here's the page in all its glory:

```
<h2>Sign my Guest Book!!</h2>
<form method="post" action="create_entry.php">
<b>Name:</b>
<input type="text" size="40" name="name">
<br>
```
