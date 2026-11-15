# Chapter 15

# Exercise 1 Solution

Numbers_Roman is a very simple PEAR package. You can find its documentation at http://pear.php.net/package/Numbers_Roman/docs/latest/.

The first step is to install the package in the usual way:

```
$ pear install Numbers_Roman
downloading Numbers_Roman-1.0.2.tgz ...
Starting to download Numbers_Roman-1.0.2.tgz (6,210 bytes)
.....done: 6,210 bytes
install ok: channel://pear.php.net/Numbers_Roman-1.0.2
```

The package provides a class with just two static methods:

+   Numbers_Roman::toNumber() converts the supplied Roman number to its Arabic equivalent.

+   Numbers_Roman::toNumeral() converts the number supplied as the first argument to Roman numerals. The second argument defaults to true, which displays the numerals in uppercase; set it to false to display them in lowercase. The third argument also defaults to true, and specifies that HTML markup for displaying the numbers with overscores should be output if the number is above 3999 (as required by the Roman numeral system). Set it to false to turn off any overscore markup.

For this exercise you want to use Numbers_Roman::toNumeral(). All you need to do is create a loop that moves through the integers 1 to 100, calling Numbers_Roman::toNumeral() for each integer and outputting the result:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>1 to 100 in Roman numerals</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>

<h1>1 to 100 in Roman numerals</h1>
<p>

<?php

require_once( "Numbers/Roman.php" );

for ( $i=1; $i<=100; $i++ ) {
    echo Numbers_Roman::toNumeral( $i, true, true ) . "<br />";
}
?>

</p>
</body>
</html>
```