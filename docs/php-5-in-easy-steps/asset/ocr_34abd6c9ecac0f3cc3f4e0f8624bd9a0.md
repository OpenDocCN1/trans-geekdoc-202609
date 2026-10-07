# Variables

A variable is a place in which to store data for manipulation within a PHP script. All variables begin with a "$" character, followed by a meaningful name of your choice. When naming variables, any letters, digits and the "_" underscore character may be used, the variable name may not begin with a digit. These are all valid variable names:

```
$abc

$my_first_variable

$var123
```

Data is assigned to a variable using the "=" operator. The assignment statement, like all PHP statements, should end with a semi-colon terminator.

The example below recreates the text example from page 22. In this case though, the entire text content is assigned to a variable $str. This makes the script more efficient because the whole text content is now written into the text area with just a single call to the echo() function, rather than the five calls used previously.

![](bbox=[0.053, 0.353, 0.266, 0.467])

![](bbox=[0.198, 0.545, 0.276, 0.673])

Note that the $str variable is not surrounded by quotes in the call to the echo() function it is not to be treated literally.

Opening this example in a web browser, via Apache, produces precisely the same generated page as that of the previous example shown at the bottom of page 22.