array_unshift will append items to the end of the array. The function will return the new size of the array. In this example, two items are added to the end of $first_array.

compact — creates an array containing variables and their values

# Syntax:

```
array compact ( mixed $varname1 [ , mixed $... ]
```

# Example:

```
$first_name = "Pete";
$last_name = "Smith";
$address = "123 Main Street";
$city = "Atlanta";
$state = "GA";
$zip_code = 30001;
```

```
$keys = array("first_name", "last_name", "address", "city", "state", "zip_code");
```

```
$first_array = compact($keys);
```

```
print_r($first_array);
```

# Output:

```
Array (
```