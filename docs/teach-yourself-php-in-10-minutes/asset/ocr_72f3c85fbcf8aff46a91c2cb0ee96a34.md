functions take two or more arguments and return the numerically lowest or highest element in the list, respectively.

This statement will display the larger of the two variables $a and $b :

```
echo max($a, $b);
```

There is no limit to the number of arguments that can be compared. The following example finds the lowest value from a larger set of values:

```
echo min(6, 10, 23, 3, 88, 102, 5, 44);
```

Not surprisingly, the result displayed is 3 .

# Random Numbers

You use `rand` to generate a random integer, using your system's built-in random number generator. The `rand` function optionally takes two arguments that specify the range of numbers from which the random number will be picked.

**Random Limit** The constant `RAND_MAX` contains the highest random number value that can be generated on your system. This value may vary between different platforms.

The following statement picks a random number between 1 and 10 and displays it:

```
echo rand(1, 10);
```

You can put this command in a script and run it a few times to see that the number changes each time it is run.

There is really no such thing as a computer-generated random number. In fact, numbers are actually picked from a very long sequence that has very similar properties to true random numbers. To make sure you always start from a different place in this sequence, you have to *seed* the random number generator by calling the `srand` function; no arguments are required.