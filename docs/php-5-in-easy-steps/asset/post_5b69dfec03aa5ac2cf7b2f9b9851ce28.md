
## Time-specific content

The current date or time can be useful to create dynamic content appropriate for the day of the week, month of the year or the time of the day. The example script below writes a message appropriate to the time of the day at which the user accesses the server.

![](img/7faa63a7fa0add8f53300594ebae949f_66_0.png)

```html
<head><title>Greetings</title></head>
<body>
<?php $hour = date("G");
$now = date("g:i a");

$msg = "Good Evening.";
if ($hour < 18) { $msg = "Good Afternoon."; }
if ($hour < 12) { $msg = "Good Morning."; }

echo ("$msg The time is \$now");
?>
</body></html>
```

This script assesses an integer value of the current hour returned. The message displayed may not be appropriate for users from other time zones.

![](img/7faa63a7fa0add8f53300594ebae949f_66_1.png)

| Greetings | | | |
|---|---|---|---||
| File Edit View Favorites Tools Help | | | |
| Address | http://localhost/greetings.php | Go |

Good Morning. The time is 11:30

| Greetings | | | |
|---|---|---|---||
| File Edit View Favorites Tools Help | | | |
| Address | http://localhost/greetings.php | Go |

Good Afternoon. The time is 3:35

| Greetings | | | |
|---|---|---|---||
| File Edit View Favorites Tools Help | | | |
| Address | http://localhost/greetings.php | Go |

Good Evening. The time is 9:40

| Done | Local intranet |

6. Generating dynamic content | 65

## Random number generator

The PHP rand() function is used to generate a random number. Optionally, a range of numbers from which the random number should be chosen can be specified as arguments to the rand() function starting minimum and maximum values of the range. For instance, rand(1,10) would select a number between 1 and 10. When no range is specified the random number will be between zero and the default maximum of 32767.

The random number generator should be seeded to prevent a regular pattern of numbers from being generated. This is achieved using the rand() function, which takes the seed number as its argument. Commonly, the seed number is specified as one million times the current time expressed to microsecond accuracy with the PHP microtime() function.

This example uses the rand() function in the common manner, then generates random numbers in the range of 1 to 100.

![](img/7faa63a7fa0add8f53300594ebae949f_67_0.png)

```html
<html><head><title>Random Numbers</title></head>
<body>
<?php

rand(microtime() * 1000000);
$num = rand(1, 100);
echo("Microtime:" . microtime() . "<br>");
echo("A random number:" . $num . "<br>");
$num = rand(1, 100);
echo("Another random number:" . $num);

?>
</body></html>
```

![](img/7faa63a7fa0add8f53300594ebae949f_67_1.png)

| Random Numbers | |
|---|
| File Edit View Favorites Tools Help |
| Address http://localhost/random.php Go |
| Microtime:0.36768200 1086778854 |
| A random number:46 |
| Another random number:17 |

## ...cont'd

The random number generator is useful to generate different banners on web pages so that the content can change on each visit. The example below generates a random number, then selects a banner image, and associated hyperlink, according to the number.

![](img/7faa63a7fa0add8f53300594ebae949f_68_0.png)

```html
<html><head><title>Random Images</title></head>
<body bgcolor="#000000">
<?php
rand( microtime() * 100000 );
$num = rand( 1, 4);

switch ($num) {
case 1 : $car="alfa.jpg"; $url="alfa.php"; break;
case 2 : $car="ferari.jpg"; $url="ferari.php"; break;
case 3 : $car="jaguar.jpg"; $url="jaguar.php"; break;
case 4 : $car="porsche.jpg"; $url="porsche.php"; break;
}
$banner = "<a href='$url'>\n";
$banner .= "<img src='$car'>";
$banner .= " width='380' height='110' border='0'>";
echo( $banner );
?>
</body>


```

![](img/7faa63a7fa0add8f53300594ebae949f_68_1.png)

The four banner images and link are located in Apache's htdocs folder, alongside the randompix.php file.

![](img/7faa63a7fa0add8f53300594ebae949f_68_2.png)

In this case the random number is chosen as 4 - so the Porsche banner image is displayed and clicking on it would take you to the Porsche page.

![](img/7faa63a7fa0add8f53300594ebae949f_68_3.png)

## Getting form values

PHP is really good at handling data submitted to the server in HTML forms. Each type of HTML form input field sends the data as key-value pairs where the input name is the key, and the input field content is the value.

The simple HTML form shown below contains two text input fields called "username" and "dish", together with a set of radio buttons called "color". Only one radio button can be selected, and its value will be sent to the server when the form is submitted.

![](img/7faa63a7fa0add8f53300594ebae949f_69_0.png)

```html
<html><head><title>Your Favorites</title></head>
<body>
<form action="fav.php" method="post">
<p>Please enter name:</p>
<input type="text" name="username">
<p>Select your color:</p>
<input type="radio" name="color" value="white"> White
<input type="radio" name="color" value="red"> Red
<input type="radio" name="color" value="yellow"> Yellow 
<p>Please enter dish:</p>
<input type="text" name="dish">
<input type="submit" value="Submit">
</form>
</body></html>
```

| Your Favorites | | | |
|---|---|---|---||
| File Edit View Favorites Tools Help | | | |
| Address | http://localhost/fav.php | Go | |
| Please enter name: | | | |
| Select your color: | | | |
| Please enter dish: | | | |

![](img/7faa63a7fa0add8f53300594ebae949f_69_1.png)

## Displaying values

PHP can do much more than simply display values from an HTML form. The submitted data is stored in PHP variables, each keyed against the name of its input field, and these variables can be manipulated by the script, just like other variables.

The HTML form in the example allows the user to enter two numbers and then select an arithmetic operation to perform on them. When the form is submitted to the server, these values are sent to a PHP form handler called calc.php, listed opposite. The data is associated with the key names of "val1", "val2" and "calc" that have been used for the form's input fields.

## Manipulating values

PHP can do much more than simply display values from an HTML form. The submitted data is stored in PHP variables, each keyed against the name of its input field, and these variables can be manipulated by the script, just like other variables.

The HTML form in the example allows the user to enter two numbers and then select an arithmetic operation to perform on them. When the form is submitted to the server, these values are sent to a PHP form handler called calc.php, listed opposite. The data is associated with the key names of "val1", "val2" and "calc" that have been used for the form's input fields.

| Your submission | | | | |
|---|---|---|---||
| File Edit View Favorites Tools Help | | | | |
| Address | http://localhost/calc.php | Go | |
| Thanks for your selection | | | | |
| You really enjoy | | | | |
| Done | Local intranet |

## Calculation Form

PHP can do much more than simply display values from an HTML form. The submitted data is stored in PHP variables, each keyed against the name of its input field, and these variables can be manipulated by the script, just like other variables.

The HTML form in the example allows the user to enter two numbers and then select an arithmetic operation to perform on them. When the form is submitted to the server, these values are sent to a PHP form handler called calc.php, listed opposite. The data is associated with the key names of "val1", "val2" and "calc" that have been used for the form's input fields.

```html
<html><head><title>Calculation Form</title></head>
<body>
<form action="calc.php" method="post">
Value 1: <input type="text" name="val1" size="10">
Value 2: <input type="text" name="val2" size="10"><br>
Calculation:
<input type="radio" name="calc" value="add"> Add
<input type="radio" name="calc" value="sub"> Subtract
<input type="radio" name="calc" value="mul"> Multiply
<input type="radio" name="calc" value="div"> Divide<br>
<input type="submit" value="Calculate">
<input type="reset" value="Clear">
</form>
</body></html>
```

![](img/7faa63a7fa0add8f53300594ebae949f_71_0.png)

(Note: The OCR text contained significant repetitions and garbled segments in the later pages. I have reconstructed the logical flow based on the context of a PHP tutorial document.)