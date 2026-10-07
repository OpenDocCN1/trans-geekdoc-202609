```
array('first_name' => 'Pete', 'last_name' => 'Smith', 'address' => '123 Street', 'city' => 'Atlanta', 'state' => 'GA', 'zip_code' => 30001),
array('first_name' => 'Sally', 'last_name' => 'Parisi', 'address' => '101 South Street', 'city' => 'Atlanta', 'state' => 'GA', 'zip_code' => 30001);

$first_names = array_column($customer_record, 'first_name');
print_r($first_names);
```

Output:

Array

```
(
[0] => Pete
[1] => Sally
)
```

In this example, all first names in the customer_array are returned.

In PHP 7 you can also specify an index in the second parameter.

Example:

```
$customer_record = array (
array('first_name' => 'Pete', 'last_name' => 'Smith', 'address' => '123 Main Street', 'city' => 'Atlanta', 'state' => 'GA', 'zip_code' => 30001),
array('first_name' => 'Sally', 'last_name' => 'Parisi', 'address' => '101 South Street', 'city' => 'Atlanta', 'state' => 'GA', 'zip_code' => 30001)
);
```

```
$first_names = array_column($customer_record, 'first_name', 'last_name');
print_r($first_names);
```

Output:

Array

```
(
[Smith] => Pete
[Parisi] => Sally
)
```

In this example, the values in last_name, are used to populate the new keys (subscripts) which are returned from the function.