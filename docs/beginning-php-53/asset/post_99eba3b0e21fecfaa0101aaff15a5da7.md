
First a new variable, $myVar, is initialized with the value 123. Next, a reference to $myVar is created, and the reference is stored in the variable $myRef. Note the ampersand (&) symbol after the equals sign; using this symbol creates the reference.

The next line of code adds one to the value of $myRef. Because $myRef actually points to the same data as $myVar, both $myRef and $myVar now contain the value 124, as shown by the two echo statements.

Now that you know what references are, and how to create them, it's time to look at how you can pass references into and out of your functions.

## Passing References to Your Own Functions

By passing a reference to a variable as an argument to a function, rather than the variable itself, you pass the argument *by reference*, rather than by value. This means that the function can now alter the original value, rather than working on a copy.

To get a function to accept an argument as a reference rather than a value, put an ampersand (&) before the parameter name within the function definition:

```
function myFunc( &$aReference ) {
    // ( do stuff with $aReference)
}
```

Now, whenever a variable is passed to myFunc(), PHP actually passes a reference to that variable, so that myFunc() can work directly with the original contents of the variable, rather than a copy.

Now that you know this, you can fix the earlier counter example by using a reference:

```
function resetCounter( &$c ) {
    $c = 0;
}
```

```
$counter = 0;
$counter++;
$counter++;
$counter++;
echo "$counter<br/>" ; // Displays "3"
resetCounter( $counter );
echo "$counter<br/>" ; // Displays "0"
```

The only change in the script is in the first line:

```
function resetCounter( &$c ) {
```

Adding the ampersand before the $c causes the $c parameter to be a reference to the passed argument ($counter in this example). Now, when the function sets $c to zero, it's actually setting the value of $counter to zero, as can be seen by the second echo statement.

Many built-in PHP functions accept references in this way. For example, PHP's sort() function, which you met in the previous chapter, changes the array you pass to it, sorting its elements in order. The array is passed in by reference rather than by value, so that the function can change the array itself, rather than a copy of it.

### Returning References from Your Own Functions

As well as passing variables by reference into functions, you can also get functions to return references, rather than values. To do this, you place an ampersand before the function name in your function definition. Then, when you return a variable with the `return` statement, you pass a reference to that variable back to the calling code, rather than the variable's value:

```php
function &myFunc() {
    // (do stuff)
    return $var; // Returns a reference to $var
}
```

Here's an example that shows return-by-reference in action:

```php
$myNumber = 5;

function &getMyNumber() {
    global $myNumber;
    return $myNumber;
}

$numberRef = &getMyNumber();
$numberRef++;
echo "\$myNumber = $myNumber<br/>"; // Displays "6"
echo "\$numberRef = $numberRef<br/>"; // Displays "6"
```

Here's how it works. First, a global variable, `$myNumber`, is created and given the value 5. Next, a function, `getMyNumber()`, is defined. This function simply uses the `global` keyword to access the global variable `$myNumber`, then returns `$myNumber`. Because `getMyNumber()` has an ampersand before its name, it returns a reference to `$myNumber`, rather than the value that `$myNumber` holds.

Next, the script calls `getMyNumber()`. The return value of `getMyNumber()` — that is, the reference to `$myNumber` — is then assigned to a new variable, `$numberRef`. Notice the ampersand after the equals sign; this ensures that `$numberRef` takes on the reference returned by `getMyNumber()`, rather than taking on the value that the reference points to.

At this point, `$numberRef` and `$myNumber` both point to the same contents. To prove this, the code increments `$numberRef`, then outputs the values of both `$myNumber` and `$numberRef`. Notice that they both hold the same value — 6 — because they both point to the same piece of data.

Return-by-reference is used quite often in languages such as C++, because it's the easiest way to return complex data structures such as arrays and objects. However, because PHP lets you return pretty much anything with its `return` statement, and automatically returns objects by reference anyway (as you see in the next chapter), you probably won't use return-by-reference that much in PHP.

### Writing Recursive Functions

In Chapter 4, you learned how to use loops to operate on large amounts of data at once. Looping is often known as _iteration_.

Recursion is another technique that you can use if you need to work on a set of values. Generally speaking, it's usually easier to use iteration than recursion; however, in certain situations recursion makes more sense. Practically any loop can be converted to use recursion instead, and vice-versa.

So what is recursion, and how does it relate to functions? Well, in simple terms, recursion occurs when a function calls itself. As you'd imagine, such a process would repeat indefinitely if not stopped, so the recursion needs to have some sort of end condition — much like a loop. This end condition is known as the *base case*, and the part of the function that calls itself is known as the *recursive case*.

Here's a quick overview of how a recursive function operates:

- The recursive function is called by the calling code
- If the base case, or end condition, is met, the function does any processing required, then exits
- Otherwise, the function does any processing required, then calls itself to continue the recursion

Of course, you have to make sure that the base case is eventually reached, otherwise the function will keep calling itself indefinitely (causing an infinite loop).

## Try It Out Creating the Fibonacci Sequence with Recursion

Chapter 4 showed how to use looping to create the Fibonacci sequence of numbers. The following script is similar to that shown in Chapter 4, except that it uses a recursive function to generate each value, rather than computing the values iteratively.

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Fibonacci sequence using recursion</title>
<link rel="stylesheet" type="text/css" href="common.css" />
<style type="text/css">
th {text-align: left; background-color: #999; }
th, td { padding: 0.4em; }
tr.alt td { background: #ddd; }
</style>
</head>
<body>
<h2>Fibonacci sequence using recursion</h2>
<table cellspacing="0" border="0" style="width: 20em; border:
1px solid #666;">
<tr>
<th>Sequence #</th>
<th>Value</th>
</tr>
<?php
$iterations = 10;

function fibonacci( $n ) {
    if ( ( $n == 0 ) || ( $n == 1 ) ) return $n;
    return fibonacci( $n-2 ) + fibonacci( $n-1 );
}

for ( $i=0; $i <= $iterations; $i++ )
{
?>
    <tr><?php if ( $i % 2 != 0 ) echo ' class="alt" ?>'
    <td>F<sub><?php echo $i?></sub></td>
    <td><?php echo fibonacci( $i)?></td>
    </tr>
<?php
}
</table>
</body>
</html>
```

Save the script as fibonacci_recursion.php in your document root folder and run it via your Web browser. You should see a page much like Figure 7-6. Notice that the sequence is identical to that produced by the script in Chapter 4.

![](img/1ddec54918a4802eb9b4febec3d4e7f6_199_0.png)

Figure 7-6

## How It Works

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

## Summary

This chapter has introduced you to the concept of functions in PHP. A function is like a black box that can accept one or more inputs and return a result. You've learned that functions make it easier for you to write robust, structured code by breaking down large projects into smaller pieces. In addition, you learned that by encapsulating code inside a function, you only have to write that code once, no matter how many times you use it throughout your script.
