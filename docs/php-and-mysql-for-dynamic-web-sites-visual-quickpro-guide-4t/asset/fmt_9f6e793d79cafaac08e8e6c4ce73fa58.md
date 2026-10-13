
Any of the PHP comments can be used at the end of a line (say, after a function call):

```
echo 'Howdy'; /* Say 'Howdy' */
```

Although this is allowed, it’s far less common.

***

***

Tip

It’s nearly impossible to over-comment your scripts. Always err on the side of writing too many comments as you code. That being said, in the interest of saving space, the scripts in this book will not be as well documented as I would suggest they should be.

***

***

Tip

It’s also important that as you change a script you keep the comments up-to-date and accurate. There’s nothing more confusing than a comment that says one thing when the code really does something else.

***

### What Are Variables?

Variables are containers used to temporarily store values. These values can be numbers, text, or much more complex data. PHP supports eight types of variables. These include four scalar (single-valued) types—`Boolean` (`TRUE` or `FALSE`), `integer`, `floating point` (decimals), and `strings` (characters); two nonscalar (multivalued)—`arrays` and `objects`; plus `resources` (which you’ll see when interacting with databases) and `NULL` (which is a special type that has no value).

Regardless of what type you are creating, all variable names in PHP follow certain syntactical rules:

*   A variable’s name must start with a dollar sign (`$`), for example, `$name`.
*   The variable’s name can contain a combination of letters, numbers, and the underscore, for example, `$my_report1`.
*   The first character after the dollar sign must be either a letter or an underscore (it cannot be a number).
*   **Variable names in PHP are case-sensitive!** This is a very important rule. It means that `$name` and `$Name` are entirely different variables.

To begin working with variables, this next script will print out the value of three *predefined variables*. Whereas a standard variable is assigned a value during the execution of a script, a predefined variable will already have a value when the script begins its execution. Most of these predefined variables reflect properties of the server as a whole, such as the operating system in use.

Before getting into this script, there are two more things you should know. First, variables can be assigned values using the equals sign (`=`), also called the *assignment operator*. Second, to display the value of a variable, you can print the variable without quotation marks:

```
print $some_var;
```

Or variables can be printed within *double* quotation marks:

```
print "Hello, $name";
```

You cannot print variables within single quotation marks:

```
print 'Hello, $name'; // Won't work!
```

**Script 1.5.** This script prints three of PHP’s many predefined variables.

***

```
1   <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML
       1.0 Transitional//EN" "http://www.w3.org/
       TR/xhtml1/DTD/xhtml1-transitional.dtd">
2   <html xmlns="http://www.w3.org/1999/
       xhtml" xml:lang="en" lang="en">
3   <head>
4       <meta http-equiv="Content-Type"
           content="text/html; charset=utf-8" />
5       <title>Predefined Variables</title>
6   </head>
7   <body>
8   <?php # Script 1.5 - predefined.php

9   // Create a shorthand version of the
       variable names:
10  $file = $_SERVER['SCRIPT_FILENAME'];
11  $user = $_SERVER['HTTP_USER_AGENT'];
12  $server = $_SERVER['SERVER_SOFTWARE'];

13  // Print the name of this script:
14  echo "<p>You are running the
       file:<br /><b>$file</b>.</p>\n";

15  // Print the user's information:
16  echo "<p>You are viewing this page
       using:<br /><b>$user</b></p>\n";

17  // Print the server's information:
18  echo "<p>This server is running:
       <br /><b>$server</b>.</p>\n";

19  ?>
20  </body>
21  </html>
```

***

#### To use variables

**1.** Begin a new PHP document in your text editor or IDE, to be named `predefined.php`, starting with the initial HTML (**Script 1.5**):

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
  <title>Predefined Variables</title>
</head>
<body>
```

**2.** Add the opening PHP tag and the first comment:

```
<?php # Script 1.5 - predefined.php
```

From here on out, scripts will no longer comment on the creator, creation date, and so forth, although you should continue to document your scripts thoroughly. Scripts will, however, make a comment indicating the script’s number and filename for ease of cross-referencing (both in the book and when you download them from the book’s supporting Web site, **www.LarryUllman.com**).

**3.** Create a shorthand version of the first variable to be used in this script:

```
$file = $_SERVER['SCRIPT_FILENAME'];
```

This script will use three variables, each of which comes from the larger predefined `$_SERVER` variable. `$_SERVER` refers to a mass of server-related information. The first variable the script uses is `$_SERVER['SCRIPT_FILENAME']`. This variable stores the full path and name of the script being run (for example, `C:\Program Files\Apache\ htdocs\predefined.php`).

The value stored in `$_SERVER['SCRIPT_FILENAME']` will be assigned to the new variable `$file`. Creating new variables with shorter names and then assigning them values from `$_SERVER` will make it easier to refer to the variables when printing them. (It also gets around another issue you’ll learn about in due time.)

**4.** Create a shorthand version of two more variables:

```
$user = $_SERVER['HTTP_USER_AGENT'];
$server = $_SERVER['SERVER_SOFTWARE'];
```

`$_SERVER['HTTP_USER_AGENT']` represents the Web browser and operating system of the user accessing the script. This value is assigned to `$user`.

`$_SERVER['SERVER_SOFTWARE']` represents the Web application on the server that’s running PHP (e.g., Apache, Abyss, Xitami, IIS). This is the program that must be installed (see **Appendix A**) in order to run PHP scripts on that computer.

**5.** Print out the name of the script being run:

```
echo "<p>You are running the file:<br /><b>$file</b>.</p>\n";
```

The first variable to be printed is `$file`. Notice that this variable must be used within double quotation marks and that the statement also makes use of the PHP newline character (`\n`), which will add a line break in the generated HTML source. Some basic HTML tags—paragraph and bold—are added to give the generated page a bit of flair.

**6.** Print out the information of the user accessing the script:

```
echo "<p>You are viewing this page using:<br /><b>$user</b>.</p>\n";
```

This line prints the second variable, `$user`. To repeat what’s said in the fourth step, `$user` correlates to `$_SERVER['HTTP_USER_AGENT']` and refers to the operating system, browser type, and browser version being used to access the Web page.

**7.** Print out the server information:

```
echo "<p>This server is running: <br /><b>$server</b>.</p>\n";
```

**8.** Complete the PHP block and the HTML page:

```
?>
</body>
</html>
```

**9.** Save the file as `predefined.php`, place it in your Web directory, and test it in your Web browser.

![Image](graphics/01_figure_11_a.jpg)

The `predefined.php` script reports back to the viewer information about the script, the Web browser being used to view it, and the server itself.

***

Tip

If you have problems with this, or any other script, turn to the book’s corresponding Web forum (**www.LarryUllman.com/forums/**) for assistance.

***

***

Tip
