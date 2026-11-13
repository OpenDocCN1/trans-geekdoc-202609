
the Web server must follow before it can proceed to the next. PHP statements, like those in the above-mentioned languages, are always terminated by a semicolon (;).

This is a typical PHP statement:

```
echo( "This is a <b>test</b>!" );
```

This statement invokes a built-in function called echo and passes it a string of text: This is a <b>test</b>! Built-in functions can be thought of as things that PHP knows how to do without us having to spell out the details. PHP has a lot of built-in functions that let us do everything from sending email, to working with information that's stored in various types of databases. The echo function, however, simply takes the text that it's given, and places it into the HTML code of the page at the current location. Consider the following (echo.php in the code package):

```
<html>
<head>
<title> Simple PHP Example </title>
</head>
<body>
<p><?php echo("This is a <b>test</b>!" ); ?></p>
</body>
</html>
```

If you paste this code into a file called echo.php (or echo.php3, if your Web host has not configured .php files to be recognized as PHP scripts) and place it on your Web server, a browser that views the page will see this:

```
<html>
<head>
<title> Simple PHP Example </title>
</head>
<body>
<p>This is a <b>test</b>!</p>
</body>
</html>
```

Notice that the string of text contained HTML tags (<b> and </b>), which is perfectly acceptable.

You may wonder why we need to surround the string of text with both parentheses and quotes. Quotes are used to mark the beginning and end of strings of text in PHP, so their presence is fully justified. The parentheses serve a dual purpose. First, they indicate that echo is a function that you want to call. Second, they mark the beginning and end of a list of "parameters" that you wish to provide, in order to tell the function what to do. In the case of the echo function, you only need to provide the string of text that you want to appear on the page. Later on, we'll look at functions that take more than one parameter (and we'll separate those parameters with commas), and we'll consider functions that take no parameters at all (for which we'll still need the parentheses, though we won't type anything between them).

## Variables and Operators

Variables in PHP are identical to variables in most other programming languages. For the uninitiated, a variable is a name given to an imaginary box into which any value may be placed. The following statement creates a variable called $testvariable (all variable names in PHP begin with a dollar sign) and assigns it a value of 3:

```
$testvariable = 3;
```

PHP is a loosely typed language. This means that a single variable may contain any type of data (be it a number, a string of text, or some other kind of value), and may change types over its lifetime. So the following statement, if it appears after the statement above, assigns a new value to our existing $testvariable. In the process, the variable changes type: where it used to contain a number, it now contains a string of text:

```
$testvariable = "Three";
```

The equals sign we used in the last two statements is called the **assignment operator**, as it is used to assign values to variables. Other operators may be used to perform various mathematical operations on values:

```
$testvariable = 1 + 1;   // Assigns a value of 2.
$testvariable = 1 - 1;   // Assigns a value of 0.
$testvariable = 2 * 2;   // Assigns a value of 4.
$testvariable = 2 / 2;   // Assigns a value of 1.
```

The lines above each end with a comment. Comments are a way to describe what your code is doing - they insert explanatory text into your code, and tell the PHP interpreter to ignore it. Comments begin with // and they finish at the end of the same line. You might be familiar with /* */ style comments in other languages - these work in PHP as well. I'll be using comments throughout the rest of this book to help explain what the code I present is doing.

Now, to get back to the four statements above, the operators we used here allow you to add, subtract, multiply, and divide numbers. Among others, there is also an operator that sticks strings of text together, called the **concatenation operator**:

```
$testvariable = "Hi " . "there!"; // Assigns a value of
"Hi there!".
```

Variables may be used almost anywhere that you use an actual value.
Consider these examples:

```
$var1 = "PHP"; // Assigns a value of "PHP" to $var1
$var2 = 5; // Assigns a value of 5 to $var2
$var3 = $var2 + 1; // Assigns a value of 6 to $var3
$var2 = $var1; // Assigns a value of "PHP" to $var2
echo($var1); // Outputs "PHP"
echo($var2); // Outputs "PHP"
echo($var3); // Outputs 6
echo($var1 . " rules!"); // Outputs "PHP rules!"
echo("$var1 rules!"); // Outputs "PHP rules!"
echo('$var1 rules!'); // Outputs '$var1 rules!'
```

Notice the last two lines especially. You can include the name of a variable right inside a text string, and have the value inserted in its place if you surround the string with double quotes. This process of converting variable names to their values is known in technical circles as variable interpolation. However, as the last line demonstrates, a string surrounded with single quotes will not interpolate variable names within the string.

## User Interaction and Forms

For many applications of PHP, the ability to interact with users who view the Web page is essential. Veterans of JavaScript tend to think in terms of event handlers, which let you react directly to the actions of the user - for example, the movement of the mouse over a link on the page. Server-side scripting languages such as PHP have a more limited scope when it comes to user interaction. As PHP code is activated when a page is requested from the server, user interaction can only occur in a back-and-forth fashion: the user sends requests to the server, and the server replies with dynamically generated pages.

The key to creating interactivity with PHP is to understand the techniques we can use to send information about a users’ interaction along with their request for a new Web page. PHP makes this fairly easy, as we’ll now see.

The simplest method we can use to send information along with a page request uses the URL query string. If you've ever seen a URL with a question mark following the filename, you've witnessed this technique in use. Let's look at an easy example. Create a regular HTML file called welcome.html (no .php file extension is required, since there will be no PHP code in this file) and insert this link:

```
<a href="welcome.php?name=kevin"> Hi, I'm Kevin! </a>
```

This is a link to a file called welcome.php, but as well as linking to the file, we're also passing a variable along with the page request. The variable is passed as part of the "query string", which is the portion of the URL that follows the question mark. The variable is called name and its value is Kevin.

To restate, we have created a link that loads welcome.php, and informs the PHP code contained in the file that name equals Kevin.

To really understand the results of this, we need to look at welcome.php. Create it as a new HTML file, but this time note the .php extension - this tells the Web server that it can expect to interpret some PHP code in the file. If your Web server is not configured to accept .php as a file extension for PHP files, you may have to call it welcome.php3 instead (in which case you'll also want to adjust the link above accordingly). In the body of this new file, type:

```
<?php
echo ( "welcome to our web site, $name!" );
?>
```

Now, if you use the link in the first file to load this second file, you'll see that the page says "Welcome to our Web site, Kevin!" The value of the variable passed in the query string of the URL was automatically placed into a PHP variable called $name, which we used to display the value passed as part of a text string.

You can pass more than one value in the query string if you want to. Let's look at a slightly more complex version of the same example. Change the link in the HTML file to read as follows (this is welcome2.html in the code archive located at http://www.sitepoint.com/books/):

```
<a href="welcome.php?firstname=Kevin&lastname=Yank"> Hi,
I'm Kevin Yank! </a>
```

This time, we'll pass two variables: firstname and lastname. The variables are separated in the query string by an ampersand (&). You can pass even more variables by separating each name=value pair from the next with an ampersand.

As before, we can use the two variable values in our welcome.php file (this is welcome2.php in the code archive located at http://www.sitepoint.com/books/):

```
<?php
echo ( "welcome to my website, $firstname $lastname!" );
?>
```

This is all well and good, but we still have yet to achieve our goal of true user interaction, where the user can actually enter arbitrary information and have it processed by PHP. To continue with our example of a personalized welcome message, we'd like to allow the user to actually type his or her name and have it appear in the message. To allow the user to type in a value, we'll need to use an HTML form.

Here's the code (welcome3.html):
