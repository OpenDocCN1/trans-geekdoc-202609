# NULL

A “NULL” value[15] is a special variable that does not contain a value. A variable is NULL if:

+   - it is assigned the constant NULL,
+   - it has not been assigned any value,
+   - or it has been unset().

# Constants

Constants are values that do not change. Named constants are created in PHP using the define()[16] function:

```
define("BOILING_TEMP_IN_CELCIUS", 100);
echo BOILING_TEMP_IN_CELCIUS; // outputs 100
```

# Exercises

Create a script variables.php and do the following:

+   1. Assign numbers to two variables and echo their values.
+   2. Create a variable to hold a name, echo the string "Hello NAME" where NAME is the value of your variable.
+   3. Define a constant that represents the acceleration due to gravity (9.81 m/s). Echo the value of this constant.

[15] “NULL” value: http://php.net/language.types.null
[16] define(): http://php.net/function.define