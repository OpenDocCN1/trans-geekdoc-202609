A PHP compare function can be used instead of a user defined function. These could include strcmp, strcasecmp, strncasecmp, substrcmp, or other PHP comparison functions that return < 0, 0, or > 0 as a result.

# array_flip — returns all keys with their associated values in an array

“array_flip() returns an array in flip order, i.e. keys from array become values and values from array become keys.”

Syntax:

# array array_flip ($array $array)

Example:

$first_array = array('first_name' => 'Pete', 'last_name' => 'Smith', 'address' => '123 Main Street', 'city' => 'Atlanta', 'state' => 'GA', 'zip_code' => 30001);

```
$result = array_flip($first_array);
```

```
print_r($result);
```

Output:

```
Array (
    [Pete] => first_name
    [Smith] => last_name
    [123 Main Street] => address
    [Atlanta] => city
    [GA] => state
    [30001] => zip_code
)
```