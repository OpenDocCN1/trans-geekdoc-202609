using curly brackets, or braces ( { } ). If you wanted to display a weight value with a suffix to indicate pounds or ounces, the statement might look like this:

```
echo "The total weight is {$weight}lb";
```

If you did not use the braces around $weight , PHP would try to find the value of $weightlb , which probably does not exist in your script.

You could do the same thing by using the concatenation operator, the period symbol, which can be used to join two or more strings together, as shown in the following example:

```
echo 'The total weight is ' . $weight . 'lb';
```

The three valuestwo fixed strings and the variable $weight are simply stuck together in the order in which they appear in the statement. Notice that a space is included at the end of the first string because you want the value of $weight to be joined to the word is .

If $weight has a value of 99 , this statement will produce the following output:

```
The total weight is 99lb
```