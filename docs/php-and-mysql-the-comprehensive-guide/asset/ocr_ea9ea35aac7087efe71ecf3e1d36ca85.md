The declaration is again simple. The enum is supplemented by a type declaration—that is, int or string. You define the values in the individual cases:

```
```php
enum values : int
{
    case case1 = 1;
    case case2 = 2;
    case case3 = 3;
    case case4 = 4;
}
```
```

To access the correct case with the scalar values, PHP offers two methods for enums:

+   - from(value) returns the matching enum case for the scalar value. If the value does not exist, PHP throws a ValueError.

+   - tryFrom(value) does basically does the same thing, except that it returns zero if a value does not exist. This variant is therefore suitable if, for example, unreliable values can also come from the data source and a separate error handling function is to be implemented.

In the following example, case2 is output.

```
```php
<?php
enum values : int
{
    case case1 = 1;
    case case2 = 2;
    case case3 = 3;
    case case4 = 4;
}

function output(values $parameter) {
    ...
}

$value = values::from(2);

output($value);
?>
```
```

# Listing 6.32 Enumerations with Scalar Values ("enumerations_scalar.php")

# ## 6.1.9 Helpful and Useful Information

This section summarizes some interesting help functions and code snippets that are needed from time to time.