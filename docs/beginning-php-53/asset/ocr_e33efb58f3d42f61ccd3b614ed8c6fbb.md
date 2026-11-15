# Escaping from Loops with the break Statement

Normally, a while, do...while, or for loop will continue looping as long as its test expression evaluates to true. However, you can exit a loop at any point while the loop's executing by using the break statement. This works just like it does within a switch construct (described earlier in this chapter) — it exits the loop and moves to the first line of code outside the loop.

Why would you want to do this? Well, in many situations it's useful to be able to break out of a loop. The infinite for loop discussed earlier is a good example; if you don't break out of an infinite loop somehow, it will just keep running and running, consuming resources on the server. For example, although the following while loop is ostensibly an infinite loop because its test expression is always true, it in fact counts to 10 and then exits the loop:

```
$count = 0;

while ( true ) {
  $count++;
  echo "I've counted to: $count<br />";
  if ( $count == 10 ) break;
}
```

Another common reason to break out of a loop is that you want to exit the loop prematurely, because you've finished doing whatever processing you needed to do. Consider the following fairly trivial example:

```
$randomNumber = rand( 1, 1000 );

for ( $i=1; $i <= 1000; $i++ ) {
  if ( $i == $randomNumber ) {
    echo "Hooray! I guessed the random number. It was: $i<br />";
    break;
  }
}
```

This code uses PHP's rand() function to generate and store a random integer between 1 and 1000, then loops from 1 to 1000, trying to guess the previously stored number. Once it's found the number, it displays a success message and exits the loop with break. Note that you could omit the break statement and the code would still work; however, because there's no point in continuing once the number has been guessed, using break to exit the loop avoids wasting processor time.

This type of break statement usage is common when working with potentially large sets of data such as arrays and database records, as you see later in this book.

# Skipping Loop Iterations with the continue Statement

Slightly less drastic than the break statement, continue lets you prematurely end the current iteration of a loop and move onto the next iteration. This can be useful if you want to skip the current item of data you're working with; maybe you don't want to change or use that particular data item, or maybe the data item can't be used for some reason (for example, using it would cause an error).

The following example counts from 1 to 10, but it misses out the number 4 (which is considered unlucky in many Asian cultures):