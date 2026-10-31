
# Conditional tests

Conditional tests can be made with the `isset()` function to indicate where form fields have been left empty, or to provide a response page where the fields have been completed:

![image](images/1r.jpg)Create an HTML document containing a form with three radio buttons providing a single field for data submission

```
<form action="isset_handler.php" method="POST">
<fieldset>
<legend>What kind of language is PHP?</legend>  
Scripting<input type="radio"
name="definition" value="Scripting"> <br>
Markup<input type="radio"
name="definition" value="Markup"> <br>
Programming<input type="radio"
name="definition" value="Programming">
</fieldset><p><input type="submit" ></p>
</form>
```

![image](images/commonr.jpg)

### isset.php

![image](images/2r.jpg)Now, save the document in your web server’s `/htdocs` directory as `isset.php`

![image](images/3r.jpg)Next, create an HTML document containing a PHP script to initialize a variable with a submitted value – or with `NULL` if no value has been submitted

```
<?php
if ( isset( $_POST['definition'] ) )
{
$definition = $_POST['definition'] ;
}
else
{
$definition = NULL ;
}
# Response statements to be inserted here (Step 4).
?>
```

![image](images/commonr.jpg)

### isset_handler.php

![image](images/4r.jpg)Finally, insert statements to output an appropriate response according to the value of the variable

```
if ( $definition != NULL )
{
if ( $definition != 'Scripting' )
{ echo "$definition is Incorrect" ; }
else
{ echo "$definition is Correct" ; }
}
else
{ echo 'You must select one answer' ; }
?>
```

![image](images/5r.jpg)Save the document in your web server’s `/htdocs` directory as `isset_handler.php` then open `isset.php` via HTTP and submit the form to see the responses

![image](images/pg141_1.jpg)

![image](images/pg141_2.jpg)

![image](images/pg141_3.jpg)

![image](images/pg141_4.jpg)

![image](images/hot.jpg)

It is technically more efficient to test whether a condition is not `TRUE` than whether it is `TRUE` – as fewer possibilities need evaluating.

# Validating form data

As users may inadvertently submit forms with empty fields, or with data in the wrong format, it is essential your PHP scripts ensure required fields are completed and submitted data is valid.

![image](images/pg142_1.jpg)

To ensure the user has entered something into a text field, PHP provides an `empty()` function that accepts a variable argument and returns `TRUE` if its value is an empty string, zero, `NULL` or `FALSE`.

To ensure the user has entered data in numeric format, PHP provides an `is_numeric()` function that accepts a variable argument and returns `TRUE` only if its value is a number.

More specific data validation can be performed using the PHP `preg_match()` function that accepts a “regular expression” argument and a variable argument in which to seek a pattern. Typically, this is used to ensure an email address is in the expected format:

![image](images/1r.jpg)Create an HTML document containing a form with two text fields for data submission

```
<form action="valid_handler.php" method="POST">
<fieldset>
<legend>Enter a quantity and email address</legend>
<p>Quantity : <input type="text" name="quantity"></p>
<p>Email Address : <input type="text" name="email"></p>
</fieldset><p><input type="submit" ></p>
</form>
```

![image](images/commonr.jpg)

### valid.php

![image](images/2r.jpg)Now, save the document in your web server’s `/htdocs` directory as `valid.php`

![image](images/3r.jpg)Next, create an HTML document containing a PHP script to initialize a variable with a submitted value – or with `NULL` if no value has been submitted

```
<?php
if ( !empty ( $_POST['quantity'] ) )
{
$quantity = $_POST['quantity'] ;
# Format validation to be inserted here (Step 4).
}
else
{ $quantity = NULL ; echo 'You must enter a quantity<br>' ; }
```

![image](images/commonr.jpg)

### valid_handler.php

![image](images/4r.jpg)Insert statements to ensure the format is numeric

```
if ( !is_numeric( $quantity ) )
{ $quantity = NULL ; echo 'Quantity must be numeric<br>' ; }
```

![image](images/5r.jpg)Now, add statements to initialize another variable with a submitted value – or with `NULL` if no value is submitted

```
if ( !empty ( $_POST['email'] ) )
{
$email = $_POST['email'] ;
# Format validation to be inserted here (Step 6).
}  
else
{ $email = NULL ; echo 'You must enter an email address' ; }
```

![image](images/6r.jpg)Next, insert statements to ensure the email address uses the expected pattern

```
$pattern = '/\\b[\\w.-]+@[\\w.-]+\\.[A-Za-z]{2,6}\\b/' ;
if ( !preg_match( $pattern , $email ) )
{ $email = NULL ; echo 'Email address is incorrect format' ; }
```

![image](images/7r.jpg)Finally, add a statement to output valid submitted data

```
if ( ( $quantity != NULL ) && ( $email != NULL ) )
{ echo "Email : $email<br>Quantity : $quantity " ; }
?>
```

![image](images/8r.jpg)Save the document in your web server’s `/htdocs` directory `valid_handler.php` then open `valid.php` via HTTP and submit the form to see the responses

![image](images/pg143_1.jpg)

![image](images/pg143_2.jpg)

![image](images/hot.jpg)

Strictly speaking, the topic of regular expressions is outside the remit of this book, but you can precisely copy the pattern in this example to ensure email addresses are in the expected format.

# Filtering data

![image](images/pg144_1.jpg)

To validate user input easily, PHP provides a `filter_var()` function that can be used to both validate and “sanitize” input values. This function requires two arguments to specify the variable to be filtered and a constant name of the filter to be used:

| Filter Constant Name | Convention |
| --- | --- |
| `FILTER_VALIDATE_BOOLEAN` | Boolean value |
| `FILTER_VALIDATE_EMAIL` | Email address format |
| `FILTER_VALIDATE_FLOAT` | Floating-point number |
| `FILTER_VALIDATE_INT` | Integer number |
| `FILTER_VALIDATE_IP` | IP address format |
| `FILTER_VALIDATE_MAC` | MAC address format |
| `FILTER_VALIDATE_REGEXP` | Regular expression format |
| `FILTER_VALIDATE_URL` | URL format |
| `FILTER_SANITIZE_EMAIL` | Strip invalid characters |
| `FILTER_SANITIZE_ENCODED` | URL-encode string |
| `FILTER_SANITIZE_MAGIC_QUOTES` | Backslash-escape characters |
| `FILTER_SANITIZE_NUMBER_FLOAT` | Strip all non-digits |
| `FILTER_SANITIZE_NUMBER_INT` | Strip all non-digits |
| `FILTER_SANITIZE_SPECIAL_CHARS` | HTML-escape ‘”<>& |
| `FILTER_SANITIZE_STRING` | Strip HTML tags |
| `FILTER_SANITIZE_URL` | Strip invalid characters |
| `FILTER_CALLBACK` | Call a custom filter function |

![image](images/forget.jpg)

The validation filters return `TRUE` when validation succeeds, otherwise they will return `FALSE`.

![image](images/hot.jpg)

Some filters allow further options to be specified. For example, a numeric range can be specified to `FILTER_VALIDATE_INT`.

![image](images/1r.jpg)Create an HTML document containing a PHP script that begins by writing a styled HTML page heading

```
<?php
$hdr = '<h1 style="color:red">PHP in easy steps</h1>' ;
echo $hdr ;
```

![image](images/commonr.jpg)

### filter.php

![image](images/2r.jpg)Next, sanitize the page heading by stripping the HTML tags to remove styling and display the stripped version

```
$hdr = filter_var( $hdr , FILTER_SANITIZE_STRING ) ;
echo "Sanitized heading : $hdr" ;
```

![image](images/3r.jpg)Now, add a function to validate a parameter as being a correctly formatted email address

```
function validate( $email )
{
if ( filter_var( $email , FILTER_VALIDATE_EMAIL ) )
{ echo( "<hr>$email IS a valid email address" ) ; }
else
```
