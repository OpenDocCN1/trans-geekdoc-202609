# Chapter 6: PHP’s Built-in Functions

149

However, within single quotes the string will be treated literally.

```
$var = "this string";necho 'Please print $var';
```

The preceding code will print "Please print $var". This concept is discussed in greater detail in Chapter 4.

![](bbox=[0.181, 0.263, 0.243, 0.303])

print versus echo. Which one should you use? This is very much a matter of personal preference: use whichever you think better on the page. There's only one major difference between the two, and this may influence your decision. echo can take multiple arguments. That is, with echo, different portions can be separated by commas. This will work:

```
echo "this is part 1"; "this is part 2";
```

But this will not:

```
print "this is part 1"; "this is part 2";
```

# PRINT FUNCTIONS NOT USED IN THIS BOOK

They didn't come up here, but these are really important to know.

PRINT() This function outputs a string using the format specified in the description of the sprintf() function.

PRINT_R() This function is great for putting to productive the time you'd otherwise spending pulling your hair out. It prints the contents of any variable—most notably arrays and objects—to the screen.

```
void print_r (mixed expression)
```

We use it frequently when we're not getting the results we expect from arrays and objects.

![](bbox=[0.181, 0.768, 0.243, 0.808])

Do not print_r($GLOBALS).You will create an infinitely recursive loop.