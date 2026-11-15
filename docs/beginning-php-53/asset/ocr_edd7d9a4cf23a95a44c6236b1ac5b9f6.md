![](bbox=[0.19, 0.09, 0.72, 0.34])

Figure 7-1

# Working with Variable Functions

When you include a function call in your code, most of the time you’ll know the name of the function you want to call. However, sometimes it’s useful to be able to store the name of a function in a string variable, and use that variable instead of the function name when calling a function. Here’s an example:

```
$squareRoot = "sqrt";
echo "The square root of 9 is: " . $squareRoot( 9 ) . ".<br/>";
echo "All done!<br/>"
```

As you can see, the first line of code stores the function name, "sqrt", as a string in the $squareRoot variable. This variable is then used in place of the function name on the second line.

This example is fairly trivial, but it shows how the concept works. Here’s a slightly more complex example:

```
$trigFunctions = array( "sin", "cos", "tan" );
$degrees = 30;

foreach ( $trigFunctions as $trigFunction ) {
    echo "$trigFunction($degrees) = " . $trigFunction( deg2rad( $degrees ) )
        . "<br/>"
}
}
```

This code creates an array of three built-in function names — "sin", "cos", and "tan" — and sets up a $degrees variable. It then loops through the array. For each element, it calls the function whose name is stored in the element, passing in the value of $degrees converted to radians (using PHP’s built-in deg2rad() function), and displays the result. Here’s the output from the code: