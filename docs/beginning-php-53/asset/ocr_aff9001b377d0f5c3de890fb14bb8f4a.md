# How It Works

Most of the code is similar to the script in Chapter 4. The script displays an XHTML header, then creates a table to display the results. It also uses a `for` loop to display the Fibonacci numbers F<sub>0</sub> to F<sub>10</sub>, much like the Chapter 4 script.

The difference is in how the Fibonacci numbers are computed. The iterative version in Chapter 4 uses two variables, `$num1` and `$num2`, to hold the current two Fibonacci numbers, computing new numbers as it iterates through the loop. This script, on the other hand, uses a recursive function, `fibonacci()`, to compute the Fibonacci number for any given sequence number. This function is then called from within the `for` loop to display the Fibonacci numbers F<sub>0</sub> to F<sub>10</sub>.

So how does the `fibonacci()` function work? You can see that it accepts the current sequence number, `$n`, as an argument. The first line of the function itself represents the base case:

```
if ( ( $n == 0 ) || ( $n == 1 ) ) return $n;
```

This code checks if the sequence number is 0 or 1; if it is then it immediately exits the function and returns the sequence number (because F<sub>0</sub> is 0 and F<sub>1</sub> is 1). So once this condition is met, the function finishes and control is passed back to the calling code.

If the base case hasn't yet been reached, the second line of code is run:

```
return fibonacci( $n-2 ) + fibonacci( $n-1 );
```

This code calls the `fibonacci()` function twice recursively — once to compute the Fibonacci number two positions lower in the sequence, and once to compute the Fibonacci number that's one position lower in the sequence. It then adds these two Fibonacci numbers together to produce the Fibonacci number for the current sequence number, which it then returns to the calling code (which will either be the code within the `for` loop, or another instance of the `fibonacci()` function).

So when this function is run with a sequence number of, say, 10, it calls itself to obtain the numbers at positions 8 and 9. In turn, when called with the sequence number 8, the function computes the Fibonacci number at this position by calling itself to obtain the numbers at positions 6 and 7, and so on. This process continues until the function is called with a sequence number of 0 or 1; at this point, it no longer calls itself but merely returns the value 0 or 1.

You can see that the function calls itself in a pattern that resembles a tree, with the initial function call as the root of the tree and the various recursive calls as branches of the tree. In fact, recursive functions are well suited to working on data organized like a tree, as you see when working with files and folders in Chapter 11.

# Summary

This chapter has introduced you to the concept of functions in PHP. A function is like a black box that can accept one or more inputs and return a result. You've learned that functions make it easier for you to write robust, structured code by breaking down large projects into smaller pieces. In addition, you learned that by encapsulating code inside a function, you only have to write that code once, no matter how many times you use it throughout your script.