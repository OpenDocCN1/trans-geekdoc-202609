# Updating existing information

You update existing information with the UPDATE query, as I describe in Chapter 4. Updating means changing data in the columns of rows that are already in the database — not adding new rows to the database table. The general format is

```
$query = "UPDATE tablename SET col=value WHERE col=value";
$result = mysql_query($query)
    or die ("Couldn't execute query.");
```

For instance, the statements to update the phone number for Goliath Smith are

```
$firstName = "Goliath";      // from form field
$lastName = "Smith";          // from form field
$phone = "555-555-5555";      // from form field
$query = "UPDATE Member SET phone='$phone'
          WHERE lastName='$lastName'
          AND firstName='$firstName'";
$result = mysql_query($query)
    or die ("Couldn't execute query.");
```

![](bbox=[0.1, 0.44, 0.2, 0.52])

If you don’t use a WHERE clause in an UPDATE query, the field that is SET is set for all the rows. That is seldom what you want to do.

Listing 8-16 shows a program called updatePhone.php that stores a name and a phone number from a form.

# Listing 8-16: Program That Updates Data

```
<?php
/* Program name: updatePhone.php
 * Description: Program checks the phone number for incorrect format. Updates
 * the phone number in the database for the specified name.
 */
?>
<html>
<head><title>Member Phone Number</title></head>
<body>
<?php
$phone = strip_tags(trim($_POST['phone']));
$phone = ereg_replace("[^0-9]","",$phone);
$first_name = $_POST['first_name'];
$last_name = $_POST['last_name'];

/* check information from the form */

/* set up array of field labels */
$label_array = array ( "first_name" => "First Name",
                       "last_name" => "Last Name",
```