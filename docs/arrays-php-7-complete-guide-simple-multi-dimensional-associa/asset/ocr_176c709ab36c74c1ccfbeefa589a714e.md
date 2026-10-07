# Found Pete!

in_array returns TRUE if the item searched is in the array. It does not return the position of the item in the array. In this example, Pete is found in the array.

key_exists — alias of array_key_exists()

“key_exists — Checks if the given key or index exists in the array”

Syntax:

bool key_exists ( mixed $key , array $array )

Example:
$first_array = array('first_name' => 'Pete', 'last_name' => 'Smith', 'address' => '123nMain Street', 'city' => 'Atlanta', 'state' => 'GA', 'zip_code' => 30001);

```
if (key_exists('first_name', $first_array)) {

  print "The 'first_name' is in the array";

}
```

Output:

The ‘first_name’ is in the array

This function eliminates the need to create a loop when searching for a key in an array.