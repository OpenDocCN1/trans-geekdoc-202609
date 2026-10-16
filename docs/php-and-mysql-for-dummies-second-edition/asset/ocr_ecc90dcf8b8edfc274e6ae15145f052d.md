# Listing 8-5 (continued)

```
    foreach ($_POST as $field => $value)
    {
        echo "$field = $value<br>";
    }
?>
</body></html>
```

If the user typed the name Goliath Smith into the form in Figure 8-4, the following output is displayed:

```
fullname = Goliath Smith
```

The output displays only one line because there is only one field in the form in Figure 8-4.

The program in Listing 8-5 is written to process the form information from any form that uses the POST method. Suppose that you have a slightly more complicated form, such as the program in Listing 8-6 that displays a form with several fields.

# Listing 8-6: A Program That Displays an Address Form

```
<?php
/*  Program name: displayForm
 *  Description:  Script displays a form that asks for the
 *                customer address.
 */
echo "<html>
        <head><title>Customer Address</title></head>
        <body>";
$labels = array( "firstName"=>"First Name:",
                "midName"=>"Middle Name:",
                "lastName"=>"Last Name:",
                "street"=>"Street Address:",
                "city"=>"City:",
                "state"=>"State:",
                "zip"=>"Zipcode:");
echo "<p align='center'>
        <b>Please enter your address below.</b><hr>";
echo "<form action='processform.php' method='POST'>
        <table width='95%' border='0' cellspacing='0'
                cellpadding='2'>\n";
foreach($labels as $field=>$label)
{
    echo "<tr>
            <td align='right'><B>{$labels[$field]} </B></br></td>
            <td><input type='text' name='$field' size='65'
                    maxlength='65' ></td>
            </tr>";
```