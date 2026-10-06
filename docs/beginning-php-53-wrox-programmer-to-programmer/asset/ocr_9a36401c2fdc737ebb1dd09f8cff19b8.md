# Chapter 7: Functions

First a new variable, $myVar, is initialized with the value 123. Next, a reference to $myVar is created, and the reference is stored in the variable $myRef. Note the ampersand (&) alters the equals sign; using this symbol creates the reference.

The next line of code adds one to the value of $myRef. Because $myRef actually points to the same data as $myVar, both $myRef and $myVar now contain the value 124, as shown by the two echo statements.

Now that you know what references are, and how to create them, it's time to look how you can pass references into and out of your functions.

# Passing References to Your Own Functions

By passing a reference to a variable as an argument to a function, rather than the variable itself, you pass the argument by reference, rather than by value. This means that the function can alter the original value, rather than working on a copy.

To get a function to accept an argument as reference rather than by value, put an ampersand (&) before the parameter name within the function:

```
function myFunction(&$aReference) {
    // (do stuff with $aReference)
}
```

Now, when a variable is passed to myFunction(), PHP actually passes a reference to that variable, so that myFunction() can work directly with the contents of the variable, rather than a copy.

Now that you know, you can fix the earlier counter example by using a reference:

```
function resetCounter(&$c) {
    $c = 0;
}
```

```
$counter = 0;
$counter++;
$counter--;
$counter++;
echo "$counter<br/>"; // Displays "3"
resetCounter($counter);
echo "$counter<br/>"; // Displays "0"
```

The only change in the script is in the first line:

```
function resetCounter(&$c) {
```

Adding the ampersand before the $c makes the $c parameter to be a reference to the passed argument ($counter in this example). Now, when the function sets $c to zero, it alters the value of $counter to zero, as can be seen by the second echo statement.

Many built-in PHP functions accept references in this way. For example, PHP's sort() function, which you met in the previous chapter, changes the array you pass to it, sorting its elements in order. The array is passed in by reference rather than by value, so that the function can change the array itself, rather than a copy of it.

159