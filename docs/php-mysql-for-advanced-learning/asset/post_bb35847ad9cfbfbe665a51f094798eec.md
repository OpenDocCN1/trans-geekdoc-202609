
```
echo $row['name'] . "<br>";
echo $row['email'] . "<br>";
}
/* close connection */
mysqli_close($con);
?>
```

## Example 2: Using mysqli_fetch_array()

```
<?php
//Connect to database
$con = mysqli_connect("localhost", "root", "", "mydb");
//execute simple query
$result = mysqli_query("SELECT * FROM employee",$con);
while ($row = mysqli_fetch_array($result))
{
//access array with column number index
echo $row[0]. " " .$row[1];
}
mysqli_free_result($result);
?>
```

## Example 3: Display records (names) in drop down

```
<?php
//Connect to database
$con = mysqli_connect("localhost", "root", "", "mydb");
//execute simple query
$result = mysqli_query("SELECT * FROM employee",$con);
echo "<select style='width:150px'>";
while ($row = mysqli_fetch_array($result))
{

echo "<option>".$row[0]."</option>";
}

mysqli_free_result($result);
?>
```

## Example 4: Display MYSQL records in HTML Table

```
<?php
//Connecting to the database

$con = mysqli_connect("localhost", "root", "", "mydb");

//execute simple query

$result = mysqli_query("SELECT * FROM employee",$con);
?>

<table border="1" width="400" cellpadding="5">
<?php
while ($row = mysqli_fetch_assoc($result))
{
?>
<tr>
<td><?php echo $row['name']; ?></td>
<td><?php echo $row['email']; ?></td>
<td><?php echo $row['phone']; ?></td>
</tr>
<?php
}
?>
</table>
```

## Example 4: Basic Searching operation using MYSQL where clause

## HTML Form

```html
<html>
<head>
<title>Simple Search</title>
</head>
<body>
<form action="search-records.php" method="get">
Name : <input type="text" name="txtName" placeholder="Enter few letters">
<input type="submit" value="Search">
</form>
</body>
</html>
```

![](img/9ab4a56a650535285811bb802190e58f_90_0.png)

## Search.php

```php
<?php
$name=$_REQUEST['txtname'];
// Connecting to the database
$con = mysqli_connect("localhost", "root", "", "mydb");
//execute simple query
$result = mysqli_query("select * from employee where name like '%$name%' ",$con);

?>

<table border="1" width="400" cellpadding="5">

<?php

while ($row = mysqli_fetch_assoc($result))

{

?>

<tr>

<td><?php echo $row['name']; ?></td>

<td><?php echo $row['email']; ?></td>

<td><?php echo $row['phone']; ?></td>

</tr>

<?php

}

?>

</table>
```

## Notes

## Example

```
<?php
if(!file_exists("/docs/resume.txt"))
{
    die("File not found");
}
else
{
    $file = fopen("/docs/resume.txt","r");
}
?>
```

## Example:

```
<?php
$a = 0;
$b = 200;
$result = $b/$a;
echo "RESULT: ". $result;
?>
```

Output: Warning: Division by zero in ... on line 4

## Example:

```
<?php
echo "Hi lets learn PHP"
echo "<br/>This is another line";
?>
```

Output: Parse error: syntax error, unexpected 'echo' (T_ECHO), expecting ',' or ';' in ... on line 3

## **Some possible errors in PHP**

- E_ERROR - Fatal Run-time errors. Execution of the script is halted
- E_WARNING - Non-fatal errors. Execution is not halted
- E_PARSE - Compile-time parse errors.
- E_NOTICE - Run-time notices.
- E_ALL - All errors and warnings, except level E_STRICT
- E_CORE_WARNING - Non-fatal run-time errors. This occurs during PHP's initial start-up.

There are some different locations where we can control errors:

- In the php.ini file
- In the .htaccess file on your web server
- From your own PHP code.

We could do the same from our PHP code during runtime by calling the error_reporting() function as below:

```
error_reporting(E_ALL);
```

To turn on error logging and log the errors to our specific log file (instead of the default error log file, which is often the web server error log file)

```
log_errors = on
error_log = "/tmp/error.log"
```

## **Creating a Custom Error Handler:**

We simply create a special function that can be called when an error occurs in PHP. In the example we will send an e-mail with an error message, if a specific error occurs:

```php
<?php
//error handler function
function customError($errno, $errstr)
{
    echo "<b>Error:</b> [$errno] $errstr<br>";
    echo "Error Occurred";
    error_log("Error: [$errno] $errstr",1,
    "info@websjyoti.com","From: webmaster@websjyoti.com");
}

//set error handler
set_error_handler("customError",E_USER_WARNING);

//trigger error
$test=2;
if ($test>=1)
{
    trigger_error("Value must be 1 or below",E_USER_WARNING);
}
?>
```

## Explanation:

set_error_handler(): The default error handler for PHP is the built in error handler. We have made the function above the default error handler for the duration of the script. Since we want our custom function to handle all errors, the set_error_handler() only needed one parameter, a second parameter could be added to specify an error level.

## Example

set_error_handler("customError",E_USER_WARNING); trigger_error() function will raise error when an illegal input occurs.

## Using Include() Function:

Suppose that you want to print the same message on every page like your company details and address, or maybe today’s date. If you are placing the same coding on each page of your site that is not very efficient because-

- You are typing the same information over and over again, which is not the good approach.
- In the case of an update or a change, you have to make the change in every single page of your site which is very time consuming process.

A solution to this problem is to use an include() method. You take commonly used information and put it in a separate file. For example, if you have a set of variables that need to be use in every page on your site, you could define them once, in a single PHP file. Then, on each of your pages, you can include() it by referencing that file.

## Difference between Include and require:

The main difference between include and require statements in PHP is that if any error occurred include will raise an error message and then will continue the rest of the code placed in the page where as require will raise a fatal error and terminates execution.

Function require () throws an error (E_COMPILE_ERROR) and stop the script.

Function include () throws a warning (E_WARNING) but the script will continue.

## **require_once()**

function require_once is useful if the result of the code is necessary but subsequent inclusions would throw an error. That goes for scripts with functions for instance. If such a script would be included more than once an error would be thrown since functions cannot be redeclared.

## **include_once()**

Function include_once is useful in the case of including remote files and not wanting them to be included several times due to an HTTP overhead. This is also useful in payment gateway and process on e-commerce websites.

## Examples

```html
<html>

<head>

<title>My Web page</title>

</head>

<body>

<div class="header">

<?php
include_once "menu.php";
?>
</div>
<div class="footer">
<?php
include_once "menu.php";
?>
</div>
</body>
</html>
```

In this example you will see a warning when you attempt to recall file “menu.php”

## PHP Errors - Troubleshooting

Fatal error: Call to undefined function xyz() in localhost/test.php on line 2

Solution: This means that a PHP function that the current page needs cannot be found. Check carefully that all of the included files have been uploaded or replaced and that you have followed the installation instructions.

PHP Warning: include(abc.php): failed to open stream: No such file or directory in localhost/test.php on line 2

Solution: This warning tells you that an include file (included using PHP’s include syntax) was not found. If you get a warning or error message that a file could not be opened, then check that the
file referred to in the error message is there and that your path to it is correct.

Warning: move_uploaded_file(upload/logo.jpg) [function.move-uploaded-file]: failed to open stream: Permission denied in localhost/upload.php on line 32

**Solution:** This warning is an example of a permissions error. The script is trying to upload a file to a directory, but the directory doesn’t have enough permission for the file to be moved to it.
