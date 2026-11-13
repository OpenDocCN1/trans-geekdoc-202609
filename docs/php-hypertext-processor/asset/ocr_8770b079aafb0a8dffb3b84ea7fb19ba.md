# # Integers

They are whole numbers, without a decimal point, like 4195. They are the simplest type .they correspond to simple whole numbers, both positive and negative. Integers can be assigned to variables, or they can be used in expressions, like so:

```
$int_var = 12345;
$another_int = -12345 + 12345;
```

Integer can be in decimal (base 10), octal (base 8), and hexadecimal (base 16) format. Decimal format is the default, octal integers are specified with a leading 0, and hexadecimals have a leading 0x.

For most common platforms, the largest integer is (2**31 . 1) (or 2,147,483,647), and the smallest (most negative) integer is . (2**31 . 1) (or .2,147,483,647).

# # Doubles

They like 3.14159 or 49.1. By default, doubles print with the minimum number of decimal places needed. For example, the code:

```
$many = 2.2888800;
$many_2 = 2.2111200;
$few = $many + $many_2;
print(. $many + $many_2 = $few<br>. );
```

It produces the following browser output:

```
2.28888 + 2.21112 = 4.5
```

# # Boolean

They have only two possible values either true or false. PHP provides a couple of constants especially for use as Booleans: TRUE and FALSE, which can be used like so:

```
if (TRUE)
print("This will always print<br>");
else
print("This will never print<br>");
```

# # Interpreting other types as Booleans

Here are the rules for determine the "truth" of any value not already of the Boolean type:

+   - If the value is a number, it is false if exactly equal to zero and true otherwise.
+   - If the value is a string, it is false if the string is empty (has zero characters) or is the string "0", and is true otherwise.