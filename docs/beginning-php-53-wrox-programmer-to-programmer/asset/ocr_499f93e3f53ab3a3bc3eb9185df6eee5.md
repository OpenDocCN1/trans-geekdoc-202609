# # Solutions to Exercises

# ## Chapter 2
### Exercise Solution

The trick here is to make a second call to date(), passing in the appropriate characters to display the current date. Here's how you might write the script (including comments where appropriate):

```
<!DOCTYPE html PUBLIC "//W3C//DTD HTML 1.0 Strict//EN"
"http://www.w3.org/TR/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en" lang="=en">
<head>
  <title>Hello</title>
  <link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>
<?php

// Get the current time in a readable format
$currentTime = date("g:i:s a");

// Get the current date in a readable format
$currentDate = date("*M, j, Y*");

// Display greeting, time and date to the visitor
echo "Hello, world! The current time is $currentTime on $currentDate";
?>
</h1>
</body>
</html>
```