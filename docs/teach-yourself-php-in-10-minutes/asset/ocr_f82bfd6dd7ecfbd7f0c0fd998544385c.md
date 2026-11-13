# Numeric Data Types

You have already seen that PHP assigns a data type to each value and that the numeric data types are integer and double, for whole numbers.

To check whether a value is either of these types, you use the `is_float` and `is_int` functions. Likewise, to check for either numeric data type in one operation, you can use `is_numeric` .

The following example contains a condition that checks whether the value of `$number` is an integer:

```
```php
$number = "28";
if (is_int($number)) {
    echo "$number is an integer";
}
else {
    echo "$number is not an integer";
}
```
```

Because the actual declaration of that variable assigns a string valuealbeit one that contains a number the condition fails.

Although `$number` in the previous example is a string, PHP is flexible enough to allow this value to be used in numeric operations. The following example shows that a string value that contains a number can be incremented and that the resulting value is an integer:

```
```php
$number = "6";
$number++;
echo "$number has type " . gettype($number);
```
```

# Understanding NULLs

The value NULL is a data type all to itselfa value that actually has no value. It has no numeric value, but comparing to an integer value zero evaluates to true:

```
```php
$number = 0;
$empty=NULL;
if ($number == $empty) {
    echo "The values are the same";
}
```
```