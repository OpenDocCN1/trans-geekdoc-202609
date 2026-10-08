# Using Operators 31

In this case, the effects are reversed. That is, first, the value of $a is returned and printed, and second, it is incremented. The value of this whole expression is 4. This is the value that will be printed. However, the value of $a after this statement is executed is 5.

As you can probably guess, the behavior is similar for the -- (decrement) operator. However, the value of $a is decremented instead of being incremented.

# Reference Operator

The reference operator (&, an ampersand) can be used in conjunction with assignment. Normally, when one variable is assigned to another, a copy is made of the first variable and stored elsewhere in memory. For example,

```
$a = 5;
$b = &$a;
```

These code make a second copy of the value in $a and store it in $b. If you subsequently change the value of $a, $b will not change:

```
$a = 7; // $b will still be 5
```

You can avoid making a copy by using the reference operator. For example,

```
$a = 5;
$b = &$a;
$a = 7; // $a and $b are now 7
```

References can be a bit tricky. Remember that a reference is like an alias rather than a pointer. Both $a and $b point to the same piece of memory. You can change this by unsetting one of them as follows:

```
unset($a);
```

Unsetting does not change the value of $b (7) but does break the link between $a and the value 7 stored in memory.

# Comparison Operators

The comparison operators compare two values. Expressions using these operators return either the logical values true or false depending on the result of the comparison.

# The Equal Operator

The equal operator (==, two equals) allows you to test whether two values are equal. For example, you might use the expression

```
$a == $b
```

to test whether the values stored in $a and $b are the same. The result returned by this expression is true if they are equal or false if they are not.

You might confuse == with =, the assignment operator. Using the wrong operator will work without giving an error but generally will not give you the result you wanted. In general,