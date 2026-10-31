However, within single quotes the string will be treated literally:

```
$var = "this string";
echo 'Please print $var';
```

The preceding code will print “Please print $var”. This concept is discussed in greater detail in Chapter 4.

![](bbox=[0.18, 0.27, 0.26, 0.32])

print versus echo. Which should you use? This is very much a matter of personal preference: use whichever you think looks better on the page. There's only one major difference between the two, and this may influence your decision. echo can take multiple arguments. That is, with echo, different portions can be separated by commas. This will work:

```
echo "this is part 1", "this is part 2";
```

But this will not:

```
print "this is part 1", "this is part 2";
```

# PRINT FUNCTIONS NOT USED IN THIS BOOK

They didn't come up here, but these are really important to know about.

PRINTF() This function outputs a string using the format specified in the description of the sprintf() function.

PRINT_R() This function is great for putting to productive use the time you'd otherwise spend pulling your hair out. It prints the entire contents of any variable—most notably arrays and objects—to the screen.

```
void print_r (mixed expression)
```

We use it frequently when we're not getting the results we expect from arrays or objects.

![](bbox=[0.18, 0.76, 0.26, 0.82])

Do not do print_r($GLOBALS). You will create an infinitely recursive loop.