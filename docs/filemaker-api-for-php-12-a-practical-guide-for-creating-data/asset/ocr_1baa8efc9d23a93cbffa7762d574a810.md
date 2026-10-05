http://en.wikipedia.org/wiki/Haversine_formula

or

The math for the Distance calculation involves some fairly nasty Trigonometry. Since a math lesson isn't the point of it I'll let you understand the math on your own, knowing that you can use the calculation as and it will work correctly. The only thing I will say about the Distance calculation is that it calculates distance in miles. If you use it in kilometers, you can change the constant in the calculation from 3959 to 6371.

The general steps in the process are as follows: the user submits with their current address or zip code and the next. Next, the PHP class contains the or zip code to Latitude and Long values. The more specific your request, the more accurate the lat/long values. That's obvious. These values, along with the user's requested date are submitted to the Store Locator script in the database. The script inserts values into the SearchLat, SearchLon, and Distance fields to acquire a found set of records. The records are sorted by the date, returned to the web page, and finally displayed to the user.

StoreLocator.php

There are two main processes to make this solution work. First is the PHP page. Second is the Store Locator. It's more efficient to describe each one separately, so we'll start with the StoreLocator.php page. Always start by including the connection to the database.

```
<php
require_once ('FileMaker.php');
$fm = new FileMaker();
$fm->setProperty('database', StoreLocator);
$fm->setProperty('hostname', 'http://127.0.0.1/');
$fm->setProperty('username', 'Admin');
$fm->setProperty('password', '1234');
```

You'll also need to include the two required classes included for you in the download file. GoogleMap.php contains all the code to connect to the Google Map API. You technically don't need to do anything to this. However, if you look through it you'll notice that you can configure any feature that is available through the API by changing the value from false to true. Most features are turned on by default in this file. I can't say enough regarding the simplicity of control over the Google Map API. What would you do - change values from false to true or handle hundreds of lines of code from Google? Next is the JSMin.php file which is all. Again, my hat is off to Brad as he ported all the code to PHP. You don't have to code any JavaScript. It just works!

```
include_once('GoogleMap.php');
include_once('JSMin.php');
```

Next, create the form for you by using the PHP_SELF dynamic shortcut to point the form back to the same page. After that, you can set your distance popup menu with any values that make sense for your solution.

```
<html>
<head>
</head>
<body>
<form action="<?php echo \$_SERVER['PHP_SELF'];?>" method="get" id="search">
Enter your address (Address, City, State) or Zip Code:
<br>
<input name="search" type="text">
<br>
Distance (miles):
<select name="distance">
<option value="5" selected>5</option>
<option value="10">10</option>
?>
```

303