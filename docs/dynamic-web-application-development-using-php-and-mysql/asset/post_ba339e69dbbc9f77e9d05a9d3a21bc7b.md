
```
```php
echo "<td><img src='graphics/$strSecond.gif' alt='$strSecond'/></td>";
echo "<td><img src='graphics/$strThird.gif' alt='$strThird'/></td>";
echo "</tr></table>";

if ($strFirst == $strSecond && $strFirst == $strThird)
    echo "<h2>You Win!</h2>";
?>
<form action='<?php echo $_SERVER["PHP_SELF"]; ?>' method='post'>
<p><input type='submit' value='spin'/></p>
</form>
```
```

The script begins by declaring an array of fruits:

```
```php
$arrFruits = array (1=>"apple", 2=>"orange", 3=>"lemon", 4=>"plum");
```
```

Function randomNumber() is defined to generate random numbers:

```
```php
function randomNumber ($intStart, $intEnd) {
    srand( (double) microtime() * 1000000);
    $intRandVal = rand($intStart,$intEnd);
    return $intRandVal;
}
```
```

Three random numbers between 1 and 4 are generated from invoking function randomNumber() and the corresponding array item is stored in its corresponding variable:

```
```php
$strFirst=$arrFruits[randomNumber(1,4)];
$strSecond=$arrFruits[randomNumber(1,4)];
$strThird=$arrFruits[randomNumber(1,4)];
```
```

The fruit images are output inside a simple table:

```
```php
echo "<h2>Try your luck at the fruit machine...</h2>";
echo "<table width='450'><tr>";
echo "<td><img src='graphics/$strFirst.gif' alt='$strFirst'/></td>";
echo "<td><img src='graphics/$strSecond.gif' alt='$strSecond'/></td>";
echo "<td><img src='graphics/$strThird.gif' alt='$strThird'/></td>";
echo "</tr></table>";
```
```

An ‘if’ construct checks if the fruits are the same:

```
```php
if ($strFirst == $strSecond && $strFirst == $strThird)
    echo "<h2>You Win!</h2>";
```
```

![](img/b2471264f405d17994ef173e4b9cec92_413_0.png)

### FIGURE 13.9 Fruit machine

![](img/b2471264f405d17994ef173e4b9cec92_414_0.png)

A simple form is used to allow the user to ‘spin’ the fruits again:

```
<form action='<?php echo $_SERVER["PHP_SELF"]; ?>' method='post'>
<p><input type='submit' value='spin'/></p>
</form>
```

The output from the above script is illustrated in Figure 13.9.

## 13.6 Page redirection and referral

Quite often you may wish to build a secure web page. You may create a login form and require that a user enters their username and password. You may check that these are correct by comparing them to a file or database (we shall show you how to do this later). If the username and password are valid then you may wish to direct the user to a new page for them to access. Otherwise the user will remain on the username and password form page.

User redirection can be performed using the ‘Location:’ string in the header() function:

```
header ("Location: webpage");
```

This basic form of web security is illustrated in Figure 13.10.

| NOTE | Header functions, like those of cookies, must be called before any output is sent to the browser. |

### FIGURE 13.10 Simple login and redirection

![](img/b2471264f405d17994ef173e4b9cec92_415_0.png)

Let's create a simple page to illustrate redirection:

```
<?php
// File: example13-26.php
if(isset($_POST["submit"])) {
    $strUserPass = array ( "john" => "red",
        "simon" => "green",
        "liz" => "blue",
        "david" => "yellow");
    if (array_key_exists($_POST["strUsername"], $strUserPass) )
        if ($strUserPass[$_POST["strUsername"] ] ==
            $_POST["strPassword"])
            header("location: example13-27.php");
        else
            echo "<h1>Incorrect Username and/or password!</h1>";
}
?>
<form name="form1" method="post" action="">
<p>
<label for="strUsername">Username: </label>
<input type="text" name="strUsername" id="strUsername"/></p>
<p>
<label for="strPassword">Password: </label>
```

```
```html
<input type="password" name="strPassword" id="strPassword"/></p>
<p><input type="submit" name="submit" /></p>
</form>
```
```

The above script determines if a form has been submitted and if so defines an array of user-name and passwords:

```
```php
if(isset($_POST["submit"]) ) {
    $strUserPass = array ( "john" => "red",
                           "simon" => "green",
                           "liz" => "blue",
                           "david" => "yellow");
```
```

Next function array_key_exists() is used to check if the username key is present in the array. The function looks like this:

```
```php
trueFalse = array_key_exists(Arraykey, Array)
```
```

In the script we write:

```
```php
if (array_key_exists($_POST["strUsername"], $strUserPass) )
```
```

It then checks to see if the entered username and passwords match and if so redirects the user to a new page:

```
```php
if ($strUserPass[$_POST["strUsername"]] === $_POST["strPassword"])
    header("location: example13-28.php");
```
```

Otherwise an error message is generated and the form is redisplayed:

```
```php
else
    echo "<h1>Incorrect Username and/or password!</h1>";
```
```

The output from the above script for an incorrect username and password is illustrated in Figure 13.11.

We shall also need to create a simple page to be redirected to:

```
```php
<?php
// File: example13-27.php

echo "<h1>Well done, you are correctly logged in!</h1>";
?>
```
```

The output from the above script is shown in Figure 13.12.

All appears to be working well, however consider what happens if a user simply bypasses the login script and loads ‘example13-27.php’ directly. It works and the user has bypassed our security.

Header redirects are like cookies and sessions in that they are part of the HTTP header, so the header() function must be called before any output is sent to the browser. If you were to include all of the correct DOCTYPE and header information in the above script the creation of a cookie still needs to come before this. Therefore the full ‘standard conforming’ script looks like this:

```
```
<?php
// File: example13-28.php

if ($_SERVER["HTTP_REFERER"]
!= "http://localhost/book/chapter13/example13-26.php")
header("location: example13-26.php");
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
"http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
<head>
<title>PHP Script</title>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1" />
</head>
<body>
<h1>Well, done you are correctly logged in!</h1>
</body>
</html>
```
```

## Exercises

13.1 Write a script to implement a function which will convert centimetres to inches and inches to centimetres. The formula for conversion is:

1 centimeter = 0.393700787 inches

13.2 Rewrite the Roman to Arabic date conversion program that you were presented with in an earlier lesson so that it makes use of functions.

13.3 Create a script which implements the ‘Drunk on a Bridge’ problem. Basically the drunk starts in the middle of the bridge and randomly staggers to the left or right until he reaches the left or right hand side of the bridge. The size of the bridge is up to you.

The drunk and bridge graphics can be very simple:

### FIGURE 13.13 Drunk on a bridge

![](img/b2471264f405d17994ef173e4b9cec92_419_0.png)

13.4 Write a script which amends ‘example13–26.php’ so that the username and passwords are stored in and read from a file.

## SUMMARY

In this chapter we began by examining how to create our own user-defined functions. We introduced the concept of variable scope and illustrated how functions can receive arguments and return a value. Following this we introduced file ‘include’ statements and illustrated how they can be used to divide up complex scripts and assist in component reuse. We then introduced dates, times and random numbers and explained why they are useful. We concluded the chapter by examining how to check the referrer web page and how to redirect a web page to another automatically.

## References and further reading

Gilfillan, I. (2002) Date and Time in PHP http://www.wdvl.com/Authoring/Languages/PHP/Date_Time/
Hioxindia.com. Dates and Time in PHP http://www.hscripts.com/tutorials/php/dateAndTime.php
Wikipedia. Subroutines (Functions) http://en.wikipedia.org/wiki/Subroutine
