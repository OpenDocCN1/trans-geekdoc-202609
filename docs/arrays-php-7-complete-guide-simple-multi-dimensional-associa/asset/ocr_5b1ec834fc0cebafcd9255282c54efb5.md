$result_array = array_intersect_uassoc($first_array, $second_array, "strcasecmp");

print_r($result_array);

# Output:

Array (
    [city] => Atlanta
    [state] => GA
)

This example returns the common values Atlanta and GA but not the zip code since the indexes are different. strcasecmp is a PHP function that compares strings. If they are an exact match then this example would return the value as shown (from $first_array). Other PHP functions which return 0, >0, or <0 can be used (see next example).

# Example:

$first_array = array('first_name' => 'Pete', 'last_name' => 'Smith', 'address' => '123
Main Street', 'city' => 'Atlanta', 'state' => 'GA', 'zip_code' => 30001);

$second_array = array('firstname' => 'Sally', 'lastname' => 'Parisi', 'address' => '101
South Street', 'city' => 'Atlanta', 'state' => 'GA', 'zipcode' => 30001);

```
function key_compare($first_key, $second_key)
{
    if ($first_key == $second_key)
        return 0;
    else if ($first_key > $second_key)
        return 1;
    else
        return -1;
}
```

$result_array = array_intersect_uassoc($first_array, $second_array, "key_compare");