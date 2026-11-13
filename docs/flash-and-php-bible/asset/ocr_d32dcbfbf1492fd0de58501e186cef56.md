This code is not only checking for a valid value but also ensuring that value is of a valid length.

```
if (!empty($name) && strlen($name) > 0)
```

In a real-world application you would probably check for a value of at least two to three characters, but that all depends on the intended use. This small update to the code ensures that a call from Flash or any other method will be secured.

# Validating ZIP codes

Of course, securing data is not limited to basic form fields. Assume there is a portion to the application that accepts a five-digit ZIP code when the user submits an image. The way to ensure a valid ZIP code is by testing for a numeric value and a valid length.

```
<?php

$zipCode = $_POST['zip'];

if(is_numeric($zipCode) && strlen($zipCode) == 5)
{
// valid zip code found
}

?>
```

The is_numeric() function accepts a variable as an argument that is tested to determine whether or not that value is a number. This function will return a true/false response so it can easily be used within an if statement or you could assign the result to a variable.

# Looking for valid types

If you want to perform this same basic validation within Flash, you would use the typeof and length functions. The typeof function returns a string value defining what the type is for the passed-in item. This function can be used for more than just number validation, but it works perfectly for this example:

```
if (typeof(zipCode) == "number" && zipCode.toString().length == 5)
{
// valid zip code found
}
```

# Cleaning User Data

Now that you have a better understanding of security in your application, the next step is to sanitize or clean more advanced data before it is stored.