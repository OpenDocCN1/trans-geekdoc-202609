and we'll consider functions that take no parameters at all (for which we'll still need the parentheses, though we won't type anything between them).

# # Variables and Operators

Variables in PHP are identical to variables in most other programming languages. For the uninitiated, a variable is a name given to an imaginary box into which any value may be placed. The following statement creates a variable called $testvariable (all variable names in PHP begin with a dollar sign) and assigns it a value of 3:

```
$testvariable = 3;
```

PHP is a loosely typed language. This means that a single variable may contain any type of data (be it a number, a string of text, or some other kind of value), and may change types over its lifetime. So the following statement, if it appears after the statement above, assigns a new value to our existing $testvariable. In the process, the variable changes type: where it used to contain a number, it now contains a string of text:

```
$testvariable = "Three";
```

The equals sign we used in the last two statements is called the **assignment operator**, as it is used to assign values to variables. Other operators may be used to perform various mathematical operations on values:

```
$testvariable = 1 + 1;   // Assigns a value of 2.
$testvariable = 1 - 1;   // Assigns a value of 0.
$testvariable = 2 * 2;   // Assigns a value of 4.
$testvariable = 2 / 2;   // Assigns a value of 1.
```

The lines above each end with a comment. Comments are a way to describe what your code is doing - they insert explanatory text into your code, and tell the PHP interpreter to ignore it. Comments begin with // and they finish at the end of the same line. You might be familiar with /* */ style comments in other languages - these work in PHP as well. I'll be using comments throughout the rest of this book to help explain what the code I present is doing.

Now, to get back to the four statements above, the operators we used here allow you to add, subtract, multiply, and divide numbers. Among others, there is also an operator that sticks strings of text together, called the **concatenation operator**:

```
$testvariable = "Hi " . "there!"; // Assigns a value of
"Hi there!".
```

Variables may be used almost anywhere that you use an actual value.
Consider these examples: