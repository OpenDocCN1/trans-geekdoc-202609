You can also add a bit of complexity by using index variables:

```
$current = 3;
print "Hello $names[$current], good to see you!\n";
```

> When you embed a particular element in the array as I did in the preceding code, make sure that you include the $ character before the index variable name. For example, if you mistakenly use $names[current] instead of $names[$current], you’ll get strange behavior when you run your program. Try it yourself; you’ll always get the first element of the array because the Perl compiler thinks current without the $ character is a string, and it tries to convert current to a number and just gets 0, because current is not a number.

# # Obtaining slices of a list

Perl makes it easy to get a *slice* of a list, which means a new list consisting of just a portion of the original list. Suppose this is your list:

```
@names = ("Amy", "Bob", "Carl", "Danielle",
       "Egbert", "Frank");
```

You want to get the second element, third element, and fourth element and save them in a new list. Here’s an amazingly short line of code that does all this:

```
@somenames = @names[1..3];
```

The two dots mean you’re obtaining a range of elements, from index 1 (which is the *second* element) up to and including index 3. This means @somenames now has the elements Bob, Carl, and Danielle.

> The original array is left unchanged. That means after you run the preceding code, your original array — @names — still has Amy, Bob, Carl, Danielle, Egbert, and Frank in it. The array @somenames has Bob, Carl, and Danielle in it, which are copies. Now suppose that after copying the slice, you change the original array like this:

```
$names[1] = 'Bridgette';
```

Now @names contains Amy, Bridgette, Carl, Danielle, Egbert, and Frank, and @somenames still has Bob, Carl, and Danielle in it.

This new variable is an array holding a list, so you can access it with its own indexes, which have nothing in common with the indexes of the original array: