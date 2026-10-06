# Chapter 3: PHP Language Basics

The location of the operators makes a difference. Placing the operator before the variable name causes the variable's value to be incremented or decremented before the value is returned; the operator after the variable name returns the current value of the variable first, then adds or subtracts from the variable. For example:

```
$x = 5;
echo ++$x; // Displays "6" (and $x now contains 6)
$x = 5;
echo +$x; // Displays "5" (and $x now contains 6)
```

Interestingly, you can use the increment operator with characters as well. For example, you can "add" one to the character B and the returned value is C. However, you cannot subtract from (decrement) character values.

# Logical Operators

PHP's logical operators work on Boolean values. Before looking at how logical operators work, it's worth taking a bit of time to explore Boolean values thoroughly.

As you've already seen, a Boolean value is either true or false. PHP automatically evaluates expressions as either true or false when needed, as you've already seen, using settype() or explicitly convert to a Boolean value if necessary.

For example, the following expressions evaluate to true:

```
1
1 == 1
3 > 2
"hello" != "goodbye"
```

The following expressions evaluate to false:

```
3 < 2
gettype( 3 ) == "array"
"hello" == "goodbye"
```

In addition, PHP considers the following values to be false:

+   * The literal false
* The integer zero (0)
* The float zero (0.0)
* An empty string ("")
* The string zero ("0")
* An array with zero elements
* The special type null (including any unset variables)
* A SimpleXML object that is created from an empty XML tag (more on SimpleXML in Chapter 14)

All other values are considered true in a Boolean context.