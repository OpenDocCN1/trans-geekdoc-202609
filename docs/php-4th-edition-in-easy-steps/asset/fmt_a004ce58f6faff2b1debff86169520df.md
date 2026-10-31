
## String Trimming, Padding and Splitting

```php
echo ‘<hr>Trimmed String : ‘.trim( $str, ‘|’ ) ;
$pad = str_pad( $str , 30 , ‘*’ , STR_PAD_LEFT ) ;
echo “<hr>Padded String : $pad” ;
echo ‘<hr>Split String : ‘ ;
$token = strtok( $str , ‘ ‘ );
while ( $token )
{
echo “$token … “ ; $token = strtok( ‘ ‘ ) ;
}
?>
```

![image](images/3bl.jpg)
Now, add a statement to display a 30-character version of the string, padded with asterisks at the beginning

![image](images/4bl.jpg)
Finally, add statements to split the string around spaces and display each individual part separated by an … ellipsis

![image](images/5bl.jpg)
Save the document in your web server’s `/htdocs` directory as `format.php` then open the page via HTTP to see the string formatted in several ways

## Making dates

![image](images/pg100_1.jpg)
The PHP `date()` function will return a date string when called, but requires a string argument to specify a format for the date string. This format string can comprise a series of letter options for date and time. For example, `date( ‘n/j/y’ )` might return “4/22/16”. Popular options are listed below along with a brief description:

| Option | Description | Example |
| --- | --- | --- |
| Y | Year as four digits | 2023 |
| y | Year as two digits | 14 |
| n | Month as one or two digits | 7 |
| m | Month as two digits | 07 |
| F | Month full name | February |
| M | Month name as three letters | Feb |
| j | Day as one or two digits | 4 |
| d | Day as two digits | 04 |
| l | Weekday full name | Monday |
| D | Weekday as three letters | Mon |
| S | Ordinal suffix as two letters | th |
| H | Hour in 24-hour format | 14 |
| i | Minutes | 45 |
| s | Seconds | 30 |
| a | Ante or post meridiem | am |

![image](images/snake.jpg)
The weekday full name option is a lowercase “L”.

By default, the timezone is set to the Universal Time Clock (UTC) but you can set it to your own timezone by specifying it as an argument to the `date_default_timezone_set()` function, and see the currently-set timezone with `date_default_timezone_get()`.

You may also create your own timestamp using the intelligent `strtotime()` function. This can accept a date string argument and return a timestamp that can be supplied as an optional second argument to the `date()` function. The argument specified to `strtotime()` can be a regular text date, such as “July 4, 2023”. Additionally, you can specify an argument such as “yesterday”, “+3months” or “next Wednesday” and the `strtotime()` function will try to figure it out and return an appropriate timestamp.

![image](images/hot.jpg)
You can discover more `date()` function options in the PHP manual online at [php.net/manual](http://www.php.net/manual)

![image](images/1bl.jpg)
Begin a PHP script with statements to display the current date, day, time and current default timezone

```php
<?php
echo ‘Date : ‘.date( ‘jS F Y’ ).’<br>’ ;
echo ‘Day : ‘.date( ‘l’ ).’<br>’ ;
echo ‘Time : ‘.date( ‘h:i:s a’ ).’<br>’ ;
echo ‘Timezone : ‘.date_default_timezone_get().’<hr>’ ;
```

![image](images/commonbl.jpg)

`date.php`

![image](images/2bl.jpg)
Next, add statements to change the default timezone and display a confirmation, then show the current time there

```php
date_default_timezone_set( ‘America/New_York’ ) ;
echo ‘Timezone now : ‘.date_default_timezone_get() ;
echo ‘<br>Time now : ‘.date( ‘h:i:s a’ ).’<hr>’ ;
```

![image](images/3bl.jpg)
Now, add statements to create a timestamp for the next day, then display its day name and date

```php
$d = strtotime( ‘tomorrow’ ) ;
echo ‘Tomorrow : ‘.date( ‘l, jS F Y’ , $d ).’<br>’ ;
```

![image](images/4bl.jpg)
Finally, add statements to create a timestamp for a memorable date, then display its month and day number

```php
$d = strtotime( ‘July 11, 1994’ ) ;
echo ‘David\'s Birthday : ‘.date( ‘F jS’ , $d ) ;
?>
```

![image](images/5bl.jpg)
Save the document in your web server’s `/htdocs` directory as `date.php` then open the page via HTTP to see the date strings formatted by the options

![image](images/pg101_1.jpg)

![image](images/hot.jpg)
Notice that you can include separator characters such as `:` and `/` in the format string.

![image](images/forget.jpg)
Some countries prefer date order of M/D/Y while others prefer D/M/Y so you can choose your preferred date format options.

## Encoding entities

![image](images/pg102_1.jpg)
There are two PHP functions available to encode HTML code, so that all characters of special significance or unusual characters are replaced by “entity” equivalents. The `htmlentities()` function encodes all characters below, which each have an entity equivalent:

![image](images/pg102_2.jpg)
Unless you are concerned about non-English language characters, it is generally preferable to use the alternative `htmlspecialchars()` function to encode only characters of special HTML significance:

• `&` ampersand – becomes `&amp;`
• `"` double quote – becomes `&quot;`
• `'` single quote – becomes `&#039;`
• `<` less than – becomes `&lt;`
• `>` greater than – becomes `&gt;`

![image](images/hot.jpg)
Call the PHP function `get_html_translation_table()` with the constant argument of `HTML_ENTITIES` or `HTML_SPECIALCHARS` to return an array of all represented characters.

One good reason to encode HTML snippets with PHP is to prevent malicious JavaScript code being executed unintentionally by the web browser. Encoding HTML tags into entities ensures that the HTML `<script>` tag will not be recognized, so its JavaScript code contents will not be executed:

![image](images/1bl.jpg)
Create a PHP script with statements to initialize a variable with an HTML snippet and display its value

```php
<?php
$html = ‘<script>window.location="index.html"</script>’ ;
// Statement to be inserted here.
echo $html ;
?>
```

![image](images/commonbl.jpg)

`encode.php`

![image](images/2bl.jpg)
Save the document in your web server’s `/htdocs` directory as `encode.php` then open the page via HTTP to hopefully see the HTML code snippet

![image](images/pg103_1.jpg)
The browser has interpreted the code and relocated to the server’s index page because it recognized the HTML `<script>` tag.

![image](images/3bl.jpg)
Return to the PHP script and insert a statement to encode special HTML characters

```php
$html = htmlspecialchars( $html ) ;
```

![image](images/4bl.jpg)
Save the edited document and reopen the page via HTTP again to see the HTML code snippet

![image](images/pg103_2.jpg)

![image](images/5bl.jpg)
Use the `View Source` facility in your web browser to see the special character entity equivalents encoded by PHP

![image](images/pg103_3.jpg)

![image](images/hot.jpg)
The PHP function `html_entity_decode()` can be used to unencode all entities back to their original character state.

## Summary

• The PHP built-in string comparison functions `strcmp()`, `strncmp()`, `strcasecmp()` and `strncasecmp()` each typically return a result of 1 (greater), 0 (equal) or -1 (less).
• String comparisons are based on the numerical ASCII value of each character, compared in sequence to account for order.
• The ASCII value of any character can be found using `ord()`.
• The length of any string can be found using `strlen()`.
• The numerical index position of a substring within a searched string can be found using `strpos()` and `strrpos()` functions.
• The search functions `strstr()`, `stristr()`, `strchr()` and `strrchr()` each return the remainder of a searched string on success.
