# PHP Arrays

To construct an empty array, pass no arguments to array():
$addresses = array();

You can specify an initial key with => and then a list of values.
The values are inserted into the array starting with that key, with subsequent values having sequential keys:

$days = array(1 => "Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun");
// 2 is Tue, 3 is Wed, etc.

If the initial index is a nonnumeric string, subsequent indices are integers beginning at 0. Thus, the following code is probably a mistake:

```
$whoops = array('Fri' => "Black", "Brown", "Green");
```

```
// same as
$whoops = array('Fri' => "Black", 0 => "Brown", 1 => "Green");
```

# Adding Values to the End of an Array

To insert more values into the end of an existing indexed array,
use the [] syntax:

$family = array("Fred", "Wilma");
$family[] = "Pebbles"; // $family[2] is "Pebbles"

This construct assumes the array's indices are numbers and assigns elements to the next available numeric index, starting from 0. Attempting to append to an associative array without appropriate keys is almost always a programmer mistake, PHP will give the new elements numeric indices without issuing a warning:

```
$person = array('name' => "Fred");
$person[] = "Wilma"; // $person[0] is now "Wilma"
```

# Assigning a Range of Values

The range() function creates an array of consecutive integer or character values between and including the two values you pass to it as arguments. For example: