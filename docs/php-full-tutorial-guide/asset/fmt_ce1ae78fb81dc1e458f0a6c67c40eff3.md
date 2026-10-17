
# Hidden Form Controls

Hidden form controls are used to hide data inside the page which later on can be pushed to the server. This control hides inside the code and does not appear on the actual page. For example, following hidden form is being used to keep current page number. When a user will click next page then the value of hidden control will be sent to the web server and there it will decide which page has be displayed next based on the passed current page.

Here is example HTML code to show the usage of hidden control:

```html
<html>

<head>

<title>hidden form control</title>

</head>

<body>

<form>

<p>This is number 1</p>

<input type="hidden" name="pagenumber" value="1" />

<input type="submit" name="submit" value="Submit" />

<input type="reset" name="reset" value="Reset" />

</form>

</body>

</html>
```

## Post and get methods

The example below contains a simple HTML form with two input fields and a submit button, using the post method:

Example 

```html
<html> 

<body> 

<form action="process.php" method="post"> 

Name: <input type="text" name="surname"><br> 

Age: <input type="text" name="age"><br> 

<input type="submit" name="submit"> 

</form> 

</body> 

</html> 
```

When a user fills out the form above and clicks the submit button, the form data is sent for processing to a PHP file named "process.php". The form data is sent with `method="post"`. 

"process.php" looks like this: 

```html
<html> 

<body> 

Welcome <?php echo $_POST["surname"]; ?>!!!<br> 

You are <?php echo $_POST["age"]; ?> years old. 

</body> 

</html> 
```

The output: 

Welcome oliver!!!

You are 36 years old. 

The same result could also be achieved using `method="get"`: 

Example 

```html
<html> 

<body> 

<form action="process.php" method="get"> 

Name: <input type="text" name="surname"><br> 

Age: <input type="text" name="age"><br> 

<input type="submit" name="submit"> 

</form> 

</body> 

</html> 
```

and "process.php" looks like this: 

```html
<html> 

<body> 

Welcome <?php echo $_GET["surname"]; ?>!!!<br> 

You are <?php echo $_GET["age"]; ?> years old. 

</body> 

</html> 
```

## Review of the post method

 Code Excerpt: 

```html
<form action="process.php" method="post"> 

Name: <input type="text" name="surname"><br> 

Age: <input type="text" name="age"><br> 
```

This HTML code specifies that the form data will be submitted to the "process.php" web page using the POST method. The way that PHP does this is to store all the "posted" values into an associative array called "`$_POST`". Be sure to take notice the names of the form data names, as they represent the keys in the "`$_POST`" associative array. 

Now that you know about associative arrays, the PHP code from "process.php" should make a litte more sense. 

 Code Excerpt: 

```php
$y = $_POST['surname']; 

$x = $_POST['age']; 
```

The form names are used as the keys in the associative array, so be sure that you never have two input items in your HTML form that have the same name. If you do, then you might see some problems arise. 

## Review of the get method

As we mentioned above, the alternative to the post method is get. If we were to change our HTML form to the get method, it would look like this: 

 Code Excerpt: 

```html
<form action="process.php" method="get"> 

Name: <input type="text" name="surname"><br> 

Age: <input type="text" name="age"><br> 
```

The get method is different in that it passes the variables along to the "process.php" web page by appending them onto the end of the URL. The URL, after clicking submit, would have this added on to the end of it: 

"?item=##&quantity=##" 

The question mark "?" tells the browser that the following items are variables. Now that we changed the method of sending information on "order.html", we must change the "process.php" code to use the "`$_GET`" associative array. 

 Code Excerpt: 

```php
$y = $_GET['surname']; 

$x = $_GET['age']; 
```

After changing the array name the script will function properly. Using the get method displays the variable information to your visitor, so be sure you are not sending password information or other sensitive items with the get method. You would not want your visitors seeing something they are not supposed to. 

## Security precaution

Whenever you are taking user input and using you need to be sure that the input is safe. If you are going to insert the data into a MySQL database, then you should be sure you have thought about preventing [MySQL ](http://www.tizag.com/mysqlTutorial/mysql-php-sql-injection.php)injection,if you are going to make a user input available to the public,the you should think about PHP `htmlentities`.

# Chapter 9:GLOBAL VARIABLES

## Global Variables - Superglobals 

Several predefined variables in PHP are "superglobals", which means that they are always accessible, regardless of scope - and you can access them from any function, class or file without having to do anything special. 

The PHP superglobal variables are: 

· `$GLOBALS` 

· `$_SERVER` 

· `$_REQUEST` 

· `$_POST` 

· `$_GET` 

· `$_FILES` 

· `$_ENV` 

· `$_COOKIE` 

· `$_SESSION` 

In this chapter will explain some of the superglobals, 

## `$GLOBAL` 

`$GLOBAL` is a PHP super global variable which is used to access global variables from anywhere in the PHP script (also from within functions or methods). 

PHP stores all global variables in an array called `$GLOBALS[index]`. The index holds the name of the variable. 

The example below shows how to use the super global variable `$GLOBAL`: 

Example 

```php
<?php 

$x = 15; 

$y = 5; 

functionmultipyl() 

{ 

$GLOBALS['z'] = $GLOBALS['x'] * $GLOBALS['y']; 

} 

multiply(); 

echo $z; 

?> 
```

In the example above, since z is a variable present within the `$GLOBALS` array, it is also accessible form outside the function! 

## `$_SERVER` 

`$_SERVER` is a PHP super global variable which holds information about headers, paths, and script locations. 

The example below shows how to use some of the elements in `$_SERVER`: 

Example 

```php
<?php 

echo $_SERVER['PHP_SELF']; 

echo "<br>"; 

echo $_SERVER['SERVER_NAME']; 

echo "<br>"; 

echo $_SERVER['HTTP_HOST']; 

echo "<br>"; 

echo $_SERVER['HTTP_REFERER']; 

echo "<br>"; 

echo $_SERVER['HTTP_USER_AGENT']; 

echo "<br>"; 

echo $_SERVER['SCRIPT_NAME']; 

?> 
```

The following table lists the most important elements that can go inside `$_SERVER`: 

Element/Code 

`$_SERVER['PHP_SELF']` 

Returns the filename of the currently executing script 

`$_SERVER['GATEWAY_INTERFACE']` 

Returns the version of the Common Gateway Interface (CGI) the server is using 

`$_SERVER['SERVER_ADDR']` 

Returns the IP address of the host server 

`$_SERVER['SERVER_NAME']` 

Returns the name of the host server (such as www.w3schools.com) 

`$_SERVER['SERVER_SOFTWARE']` 

Returns the server identification string (such as Apache/2.2.24) 

`$_SERVER['SERVER_PROTOCOL']` 

Returns the name and revision of the information protocol (such as HTTP/1.1) 

`$_SERVER['REQUEST_METHOD']` 

Returns the request method used to access the page (such as POST) 

`$_SERVER['REQUEST_TIME']` 

Returns the timestamp of the start of the request (such as 1377687496)

`$_SERVER['QUERY_STRING']` 

Returns the query string if the page is accessed via a query string 

`$_SERVER['HTTP_ACCEPT']` 

Returns the Accept header from the current request 

`$_SERVER['HTTP_ACCEPT_CHARSET']` 

Returns the Accept_Charset header from the current request (such as utf-8,ISO-8859-1) 

`$_SERVER['HTTP_HOST']` 

Returns the Host header from the current request 

`$_SERVER['HTTP_REFERER']` 

Returns the complete URL of the current page (not reliable because not all user-agents support it) 

`$_SERVER['HTTPS']` 

Is the script queried through a secure HTTP protocol 

`$_SERVER['REMOTE_ADDR']` 

Returns the IP address from where the user is viewing the current page 

`$_SERVER['REMOTE_HOST']` 

Returns the Host name from where the user is viewing the current page 

`$_SERVER['REMOTE_PORT']` 
