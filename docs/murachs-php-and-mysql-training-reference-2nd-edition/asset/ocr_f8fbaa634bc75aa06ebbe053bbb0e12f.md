# How to assign floating-point values

# Using normal notation

```
$float_1 = 3.5;    // Must contain a decimal point
$float_2 = -6.0;   // May be negative
$float_3 = .125;   // Same as 0.125
$float_4 = 1.;     // Same as 1.0
```

# Using exponential notation

```
$exp_1 = 9.451e15;   // Expands to 9.451 × 10^15 - 9451000000000000
$exp_2 = 6.022e+23;   // Plus sign for exponent is optional
$exp_3 = 1.602e-19;   // Exponent may be negative
$exp_4 = 9.806e0;     // Exponent may be zero
$exp_5 = -1.759e11;   // Mantissa may be negative
$exp_6 = 3e9;         // Mantissa may be a whole number
```

# Two functions for working with infinity

| Function | Description |
|---|---|
| is_infinite($value) | Returns TRUE if $value is a positive or negative infinite value. |
| is_finite($value) | Returns TRUE if $value is a finite value. |

# Working with infinity

# Getting an infinite value

```
$inf_x = INF;      // Positive infinity, case-sensitive
$inf_x = -INF;     // Negative infinity
$inf_x = 1e200 * 1e200;  // Result is INF
$inf_x = 1 + INF;  // Result is INF
$inf_x = 1 / INF;  // Result is 0
$inf_x = 1 / 0;    // Generates a warning
```

# Testing for an infinite value

```
$result = 1e200 * 1e200;
if (is_infinite($result)) {
    echo('Result was out of range.');
} else {
    echo('Result is ' . $result);
}
```

# Description

+   - A *floating-point number* is a number with a fractional part. Floating point numbers are also called *floats, doubles,* or *real numbers.*
+   - To store numbers that are extremely large or small, you can use *exponential notation*. A floating-point number has about 14 digits of precision and the exponent can typically range from -307 to 308.
+   - The constants named INF and -INF represent infinite values. INF represents numbers that are too large to store as floating-point numbers, and -INF represents numbers that are too small to store.
+   - Operations that involve an infinite value may return unexpected results.
+   - Dividing by zero generates a warning.