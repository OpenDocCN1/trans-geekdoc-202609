I have 10000 dollars in my pocket.
Wow! Depositing 50! I'm rich!
I am about to spend 25 in groceries!
The amount in my pocket is still 10000!

![](bbox=[0.14, 0.195, 0.24, 0.275])

If you're familiar with other languages, the idea that variables are global by default will seem strange. In Perl, if you declare a variable inside a subroutine, by default that variable becomes part of the global scope. To prevent this from happening, declare the variable using the my keyword.

# Returning data to the caller

Although passing a single or multiple items to a subroutine is exciting, the most amazing thing you can possibly imagine is for a subroutine to return data back to the caller. If you haven't experienced this, then your life has been far from complete.

Just as you can pass a set of parameters to a subroutine as a list, you can pass a set of data back out of the subroutine as a list. Or, you can pass a single item of data, which is a scalar.

Take a look at this example.

```
sub Multiply {
    $first = @_[0];
    $second = @_[1];
    return $first * $second;
}

$total = Multiply(10,20);
print "The total is $total\n";
```

The Multiply subroutine accepts two parameters. It then multiplies these two parameters and returns the single number as a scalar. In the main code, the call to the subroutine is on the right side of an equal sign. That means that when the subroutine returns, you get back a single number, and you store that number in the variable called $total. Then in the next line, you print out that number.

Here's the output from this program:

The total is 200

The subroutine returned a value, 200, and you were able to store that value inside a variable.