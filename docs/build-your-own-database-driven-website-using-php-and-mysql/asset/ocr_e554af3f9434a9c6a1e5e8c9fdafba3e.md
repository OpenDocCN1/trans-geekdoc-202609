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
<p>?php echo("This is a <b>test</b>!" ); ? ></p>
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

You may wonder why we need to surround the string of text with both parentheses and quotes. Quotes are used to mark the beginning and end of strings of text in PHP, so their presence is fully justified. The parentheses serve a dual purpose. First, they indicate that echo is a function that you want to call. Second, they mark the beginning and end of a list of "parameters" that you wish to provide, in order to tell the function what to do. In the case of the echo function, you only need to provide the string of text that you want to appear on the page. Later on, we'll look at functions that take more than one parameter (and we'll separate those parameters with commas),